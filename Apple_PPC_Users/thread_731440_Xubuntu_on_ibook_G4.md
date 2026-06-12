---
title: "Xubuntu on ibook G4"
date: 2008-03-21
forum: Apple PPC Users
---

### Post by LinuxRT on 2008-03-21
Hey guyz, 

Back again, so decided to install xubuntu now, bc when going to Ubuntu my wallpaper is black, Nautilus cannot be launched bc of Bonobo error and all the applets from the desktop (e.g. battery, trash etc..). But once I boot the Live  xubuntu-7.10-desktop-i386(2).iso CD, It just won't install/start. 

I read a thread, but how do you change "splash" to "nosplash" in yaboot.conf , i can't pass that stage. 


sudo ybin --config /media/disk/etc/yaboot.conf - ?



Should I install Ubuntu 6.10 instead or another version of Xubuntu?

Thanks for you help!

---

### Post by LinuxRT on 2008-03-21
I forgot to say once I pressed any key in the initial boot, it will change to yaboot version 1.3.13

---

### Post by slacka-vt on 2008-03-21
Dude,

         Are you seriously trying to boot / install an Ubuntu i386 platform OS
on your iBook G4 PPC ?
i386 is for an Intel Mac (i.e. 2006 Mac's and newer with Intel processors)

For an iBook G4, download and burn this ISO, this is your best bet.

[Hardy Mini.iso Net-Installer]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-powerpc/20070308ubuntu33/images/powerpc/netboot/")

another alternative that has worked for your type of machine is this live cd:

[Hardy Pre-Release Live Cd + Installer PPC]("http://cdimage.ubuntu.com/ports/daily-live/current/hardy-desktop-powerpc.iso")

---

### Post by LinuxRT on 2008-03-22
So I went took your advice and install the mini.iso. (Net-installer)

But the only problem is that after i decide to put the ubuntu archive mirror as "ports.ubuntu.com" or "http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/"

The install will no go further bc i have no internet. How can I fix my DHCP/Airport Extreme during installation?

Thanks again

---

### Post by adelahunty on 2008-03-22
LinuxRT,

Airport (for me at least) has always been a complete beeyatch to get going.  To be frank, I never bother with wireless on an iBook as life is way too short to get up n' going.  I am sure there is a way, but I haven't found it.  Someone with better knowledge and more time may have the answer...

If you don't have a network of any kind, then you are royally stuffed if you are trying to install via a network.  There are two options:

1 - If you are going through a wireless router for your internet connection at home, then there's usually a few wired ports at the back of the router modem.  This means that you can plug in an ethernet cable to the iBook, and that should allow you to do a wired connection.  From there, a network install is more than possible. :-)

2 - Don't use a network install disk in order to get your computer going.  Again, try Xubuntu, but make sure you get the ppc version, and not the i386 one you seem to have downloaded.  If you want the desktop version, then download [THIS FILE LINKED TO HERE](http://cdimages.ubuntu.com/xubuntu/ports/releases/feisty/release/xubuntu-7.04-desktop-powerpc.iso), which is the bunny you'll need.  I've linked to Feisty (7.04) as this seems to be a little happier for some reason than Gutsy (7.10).  From there, you can have a quick play, and then do an install by clicking an icon.  Easy-peasy.  It'll run fine on your G4, as it is more than happy on my G3 Graphite Clamshell.

2a - If that disk doesn't work for some reason, then go to the cdimages site, and get hold of the Alternate install for Xubuntu, which is this one [HERE](http://cdimages.ubuntu.com/xubuntu/ports/releases/feisty/release/xubuntu-7.04-alternate-powerpc.iso).

Actually, I notice that you downloaded from the UK - if you live there / here, and you're having extraordinary issues downloading said files, I can pop one in the post for you Tuesday when everything opens again....

---

