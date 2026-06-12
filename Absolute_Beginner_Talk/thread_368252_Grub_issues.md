---
title: "Grub issues"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by pwrntspd on 2007-02-23
Ok so i loaded Ubuntu Edgy on this old pc of mine, its the only thing on the hard drive.  I got all the way through the installation (had some trouble with the live cd so i used the alternate install) and had no issues, but when i went to boot it after installing Post data only gets to 

GRUB loading stage 1.5.

GRUB loading please wait...

and thats it, i dont know if its frozen or what but nothing happens.
Can someone please help? Or give me an idea of whats wrong?

---

### Post by ed-j on 2007-02-23
> **pwrntspd said:**
> Ok so i loaded Ubuntu Edgy on this old pc of mine, its the only thing on the hard drive.  I got all the way through the installation (had some trouble with the live cd so i used the alternate install) and had no issues, but when i went to boot it after installing Post data only gets to 

GRUB loading stage 1.5.

GRUB loading please wait...

and thats it, i dont know if its frozen or what but nothing happens.
Can someone please help? Or give me an idea of whats wrong?

Caution: Reply from Novice!

What sort of PC is it? Does it have a graphics card? What sort of monitor are you using?

I might be able to give you an idea or two with a few more details.

---

### Post by xyz on 2007-02-23
Would this help:
[FAQ: MY system froze at GRUB!]("http://ubuntuforums.org/showthread.php?t=2689")
[GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors")
From what I can gather, there is something missing in your /boot partition that grub is trying to find but can't.

---

### Post by pwrntspd on 2007-02-23
> **ed-j said:**
> Caution: Reply from Novice!

What sort of PC is it? Does it have a graphics card? What sort of monitor are you using?

I might be able to give you an idea or two with a few more details.

Its a pIII 500 mhz, 352mb ram, it has a graphics card, some old nvidia 16mb card realll old, but it seems to work fine.  The monitor is viewsonic CRT
btw its a powerspec computer (microcenter brand)

---

### Post by ed-j on 2007-02-23
> **pwrntspd said:**
> Its a pIII 500 mhz, 352mb ram, it has a graphics card, some old nvidia 16mb card realll old, but it seems to work fine.  The monitor is viewsonic CRT
btw its a powerspec computer (microcenter brand)

Hi !

I'm a Novice and you may need some other advice, but, I think Edgy 6.1 may be a bit much for such a system? As a primary suggestion I would say you might need to try running Ubuntu 5.1 (Breezy Badger). However, don't be too hasty as you might get some more detailed advice on this. Best I can do . Good luck!

---

### Post by pwrntspd on 2007-02-23
> **ed-j said:**
> Hi !

I'm a Novice and you may need some other advice, but, I think Edgy 6.1 may be a bit much for such a system? As a primary suggestion I would say you might need to try running Ubuntu 5.1 (Breezy Badger). However, don't be too hasty as you might get some more detailed advice on this. Best I can do . Good luck!

actually im trying to get Xubuntu 6.1 working, alot lighter on the pc than Ubuntu
but i think i know the problem
in post data it says the harddrive is running in CHS mode for windows rather than LBA for linux....now i just need to fix that...any ideas?

---

### Post by Duck2006 on 2007-02-23
Boot the system up with the live cd
Reinstall grub by, 

applications=>accessories=>terminal

type
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit

close the terminal
reboot

This sould setup grub for you.

---

### Post by ed-j on 2007-02-23
> **pwrntspd said:**
> actually im trying to get Xubuntu 6.1 working, alot lighter on the pc than Ubuntu
but i think i know the problem
in post data it says the harddrive is running in CHS mode for windows rather than LBA for linux....now i just need to fix that...any ideas?

I'm afraid I don't even know what CHS and LBA modes are? When I install a version of Ubuntu I get the installation menu to erase the complete lba hd0 , or something? I don't try to specify in which mode it will run, install or operate. Best I can do again.  :-) EDIT: Thanks Duck2006!

---

### Post by pwrntspd on 2007-02-23
> **Duck2006 said:**
> Boot the system up with the live cd
Reinstall grub by, 

applications=>accessories=>terminal

type
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit

close the terminal
reboot

This sould setup grub for you.

Yeah duck i tried that three times...still didnt work...

---

### Post by Patrick K on 2007-02-23
CHS Cylinders-Heads-Sectors
LBA  Logical Block Addressing

These are set in the system BIOS. I think CHS uses the actual geometry of the drive. LBA provides a translation of the geometry so large drive can be used. I don't know much about them except large drives (over 8GB, I think) should use LBA. I've never change these setting on a drive that has been formatted, so I don't know if it is a good idea or not. I suspect not. Sorry I can't be more of more help. I'd bet Wikipedia has a bunch on info on both.

---

### Post by Duck2006 on 2007-02-23
From the live cd

applications=>accessories=>terminal

sudo fdisk -l

and post the out put here

---

### Post by wesley_of_course on 2007-02-23
Wesley here ;

        Might help ?!?!?!?!?

          [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Duck2006 on 2007-02-23
The post that
> Wesley here ;

Might help ?!?!?!?!?

[http://users.bigpond.net.au/hermanzo...bDiskPage.html](http://users.bigpond.net.au/hermanzo...bDiskPage.html)

Would be the way i would go.

---

### Post by pwrntspd on 2007-02-23
Alright well thanks for all the help guys.  I fixed it.  Found out my boot partition was too large...whoops...also had to manually set the harddrive to LBA in the bios. After that i reinstalled xubuntu and everything works fine!  Thanks for all the help.

\\:D/

---

