---
title: "Ubuntu booting to a blank screen"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by bluezapper on 2007-07-08
Hi,

After reinstalling ubuntu I ran into a lot of problems. When I start Ubuntu after shutting down it boots up to a blank(black) screen but I can hear the drums sound and even when I type username and password it logs me in but I can only see blank screen. The only way to logoff is to press my power off button and nothing works.

But when I boot in recovery mode everything goes well. I am using IBM Thinkpad T22 with 256 MB RAM and I have Savage drivers. 

Can someone please help me in solving this problem. 

regards,

bluezapper.

---

### Post by BL00dFox on 2007-07-08
MY guess is that your video drivers arent installed properly. Try going into recovery mode and typing ```
sudo dpkg-reconfigure xserver-xorg
``` and follow the process through. Please post back your results.

Good Luck

---

### Post by bluezapper on 2007-07-08
Hi BLOOdFox,

I did as you said and I got the following warning:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070708085835


Now what should I do ??


thanks

bluezapper

---

### Post by BL00dFox on 2007-07-08
Have you tried rebooting?

---

### Post by Malta paul on 2007-07-08
Will your system boot OK using the live disk?

---

### Post by bluezapper on 2007-07-08
I tried rebooting, now I can screen the login screen. But, I saw that I dont face this probelem on immediate reboots. I see it when I shut down my computer in the night and try to reboot it in the morning.

However, now , I will check if it occurs again and get back to you people. Thanks for the help you have provided.

@Malta Paul: It boots perfectly with the live disk.



thanks

@bluezapper.

---

### Post by BL00dFox on 2007-07-08
> **bluezapper said:**
> But, I saw that I dont face this probelem on immediate reboots. I see it when I shut down my computer in the night and try to reboot it in the morning.

Now thats really interesting. It probably has something to do with your hardware...

---

### Post by bluezapper on 2007-07-08
I shutdown and left it for a few minutes. Now, I rebooted it  and it does not show me the boot login screen again.

I forcefully shut it down and rebooted back in recovery mode. If the probelm is with my hardware then why does it boot perfectly in recovery mode.

Any help on this one ??

---

### Post by BL00dFox on 2007-07-08
> **bluezapper said:**
> I shutdown and left it for a few minutes. Now, I rebooted it  and it does not show me the boot login screen again.

I forcefully shut it down and rebooted back in recovery mode. If the probelm is with my hardware then why does it boot perfectly in recovery mode.

Any help on this one ??

Maybe because your graphic card drivers have problems loading from a "cold start"... Just a thought -> I suggest you seek some second opinions...

---

### Post by Malta paul on 2007-07-08
Another just a thought, boot up in recovery mode then type EXIT and see if it boots to your normal log in screen ;)

---

### Post by bluezapper on 2007-07-08
@Malta It works that way but not on cold start.

---

### Post by bluezapper on 2007-07-08
finally got it working by adding the option to the Xorg.conf file:


         Option "BusType" "PCI"
         Option "DmaMode" "None"

This seems to be a bug associated with IBM T20, T21, T22 already reported to Ubuntu under Bug #33617. However, in case someone encounters this problem, please refer to the following link for resolutions:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/33617](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/33617)

BR
bluazapper

---

### Post by bwhaley on 2007-07-14
FYI, I had this exact problem on an IBM T22. I added:

```
Option "BusType" "PCI"
```

to the Device section of /etc/X11/xorg.conf and the problem went away.

Thanks for the tips.

- Ben

---

