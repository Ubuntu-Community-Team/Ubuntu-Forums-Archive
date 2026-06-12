---
title: "touchpad and fan issue"
date: 2012-01-12
forum: Any Other OS
---

### Post by hollowhead on 2012-01-12
For various reasons well rehearsed on these forums I thought I'd give mint a go.  No problems installing and most stuff works on my toshiba l350 laptop but I have a couple of serious problems.  One the fan won't switch off and two the touchpad doesn't work.  Both worked in ubuntu proper although I did have an issue getting the fan to work properly initially.  The problem is I cannot remember what I did to do this.  

I've tried this


[http://fossplanet.com/f10/%5Bbug-321578%5D-re-toshiba-satellite-l350-l505-fan-regulation-problemin-ubuntu-8-10-ubuntu-9-10-a-163559/](http://fossplanet.com/f10/%5Bbug-321578%5D-re-toshiba-satellite-l350-l505-fan-regulation-problemin-ubuntu-8-10-ubuntu-9-10-a-163559/)

and some of this 

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578)

I installed acpi and the touchpad worked but the fan wasn't switching on so I tried reinstalling which is where I am now....

Please can someone help.

Can get fan to work if I hibernate first otheriwse its random on and off.  Toucpad started working...

Managed to work out how to add GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

to /etc/default/grub

this and instlaling the coretemp module worked although I have lost the use of fn-f6/7 keys but I'm not worried about that.....

---

