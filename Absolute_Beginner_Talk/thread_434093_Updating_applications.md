---
title: "Updating applications"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by chris1974 on 2007-05-05
I thought Ubuntu was supposed to be easy.

I can install applications via add/remove easily enough.  But the add/remove doesn't get me the most recent version of the software.  Is there a way to upgrade individual applications without hunting down source code and compiling?  I thought that was why we had the add/remove, so we didn't have to compile our own source code.

By the way, I am trying to update MonoDevelop, the current version of which is 1.2.3.1 (or 0.13, depending on which page of the website I look at).  I currently have 0.12.  According to their release notes, I need to compile some packages, none of which can be found in Synaptic.  Actually some are found, but they are old versions and I do not have the option of marking them for upgrade (the option is ghosted out).

Chris

---

### Post by christhemonkey on 2007-05-05
That is because the repositories are frozen (apart from security patches) every release.

This is what actually constitues the release, the freezing of patches, otherwise, each version would just continue to develop for ever....
See:
[http://en.wikipedia.org/wiki/Software_release_life_cycle](http://en.wikipedia.org/wiki/Software_release_life_cycle)
[http://en.wikipedia.org/wiki/Rolling_release](http://en.wikipedia.org/wiki/Rolling_release)

---

### Post by DSn0wMan on 2007-05-05
The repositories will usually give you the latest stable version available at the time of the last feature freeze. In other words if there is a new version of a particular application released after the Ubuntu release it wont be immediately available.

Sometimes you will find that within a few weeks of a particular application release it will show up in the backports repository. If it doesn't end up in the backports you can usually find an alternative repository or a .deb file to use somewhere.

Please keep in mind it does take some time to develop a proper package from a source release.

---

