---
title: "Live CD not booting"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by flyingpengwin on 2007-11-08
Hello :mrgreen: 
I have a HP Pavilion Notebook dv6000 model.
It has a AMD Turion^64^x2 processor, 1Gb of ram, Nvidia graphics card, Windows Vista, and right now it has a defective internal wifi card.
Today I downloaded the 7.1 Gutsy Gibbon, 32 bit, desktop edition, i386 and burned the iso as an image to a CD. When I restart the computer with the Live CD in, it brings up the UBUNTU like normal. I choose run or install and let the CD do its thing. At the point where the UBUNTU words come up and a the bar starts to oscillate back in forth. After this instead of keeping the UBUNTU letters on page and loading. It goes to the DOS page and tries to load the CD from there but after a while the page goes blanks and the CD Drive fails. I tested the CD on my desktop computer and i works perfectly. Please help!
(I tried to include as much information possible to help the amount of questions.)

P.S. I removed the faulty wifi card and tried it like that and still no luck (its back in again)

---

### Post by Dr Small on 2007-11-08
A faulty cd rom perhaps ?

---

### Post by flyingpengwin on 2007-11-08
> **Dr Small said:**
> A faulty cd rom perhaps ?
I don't think so. It worked perfectly on my eMachine desktop (I did not have a say in the purchase of this computer :XD ) so I dont know what it could be. I also ran the CD check and nothing came up.
Thanks though :mrgreen:

---

### Post by flyingpengwin on 2007-11-08
bump

---

### Post by flyingpengwin on 2007-11-08
does anyone have any ideas???

---

### Post by Sef on 2007-11-08
Could you post your computer specs?  It could be a problem related to your hardware.

---

### Post by tba2287 on 2007-11-09
I have the same model as you (although i have an Athlon X2 instead) and I'm having similar problems:

[http://ubuntuforums.org/showthread.php?t=605255&highlight=tba2287](http://ubuntuforums.org/showthread.php?t=605255&highlight=tba2287)

I'm wondering if anyone can help me here too?

---

### Post by flyingpengwin on 2007-11-09
> **Sef said:**
> Could you post your computer specs?  It could be a problem related to your hardware.
I posted everything about my computer i could think of
what other specs are needed???

---

### Post by bcrom on 2007-11-09
If you have an AMD processor, shouldn't you be using the AMD install disk and not the i386?

---

### Post by Dr Small on 2007-11-09
> **bcrom said:**
> If you have an AMD processor, shouldn't you be using the AMD install disk and not the i386?
No, you can use i386 for AMD 64 or not 64. It doesn't matter.

---

### Post by Iceni on 2007-11-09
A good idea is to try the alternate install cd. Burn one and see if it works. Go with the standard i386 32-bit version.

I've run into some problems with the live cd on laptops myself, there seem to be some trouble with the nvidia driver, but nothing like you describe.

---

### Post by flyingpengwin on 2007-11-09
> **Iceni said:**
> A good idea is to try the alternate install cd. Burn one and see if it works. Go with the standard i386 32-bit version.

I've run into some problems with the live cd on laptops myself, there seem to be some trouble with the nvidia driver, but nothing like you describe.
Isn't the alternative CD only to install???
I didn't think it had a Live CD version.
I cannot install Ubuntu on my laptop because it has Vista and I really do not want to deal with risking my C: drive during installation since i don't know exactly what I'm doing.

---

### Post by bcrom on 2007-11-09
Use a program like PartitionMagic Pro or Gnome Partition editor to create a separate partition for ubuntu.  I've done that many times and never clobbered my windows installation.  Still, dual booting is a risk, and if you can't possibly risk a total reformat, then I suggest getting a different drive to experiment with linux.

---

### Post by Pumalite on 2007-11-09
HP Pavilion Notebook dv6000 model
It's a notebook. Before you take the plunge, read this to get informed as to the nature of the problem:

[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-wireless-driver-issues.-403326/)
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

---

### Post by nudaydawning on 2007-12-31
On a similar note, I'm having the same problem.  The CD runs within the windows environment (giving you the screen with the menu and the three programs you can install) but I don't even get a "press any key to boot from CD" option when I restart my computer.

---

### Post by bcrom on 2007-12-31
Try pushing F12 and keep pushing as soon as you start your computer and see the BIOS screen.  If that doesn't work, try F2, and then all the function keys.  One of them should bring up a menu with the option 'Boot from CD/DVD.'

---

### Post by nudaydawning on 2007-12-31
Thanks.

---

