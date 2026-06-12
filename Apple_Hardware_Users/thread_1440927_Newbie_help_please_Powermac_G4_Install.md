---
title: "Newbie help please Powermac G4 Install"
date: 2010-03-28
forum: Apple Hardware Users
---

### Post by strangesteve on 2010-03-28
Hi folks this is my first post, I have just been given a powermac G4 running os 9.

Managed to download ubuntu 9.04 for powerpc on it. Its an iso file.

Could someone tell me how to mount it and burn it onto a CD. Unfortunately I.E. is so old its not compatilble with most websites for downloading utilities and just keeps crashing.

There doesn't seem to be any apps on the machine that will recognise the iso file. Its connected to a router that has a couple of vista machines on it, I suppose if it could see the windows machines it would be easy to drag utils over etc. 

I would really like to get ubuntu going on this, this is my first dabble with Linux and Macs.

OS9 kinda reminds me of windows 3 !!!

Cheers

Steve

---

### Post by linuxopjemac on 2010-03-28
I recommend you to use another computer to burn the iso to a CD. I would burn it at low speed, otherwise your old Mac might have problems reading the CD. Another advise, if you want a little bit less painful installation experience I recommend you to install Debian with a wired internet connection (a Netinstall). Iso's for that can be downloaded here:
[http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso)

[http://forums.debian.net/viewtopic.php?f=16&t=20481&sid=8d82bee84e533cf0669cfb57c6a33f66](http://forums.debian.net/viewtopic.php?f=16&t=20481&sid=8d82bee84e533cf0669cfb57c6a33f66)

You will have a problem with X11 (the GUI). You will need to adapt the xorg.conf file to your needs as this will probably not be done well.

---

### Post by penguirl on 2010-03-28
@strangesteve The important thing to remember when burning an OS install disc, at least with Ubuntu/Debian & OS X is NOT to mount the image before you burn it, you want to burn the image as is. Burning it at the lowest possible speed is also very good advice.

@linuxopjemac In my search for a distro that I liked and worked well on my iMac I tried to install Debian but as you mentioned I ran into a problem with the GUI and correcting it seemed beyond my abilities, what do you modify in xorg.conf to get it working? Does Debian have the same shifted right display issue that Ubuntu does on widescreen iMacs?

---

### Post by linuxopjemac on 2010-03-28
debian has the same issues as Ubuntu, so you will have the same shift problem. You can edit the xorg.conf file yourself. there are fixes:
[http://mac.linux.be/content/howto-fix-20-g5-imac-display-shift-nv-debian](http://mac.linux.be/content/howto-fix-20-g5-imac-display-shift-nv-debian)

---

