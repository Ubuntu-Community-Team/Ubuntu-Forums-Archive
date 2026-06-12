---
title: "More modem woes"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by lee292 on 2007-03-22
Rather than do a recompile of the kernel and the other stuff required to get a Winmodem to work under Linux, I purchased a Zonet PCMCIA modem, model ZFM5600.  It's a full-hardware modem which should work under Linux.  It works fine under Window$.  I followed the setup documention on the Ubuntu website, but I don't hear it dialing and Firefox gives a "server not found" messsage.   

Like a recent poster, I live in an area where there's no cable, too far away from a switch point to get DSL, and satellite broadband is too expensive for me.  Dial-up sucks, I know, but it's all I can get. 

What do I need to do to get it to dial my ISP?  Thanks in advance for your help!

---

### Post by sharong on 2007-04-16
Hi, I was really confused by modems at first, but it's not that hard once you know how it works.
So, you've got your modem set up (I assume the computer is recognising it and can find it etc? - if not, then you need to do that first.  I don't know a lot about hardware modems, as I did the winmodem thing and it worked, but maybe someone else can help with that.)

You need to use wvdial or something similar to actually dial up.  You probably have wvdial on your system already (type 'whereis wvdial' and check that it is listed).

Type 'wvdialconf' or 'sudo wvdialconf' and then 'wvdial' or 'sudo wvdial' (only put the sudo in if you need to) to set the program up.  It does it automatically, you don't have to do anything, just let it run.

There's a file called 'wvdial.conf' in /etc which specifies the configuration for wvdial.  It gets set up when you run wvdialconf.  It stores information like your ISP name, DNS servers, your username and password etc, so check that those are correct.  Once you have set it up, you shouldn't need to change it.

Once that's set up, type 'wvdial' or 'sudo wvdial' to dial out.  Some messages get displayed on screen to tell you what it's doing.  It should connect to your ISP.  You need to do wvdial each time you want to get online.

Other dial-up related things are chat and pppd, but wvdial uses those and calls them for you - technically, you can call them yourself if you don't have wvdial, but it's more complicated.  You'll see references to them in the man pages for wvdial though.

Hope this works!

---

### Post by sharong on 2007-04-16
This is a really helpful site:

[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

Check it out.

---

### Post by lee292 on 2007-04-17
Thank you.  I went to the link a few days ago, re-read it, and have felt like a total idiot ever since! :oops:  Aha! you have to install Gnome PPP and do a bit of configuring for the modem to work!  Since I did that both the PCMCIA card modem and the old Sportster work like a charm.  Thanks to all for having posted their suggestions!

---

