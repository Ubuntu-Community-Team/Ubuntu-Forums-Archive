---
title: "ATI DRivers"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-08
Now, in Ubuntu how do you know you have the best possible drivers and are getting the best FPS? I was playing UT2004 on ubuntu tonight and it didn't seem as crisp as in windows. Is that due to it being linux or just that I don't have the best drivers set for the card? I had the settings at max and still the same picture. Any ideas? Thanks!

---

### Post by jiminycricket on 2007-05-08
What kind of ATI card do you have?  There are open source drivers that support AIGLX for  Beryl, but may have worse 3d support, yet ATI's cards don't support AIGLX and may have faster 3d but don't support older cards.  Also they are quite bugger than the open source ones.

Type lspci | grep VGA into a terminal and post back

---

### Post by Tumpster on 2007-05-08
main@main:~$ lspci | grep VGA
0000:05:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
main@main:~$

---

### Post by jiminycricket on 2007-05-08
Do lsmod | grep fglrx to see if you're already running the ATI closed drivers. 

[http://www2.ati.com/drivers/linux/linux_8.36.5.html](http://www2.ati.com/drivers/linux/linux_8.36.5.html) says your card is supported.  What happens when you go into the restricted device manager (System->Administration->Restricted Device Manager), read the X**** sticky at the top of this forum for how to install fglrx.

Just know that they are buggier than r300 drivers and will cause crashes, freezes, other problems that the open source drivers will not, and they can't be fixed by  developers because they are closed source and ATI don't have much incentive to improve, unfortunately.

---

### Post by Tumpster on 2007-05-08
I did that and got this:
main@main:~$ lsmod | grep fglrx
fglrx                 388908  8
agpgart                34888  1 fglrx

---

### Post by jiminycricket on 2007-05-08
So you've installed fglrx already.  There are probably some performance tweaks in ATI's GUI control panel and maybe xorg.conf (google), but I'm not familiar enough with their driver.

Otherwise, complain to ATI via the link in my sig.

---

### Post by Tumpster on 2007-05-08
should I have FGLRX or should I have the open source? WHat do you think would give me the best picture and gaming ability?

---

### Post by jiminycricket on 2007-05-08
You can try the r300 drivers by change the driver from fglrx to radeon in /etc/X11/xorg.conf and erase any other fglrx-specific lines under Video.

If it doesn't work just type in fglrx again.

---

