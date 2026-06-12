---
title: "Anyone had succes with pspi for Gimp in ubuntu 7.04"
date: 2007-07-03
forum: Art &amp; Design
---

### Post by filologen on 2007-07-03
I would like to use some photoshop plugins in gimp 2.3 (or alternatively 2.2) by using pspi, but haven't had any succes on my Ubuntu 7.04 setup.

Has anyone gotten this to work? 

Any help would be very appreciated.

---

### Post by filologen on 2007-07-07
Never mind - I figured it out by myself. It more or less worked out of the box (on 2.2.x as well as 2.3.x), but I had simply not set the permissions right.

---

### Post by joearf on 2008-03-01
Hi filogen, 

Wonder if you could be a little more specific about what you did. I'm having a problem using pspi, myself. 

I unpacked the pspi and pspi.exe.so files into my plug-ins directory [~/.gimp-2.4/plug-ins] and relaunched Gimp. I was expecting to see the warning mentioned in the readme file, but got nothing. When I went to the Xtns menu, there was no Photoshop Plugin Settings submenu. I tried copying the two files to both the application's plugins directory [/usr/lib/gimp/2.0/plug-ins] no luck with that either. 

There was yet another .gimp plugins sub directory in my home [.gimp-2.2/plug-ins] and, even though that was not listed under the folders in my Preferences->Folders->Plugins I tried placing the files in there, too. Still no success. 

After reading filogen's entry above I looked at the persmissions on the files and tried playing around with them - even 777'd them - and placed copies in each of the directories. Still no luck.

I have pspi working well on my Windows desktop, but it's not my primary machine, so I'd love to get it going here.

Using:
Ubuntu 7.10 [Gutsy Gibbon]
Gimp 2.4.2
gimp-pspi-1.0.5.ubuntu.i386.tar.gz. Ubuntu 5.10 binary


Thanks

--------------------------------

[LATER] Read in another discussion in this forum. A poster named Bogolisk says "pspi stopped working with gimp 2.3.1x on linux." Can anyone confirm this?

---

