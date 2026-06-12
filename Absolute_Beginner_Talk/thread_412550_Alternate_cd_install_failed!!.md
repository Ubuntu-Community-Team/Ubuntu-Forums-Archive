---
title: "Alternate cd install failed!!"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by lamalex on 2007-04-18
So I finally convinced my family to let me install Ubuntu onto their Virus ridden pc, they've been using my laptop for a few months and like it, just never saw a reason to change until in the past week or so the pc has become so infected I took the power cord so that all of the Trojans couldn't keep mining for credit cards. To install I used the alternate install cd because I was going to set up an lvm however everything I have tried has failed; for some reason I can't get grub to install.

_System History_
The box used to have a RAID0, the RAID has since been broken and both disks fully formatted. I have the feeling this RAID is why GRUB will not install although that's just my guess.

_System Specs_
ASUS K8N4-E Deluxe
AMD Athlon 64 2800+
2x512mb DDR-PC3200 ram
2x160gb SATA hdd
nVidia 7600GT pci-e

_Partition Plan_
I had set up my partitions like this:
**LVM Group**
logical volume 1 -- 45gb /(root)
logical volume 2 -- 272.9gb /home

**/dev/sda**
/dev/sda1 -- 100mb /boot
/dev/sda2 -- 2gb swap
/dev/sda3 -- 157.9gb LVM

**/dev/sdb**
/dev/sdb1 -- 160gb LVM

Install went fine, went all the way through, but upon restart i get this error
> 
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER


That's where I am. I've tried reinstalling GRUB via the alternate cd but haven't been able to get it, I'm thinking maybe I'll pull out the cmos chip and reset the bios to clear out any leftover junk from the RAID0. Does that sound like a good idea? Can anyone help me figure out how to get GRUB onto my machine and start using it? This part is only fun for so long before it becomes a pain. Also: does anyone have a mirror for the supergrub site? It's been down and I'd like to give supergrub a try.

EDIT/CONCLUSION: The problem wasn't even grub, the problem was hardware related. I had forgotten that my mobo had a hardware RAID controller that the SATA drives were plugged into. I moved the over to the regular SATA controller and after some messing with lvm settings it worked! Now I'm updating and happy with my shiny new 260gb /home. It feels really good to win, thanks for your help everyone!

---

### Post by ajgreeny on 2007-04-18
Try using a live linux CD, it doesn't need to be ubuntu, if you need to download one specially try puppy, I know it works as I have used it myself.
Boot into the ubuntu/puppy live CD
open a terminal and run :
command:-
    "sudo grub"  (in puppy linux just "grub" seems to work)

then:
command:-
    "find /boot/grub/stage1"

replace the question marks in the following command with the output of the last command :
command:-
    "root (hd?,?)"
If you have more than one linux install, use the one that you want the grub to run from. [like : root (hdo,1) ,probably]
then:
command:-
    "setup (hd0)"  This will put grub on the first sector of your first disk, but you can put it where you like.  Generally this (hd0) is needed when you are dual booting with windows to put grub in place of the windows MBR.

and
command:-
    "quit"

Reboot

You could try doing this several times, putting grub on all disks.  Only the one that the bios is set to boot from will be used, so perhaps keep trying the different disks until you find something that will get you into the grub menu, and thus ubuntu.
Good luck.

---

### Post by lamalex on 2007-04-18
so in my situation root would be
```

root (hd0,3)

```
since my /(root) is on sda3?

---

### Post by leibowitz on 2007-04-18
> "find /boot/grub/stage1"

replace the question marks in the following command with the output of the last command :
command:-
"root (hd?,?)"

He said replace the "?" with the output from this command : "find /boot/grub/stage1"

I never used this, but it seems to be a pretty useful tip. In your case I suppose it will output hd0,0 because of your /boot partition but I'm really guessing here!

---

### Post by ajgreeny on 2007-04-18
Your sda3 will be just (hd0) as you just put grub on the disk, not on a separate partition of the disk.  Think if you put (hd0,3) nothing would happen as in any case it would be hd0,2 (grub counts from zero all the time).  But as liebowitz said, use the output, not your own version of it.

Just try them and see, I'm pretty sure you won't do any harm by having multiple grubs on the system, as only one will ever be read at boot, depending on how your bios is set.

---

