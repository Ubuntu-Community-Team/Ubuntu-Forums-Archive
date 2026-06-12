---
title: "Kubuntu Wireless Setup"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by Hangetsu on 2006-03-29
OK, I managed to trash my Ubuntu installation - Not surprising, but I'm learning alot as I trash my machine :D

I'm going to put in a new install using Kubuntu -- I like the KDE interface better than GNOME personally.  However, I'd like to get some information regarding Kubuntu before I try again.

I have a WPA2 - protected wireless network (AES), and I have a NetGear WG311v3 card installed.  With Ubuntu, setting this up is a breeze with ndiswrapper, ndisgtk (gui for ndiswrapper), and wpa_supplicant.

Are these all available for Kubuntu?  When I tried Kubuntu last night, it didn't seem to have ndiswrapper available for use.  Also, is there an equivalent to ndisgtk for KDE (or is ndisgtk independent of windows environment)?

From what I've read doing a search on these boards, wpa_supplicant should install the same way as with straight Ubuntu - Is this the case?

Thanks again for the help everyone.  The community support for this distro is absolute fantastic, I just hope I learn enough someday to return the favor to future newbies moving from Microsoft!!

---

### Post by Hangetsu on 2006-03-29
Uh oh.  No responses...  That's worrying me.


(Yes, its only been 90 minutes, but I hoped this was an easy one :p)

---

### Post by sailor2001 on 2006-03-29
ndiswrapper.sourceforge.net/

---

### Post by Hangetsu on 2006-03-29
Should I grab the file from there?  If I don't use debian packages, I thought I had to rebuild the kernel...

---

### Post by WoodyMahan on 2006-03-29
I am using a wireless card in my laptop.  I got it working in Ubuntu, then decided to install Kubuntu and all Kubuntu turned out to be was a slighlity different interface to the same stuff.  I didn't have to change anything as far as setup goes.  I would suspect that you can setup you wireless card with Kubuntu the exact same way as your Ubuntu install and it will be just as much of a Breez.

---

### Post by Hangetsu on 2006-03-29
That's what I thought as well.  The thing that threw me was that I couldn't run a sudo apt-get install ndiswrapper (I may have tried dpkg instead of apt-get, maybe that explains it).  I also only got my card working using the gui frotn end ndisgtk (which means I don't need it, but its easier for a newbie like me), and I wanted to find out if ndisgtk is going to install a bunch of GNOME libraries that I don't want / need.

---

### Post by WoodyMahan on 2006-03-30
In the K Menu of my Kubuntu Install, under Internet, I have a KWiFiManager.  This might help you.

---

