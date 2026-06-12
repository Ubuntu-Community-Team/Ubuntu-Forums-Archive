---
title: "MacBookPro 3,1 WPA problem"
date: 2009-04-02
forum: Apple Hardware Users
---

### Post by lambengolmor on 2009-04-02
Hi everybody, I've a MacBookPro 3.1. Also if the tutorials sais that the wireless works in ubuntu 8.10 I can't manage to connect to a wireless WPA network (to avoid stupid question, YES, I have the password and it works fine with macosx and windows). I use wicd instead of networkmanager but using networkmanager doesn't change things (I've tried).
Sorry if the question was already asked, thanks in advance for the help

PS: I'm asking this because I think I'm going to reinstall after 9.04 is out, so i want to make sure everything will work or I have to go look for some other distro since I'm not the network administrator so I can't just stop using wpa and all of you know how painful is to use linux without internet connection...

---

### Post by cyberdork33 on 2009-04-02
> **lambengolmor said:**
> Hi everybody, I've a MacBookPro 3.1. Also if the tutorials sais that the wireless works in ubuntu 8.10 I can't manage to connect to a wireless WPA network (to avoid stupid question, YES, I have the password and it works fine with macosx and windows). I use wicd instead of networkmanager but using networkmanager doesn't change things (I've tried).
Sorry if the question was already asked, thanks in advance for the help

PS: I'm asking this because I think I'm going to reinstall after 9.04 is out, so i want to make sure everything will work or I have to go look for some other distro since I'm not the network administrator so I can't just stop using wpa and all of you know how painful is to use linux without internet connection...
what driver are you using? What does it do when you try to connect?

9.04 may work very differently than 8.10. You should download the beta livecd and try it out on your computer.

---

### Post by lambengolmor on 2009-04-02
Sincerly I'm not sure, could it be madwifi or wesd? Where can I check wich one is in use?
When I try to connect it does nothing: I put the password in, it tries to connect for a little bit then it just sais "disconnected" (and of course it really IS disconnected).
For what regards the 9.04... If it's THAT different isn't it just futile to try it since it would be so unstable that it wouldn't be an attendible test... Am I wrong?
Thanks for any info,

---

### Post by cyberdork33 on 2009-04-02
> **lambengolmor said:**
> Sincerly I'm not sure, could it be madwifi or wesd? Where can I check wich one is in use?
When I try to connect it does nothing: I put the password in, it tries to connect for a little bit then it just sais "disconnected" (and of course it really IS disconnected).

in a terminal, try lsmod. that will list modules loaded. it is probably "wl"

> **lambengolmor said:**
> For what regards the 9.04... If it's THAT different isn't it just futile to try it since it would be so unstable that it wouldn't be an attendible test... Am I wrong?
Thanks for any info,
Actually, it is quite stable :) I am using it on my Mac at home already.

---

### Post by lambengolmor on 2009-04-03
there's no wl module... But I found ath9k... Should I change? How's done?

---

### Post by cyberdork33 on 2009-04-03
> **lambengolmor said:**
> there's no wl module... But I found ath9k... Should I change? How's done?
oh sorry, yoou have an atheros card in the 3,1... Newer ones have Broadcom.

ath9k is probably the best there is, there are still some issues.

It may be good to file a bug:
[https://bugs.edge.launchpad.net/ubuntu](https://bugs.edge.launchpad.net/ubuntu)

Then you have some things you can try as a workaround.
First, wicd in place of network-manager might help
Lastly, you can try to get a version of madwifi driver working (old driver that ath9k replaced).

Sorry, there is not a definitely solution for this.

---

### Post by lambengolmor on 2009-04-03
Er... I'm yet using wicd and this doesn't solve the problem at all... What should I do to install the old madwifi driver? Just search in aptitude? *goes searching in the aptitude*

---

### Post by cyberdork33 on 2009-04-03
> **lambengolmor said:**
> Er... I'm yet using wicd and this doesn't solve the problem at all... What should I do to install the old madwifi driver? Just search in aptitude? *goes searching in the aptitude*
no, it has been completely replaced with ath9k (in the Linux kernel). You will have to compile it. I think there are some instructions in an old wiki page... 

Here ya go:
[https://help.ubuntu.com/community/MacBook2-1/Hardy#Madwifi](https://help.ubuntu.com/community/MacBook2-1/Hardy#Madwifi)

There is also the ndiswrapper option (I forgot about that one!). Instructions for that are on the same page.

---

