[![Actions Status](https://github.com/skaji/CI/workflows/linux/badge.svg)](https://github.com/skaji/CI/actions)

# NAME

CI - Get details about the current CI environment

# SYNOPSIS

    use Test::More;
    use CI qw(is_ci);

    plan skip_all => 'only in CI' if !is_ci;

    ...

    done_testing;

# DESCRIPTION

This module provides details about the current CI environment.
This is a perl port of [https://github.com/watson/ci-info](https://github.com/watson/ci-info).

# FUNCTIONS

Note that all functions are not exported by default. You can optionally export some functions by, for example, `use CI qw(is_ci);`.

## name

Returns a string containing name of the CI server the code is running on. If CI server is not detected, it returns `undef`.

## is\_ci

Returns `1/0`. Will be `1` if the code is running on a CI server, otherwise `0`.
Some CI servers not listed here might still trigger the `is_ci` to be set to `1`
if they use certain vendor neutral environment variables.
In those cases `name` will be `undef` and no VENDOR-CONSTANT will be set to `1`.

## is\_pr

Returns `1/0/undef` if PR detection is supported for the current CI server.
Will be true if a PR is being tested, otherwise false. If PR detection is not supported for the current CI server, the value will be `undef`.

## VENDOR-CONSTANT

Returns `1/0`.
Will be `1` if the code is determined to run on the given CI server, otherwise `0`.

Examples of vendor constants are `TRAVIS` or `APPVEYOR`. For a complete list, see the support table below.

# SUPPORTED CI TABLE

    Name                  Constant        is_pr
    --------------------- --------------- -------------
    AWS CodeBuild         CODEBUILD       Not supported
    AppVeyor              APPVEYOR        Supported
    Azure Pipelines       AZURE_PIPELINES Supported
    Bamboo by Atlassian   BAMBOO          Not supported
    Bitbucket Pipelines   BITBUCKET       Supported
    Bitrise               BITRISE         Supported
    Buddy                 BUDDY           Supported
    Buildkite             BUILDKITE       Supported
    CircleCI              CIRCLE          Supported
    Cirrus CI             CIRRUS          Supported
    Codeship              CODESHIP        Not supported
    Drone                 DRONE           Supported
    dsari                 DSARI           Not supported
    GitHub Actions        GITHUB_ACTIONS  Supported
    GitLab CI             GITLAB          Not supported
    GoCD                  GOCD            Not supported
    Hudson                HUDSON          Not supported
    Jenkins CI            JENKINS         Supported
    Magnum CI             MAGNUM          Not supported
    Netlify CI            NETLIFY         Supported
    Nevercode             NEVERCODE       Supported
    Sail CI               SAIL            Supported
    Semaphore             SEMAPHORE       Supported
    Shippable             SHIPPABLE       Supported
    Solano CI             SOLANO          Supported
    Strider CD            STRIDER         Not supported
    TaskCluster           TASKCLUSTER     Not supported
    TeamCity by JetBrains TEAMCITY        Not supported
    Travis CI             TRAVIS          Supported

# AUTHOR

Shoichi Kaji <skaji@cpan.org>

# COPYRIGHT AND LICENSE

Copyright 2019 Shoichi Kaji <skaji@cpan.org>

The MIT License (MIT)

Note that the actual CI information comes from [https://github.com/watson/ci-info](https://github.com/watson/ci-info),
whose license is MIT.
