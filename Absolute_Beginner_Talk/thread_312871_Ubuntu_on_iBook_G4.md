---
title: "Ubuntu on iBook G4"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by vbbr on 2006-12-05
Hi,
Can someone please guide me on how I can start with Ubuntu?
Are there any installation instructions/guides for installing Ubuntu on iBook G4?:confused:  I would like to make a dual boot system.

Thanks!:)

---

### Post by Sef on 2006-12-06
If it's pre-intel, then download the PPC version.  If it is intel, then download the x86 version.  

To dual boot, there are two tutorials that are really good.

1) For install with the alternate version: [The Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/")

2) For install with the Live CD version: [Psychocats Installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by linear on 2006-12-06
An iBook G4 is PPC. The two tutorials are useful, but specific for non-Mac Intel. Some of the information does not apply.

Here's what I'd recommend. First read these:

[https://wiki.ubuntu.com/Installation/PowerPC](https://wiki.ubuntu.com/Installation/PowerPC) - (for Breezy, but some useful info)
[http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

Then:

0. Read up in the [Apple PPC Users]("http://www.ubuntuforums.org/forumdisplay.php?f=133") forum on any model specific quirks.
1. If you have an OS X installation you want to save, back up the OS X partition. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition the disk. Make two partitions, leave the first as free space and install or restore OS X to the second. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively.
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

---

