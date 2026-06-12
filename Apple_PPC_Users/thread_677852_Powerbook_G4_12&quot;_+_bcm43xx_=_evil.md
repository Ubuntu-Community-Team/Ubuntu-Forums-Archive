---
title: "Powerbook G4 12&quot; + bcm43xx = evil?"
date: 2008-01-25
forum: Apple PPC Users
---

### Post by rbach on 2008-01-25
Hi, I just switched from OS X on my old powerbook to running Ubuntu and I've tried everything I could find to get wireless to work, but instead it decided not to recognize my airport extreme card at all.  Can anyone help me get my wireless card back? :confused:
-Eric

---

### Post by stream303 on 2008-01-26
I don't own a powerbook, but a late 2004 12" iBook, so this may not help, but....

Gutsy's Network Manager was hogging my cpu, so I disabled it (did NOT remove it) and my network connections were fixed.  If you don't need the automatic switching of Network Manager, maybe temporarily disabling it might help in the diagnosis.  I disabled it with docs contained  here:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

I have very limited wireless knowledge, so I'm afraid this is the best I can offer at this time..

---

### Post by msbigbadwolf on 2008-01-26
Have you followed this thread?
[http://ubuntuforums.org/showthread.php?t=142727](http://ubuntuforums.org/showthread.php?t=142727)

I struggled for a while trying to get my Airport Extreme card to work as well, and in the end my problem was the firmware - when I had copied the AppleAirport2 drivers directly from the Mac OS X side and extracted them with fwcutter, the wireless refused to work. By using the generic wl_apsta-3.130.20.0.o driver instead, everything worked perfectly.

The generic driver is linked off the bcm43xx page: [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

Hope that helps!

---

### Post by guidop on 2008-01-26
See this post, and referenced threads:

[http://ubuntuforums.org/showpost.php?p=4189473](http://ubuntuforums.org/showpost.php?p=4189473)

The .deb file hosted at speedyshare (still available when I checked last week) bundles a copy of the  the broadcom firmware, so you don't have to find it separately.  It should work with your PowerBook's airport card, if it's the same as in my Powerbook (BCM4306 rev 03), and others of similar vintage.

I'm running Feisty, so use WICD to ease configuration and connection on WPA encrypted networks.  With the firmware and WICD under Feisty, my wireless performance is very reliable.

This is my airport card info:
```

$ lspci | grep Bro
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

---

### Post by rbach on 2008-01-26
so I've heard feisty is better for airport than dapper.  SO I go to install feisty and it starts to open the installer and then it quits?  Any ideas?

---

### Post by guidop on 2008-01-28
IIRC:

I booted the Kubuntu 7.04 desktop (live) CD, the bootsplash colors were strange, but it worked OK once the desktop started:

[http://www.cdimage.ubuntu.com/kubuntu/ports/releases/7.04/release/](http://www.cdimage.ubuntu.com/kubuntu/ports/releases/7.04/release/)

I used the installer on the live desktop to partition my free space and install a command line system, then rebooted and installed the Xubuntu desktop using a hardwired ethernet connection.


I installed the bcm43xx drivers and firmware, and WICD (Xubuntu does not install network manager) to get wireless working.  If you're running Gnome or KDE, you will probably have to uninstall (or disable) the network-manager or knetworkmanager module.

You can get a pre-built bcm43xx .deb file with airport firmware from: 

[http://www.speedyshare.com/214793933.html](http://www.speedyshare.com/214793933.html)

and WICD from:

[https://sourceforge.net/projects/wicd/](https://sourceforge.net/projects/wicd/)


I also modified my yaboot.conf, /etc/initramfs-tools/modules, and /etc/modprobe.d/blacklist-framebuffer files per instructions posted by Eric Work at this link to fix the bootsplash colors and get mac-on-linux to work fullscreen:

[https://launchpad.net/ubuntu/+source/usplash/+bug/21478/comments/16](https://launchpad.net/ubuntu/+source/usplash/+bug/21478/comments/16)


Because I have an ADB trackpad, I compiled a patched kernel to get more functionality, reference this thread:

[http://ubuntuforums.org/showthread.php?t=380884](http://ubuntuforums.org/showthread.php?t=380884)

My post has my trackpad settings, and the up-to-date link to the kernel patches.


The above should get you a decently working base install, if your PowerBook hardware is not too different from mine.


For reference, which 12" PowerBook model and Airport Card version (per lspci) do you have?

---

### Post by jrharvey on 2008-01-29
I only read the first post but ubuntu works perfect on my powerbook G4. I am using 7.10. The only problems i have run in to is compatability with certain apps. Alot dont work on PPC architecture. Oh yes and the NVIDIA card does not have a driver :(

---

### Post by tr333 on 2008-01-30
i was dualbooting feisty and OSX on my powerbook 12'' for a while.  All I had to do for wireless was to install the bcm43xx-fwcutter stuff to grab the firmware.  Wireless seemed to work perfectly with WPA2 and NetworkManager both going well.

---

