---
title: "My XFS cannot build."
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Hxsrmeng on 2007-08-31
I obtained the XFS source codes from sgi, including linux-2.6-xfs and xfs-cmds.

what's the relationship between linux-2.6-xfs and linux-kernel source code?

Then I did
$ cd xfs-cmds
$ make

And I got:
echo "cmd builddirs"
cmd builddirs
([ -d /usr/src/linux-2.6.22.1/fs/xfs-cmds/SRPMS ] || mkdir -p /usr/src/linux-2.6.22.1/fs/xfs-cmds/SRPMS)
([ -d /usr/src/linux-2.6.22.1/fs/xfs-cmds/RPMS/i386 ] || mkdir -p /usr/src/linux-2.6.22.1/fs/xfs-cmds/RPMS/i386)
echo "=== Making cmds `date`"
=== Making cmds Thu Aug 30 23:23:37 EDT 2007
for d in attr acl xfsprogs dmapi xfsdump; do \
                echo "== Building $d"; \
                ( cd /usr/src/linux-2.6.22.1/fs/xfs-cmds/$d && ./Makepkgs ) || exit 1; \
        done
== Building attr
== clean, log is Logs/clean

== configure, log is Logs/configure

== default, log is Logs/default

== dist, log is Logs/dist
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/attr/build/attr-2.4.38.src.tar.gz
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/attr/build/tar/attr-2.4.38.tar.gz
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/attr/build/rpm/attr-2.4.38-0.src.rpm
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/attr/build/rpm/attr-2.4.38-0.i586.rpm
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/attr/build/rpm/libattr-2.4.38-0.i586.rpm
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/attr/build/rpm/libattr-devel-2.4.38-0.i586.rpm
== Building acl
== clean, log is Logs/clean

== configure, log is Logs/configure

== default, log is Logs/default

== dist, log is Logs/dist
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/acl/build/acl-2.2.44.src.tar.gz
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/acl/build/tar/acl-2.2.44.tar.gz
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/acl/build/rpm/acl-2.2.44-1.src.rpm
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/acl/build/rpm/acl-2.2.44-1.i586.rpm
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/acl/build/rpm/libacl-2.2.44-1.i586.rpm
Wrote: /usr/src/linux-2.6.22.1/fs/xfs-cmds/acl/build/rpm/libacl-devel-2.2.44-1.i586.rpm
== Building xfsprogs
== clean, log is Logs/clean

== configure, log is Logs/configure
make: *** [cmds] Error 1

What's the problem? Thanks in advance.

---

### Post by kidders on 2007-09-01
Hi there,
The sources you've got almost look like Red Hat sources. :confused: In any case, there's not enough information here to even speculate as to the problem, I'm afraid. Are you certain all build dependencies are installed correctly? Perhaps you should take a look at the configure logs the output you posted seems to mention.

One thing I feel I should mention, since this is the Absolute Beginner Talk forum, is that building XFS kernel support & utilities from source is something that you really shouldn't be doing, unless you know enough about building software not to have to ask questions like this one. I mean _no offense_ by saying this, but ...
[LIST]
[*]Even a small mistake can lead to disaster. NB: A successful build does *not* mean you've made no mistakes.
[*]Assuming you don't make any mistakes, you may still provoke disaster, depending on how the XFS version you're compiling interacts with the kernel you've installed.
[*]You will presumably need to rebuild Ubuntu's kernel before attempting to use the software you're compiling, so the same caveats apply there.[/LIST]To answer your first question, and assuming that by "linux-2.6-xfs" you mean the XFS CVS tree, then there isn't really a direct relationship. In general, CVS builds of things are almost 100% guaranteed to be unstable, where the Linux kernel's XFS support is very reliable. Eventually, current CVS builds of XFS may make it into the kernel source tree, subject to various fixes, or with certain features removed.

Much of this post doesn't have anything to do with the questions you asked ... I'm sorry for that ... but given the title of this subforum, I didn't want to confine myself to a short sequence of glib comments. Please feel free to shout obscenities at me if you already know the following...
[LIST]
[*]You're toying with your OS's ability to read & write data accurately to/from your hard disks.
[*]You need a *very* good reason not to use your kernel's XFS support, and Ubuntu's approved XFS utilities.
[*]You also need familiarity with software building, and good instincts for the sorts of things that can go funny.
[*]To use the result in a commercial setting, you would need to have no hesitation in applying the word "guru" to yourself hehe.
[*]It's likely that Ubuntu is the wrong distro to be doing this sort of thing on anyway. If you do need your own XFS build, you might want to consider switching to a distro that doesn't assume you haven't customised it.[/LIST]Anyhow, now that I've said my piece (lol), I'd be more than happy to investigate your compile problems in more detail with you. I've never done this sort of thing on a binary distribution before ... have you discovered anything about how your XFS build would react to Ubuntu's periodic kernel updates?

---

