---
title: "Ipod help!"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Kaare_K on 2008-03-29
Hey i've searched for the answer but I can't find it.

I am trying to mount my ipod touch in Gutsy and I'm having problems. I go through the wiki and follow it exactly, however when i go into Terminal and try to use the ipod-touch-mount command I get this output....

ping: unknown host 292.168.1.107
iPod is not responding to pings at 292.168.1.107.
Please set the environment variable IGNOREPING if you want to ignore this.

That ip the one I set in the installation of the ipod convince package and that's why my static ip on my ipod is set to. Any help would be appreciated!!

Thanks!

---

### Post by gobbles414 on 2008-03-29
> **Kaare_K said:**
> Hey i've searched for the answer but I can't find it.

I am trying to mount my ipod touch in Gutsy and I'm having problems. I go through the wiki and follow it exactly, however when i go into Terminal and try to use the ipod-touch-mount command I get this output....

ping: unknown host 292.168.1.107
iPod is not responding to pings at 292.168.1.107.
Please set the environment variable IGNOREPING if you want to ignore this.

That ip the one I set in the installation of the ipod convince package and that's why my static ip on my ipod is set to. Any help would be appreciated!!

Thanks!

What version is the firmware of your iPod Touch? Is you iPod formatted in HFS+ or FAT? Are you running Ubuntu on a Mac or a normal PC? Your answers will help me and others to help you.

---

### Post by ntetreau on 2008-03-29
> **Kaare_K said:**
> Hey i've searched for the answer but I can't find it.

I am trying to mount my ipod touch in Gutsy and I'm having problems. I go through the wiki and follow it exactly, however when i go into Terminal and try to use the ipod-touch-mount command I get this output....

ping: unknown host 292.168.1.107
iPod is not responding to pings at 292.168.1.107.
Please set the environment variable IGNOREPING if you want to ignore this.

That ip the one I set in the installation of the ipod convince package and that's why my static ip on my ipod is set to. Any help would be appreciated!!

Thanks!

Can you surf the web from your ipod?  If so double check again in the wifi settings fo your iphone that the ip address is the right one.  Ping is a very low level communication tool that just look on your network is there is anything that address.  If the ping comes back negative, I don' t there is network connectivity between the two devices.  Also, make sure that SSH is installed on your ipod touch although as i said before, your computer can' t even find a connected device at that address unfortunately.

---

