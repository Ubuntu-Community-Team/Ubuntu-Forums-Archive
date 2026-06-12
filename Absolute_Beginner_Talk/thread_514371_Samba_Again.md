---
title: "Samba Again"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-07-31
Hi,

I have 2 Toshiba laptops one running XP and other Kubuntu. I have been using kubuntu for around 2 months now and its doing great. Now until about two weeks ago everything was working fine. I dont know what happend, but for the last two weeks I can access the shared folder from windows but I cant get to access anything on the windows laptop from the kubuntu laptop. I tried setting up samba. I have a zonealarm firewall, I made sure that my Kubuntu Ip was in the trusted zone. I have no idea what happened..everything was working fine.

I set up samba according to the instructions given on this thread:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

My network setup is like this. I have a Belking G router connected to the cable modem which provides the internet. And 3 laptops (one is my room-mate's) wirelessly connected to the router. And 2 of my laptops wirelessly connected using Samba.

Any help is greatly appreciated!
Thanks.

---

### Post by linuxnovice on 2007-08-02
Bump

---

### Post by JAPrufrock on 2007-08-02
> **linuxnovice said:**
> Bump

Don't know if this will help, but I've had problems, every once and a while, of my IP addresses changing (router temporarily insane), which can screw up samba, as well as ssh.

---

### Post by linuxnovice on 2007-08-03
Yes but I have set it up that all my machines get the same IP all the time.

---

### Post by dca on 2007-08-03
Is the WinXP laptop shared out?  Also, make sure file/print sharing option selected in folder options, right-click My Computer and select remote access.  Check the two setting(s) allowing remote access to XP box.  You may have to add a login name to the second (bottom) remote access settings...

---

### Post by dca on 2007-08-03
I doubt this will be any help but the way I've always done it in my home network was by creating a box as a central server.  When I was making a half-a$$ attempt to learn AIX I inherited an old Penguin server w/ dual PIII 1Ghz processors and quite a bit of ram.  Loaded it up w/ four 40GB HDD and installed Ubuntu 6.06LTS server ed w/ RAID 0.  It was basically a head-less server from the get go.  Just sat in the washer/dryer pantry connected directly to the wireless router via one of the four RJ45 ports.  Now, at the time, there was me and my laptop, the wife and her PC, my cousin and his laptop, and a few others.  If large files needed to be xferred anywhere or to each other the central server was the go between so no other tweaking would need to be done on my Linux laptop or my wife's XP PC.  Each person had a Samba login/share on the server.  The nice thing was all the music I d/l or ripped were stored there and the box used rsynch to make b/u to an external drive...

---

### Post by linuxnovice on 2007-08-03
Well that is what I would eventually want to do...but I am a student and I dont have much time to tweak around that alot. I bought the second laptop for the only reason that I could tinker with linux :) 

The folder's I want to share in windows are shared (they have a hand below their icon) The funny thing is, it was working properly. A week ago, I went to my sister's place and their internal network using a different ip schema. Maybe the ubuntu box got confused or something....

---

### Post by dca on 2007-08-03
Could be, but that's pretty much why I only share out at one source.  Nobody should need to access any files on my laptop.  Now I understand that the PCs in my house are wireless and stationary but still.  I don't want to access them, I would rather allow access to one source which makes the whole thing easier from a network/sys admin perspective to manage.

---

### Post by linuxnovice on 2007-08-03
My linux box has more space on it. So after I got this machine I store all my movies here. The thing is, when I play them, sometimes the video gets stuck because its streaming over the network rather than playing from the hardrive. I dont know whether this is an isolated issue..

---

