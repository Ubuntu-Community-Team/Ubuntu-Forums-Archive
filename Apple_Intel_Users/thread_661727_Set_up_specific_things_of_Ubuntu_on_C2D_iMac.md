---
title: "Set up specific things of Ubuntu on C2D iMac"
date: 2008-01-08
forum: Apple Intel Users
---

### Post by mattr01 on 2008-01-08
Hi.  I want to set up the following things on my iMac:

[LIST]
[*]Inbuilt Speakers/Mic
[*]Apple Remote
[*]wifi (if possible)
[/LIST]

when i plugged in my usb headset, there was a lot of static when playing music.

I also can't open various folders that are on my OSX partition:

[LIST]
[*]Documents
[*]downloads
[*]music
[*]movies
[*]desktop
[*]pictures
[*]library
[/LIST]

I tried chmodding it but it didn't work.  Does anyone have any ideas?

---

### Post by cyberdork33 on 2008-01-08
you need to be more specific about the hardware you have...

what iMac?

I am going to assume that you have an aluminum iMac since your audio is not working. Check the FAQ for patches to get the sound working. Unfortunately, I do not know if there is a way to get the mic working yet if the same patch does not enable it.

I can't say much for the remote as this works without configuration for most people. There are a few threads here discussing the setup of lircrc

Your wifi is likely a broadcom card like mine, and only really works well by using ndiswrapper. This is a kernel module that "wraps" a windows driver for your card, to be used in linux. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The Mac filesystem (HFS+) stores permissions on files the same way that Linux stores permissions in it's filesystems. Therefore, files and folders that are owned by your OSX user are NOT owned by the linux user, and are denied several actions. You should be able to access the files via root though! You can boot up OSX and be sure to set permissions there (as it seems not to work correctly when changing them under Linux for some reason).

---

