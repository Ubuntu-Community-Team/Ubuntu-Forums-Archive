---
title: "Ubuntu 7.07 not loading live CD..."
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by cokashmola on 2007-10-15
So, I start out selecting "Start or Install Ubuntu" and begin the boot. The bar comes across the screen and loads all the way up. Then, this white horizontal bar appears in the upper left hand conrner and then goes away. From there, everything stops. CTRL+ALT+F2 doesn't do anything, so that means it isn't even running.

Can anyone help out with this?

---

### Post by overdrank on 2007-10-15
> **cokashmola said:**
> So, I start out selecting "Start or Install Ubuntu" and begin the boot. The bar comes across the screen and loads all the way up. Then, this white horizontal bar appears in the upper left hand conrner and then goes away. From there, everything stops. CTRL+ALT+F2 doesn't do anything, so that means it isn't even running.

Can anyone help out with this?

Hi and can you give us some specs on the system and are you running Feisty 7.04 or Gutsy 7.10?

---

### Post by cokashmola on 2007-10-15
Oops, typo. It's 7.04 Feisty. My specs are:

Compaq Deskpro EN
Intel Pentium III Processor
863 MHz
288 MB of RAM    o.0

Is that all you need?

---

### Post by overdrank on 2007-10-15
> **cokashmola said:**
> Oops, typo. It's 7.04 Feisty. My specs are:

Compaq Deskpro EN
Intel Pentium III Processor
863 MHz
288 MB of RAM    o.0

Is that all you need?

Hi the memory  is a little low but it may work. You may check the disc for errors and also run a checksum
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Also if you just want to install you can use the alternate cd it is for low memory systems, found here
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)
Good luck!

---

### Post by Frak on 2007-10-15
You have to have at least 320MB of RAM to boot a live CD

EDIT
Try the AlternateCD, I thought you were talking about Gutsy Gibbon.

---

### Post by cokashmola on 2007-10-16
Okay, thanks to the both of you! I'll give it a shot.

Also, it'd be weird if its a RAM problems because I got the same LiveCD to boot on my 128mb RAM piece of junk laptop. (IBM 770X).

However, I'll still give it a shot!

---

### Post by cokashmola on 2007-10-16
The Alternative CD installed Ubuntu just fine, but now I have another problem. When I boot, Ubuntu shows the bar and loads all the way up. Then, I just get a black screen. I tried CTRL+ALT+F2 and nothing happened yet again.

---

### Post by overdrank on 2007-10-16
> **cokashmola said:**
> The Alternative CD installed Ubuntu just fine, but now I have another problem. When I boot, Ubuntu shows the bar and loads all the way up. Then, I just get a black screen. I tried CTRL+ALT+F2 and nothing happened yet again.

Hi what is the model of the video card in the system?

---

### Post by cokashmola on 2007-10-16
I know that it is an ATI Radeon, but I'm not sure the exact model number. Will I need to find this out?

---

### Post by cokashmola on 2007-10-16
Ah, found it.

ATI Radeon 7200 32MB TV Rage Theater PCI

---

### Post by cokashmola on 2007-10-16
It's actually just ATI Radeon 7200 32MB Rage Theater PCI

---

### Post by overdrank on 2007-10-16
> **cokashmola said:**
> It's actually just ATI Radeon 7200 32MB Rage Theater PCI

You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and  then hit enter and then  b to boot. This will allow you to see if any errors are shown.  Hope this helps. Good luck!

---

### Post by cokashmola on 2007-10-16
Okay, I'll give this a try!

---

### Post by SoloSalsa on 2007-10-16
While the Rage series works with legacy drivers and such, Rage Theater and TV Rage and Rage AllInWonder have little or no support.  I looked into them a year ago, when trying to repurpose an old computer...  The card was aweful for a GUI, as I recall.  I doubt things have changed since then.

---

### Post by cokashmola on 2007-10-16
Removing quiet and booting didn't work, so I'm going to mess around with it for a bit to see if other options will work.

What I think I will try is booting in recovery mode and enter the following commands..

apt-get install linux-386
apt-get remove linux-server

This will downgrade the kernel, which may help because my computer is rather old.

---

### Post by cokashmola on 2007-10-16
Bleh, I was afriad someone would say that Salsa. I suppose i could invest in a new video card if this doesn't work. What I really need is a new computer though :]

---

### Post by nikoPSK on 2007-10-16
Hi, When I first got ubuntu, I used the xubuntu livecd to recover my data then figured, screw windows, I'm going open-source. So i got the ubuntu live cd, no worky, I have 512 ram like you and a 2 GHz processor. The alternate worked fine. And if you just want to uubntu a try give [wubi]("http://wubi-installer.org/") a try::)

---

### Post by lazyart on 2007-10-16
Try xubuntu instead.  The video card is not the problem-- I've run with a Radeon 7000.

---

### Post by nikoPSK on 2007-10-16
yea, Ive got a nvidia geforce 5200 GTX

(dated) 

But if you're just looking for the taste of ubuntu try xubuntu or wubi.

---

### Post by Frak on 2007-10-16
> **nikoPSK said:**
> yea, Ive got a nvidia geforce 5200 GTX

(dated) 

But if you're just looking for the taste of ubuntu try xubuntu or wubi.
I've 5500, nothing to worry ;)

---

### Post by nikoPSK on 2007-10-17
> **Frak said:**
> I've 5500, nothing to worry ;)

I found a 7200 for 120 $ should i egt ti? Also I want to run dual screens so yeah:P:)

---

### Post by Frak on 2007-10-17
> **nikoPSK said:**
> I found a 7200 for 120 $ should i egt ti? Also I want to run dual screens so yeah:P:)
Sure, go for it. Great price.

---

