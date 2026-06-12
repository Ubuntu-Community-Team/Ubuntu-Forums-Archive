---
title: "Problem Installing Gutsy on Low Mem System"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by motion parallax on 2008-02-02
It's a HP 700MHz with 312 RAM.

I've tried the live CD. The Ubuntu splash screen loads on start, but after the status bar loads the screen goes blank.

I've tried the alternate CD. It takes me to a command prompt on start, and none of the options listed are "install" or anything like it.

I wonder if the blank screen comes from the fact that I'm using a GEForce4 128MB 3D card. I've tried plugging the monitor into the on-board video, but I don't get any signal with Windows or Ubuntu.

If anyone has any input, I would appreciate it.

---

### Post by wolfen69 on 2008-02-02
sounds like your video card is dead.

---

### Post by dcstar on 2008-02-02
> **motion parallax said:**
> 
........
I've tried the alternate CD. It takes me to a command prompt on start, and none of the options listed are "install" or anything like it.
........

[https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6rl]](https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6rl])

---

### Post by spiderbatdad on 2008-02-02
have you tried with noapic nolapic vga=771...also hit f6 at grub, then f1 for more options and f6 again for examples.

---

### Post by motion parallax on 2008-02-02
I looked at the link given and now I'm going to try an install from within windows.  I'll update this later.

---

### Post by motion parallax on 2008-02-02
Tried installing with NetBoot, couldn't connect to the network.  

Tried copying the alternate CD over, gave me a redundancy error and closed before file transfer was complete.  

I really don't know what to do here.

---

### Post by chewit on 2008-02-02
Your RAM is more than enough, I managed to use the live CD on a much lower PC as you can see below.

---

### Post by motion parallax on 2008-02-02
Your PC is about the same specs as my PC.  I'm surprised.  

I know the Live CD I have works, because I used it on my laptop just the other week.  

I wonder if its the nvidia card.  I don't know why my onboard video isn't working.

---

### Post by ThePinkWitch on 2008-02-02
I have Gutsy installed on a 1.5G, 200mg RAM, with an old NVidia GeForce GTS Pro 32 MG graphics card and it's running beautifully. It's not lack of RAM.

---

### Post by motion parallax on 2008-02-02
No problems losing video on the nvidia card during install?

---

### Post by spiderbatdad on 2008-02-02
no the issue seems related to irqpolling or graphics card. Some bios setting allow for pci config. Also there are noapic nolapic vga=771 as I mentioned before.

---

### Post by motion parallax on 2008-02-02
Could you explain what that is and how to implement it?  My experience here is limited.

---

### Post by spiderbatdad on 2008-02-02
when you insert the cd and start up, you should be presented with an options screen. Hit f6. Now at the bottom of the screen you should see a kernel line. Delete from the end of the line everything up to and including ro....for example ro --quiet splash. Replace with "noapic nolapic vga=771" No Quotes. I can not guarantee these are the exact parameters for your machine, but there is a fair chance they will work...no harm will be done. If this works. You will need to do it again on your installed system until you edit the kernel line in /boot/grub/menu.lst...which is easy and can be discussed once you determine if this will work for you.

---

### Post by motion parallax on 2008-02-02
Is the "Options" screen the loader that asks whether I want to run XP or Ubuntu-Linux?  Because that's only input screen that comes up after restarting with the CD.

---

### Post by motion parallax on 2008-02-02
F6 didn't do anything during the loader, but right after the loader it brought up a screen titled "GRUB4DOS".  I have the following options:

find /ubuntu/disks/boot/grub/menu.1st
find /ubuntu/install/boot/grub/menu.1st
find /menu.1st
find /boot/grub/menu.1st
find /grub/menu/1st
commandline
reboot
halt

---

### Post by spiderbatdad on 2008-02-02
we could be a little off track here. Are you still trying to install the alternate cd? You do not have enough RAM for Gutsy 7.10. Have you considered xubuntu? Also It looks as though you need to set CD as your first boot option.

---

### Post by motion parallax on 2008-02-02
Okay.  I have both the live and alternate CD's.  

Live CD - splash screen loads, then screen goes black indefinitely.

Alternate CD - goes straight to command prompt with a string of letters as the prompt itself.  I can load up the alternate and tell you what it says.  

Either way, the only input screen either gives me before this is the loader asking if I want to load Windows or Linux.  

The computer is configured to boot from CDROM.

---

### Post by motion parallax on 2008-02-02
I'm more than willing to try Xubuntu.  My original goal was to install the server edition on this compy, then download the XFCE desktop manager.

---

### Post by spiderbatdad on 2008-02-02
I'm not sure what's going on, but what you are describing does not sound like the Live CD options screen...It sounds like a GRUB screen...which leads me to believe you are not set to boot from cd as the first option. , or some other boot loader program is running.

---

### Post by spiderbatdad on 2008-02-02
Upon starting with thelive cd in, you should see the screen shown below.

---

### Post by motion parallax on 2008-02-02
When I first used the Live CD (this is on both my laptop and PC), it wouldn't boot from the CD even though both have CDROM before HDD in the BIOS boot order.  So I loaded Windows, clicked on the install icon in the CDROM directory.  It installed some kind of loader program, then prompted me to restart.  

After restart, a screen now pops up (GRUB4DOS, I believe) asking if I want to load Windows (first option) or Ubuntu-Linux (second option).  At the bottom the command F8 is listed for advanced Windows options.  Selecting Windows will boot Windows as normal.  Selecting Ubuntu-Linux will load the Live CD.  

On my laptop, selecting Ubuntu-Linux is how I get the Live CD to load into RAM and run from the CD.  On this system, which has a full Ubuntu Gutsy 7.10 install, the GRUB loader loads first.  If I select Windows, GRUB4DOS loads asking if I want to run Windows or Ubuntu-Linux.  If I want to use the Live CD on my laptop, for partition editing as an example, I select Windows on GRUB, then Ubuntu-Linux from GRUB4DOS.

---

### Post by motion parallax on 2008-02-02
I can't get to that screen on my PC.

---

### Post by motion parallax on 2008-02-02
With the alternate CD in the drive, the GRUB4DOS loader comes up.  If I select Windows, Windows will load.  If I select Ubuntu-Linux, it goes to the command prompt.  I can't get any other screen to start.  

Is there some way to get the installation screen to come up from the command prompt?

---

### Post by motion parallax on 2008-02-02
I want to do a full overwrite of Windows, so is there some way of just removing Windows entirely and installing Ubuntu later?

---

### Post by spiderbatdad on 2008-02-02
OK I just noticed Vista in your signature...didn't assume that as we were talking a low mem system. I believe vista requires its own partition editor. I'm not sure how to guide you any further except to suggest looking at the installations forum a little and read a guide to dual booting with Vista. [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)  if you've done all this and are having trouble booting, look into editing /boot/grub/menu.lst so that the end of the kernel line, where ro --queit splash, is replaced with noapic nolapic vga=771. It seems you pointed out an option earlier to load boot/grub/menu.lst, but that's an "L" in your post i remember you copied it as a 1.

---

### Post by motion parallax on 2008-02-02
No, no, my laptop is a Vista/Ubuntu 7.10 dual boot that works fine.  I'm installing this on my old PC that has XP, 700MHz Intel Celeron, and 312MB RAM.

I want this to be a total, independent install on my PC.  XP is near crashing, I don't have a disk to reinstall it, and, honestly, why bother?  My laptop has Vista for any Windows-related uses.  I want this PC to be totally Ubuntu.

---

### Post by spiderbatdad on 2008-02-02
ok. so it seems like something is wrong with that disk. Did you do the md5sums check? You just aren't getting the right install screen at start up, and I have never seen that before. Perhaps burn a new disk from another site.

---

### Post by motion parallax on 2008-02-02
Fearing something was wrong with my integrated graphics chip, I set my graphics chip as my primary video driver on Windows, then restarted and attempted to resume the installation.  

Using Live CD:
When the computer restarted, it was still using the nvidia card as the primary.  The ubuntu splash screen loads, the primary screen goes to a blank screen with a blinking cursor, then totally dark.  

Strange thing, the second monitor (which I had plugged in to the graphics chip) turns into this wild kaleidoscope of colors when the nvidia monitor goes dark.  If I hit up and down on the keyboard the colors shift around until I stop.  

At this point, nothing really happens.

---

### Post by motion parallax on 2008-02-02
The Live CD is the same CD is used to install Ubuntu on my laptop last week.  The alternate CD I ran the check at both the terminal level and one built in to the burning program.  Iso burn, lots of files on the disk.  

I guess I could try burning another alternate if I can find a blank laying around here.

---

### Post by motion parallax on 2008-02-02
Alternate CD:
Computer starts, goes to the loader, I select Ubuntu-Linux.  Ubuntu splash screen loads, then goes to text command line and says

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands. 

(initramfs) _

---

### Post by spiderbatdad on 2008-02-02
why not just burn xubuntu 7.06? Use that until Hardy is released. You can add the server apps you want after your install is working. I say 7.06 because in many respects it has proven to be more compatible with a majority of systems.

---

### Post by motion parallax on 2008-02-03
If the Gutsy Live CD isn't working, will the Xubuntu be any different?

---

### Post by motion parallax on 2008-02-04
Any more input on this, or should I try another OS?

---

