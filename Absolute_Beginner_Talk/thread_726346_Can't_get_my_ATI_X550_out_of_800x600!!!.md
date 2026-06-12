---
title: "Can't get my ATI X550 out of 800x600!!!"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2008-03-16
Please excuse me while I vent in between paragraphs, because after plenty of experience with both nVidia and ATI cards, I have to say that I will NEVER EVER put an ATI card in my computer (unless they make the drivers open source and we take care of all these stupid problems with that).  Otherwise, ATI's are a waste of my time.

So here's what I tried:

Restricted driver manager -

Installed the driver with no errors.  Upon reboot, was given an error...something like, "couldn't detect your monitor.  Do you want to reconfigure xorg?"...something like that.  I'd say no, and  the system would boot up, and still be in 800x600, with no other resolutions available in the Screen and Graphics config.  I tried changing the monitor in here to just a plain old monitor with "1024x768" in the name of the monitor.  Tried to change resolutions, still didn't work.

Legacy VESA drivers -

I did a dpkg-reconfigure on the xorg thing, going through that long question and answer series, selecting the VESA driver instead of the ATI from the list.  That caused all kinds of garbage to show up on the screen the next time around, I did something slightly different (perhaps kernel buffering option being picked, who f-ing knows)...  Anyway, still no ability to switch resolutions.

Envy -

I just finished trying envy, which appeared to install the driver with no errors.  And upon reboot, when trying to change resolutions, clicking the test button does NOTHING.  The computer is just got some kinda mad craving for 800x600, and it's really really pissing me off.

I was about to ask for help to figure this problem out, but I think  it would be almost easier to just put this stupid card on ebay and replace it with one made by nVidia.  If you have an ATI and know what I'm doing wrong, I'm all ears.

---

### Post by handydan918 on 2008-03-16
Can't recall for sure, but it may be necessary to do a dpkg-reconfigure xserver-xog after installing the ATI driver. Seems like my brother had this issue with his x550.

---

### Post by diablo75 on 2008-03-17
> **handydan918 said:**
> Can't recall for sure, but it may be necessary to do a dpkg-reconfigure xserver-xog after installing the ATI driver. Seems like my brother had this issue with his x550.

I forgot to mention I did that too.....  Yeah.  I'm hawking this stupid hardware.  Sorry ATI.  Try me again next year.

---

### Post by handydan918 on 2008-03-18
You can down load a driver from ati [here.]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")
Read the instructions, and I think you may get through it. Video drivers are often best installed while X is NOT running, so this'll be your big chance to brush up on you console basics. Post back if you get stuck.
I bet doing this from single user mode would save some typing of 
s

u

d

o

over and over...

---

