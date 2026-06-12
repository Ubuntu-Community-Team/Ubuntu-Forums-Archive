---
title: "Triple booting 7, OSX, and 9.10 using rEFIt"
date: 2009-10-15
forum: Apple Hardware Users
---

### Post by metroidnemesis13 on 2009-10-15
I installed rEFIt and got it to recognize all my partitions except linux.  I know I installed it because I accessed it through grub at one point but I don't want grub because I don't like having 2 menus.  How do I add an icon\link to rEFIt to let me boot into ubuntu?  I already have windows 7 and os x.

---

### Post by Bachstelze on 2009-10-15
You can't. rEFIT cannot boot Linux directly.

---

### Post by phidia on 2009-10-15
I don't have much experience with rEFlt either but I'm looking to learn more.
There is a website [here]("http://refit.sourceforge.net/") that seems pretty comprehensive. Hope that's useful.

And look at the section [here]("http://refit.sourceforge.net/doc/c2s2_startos.html") on booting an OS from rEflt.

---

### Post by mabovo on 2009-10-15
> **phidia said:**
> I don't have much experience with rEFlt either but I'm looking to learn more.
There is a website [here]("http://refit.sourceforge.net/") that seems pretty comprehensive. Hope that's useful.

And look at the section [here]("http://refit.sourceforge.net/doc/c2s2_startos.html") on booting an OS from rEflt.

It seems that rEfit doesn't work well with OSX 10.6.
I'm sing triple booting OSX10.6, Windows 7 Ultimate and Karmic 9.10 on MacBook2,1.

I've reinstalled rEfit a couple of times but to show the menu optins on screen I have to press "ctrl-D" if not the OSX10.6 (Snow) comes first without sign of the installed rEfit.

??????

---

### Post by metroidnemesis13 on 2009-10-15
Yeah I looked at those pages, they don't seem to be much help for my issue.  I can get 10.6 to boot by the way.  Can Ubuntu 9.10 actually restart a second generation unibody aluminum macbook properly?  Did they fix that?

---

### Post by Bachstelze on 2009-10-16
> **metroidnemesis13 said:**
> Yeah I looked at those pages, they don't seem to be much help for my issue.  I can get 10.6 to boot by the way.  Can Ubuntu 9.10 actually restart a second generation unibody aluminum macbook properly?  Did they fix that?

Yeah, it works in Karmic.

---

### Post by mabovo on 2009-10-16
Snow/sda2, 7/sda4 and Karmic/sda3 working pretty good on MacBook2,1.

When booting rEFIt display the Apple, GRUB2 and GRUB icons. 

I don't know how to remove the third "allien" icon !

---

### Post by phidia on 2009-10-17
From this [wiki efi]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface")

> # Linux has been able to use EFI at boot time since early 2000, using the elilo EFI boot loader or, more recently, EFI versions of GRUB.[13]

---

### Post by metroidnemesis13 on 2009-10-17
So would I have to set up two separate grub boots, one to boot windows and one to boot ubuntu?  My goal is to get 3 icons to show up in refit so i can click on ond and have it send me directly into the os.

---

### Post by Bachstelze on 2009-10-18
> **metroidnemesis13 said:**
> So would I have to set up two separate grub boots, one to boot windows and one to boot ubuntu?  My goal is to get 3 icons to show up in refit so i can click on ond and have it send me directly into the os.

As I said, you can't do that. You'd have to use elilo or an EFI-enabled GRUB instead of rEFIt.

---

### Post by metroidnemesis13 on 2009-10-18
Forgive me for being dumb but I don't mess with bootloaders much.  How would I go about doing that?  Do you have some advice?

---

### Post by johnyo12345 on 2009-11-04
You don't have to mess around with grub etc, and whoever said refit can't boot linux is wrong.

I'm currently triple booting os x 10.6, windows 7, and 9.04 using refit, and all 3 come up with a nice little icon when i boot up. There are just a couple basic steps that need to be done. It sounds like you had no problem with windows or mac using refit. In order to get ubuntu to work, I would recommend the following:

1. make sure that the windows partition is the last partition on your disk (~sda4)
2. install ubuntu as before, but in the very last step, right before you click 'finish', click on 'advanced' then check 'use bootloader' and scroll down to disk 3 or wherever you put ubuntu.

This has worked fine for me several times. If it doesn't work leme know and I'll try to help out. This works for ubuntu 9.10 as well, but instead of the penguin icon on REFIT it showed up as a 'legacy operating system.' It still boots but no penguin icon. I'm kinda OCD... so I wiped it and reinstalled 9.04. But yea I hope this works for you!

---

### Post by metroidnemesis13 on 2009-11-04
Somehow I got the three icons to appear.  Now when I boot Ubuntu or Windows 7 it boots into GRUB.  is there a way to eliminate or bypass grub and have the windows icon boot to windows and Ubuntu boot to Ubuntu?

---

### Post by patg7590 on 2010-03-28
sorry to dig up an old thread...

did this get resolved? I'm having the same issue. I'm only able to boot osx atm. Working on it. Just wondering if there was any progress on this?

---

### Post by CJN on 2010-03-28
The specifics depend on the versions of windows OS and ubuntu OS that you are using, but in general get all three installed (OS X should be there already) and make sure you can boot windows, while installing ubuntu make sure you put the bootloader in the / partition wherever that turned out to be for you, then in order to get refit to play nice you should do the following: 

( In this example I assume your disk is /dev/sda , default for macbooks,   and your root partition is /dev/sda4 , adapt these if necessary! )  
1) Download an Ubuntu Live CD ( see [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)   ) and burn the ISO to CD.
 2) Boot your macbook from the CD (hold option key at startup if you   don't have rEFIt)
 3) Open a terminal, mount your original root partition
 sudo mkdir /mnt/root
sudo mount -t ext4 /dev/sda4 /mnt/root 
4) Find the correct package for your architecture on [http://packages.debian.org/sid/gptsync](http://packages.debian.org/sid/gptsync)   and download it to somewhere under /mnt/root/
 5) Set up /proc and /dev
 sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev 
6) Chroot into your original system, you're now in your own system.
 sudo chroot /mnt/root /bin/bash
7)  Install the package downloaded in step 4
 sudo dpkg --install gptsync*deb
8 ) Run gptsync on the affected disk
 sudo gptsync /dev/sda
9)  Reinstall grub (this shouldn't overwrite rEFIt, but you can keep a  copy  of rEFIt on CD if you're concerned)
 sudo grub-install /dev/sda
10)  reboot, the system should be able to boot again now

---

