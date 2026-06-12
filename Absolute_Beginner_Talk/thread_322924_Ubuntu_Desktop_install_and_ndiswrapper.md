---
title: "Ubuntu Desktop install and ndiswrapper"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by gnk979 on 2006-12-21
I was trying to install Ubuntu desktop and could not get my wireless card on my Desktop to work. The help showed that I could make it work with ndiswrapper and this is supposed to be available for install on the install image. I could not find any way to intall it. 

I had earlier tried PC Linux OS and with that the ndiswrapper was automatically installed and I could get my wireless to work.

I also have no way of moving my desktop which is on the second floor to my basement where the DSL router is and that that is not an option. 

Can someone help ?

---

### Post by jbutler12 on 2006-12-21
ndiswrapper comes by default.  unfortunately, ndiswrapper-utils (which gives a much friendlier way to use ndiswrapper) and the GUI ndiswrapper interface (which i dont recommend by the way) come on the CD.  Assuming you installed from a burned .iso (this worked for me on Edgy), put your Ubuntu CD in your CD rom.  Go to system->administration->Synaptic Package Manager and search for ndiswrapper-utils and install it.  Also install wireless-tools at the same place in the same way with the CD in the drive.  Once this is done, this article helped me a ton:

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

Post up any problems you may have.

-John
Use [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) and not the GUI tools.  Ive been running wireless fine using the command line and the GUI tools are still telling me the connection has failed.

---

### Post by gnk979 on 2006-12-21
> **jbutler12 said:**
> ndiswrapper comes by default.  unfortunately, ndiswrapper-utils (which gives a much friendlier way to use ndiswrapper) and the GUI ndiswrapper interface (which i dont recommend by the way) come on the CD.  Assuming you installed from a burned .iso (this worked for me on Edgy), put your Ubuntu CD in your CD rom.  Go to system->administration->Synaptic Package Manager and search for ndiswrapper-utils and install it.  Also install wireless-tools at the same place in the same way with the CD in the drive.  Once this is done, this article helped me a ton:

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

Post up any problems you may have.

-John
Use [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) and not the GUI tools.  Ive been running wireless fine using the command line and the GUI tools are still telling me the connection has failed.


I did use the Synaptic Package Manager and marked the ndiswrapper packages (and utils), but after the process starts, it tries to access the internet to download packages. I would like it to load it of the Live CD instead and I am trying a way to do it... 

Also being new I appreciate the support of the user community.

---

### Post by jbutler12 on 2006-12-21
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) walks you through how to do it.  See #6: Installing ndiswrapper-utils without internet access.  Also note that if you have Edgy, you need to istall ndiswrapper-utils-1.8

-John

---

