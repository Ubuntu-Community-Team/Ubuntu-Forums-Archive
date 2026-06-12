---
title: "Gutsy hangs on startup"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by BuXXi on 2007-11-20
Hi, yesterday I installed Gutsy. Installation went great and the system booted up.
But after a reboot it hanged on "Loading Hardware Drivers", searched through the forums and found something about usb2.0 causing this. Added noapic and noirqdebug in grub and system booted up.
But now it seems to the same problem yet again and the previous didn't work, sometimes it even comes farther (to like 70%) in the progressbar. Thinking it's maybe cause of the harddrive, but windows works great on it.

Using a AMD64 3200+ on a Gigabyte GA-K8NS, with two Corsair VS512MB400.
Ubuntu is installed on a Seagate Barracuda 200GB IDE. (got another harddrive, WD Caviar IDE 250GB too)

Thanks in advance!

---

### Post by cmnorton on 2007-11-21
Try to boot with the Ubuntu live CD or another CD-based distro, mount your Ubuntu drive, and look at the /var/log/messages and /var/log/syslog and other files in /var/log. This does not sound like a laptop. My laptop occaisionally freezes early into the boot, and it appears to be battery related.

---

### Post by BuXXi on 2007-11-23
Cannot find anything interesting i the logs, attaching the messages-log and a photo what's visible when it has hanged.

[http://www.pici.se/pictures/KODlLjWpd.jpg](http://www.pici.se/pictures/KODlLjWpd.jpg)
[http://www.omfilm.net/users/buxxi/messages.txt](http://www.omfilm.net/users/buxxi/messages.txt)

---

