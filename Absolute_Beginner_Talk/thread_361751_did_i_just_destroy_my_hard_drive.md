---
title: "did i just destroy my hard drive?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by autrui on 2007-02-14
hi,

i'm running ubuntu 6.06 on my laptop, along with windows xp pro.  took me a couple installs to get the dual-boot thing to work (had to install windows BEFORE ubuntu, otherwise windows went automatically to windows, no chance to pick ubuntu).  i use ubuntu for work/internet browsing, and winxp just for world of warcraft (i know, i'm lame).

so, i was just at my favorite torrent site (myspleen), and went a little crazy; i had about 9 instances of bittorrent running, when i decided to stop them all and install azureus, because things were getting laggy.  as i was closing them, i was starting to get weird error messages i had never seen before, something about not being able to find certain files or memory or something.  naturally, i ignored them, and continued closing the bittorrent windows.  i decided it was time for a reboot.

however, it didn't really shut down; it stalled somewhere, and eventually i did a "hard reset."  when i restarted, and chose ubuntu as my os (from the dual boot menu), i got the following error message:
```

booting 'ubuntu, kernel 2.6.15-27-386'

root (hd0,4)
file system type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-27-386 route=/dev/hda5 ro quiet splash
[linux-bzImage, setup=0x1c00, size=0x157860]
initrd /boot/initrd.img-2.6.15-27-386
[linux-initrd @ 0x1f979000, 0x6761acbytes]
savedefault

Error 29: disk write error

press any key to continue...

```
i pressed any key, and was brought back to the os-selection menu.  thereafter, if i try ubuntu or windows, i get the following: 

```

booting '<insert OS name here>'

error 18: selected cylinder exceeds maximum supported by bios

press any key..

```
pressing any key brings me back to the os selection menu.  i ctrl-alt-del, and the same thing happens over and over now.  the first time i select an os, i get error 29; thereafter, it's error 18.  

im always fine with wiping/reinstalling (maybe too fine with it?), but i really really would like to get my work files off first.  i can start it up using the live cd (6.06).  when i go to "system>admin.>disks" it opens, and thinks forever, never showing any disks (not the windows partition, not the linux partition, nothing).

did i fry my hard drive?  did i fry something else?  did i forget to plug in my mouse (or something similarly noobish)?

thanks.

autrui.

---

### Post by kerry_s on 2007-02-14
Try booting the livecd and in terminal run> sudo fsck /dev/hda

On your next install use a journaled filesystem instead, ext3,reserifs,(jfs> errors on the first try, but will finish on the second try),(xft> needs separate boot of ext2 or ext3 or reserifs)

---

### Post by PurplePenguin on 2007-02-14
Somebody else will see this and offer some expert advice, but in the meantime, maybe it's a good idea to run fsck and fix any filesystem problems.  It's probably easiest to do this by booting a live cd, going to the command line, and then running fsck on your drive.

```
sudo fsck /dev/hda1
```
replace /dev/hda1 if you've got your partition somewhere else

---

### Post by autrui on 2007-02-15
i'm not sure what that did, but it appeared to have worked!  computer boots normally, all my files appear to be ok.  THANKS SO MUCH!   my students would not like hearing i lost all their grades.  

autrui.

---

### Post by Kit Kat on 2007-02-15
:lolflag: I don't think you did! It just looks like it! Things are seldom what they look like!:)

---

### Post by autrui on 2007-02-15
hm.  so this morning, the power went out in my neighborhood; i went to sleep with the compy on, and woke up just in time to see the battery die.  when i started it today (at the local cafe), the problem was back.  

i'm running on the live cd now, but "sudo fsck /dev/hda#" didn't work this time.  when i press enter, this line shows up:

fsck 1.38 (30-Jan-2005)

and a blinking cursor is all that comes after.  indefinitely; no new command prompt.

if i try to run it on my ntfs partition, which previously produced unsuccessful, but inspiring results, now does this same thing; name of program, blinking cursor.

also, just before it worked the first time, i checked the partition editor, just for kicks, to see if it could find anything; it did, it saw all my partitions.  now, it doesn't see anything.  

any ideas?

thanks.

autrui.

---

