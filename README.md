# gbdefjj - Git-Based DiffEditor For JuJutsu

(I pronounce it _gee-bee-def-jay-jay_).

`gbdefjj` is a [diff-editor](https://docs.jj-vcs.dev/latest/config/#editing-diffs) for `jj`.
It creates a Git repo in `$right` and allows to interactively stage changes for the diff.
This is super handy for `j split`, `jj squash -i` and friends.

I didn't like the built-in diff-editor and was not satisfied with [hunk.nvim](https://github.com/julienvincent/hunk.nvim).
It works fine but I felt it was not as ergonomic as I was used to by using [Neogit](https://github.com/NeogitOrg/neogit).

[Katalin](https://www.knifepoint.net/~kat/kb-jj-patchedit.html) provided an interactive, patch-based approach.
Their post inspired me to create `gbdefjj`.

By default, `gbdefjj` will open Neogit (within Neovim).
The user then interactively stages hunks as if they wanted to select changes to be committed within Git.
But instead of committing, one simply closes Neovim and commits within `jj`.

## Setup

```
# ~/.config/jj/config.toml
[ui]
diff-editor = "/path/to/gbdefjj/gbdefjj"
```

Instead of Neovim+Neogit, one may use anything that allows to stage changes within a Git repo.
Simply dropping into the shell and running Git commands would do.
Setting `GBDEFJJ_EDITOR` will changed the default behavior.
A `git add -p`-based workflow is provided and can be invoked like this:

```
GBDEFJJ_EDITOR="git_add_p" jj split
```
