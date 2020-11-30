## README

STATUS: Pre-alpha, in design and prototyping phase.

### About

`tape.versions`

`deps.edn` versions to be used across subprojects.

### Usage

You should be familiar with Clojure's [Deps and CLI](https://clojure.org/guides/deps_and_cli).

#### Subproject deps

In the subproject `deps.edn` declare local dependencies, and for versioned
dependencies leave the coordinates empty. Ex:

```clojure
{:deps {me.raynes/fs {} ;; empty, omit :mvn/version "x.y.z"
        some/local   {:local/root "../local"}}}
```

#### Project-wide versions

In `versions/deps.edn` add your project-wide deps versions as overrides. Ex:

```clojure
:aliases
{:versions
 {:override-deps
  {me.raynes/fs {:mvn/version "1.4.6"}
   ...}}}
```

#### CLI run

Set `/versions` dir as your `CLJ_CONFIG`, and prepend the `versions` alias. Ex: 

```sh
cd <subproject>
CLJ_CONFIG=../versions clj -A:versions:<other>:<aliases> <and> <arguments>
```

### Credits

- [seancorfield](https://github.com/seancorfield) via
  [forum](https://ask.clojure.org/index.php/8440/equivalent-of-leiningens-managed-dependencies-in-deps-edn)

### License

Copyright © 2019 clyfe

Distributed under the MIT license.
