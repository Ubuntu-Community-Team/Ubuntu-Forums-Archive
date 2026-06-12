---
title: "HowTo check and repair HFSplus in Ubuntu"
date: 2008-05-09
forum: Apple Hardware Users
---

### Post by Rogério Brito on 2008-05-09
Hi,

I am the maintainer of Debian's hfsprogs package, which provides mkfs.hfs{,plus} and fsck.hfs{,plus} on both Debian and Ubuntu.

This "hack" is already well known (see [http://bugs.debian.org/436159](http://bugs.debian.org/436159)) and communicated to Apple on their channels.

I already have made a package with support for amd64 which I expect to reach Debian soon (as I, myself, use amd64 and I keep my external HDs formatted with HFS+).

It should reach Debian's experimental and if some Ubuntu person can, it can be backported to other distributions.

As you can see ([http://packages.ubuntu.com/hfsprogs](http://packages.ubuntu.com/hfsprogs)), hfsprogs is already available on Ubuntu, but it has bugs.

Unfortunately, the source code of Apple's programs is not exactly clean and I would like to initiate a project on Debian's Alioth (think of it as Debian's version of sourceforge) for the new upstream version that is team-maintained and which would consist of patches to the utilities of Apple to clean up miscoding, warnings, consistency, correctness and, perhaps, submit them upstream so that we can reduce our work in the future (and have a more solid filesystem for exchange of data between computers).

This system of producing patches has already proved to work extremely well in the case of the lame MP3 encoder (to the point where the patches were so complete that the whole initial tool was unnecessary).

So, if you want to help or know someone who currently can help maintaining the package, please get in contact with me. My e-mail address is listed on the hfsprogs package on Debian's site.


Regards, Rogério Brito.

---

