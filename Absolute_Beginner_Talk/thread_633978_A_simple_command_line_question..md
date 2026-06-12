---
title: "A simple command line question."
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by detroit/zero on 2007-12-07
I'm sure this has been done before, and probably done to death, but it would seem that I do not walk in the ways of the search bar and can't find anything about this specific question:

How do I do [anything] with a file in the command line when there is a space in the file/folder name?

For example:

Say I want to cd from my home directory into a folder named "My Files" I then type **$***cd My Files* into the command line, but get an error message to the effect of "*No such folder: My*". I'm then stuck going and renaming files and folders with an underscore rather than a space.

I tried using the wildcard *, but that leads to all sorts of confusion. Whatever comes after the wildcard is discounted, so "*My*Files"* is mixed up with, say, "*My Music*" or "*My Videos*", and hilarity then ensues (especially when renaming large groups of files).

I know it's a quick and painless answer, and I know I read it somewhere before, but I can't seem to find it to save my life.

Thanks for any help.

---

### Post by dje on 2007-12-07
try this ```
cd My\ Files
```. hth :)

---

### Post by jordanmthomas on 2007-12-07
Also, you can use quotation marks
```
cd "My Files"
```
or tab completion (which will fill in \ like above)

---

### Post by detroit/zero on 2007-12-07
Marvelous, marvelous.. The backslash did the trick. Thanks, dje.

I'm surprised that quotation marks didn't occur to me before this. I must need more coffee.

Thanks for the help, fellas..

---

