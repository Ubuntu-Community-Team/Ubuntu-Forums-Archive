---
title: "Installing windows"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by andstuff on 2007-03-26
Allright, I'm getting a rather weird problem. At the moment, I only have ubuntu installed on my computer and I'm trying to install windows XP, to be able to run both os, but I get a bit of a weird problem. I must press any key to boot the windows CD but my keyboard is only recognized once booting up in ubuntu (figured that out with the num lock led). So my keyboard is ony recognized after the boot message, so I'm screwed. It might be important to note that it's on a desktop (not a laptop haha) and the keyboard isn't USB, it's the regular type...

Any technique to get this working would be much appreciated, even if it implies earassing ubuntu as I already backed up everything.

Thanks in advance :)

---

### Post by dstew on 2007-03-26
Your keyboard should be recognized by your BIOS, before any operating system is loaded. You press F12 or F2 (or whatever key your computer uses) at the initial splash screen to enter your BIOS setup program to change your boot order, right?

But also, you are going to have trouble installing Windows after you have already installed Ubuntu. The Windows installer will not respect the presence of another OS. It is usually better to install Windows first, then Ubuntu.

---

### Post by andstuff on 2007-03-26
It seems the issue is deeper than that. I can press esc, F1, F2, F12 all I want before the splash screen, and nothing will happen. I can only get my num lock LED working RIGHT AFTER the kernel is booted, as I mentionned. Could this be circumvented? Is there a way to alter the BIOS or boot sequence from within Ubuntu?

---

### Post by dstew on 2007-03-26
Tell me about your computer system.

---

### Post by andstuff on 2007-03-26
It is a year-old Compaq Pressario "SR1519X", 2.93GHz with the stock 118-key (it has volume control and such) PS2 keyboard 

It was bought with XP installed on it, and I ran into some virus trouble, and tried to install Ubuntu, after a failed attempt to partition the drive, I formatted the drive and installed Ubuntu. At this point, the BIOS/boot screen changed (it no longer had the COMPAQ splash screen nor the same BIOS "check screen".

I'm afraid reformating would leave my BIOS unchanged and I'd be stuck with an unaccessible, empty drive.

---

### Post by dstew on 2007-03-26
With that computer, you press F1 or F10 at startup to access the BIOS. Did you try that? The BIOS must be there in order to run the drives and boot the system. Linux does not use BIOS calls in its OS, so it probably is providing keyboard access after it boots from its own code. However, it is strange that the BIOS does not allow you to boot the Windows CD.

Try to get into the BIOS by tapping F1 while re-booting. Maybe it just needs to have its defaults restored in order to get the keyboard working again.

---

### Post by Benchrest on 2007-03-26
It might be the "DEL" key to enter bios. When you power your computer on the bios should load first and ussually very briefly you will see (probably on the bottom of the screen) a message that says "press xxx to enter setup/bios". But I still don't see why bios would disable your keyboard. Ubuntu should not have altered your bios. 

But in any case, windows requires itself (the big cheese) to be installed first. But what your trying to do windows should have just overlaid the Ubuntu boot record with its own. Hum.

I can only guess your bios is corrupted. If you can't get to bios at boot, you might be able to download a new bios with the installation instructions from your manufacturers web site using Ubuntu. It should create a diskette or cd that is self loading. But make absolute sure it is for your machine or it may cause death. And don't power off while its running.

---

### Post by andstuff on 2007-03-26
Allright, so I tried so I tried pretty much every key to get to the setup, I'm supposed to use f1 and, as I said earlier, my computer doesn't recognize my keyboard or enable it until the linux kernel is loaded.

I looked into getting a bios software upgrade. But since the keyboard is made by compaq themselves, the only bios upgrade I found was an exe extension that's supposed to be used while in windows and WINE can't handle it :(.

Any other ideas, I don't mind them being rather complicated. So I might add a bit of info on my computer.

It seems to boot the USB drives before the CD, as I can't start my computer to an os if I have my thumb drive in.

It doesn't have a disquette drive.

Would it be possible to install windows on another computer with the hard drive I have in my computer right now and put it back into my main computer ?

---

### Post by dstew on 2007-03-26
You have to install the system on the same computer you will use it on. Maybe it would work in an identical computer, but probably not.

You might need to reset the BIOS CMOS. Usually there is a jumper on the motherboard. You move the jumper from the running position to the reset position for a few seconds, then put it back. Look at your user manual or on a forum about your computer. This should restore the default settings.

---

### Post by andstuff on 2007-03-26
All restored to default... stil doesn't work :'(

I feel special :-k , isn't really fun actually :P

---

### Post by halitech on 2007-03-26
I have loaded windows on 1 set of hardware then moved it to another system and have it load the drivers for the new motherboard but it's generally not a very good idea as it will mess things up but in a pinch, it will work.

if you already have Ubuntu up and running, installing Windows will mess up your grub so you will have to fix that from a live cd. if you need windows, why not try to run it in a VMware window?

---

### Post by andstuff on 2007-03-27
Running VMware is pretty much out of the question as I need all my computer's ressources as I will only be doing audio work with windows, so running two os would lag everything up...

Any other ideas would be really appreciated, as I mentionned earlier, I don't mind and I actually am planning on earasing my ubuntu partition and to install once windows is in.

---

### Post by andstuff on 2007-03-27
I just thought of it, could I install windows from VMware ? Anyhow, I'm going to try that tonight...

---

### Post by andstuff on 2007-03-28
Woohoo I got it working :D

Turns out, it most probably was a problem with my keyboard. A weird one since it worked earlier this week and did inside ubuntu. So I ended working around my "press any key" problem by plugging my mouse in the keyboard port and just clicked around when it prompted me to press a key. While the install windows was loading, I plugged my keyboard back in and I now have installed windows and I should install ubuntu later on.

Hope this can help someone else later on. Much love, Louis.

Oh, props to the ubuntu team, I had forgotten how complicated installing windows is and how much it sucks compared to ubuntu, thanks a million !

EDIT : I forgot to add that now my keyboard is recognized on boot up, rather weird...

---

