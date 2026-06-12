---
title: "Installation hangs on boot up Power Mac G4"
date: 2012-05-19
forum: Apple Hardware Users
---

### Post by tdlam on 2012-05-19
I just installed Ubuntu 12.04 on a PowerMac G4. I chose the Xubuntu desktop environment during installation.  But now that installation is finished, the distro is  halting at boot-up as soon as the "UBUNTU 12.04 with the scrolling dots underneath it" appear on the screen.

I was wondering if anyone had a fix or any ideas. I apologize ahead of time if this has been posted anywhere else. I had trouble searching for the topic.

Thanks in advance. 

I believe that my graphics card is an ATI rage 128 if that makes any difference.

---

### Post by 2F4U on 2012-05-20
I don't have a G4, so probably can't be of much help, but I found this piece of information about your graphics card:

[https://wiki.ubuntu.com/PowerPCFAQ#ATI_Rage_128_cards](https://wiki.ubuntu.com/PowerPCFAQ#ATI_Rage_128_cards)

---

### Post by bazzlevi on 2012-08-20
> **tdlam said:**
> I just installed Ubuntu 12.04 on a PowerMac G4. I chose the Xubuntu desktop environment during installation.  But now that installation is finished, the distro is  halting at boot-up as soon as the "UBUNTU 12.04 with the scrolling dots underneath it" appear on the screen.

I'm having the exact same problem. My video card is the Nvidia Geforce 2. I've tried several different options from the alternate CD, including CLI, and all result in a system that boots to the black screen as you describe, but it never progresses beyond that point. Some error or progress messages would be nice...

---

### Post by abtabt on 2012-08-25
[COLOR="Red"]bazzlevi wrote

I'm having the exact same problem. My video card is the Nvidia Geforce 2. I've tried several different options from the alternate CD, including CLI, and all result in a system that boots to the black screen as you describe, but it never progresses beyond that point. Some error or progress messages would be nice... [/COLOR]

can you tell me witch mac it is ? (maybe i can point you in right way)

look on web site everymac


[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

---

### Post by clickgear on 2013-04-11
I'm having what appears to be the same issue: I used the mini-iso CD to try and install the base system (without even any desktop yet), and it hangs at the point where Ubuntu 12.04 appears on the screen with the dots underneath.  The dots are all white, and never change color as I have seen them do on a successful installation boot.  My computer is a PowerMac G4 Quicksilver 867 MHz with an Nvidia GeForce 2 MX card (according to everymac.com).

---

### Post by clickgear on 2013-04-11
> **clickgear said:**
> I'm having what appears to be the same issue: I used the mini-iso CD to try and install the base system (without even any desktop yet), and it hangs at the point where Ubuntu 12.04 appears on the screen with the dots underneath.  The dots are all white, and never change color as I have seen them do on a successful installation boot.  My computer is a PowerMac G4 Quicksilver 867 MHz with an Nvidia GeForce 2 MX card (according to everymac.com).

OK, I got past my issue with help from this thread:

[http://ubuntuforums.org/showthread.php?t=2131644](http://ubuntuforums.org/showthread.php?t=2131644)

The key was to include the 'nomodeset' parameter in yaboot configuration file.  I'm not booting into a desktop yet, so the xorg.conf wasn't strictly necessary for me.  This may help the rest of you!

Kurt

---

