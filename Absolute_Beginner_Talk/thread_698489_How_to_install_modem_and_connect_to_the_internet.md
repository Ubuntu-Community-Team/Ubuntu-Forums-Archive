---
title: "How to install modem and connect to the internet"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Louis de Broglie on 2008-02-16
Hi,

I have a Prolink 1456PVA V.92 PCI SOFT modem. Can anybody tell me where can I get ubuntu 7.04 driver for my modem. And how do I install this driver? How to connect to the internet after installing modem driver? By the way, can anybody tell me the command to install gcc in ubuntu.:)

My driver software cd contains drivers for fedora 3 & 4, redhat 8 & 9, mandrake 10, suse linux, Windiows vista 32 & 64, xp 32 & 64, 98se, me, 2000. I have searched the modem manufacturer website. There are no driver for ubuntu 7.04 there.

Thanks.

---

### Post by oilchangeguy on 2008-02-16
> **Louis de Broglie said:**
> Hi,

I have a Prolink 1456PVA V.92 PCI SOFT modem. Can anybody tell me where can I get ubuntu 7.04 driver for my modem. And how do I install this driver? How to connect to the internet after installing modem driver? By the way, can anybody tell me the command to install gcc in ubuntu.:)

Thanks.

if it's available in your area, i suggest upgrading to a highspeed connection. or check ebay for a serial port external modem.

---

### Post by mikeyphi on 2008-02-16
Can't help with the Soft Modem
However, gcc is available in the repos - open Synaptic, search for gcc

---

### Post by Louis de Broglie on 2008-02-16
It is not available in my area and it is not possible for me to buy something from ebay.:(

So does that mean there are no ubuntu driver for my modem?:confused:

---

### Post by mikeyphi on 2008-02-16
You edited your post to say you have drivers for Redhat etc. It is possible to convert Redhat to Ubuntu (no guarantee it will work!) Use the package 'alien' also available via Synaptic

---

### Post by Louis de Broglie on 2008-02-16
Can you please tell me a step by step procedure about installing redhat driver? If I know the whole process, then it will be easy. Otherwise, I boot ubuntu, I fail, then, I connect again in vista, load this webpage again etc. My internet is slow. So..:)

---

### Post by zerhacke on 2008-02-16
Even after you get the driver installed, you're still going to need another package to dial up to the net unless you're well versed in CLI.

That package is called gnome-ppp.

Good luck getting the redhat package to work.  man alien will give you more info.

---

### Post by Louis de Broglie on 2008-02-16
Thanks all for support. Ubuntu forum is really helpful. I am now going to try that.:)

---

### Post by mike555 on 2008-02-16
If you have serial port you could get an external modem , I have had good luck with Zoom brand for dialup ...........

---

### Post by oilchangeguy on 2008-02-16
> **mike555 said:**
> If you have serial port you could get an external modem , I have had good luck with Zoom brand for dialup ...........

mikey, you might want to read the entire thread prior to posting. see post #2.

---

### Post by Ivorydawn on 2008-02-16
Hi,

Have a read of this post, it may help.

Regards

Andrew

---

### Post by Ivorydawn on 2008-02-16
HI,

Actually try reading this one [http://ubuntuforums.org/showthread.php?t=308098](http://ubuntuforums.org/showthread.php?t=308098)

Bit quick on the enter button last time, sorry bout that.

Regards

Andrew

---

### Post by kevmore on 2008-02-16
you might want to start here.

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)


I got one working a few weeks ago, but forgot how.  Now I am setting up another computer with a us robotics modem.

---

### Post by Louis de Broglie on 2008-02-17
Can you tell me how to find my posts? It took me ages to find this post again. Anyway, I failed to install those packages you mentioned. But I know how to install packages now. Where can I find those packages? I tried synaptic package manager but can't find it. Even if I install my modem, how do I dial to connect to the internet?:(

---

### Post by Louis de Broglie on 2008-02-17
Sorry, I did not see that this thread has second page too. So I am going to read those links you mentioned. Thanks.:)

---

### Post by mike555 on 2008-02-17
I thought he was looking for a working dialup modem , (if he can't get his drivers working ) that is why I said I had good luck with Zoom modems , like they sell locally (at least where I live)

---

### Post by jan quark on 2008-02-17
to find your posts you can subscribe to your thread
using the thread tools I guess at the top of the page

or going directly to the bottom of the page and clicking on subscribe to thread in the left corner

then you can go the the user cp control panel 

and view your subscribed threads from there

---

### Post by kevmore on 2008-02-17
you can also click on the search drop down menu and at the bottom is "find your posts" and "find your threads".

---

### Post by kevmore on 2008-02-17
If you do have to get a new modem, spend the extra few bucks and get a US Robotics hardware modem.  
It is supported by linux and works as soon as you hook it up, with no drivers to install at all.  The only program you need is the dial up program, gnome ppp.  I searched for it on "Add Remove Programs" and found it there.  Good Luck.

---

### Post by Louis de Broglie on 2008-02-18
Hmm. I had better success this time. I managed to install lots of packages and I know how to configure internet connection to dial. But I found out in the network button on the top right corner of the desktop that no modem is installed. So I just have to install my modem. I inserted my modem cd. Then opened synaptic package manager. Then selected load packages from cd like I did to install other packages from cd. But no package is selected. That means my modem is not supported in ubuntu. Right?:confused:

Those modems you mentioned are not available in my area.:( But thank you for your enthusiastic support. This community is so good.:)

---

### Post by Louis de Broglie on 2008-02-18
Alright. I tried to install redhat, fedora, mandrake ,suse drivers in ubuntu but non installed properly. Then I contacted modem manufacturers and they said they have no driver for ubuntu at present. I think the only solution is to be patient and see if any future version of ubuntu solves my problem.:popcorn:

---

### Post by spiderbatdad on 2008-02-19
```
sudo apt-get install build-essential
``` will install gcc for you, and other libs vital to compiling.
Getting a softmodem to work can be tricky. Try kppp from synaptic as it has fewer problems in Gutsy than gnome-ppp. If you are having trouble finding packages, it is probably due to the fact that your sources are commented out...the result of installing 7.10 without a working internet connection.
You may have to result to downloading gnome-pppfixedforgutsy.deb or kppp from sourceforge (or wherever) and putting them on a flashdrive to upload to your ubuntu desktop.

wvdial is should already be installed for you, and ppp-config. check out this guide to try to configure your modem from cli. [http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by spiderbatdad on 2008-02-19
run ```
sudo wvdialconf
```to see if your modem is detected.

---

### Post by Louis de Broglie on 2008-02-20
Yes. I have managed to install many packages including gcc, g++. I tried wvdial:

sudo wvdialconf /etc/wvdial.conf

But it says no modem is detected.:(

---

### Post by spiderbatdad on 2008-02-20
This site might be the best for getting a soft-modem connected:[http://www.linmodems.org/](http://www.linmodems.org/)

The scanModem tool is a good first step. It will produce a folder full of valuable information on configuring your modem. Unfortunately, soft-modems can be very time consuming, initially.[http://132.68.73.235/linmodems/index.html#scanModem](http://132.68.73.235/linmodems/index.html#scanModem)

---

### Post by Louis de Broglie on 2008-02-20
I already run scan modem. But i do not really get it's output. Should I email it to you?:)

---

