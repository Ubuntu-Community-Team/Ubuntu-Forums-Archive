---
title: "Enabling Belkin USB Wireless G Adapter F5D7050A"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by rjjohnson4 on 2007-04-20
My only access to the internet is through my wireless adapter and it isn't recognized in Feisty.  I can't get access at ndiswrapper or anything because I need internet connection to download them.  It's kind of a catch 22.  I've done a lot of research, but nothing seems to work.  Can someone please give me a dumbed down step by step instruction list of what to do to get it working?!?!?

RJ

---

### Post by rjjohnson4 on 2007-04-21
Here's what I tried

1) [http://gentoo-wiki.com/Belkin_F5D7050](http://gentoo-wiki.com/Belkin_F5D7050)

I can't get access to ndiswrapper because it won't install and i get errors saying ndiswrapper can't be found.

2) [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

I don't thoroughly understand this and some of the commands won't work.

Please advise of an easier way or dumbed-down instructions.


I'm close to going back to windows...someone prevent that please!!!!!

---

### Post by billdotson on 2007-04-21
do not let me discourage you in ANY WAY WHATSOEVER.. but from what I hear USB wireless adapters for Linux is hard to work with.  If you could get setup w/ a normal PCI network card you'd be in business real quick

---

### Post by rjjohnson4 on 2007-04-21
problem is that's what i got and i don't have any other options right now.  i can't get connected to the wireless router unless i get ahold of 125 feet of ethernet cable!  I'm moving in a month and then I'll have the router connected to my comp, so maybe i'll try out ubuntu then.  It's just disappointing because I really want to make the move to Feisty from windows FOR GOOD.  Windows has its perks, but I'm ready to explore linux.  You're not discouraging me, but I really want a workaround for this month!

---

### Post by RKCole on 2007-04-21
rjjohnson4.

Don't give up on this one. :)  I bought a Cnet CWD-854 Wireless-G USB Dongle a few months ago, and I was about to just give up on getting ti to work with Ubuntu.  I did a LOT of research and a LOT of posting, believe me.  I'm not sure what chipset your USB dongle uses, but I'm assuming it is made by RaLink Technology, as they manufacture the chipset for my dongle.

If you run:
```

lsusb

```
in a terminal while your dongle is plugged in, you should at least be able to get some information about it.

If you have not already done so, you may want to check out the forums [here]("http://rt2x00.serialmonkey.com/").  I'm not sure if it will be of help or not, but i wrote a guide in OpenOffice Writer this morning about getting RaLink devices up and running.  I'll attach it to this post for you.  There is a graphical utility I use (called RutilT) which seems to interface very well with my wireless dongle.  I now have wireless up and running with WPA2 and AES encryption.  [Here]("http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/rutilt_0.14-0~3v1ubuntu1_i386.deb") is a link to a .deb package for this utility.  I tried to set things up via NetworkManager and other programs, but to no avail.  I was able to get everything running pretty well thanks to RutilT.

I hope that this helps, and if I can be of any help at all, please let me know.

Take care.

---

### Post by sgardne on 2007-04-21
So did this work? I have the same dongle and I'd like to give it a try.

---

### Post by RKCole on 2007-04-21
It was just reported to me that the document I submitted here (and on another forum) does not open properly.  I'm not sure exactly what happened, but now the original does not open either.  I'm not sure if I can remove the attachment, or if a moderator would have to, but I am going to have to re-write everything...so I will hlpefully have this resolved soon.

I apologize for any inconvenience.

Take care.

---

### Post by rjjohnson4 on 2007-04-21
no prob.

I tried typing lsusb in the terminal and i don't get any info on my adapter.

i ran lshw to get more info and it has a lot of nothing for my usb adapter.

It recognizes my Dell printer and Seagate External hard drive, but the Belkin adapter has a bunch of nothing.

---

### Post by rjjohnson4 on 2007-04-21
ok...I still haven't gotten it working, but I found a new website that looks really easy compared to the other sites.  I'll give this a try and give my feedback.  I know others are tracking this thread because of similar problems.

[http://www.wlanfr.net/contenus.php?id=182](http://www.wlanfr.net/contenus.php?id=182) 

One thing is the links they have for the drivers is broken...use this one instead.

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

---

### Post by sgardne on 2007-04-21
Okay just plugging this device in without doing anything else causes serious system slowdown and in most cases it's so bad i have to restart  by holding down the power button because I just can't do anything. Ctrl+alt+backspace doesn't even work. I'm very wary of this device now, and I'm considering just going out and getting one of the ones that's listed as working out of the box, but I'd rather not. Please let me know how your tests go.

---

### Post by RKCole on 2007-04-21
Okay...It took quite a few hours, but I just re-wrote my guide.  I'll attach it here in case ti can be of any help.  Apparently the file corruption was caused by none other than my ignorance in using command-line archiving utilities.  This file opens just fien now, but if there si any problem (I'm keeping my fingers crossed that there will not be) please let me know.

sgardne:  I had this problem with my device as well.  I'm not sure if it s the same problem, but for mine Ubuntu would load three different driver modules at the same time.  I couldnt' even boot my system with the device connected.  I had to blacklist the drivers (which were to fully functional to begin with), and that solved my problem.

Nevermind the guide...It's too big in size to attach here.  If anyone wants it, please e-mail me and I will send it back in a reply message.

Take care.

---

### Post by rjjohnson4 on 2007-04-21
so i've been screwing around with it for a long time.  i'd type in lsusb and nothing for Belkin came up.

I finally decided to reinstall Fesity.  I was on the live cd and I realized that by looking at lsusb, the Belkin compnent was listed.  I reinstalled and now it at least recognizes the device.  I'm going to retry getting it to work, but it's looking up.

---

### Post by rjjohnson4 on 2007-04-25
A big thank you to RKCole.  The guide compile by him worked like a charm.  Thanks again!

---

### Post by RKCole on 2007-04-25
No problem, rjjohnson4.  I'm just glad it helped.

Take care.

---

### Post by CoolRat33 on 2007-06-10
Hello

I'm trying to connect my ASUS WL 167g USB adapter for wireless internet.  Its been very uncooperative and I just can't get it, or any other card to work.  I have little experience with Linux, but I'm intent on getting rid of Windows and all MS products.

RK Cole, you wrote " Nevermind the guide...It's too big in size to attach here. If anyone wants it, please e-mail me and I will send it back in a reply message."

Could you please send me the guide?  Please send to rayambrosi (AT) gmail.com  (replace AT with @ and remove spaces).

Thank you very much!!

---

### Post by MeX31 on 2007-09-10
I'm having the exact same slowdown problem. This is serious biz

---

### Post by enveeess on 2007-10-07
> **RKCole said:**
> Okay...It took quite a few hours, but I just re-wrote my guide.  I'll attach it here in case ti can be of any help.  Apparently the file corruption was caused by none other than my ignorance in using command-line archiving utilities.  This file opens just fien now, but if there si any problem (I'm keeping my fingers crossed that there will not be) please let me know.

sgardne:  I had this problem with my device as well.  I'm not sure if it s the same problem, but for mine Ubuntu would load three different driver modules at the same time.  I couldnt' even boot my system with the device connected.  I had to blacklist the drivers (which were to fully functional to begin with), and that solved my problem.

Nevermind the guide...It's too big in size to attach here.  If anyone wants it, please e-mail me and I will send it back in a reply message.

Take care.

Hi,

I'm also having serious problems getting the Belkin device to work...would really appreciate a copy of the guide please.

Regards

---

