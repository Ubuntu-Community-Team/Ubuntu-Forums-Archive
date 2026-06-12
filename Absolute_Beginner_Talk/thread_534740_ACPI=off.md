---
title: "ACPI=off"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by netjess on 2007-08-25
I am trying to install KUBUNTU on a Compaq that is about 4 years old, I have 1GB SDRAM. I have to use acpi=off to boot the live cd for install.
 When I install I thought it would pass the same parameter to the HDD install but it didn't. I can not boot the the hdd without the parameter and the install gives no oportunity to pass parameters.

 Would someone tell me how to get to edit the boot params on my HDD?

 Thanks.

---

### Post by annda on 2007-08-25
to make the kernel option included when booting, you need to change one bootloader file

i assume you can boot into recovery mode only. once you have logged in type this:

```
nano /boot/grub/menu.lst
```

go to the most recent ubuntu kernel and in the line that starts with kernel add this at the end: acpi=off

ctrl+o to save, ctrl+x to exit. reboot. now you should be able to boot into ubuntu from grub.

---

### Post by southernman on 2007-08-25
Try doing it with grub by doing either:

sudo nano /boot/grub/menu.lst
gksudo gedit /boot/grub/menu.lst

look for a line that says:
# defoptions

It may have something added in that line, if so add to the end of the line
acpi=off (put a space between this option and the last)

if it doesn't have any options there already then add this to it:
=acpi=off (don't put a space between the first equal sign)

***This is what you'll really need after reading over your post again... ***

Chances are you'll need to quickly hit the escape key (ESC) when grub starts to load. After doing so, use the down arrow key to highlight the first boot option and push the "e" key to edit the line. Here you'll add the acpi=off with a space between the last option and this entry. I think you'll then hit the "q" key (to quit) and then the "b" key to proceed with booting.

HTH's

---

### Post by netjess on 2007-08-26
Thanks,
I continued to search after I made the original post and found the instuction to edit in GRUB at boot time:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) 

 I tried to add the "acpi=off" but I still get the error:

Int 14: CR2 f8000000 err 00000000 EIP c020c384 CS 00000060 flags 00010 stack: c00f7d50 c03f129b c0371d8c 00000002 c00f7d59 000f7d50 00000000 0000

 I get the same error when booting the live CD but not if I turn off ACPI.

 Any ideas how I can get my HDD install to boot?

---

### Post by netjess on 2007-08-26
FYI,
I tried updating my BIOS. Didn't help.

---

### Post by netjess on 2007-08-26
:popcorn:

 Success! I just kept trying to edit in different places.

 It seems adding the acpi=off only works at the end of the first line.

 :guitar:

---

### Post by southernman on 2007-08-26
Sorry for not being complete in my original suggestion. After adding the line to "defoptions" I should have instructed you to do "sudo update-grub"

I'm glad you were able to get it going in spite of. I can see the joy in your post! ;)

*atta boy pat on the back*

---

### Post by netjess on 2007-08-27
Thanks for the help. The posts did help me find the solution.

---

