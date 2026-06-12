---
title: "PowerPC - How to upgrade from Ubuntu Hardy Heron (8.04) to Intrepid Ibex (8.10)"
date: 2008-10-30
forum: Apple Hardware Users
---

### Post by tiresia on 2008-10-30
To upgrade from Hardy Heron (8.04.1) to Intrepid Ibex (8.10)

**BACKUP IMPORTANT DATA AND CONFIGURATION FILES!!!**

1. **Option**
System > Software Sources > Updates 
Choose in 'Release Upgrade' >> Normal releases <<
Start the Update Manager

Here some important links:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)


2. **Option**
You can edit your /etc/apt/sources.list file replacing each occurrence of 'Hardy' with 'Intrepid' 
```
sudo nano /etc/apt/sources.list
```
Here is an example:
```
deb http://ports.ubuntu.com/ubuntu-ports/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted
```
Replacing 'hardy' with 'intrepid':
```
deb http://ports.ubuntu.com/ubuntu-ports/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu intrepid main restricted
```
Exit (ctrl+X) and save the file
When you are ready, run 
```
sudo apt-get update
sudo apt-get dist-upgrade
```

(I prefer using 'aptitude' instead of 'apt-get')

3. As always you can **download** the image from
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
[http://cdimage.ubuntu.com/ports/releases/intrepid/release/](http://cdimage.ubuntu.com/ports/releases/intrepid/release/)
[ftp://ftp.gnome-db.org/mirror/cdimage.ubuntu.com/ports/releases/intrepid/release/](ftp://ftp.gnome-db.org/mirror/cdimage.ubuntu.com/ports/releases/intrepid/release/)

[I]The second server is for the moment overloaded. 
You can find in this thread a torrent file:[/I]
[Download Ubuntu Intrepid for PowerPC - Torrent File]("http://ubuntuforums.org/showthread.php?t=963868")

:::::::
Read this **FAQ** before posting:
 [Where to download Ubuntu for PowerPC and other frequently asked questions]("http://ubuntuforums.org/showthread.php?t=427714")
:::::::

enjoy!

---

### Post by moviemaniac on 2008-10-31
Thanks very much for this great guide!
Just one question: Is there any way to change the sources list in the alternate install-cd so that it works too?

---

### Post by tiresia on 2008-10-31
Sorry, but I don't understand what you mean. Do you want to install with an Installer a different version from that one on the cd?

---

### Post by moviemaniac on 2008-10-31
No. The problem is, as I stated in the other thread ([http://ubuntuforums.org/showthread.php?t=964208](http://ubuntuforums.org/showthread.php?t=964208)) that the installer doesn't recognize the CD - no matter if I boot from it or start the install-script on the cd to upgrade. The error also has something to do with the installer not finding the sources on the cd so I suspect wrong entries in the sources-file on the cd.

//edit: Apparently these two bugs have nothing in common, someone already filed a bugreport: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608)

---

### Post by tiresia on 2008-10-31
The link in your last post is incorrect :) 
Anyway, it seems that there is a bug in the Intrepid Installer CD for PowerPC, so that it can't see the Optical Driver - most probably because the kernel doesn't have the right module for it. Here more about it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608)

As suggested there (I haven't tried yet - but see the post of [olarilole]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260608/comments/5")), you can try to load the right module switching to a second cosole (ctrl+alt+F2) and typing:```
modprobe ide-scsi
```
After that, when you are asked for a cd device choose /dev/scd0

---

### Post by moviemaniac on 2008-10-31
Hmmm... the links do work for me...

I'll try the suggestion by olarilole once my brother comes back home with his Powerbook, thanks! :D

---

### Post by pxwpxw on 2008-10-31
I installed on my G5 powermac by using the net install miniso burned to a cd, and booted from that - no problem booting from the mini iso cd, and the net install does not look for a full install CD.
G5 is and early model 1.6GHz single processor, maybe that is relevant also.

---

