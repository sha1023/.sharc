# .sharc

My toolbox for easy management and growth of bash aliases/functions.

---

## Installation:
1) Clone the repo to your favorite location. I assume that is $HOME.
2) Append the following code to your bashrc:
```bash
##source portable aliases
ShaMottoColor=$(tput setaf 2) # Green
source $HOME/.sharc/.sharc
```

---

## Usage:

This package is sort of self documenting the `sharc` command prints all comments that are prefixed by "###" and all aliases/functions not prefixed by "\_".

I've included some of my favorite aliases, but the package is really just meant to allow for easy modification and addition of aliases. There are also a few cute tools for editing particular commands on the fly:

### Essential Functions:

0) `sharc`: Summarize sHARC -- print available commands.
1) `esharc`: Edit SHARC -- scans the packages for the argument you feed it and then open the relevant alias file. With no arguments it opens all the alias files. (Make sure to know how to quit out of vim before using this.)
2) `grsharc`: GRep SHARC -- greps all alias files. It should understand all grep flags you think to feed it.

If you'd like to add some local aliases files that git won't nag you about, simply add the file extension ".local". I've added it to gitignore.

### Gratuitous Functions:

My favorite aliases included are:
1) `hcd`: Heat map CD -- with no arguments it dumps out the visit counts to different directories. With one argument (`hcd regex`) it cds into the most visited directory which matches `regex`. With two arguments (`hcd regex n`) it cds into the nth most most visited entry that matches regex. WARNING this is accomplished by overloading the cd command to store directory changes to a state file. if that makes you uncomfortable (It probably should.), you can find the overloaded cd for inspection or removal using the command `esharc cd`. Alternatively, all the relevant hcd utilities are in `./sharc/.nestedrc/hcdrc` you can simply delete the file.
2) `gac`: Grep All Code -- greps all code from the git root.
3) `egac`: Edit Grep All Code matches -- edits any files revealed by gac
4) `fgm`: Find Git Matches -- Finds files in your git directory that match the provided regex.
5) `efgm`: Edit Found Git Matches -- Edits the file in your git directory that matches the provided regex.
6) `motto`: change MOTTO -- Prefixes your command line prompt with your motto.

## Structure:

There is a controller file `.sharc/.sharc` it sources all files found in `.sharc/.nestedrc` ensuring to source the files in order of their depth in the directory tree.
This is to ensure that aliases can be reused by deeper levels.
If you would like to add another bash source file, simply add it to .nestedrc or one of its children directories.

`.sharc/.state` contains all files important to the sharc state (E.g. your personal motto). 
If .state does not exist it is created when .sharc is sourced.
