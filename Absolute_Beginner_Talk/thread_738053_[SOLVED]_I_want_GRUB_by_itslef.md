---
title: "[SOLVED] I want GRUB by itslef"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by barbedsaber on 2008-03-28
Ok, so I had a partiotned hard drive, with vista (shudders) and ubuntu (YAY!!) Cleared the vista partition, and installed XP, I made sure i picked the right partition. But, of course, I have the windows boot loader, and I need GRUB again, so I can choose ubuntu, but I don't want to install ubuntu again just grub. where do I get it, and how do I install it?

(I'm sure this has been asked before, and I did look, just not amazingly well)

all help appreciated.

---

### Post by bumanie on 2008-03-28
Do you both OSes on a single hard drive. Is xp now on the first partition?

---

### Post by TeoBigusGeekus on 2008-03-28
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I hope you find some answers.

---

### Post by Oldsoldier2003 on 2008-03-28
> **barbedsaber said:**
> Ok, so I had a partiotned hard drive, with vista (shudders) and ubuntu (YAY!!) Cleared the vista partition, and installed XP, I made sure i picked the right partition. But, of course, I have the windows boot loader, and I need GRUB again, so I can choose ubuntu, but I don't want to install ubuntu again just grub. where do I get it, and how do I install it?

(I'm sure this has been asked before, and I did look, just not amazingly well)

all help appreciated.

Use the  [SuperGrub Live CD]("http://supergrub.forjamari.linex.org/") there is an option there that will install Grub and automatically set you up for a Linux/windows Dual boot.

---

### Post by barbedsaber on 2008-03-28
As far as I know, xp is on the first partiton.

I can tell you that they are on 1 hard drive, I didn't want a complicated setup with 18 hardrives and 16 towers, to confusing. :lolflag:

---

### Post by BennBuntu on 2008-03-28
supergrub might help you out.

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

For when you can't install linux last

---

### Post by adelahunty on 2008-03-28
If you have a live CD, you can boot that to get to a desktop.  If you then get up a terminal (konsole or gnome-terminal, depending on which Ubuntu you're using), you can mount the drive and the Linux partition somewhere.  For example, if your Linux partition is on the second partition of the hard drive, something like this:
```
sudo mount -t ext3 /dev/sda2 /mnt
```

Change to that disk:
```
cd /mnt
```

Then, change the root partition to that drive:
```
chroot /mnt
```

From there, you have Grub at your mercy, and you should be able to install it.  At the very least, you should be able to get up the Grub interactive shell to play around with things, just by typing 'grub' at the prompt (or 'sudo grub' to be precise).  I'm away from a machine I can play with right now, otherwise I'd tell what to type to get grub installed...

The SuperGrub disk is a great one to have knocking about anyway - very useful!

For future reference, always install Windows first, then put on Linux, as the Windows bootloader will overwrite Grub every time.  But then, you've probably guessed that by now... :)

---

### Post by lswest on 2008-03-28
or you can do this:
boot into the liveCD
open a terminal
```

sudo grub
find /boot/grub/stage1
root [result of find]
setup [hdx]
```

the actual how-to is [here]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by barbedsaber on 2008-03-28
I new the ubuntu forum was great, but the speed that I was up and running again was amazing, I used a super grub disk (I thought it was called womthing like that.) anyway, thanks for all your help, it worked!
you guys rock :guitar:

---

### Post by bumanie on 2008-03-28
This is the traditional way to reinstall grub. Not sure if it will work as xp was installed after ubuntu. You may also have to edit your /boot/grub/menu.lst as grub probably has not made a reference to xp.You can try supergrub disc or you can boot the live cd and do it from there. Once booted, go to terminal
> sudo grub --> enter
> find /boot/grub/stage1 --> enter You should get an output of (hd0,1), if / of ubuntu is on the second partition
> root (hd0,1) --> enter [substitute (hdx,x) to match the numbers of your output 
> setup (hd0) --> enter
> quit
exit live cd and reboot
You may like to read this first it has heaps of information on grub
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

