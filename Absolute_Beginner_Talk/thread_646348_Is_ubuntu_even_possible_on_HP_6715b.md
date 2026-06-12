---
title: "Is ubuntu even possible on HP 6715b ?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by SqlByte on 2007-12-21
So many problems installing ubuntu/kubuntu/slackware on my laptop HP 6715b it's crazy :S
So is it possible to install it or i have to use something like mandriva, i think only that works out of the box for me.
I just downloaded kubuntu-7.10-alternate-amd64.iso i didn't install alternate never before so if someone could tell me how to do it ? And will it work on my laptop ?

---

### Post by bobpur on 2007-12-21
I have limited experience with the Alternate Install Ubuntu cd, but the prompts are pretty straightforward. If I remember correctly, The alternate install is like installing Ubuntu back when it was new (v5.04 or so). and I done it with no experience at all. 
You don't offer much info about your problems. What's the matter, maybe we can help if we had more to work with.

---

### Post by Sef on 2007-12-21
To install with the alternate cd, read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").   I prefer the alternate cd; it is easy to use.  The only difficult part would be partitioning.

---

### Post by SqlByte on 2007-12-21
Well the problem is that it simply can't be installed, the installation is aborted after install menu.
I will partition it via windows, because it will be dual boot.
The only problem i got now is deleting the slackware that is currently on my sistem on dual boot with win.
If i simply delete the partition where slackware is will i be able to boot windows ?!
I think there would be problems, just don't know how to solve them :(

---

### Post by snkmad on 2007-12-21
I got a friend who had a hell of a time trying to install ubuntu on some HP 6125 laptops.
He did managed to install, using the alternative cd, but he had to tweak the install with loads of options....

---

### Post by Sordelka on 2007-12-21
My friend installed it and is working on it. Yea, we did spend a night but it is possible. Just do all your stuff slowly, no rush!

---

### Post by louieb on 2007-12-21
> **SqlByte said:**
> The only problem i got now is deleting the slackware that is currently on my sistem on dual boot with win.
If i simply delete the partition where slackware is will i be able to boot windows ?! ...
Big problem if you do that -- it won't boot at all. -- 1st you must change the MBR to boot windows. Its not hard and there are lots of ways to do it as shown here: [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by The Cog on 2007-12-21
You cannot format the disk for a Linux install using Windows because Windows cannot create partitions of the right type. Your best bet is to use Windows to reduce the size of the Windows partition, leaving unallocated space on the disk. Then choose the Ubuntu installer option to use the free disk space. It will then create the partitions that it needs and format them with the right filesystems.

Use the Alternate installer CD to avoid possible graphics card problems. You can fix the graphical stuff after installation.

---

### Post by jimmysp on 2007-12-28
Hi, I am also an owner of this laptop.
First to answer your question, if you want to have the graphics when you install, you should try plugging in an external monitor with 4:3 ratio (and press Fn+F4 when the Ubuntu boot menu appears). I think there is a problem in the opensource driver which does not work on 16:9 monitors, or at least on this one crashes.

If you don't have an external monitor, try using this instructions:
*On some hardware with ATI/nVidia cards: If the liveCD boots all the way to Gnome but hangs and just shows the mouse pointer and eventually the wallpaper, restart the liveCD, press F6 and change the options "quiet splash --" with "nosplash noapic noacpi --".*
(taken from here [http://www.linuxmint.com/rel_daryna.php](http://www.linuxmint.com/rel_daryna.php))

For the first solution I can guarantee, it has worked for me, but I haven't tested the second one.

For this laptop, I have tried:
 Fedora rc8 - same problem with the graphical (I think on the fedora forums I found the solution with the external monitor - cool one :) )
 OpenSuse 10.3 - quite ok, but the package manager is driving me crazy here
 Mandrake 2008.0 and 2008.1 - some problems with having to blacklist bcm43xx and ssb, but the drivers are stubborn and don't like to be blacklisted
 PcLinuxOs - quite ok too, after the updates

On all distros I tested, the wireless card is working only with ndiswrapper, except in Fedora. It worked in Fedora with the ssb driver and the firmware files from the net, without ndiswrapper.
The suspend/resume is not working at all.
Kernel 2.6.22 does not shut it down (only with 2.6.23). It only says "Halting the system" and remains like this - I have to press the power button for 4 secs.
Until now, I think Fedora was the distro wich handles this laptop's hardware at the best.

Hope my little review helps other owners too.

---

### Post by BigCheese on 2008-01-10
OK, I am a bit of a Linux newbie as well, but I can confirm that plugging in an external monitor (so long as it isn't widescreen 16:9 format) and switching to it using the Fn+F4 combination stops the install from crashing before it loads up.  

In case it's any use to anyone, I'll go through what I did.I bought the 6715b with Vista Business on it and installed XP Pro as a full disk NTFS partition.  By plugging in the external monitor I could get the normal Ubuntu live CD to run (took a while to load, but it got there) and installed normally.  Once that was done I rebooted from the drive, switched to the external monitor again at GRUB and went in to Ubuntu as normal - all ok to this point.

I used a wired net connection to update all of the packages installed (from all the available repositories) and activated the unsupported ATI driver in the 'Restricted Drivers Manager' and the Broadcom wireless driver.  After a reboot I went into the 'Screens and Graphics' window and manually selected the default monitor to be a LCD Panel 1680x1050 (widescreen), disabled monitor 2, unplugged it and rebooted again.

This time Ubuntu loaded on the laptop screen fine, displaying at the correct resolution and with no further display or loading problems (YAY!!) :D

I still haven't got the wireless networking to work, which is annoying, but as I have XP dual boot I can always resort to that if there's no wire handy.  Anyone with a step-by-step newbie friendly wireless fix for this machine - please let me know!!

Cheers for all the help in the rest of the forum by the way - I think I would have actually gone mad without the external monitor tip! :D

---

### Post by jimmysp on 2008-01-11
Hi BigCheese,

I am glad I could help with external monitor solution.
For your wireless card, I recommend you use ndiswrapper with the Windows drivers.
This was the only way I could make the BCM4312 chipset work (like I stated above, only in fedora I could use the inbuilt ssb driver).
To install ndiswrapper you should first blacklist the driver **bcm43xx** (try here for info: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28blacklist%29](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28blacklist%29))

After that, I think you can use the Restricted Drivers Manager, or whatever it is called. If I remember, you have an option of using the "Windows drivers". I can't recall exactly right now, because I switched to Mandriva, and I managed to make it work quite fast and reliable on this laptop.

---

