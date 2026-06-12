---
title: "Replacing imac OS question"
date: 2021-05-09
forum: Apple Hardware Users
---

### Post by guytas on 2021-05-09
Hi everyone.  I just tried the ubuntu from an USB stick.  I was impressed.  But I'm scared a little bit to loose my stuff from the Windows side.  I dont rely too much on backups.  I do have backups of my data, documents and photos but there are always something scary about this.  Anyhow...  let me explain more...

I have an old iMac 2013 with 1tb SSD drive. 400 gig for Mac OS and 600 for Windows 10.  I'm thinking to replace the Mac OS with Ubuntu. But at the moment, when I'm in Windows, I can click on the "Boot camp" icon and select to reboot from OS X. Then, from that point on, every reboot starts with OSX.  This is want I like and what I want to keep.  I mean.  not from OSX anymore but in Ubuntu.  And... to comes back to reboot all the time in Windows, I go in the system configuration of the OSx and choose to reboot from Windows.  How is this going to be done in Ubuntu?

I do not want to keep a WIRED keyboard just to be able to hold the ALT key to select a boot.

Am I heading for troubles????

Thanks

---

### Post by grahammechanical on 2021-05-10
> How is this going to be done in Ubuntu?

It is not done in Ubuntu. Not without manually changing configuration files every time we want to set the new OS boot priority. When we dual boot Linux with another OS or even with another Linux OS we get a boot menu that has a default OS to boot after about 10 seconds or we can select another OS to boot. But changing the OS boot order in that menu is not so easy and Ubuntu does not have a utility that will let us make the change. Changing the OS order in that menu requires editing a configuration file and overwriting the existing file with the edited file.

I am surprised that Microsoft provided a utility to make such a switch. Perhaps it is not a Microsoft application.

You might want to consider Grub Customizer.

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

[https://tipsonubuntu.com/2018/03/11/install-grub-customizer-ubuntu-18-04-lts/](https://tipsonubuntu.com/2018/03/11/install-grub-customizer-ubuntu-18-04-lts/)

You will see that to install Grub Customizer in Ubuntu 18.04 we install a PPA (Personal Package Archive), But in Ubuntu 20.04 Grub Customizer is now available through the Ubuntu Software Store (also called Software) that is part of every Ubuntu installation.

It is a long time since I experimented with Grub Customizer. I expect that it has been improved since I last used it. But as it has been so long since I tried it (I no longer have need for it) that I am not qualified to comment on its usability. 

Regards

---

### Post by slickymaster on 2021-05-10
*Thread moved to **Apple Hardware Users**.*

---

