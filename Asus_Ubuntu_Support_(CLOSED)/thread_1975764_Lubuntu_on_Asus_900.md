---
title: "Lubuntu on Asus 900"
date: 2012-05-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Microaide on 2012-05-07
I have tried twice to install Lubuntu 12.04 on my Asus 900 netbook. I did it using the lubuntu-12.04-alternate-i386.iso image, which I put on a USB stick using UNetbootin. I ran the install twice, once connected to internet and once not. Both times the install completes, but when I try to boot Lubuntu I get as far as the graphic startup screen with the blinking dots, then a black screen, and nothing more.

The MD5 sum of my iso is C02ABD9B05691AF1F1192FCC394B1713. I downloaded the iso three times and got same MD5 sum each time, although the web site [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) shows it as a1685837ad50845b6685086fc4743c83. Anyone know the correct MD5 sum? I did use the same iso to install Lubuntu under VirtualBox, and that worked fine, so it would appear my iso is OK.

Any hints as to why it won't boot on my Asus 900? Anyone have it working on a 900, and if so, how did you do it? I was hoping to get a newer OS than Eeebuntu 3.0.

Ok, I have some more information to add. My freeware Windows MD5 calculator was giving me the wrong value. I downloaded a different Windows MD5 calculator, and now get the correct value of a1685837ad50845b6685086fc4743c83. So my ISO is good.

Secondly, when I boot using the USB stick created with my ISO using UNetbootin and select "Check disc for defects", I get an error that says the ./pool/universe/l/lxpanel-indicator-applet-plugin_0.5.8+git20120212-0ubuntu3_i386.deb failed MD5 checksum verification. Your CD-ROM or this file may have been corrupted. I tried reformatting the USB stick and using UNetbootin again with same result. I tried a different USB stick with same result. I created a virtual machine with VirtualBax, booted the ISO image, and did a Check disk for defects. It passed with no errors.

But still, if I boot the USB stick on my Asus 900 and select Install Lubuntu, it will then boot to the graphical Lubuntu screen with the blinking dots, then go to a black screen forever.

Update May 9, 2012-
I have reason to believe that when I install Lubuntu 12.04 on my Asus 900 using the alternate install CD iso image, the operating system is actually running properly, but my screen is completely black so I can't see anything! The reason I think this is that when I press the special function keys (hold Fn while pressing one of the F1-F12 keys), some of them seem to work. In particular, I can turn my WiFi on and off, and I see the blue WiFi LED on the front of the computer go on and off. Also, when I plug in a USB flash drive, the light on the drive blinks for a few seconds, indicating that the drive is being mounted. But the screen is still black.

So I tried installing with the lubuntu-12.04-desktop-i386.iso image file, and it installed and runs perfectly.

I may not be out of the woods yet. The reason I tried installing with the alternate iso was that I also need to put Lubuntu on my Asus 701 machines, and they have only a 4G solid state drive, which I believe is too small to use the graphical desktop installer. Will the alternate installer work on an Asus 701? Or will the standard installer work with a 4.0GB drive? I guess I will find out.

But IMHO the alternate installer SHOULD WORK on an Asus 900. I think there is a problem with the alternate installer iso image, maybe a video driver problem.

---

### Post by Kalmar on 2012-09-09
The same problem here on Asus EEE PC 1225B. Anybody found a solution?

---

### Post by Plumtreed on 2012-09-09
I use Peppermint OS which is based on Lubuntu and used the following link to work around the 4GB size problem on my 701SDX.....[HTML]http://peppermintos.net/viewtopic.php?f=9&t=4911&start=10[/HTML]

It does work for Lubuntu as well. However, even Lubuntu seems 'heavy' for the eeePC700 series and you may want to consider using Peppermint which leans towards more web-based apps to make it 'lighter'.

...oops! OP goes back to May!!!!

---

### Post by Kalmar on 2012-09-10
Well, I pulled the subject out of limbo because that's the only description of a problem I found which is identical to my experience. Note that my 1225B has 500GB hard drive, so the space is not the limit here.

---

### Post by Plumtreed on 2012-09-10
> **Kalmar said:**
> Well, I pulled the subject out of limbo because that's the only description of a problem I found which is identical to my experience. Note that my 1225B has 500GB hard drive, so the space is not the limit here.

Different problem.....I can't help you with your problem but I can help the OP....who, clearly, no longer needs help.

---

### Post by marinara on 2012-09-10
"same problem" is not a description

---

