---
title: "grub in MBR - or is it?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-04-24
I have installed Linux and all is fine except I am unable to boot other distros through the Grub by chainloading, configfile, or just plain copying there kernel codes form menu.lst to the boot distro menu.lst. How do I know that Grub is in the MBR as it should be (as I am told)? How can I move it there or install it there?

---

### Post by NiBu on 2007-04-25
Is ubuntu your only os running on pc? Nomally you should see the grub menu at boot time if you have grub installed. When ubuntu boots normally it means that you have grub installed.
If not, you can install grub with grub-install command! Or you can update it with grub-update command! Here is some help for you: 
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

