---
title: "Mac-On-Linux doesn't work well with Fiesty Fawn"
date: 2007-06-13
forum: Apple PPC Users
---

### Post by bawalker on 2007-06-13
Hello all,

I'm writing because I've ran into issues with running MOL 0.9.72 on Ubuntu 7.04.  I went through installed a fresh copy of Ubuntu on my dual G4 which went fine.  I installed all the nessecary files such as autoconf, m4, libncurses, etc.  Then I extract the gzip file and do the following steps:

1.) ./autogen.sh
2.)  make (including the make menuconfig part)
3.)  make install
4.)  run molvconfig

Afterwards I immediately go and configure my /etc/mol/molrc.macos config file to show 256mb of memory and to adjust the disk devices that it can access.  I did have to temporarily disable the included molrc.net file because I was having tun0 errors, but for now I'm not worrying about that.  Instead when I run 'startmol' and have a Mac OS9 disc in there... the screen goes to full screen for a brief second but kicks me back out to the terminal window with an error that no SCSI devices could be found.  I watch and the CDRom is not even accessed during this time.  At first I figured it was a configuration error, so I checked and my molrc.macos file references

blkdev:         /media/cdrom0 -cd

I tried using paths like /dev/hd(x), /media/cdrom, you name it.  Nothing happened.  Does anyone have any ideas???

Brad

---

### Post by sulobanks on 2007-06-15
Could this have something to do with the inconsistency of fiesty recognizing ide drives as hd* or sd*?  I've seen several posts where people couldn't get other things (like external drives) to work because of feisty incorrectly recognizing their internal hd.(well, really insisting on sd rather than hd)  Not sure how recently you started using feisty, but it if it was a recent enough upgrade, you may not have noticed the change from hda to sda.  Might be worth a shot to verify that your system is calling your primary drive hda.

---

### Post by bawalker on 2007-06-15
Actually it appears that it not booting properly (mac on linux emulator software) is due to a bug.  The configurations I had of /dev/hda(x) were in fact correct.

---

