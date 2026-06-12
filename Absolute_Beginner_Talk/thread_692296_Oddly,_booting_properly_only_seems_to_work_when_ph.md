---
title: "Oddly, booting properly only seems to work when physically connected to the LAN"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Slarty Bardfast on 2008-02-09
This is a really weird issue.  It could be related to Ubuntu or the fact that I'm trying to use it with an Asus Eee.  At this point I need to know if there's somewhere to look for more clues.  Bascially, when my ethernet cable is plugged in, and my connection is active, everything works just fine at boot.  If it's not active or configured right (I found this out by connecting to an open wifi network which reset my dns settings. I rebooted with the incorrect settings, and the problem happened again. When I corrected it and rebooted, it worked fine) or the cable is not plugged in the problem will occur.  Basically, it will boot, but when the splash screen appears the loading bar gets about 2/3 across and it jumps to a terminal and hangs at wacom, acpi, then cups for quite awhile.  Eventually the GDM pops up, I log in fine.  When it is logged in though, it takes a really long time to load up, and opening any applications takes forever.  If I reboot and say plug in the cable, everything works fine.  I've installed the asus eee script that apparently fixes acpi, adds overclocking etc etc so I suspect that it may not be loading properly for whatever reason when I'm not connected to my network (which doesn't make a lot of sense to me).  

Anyone know a good starting point for troubleshooting here? I've fooled around in /var/logs but I can't find anything that seems relevant to me.  Any tips would be greatly appreciated.  Thanks in advance!

---

### Post by dcstar on 2008-02-09
> **Slarty Bardfast said:**
> This is a really weird issue.  It could be related to Ubuntu or the fact that I'm trying to use it with an Asus Eee.  At this point I need to know if there's somewhere to look for more clues.  Bascially, when my ethernet cable is plugged in, and my connection is active, everything works just fine at boot.  If it's not active or configured right (I found this out by connecting to an open wifi network which reset my dns settings. I rebooted with the incorrect settings, and the problem happened again. When I corrected it and rebooted, it worked fine) or the cable is not plugged in the problem will occur.  Basically, it will boot, but when the splash screen appears the loading bar gets about 2/3 across and it jumps to a terminal and hangs at wacom, acpi, then cups for quite awhile.  Eventually the GDM pops up, I log in fine.  When it is logged in though, it takes a really long time to load up, and opening any applications takes forever.  If I reboot and say plug in the cable, everything works fine.  I've installed the asus eee script that apparently fixes acpi, adds overclocking etc etc so I suspect that it may not be loading properly for whatever reason when I'm not connected to my network (which doesn't make a lot of sense to me).  

Anyone know a good starting point for troubleshooting here? I've fooled around in /var/logs but I can't find anything that seems relevant to me.  Any tips would be greatly appreciated.  Thanks in advance!

If you are using DHCP then the networking will wait for a DHCP server response (which can take a while), make your system's networking "Static" and things should speed up with no connection.

As well, the DNS settings and /etc/hosts file configuration can also cause issues.

I use Static, and I just did a test reboot with my cable disconnected and my system came up almost as fast as normal (which is pretty quick).

---

### Post by Slarty Bardfast on 2008-02-09
Yeah it's static.  I don't use DHCP on my wired LAN, just wifi but I haven't gotten that far yet (long story). It's a standard hosts file.  I don't think the problem is directly related to the actual network settings.  I shouldn't need a network connection to open a terminal in less than 45 seconds :) but then again who knows, the problem does only occur when I'm not connected. It's really bizarre.  My Ubuntu desktop boots up just fine regardless of a network connection as well.  It's not the long boot thats bothering me, it's the slow performance when I log in.

---

### Post by kryth on 2008-02-09
That's funny I've had the exactly oppisite problem I can't shutdown properly unless I'm not physically connected to my lan.

---

### Post by Slarty Bardfast on 2008-02-09
Yeah, that is weird.  In my case I don't see how being connected or not could affect performance. If I switch to the console and back it won't even reload the gui half the time. And like I said, if I boot up connected it works normally.  I grabbed a dmesg from a boot with and a boot without the connection and I don't see much difference between the 2.  I dunno, I may end up just saving everything and re-installing but I've done that one too many times in the past and would actually like to figure this one out.

---

### Post by Slarty Bardfast on 2008-02-12
Ok, I've figured it out.  It turned out to be my /etc/hosts file after all.  There was a pile of IPv6 entries in there and when I commented them out everything started to work properly.  I don't know why this fixed it but it seems to have.  Any idea how to mark this [solved]?

---

