---
title: "My ASUS 990FX, AMD 8350, Ubuntu, Win7 Build - My Notes for Success."
date: 2013-01-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by bmullan on 2013-01-30
I just built a new pc to replace my 4 year old one.

[LIST=1]
[*]AMD 8350
[*]Corsair Obsidian d550 ATX case (great ventilision/modularization
[*]Corsair AX750 Gold Series Power Modular Supply
[*]16GB ram GSkill Ripsaw
[*]ASUS Sabertooth 990FX R2.0 motherboard
[*]GTX 650 graphics (384 gpu but no sli - I don't do games but this is a great card for $90)
[/LIST]

Ubuntu 12.10 64 bit just screams on this CPU & motherboard !

For just Ubuntu the only real config I did was to install the NVIDIA drivers instead of Nouveau for the GTX 650.   And that required me doing a bunch of extra work (I'd probably NOT recommend you downloading directly from NVIDIA's website for this GTX 650 card unless you really know what you're doing.

Last nite I had 15 simultaneous video conversions (avi to mpeg4) going using the Handbrake app and the AMD 8350 wasn't breaking a sweat as I was still able to watch a netflix video & browse the web at same time.   Those video conversions finished in about 20 minutes.    On my old Quad core AMD 940 that would have taken well over an hour at least.

Of all the parts of this build I really have to say the Corsair D550 case impressed me the most.  It wasn't the most expensive part of the build but geez Corsair "really" did some great engineering on that Case.   2 front intake fans,  1 rear, both sides just push a button to remove, front face can open either direction to access DVD or other drives, modular no-tool drive mounts w/vibration damper snapon connectors and 3 more fan openings (2 top and one side) if you need them.

Now... I am posting this for those that create Dual Boot Ubuntu/Windows 7 systems.

The following may solve some huge problems you may run into & may just keep you from causing yourself alot of pain.

I had an existing Windows 7 Ultimate HD.

After putting this system together and installing all of my old drives  .. including my 4th SATA HD - Win7.

I booted and when I got the menu I selected to boot Win7.

Win7 BSOD'd during bootup ???

I had to scratch my head why it was BSOD crashing on boot.   

Then it dawned on me... DUHH Homer...

That was a pre-existing Win7 ultimate HD and the OS had **NONE** of the drivers that came on the DvD with the ASUS Sabertooth 990FX R.0 motherboard.

**PROBLEM #1** - with Windows 7

I couldn't boot into Windows 7 to add the ASUS drivers (it would BSOD).   

Only recourse was to totally reinstall Windows 7 Ultimate !  

**PROBLEM #2** 

For some reason the Windows 7 ultimate Install refused to install on the new "extra" SATA HD ????

It kept displaying an error:

 ** *"Setup was unable to create a new system partition or locate an existing system partition."***

**FOUND CAUSE:**

I already had 3 - 2 TB SATA3 HD's in the new computer one of which was my working Ubuntu 12.10 x64 system.

Then the Solution dawned on me what was happening with Windows 7.

**THE CAUSE:**   

Windows 7 cannot install on a system with multiple existing HDs with one of which already being a BOOTABLE OS.

I don't know where i originally read that but its either if the existing system has 2 or 3 drives installed that a NEW drive will
fail any attempt by Windows 7 to install onto it.

**THE SOLUTION:**

I opened my Corsair D550 rear side door and disconnected ALL of the existing SATA cables from my existing HDs.

I rebooted w/the Windows 7 Ultimate CD in and ... AWESOME .... Windows 7 Ultimate installed without any problems on the new extra SATA HD.

Once Win7 was done... 

I rebooted into Windows 7 then inserted the ASUS CD to install all of the Windows Drivers for the ASUS Sabertooth 99FX R2.0 motherboard (you have to do this because your network interface, USBs etc won't work until those drivers are added to Windows.

IMPORTANT SIDE NOTE FOR THOSE USING UBUNTU WHEN YOU FIRST CREATE DUAL BOOT WITH WINDOWS

If you install Windows AFTER you already have a working linux (or Ubuntu in my case)...  

IT IS REALLY MANDATORY THAT YOU DISCONNECT ALL THOSE EXISTING SATA HDs **BEFORE** INSTALLING WINDOWS 

WHY... because if the Linux HDs were connected when you install Windows 7 the Windows Bootloader would overwrite the Linux GRUB bootloader and you'd just have made yourself alot of extra work to recover GRUB so you could boot back into Ubuntu.

After Windows is installed....

Shutdown your PC, reconnect all the SATA HD DATA cables, then Reboot again.

If Linux/Ubuntu was the 1st drive originally you will boot into Ubuntu.  

Open a Terminal window and execute the command to update the grub bootloader --- which will then see your new Windows 7 HD and add it to the Boot Selection Menu you get when your Ubuntu System boots up.

command:

    $ sudo update-grub

when that command is done reboot your system again:

   $ sudo shutdown -r now

When it boots this time you will see you have the menu option to choose to boot either Ubuntu -or- Windows 7.. ***woot wooot***. !

I got the AMD 8350 because I do a lot of virtualization and having the extra cores means I can run more virtual machines simultaneously when doing "work" related stuff.

Hope this helps others both those building a new PC & interested in the AMD 8350 or the ASUS Sabertooth or the GTX 650 card.

But also especially because I tried to explain the weirdness of Windows 7 (and its error msg) **IF** you ever try to install Win7 on a new *"extra HD"* in your system.   

Now you will know how to fix that Win7 error and get it all done successfully and end up with a great dual boot Ubuntu & Win7 system.

---

### Post by technology4 on 2014-01-16
Hi
I'm thinking of getting a ASUS Sabertooth mobo and found this post very useful. Many thanks for posting

Alan

---

### Post by oldfred on 2014-01-16
You did not mention, but new systems are both UEFI and BIOS. And usually Windows 7 is BIOS boot as you have to copy DVD to flash and add a few things to make it UEFI capable.

With new systems you do want to be consistent. Either all BIOS boot or all UEFI boot.
New drives over 2TiB have to be gpt partitioned. gpt does have some advantages over MBR.

And Windows only boots from gpt partitioned drives with UEFI.
Both Windows on Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.
But Ubuntu can boot from gpt partitioned drives with UEFI or BIOS. 

Best to have Windows on one drive and Ubuntu on all other drives.

---

