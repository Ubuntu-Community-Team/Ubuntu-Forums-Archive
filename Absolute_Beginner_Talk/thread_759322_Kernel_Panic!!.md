---
title: "Kernel Panic!!"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Lupurus on 2008-04-19
Hi, 
I'm having the following error when I try to boot Gutsy:

" Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

I've been using Gutsy without problem for months now, and I suspect the problem arose when I had to turn off the computer in the middle of an update.

I've seen this thread: [http://ubuntuforums.org/showthread.php?t=576087](http://ubuntuforums.org/showthread.php?t=576087)

And I wouldn't be surprised if it worked for me. Problem is, I can't mount my hard drive to change anything! (I'm using the most recent LTS live cd).

sudo fdisk -l comes up with nothing at all, and plain ls only lists 'desktop'.

Furthermore, since I started using the live cd, (I haven't made any changes to anything) I can't even use my vista partition anymore!

When I turn on the computer, I get the toshiba loading screen, then grub starts to start up... and then I'm back at the toshiba screen over and over. 

My computer is a toshiba sattelite laptop, though I don't think that's too relevant. 

Help?

---

### Post by warbread on 2008-04-19
Fdisk -l isn't going to give you anything unless you specify a drive to look at.  Try 'sudo fdisk -l /dev/sda'.  Then mount the etx3 partition.

---

### Post by Lupurus on 2008-04-19
Still nothing I'm afraid. I took fdisk's advice and tried it with /dev/hdb as well, but nothing.

---

### Post by warbread on 2008-04-19
That is bonkers.  What happens when you create a folder and just try mounting /dev/sda2 (or whatever you think your linux partition might be) to it?

---

### Post by Lupurus on 2008-04-19
Hm, I messed around with the tab-complete a bit though and tried sudo fdisk -l /dev/hda and that gave me```
Disk /dev/hda: 732 MB
...(let me know if this is useful and I'll transcribe it)
Disk /dev/hda doesn't contain a valid partition table

``` 
Does that mean anything?

---

### Post by Lupurus on 2008-04-19
Erm, linux noob. Dunno how to mount stuff without being explicitly told...

---

### Post by Lupurus on 2008-04-19
ok, figured out how to mount stuff to folders. I have no idea what the partition name is, so I tried a bunch of things (from hda1 to hda9 and sda1 to sda5) and none of them existed.

That is, it said "Mount: special device /dev/sda2 does not exist"

---

### Post by Lupurus on 2008-04-19
Well, I now know that that /dev/hda is just my cd. Do you think the gparted live cd could help find my hard drive/make grub work?

Also, my BIOS still sees my hard drive, if that means anything.

I hope my disk hasn't failed... O_O

Edit: I feel bad for posting over and over. I got grub to work! A gentoo live cd recognized my hard drive, so all is not lost.

---

### Post by warbread on 2008-04-20
Yes.  Gparted would work wonderfully, I think.  Why didn't I think of that before?

---

