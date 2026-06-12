---
title: "Need internet to install - apparently"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by BillyMax on 2008-02-27
I'm trying to install programs/packages like ubuntu-restricted-extras with the add/remove tool thingy.

When i click to install it, it comes up with 'need to refesh list' and you 'must have an internet connection to do this' 

On that computer I don't have internet.

Is there any way around this?

---

### Post by aysiu on 2008-02-27
> **BillyMax said:**
> I'm trying to install programs/packages like ubuntu-restricted-extras with the add/remove tool thingy.

When i click to install it, it comes up with 'need to refesh list' and you 'must have an internet connection to do this' 

On that computer I don't have internet.

Is there any way around this?
There *are* ways around this, but they're not simple.

Your best bet may be APTonCD:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by benpage26 on 2008-02-27
If you are using aptitude / apt-get / synaptic package manager their purpose is to get software 'packages' from the internet and install them.  

The way around it would be to download the .deb files (these are the extensions for the packages) from another computer then transfer to the non-internet box to install.

Alternatively it may be easier to temp/permanantly connect the machine to the internet.  Is there any reason it is not connected to the net?

---

### Post by markbusu on 2008-02-27
Are you trying to configure Wifi or a normal Ethernet Cable Network Card?

What Wifi Card do you have? You might consider downloading the Package from another machine and moving it over to your Ubuntu Installation using CD / USB Stick...

---

### Post by jan quark on 2008-02-27
you can also try to download the deb package on a machine with internet connection and transfer it to your pc without inet on a usb stick or cd:

[http://rpmseek.com/rpm/ubuntu-restricted-extras_9_i386.html?hl=com&cs=ubuntu-restricted-extras:PN:0:0:0:0:3961952](http://rpmseek.com/rpm/ubuntu-restricted-extras_9_i386.html?hl=com&cs=ubuntu-restricted-extras:PN:0:0:0:0:3961952)

---

### Post by aysiu on 2008-02-27
> **jan quark said:**
> you can also try to download the deb package on a machine with internet connection and transfer it to your pc without inet on a usb stick or cd:

[http://rpmseek.com/rpm/ubuntu-restricted-extras_9_i386.html?hl=com&cs=ubuntu-restricted-extras:PN:0:0:0:0:3961952](http://rpmseek.com/rpm/ubuntu-restricted-extras_9_i386.html?hl=com&cs=ubuntu-restricted-extras:PN:0:0:0:0:3961952)
You'd need more than just the .deb, since *ubuntu-restricted-extras* is a metapackage that just points to other packages. It does not actually contain all the packages it will install. And one of the packages it installs doesn't even contain the software it installs (*flashplugin-nonfree* takes the Flash plugin off the Adobe website).

---

### Post by jan quark on 2008-02-27
> You'd need more than just the .deb, since ubuntu-restricted-extras is a metapackage that just points to other packages. It does not actually contain all the packages it will install. And one of the packages it installs doesn't even contain the software it installs (flashplugin-nonfree takes the Flash plugin off the Adobe website).

thanks for getting this straight aysiu

I guess you need to look for these deb packages

[LIST]
[*]gstreamer0.10-plugins-ugly 
[*] gstreamer0.10-plugins-ugly-multiverse 
[*] msttcorefonts 
[*] flashplugin-nonfree this you can download here [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
[*] sun-java6-plugin 
[*] unrar 
[*] gstreamer0.10-plugins-bad 
[*] gstreamer0.10-plugins-bad-multiverse 
[*] gstreamer0.10-ffmpeg 
[*] liblame0 
[*] libdvdread3
[/LIST]

---

### Post by aysiu on 2008-02-27
Unfortunately, it gets quite complicated. While some of those dependencies are independent packages (unrar, liblame0, and libdvdread3), a lot of those dependencies are also metapackages that point to other packages, and I'm pretty sure msttcorefonts and sun-java6-plugin pull stuff off the internet.

---

### Post by BillyMax on 2008-02-27
I suppose it might just be easier to buy/get convertors for my music etc...

It wouldn't be easy to connect to internet. Not for any software/ubuntu/computer related reason though.

---

