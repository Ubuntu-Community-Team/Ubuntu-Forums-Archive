---
title: "Upgrade Nightmare"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by AcademyKP03 on 2007-10-22
**This post could be related to an Ubuntu bug filed at**: h [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Alright, hoping someone can post some direction on what I should do next ..... I upgraded to 7.1 from Fiesty ...... everything was going great, then it said it needed to reboot to complete the upgrade .... so I did ..... and then out of nowhere .... WHAM!  the familiar orange loading progress bar came up - but then I noticed it would only progress to about 1% and worse, it just sat there ... after 5 minutes of sitting there .... where I kept telling myself ... it was normal for the first time ..... I got the following:

     Check root = bootarg cat/proc / cmd line or missing modules, devices: cat / proc / modeule ls / dev

Alert! /dev/by-uvid/67f22f190ce9304622-839a-c01a44e423a4 does not exist.  Dropping to shell

BusyBox v.1.3 (debian 1:1.3 - 5ubuntu7) Built in shell (ash)

Enter 'help' for a list of built-in commands

(initramfs)

----------------------------------

what the hell?

I tried both recovery and super grub disk - with the later saying it succeeded and booting back up to the orange progress bar and then crashing again with the same message as noted below.

Any advice / direction would be greatly appreciated. 

Thanks

John

---

### Post by solar george on 2007-10-23
Boot into recovery mode (single user mode) - see if that works.

Post the root line of your /boot/grub/menu.lst
Can you remember which partition your root was on?

---

