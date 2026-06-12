---
title: "Internet Wireless connection problem"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by learn on 2008-01-20
Hi all,
I'm totally new to linux. Recently, I had just installed Ubuntu 7.10-desktop-i386 into my laptop. But I can't access Internet, even the wireless network connection shows 76%. Besides that, I also have the problem with the upgraded my software packages. The urgrading progress keep stucking in the middle. After failed to upgrade my packages, I checked for the shown error message,those updates are time out. Does any know about this? Thanks, I appreciate any help.

---

### Post by mikeyphi on 2008-01-20
> **learn said:**
> Hi all,
I'm totally new to linux. Recently, I had just installed Ubuntu 7.10-desktop-i386 into my laptop. But I can't access Internet, even the wireless network connection shows 76%. Besides that, I also have the problem with the upgraded my software packages. The urgrading progress keep stucking in the middle. After failed to upgrade my packages, I checked for the shown error message,those updates are time out. Does any know about this? Thanks, I appreciate any help.

76% on your wireless should be OK!!
Can you access Internet through Firefox?
For the package update - open System/Administration/Software Sources and check that the 4 repos are enabled.
Also on package update - it could be that the repos you tried were down at the time - do the above checks and try again.

---

### Post by rosegarden78 on 2008-01-20
Wireless woes were mine as well.  I had a Dell card.  In the days of Edgy Eft I had to find the bcm43xx package, install it and load it with modprobe.  I still need the package but the wireless works fine.  Sometimes if I wiggle my wifi card - mine is cracked with tape reinforcement - it will work a moment later.

I think it has to do with network conditions.  I used to unplug and plug my router because of poor DSL connection that stopped responding, often 3-5 times a day.  Now the connection is stable and I don't need to reboot the router.

You can also click the signal and click your access point to reconnect.  This makes your computer handshake the router and usually get a fresh connection.  In Xubuntu you need to add the nm-applet from Synaptic to get the network manager in the task bar.

I think you're card is working, but when it comes time to upgrade consider a Linux-approved  wifi card to minimize future headaches.  Just make sure you upgrade to the latest distro like Ubuntu Gutsy because it should work automatically now.  Install Ubuntu first then add KDM or XFCE for best results.

---

### Post by learn on 2008-01-20
Thanks all,

mikeyphi, I can't access Internet through Firefox. For the ways that you guided me, I had been tried out but it did not work for my ubuntu and it kept on stuck. I also dunno why it acts like that..haha

rosegarden78, my ubuntu comes with KDM and XFCE installed...even though the wireless network connection shows connected but it still can't access the internet through browser.

Thanks again. But what's the problem lies on?

---

### Post by learn on 2008-01-21
anyone?

---

### Post by rosegarden78 on 2008-01-22
Trying to keep track of post is proving difficult for me.  There must be an easier way.

When this happens I just unplug the router to the modem/router and plug then in again.  Other than that is  could be an address conflict?  You know like when your router and modem have the same address of 192.168.1.1?

So you go into router config and change your router to 192.168.3.1

---

