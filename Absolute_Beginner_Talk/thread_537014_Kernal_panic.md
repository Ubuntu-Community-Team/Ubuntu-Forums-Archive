---
title: "Kernal panic"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by rai78 on 2007-08-28
I have looked through previous posts but they are either not quite the same problem or I just don't understand. 

 When I try to boot ubuntu, loads of lines (no idea what that is, really am a beginner) come up the last one says <0> kernel panic - not syncing Attempted to kill the idle task.  I'm currently working through some lessons which have been posted on here and reading all the information I can as even DOS is a mystery to me and I would really like to move away from windows.  

I repeatedly get the BSOD (blue screen of death) on windows and took the computer back to PC World where I bought it from, but apparently 'if Dave can't fix it no one can' so have resorted to reinstalling windows on a monthly basis (you can see why I want to move from windows.  It seems to be a memory problem with windows, would this effect ubuntu.

Ubuntu was also freezing before I had to reboot but the mouse worked just couldn't click on anything or use the key shortcuts.  

Help me please but in very simplistic terms.  Thank you.

---

### Post by dstew on 2007-08-28
Usually a problem like this is related to hardware. It doesn't mean that your hardware is bad, only that you might need to change some basic system settings to get your system running smoothly.

What kind of system do you have? What memory do you have in it? Processor? Hard disk?

One often-seen  problem that gives kernel panic is a BIOS setting that causes the interrupt system to fail. Anyway, let us know more about your system and we will try to help you.

---

### Post by igknighted on 2007-08-28
If windows is BSOD'ing regularly and Ubuntu is kernel-panic'ing, I think there is a high likelihood that you have some sort of hardware failure.  I would run a disk scan as well as a RAM check if you can.  The RAM check should be at the grub menu, and if it passes that run the disk check from the liveCD.

---

### Post by rai78 on 2007-08-28
OK, I've got windows xp home edition and ubuntu 7.04 but had to tick the alternate desktop box before the download worked (if that makes any difference.  Not really sure about other stuff so just copied down all the information that comes up under system:
Compaq Presario Intel(R)
Pentium(R) CPU 2.66GHz
2.67 GHz, 1.00GB of Ram
Hope that OK if you need any more you'll have to tell me where to get it.  Thanks.

Just noticed third post.  I've run all the checks I can from the system recovery checks to any I've found on windows.  Always says hardware OK.  Not sure about RAM checks just know I've done all the checks I can find.

When I first boot up have ran the ubuntu check (is this first list the grub menu) but get the same message as shown about kernel panic.

---

### Post by dstew on 2007-08-29
Without going into full debugging mode, try shutting off the motherboard's advanced programmable interrupt controller (APIC). You can do this in your BIOS setup, which can be reached by pressing F10 when the computer is first starting up. This might help both of your systems. With this device shut off, the old PIC will take over, giving a more stable but probably slower system.

For the Linux system, you can turn of the APIC by adding **noapic** to the kernel boot line. You can try this boot option temporarily by editing the kernel boot line from the Grub screen, where you pick your operating system. Highlight the linux system you are going to boot using the up and down arrows, but instead of hitting 'return' , hit 'e' to get to edit mode. Select the kernel line with the up and down arrows, and hit 'e' again. This takes you to the end of the line, where you enter **noapic**, then hit 'return', and 'b' to boot.

If this helps, you can make the boot option change permanent by adding 'noapic' to the kernel line in the /boot/grub/menu.lst file. 

One other thing to try might be resetting the BIOS setting to the default in the BIOS setup screens.

---

### Post by rai78 on 2007-08-29
Ran RAM test and had 15,470,598 errors which is quite a few.  After looking up how to fix them I took apart the comp, dusted everything blew everything with the hairdryer, took out the RAM cleaned and replaced.  After running the RAM test again there were no errors.  Sometimes the simplest solutions work.  If any one else has this problem I hope the same works for you.  I'm now hoping all will be well, ubuntu now starts but only time will tell if it will crash again.  Thanks for advice.

---

### Post by DM was on fire! on 2007-08-29
Glad to hear everything worked out. :)
I had a lot of kernel panics when I ran Linspire (atleast six, maybe more). When it kernel panicked a week after a fresh install, I decided to convert to Ubuntu. I'm still having freezes and stuff, though.

I'll most likely try that, though. ^^

---

