---
title: "Considering Ubuntu Linux: Is Linux MCE compatible?"
date: 2008-01-26
forum: Apple Intel Users
---

### Post by maneeshpan on 2008-01-26
I am considering installing Ubuntu Linux but want to use Linux MCE with it. I was under the impression all Linux programs will work with any and all distributions but now I hear something about Linux MCE being made for Ubuntu's cousin Kbuntu.

I want Linux MCE or a similar program for Ubuntu. If I get Ubuntu could I run Linux MCE? If not what alternative is there? If not also why not? If not does this mean not all Linux software works with all Linux distros? I am running Mac OS X on an Intel based Apple Mac Mini with Intel Core Duo processor -- this is a last generation Mac Mini the newer ones have Intel Core 2 Duo processor -- I also have Mac OS X Tiger (10.4.11) and QuickTime + iTunes 7.6 for Mac. I have a separate Windows PC running XP Prof Sp2.

My Mac Mini has Front Row software and Apple Remote the Windows PC obviously lacks Media Center -- I want Linux also with Media Center related capabilities.

Any suggestions on Ubuntu versus Kbuntu? I already have an Ubuntu CD but if I need Kbuntu that's what I'll get to use.

Can Boot Camp in Leopard be used for installing Linux the same way its designed to make Windows work? 

Thanks!

---

### Post by cyberdork33 on 2008-01-26
> **maneeshpan said:**
>  Can Boot Camp in Leopard be used for installing Linux the same way its designed to make Windows work?It will partition the drive for you, yes, but you will have to do some other changes after that. There are quite a number of threads here explaining that.

There are other linux media center software packages. MythTV and LinuxMCE are probably the most popular and there are several distros aimed specifically at setting up a media center pc. I think that LinuxMCE has one too. 

It does indeed look like LinuxMCE uses Kubuntu, but it may install on normal Ubuntu and install all the dependencies. This will cause it to take up much more disk space though as it would be like installing kde and gnome on one install (not that you can't do that if you want).

[http://www.mythtv.org/](http://www.mythtv.org/)
[http://www.mythbuntu.org/](http://www.mythbuntu.org/)
[http://mysettopbox.tv/knoppmyth.html](http://mysettopbox.tv/knoppmyth.html)
[http://freevo.sourceforge.net/](http://freevo.sourceforge.net/)

---

### Post by maneeshpan on 2008-01-27
Thanks for the help! I'll get either Ubuntu or Kbuntu up and running whenever I get time and Linux MCE or Myth TV.

As for using Boot Camp to install Linux -- thanks for the tip -- partitioning for Linux then with Boot Camp is possible and just as easy as doing for Windows but I have to change some settings afterwards for the installation. of Linux.

---

### Post by cyberdork33 on 2008-01-27
> **maneeshpan said:**
> Thanks for the help! I'll get either Ubuntu or Kbuntu up and running whenever I get time and Linux MCE or Myth TV.

As for using Boot Camp to install Linux -- thanks for the tip -- partitioning for Linux then with Boot Camp is possible and just as easy as doing for Windows but I have to change some settings afterwards for the installation. of Linux.basically, you need to use botocamp to partition. Boot the live cd, use gparted to delete the created partition, then start the Ubuntu installer and tell it to install to the free space.

---

