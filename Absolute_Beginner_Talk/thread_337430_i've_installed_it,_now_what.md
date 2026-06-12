---
title: "i've installed it, now what?"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by estin on 2007-01-13
First off, i've been using windows forever so i'm completely new to well........anything but windows. So after being constantly driven nuts by xp for years now, i've ditched it and now i'm using Ubuntu. 
The things i miss most are my programs like dvd shrink, flashfxp, and the use of my wireless laptop card.  So i'm curious if anyone can shed some light on backing up dvd's and basic FTP with ubuntu.  and if i can get my wireless card working, that would be a plus too.  thanks in advance everyone.

---

### Post by aysiu on 2007-01-13
For DVD Shrink, this thread may help:
[DVDShrink and DVD Decrypter equivalents for Ubuntu? Recommendations?](http://ubuntuforums.org/showthread.php?t=249715)

For FTP, you can use the file browser (Nautilus), the FireFTP extension for Firefox, FileZilla Beta, FileZilla for Windows using Wine, gFTP, KFTPGrabber, KBear, and a bunch of other programs. If you don't know how to install or browse for software, read this:
[http://www.psychocats.net/ubuntu/installingosftware](http://www.psychocats.net/ubuntu/installingosftware)

If you post the brand of wireless card you have, that may help.

---

### Post by finer recliner on 2007-01-13
FTP (by command line):
open a terminal (applications > accessories > terminal)
type "ftp servername.com" (without quotes)
enter your username and password as prompted
the commands for transfering files should be the same as windows (type "help" for a complete list of commands)

FTP using a GUI (graphic user interface):
places > connect to server
procede to plug in your information

if built in support does not meet your needs try gFTP:
easily installed by going to applications > add/remove... > internet > check gFTP > apply changes

---

### Post by Shatrat on 2007-01-13
One of the first, yet more painful, things you probably need to do is get your graphics chipset working.  At least, if you have an ATI or an Nvidia graphics chipset in your laptop it probably wont be up to its full potention with 3D and everything until you install their proprietary driver which can't be redistributed with ubuntu (yet).

Nvidia is pretty easy to do, ATI isnt as hard as it used to be.  Check out the Multimedia section and use the search, theres a million threads on it and some good how-tos.

---

### Post by tchoklat on 2007-01-13
You can get an FTP client through Synaptic, In think it is GFtp
 
sudo aptitude update
sudo aptitude install gftp
 
Also install Wine and and you can install and use dvd shrink also. Note that there are guides on this if you search these forums and the ubuntu wiki
 
tchoklat

---

### Post by estin on 2007-01-13
ok, my wireless card is a broadcom 802.11g  normally i just connect to my linksys router for internet but right now i have to use the ethernet cable or nothing.   i guess right now i kinda feel like i jumped in the ocean without a life jacket, although i refuse to go back to XP just cause i don't know what i'm doing right now.

---

### Post by seijuro on 2007-01-13
I use gFTP myself I like it quite a bit, fast and simple.

---

### Post by tonyr1988 on 2007-01-13
For your wireless, check out [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") link. Do what it says (to get to your terminal, Applications -> Accessories -> Terminal) to see if you have that particular Broadcom chipset. If you do, click one of the links at the bottom of that page, depending on your version of Ubuntu and it'll tell you how to install the driver. It looks fairly painless, but if you get stuck at any of the steps, feel free to ask.

Good luck! Did you have any other big concerns? Once you get everything up and running fine (it'll take longer to get all the drivers than it did in Windows - sometimes because of legal reasons), you'll never want to go back. Unlike in Windows, your system won't slowly degrade and get slower and slower over time. :) It only gets better from here...

---

### Post by raul_ on 2007-01-13
> **aysiu said:**
> For DVD Shrink, this thread may help:
[DVDShrink and DVD Decrypter equivalents for Ubuntu? Recommendations?](http://ubuntuforums.org/showthread.php?t=249715)

For FTP, you can use the file browser (Nautilus), the FireFTP extension for Firefox, FileZilla Beta, FileZilla for Windows using Wine, gFTP, KFTPGrabber, KBear, and a bunch of other programs. If you don't know how to install or browse for software, read this:
[http://www.psychocats.net/ubuntu/installingosftware](http://www.psychocats.net/ubuntu/installingosftware)

If you post the brand of wireless card you have, that may help.

The install software link is broken

---

### Post by Soarer on 2007-01-13
> **raul_ said:**
> The install software link is broken

Its just a typo: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by aysiu on 2007-01-13
My typing was crap last night. I had a typo in another thread as well. Thanks for the correction.

---

### Post by Threbus5 on 2007-01-13
Hi,

I had the wireless problem too.

My solution:
(1) opened the Ubuntu system configs for networking and enabled the wireless card with the proper IP address (I use fixed LAN addresses but the automatic DNS should work ok)
(2)copied the router's hex encryption code from the router or wireless access point's config. This was accessible via an internet browser.  And added that encryption code into the Ubuntu wireless config.
(3) otherwise duplicated the windows configuration for the wireless card on the Ubuntu machine
(4) if asked, saved the congifuration and 
(5) restarted the Ubuntu machine 

Note:
I had problems with the wireless card being enabled and then with it not quite connecting to the secure wireless net. The wireless card LEDs indicated that it was powered on and connected to the secure LAN (but it was lying.)
It helped to temporaily disable the wireless security on the (wireless access point or router) and then determine that everything linked in the clear before building the security settings.

The howtos in this forum contain significant help that should solve your problems. Look around.

Your move from windows is probably wise. After all, when was the last time that you used Windows XP compatible programs on a machine that had a 5 Gb hard drive, 333 MHz processor and 192 Mb RAM? Ubuntu is fast, friendly, and secure - and it has a marvelous support group.

Best wishes.

---

