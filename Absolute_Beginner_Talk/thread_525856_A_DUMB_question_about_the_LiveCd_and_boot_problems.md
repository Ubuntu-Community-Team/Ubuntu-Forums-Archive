---
title: "A DUMB question about the LiveCd and boot problems"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-08-14
Ok, so I have installed Ubuntu on my laptop and pretty much have as much stuff as I need going there for the time being.  A friend and I were talking and I told him I'd really like to put Ubuntu on an old desktop and perhaps go straight Windows for now on my laptop (limited memory).  I have been running Windows XP in a virtual machine in 7.04 when I needed it.

Anyway, he comes over today with a complete old system - PIII 500, 256 ram, Diamond Viper V770D agp video card.  So, I try to boot with the LiveCD so we can see if there is anything on the hard disk he may want prior to using the complete drive for Linux.  Well, if I select the 1st option to boot off the LiveCD, it comes up with a screen showing the Ubuntu logo and a progress bar that basically just moves back and forth.  After a while, it comes up with the following:
-
-
BusyBox v1.1.3 (Debian 1:1:1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands
-
/bin/sh/: can't access tty; job control turned off
(initramfs)
-
-

So, I did some looking in the forum and people were saying they got around this with noapic in the boot string, so I tried rebooting the CD, then pressing F6 so I could enter in more boot options,  I tried adding noapic to the boot string and got the same result.  Then I tried vga=771 and got the same result.  I tried both together and of course got the same error.  I have noticed that right when it starts the loading process when I use the default F1 option that message comes up briefly saying old bios and acpi must be forced.  Well, I'm kinda at the end of my knowledge base so far, so can someone give me some pointers to put me back on track?

Thanks!:)

---

### Post by Blutack on 2007-08-14
If when you edit the boot string you delete the quiet splash bits you will at least get lots of output when it all goes pearshaped.  Have you verified the disc is ok by the way (just on the offchance)?

---

### Post by anewguy on 2007-08-14
Duuuuuuooooo - I forgot turning off the splash, and of course since I used the CD in my laptop I assumed it was ok (dumb thing to do - 2 different drives now), so I'll give those a try and post back.  Thanks for helping out!:)

---

### Post by anewguy on 2007-08-14
Well, I'm seeing 2 errors right off the bat:

- the bios is old and you have to force apci
- the floppy drive must be wacky as it is returning errors and that it where the boot dies

Will be trying to find away around that - so far disabling in the bios and/or disconnecting both the power and the data cable still causes the error - and to think, there's no floppy in the drive!:)

---

### Post by EagleRock on 2007-10-21
> **anewguy said:**
> Ok, so I have installed Ubuntu on my laptop and pretty much have as much stuff as I need going there for the time being.  A friend and I were talking and I told him I'd really like to put Ubuntu on an old desktop and perhaps go straight Windows for now on my laptop (limited memory).  I have been running Windows XP in a virtual machine in 7.04 when I needed it.

Anyway, he comes over today with a complete old system - PIII 500, 256 ram, Diamond Viper V770D agp video card.  So, I try to boot with the LiveCD so we can see if there is anything on the hard disk he may want prior to using the complete drive for Linux.  Well, if I select the 1st option to boot off the LiveCD, it comes up with a screen showing the Ubuntu logo and a progress bar that basically just moves back and forth.  After a while, it comes up with the following:
-
-
BusyBox v1.1.3 (Debian 1:1:1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands
-
/bin/sh/: can't access tty; job control turned off
(initramfs)
-
-

So, I did some looking in the forum and people were saying they got around this with noapic in the boot string, so I tried rebooting the CD, then pressing F6 so I could enter in more boot options,  I tried adding noapic to the boot string and got the same result.  Then I tried vga=771 and got the same result.  I tried both together and of course got the same error.  I have noticed that right when it starts the loading process when I use the default F1 option that message comes up briefly saying old bios and acpi must be forced.  Well, I'm kinda at the end of my knowledge base so far, so can someone give me some pointers to put me back on track?

Thanks!:)

That's a very familiar problem with me.  The solution for my PC at the time was to add the irqpoll boot option.  That should slow the boot time, but make it boot into the CD correctly.  It was working with Feisty, but I'm not 100% sure if it'll work with Gutsy.

---

