---
title: "Install Ubuntu over Kubuntu"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by notbitmonk on 2007-08-07
I would like to do a clean install of Ubuntu.  Right now I have a dual boot of XP and Kubuntu.  Last time I tried re-installing Kubuntu  it messed up my dual-boot to the point that I had to install both OSs.  I won't like to do that again and this is not to have the Gnome desktop manager.  I do not have an internet connection so I won't be able to download anything if it were needed.  Can you provide some help? TIA

---

### Post by Inxsible on 2007-08-07
The only difference between Ubuntu and Kubuntu is the desktop manager.

you can do this in order.

```
sudo aptitude install ubuntu-desktop
``` then log out and login again into GDM instead of KDM.

Once into GDM, you can remove KDM by

```
sudo aptitude remove kubuntu-desktop
``` that way you will have a pure Gnome desktop.

Try this [link]("http://www.psychocats.net/ubuntu/puregnome") for a much more detailed explanation.

---

### Post by Damanther on 2007-08-07
If you feel like you need a clean install and you have a Ubuntu CD you can install it, then add the kde desktop at a later point. Or keep the Gnome desktop if you like it.

You will probably want an active internet connection for updates though.

---

### Post by por100pre1 on 2007-08-07
Can you get an Ubuntu CD somehow? If you can, get it, insert it, and install ubuntu-desktop with apt-get or Adept. Hope that helps. :)

---

### Post by stchman on 2007-08-07
> **notbitmonk said:**
> I would like to do a clean install of Ubuntu.  Right now I have a dual boot of XP and Kubuntu.  Last time I tried re-installing Kubuntu  it messed up my dual-boot to the point that I had to install both OSs.  I won't like to do that again and this is not to have the Gnome desktop manager.  I do not have an internet connection so I won't be able to download anything if it were needed.  Can you provide some help? TIA

Boot up the Live CD and remove the EXT3 and swap partitions.  Make sure you have your data backed up.  Leave the partitions as free space.

On the install tell Ubuntu to use the largest free space.

---

### Post by notbitmonk on 2007-08-07
> **stchman said:**
> Boot up the Live CD and remove the EXT3 and swap partitions.  Make sure you have your data backed up.  Leave the partitions as free space.

On the install tell Ubuntu to use the largest free space.

I do have the LiveCD and what you said was what I did the last time and I ran into some trouble.  I believe that is the only way to do it.  About deleting the partition and swap file I can do it with no trouble however I can not select the largest continuous space because that will be my second hard drive.  How big should I make the swap file?

---

