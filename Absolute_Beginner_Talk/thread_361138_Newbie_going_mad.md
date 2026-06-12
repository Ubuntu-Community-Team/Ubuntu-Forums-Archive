---
title: "Newbie going mad"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by helamen on 2007-02-14
I am a newbie, and is tearing my hair out, going blind from reading all the forums, and mad at not being able to install ubuntu 6.10.

I have a laptop Toshiba Satellite A80, which can run Mandriva, PClos, DSL, but do you think I can install ubuntu that is suppose to be a begineers dream of having a linux and so popular with all? it took half an hour to get to the desktop and then it freezes. I am only looking at ubuntu, because I cannot get the wireless to work on Mandriva, PClos has NTFS problems, DSL has wireless problems and so on.

It is sheer hell trying out Linux!!!!!

So where to now? or have to go back to Windoze.

Sorry fellows
helamen

---

### Post by aysiu on 2007-02-14
I'd stick with PCLinuxOS.

What exactly do you mean by "has NTFS problems"?

By the way, according to [this page](http://www.linux-on-laptops.com/hosted/toshiba-a80-121-kubuntu.html), Ubuntu seems to work nigh-perfectly on the Toshiba Satellite A80-121. Is A80-121 really different from A80?

---

### Post by ramjet_1953 on 2007-02-14
OK, try these two things first.

1. If you didn't burn the iso image of Ubuntu at a low speed (<4 X is best) the re-burn it and see if that fixes the problem. If not, go to the next step.

2. Dowload the alternate CD. This often fixes any install problems. It is not a graphical installer, but is fairly intuitive, and offers more options.

If you still have problems, come back and there are some other things we can try.

Regards,
Roger 8-)

---

### Post by helamen on 2007-02-14
NTFS problems is that the harddisks are in that format and PClos cannot install to it

I was hoping Ubuntu would be a good choice

thanks

---

### Post by helamen on 2007-02-14
I bought the Ubuntu that came along with the latest issue of Linux Magazine in Australia

helamen

---

### Post by helamen on 2007-02-14
So it says Kubuntu works with the laptop, his laptop has twice the memory and twice the harddisk with a different network card, I haven't tried Kubuntu, I was using edgy

Xubuntu works, I borrowed the disk and had to give it back, but the wireless did not work.

will have to download more to try out

ta
regards
helamen

---

### Post by aysiu on 2007-02-14
> **helamen said:**
> NTFS problems is that the harddisks are in that format and PClos cannot install to it

I was hoping Ubuntu would be a good choice

thanks
*No* Linux distro will install to NTFS any more than Windows will install to Ext3.

To install PCLinuxOS, use DiskDrake to resize the NTFS partition. This will create free space where you can create a new Ext3 partition and install PCLinuxOS to it.

More details on DiskDrake [here](http://ubuntuforums.org/showthread.php?t=114142) > I haven't tried Kubuntu, I was using edgy Kubuntu and Edgy aren't mutually exclusive. Ubuntu comes in different "flavors" (Kubuntu, Ubuntu, Xubuntu, Edubuntu) and also different versions (6.10 Edgy Eft, 6.06 Dapper Drake, 5.10 Breezy Badger, 5.04 Hoary Hedgehog, 4.10 Warty Warthog).

Kubuntu Edgy is version 6.10 (which stands for October 2006) of Ubuntu with a KDE desktop environment (hence, Kubuntu). Even though Kubuntu interface looks different and has different default applications, it is the same distro as Ubuntu and has the same hardware detection and installation.

---

### Post by helamen on 2007-02-14
thanks aysiu

I managed to use diskdrake, and installed pclos onto external harddisk, but didn't know how to do the lilo or grub ... will read somemore!!!!

only winXPHE boots up, no signs of pclos

regards
helamen

---

