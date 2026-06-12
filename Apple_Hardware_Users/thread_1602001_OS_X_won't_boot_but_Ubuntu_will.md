---
title: "OS X won't boot but Ubuntu will"
date: 2010-10-20
forum: Apple Hardware Users
---

### Post by Nwwmac on 2010-10-20
I hope someone can help me with a very weird problem I'm having. 

I have an aluminium iMac that I've been dual booting with Linux for a few months - first with Mint 9 and now with Ubuntu 10.10. There were no problems at first but recently the Mac was sometimes not able to boot OS X after shutting down Linux. Moving to Ubuntu has had no effect on this. Sometimes unplugging the machine for a bit and then restarting it would help (and sometimes not), sometimes memtest and then a reboot would work (or not). 

Here is what happens: 

From within Ubuntu I tell the machine to restart from the drop down menu at the top right. The machine logs me out, shuts down, and restarts. I get the rEFIt chooser, choose OS X on the iMac's internal drive. I get the white screen and the grey apple logo and - nothing happens. I should get a spinner and then the login screen. 

Here is where it gets very weird. 

I have a clone of my OS X installation on a boot-able external drive. EXACTLY the same result from choosing this option. 

Weirder still. 

Booting from the  OS X CD also fails. 

Booting back into Ubuntu is flawless. 

I'm stumped! I've run memtest from GRUB and when I was able to get into OS X disk utility did not find errors on either drive.  

I'm under the assumption that Ubuntu is not cleaning up after itself somehow and this is why OS X in any form fails. 

Any advice? I don't know what to do next... :confused:

Thanks!

---

### Post by pindar on 2010-10-21
Have you tried booting with the "option" ("alt") key pressed? That should get you into the Apple boot manager where you should be able to select your OS X volume to start from. If your problem is with refit, that should bypass it.

---

### Post by teejmya on 2010-10-21
Boot into verbose mode by holding down the letter V.
The last few lines of what it prints should be the error that you are having.
If you don't know what it's talking about, post it here and we can help you more.

---

### Post by Nwwmac on 2010-10-21
I've tried both suggestions to no avail. 

Booting with Option held down shows the MacHD as "rEFIt" and choosing it gives the same result. Grey screen, apple logo, nothing else. 

Simply choosing OS X and holding down "V" yields nothing - just the white screen and grey apple logo. Since there is no grey spinner it looks to me like there is nothing to report, but that is only a guess. 

Help?

---

### Post by Nwwmac on 2010-10-22
There was a very [helpful article]("http://www.tuaw.com/2010/10/22/mac-101-whats-happening-when-your-mac-is-starting-up/") on TUAW today, outlining the Mac boot process. It also lists a few codes available at startup. I tried command-V (verbose) and shift (safe boot). I got nothing from either. 

I was able to narrow things down a bit (I think) after reading it. 

Quote:
[INDENT]**The Gray Screen and The Apple Logo:** The firmware knows  where the system booter file is, since it saves the location in  nonvolatile RAM (NVRAM). The choice of booter file can be specified in  either System Preferences > Startup Disk or the Boot Camp control  panel in Windows. When the booter file is found, EFI (Extensible  Firmware Interface) starts the booter process to load Mac OS X or  Windows if you're using Boot Camp on a Mac. When booting into Mac OS X,  that friendly dark gray Apple logo is displayed. What if the firmware  can't find a booter file? That's when you see that folder icon with a  question mark in it.[/INDENT]I don't get the folder icon so the problem does appear to be a missing booter file. 

Quote: 
[INDENT]**The Spinning Gear: **The booter process is started by the  Mac firmware and it does two things. It loads the Mac OS X kernel, and  it loads kernel extensions (KEXTs) so the kernel is able to take over  the system and continue startup. When the booter successfully loads the  kernel, you'll see the dark gray spinning gear icon below the Apple  Logo. After this point, the gear spins while  launchd, the parent process for every process that runs on the Mac, is started and other processes are spawned.[/INDENT]It looks like my booter file is not completing properly, AND/OR the kernel is not loading for some other reason. 

I'm going to guess that the problem is a corrupt booter file because that would be a common issue no matter what disk I'm trying to boot from - internal, external, or CD. 

Does that sound right? And if it does, where do I go from here? I'd like to avoid the $$ of a pro repair if I can. Since I can't boot the CD I'm a bit stumped as to what to do.

---

### Post by Nwwmac on 2010-10-23
Still trying to get this iMac back on it's feet. 

Using Verbose Mode (command-V) and trying to boot from the Snow Leopard CD, I was able to get some information on what is happening.

Under a blue box that says rEFIt 0.14 I get the following before it freezes:

Start Bot.efi

efiboot device: Acpi (PNP0A03,0)/Pci(1F|1) (Primary, Master)/HD(Part3, MBRType=20, SigType=00)

Boot File Path: /System\Library\Core Services\Boot.efi

Loading 'mach kernel'

Loading Drivers

Loading System\Library\Caches\com.apple.kext.caches\Startup\Extentions\mkext...................

---

### Post by Nwwmac on 2010-10-24
I think I may have this boot failure problem fixed. Getting Teejmaya's tip about verbose mode to work was the key (ie. hold command-V immediately at start and keep holding them until you get the black screen with text). 

The code I posted in my previous entry suggested some kernel extension (that's what kext means) was the root of the problem. A Google search for 'OS X kernel won't load' lead me to [AppleToolBox.com]("http://appletoolbox.com/2010/08/security-update-2010-05-cannot-startup-other-problems/") where it was suggested that I unplug as many USB devices as I could. I unplugged everything but the mouse and keyboard and - I was able to boot without issue. 

Once I was in, I wanted to make sure to squash any bugs before trying to reboot again. I also took their advice and installed the "Mac OS X 10.6.4 Combo Update". It was very large but was said to have many bug fixes. Rebooting after that was not a problem. 

Then, just to make sure, I booted into "safe mode" (hold Shift while starting up). AppleToolBox suggested that this would force a number of clean up routines, including clearing of problematic cache files. 

I suspect that disconnecting the USB devices was the fix here, but I figured being thorough would not hurt. This was an annoying bug, being locked out of my main OS. 

I hope this is helpful to somebody!

---

