---
title: "DVD not bootable"
date: 2011-11-09
forum: Any Other OS
---

### Post by tech291083 on 2011-11-09
Hi,

I have just downloaded Debian 6.0.3 i386 DVD version worth 4.4 GB and written is successfully to a DVD, but this DVD does not boot on any of the pcs I have tried it on despite changing the  boot sequence in the BIOS. Hre is the page that I have downloaded it from.

[http://cdimage.debian.org/debian-cd/6.0.3/i386/bt-dvd/](http://cdimage.debian.org/debian-cd/6.0.3/i386/bt-dvd/)

I have downloaded this one thinking they all are the same.

[debian-6.0.3-i386-DVD-6.iso.torrent]("http://cdimage.debian.org/debian-cd/6.0.3/i386/bt-dvd/debian-6.0.3-i386-DVD-6.iso.torrent")   

But I have just been told by a forum member QLee (link to his profile at the end of this post) that only the 1st DVD is bootable and he has also cited an official Debian FAQ for this, which comes as a total surprise to me. Is it true that only the 1st DVD is bootable? Why so? Thanks


> 
Only the first CD/DVD in a set is bootable.
 [http://www.debian.org/CD/faq/#bootable](http://www.debian.org/CD/faq/#bootable)


[http://ubuntuforums.org/member.php?u=934089](http://ubuntuforums.org/member.php?u=934089)

---

### Post by satanselbow on 2011-11-09
[http://www.debian.org/CD/faq/#bootable](http://www.debian.org/CD/faq/#bootable) gives a pretty good explanation and reasoning...

---

### Post by hhh on 2011-11-09
If you're looking for a bootable Debian desktop environment on a single DVD, you can use the Live images. They come in GNOME, KDE, Xfce and LXDE and you can install them to hard drive (from the live session too, if I remember correctly). Choose the CD/DVD/USB image for your architecture...

[http://www.debian.org/CD/live/](http://www.debian.org/CD/live/)

One quirk is that these images install with a feature that speeds up reboot time by bypassing Grub, so if you want to get into Grub to boot another operating system you have to shutdown first. Or you can remove that feature by running this in a terminal (assuming you're logged in as USER, not ROOT)...```
sudo apt-get purge kexec-tools
```

---

