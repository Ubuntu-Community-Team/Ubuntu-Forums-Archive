---
title: "BT internet connection worries"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by deuchar1 on 2007-03-19
Hi guys,

I recently installed Ubuntu to dual boot alongside my XP install after a recommendation from a friend and things seem to be going well.

I've just ordered BT broadband and will be receiving their Home Hub. I noted their software only works with Windows - will it be possible for me to get the Hub working on Ubuntu 6.10 so I can use it to access the internet?

My worry is that I obviously won't have a connection to download any additional requirements should there be any - so if there are some, could someone please let me know and I can download them beforehand?

Thanks for your help,
Graham

---

### Post by Lexyboy on 2007-03-19
Since noone's replied yet, I'll have a go (I don't use BT so am just guessing).  Assuming you have 'proper'  broadband not ISDN / 'dial-up' broadband, you shouldn't have any problems - ubuntu should recognise your connection and Just Work.  At least, that was my experience with NTL broadband.

Possibly you'll need the software to be fun from windows to configure your hub, but you shouldn't need special software to use it once it's working.

In general I've found that a lot of software packaged with hardware is not necessary - when I ran the NTL CD I was given it totally screwed up windows somehow.  Reinstalled and didn't bother with the CD and no problems (in windows or linux).  Generally they just have some support s/w and install lots of advertising links all over your desktop :mad: 

As I say, I've not had experience with BT so this is all conjecture, but I expect you'll be pleasantly surprised how ubuntu copes...

Let us know how it goes!

---

### Post by ubuntu1 on 2007-03-19
I use BT Internet via the Homehub and it works with no problems using ethernet and wireless. You get into the router using a web browser (I use firefox and Opera). You should be fine.

---

### Post by justleen on 2007-03-19
i have the same with my ISP. I got a router, and a CD for windows..
Now i get the shivers any way from suchs CD's.. Its my router, so I like to be the one configuring it.  In most cases, you can simply check the brand of your router, and search for the manual. Thats way you can set it up any way you want it.

The CD's you get with is, usually just configures windows networking. 
In my experience, like the poster above, you shouldnt have any problems.

Ill bet you can simply plug your router in, boot ubuntu, and go.. 
There is a changes your router needs to be configured for the BT network,. in that case (if you dont wanna do it manually) you can run the CD on windows, which takes care of the router config. If you then boot to Ubuntu, it should work

(keep in mind, i dont have BT either.. let us know how you get on!)

---

### Post by Fitzcarraldo on 2007-03-19
I also have a BT Home Hub and use it with ubuntu without any problem. As already stated, it is possible to access the hub's configuration pages via a Web browser (see BT Home Hub's User Guide), and this works fine. Also, although the BT Home Hub comes with a CD for Windows, you don't need to install anything from it -- I didn't, for example. You can activate for BT Broadband Talk from a BT Web page -- as I did -- so you really don't need anything from the CD.

By the way, there is an excellent third-party article on the BT Home Hub here:

[http://www.frequencycast.co.uk/homehub.html](http://www.frequencycast.co.uk/homehub.html)

Notice that it tells you how to connect a printer or USB HDD to one of the two USB ports on the BT Home Hub. You can then have a network printer (no need to keep a PC on your network switched on just to be able to print) or instead have a network storage device accessible by all the PCs on your network.

I have not yet tried connecting a printer, but my brother has already connected an old Iomega 140 Gb USB HDD (USB 1.1, I think) to his BT Home Hub and is using it as a network storage device for his home network. To give you an idea of the access speeds, he copied a 5 Mb file from his HDD to the USB HDD in 15 seconds, which is not that bad, actually.

So, in summary, the BT Home Hub is no problem for ubuntu.

---

### Post by deuchar1 on 2007-03-20
Thanks for putting my mind at rest guys. I'm getting the hub tomorrow, so I will let you know how the installation goes.

And I more that agree with the policy of avoiding software installs until you know they are needed - I've had so many devices which auto-configured without the software CD and whenever I went ahead and used the CD my system got clogged with adverts and rubbish.

---

### Post by Fitzcarraldo on 2007-03-20
I forgot to mention another interesting aspect of the BT Home Hub: it's a Linux box! Yep, I kid you not -- the firmware inside the BT Home Hub is Linux-based.

---

### Post by lpmasterblow on 2007-03-20
As the previous posters have said, the CD that BT send you is only to configure windows networking. If you set your ubuntu networking settings up to connect to the gateway it should either assign you an IP through DHCP or if you choose to keep it static, it's happy with that.  To use the homehub for network storage you need to ensure your usb hdd is formatted in fat32. The linux box within won't read NTFS formatted drives.

---

### Post by getaboat on 2007-03-20
I'm pretty sure that under the wrappers my Linksys modem and router is a Linux box. I wonder if more are.

Agree with all the posts above, admin on the router is by using the browser (or telnet to it when in debug mode).

---

### Post by deuchar1 on 2007-03-26
Hey guys, just to let you know everything went smoothly.
I just used the install CD in Windows - I seldom use it anyway so I can live with the junk it puts onto the system - and when I restarted in Ubuntu it just worked. Didn't have to change a single setting. Oh, how I love Linux :)

---

