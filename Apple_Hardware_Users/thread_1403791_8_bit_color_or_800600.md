---
title: "8 bit color or 800*600"
date: 2010-02-10
forum: Apple Hardware Users
---

### Post by Bq32 on 2010-02-10
So, I've had a problem with the monitor on Xubuntu for a while, so far. Currently, I am running Xubuntu 9.04 on a PowerMac G4 with 16MB VRAM, and I know, so far:

"ati" calls 1280x1024 "unsupported".
"FbDev" works with a great res, but 8-bit color.
"r128" seems to work with modprobe, and is just a wraparound to "ati" (or vice-versa?)
"FbDev" hates different FbBpp's and Color depths.

---

### Post by James M on 2010-02-11
Welcome to Linux. You have an ATI card? I'm sorry man but that is gonna give you hell. ATI doesn't support linux well.

---

### Post by Bq32 on 2010-02-13
> **James M said:**
> Welcome to Linux. You have an ATI card? I'm sorry man but that is gonna give you hell. ATI doesn't support linux well.

Unfortunately, I can't use any other card. When I put in another AGP, my screen doesn't load. Not even at bootup. I updated to Karmic, still nothing changed.

---

### Post by Bq32 on 2010-02-17
And Debian doesn't seem to want to load at all. Can anyone ese help with this?

---

### Post by linuxopjemac on 2010-02-17
what did you try ? I would advide the netinstall ppc version...
[http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso)

---

### Post by Bq32 on 2010-02-17
> **linuxopjemac said:**
> what did you try ? I would advide the netinstall ppc version...
[http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso)

NetInstall, don't you have to have internet connection for it? I have an Airport 802.11b in my comp right now, but it can cut out at points. Is there any way I can locally have the packages, on another hard drive, for example?

---

### Post by linuxopjemac on 2010-02-17
you need a working internet connection for this, normally wired suffices. But you don't have that, then I would not go for that. I would then go for a full CD installation.

[http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/](http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/)

If you have a working airport in a Linux live environment via a liveCD like Ubuntu or Debian, you might want to take a look at hard disk installation, without removable media:

[http://www.bucksch.org/1/projects/debian/crossinst/](http://www.bucksch.org/1/projects/debian/crossinst/)

---

### Post by Bq32 on 2010-02-20
> **linuxopjemac said:**
> you need a working internet connection for this, normally wired suffices. But you don't have that, then I would not go for that. I would then go for a full CD installation.

[http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/](http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/)

If you have a working airport in a Linux live environment via a liveCD like Ubuntu or Debian, you might want to take a look at hard disk installation, without removable media:

[http://www.bucksch.org/1/projects/debian/crossinst/](http://www.bucksch.org/1/projects/debian/crossinst/)

So, I finally got Debian up via NetInstall (I only had 1 CD, so I figured I'd try it), and I'm now back where I started. Should I find Debian forums, then?

---

### Post by linuxopjemac on 2010-02-21
You mean that X works the same as in Ubuntu ?

---

### Post by Bq32 on 2010-02-21
> **linuxopjemac said:**
> You mean that X works the same as in Ubuntu ?

It's exacly the same, except with GNOME UI. 800*600 with no driver, 8-bit with FbDev. ati and r128 have no found driver, and won't install.

---

### Post by Bq32 on 2010-02-21
I got my computer running smoothly in 1280*1024 24bit color. What the problem was was that I had the wrong HorizSync set up, it had to be 70.0.

---

### Post by linuxopjemac on 2010-02-21
Finally success !!!

---

### Post by linuxopjemac on 2010-02-22
Can you post your working Xorg.conf file and tell us what kind of monitor you are using please.

---

