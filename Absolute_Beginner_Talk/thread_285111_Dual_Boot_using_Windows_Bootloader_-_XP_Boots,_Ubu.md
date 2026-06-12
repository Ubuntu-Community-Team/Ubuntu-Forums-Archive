---
title: "Dual Boot using Windows Bootloader - XP Boots, Ubuntu Won't"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by myounce on 2006-10-26
Here's my situation:  WinXP installed on /dev/hda1, Ubuntu and GRUB on /dev/hda2.  I've got c:\boot.ini modified and a copy of the Linux boot sectors in c:\ubuntu.bin.

Here's what happens when I boot:  Windows bootloader opens and gives me the option of going into XP or Ubuntu.  If I choose XP, everything works.  If I choose Ubuntu, I just get taken to a "grub>" prompt.  Am I missing a GRUB configuration file somewhere?  What do I need to get this working properly?

Thanks!

---

### Post by gn2 on 2006-10-26
Maybe you could do it another way, by either of the methods in this thread:  [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by myounce on 2006-10-26
I don't have two hard drives to work with.

---

### Post by doobit on 2006-10-26
> **myounce said:**
> Here's my situation:  WinXP installed on /dev/hda1, Ubuntu and GRUB on /dev/hda2.  I've got c:\boot.ini modified and a copy of the Linux boot sectors in c:\ubuntu.bin.

Here's what happens when I boot:  Windows bootloader opens and gives me the option of going into XP or Ubuntu.  If I choose XP, everything works.  If I choose Ubuntu, I just get taken to a "grub>" prompt.  Am I missing a GRUB configuration file somewhere?  What do I need to get this working properly?

Thanks!

It sounds like you are missing the boot/grub/menu.lst file, or it is misconfigured. You can boot with the liveCD, mount hda2 and look to see if it is there. If it's there, then you probably need to edit it to put the correct hard drive locations in. If it's not there, then you may need to run grub configure again or find a copy here on the forum and manually configure it to work for your situation. 

BTW, I would have installed grub on the MBR relied on the grub bootloader to do everything instead of trying to modify the Windows boot.ini.

---

### Post by myounce on 2006-10-26
Yeah, I had GRUB in the MBR for awhile, but the wife and kids were starting to rebel.  Not so much about GRUB itself, but when you'd try to restart Windows, it would hang.  If you've got a solution for that, I'd love to hear it, because this little adventure of booting from the Windows bootloader has turned into a pain in the arse!

I'll hunt for the menu.lst file tonight.

---

### Post by doobit on 2006-10-26
> **myounce said:**
> Yeah, I had GRUB in the MBR for awhile, but the wife and kids were starting to rebel.  Not so much about GRUB itself, but when you'd try to restart Windows, it would hang.  If you've got a solution for that, I'd love to hear it, because this little adventure of booting from the Windows bootloader has turned into a pain in the arse!

I'll hunt for the menu.lst file tonight.

My wife didn't like it too much either, but I set Windows as the default, and shortened the time to two seconds. She hardly even notices anymore.

---

### Post by Sef on 2006-10-26
> Yeah, I had GRUB in the MBR for awhile, but the wife and kids were starting to rebel. Not so much about GRUB itself, but when you'd try to restart Windows, it would hang.

Sounds like you had bad GRUB.  I have had dual boots and never had that problem.

---

