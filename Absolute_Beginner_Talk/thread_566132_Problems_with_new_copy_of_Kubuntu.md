---
title: "Problems with new copy of Kubuntu"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by ROJIRU on 2007-10-03
One of you guys suggested that I get kubuntu. Had problems downloading a copy so I bought one.
But kaffein does not play dvd's. I get the following messages: 
1)No plugin found to handle this resource.
2) The application kaffein player crashed and caused the signal ii CSIGSEGV - A BUG IN APPLICATION.
CAN ANYONE HELP. Thank you all in anticipation. Rojiru

---

### Post by arochester on 2007-10-03
If you are connected to the internet input the following command in a terminal > sudo apt-get install libdvdcss2 This will get you the codec. It is illegal to use in the USA and is not provided with the package.

---

### Post by ROJIRU on 2007-10-03
Thanks, but I'm having to use windows xp to access the internet, with a copy of firefox which i'm using instead of ms explorer. I'm trying to ditch Microsoft but keep getting problems. Also I live in the UK. so should n't be affected by us laws.

---

### Post by funpop on 2007-10-03
yes you need libdvdcss2

but it is not prvided by ubuntu. you can get it from the medibuntu repos, see here:


[http://medibuntu.sos-sts.com/]("http://medibuntu.sos-sts.com/")

or just download it here from videolan.org: [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb]("http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb")

---

### Post by ROJIRU on 2007-10-03
Thanks funpop, downloading VlC is one of my problems. I don't know whether it is because I am using windows xp. But i get the file, transfer it to my second computer via usb, load it onto ubuntu typr in the sudo command, it appears to work, but then I get some message about not being able to unwrap the paccage or something. Other downloads appear to give me the same trouble. I've just bought a copy of ubuntu, in case their was a problem with my loaned copy. but I've yet to install it.
Also i'm using a Belkin USB wireless thing-a-me-jig to receive the internet and I think that this is likely to be uncompatible.

---

### Post by funpop on 2007-10-03
*buntu without internet access is pretty boring :)

heres a thread that may help you to setup your belkin: [http://ubuntuforums.org/showthread.php?t=361287](http://ubuntuforums.org/showthread.php?t=361287)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

sounds pretty complicated for a beginner. no way to plug a cable into your computer :P at least for installation ??


if you transfer software, transfer them as .deb files. problem is: they have dependencies that may not be satisfied on your installation ...

---

### Post by ROJIRU on 2007-10-03
Thanks again, I'm really trying hard to ditch MS. I like what I see in both ubuntu and kubutu, so I'm just going to tough it out. But I'm not computer wise, I have to hack around for ages to get what I want. I'll research your suggestions and see what happens. I could do with someone local to show me how. The son in law is pretty good, he gave me my ubuntu copy, but he lives in Kent and I live in Worcestershire UK. I'll have to e-mail him. Rojiru

---

### Post by ushills on 2007-10-03
If you can access the internet from Ubuntu, read the following, hopefully you can connect your Ubuntu box to your internet router or similar.  Is it the same machine as you use XP from?

[http://ubuntuforums.org/showthread.php?t=413624]("http://ubuntuforums.org/showthread.php?t=413624")

It will guide you through.

You don't want to download programs in Windows and install in Linux, Ubuntu uses stores called repositories where the majority of software is kept.

For example to install vlc, one would open a terminal window (Applications > Accessories > Terminal) and enter the following.

```
sudo apt-get install vlc
```

That is all you need to do.

---

### Post by natman on 2007-10-03
Have youtried just installing Ubuntu and then downloading the KDE dsktop, that way you essentially have both in one.

---

