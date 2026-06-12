---
title: "need to get GRUB back"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-08-16
Just formatted the windoze partition on my computer. I assume GRUB was on this partition because now I am unable to find ubuntu, although windoze can see the drive.
Is there any way of reinstalling GRUB without having to reinstall ubuntu from scratch.
I am certain I did not interfere with the swap or ubuntu partitions.

---

### Post by sad_iq on 2007-08-16
This should work:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Steve1961 on 2007-08-16
Just boot with the live CD and mount your Ubuntu partition.  Then from a terminal:

sudo grub
root (hd0,1)   this must be the root partition of your ubuntu installation
setup (hd0)
exit

Just note that grub disk notation uses it's own method - hda1 is (hd0,0) and hda2 is (hd0,1), so amend this bit as necessary.  (hd0) is the location of the mbr on the first disk (where grub used to be).

---

### Post by Bachstelze on 2007-08-16
Everyone does it from the GRUB shell. Am I the only one who thinks it's much clearer to do this ?

```
sudo mount -t ext3 /dev/whatever /mnt
sudo install-grub --root-directory=/mnt /dev/whatever
```

---

### Post by Steve1961 on 2007-08-16
> **HymnToLife said:**
> Everyone does it from the GRUB shell. Am I the only one who thinks it's much clearer to do this ?

```
sudo mount -t ext3 /dev/whatever /mnt
sudo install-grub --root-directory=/mnt /dev/whatever
```

Err.... yep I think the grub shell method looks simpler to me.  Sorry.

---

### Post by bumanie on 2007-08-16
Excuse my ignorance, but what should I be writing where the 'whatever' is. I tried to do through terminal from the live cd and was told no command existed.
I love ubuntu but do find siome of the commands difficult. Am getting better slowly however.

---

### Post by amazingtaters on 2007-08-16
Couldn't he download a Super Grub live cd and boot to that to reinstall grub to his ubuntu partition?

---

### Post by bodhi.zazen on 2007-08-16
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

See the "quick start" option in that how-to ^^

---

### Post by Steve1961 on 2007-08-16
> **bumanie said:**
> Excuse my ignorance, but what should I be writing where the 'whatever' is. I tried to do through terminal from the live cd and was told no command existed.
I love ubuntu but do find siome of the commands difficult. Am getting better slowly however.

The 'whatever' is your ubuntu root directory, so from a terminal type:

sudo fdisk -l

Identify your partition /dev/hda1, hda2, sda1. sda2 or whatever it's called
> 
Couldn't he download a Super Grub live cd and boot to that to reinstall grub to his ubuntu partition?

Sorry, I've never used it so can't comment

---

### Post by billbog on 2007-08-23
Just to give my experience : I have had to reinstall GRUB after having to reinstall windows and as a beginner I found sad_iq 's thread worked for me.However in the command line :
find /boot//grub/stage1 make sure you leave a space after find or it wont work
I am sure that the advice given by the others was excellent but I personally could not understand it.I also could not burn the Super Grub live cd .
My dual boot is is to two separate hard drives.

---

