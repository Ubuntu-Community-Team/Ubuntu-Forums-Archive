---
title: "Creative installation method didn't work, need help"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by themish on 2007-01-06
I have a toshiba portege3110ct that I'm trying to get xubuntu on to.  This has no floppy, no os, 6 gb hd, no cdrom drive, no usb support(no os).  So i put the hardrive from the 3110ct into the hd slot for my dell latitutde d610, installed xubuntu edgy through liveCD.  Pulled the hd from the d610, put it back into the 3110ct.  Started up.  So far it goes thru GRUB, to initial xubuntu loading bar, where it hangs for about a minute, then says

busybox v1.1.3 (debian 1:1.1.3-2ubuntu3) built-in shell (ash)
Enter 'Help" for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _


from here there are limited commands that i know nothing of
other than that, ctrlaltF1 works, yields a bunch of stuff and :
/dev/sda1 does not exist.  Dropping to a shell!

I'm going to try ](*,) , then I will try putting the 3110ct hd back into the dell and seeing if it yields the same problem, that will isolate whether or not its a transplant or an install problem.  Any tips appreciated, thanks.


EDIT: Put 3110ct hd into dell, boots and works like a charm...clearly a transplanting issue, anyone?

---

### Post by Bosonator on 2007-01-06
I got that similar error message one time, and it was because the lines in /boot/grub/menu.lst that indicated where my hard drives are got all messed up. 

Your method of installation sounds kind of sketchy (although with no floppy drive even, I can't think of any better way!). However, you might try putting the drive back in the "good" computer, opening /boot/grub/menu.lst and changing any entries that look like garbled text (A38DFAESLKJA8FSA3908S, for  example) with the appropriate labels for your hard drive. If you didn't do anything too complicated with your partitioning, the label for your root partition should be /dev/hda1. 

I've never tried anything like this before, so regard this advice as "just something to try if you don't get any better advice".

Cheers.

---

### Post by themish on 2007-01-06
Well to no avail it seems, I'm going to try an install of 6.06 ubuntu, instead of xubuntu.  Hopefully it will yield results.

---

### Post by macogw on 2007-01-06
> **Bosonator said:**
> I got that similar error message one time, and it was because the lines in /boot/grub/menu.lst that indicated where my hard drives are got all messed up. 

Your method of installation sounds kind of sketchy (although with no floppy drive even, I can't think of any better way!). However, you might try putting the drive back in the "good" computer, opening /boot/grub/menu.lst and changing any entries that look like garbled text (A38DFAESLKJA8FSA3908S, for  example) with the appropriate labels for your hard drive. If you didn't do anything too complicated with your partitioning, the label for your root partition should be /dev/hda1. 

I've never tried anything like this before, so regard this advice as "just something to try if you don't get any better advice".

Cheers.
That method of installation usually works.  Try booting it in recovery mode.  Hit Esc when GRUB comes up and then scroll down to recovery mode and see what it spits out.

---

### Post by themish on 2007-01-06
alright ill try that

EDIT:

Hangs on 
Begin: Waiting for root file system

Then, previous error messages stated.

I think the dev/sda1 does not exist is a critical factor here

---

### Post by themish on 2007-01-07
Also maybe because i took out the main harddrive from the D610 and put the 3110ct harddrive in its place during installation.  This could have something to do with it....I have no idea.

---

### Post by macogw on 2007-01-07
Hmm, maybe the computer you're trying to put it on isn't calling that /dev/sda1.  Maybe it's /dev/hda1 or /dev/sdb1.  See if you can change that (hit Esc in GRUB) then edit the entry.

---

### Post by themish on 2007-01-07
Alright I'm trying that now, installed reg'lar ubuntu 6.06, edited GRUB to hda1....and hanging on mounting root file system :(.  I will try other combinations as well.

EDIT:
Wow, gave hda1 another chance....looks like it got past that problem.

Booted past kernel init, lets see if itll give me gui.

No, no gui, looks like there is reconfiguring to do.

---

### Post by macogw on 2007-01-07
Okay, so now it's up to video.  This is a common thing that is troubleshooted (troubleshot?) on here.  Do you have an ATI or nVidia graphics card by any chance?  If so, what's the model number?  Regardless of what you say, the first thing to try is:
sudo dpkg-reconfigure xserver-xorg
and answer all the questions.  That might fix it.  If it's ATI or nVidia, though, there's probably more fiddling to be done.

---

### Post by themish on 2007-01-07
Nope, its some sort of integrated video chipset, I'll come back with details on how xserver's reconfig goes.

---

### Post by halitech on 2007-01-07
depending on what the laptop that it was installed on originally had for a video card, may not be much to do but if they are alot different, may need to do some major reconfiguring but the  reconfigure should get you up with at least basics.

if it's integrated I would bet either ATI or Intel.

---

### Post by themish on 2007-01-07
yeah, the d610 (not the target laptop) had an ati card in it...target's card is 

Trident Cyber9525
64-bit Graphics Accelerator
32-BIT PCI local bus support
BitBLT hardware
Integrated 2.5MB Video Memory

We'll see how that goes.

---

### Post by themish on 2007-01-07
Sweet mother of god I dont know half of the reconfigure options, any help?

Alright after some work I've gotten 800x600 to start up!

Very excited, go xubuntu!

---

