---
title: "How to reset uername and password on laptop?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by lilceezer on 2006-07-12
I bought this iBookG4 at an estate auction with Ubuntu already as the operating system.  Which is why I don't know the username and password, nor do I have a clue on how to retrieve/ or ersae them.  I really need someone to help me please, and a BIG thanks in advance!

---

### Post by aysiu on 2006-07-12
Boot into recovery mode and then type ```
adduser lilceezer
``` Answer all the prompts (you won't see your password as you're typing it in--that's fine). Then ```
adduser lilceezer admin
reboot
```

---

### Post by lilceezer on 2006-07-12
Aysiu,

Thanks so much for the quick reply!   I am an infant to Appe/Mac PCs.  How exactly do I boot into recovery mode?  I rebooted and saw an option to press 1 for Linux, or c for  cd/rom.  Please help me....

---

### Post by cotcot on 2006-07-12
When you boot the computer you normally get a menu with a number of possibilities. Find something like this :
> Ubuntu, kernel 2.6.12-10-386 (recovery mode)
This is an example of a Ubuntu Breezy entry with kernel 2.6.12-10-386. The kernel number can be different. Important is that you see "recovery mode" between brackets. Select that one and you will get the possibility to enter the commands aysiu has given you.
If you do not see this possibility come back to the forum and we will try to find a solution for you. (Most likely using the liveCD).

---

### Post by aysiu on 2006-07-12
This is what cotcot is describing.

---

### Post by lilceezer on 2006-07-13
Thanks again Aysiu and Cotcot,

WHen my laptop reboots it says: Welcome to yaboot version 1.3.13.  What command should I enter?  I have never worked with Ubuntu before.

---

### Post by mcduck on 2006-07-13
> **aysiu said:**
> Boot into recovery mode and then type ```
adduser lilceezer
``` Answer all the prompts (you won't see your password as you're typing it in--that's fine). Then ```
adduser lilceezer admin
reboot
```

Instead of creating new user, I'd recommend just finding out the username for the existing user, and then replacing password for that user.

It's easier too:

1. Boot into recovery mode
2. run 'ls /home' to get the user name (every user has a home directory inside /home, and directory name is same as the user name).
3. run 'passwd username' to set the new password for this user (replace 'username' with the actual name you found out in last step)
4. run 'reboot' to reboot the machine

---

### Post by lilceezer on 2006-07-13
Thanks Mcduck,

But part of the problem is geeting my laptop to boot into recovery mode.  It keeps loading in yaboot version.

---

### Post by mcduck on 2006-07-13
> **lilceezer said:**
> Thanks Mcduck,

But part of the problem is geeting my laptop to boot into recovery mode.  It keeps loading in yaboot version.

I'm sorry, I can't help you with that as I'm using PC, not Mac, so I have no idea about yaboot..

---

### Post by cotcot on 2006-07-13
Yaboot seems to be something typically Mac. I do not know it.

I suppose you can run the install CD and have Ubuntu from the install CD running.
Than in terminal :
```
sudo su
mkdir apple pear
mount /dev/hda4 apple
mount /dev/hda1 pear
chroot apple /bin/bash
adduser lilceezer
adduser lilceezer admin
grub

```

You will get the grub prompt : grub>

Then :
```
root (hda0,3)
setup (hda0,0)
```

(hda0,3) can be another partition in your case. It should be the partition with your root directory on. (hda0,3) is the same as hda4. Yours can be different. With chroot you change the rootdirectory from the liveCD to the the partition in the hard disk.
(hda0,0) is the location for the bootloader ; in this case the MBR.
Reboot the computer without the install CD. This should give you the grub bootloader menu (with the recovery option as shown in the post of aysiu).
But you do not need it. You can boot the default and login as lilceezer and your password.

I have successfully checked this procedure on my PC2 (see signature) with the only difference that i did the setup to the floppy "setup (fd0)" instead of to the MBR "setup (hda0,0)". If you have a floppy you could try it first. Floppy in will give you grub bootloader menu. Floppy out will give you your yaboot.

This procedure supposes that ubuntu had been installed with grub. In that case you will find a file in /boot/grub/ called "menu/lst" with the menu entries.

Good luck

---

