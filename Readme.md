# Mapio Manifest

This repository contains a manifest which describes all mapio repositories.

This is useful to have a common environment for all git projects.

The manifest can be used thanks to the **repo** tool.

## Repo

Repo is a tool created by Google that can manage many repositories.

### Install

You can install it manually like this:

```console
$ mkdir -p ~/.bin
$ PATH="${HOME}/.bin:${PATH}"
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo
$ chmod a+rx ~/.bin/repo
```

## Usage

To use the mapio manifest you must do:

```console
$ repo init -u https://github.com/pcurt/mapio-manifest -m mapio-manifest.xml
```

You can also init on a specific branch of the manifest by adding the `-b` option, like:

```console
$ repo init -u https://github.com/pcurt/mapio-manifest  -m mapio-manifest.xml -b mydevbranch
```

Then, to synchronize all repositories:

```console
$ repo sync
```

Be careful, repo sync will automatically put you in a head detached state for all repositories, you must go checkout your branch for each repositories if needed.

For instance, if you want to checkout master branch on mapio repositories, you can use the `repo forall` command like this:

```console
$ repo forall -g mapio -c git checkout master
$ repo forall -g mapio -c git pull
```

The `-g` options allows running the `forall` subcommand only on repository in the group `mapio` (see mapio-manifest file for more detail)

## Links

https://gerrit.googlesource.com/git-repo/

https://gerrit.googlesource.com/git-repo/+/HEAD/docs/manifest-format.md

https://source.android.com/setup/develop/repo