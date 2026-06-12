---
title: "Offline lightweight ubuntu installation from Boot CD and external drive?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by SunshineSmile on 2006-11-14
Hi guys!

I am contemplating installing a linux OS on an old Laptop with- at best- 64MB ram and 4GB Harddrive space. 

The laptop has no ethernet connection. I need it to work with a D-Link G122 USB Wlan adapter. 

This [Low Memory Wiki]("https://help.ubuntu.com/community/Installation/LowMemorySystems") says I can do a server install from the boot CD and install lightweight applications. 

My problem: I won't be able to sudo apt-get fluxbox or any other stuff from the net after the server install, unless I am absolutely sure that my WLAN is supported. Therefore, I'd like to know the following:

1) can I install the server-version, and manually install the programs I need from an external drive? 

2) Any recommendations for which programs I should use on this shitty laptop? I want to surf the net mainly. What do I need to download besides a desktop program like fluxbox and a browser?

3) Now, besides learning the basic commands properly, to navigate and copy these programs from my external drive- Where do I learn how to install them? Does fluxbox etc only need to be untar'ed in the right directory? Which one? Anybody willing to point me in the right direction?

---

### Post by deadgobby on 2006-11-14
It seems that your ram may be not nuff to get Ubie running. However, xubuntu may be the one to make that little engine to run. It has the basics and be able to surf the net.
Gobby

---

### Post by bodhi.zazen on 2006-11-14
> **SunshineSmile said:**
> Hi guys!

I am contemplating installing a linux OS on an old Laptop with- at best- 64MB ram and 4GB Harddrive space. 

Try fluxbuntu

[[color=darkgreen]Fluxbuntu[/color]](http://fluxbuntu.org/)

It is in develpment, but very functional.

[[color=darkgreen]Download Fluxbuntu[/color]](http://fluxbuntu.ninjapenguins.net/fluxbuntu-nbuild1-revision2/fluxbuntu-nbuild1-rev2-desktop-i386.iso)

MD5 sum:
c054428c46a1b5ffaab4295bc7db3c9b  fluxbuntu-nbuild1-rev2-desktop-i386.iso

---

### Post by SunshineSmile on 2006-11-14
> **bodhi.zazen said:**
> Try fluxbuntu

[[color=darkgreen]Fluxbuntu[/color]](http://fluxbuntu.org/)

It is in develpment, but very functional.


Whoa.. hold on.. I already checked out fluxbuntu, but that stuff is under development. Does the distro have my D-link WLAN driver then?  I mean, Damn Small Linux is also fast and would work, but I can't get my D-Link working with that.. so if fluxbuntu can't either, and ubuntu can- well that's why I thought of server-installing ubuntu, and use fluxbox with it. 

I don't know what fluxbuntu can... Is the fluxbuntu I got from your link a bootable CD? (only have one blank CD left :-D )

---

### Post by bodhi.zazen on 2006-11-14
> **SunshineSmile said:**
> Whoa.. hold on.. I already checked out fluxbuntu, but that stuff is under development. Does the distro have my D-link WLAN driver then?  I mean, Damn Small Linux is also fast and would work, but I can't get my D-Link working with that.. so if fluxbuntu can't either, and ubuntu can- well that's why I thought of server-installing ubuntu, and use fluxbox with it. 

I don't know what fluxbuntu can... Is the fluxbuntu I got from your link a bootable CD? (only have one blank CD left :-D )

Yes it is a bootable or Live CD. If you like you can also install.

I do not know about your D-Link, but:[list=number][*]Fluxbuntu is 100 % Ubuntu compatible.[*]You can get help at the [Fluxbuntu irc](irc://irc.freenode.net/#fluxbuntu)[/list]

IMO, in your situation, I would most certainly fluxbuntu before I server installed (less hassle).

---

### Post by zytsef on 2006-11-14
Check the wiki for support for specific wireless cards. It's a very useful resource and is usually up to date: [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Looks like they even have something specifically for your card ;)

---

### Post by SunshineSmile on 2006-11-14
Well, if ubuntu, fluxbuntu and xubuntu all have the same WiFi drivers, then I guess it's a coin toss. My wireless worked with the xfld live cd, which is based on Edgy Eft, so I am excited to find out if fluxbuntu will work as well. Hold my hand now.. SPEED :D 

Thanks a lot for the helpful info so far. Now it is installation time!!

---

### Post by kerry_s on 2006-11-14
If all else fails try DSL linux, it's made for older machines -> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

