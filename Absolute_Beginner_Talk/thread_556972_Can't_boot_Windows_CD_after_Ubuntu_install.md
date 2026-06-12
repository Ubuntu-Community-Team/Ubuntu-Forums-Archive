---
title: "Can't boot Windows CD after Ubuntu install"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by badfish3 on 2007-09-22
I installed Ubuntu 7.04 Desktop Edition on my computer (using the install option from within the live CD). The program formatted my hard drive clean to an ext3 partition. No problem yet.

I now need to remove Ubuntu and install Windows XP (I do not want a dual boot, just Windows).

The problem is that my computer won't boot from my windows CD anymore. I have tried with my Windows 95, 98, ME and XP CDs and non are working. If I try to boot with my Ubuntu CD or any other bootable CD that is not a Windows CD, they all work flawlessly. I've tried Super GRUB Disk, fdisk /mbr, Ultimate BOOT CD utilities, Hiren's BOOT CD utilities but all I've been able to do is delete the partition and reinstall Ubuntu.

When I try to boot using a Windows CD, I get this screen after the POST :

Verifying DMI Pool Data ............
Boot from CD :
Boot from CD :


Or sometimes (depends if my hard drive has been formatted or not) this :

Verifying DMI Pool Data ............
Boot from CD :
Boot from CD :

NVIDIA Boot Agent, PXE-2.0 (build 082 V1.82)
Copyright (C) 2001 NVIDIA Corporation
Copyright (C) 1997-2000 Intel Corporation
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting NVIDIA Boot Agent.
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER
_


After witch if I press enter with a Windows CD in, it just repeats this same process and I'm back to square one or I use another bootable CD and it loads.

If you need anymore information, don't hesitate to ask, and if this post is not in the right forum I apologize.

Please help me before I rip off the few hair I have left from my head.

Thank you.

---

### Post by alienexplorers on 2007-09-22
Boot the ubuntu live cd and when it loads type in to the terminal:
> sudo gparted
when gparted starts just delete all partitions on the drive you want to clear out.
when done restart and try running the windows disk again.

---

### Post by badfish3 on 2007-09-22
OK, I went and did what you asked (gparted, delete partition).

Now I get a new error message but I still can't boot from my Windows CD

Here's the message after the POST :

Verifying DMI Pool Data ...........
Boot from CD :
Boot from CD :
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 22




And the only thing that works at that point is Ctrl-Alt-Del :P

---

### Post by alienexplorers on 2007-09-22
Now you need to fix your MBR.  Install windows disk and boot into recovery terminal.  Type in fixmbr & fixboot.  See if that helps.

---

### Post by mysticmatrix on 2007-09-22
> **badfish3 said:**
> OK, I went and did what you asked (gparted, delete partition).

Now I get a new error message but I still can't boot from my Windows CD

Here's the message after the POST :

Verifying DMI Pool Data ...........
Boot from CD :
Boot from CD :
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 22




And the only thing that works at that point is Ctrl-Alt-Del :P

When Windows asks to boot from CD, hit enter

---

### Post by badfish3 on 2007-09-22
OK, here's the thing... Windows does NOT ask me to boot from CD. When I put in the CD, the computer tries to read it then it either hangs or gives the error I mentioned in my last post. I Can't get in the terminal at this point. Every other bootable CD I have still work but not the Windows CDs.

So I used Smart fdisk 2.05 to repair the MBR.

After I do that, I get this screen and it hangs there when I have a Windows CD in and pressing enter does not do anything :

Verifying DMI Pool Data ...........
Boot from CD :
Boot from CD :

Error Loading OS

This is with Win XP, Win 98, Win ME, Win 95 CDs.

---

### Post by tie_dyed_sox on 2007-09-22
If your system won't boot from the CD, then I suspect the problem is either with your BIOS or the CD itself (which seems unlikely if you have tried various discs).
Have you made any changes to the settings in your BIOS recently? If so, try reverting them. I'm not sure if it's relevent but I noticed that you have NVIDIA Boot Agent, PXE-2.0 enabled. I think that's set in the BIOS so try turning it off.
Good luck!

---

### Post by badfish3 on 2007-09-22
I haven't touched the BIOS at all (unless Ubuntu did during installation without me knowing witch I doubt).
As for the Nvidia boot loader, it only comes up when no boot loader is detectedon my hard drive.

---

### Post by badfish3 on 2007-09-22
Update! I think I've found a work-around. I didn't think about it until now, I used my Windows Vista beta2 CD and it booted, it's installing right now, I'll keep you posted. Oh and btw, if anyone here remembers how to uninsall Vista and reinstall XP or you have a link to a web page with that information, I would be grateful. I remember having a lot of trouble doing so but I can't remember how I did it.

Thank you!

---

### Post by tie_dyed_sox on 2007-09-22
Hmm... If your system won't boot from CD (and you've tried various Windows CDs) then either there's a problem in the BIOS or the CD-ROM drive has kicked it. It doesn't appear to have anything to do with Windows/Ubuntu on your HDD since it shouldn't even be looking at them if the CD-ROM is the first boot device.

Try disabling your HDDs in the BIOS (in case there's a hardware fault with one of them) and check that the CD drive is the first/only boot device.
If it still won't boot any CDs then you could try another CD drive.
If it works then re-enable your HDDs (one at a time if there's more than one) to see if there's a hardware problem - I once had a faulty HDD that caused the system to hang just after the POST.

Let me know how it goes.

---

### Post by tie_dyed_sox on 2007-09-22
Ok, that's bizarre. Not sure why it wouldn't boot from the other CDs you tried.
Anyway, good luck with that!

---

### Post by master_kernel on 2007-09-22
One question: Why do you want Windows instead of Ubuntu?

Your problem seems like the XP CD itself if your mbr is formatted correctly and your partitions are all deleted.

Keep us updated!

master_kernel

---

### Post by slira on 2007-09-22
Hi
try booting from a windows bootable floppy diskette (if you do not have one, make one in a friend's windows machine) and fix things from there...

first see

[http://www.computerhope.com/issues/ch000474.htm](http://www.computerhope.com/issues/ch000474.htm)

[http://www.duxcw.com/faq/computer/dmi.html](http://www.duxcw.com/faq/computer/dmi.html)

[http://www.dewassoc.com/support/win98/verify_dmi_data.htm](http://www.dewassoc.com/support/win98/verify_dmi_data.htm)

[http://www.kingsley-hughes.com/pc-zone/windows/dmihang.php](http://www.kingsley-hughes.com/pc-zone/windows/dmihang.php)

might help...

another idea: install ubuntu in minimum space; from ubuntu make a free unallocated space on disk or format it as ntfs; try to install windows there; i f things work well, windows will rewrite your MBR when installing and you will not be able to reach grub on next booting; from windows destroy ubuntu's partition or reformat it....

another idea: use a disk "cleaner" like Darik's Boot and Nuke; but please notice this an extreme decision... I NEVER TRIED IT
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

best
slira

---

### Post by tie_dyed_sox on 2007-09-22
> **master_kernel said:**
> One question: Why do you want Windows instead of Ubuntu?


Sounds like flamebait to me :p

---

### Post by slira on 2007-09-22
> **tie_dyed_sox said:**
> Sounds like flamebait to me :p

indeed! we are helping someone to give up ubuntu...!!! this must be unethical, or something... :lolflag:

---

### Post by badfish3 on 2007-09-22
> **slira said:**
> indeed! we are helping someone to give up ubuntu...!!! this must be unethical, or something... :lolflag:

I have Ubuntu on my laptop too :P

But I'm giving my PC to my little sister and she wants Windows.

---

### Post by slira on 2007-09-22
youngsters..........
:)

did you manage?

---

### Post by dirt mcgirt on 2007-09-22
im in the same boat at the OP, but i really dont know what im doing with ubuntu...i just got this computer from my older brother, and im not sure what im doing at all, let alone how to do it...

if someone could explain a few things, that would be great...

(i need windows xp for some of the programs i have to run...)

---

### Post by badfish3 on 2007-09-22
OK, I was successful with my Windows Vista install, I formatted my HD and now I get this screen :

Verifying DMI pool data ...........
Boot from CD :
Boot from CD :
Missing operating system

I think I'll have to try with someone else's windows XP CD to see if it's not mine that's damaged (it is quite old).

I checked the BIOS, I did not see anything that could cause the problem in there, my boot order is still Floppy, CD, HDD. I tried disabling the HDD (before formatting Vista) and Vista loaded anyway :(

I used all my boot disks (my old DOS, win 3.1, win 95, win 98, win ME, and win XP) and only the win 98 one has the format and fdisk commands and I still can't boot from my Windows XP CD (but I can boot from Ubuntu or Vista CDs).

I'll see what else I can do,

Thanks for the help!

---

### Post by badfish3 on 2007-09-22
I was able to get in the Win XP install program by booting from a floppy and running e:\i386\winnt.exe
But it doesn't want to install windows and it says that it was unable to locate a drive with enough memory to install itself.

---

### Post by slira on 2007-09-22
> **dirt mcgirt said:**
> im in the same boat at the OP, but i really dont know what im doing with ubuntu...i just got this computer from my older brother, and im not sure what im doing at all, let alone how to do it...

if someone could explain a few things, that would be great...

(i need windows xp for some of the programs i have to run...)

Hi there
you just want windows, or you want to keep ubuntu and dual boot?

the problem is that installing windows destroys the ubuntu boot (grub or whatever you have)... windows "thinks" "he's" the only possible OS and rewrites the MBR for "himself"... it is possible to restore grub using a live CD or super grub, but if you are not familiar with ubuntu this can be a little hard...

the other solution is to install windows, and then reinstall ubuntu... but that's a bit of work!

best
slira

---

### Post by badfish3 on 2007-09-22
Crap, now I did it, I unplugged my second hard drive (I have all my pictures and music on this drive so I was afraid to lose it by accident. But now the computer won't boot at all :'( All I get is the video card info at the start then this screen :

Award BootBlock BIOS v1.0
Copyright (c) 2000, Award Software, Inc.

BIOS ROM checksum error

Detecting floppy drive A media...

And even if I have a floppy in the drive A: nothing happens (I've waited for about 10 min).

/cry

---

### Post by badfish3 on 2007-09-22
> **slira said:**
> Hi there
you just want windows, or you want to keep ubuntu and dual boot?

the problem is that installing windows destroys the ubuntu boot (grub or whatever you have)... windows "thinks" "he's" the only possible OS and rewrites the MBR for "himself"... it is possible to restore grub using a live CD or super grub, but if you are not familiar with ubuntu this can be a little hard...

the other solution is to install windows, and then reinstall ubuntu... but that's a bit of work!

best
slira

I wanted to uninstall Ubuntu and only have Windows but I can't even boot at all now :(

---

### Post by tie_dyed_sox on 2007-09-22
Ok, this is getting messy... I think you might need to start from scratch here.
Physically remove all HDDs except the one to which you want to install Windows.
If you're comfortable with the hardware side of things, I'd carefully remove the battery for your BIOS and then put it back in. This will reset your BIOS settings to default. 
You'll then need to set the time and date, change your HDD type to 'auto', and correct the device boot sequence (you'll need the CD-ROM as the first device for installing Windows). 
You might want to refer to your motherboard manual if you have one, or download it to another PC.
Make sure the BIOS is correctly identifying your HDD and CD-ROM drive.
If it still doesn't work then try replacing the CD-ROM drive.
Assuming all goes well, you should be able to boot your Windows CD. When it comes to partitioning, delete all the partitions you no longer require.
If you're still having problems after all that, then I'd call for an exorcist :p

---

### Post by badfish3 on 2007-09-22
Thanks, I'll try that when I have more time, right now I'm gonna take a break.

---

