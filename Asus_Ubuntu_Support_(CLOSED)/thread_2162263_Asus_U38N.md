---
title: "Asus U38N"
date: 2013-07-13
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Nameless2 on 2013-07-13
Hey, I recently bought this officially no-notebook. It's got pretty neat specifications for its price and as I selected it for its 1080p vivid screen with IPS, I still think I struck a pretty good bargain. Problem however is that I can't seem to properly install Ubuntu as a second boot. I managed to make a slight mistake with the location for Grub and now all I get is the grub command line. I was going to fix that by simply repartitioning and reinstalling, but I am not getting any graphics after the first boot of any installation image.
The problem is probably in the graphics being provided by an AMD A8-4555m and the problem consists of loading an installation/live image onto a USB-stick (I tried 12.04 through 13.04 and daily live, all 64 bit) and then only the first time it would show me graphics and after that, whatever image I take, it would not show me any graphics anymore, so I managed to install from the live image, but after that haven't seen a thing but the backlight. I can actually hear the live image reaching the desktop, but can't see a thing. After that I tried a Kubuntu live image and I actually did see the whole boot process and live desktop, but after rebooting, again no graphics, no matter what image I used.
So I am wondering, does anyone know how to get graphics on the live image working on this APU?

---

### Post by Erikas on 2013-07-14
Same laptop, same issue here. Went through blood and tears but unable to fix it. Even installation process throws random errors, even with several different bootable USBs or distros.

However, I am able to run Live Xubuntu on it (after several reboots). This reply message has been sent from the Live session.

---

### Post by Nameless2 on 2013-07-14
Xubuntu wouldn't hurt either, thanks for the reply. :)
Are you able to consistently boot into the live image, or was it a one-shot only?

From another website I got the hint that it might be this laptop requires the closed source drivers for the graphics, whereas if not equipped with that it should fall back to basic drivers but it doesn't. Solution would then be to boot into the command line and through vi edit the x.org settings. Or, I just remind myself, get a live image running and edit the x.org files through there. Hmm, long shot that, but wish me luck trying Lubuntu and/or Xubuntu.

---

### Post by Erikas on 2013-07-15
I am not able to load Live image consistently. Maybe every 3rd or 5th time it gets me there.

There is clearly a graphical issue because system loads all the way to login screen (ubuntu login screen sound) but there is nothing to see... :@

X.org is a good point. Will execute this later today and let you know.

---

### Post by Erikas on 2013-07-15
Okay, I have managed to fix it and it was very simple - for short period of time. The only thing you have to do is in BIOS: ensure the BIOS launches CSM (make it enabled) and make sure secure boot is disabled, save changes and install Linux distribution. My understanding is that many ASUS VIVOBOOK needs to have CSM enabled in BIOS otherwise screen might/will not turn on.

After I restarted the laptop, it came back to the same state... I am trying Live session right now and go through the logs, perhaps I will be able to see what has happened.

Now I have tried replacing litedm with gdm but that failed because gdm is not available in software repository. 

After another trial through blood and tears I have managed to get to command line as root but it has been mounted as 'read-only' so it is useless... After failing to make any x.org changes under command line I have rebooted the machine. It beautifully loaded to fully installed Ubuntu, so from there I have changed litedm to gdm, rebooted the laptop and same old all over... Blank screen!

I have no idea what can be done next. Even ASUS techies said that this might work or might not as it was specifically designed for Windows 8 and ASUS's touchscreen to be run on Windows 8... It is clearly an intermittent issues with the hardware.

---

### Post by Nameless2 on 2013-07-15
Your remark about "the screen" made me realize there are more ways out of this laptop. I just hooked it up through the HDMI port to my television and consistently managed to boot into a graphics environment, eventhough completely garbled all the time, and with massive resolution issues. So I hooked it up with an old VGA monitor through the mini VGA adapter, but then after the Ubuntu loading screen the laptop screen took preference all the time and the external screen went into power saving mode. 

And now, I just plugged it into my PC screen's DVI connection and I landed straight into the 2D desktop perfectly fine. I have to add here that everytime the backlight of the laptop's screen was on and above all, the touchscreen functions fine as well. So it just seems that the APU does not see the screen properly in some way.

---

### Post by Erikas on 2013-07-15
I have thought the same that it is a compatibility issue with AMD chip. It seems as if Linux trying to load drivers from the location which is not compatible to this specific hardware.

I have managed to go into a log file and it clearly shows that graphics drivers being loaded and shortly stopped afterwards.

The other option is to install something like Arch Linux and start adding components bit by bit but that will be sooooo time consuming... Unless somebody who is really Linux savvy thinks otherwise or perhaps experienced this kind of problem and managed to fix it with Ubuntu installed.

---

### Post by Nameless2 on 2013-07-15
> **Erikas said:**
> I have thought the same that it is a compatibility issue with AMD chip. It seems as if Linux trying to load drivers from the location which is not compatible to this specific hardware.

I have managed to go into a log file and it clearly shows that graphics drivers being loaded and shortly stopped afterwards.

The other option is to install something like Arch Linux and start adding components bit by bit but that will be sooooo time consuming... Unless somebody who is really Linux savvy thinks otherwise or perhaps experienced this kind of problem and managed to fix it with Ubuntu installed.
Actually I just solved it and in hindsight it is rather simple.
Through Unetbootin I downloaded a copy of the Ubuntu 64bit dayly image onto a 2GB stick, plugged that into the U38N, attached an ethernet cable through the converter into the next USB connection and hooked up a proper screen through the HDMI connection. I then booted into the live image, which only showed on the hooked screen, but otherwise functioned fine. I erased the default D: drive and split it into a 4GB swap partition, a 250MB partition to install Grub onto and the rest of the free space I broke up into a partition for Ubuntu and an NTFS partition which I will use for files and folders that I want to share with Windows 8.
Installation then went without a hitch, Grub loaded upon reboot with Ubuntu and Windows 8 both aboard and both booting. Still Ubuntu only showed on the hooked screen, but after installing the proprietary fglrx driver and rebooting, it now works without anything attached.

---

### Post by Erikas on 2013-07-15
Interesting and sounds positive.

Have you tried restarting and shutting down several times the computer? Rebooted without any glitches?

Have you changed anything on BIOS settings prior this re-installation? To something more friendlier?

---

### Post by Nameless2 on 2013-07-15
Managed to boot straight into desktop 5 times now, either by reboot, hard boot or reboot from Windows 8. No issues yet and hope it stays this way. The thing I indeed forgot to mention are the UEFI settings. Like suggest by you and on several sites I browsed for this problem, one has to turn on CSM (set to Enabled). Then turn off Secure Boot Control. The tricky thing there for me was that it took like 3 times before it actually accepted those settings and inbetween I did set an administrator password for the UEFI. So even when you apply those settings, save and exit UEFI, reboot into it and check if your new settings actually are applied.

---

### Post by Diechwei on 2013-07-16
Hi,

I had the same problems as described above for my brandnew U38N, and since last night it seems to work: At least 4 times reboot/shutdown+start did work nicely.

So here is what I did:
I had installed Ubuntu after getting to run the Live-64bit Ubuntu 13.04 iso-image from an USB stick.
As described above, this needed several trials.

I found out, that Lenovo IdeaPad S405 got the same APU and also the same problems:
[http://ubuntuforums.org/showthread.php?t=2147113](http://ubuntuforums.org/showthread.php?t=2147113)
So I used once more the USB stick to install Ubuntu 13.04 directly. This needed several trials until the screen worked,
but finally, I was successful. I used the USB2Ethernet adapter to have wired internet connection.
Sadly, it did not help, still the next reboot showed a black screen.
However, after two more trials I was lucky and the screen worked and I could continue configuration.
So I installed the AMD Catalyst graphic drivers as described here:
[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/286775#286775](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/286775#286775)
This worked fine.

Since it was late in the night, I tried 4 times a reboot or a shutdown+start and each time it worked fine.

Remarks:
1. I did not turn off secure boot, I did not need CSM. I was lucky that the screen worked two times, so I did not need an external monitor.
2. So, probably it is all about successfully installing and running the AMD Catalyst graphic drivers.
3. For anybody, who got already Ubuntu installed, but not yet with the AMD Catalyst graphic drivers, one might try out this:
In the grub2 boot menu, type 'e' and add the boot option "nomodeset". In my case, I eneded up always that Ubuntu successfully booted, but
without graphic, only text/command line.
Then establish an wired internet connection and install the AMD drivers as described in the link above.
I did not try out this procedure, but if it works, it might be the fastest way to make the graphic of an already installed Ubuntu working.

---

### Post by Erikas on 2013-07-16
> **Nameless2 said:**
> Managed to boot straight into desktop 5 times now, either by reboot, hard boot or reboot from Windows 8. No issues yet and hope it stays this way. The thing I indeed forgot to mention are the UEFI settings. Like suggest by you and on several sites I browsed for this problem, one has to turn on CSM (set to Enabled). Then turn off Secure Boot Control. The tricky thing there for me was that it took like 3 times before it actually accepted those settings and inbetween I did set an administrator password for the UEFI. So even when you apply those settings, save and exit UEFI, reboot into it and check if your new settings actually are applied.

It did not work with external screen in my case as it did for you.

However, I have found the other way how to fix it on one of Linux Mint forums and that is exactly what I have done and it has been tested, and it works 100% for Xfce and others. I am using Xubuntu and it works beautifully on U38N.

Before you do all this, again make sure CSM is enabled and Secure Boot is disabled!


[LIST=1]
[*]During boot hold down the left shift key to get the GRUB boot menu to show.
[[IMG]http://i49.tinypic.com/358nift.png[/IMG]]("http://i49.tinypic.com/358nift.png")
[*]Press  the 'e' key to edit the boot parameters. Using the cursor keys of your  keyboard scroll down to the line that starts with "linux" (red box in  the screenshot) and go to the end of that line (red arrow in the  screenshot).
[/LIST]

[LIST=1]
[*][[IMG]http://i49.tinypic.com/slmxiw.png[/IMG]]("http://i49.tinypic.com/slmxiw.png")
[*]Add  the boot parameters "nomodeset xforcevesa" (without the quotes, see red  box in the screenshot). As you type, it will wrap to the next line on  the screen and show a backslash character at the end of the previous  line. That's fine. Press Ctrl+X or F10 to continue to boot.
[[IMG]http://i45.tinypic.com/vbdig.png[/IMG]]("http://i45.tinypic.com/vbdig.png")
[*]If you followed these steps, but you are still unable to boot successfully, please make a new topic for that and ask for help. _**(BEFORE GOING TO BULLET POINT 4, I (ERIKAS) HAVE DOWNLOADED AMD PROPRIETARY DRIVERS FROM THEIR SITE AND INSTALLED IT AFTER THE SUCCESSFUL SYSTEM REBOOT) **_
[*]After successfully booting:
- for Linux Mint 13 and earlier, open the Additional Drivers program from the menu;
- for Linux Mint 14 open the Software Sources program from the menu, then go to the Additional Drivers tab there.
- for Linux Mint 15 open the Driver Manager program from the menu (see: [http://www.linuxmint.com/rel_olivia_wha ... intdrivers]("http://www.linuxmint.com/rel_olivia_whatsnew.php#mintdrivers")).
See  what graphics card drivers are available for you (my graphics card  doesn't need additional drivers, so I can't show any in the screenshot).  If you are sure of the one you should install go ahead. But if you need  further help with this, please make a new topic in the [Graphics Cards & Monitors]("http://forums.linuxmint.com/viewforum.php?f=59") forum and include the output of the command "inxi -SGx" run from the terminal.
[[IMG]http://i46.tinypic.com/2hf2n2p.png[/IMG]]("http://i46.tinypic.com/2hf2n2p.png")
Note  that if you have a NVIDIA Optimus graphics card (Intel IGP + NVIDIA  GPU), you need Bumblebee. That goes beyond the scope of this topic, but  see here: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee).  If you have a AMD Hybrid graphics card (Intel IGP + AMD GPU), I don't  know the right steps except switch either the one or the other off (in  the BIOS to "on-board IGP only" for Intel or "discrete mode" for AMD).  For more help if you have multiple graphics cards, please make a new  topic in the [Graphics Cards & Monitors]("http://forums.linuxmint.com/viewforum.php?f=59") forum.
[/LIST]

I guess that is it for this case! Yay! :popcorn::D

---

### Post by sarkvik on 2013-07-20
Had the exact same problem with Xubuntu on my U38N, and as Erikas mentioned, "nomodeset xforcevesa" solved the booting problem for me. Had to remove a couple of lines before that though. And as someone else said, run with CSM enabled and safe boot disabled. 

And after I installed the proprietary drivers for the graphics, the laptop now boots without a problem every time.

---

### Post by RolfRomeo on 2013-09-03
Also been having issues with this, and upon installing ubuntu originally "nomodeset" in grub worked fine until I could install Catalyst. 

Recently a kernel upgrade kicked out my graphics drivers and "nomodeset xforcevesa" didn't work. What I had to do was to start ubuntu in recovery mode, drop to root shell, issue the command "mount -o rw,remount /" to remount / as read/write, and then install catalyst from there. The next kernel upgrade went without a hitch though, so this issue may slowly begin to solve itself.

---

### Post by sarkvik on 2013-09-04
Anyone got the keyboard backlight to work?

---

### Post by starfall2 on 2013-09-10
> **sarkvik said:**
> Anyone got the keyboard backlight to work?

Have you tried putting acpi_osi="" in the grub kernel command-line?

This fixed all of the ACPI keys on my ASUS N550JV.

---

### Post by Nameless2 on 2013-10-19
I'm guessing my most recent issue with this laptop was due to the upgrade from Windows 8 to 8.1. My guess is that it messed up some NTFS partitions or the boot partition that I had created as it kept running in an infinite loop of failing to load several partitions and folders. So my Ubuntu install got totally unbootable even through the recovery or older kernel options.

Now I installed Ubuntu again by:
- Downloading the Ubuntu 13.10 release image
- Using UNetbootin to write the downloaded image onto a 2GB USB stick
- Turn off the Asus U38N
- Hook an ethernet cable up through the usb adapter and the USB3.0 port
- Insert the 2GB stick in a USB2.0 on the right side of the laptop
- Attach an external 1920x1080p screen through the HDMI port on the right side of the laptop
- Attach power cord
- Boot up the computer and immediately press F2 to enter UEFI/BIOS. In there set "Launch CSM" to "Enabled" and "Secure Boot State" to "Disabled". Under "Boot Option Priorities", make sure to select the USB stick as "Boot Option #1". Press F10 to save and reboot.
- When booting from the USB stick, select "Try Ubuntu" and you should get output on at least the attached screen, possibly also on the screen of the laptop itself
- Once inside the live environment, start up the installation program and select manual partitioning
- Make sure that at least the following partitions are present, or created: Windows 8/8.1 partition, UEFI partition, swap partition for linux, a 250MB partition and a partition for Ubuntu.
- Make sure to format the Ubuntu partition to ext4 format and the 250MB paritition to ext2 format. The mounting point for the ext4 partition should be "/" and for the ext2 partition "/boot". Before confirming all disk changes, select the ext2 partition as the location to install grub from the roll menu at the bottom.
- Continue installation as you would normally do and reboot.
- Grub should now give 4 options: Ubuntu, Ubuntu Advanced Options (recovery), Windows Boot Menu and System Settings (UEFI). Select Ubuntu.
- Once loaded, search for the "Additional Drivers" tab in the "Software and Updates" menu and select the option "Using Video driver for the AMD graphics accelerators from fglrx (proprietary)"
- Let the driver install, close the menu and shut down the laptop.
- Unplug the HDMI cable and screen, boot the laptop and be greeted by full Ubuntu screen functionality!

I must admit I do not get a ful 100% boot ratio, I am greeted with a black screen once in a while, but then it always already failed to show the Asus logo from the start already, or Grub. So I simply press the power button for 5 seconds to turn everything off, wait a bit and try again. Usually fixes it in one go.

Edit:
forgot to mention that for me, all the keyboard functions work out of the box with a fresh Ubuntu installation, non excluded. So if your keyboard doesn't light up properly (or light down), you most likely have bad hardware.

---

