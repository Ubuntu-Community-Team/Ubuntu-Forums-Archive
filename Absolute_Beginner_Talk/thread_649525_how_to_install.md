---
title: "how to install"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by nitsthegame on 2007-12-25
hi guys! Plz help me out

I am unable to install ubuntu 7.10 desktop i386. It hangs after completeion of installation and thus aborted.

I hav the following config:

Intel Core 2 duo 1.86 Ghz
Intel DG 965RY moterbard
380 GB SATA HDD
1 GB DDR2 RAM
Nvidia Geforce 8600 GT 512 MB video card
CD writer

I hav checked the hashes too

Wht could be the problem ???
plz solve as soon as possible

If possible can some1 also post the list of supported video cards

---

### Post by Rocket2DMn on 2007-12-25
What do you mean it hangs?  What is displayed on the screen?  When you reboot the computer do you get the GRUB boot menu?

---

### Post by Brandel Valico on 2007-12-25
[Brief list of Video Cards supported]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?")

Found an actual list of Ubuntu Video Cards. Thus I edited my post

---

### Post by nitsthegame on 2007-12-25
> **Rocket2DMn said:**
> What do you mean it hangs?  What is displayed on the screen?  When you reboot the computer do you get the GRUB boot menu?

i make the partitions and then say next

the installation completes and then it tarts preparing the pc  this is where it hangs and when i reboot it starts with win xp
no ubuntu

---

### Post by lgambett on 2007-12-25
Every time you power on a dual boot PC prepared with Ubuntu you should see the boot loader screen (the GRUB one). GRUB starts Ubuntu after a few seconds. Do you get the GRUB screen ? What happens next ? Do not mind of "supported video cards"; if you booted succesfully with the Live CD the card is OK to start Ubuntu.

---

### Post by bumanie on 2007-12-25
I would be tempted to boot the live cd and in terminal type 
sudo find/boot/grub/stage1
and see if there is any output. If there is no output, grub probably has not been installed for some reason. If there is an output, post the result and someone will tell you how to restore grub to its correct location.

---

### Post by nitsthegame on 2007-12-25
i hav not been able to boot using the live cd

i hav to first make temp files of ubuntu and then install

if i try to boot using the live cd it fails and goes to DOS mode

---

### Post by bumanie on 2007-12-25
I don't have any specific idea as to what could be causing this. What I can say is that
1) I have a computer savvy friend who is unable to get the live (gutsy) cd to boot on any of his seven computers - Why??? We don't know.
2) Some people who have not been able to boot/install with the live cd have had success with the alternate cd - it may be worth trying.
3) I assume your first boot device in your bios settings is cdrom - may be worth checking to make sure
4) If I understand one of your earlier posts correctly, you can (or at least were able to) get up to the install screen. If you can still get to there, you can access terminal  - Applications --> Terminal and try the above command.
If you can't get to that point, I have no other suggestion other than trying the live gparted cd and see what your partitions look like, ie sizes, file system type etc.
Sorry I can't be of more help.

---

### Post by Rocket2DMn on 2007-12-25
> **nitsthegame said:**
> i hav not been able to boot using the live cd

i hav to first make temp files of ubuntu and then install

if i try to boot using the live cd it fails and goes to DOS mode

Sounds like the alternate cd is for you.  You can download it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom.  Don't forget to check the md5sum:
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
Then burn the disc at a slow speed like 4x to prevent write errors, and use quality media if possible.
This cd doesn't have a live session but gives you a text based installer which is more stable and reliable than the live cd.  Let us know how this turns out.

---

