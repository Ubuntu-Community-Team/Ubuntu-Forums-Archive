---
title: "ext4 Birth times"
date: 2012-05-23
forum: Any Other OS
---

### Post by qyot27 on 2012-05-23
Support for exposing these to stat was added back in 2010, if I recall.  In the mailing list entries, it also refers to some of the other pieces of the system that had been updated to pass this information through and allow stat to populate that field.

But even though I've tested several distros, none of them exhibit this ability...despite having the right version (or higher) of coreutils, and ostensibly the underlying libraries.

My question is whether anyone knows of a distro that does actually come with this ability out of the box.  So far the only one that I've found that can display a value in the Birth field is Cygwin, but that's not ext4 (and neither is it a Linux distro).  I've tried with Fedora, Archbang, versions of Ubuntu that finally had the right coreutils version...they all show the Birth time field, but it's blank.

I mean, it is possible to get at the data the hard way ( *sudo debugfs -R 'stat <inode>' /dev/sdaX* ... it's the 'crtime' portion), but beyond the initial extra step of grabbing the inode number from stat and then using it above, debugfs shows the result in a separate text-mode output, AND you still have to correctly convert into proper nanoseconds.

---

