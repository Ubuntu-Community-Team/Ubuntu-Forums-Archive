---
title: "[SOLVED] Grub looping"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Speedoo on 2007-08-27
Hi all,
I've been running Feisty on my laptop without problems for a few months now.  Today, however, I discovered I have no wireless internet access.  Being from a Windows background, and new to Linux, my first impulse was to reboot.  When I got to the GRUB loader screen, I selected Ubuntu, only to have my computer restart and again present the GRUB screen.  No matter which option I select, I get returned to the GRUB screen.  I'm unable to log in to Ubuntu, either standard, recovery, or previous kernel version, and also can't log into Windows XP (I'm posting this from my hardwired desktop machine.)  Please help!

---

### Post by KIAaze on 2007-08-27
Can you boot from the Live-CD?
This might help you fix the problem, because right now it looks like something is wrong with /boot/grub/menu.lst.

---

### Post by Ubuntized! on 2007-08-27
Did you messed up any file in the root directory?

---

### Post by stevebakerj on 2007-08-27
> **Speedoo said:**
> Hi all,
I've been running Feisty on my laptop without problems for a few months now.  Today, however, I discovered I have no wireless internet access.  Being from a Windows background, and new to Linux, my first impulse was to reboot.  When I got to the GRUB loader screen, I selected Ubuntu, only to have my computer restart and again present the GRUB screen.  No matter which option I select, I get returned to the GRUB screen.  I'm unable to log in to Ubuntu, either standard, recovery, or previous kernel version, and also can't log into Windows XP (I'm posting this from my hardwired desktop machine.)  Please help!

Might be worth downloading Super Grub:

[http://supergrub.forjamari.linex.org/?section=features](http://supergrub.forjamari.linex.org/?section=features)

to fix your prob and have as a standby for future use.

---

### Post by Speedoo on 2007-08-27
Thanks Steve,
Super Grub did the trick (although I must say the documentation is akin to learning a foreign language!)
I've got Feisty up and running again, but I'm afraid to reboot!  I plan to keep it running until I HAVE to reboot for some reason, then if the Grub loader still doesn't work, I can get into it with Super Grub again.  I did look through the menu.lst, but can't see anything wrong.

---

### Post by KIAaze on 2007-08-28
Does your GRUB display this at startup:
> Press enter to boot the selected OS, or 'e' to edit the
    commands before booting, or 'c' for a command-line.


If "e" or 'c' work, you could try entering the necessary commands to boot up manually the next time you are forced to reboot.
If you find one that works, putting it into menu.lst should work too I think.
Otherwise there's something really wrong with Grub.

For available Grub commands, see:
[http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")

---

