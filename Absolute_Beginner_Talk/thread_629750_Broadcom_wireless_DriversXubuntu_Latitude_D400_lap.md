---
title: "Broadcom wireless Drivers/Xubuntu Latitude D400 laptop"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by evadwolrab on 2007-12-02
This is my post from a thread in the 'Other OS' section. Since this is Xubuntu-related, I thought it relevant to post it here:

> > **styven said:**
> Good evening all,

It seems that your issue is sorted which is great.

However for the benefit of those that may be struggling, I used the following to get wireless working on my HP nx6310 laptop........

styven@styvens-laptop:~$ sudo apt-cache search fwcutter
[sudo] password for styven:
bcm43xx-fwcutter - Utility for extracting Broadcom 43xx firmware
styven@styvens-laptop:~$ 

Mind you in gutsy it prettty much does it for you, see screenshot.

Hope that will help someone.

Steve.
I get 'the software source for the package bcm43xx-fwcutter is not enabled' when I use that restricted package manager to do it automatically. I've enabled everything in the first tab in the repo's section of synaptic.

Any ideas anyone? I've tried searching synaptic for 'bcm' but nothing comes up.

---

### Post by jimbob on 2007-12-02
Use this  post (#1) to get your broadcom wireless working.

[http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318)

---

