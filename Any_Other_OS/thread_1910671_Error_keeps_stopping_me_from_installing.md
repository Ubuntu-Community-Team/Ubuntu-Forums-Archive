---
title: "Error keeps stopping me from installing"
date: 2012-01-17
forum: Any Other OS
---

### Post by grantoos on 2012-01-17
Here's the deal. I have Xubuntu dual boot with Windows and everything is fine but I wanted to try Mint 12 so I installed it on my USB stick (DVD too) and when I reboot, it goes into the menu where I choose Linux Mint, Compatibility Mode, etc. No matter which one I choose, it crashes and stalls with a bunch of code on the screen.

The main error I was able to grab from the screen is "unexpected exit with status 0x0009". I did a bit of searching and I figure it's probably my video card. Previously, I had tried Mint 11 and it was fine. What happened was my card died (Nvidia 9800GT) so I got a new one (GT 5500). So I'm assuming Gnome 3 doesn't like my new card because I was able to install Xubuntu no problem.

Any ideas on how to fix this? I've never encountered any issues with an Linux installs up until now with Gnome 3 whether it's Mint or Ubuntu.

---

### Post by imachavel on 2012-01-17
ok so old graphics card stopped working, you installed new one. Now that you have done so, you are saying install error? What error a screen error? Have you toggled the resolution? Have you tried downloading the driver for your graphics card and then going to ubuntu restricted drivers? 

Also if you take out either card from pci/agp/whatever slot, then boot with on board graphics, how does that work for you? What monitor? Vga monitor connected to vga adapter on back of gpu? Uhhh... screen resolution ok? How are you viewing the forum? From another computer? What is your exact error please state?

btw there is a terminal command option to use unity or gnome. Actually not an option for use, an option for install. I forgot what it is. After doing so, when you log out, you go to the gear next to your log in name, then click on it, then you will see a list of options of which interface to use. I doubt the interface is causing gpu problems though

---

### Post by grantoos on 2012-01-17
I don't have onboard video, just the video card so right now I'm in Windows.

The error is just a bunch of code, it was too much for me to copy down so I just posted the 0x0009 one.

The card is fine in Xubuntu and drivers are up to date, ubuntu restricted and everything, that's why this is confusing.

---

### Post by grantoos on 2012-01-17
Update:

It seems that it's just Gnome in general, not just Gnome 3 because I tried to boot into Mint 11 on my USB stick and same thing. Mint 11 was Gnome 2, right?

Here's some more of the error:

Terminated by signal 9 (killed)
mode sense 23 00 00 00
write protect is off
no caching mode present
assuming drive cache: write through
attached scsi removable disk

---

### Post by Perfect Storm on 2012-01-18
Moved to Other OS/Distro Talk.

---

### Post by grantoos on 2012-01-23
**_UPDATE_**
After trying so many different things, here's what happened:

It's not just Mint, it's pretty much every distro out there! I tried Xubuntu, Mint, Ubuntu, Fedora, etc. and it was all the same result, it would crash while trying to load the live CD. I'm assuming at this point it's the kernel, it probably doesn't like newer Nvidia technology, who knows.

**_[COLOR="Red"]THE SOLUTION[/COLOR]_**
Ok so I figured out how to fix it. For me, I installed Mint 12. Here's what I did, it might work for anyone else having this trouble:

****Note**: this fix is also for those people that get a blank screen when they boot into the OS.**

1. Boot up with the Live CD
2. When I got to the options screen I pressed "tab" to edit and added "nomodeset". It's important where you put "nomodeset", read this: [http://ubuntuforums.org/showpost.php?p=10740097&postcount=3](http://ubuntuforums.org/showpost.php?p=10740097&postcount=3)
3. After that it boot into the Live CD desktop where I ran the installation.
4. After the install, I rebooted and when I got to the GRUB menu, I pressed "e" to edit where I had to add "nomodeset" again. Read this: [http://ubuntuforums.org/showpost.php?p=11491229&postcount=812](http://ubuntuforums.org/showpost.php?p=11491229&postcount=812)
5. Once I got into the desktop, Mint then recognized my video card and I installed the Proprietary Drivers.

That's it! So anyone that is having trouble like this, hopefully this will help you too.

---

### Post by mips on 2012-01-24
That's a pretty common issue.

---

### Post by grantoos on 2012-01-24
> **mips said:**
> That's a pretty common issue.

It seems to be, but it was amazing how uncommon it was to find a solid solution to the problem.

---

