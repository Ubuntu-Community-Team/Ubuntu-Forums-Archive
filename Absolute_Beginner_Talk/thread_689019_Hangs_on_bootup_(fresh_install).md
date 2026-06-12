---
title: "Hangs on bootup (fresh install)"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-02-06
I've just installed 7.10 fresh on a friend's machine. When booting, it hangs as soon as the "ubuntu" splash screen comes up. I've used two different install CDs, and I get the same problem with both.

Ideas??

EDIT: I'm suspicious of the internal USB interface. I can see the keyboard being tested as soon as the splash screen comes on (the "num lock" light flashes), and that's where the boot sequence gets stuck. It's a USB keyboard, so that's where my suspicion comes from.

---

### Post by spiderbatdad on 2008-02-06
mmm almost definitely. Not sure of a work around...must be something out there... a script for init.d. Is there a ps2 keyboard around to try?

---

### Post by doctorbighands on 2008-02-06
I don't have a ps2 keyboard, unfortunately.

I've just tried changing a couple of the USB settings in the BIOS, and that didn't help. Also, I unplugged everything with a USB cable (except the keyboard - it won't even bring up the splash screen without that), and that didn't work, either.

---

### Post by spiderbatdad on 2008-02-06
Is the keyboard definitely good? The integrated peripherals or whatever in Bios seems to be the common fix.

---

### Post by doctorbighands on 2008-02-06
The keyboard is definitely good. It worked in Vista before I dumped that, and it works whenever I run from an Ubuntu live CD.

Whatever the first thing is that gets checked during the boot sequence (immediately after the splash screen comes on) is what seems to be the problem.

---

### Post by oedha on 2008-02-06
mmm.....is it possible...the display card ? it that installed properly ?

---

### Post by bwtranch on 2008-02-06
Nice cat. Used to have one just like it. Sounds like a USB mod problem. Don't know why.  Might try a 8.04 install otherwise I don't know except for a re-compile of the kernal. Make sure your install disk is OK, too. Do a checksum. (I don't think that's it, but...)

---

### Post by doctorbighands on 2008-02-06
I tried installing from two different 7.10 discs, both of which came straight from Canonical, and I tried a 7.04 disc whose checksum was fine. Same problem in each case.

---

### Post by doctorbighands on 2008-02-06
*bump*

I really need help on this, if anyone can.

---

### Post by Blue Sassley on 2008-02-06
Never Mind...

Sorry Blue

---

### Post by doctorbighands on 2008-02-06
I've combed the forums, I've searched bug reports, I've done google searches...I can't find anyone else who's reported this issue!!

I'm going to try installing Linux Mint on their machine. If that doesn't work, I'll be truly stuck. I don't want to have to leave them with "Sorry, I guess Linux just doesn't work on your machine," but I feel like that's about where I am right now.

This really sucks.

---

### Post by ugm6hr on 2008-02-06
Did the Ubuntu LiveCD work OK?

Have you tried booting without the splash?  You can edit Grub when it boots and just delete the "quiet" and "splash" options.

---

### Post by doctorbighands on 2008-02-06
The live CDs have worked in every case (except that the Feisty one told me there was no wired connection available, and there is).

I tried going into Grub to edit out the splash, but I didn't see anything called "quiet" or "splash".

---

### Post by ugm6hr on 2008-02-06
> **doctorbighands said:**
> The live CDs have worked in every case (except that the Feisty one told me there was no wired connection available, and there is).

I tried going into Grub to edit out the splash, but I didn't see anything called "quiet" or "splash".

Obviously I'm doing this from memory - since I'd have to reboot to check!

When booting - do you get the Grub menu?  If not - press Escape when booting (you usually have 3 seconds to do this).

On the Grub menu - select the default Ubuntu line and press "e"
This allows you to edit the Grub entry (menu.lst) live
I think it is the second line - press "e" to edit again and right-arrow to go to the end of the line.
These 2 words should be there at the end.  Just delete them.
Then press "b"

This should boot without splash.  You will then get appropriate error messages.

Have you actually tried leaving the computer to continue booting for about 5-10 minutes?  If so, and it successfully boots - this is probably the problem: [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

---

### Post by doctorbighands on 2008-02-06
I have left it alone. After about 5 minutes or so, the splash screen disappears and I get a prompt that says something like "<initramfs>". 

[I'm not sitting in front of the machine right now, but I'm pretty sure that's what the prompt says.]

I'll try eliminating the splash, as you suggested. Maybe then I can get some clues...

---

### Post by Officer Dibble on 2008-02-06
Have you tried updating your BIOS?

What is your motherboard, we can probably help find an update if you're not sure what you're looking for.

---

### Post by doctorbighands on 2008-02-06
I haven't tried updating the BIOS. The machine is only a few months old; would there be a new BIOS version so soon?

---

### Post by lostcause64 on 2008-02-06
You don't happen to have an ATI graphics card in it do you?  I have an ATI x850xt that hangs the machine at the Ubuntu logo very early in the boot process and no one has been able to find a work around for it, even after trying every trick in each ATI thread up here.  My only solution is to remove the ATI card, using the onboard Intel graphics instead.  I am running a PS2 keyboard and USB mouse in a dual boot with XP Pro with no problems otherwise, in the event that the previously mentioned USB keyboard is involved.  Some day, either somebody will get it right with ATI, or I'll finally be able to replace that card with an nVidia...

John

---

### Post by doctorbighands on 2008-02-06
Nope, it's an nVidia card. If that's what's causing the problem, then I wouldn't know what to do about it.

Thank you, though!

---

### Post by ugm6hr on 2008-02-06
Assuming you installed from a LiveCD with the same hardware as what is attached at the moment, and you used the standard "run or install" (i.e. you didn't need to use an additional driver or use safe mode) on LiveCD, I can't see how it could be a hardware problem.

Sometimes, the installation picks a different driver than the LiveCD (I think some of the older Intel wifi chipsets did this), but that shouldn't stop things booting into X (unless it applies to the graphics card).

Just to check - does Safe mode work from the installation?

---

### Post by Officer Dibble on 2008-02-06
> **doctorbighands said:**
> I haven't tried updating the BIOS. The machine is only a few months old; would there be a new BIOS version so soon?

Please tell me what motherboard you have and I'll look into it for you. :)

---

### Post by doctorbighands on 2008-02-06
Okay, I'm now sitting in front of the offending machine, so I can troubleshoot.

I killed the splash screen on boot, and here's what it said when it ended.

The last line of the boot sequence reads as follows: (in other words, this is where it seems to stick)
```
[   4.377763] drivers/usb/input/hid-core.c: v2.6: USB HID core driver
```

Then, after waiting for about 3 minutes or so, the following popped up:
```
Done.
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat proc/modules ls /dev
ALERT! /dev/hda1 does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```

Any help you can offer would be wonderful. Thank you!

---

### Post by ugm6hr on 2008-02-07
I am afraid I don't know.  This looks worrying though:
> ALERT! /dev/hda1 does not exist. Dropping to a shell!

How have you partitioned the HD?  Might be worth running a diagnostic on the HD: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) might be useful.

---

