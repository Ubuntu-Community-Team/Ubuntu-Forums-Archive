---
title: "Keyboard no longer works"
date: 2007-12-09
forum: Apple PPC Users
---

### Post by ulissesroc on 2007-12-09
ibook g4. Some upgrades with feisty, then a reboot, then the keyboard does not longer work. I really would like to have, at least, my wesnoth savegame saved. Having not the feisty cd, what can I do? With extfsmanager with osx, or a name like this, I can't have it done, since it does not mount the partition.

Thanks

---

### Post by guidop on 2007-12-09
1) Did you use the version of ext2fsx corresponding to your version of OS X?
 - Version 1.3 works for me under Mac OS 10.3.9
 - I haven't tried the later dev version for Tiger.

2) Can you use Os X to download and burn a Feisty PPC live (desktop) CD?
- You should be able to get it to boot and run on your iBook.  You should be able to mount your Ubuntu ext3 partition and save your file to an external drive, or even mail it to yourself if it's not too large.
- If you can't mount your Ubuntu ext3 partition from the live CD, I suspect something far more serious is wrong with that file system partition.

---

### Post by ulissesroc on 2007-12-10
yes, i will burn the live cd, as a last chance (damn it, I forgot the original one in amsterdam).

I am using the 1.1.3, downloaded from their site. I should maybe try the last beta, to see if the problem is fixed.

I was compiling battle for wesnoth when the ibook got freezed. And then nothing more.

But I was compiling it wo sudo, I think

---

### Post by guidop on 2007-12-11
I don't know how big a project the Battle for Wesnoth is to compile, is it possible that you used up all the free space on your Linux disk partition?

That is one of the few non-administrator level actions I have seen bring down a Unix (Solaris) box.  I expect it might do the same to Linux if you run out of space on the root partition.

If you did run out of space, you might be able to recover your install by mounting your partition and deleting the wesnoth files, and maybe check /tmp/ and /var/log/, too.

---

