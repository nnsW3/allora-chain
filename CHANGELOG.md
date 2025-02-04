<!--
Guiding Principles:

Changelogs are for humans, not machines.
There should be an entry for every single version.
The same types of changes should be grouped.
Versions and sections should be linkable.
The latest version comes first.
The release date of each version is displayed.
Mention whether you follow Semantic Versioning (we do at and after v1.0.0).

Usage:

Change log entries are to be added to the Unreleased section
under the appropriate stanza (see below).
Each entry should ideally include the Github issue or PR reference.

The issue numbers will later be link-ified during the
release process so you do not have to worry about including
a link manually, but you can if you wish.

Types of changes (Stanzas):

* __Added__ for new features.
* __Changed__ for changes in existing functionality that did not aim to resolve bugs.
* __Deprecated__ for soon-to-be removed features.
* __Removed__ for now removed features.
* __Fixed__ for any bug fixes that did not threaten user funds or chain continuity.
* __Security__ for any bug fixes that did threaten user funds or chain continuity.

Breaking changes affecting client, API, and state should be mentioned in the release notes.

Ref: https://keepachangelog.com/en/1.0.0/
Ref: https://github.com/osmosis-labs/osmosis/blob/main/CHANGELOG.md
-->

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html) for all versions `v1.0.0` and beyond (still considered experimental prior to v1.0.0).

## [Unreleased]
<!-- ## v0.3.0 -->
* Refactors to adapt to single transaction insertions from workers and reputers.

### Added

* Changelog added (this), improved [contribution guidelines](./CONTRIBUTING.md), and simplified [PR template](./.github/pull_request_template.md)
* [#443](https://github.com/allora-network/allora-chain/pull/443) Create mechanism to import and export state with `initGenesis` and `exportGenesis`
* [#461](https://github.com/allora-network/allora-chain/pull/461) Create index of topics by block height at which their open worker nonce closes
* [#432](https://github.com/allora-network/allora-chain/pull/432) State sync enabled for faster validator syncing
* [#478](https://github.com/allora-network/allora-chain/pull/478) Create and apply abstraction for augmenting topic fee revenue that is sure to check for topic activation criteria for both funding events, fee payments, and stake additions
* [#482](https://github.com/allora-network/allora-chain/pull/482) Creation of an official Upgrade Flow

### Removed

* [#458](https://github.com/allora-network/allora-chain/pull/458) Removal of Blockless and batch processing; Introduction of online, individual payload processing. This resolves many security, performance, and scalability issues.
   * A number of PRs were merged prior to v0.3.0 that improved upon our usage of Blockless, however that has been removed in favor of its removal in #458. Hence, we are not listing those PRs here.
   * [#462](https://github.com/allora-network/allora-chain/pull/462) Add individual payload processing
   * [#470](https://github.com/allora-network/allora-chain/pull/470) Skim of top performers per topic as they submit payloads ("online skimming")
   * [#464](https://github.com/allora-network/allora-chain/pull/464) Remove libp2p peer ids from chain
   * [#459](https://github.com/allora-network/allora-chain/pull/459) Revamp nonce management

### Fixed

* [#486](https://github.com/allora-network/allora-chain/pull/486) Correctly set initial emission per unit staked token
* [#460](https://github.com/allora-network/allora-chain/pull/460) Apply a number of bugfixes and high-precision unit tests that ensure our implementation matches our simulation of Allora and therefore the original intentions of the whitepaper and Foundation.
* [#487](https://github.com/allora-network/allora-chain/pull/487) Patch to have the single `allorad` home folder in Docker
* [#437](https://github.com/allora-network/allora-chain/pull/437) Fix issue for excessive effective revenue dripping
* [#441](https://github.com/allora-network/allora-chain/pull/441) Prevent DoS from attempting to withdraw negative stake amounts
* [#472](https://github.com/allora-network/allora-chain/pull/472) Prevent topics to be created with a ground truth lag too big so that the reputation nonce could be dropped when the ground truth is revealed
* [#484](https://github.com/allora-network/allora-chain/pull/484) Fix issue with permissions within Docker container
* [#477](https://github.com/allora-network/allora-chain/pull/477) Fix issue arising from no forecasts being sent in worker payload
* [#436](https://github.com/allora-network/allora-chain/pull/436/files) Fix bug related to excessive usage of topic ground truth lag and misleading error message
* Additional bugfixes and improvements

### Security

* [#454](https://github.com/allora-network/allora-chain/pull/454) Bump CometBFT version
* [#465](https://github.com/allora-network/allora-chain/pull/465) Catch and avert error leading to inappropriate transfer of funds
* [#440](https://github.com/allora-network/allora-chain/pull/440) Remove parallelization to avert nonuniform executions between hardwares

## v0.2.14

* Added many new queries
   * [#430](https://github.com/allora-network/allora-chain/pull/430)
   * [#399](https://github.com/allora-network/allora-chain/pull/399)
   * [#353](https://github.com/allora-network/allora-chain/pull/353)
* Added confidence interval to network inference query
   * [#402](https://github.com/allora-network/allora-chain/pull/402)
* New actors are incorporated more smoothly instead of ignored then included in their next round
   * [#420](https://github.com/allora-network/allora-chain/pull/420)
* Created fuzzer so anyone can help find vulnerabilities (tell them how they can submit)
   * [#407](https://github.com/allora-network/allora-chain/pull/407)
* Parallelized tests for faster CI
   * [#394](https://github.com/allora-network/allora-chain/pull/394)
* Formally adopted gitflow with improved contributor experience
* Simplified nonce semantics
   * [#416](https://github.com/allora-network/allora-chain/pull/416)
* More reliable fetching of previous data
   * [#412](https://github.com/allora-network/allora-chain/pull/412)
   * [#409](https://github.com/allora-network/allora-chain/pull/409)
* Added validations for safer data ingress
   * [#398](https://github.com/allora-network/allora-chain/pull/398)
* Update forecast utiity function
    * [#382](https://github.com/allora-network/allora-chain/pull/382)
* Automatically expire stake removals instead of requiring a 2nd tx
   * [#362](https://github.com/allora-network/allora-chain/pull/362)
* Added min bound on epoch length to prevent topics from hogging too many resources
   * [#376](https://github.com/allora-network/allora-chain/pull/376)
* Add restore from snapshot
   * [#352](https://github.com/allora-network/allora-chain/pull/352)
* Version updates to all docker files and deployment scripts
* Removed duplicate computations for increased efficiency
   * [#367](https://github.com/allora-network/allora-chain/pull/367)
* Bugixes, improved error handling, way more coverage, and simplifications including:
   * [#327](https://github.com/allora-network/allora-chain/pull/327)
   * [#318](https://github.com/allora-network/allora-chain/pull/318)
   * [#401](https://github.com/allora-network/allora-chain/pull/401)
    * [#272](https://github.com/allora-network/allora-chain/pull/272)
* More efficient state pruning
   * [#319](https://github.com/allora-network/allora-chain/pull/319)
* Way more validator logging
   * [#305](https://github.com/allora-network/allora-chain/pull/305)
* Removed print statements so more efficient logging
    * [#298](https://github.com/allora-network/allora-chain/pull/298)
* Tuned default global parameters
* Self-delegation disallowed (security patch)
   * [#269](https://github.com/allora-network/allora-chain/pull/269)
* Added stress tests
* Improved [README](./README.md)
* Move expensive logarithm and exponentiation operations to offchain nodes when possible
   * [#258](https://github.com/allora-network/allora-chain/pull/258)


## v0.1.0

*Versions below `v0.2.14` were associated with our "Alpha Testnet" and "Edgenet" deployments, before formal versioning was adopted.*

