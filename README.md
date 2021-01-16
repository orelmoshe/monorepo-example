# monorepo-example

<img src="README.png" alt="Objective" style="width: 100%;"/>

---

# Monorepo vs. polyrepo

Monorepo means using one repository that contains many projects, and polyrepo means using a repository per project.

---

## Introduction

### What is monorepo?

Monorepo is a nickname that means "using one repository for the source code management version control system".

- A monorepo architecture means using one repository, rather than multiple repositories.

- For example, a monorepo can use one repo that contains a directory for a web app project, a directory for a mobile app project, and a directory for a server app project.

- Monorepo is also known as one-repo or uni-repo.

### What is polyrepo?

Polyrepo is a nickname that means "using multiple repostories for the source code management version control system".

- A polyrepo architecture means using multiple repositories, rather than one repository.

- For example, a polyrepo can use a repo for a web app project, a repo for a mobile app project, and a repo for a server app project.

- Polyrepo is also known as many-repo or multi-repo.

---

## Tooling

### Bazel

[Bazel](https://github.com/bazelbuild/bazel) is a fast, scalable, multi-language and extensible build system. Bazel only rebuilds what is necessary. With advanced local and distributed caching, optimized dependency analysis and parallel execution, you get fast and incremental builds.

Bazel requires you to explicitly declare your dependencies for each 'target' you want to build. These dependencies can be within the same Bazel workspace, or imported at build time via say git - there's no need to have all the files directly in your repo.

The nice thing is you can declare the commit id or file hash for the dependency you're importing to make sure you're getting what you expect, and keep Bazel's reproducibility properties.

### Lerna

[Lerna](https://github.com/lerna/lerna) is a tool that optimizes the workflow around managing multi-package repositories with git and npm.

---

## Monorepo scaling

### Monorepo scaling problem

Monorepo scaling becomes a problem when a typical developer can't work well with the code by using typical tools such as vanilla git.

- Monorepo scaling eventually becomes impractical in terms of space: when a monorepo grows to have more data than fits on a developer's laptop, then the developer cannot fetch the monorepo, and it may be impractical to obtain to more storage space.

- Monorepo scaling eventually becomes impractical in terms of time: when a monorepo grows, then a complete file transfer takes more time, and in practice, there are other operations that also take more time, such as git pruning, git repacking.
- A monorepo may grow so large contain so many projects that it takes too much mental effort to work across projects, such as for searching, editing, and isolating changes.

### Monorepo scaling mitigations

Monorepo scaling can be improved by:

- Some type of virtual file system (VFS) that allows a portion of the code to be present locally. This might be accomplished via a proprietary VCS like Perforce which natively operates this way, or via Google’s “G3” internal tooling, or via Microsoft’s GVFS.

- Sophisticated source code indexing/searching/discovery capabilities as a service. This is because a typical developer is not going to have all the source code locallly, in a searchable state, using vanilla tooling.

### Monorepo scaling metrics

Monorepo scaling seems to become an issue, in practice, at approximately these kinds of metrics:

- 10-100 developers writing code full time.

- 10-100 projects in progress at the same time.

- 10-100 packaging processes during the same time period, such as a daily release.

- 1K-10K lines of code

- 1K-10K versioned dependencies, such as Node modules, Python packages, Ruby gems, etc.
