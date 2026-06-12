---
title: "help, ubuntu 7.10, un my laptop dell 6400"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by ipatec on 2007-10-21
Hello,
I just downloaded Ubuntu 7.10 and ran it as Live CD...on my Dell Inspiron 6400(E1505)
Ok, I have some problems, my wireless connection doesn't work, and my Video Card (ATI X1400) I don't think it's recognized because the resolution is 1024x768 instead of 1280 x 800
Other problem is that I have Vista installed and I don't want to renounce at it yet, so how can I install Ubuntu, without removing Vista and affecting it's partition. Now I'm having just one partition (NTFS) where Vista it's installed...there are 50 GB available on it.
Thanks for help!

---

### Post by mikewhatever on 2007-10-21
I can't say much about the wireless, cause you have not mentioned neither the hardware nor the router models and it is too tricky to guess. You ati card is recognised if you where able to see the desktop, and the resolution should get to normal once Ubuntu is installed and the restricted driver enabled.
To dual boot Vista & Ubuntu [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
or 
[http://www.google.co.il/search?q=ubuntu+vista+dual+boot&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+vista+dual+boot&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

---

### Post by ipatec on 2007-10-21
The network devices are:
Broadcom 440x 10/100 Integrated Controller
Dell Wireless 1390 WLAN Mini-Card

---

### Post by ipatec on 2007-10-21
I've tried to install it, and it just remain at partition resizing with no progress...any advices?

---

### Post by Sef on 2007-10-21
>  I've tried to install it, and it just remain at partition resizing with no progress...any advices?

Use the partitioner in Vista to shrink the partition.  Then use Ubuntu Live CD to reformat the remaining partition.

---

### Post by amir.khosroshahi on 2007-10-24
About dual booting with Vista:
I don't have Vista, but I guess there are a lot of material about this issue in the web. like this one:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

About graphics resolution and wireless:
After you install Ubuntu 7.10, you can use restricted driver manager to  enable both drivers for your ATI X1400 (fglrx) and your Broadcom wireless adapter.

If you can't get your laptop's best resolution (mine is 1280x800) after enabling ATI proprietary driver, then tell me. I had the same problem and could resolv it.

---

### Post by jinnman on 2007-10-24
Same problem with my wireless.
I'm messing around with the Live CD of Ubuntu 7.10 64-bit.  I am connected via wire to my router fine, hence typing this post.  I tried the Restricted Drivers Manager and the firmware for my wireless pops up "Broadcom 43xx chipset family".  When I enable firmware, I get the error message:

The software source for the package
bcm43xx-fwcutter
is not enabled.

What am I doing wrong?

(The other driver was for my video, ATI downloaded and installed.  It asked me to reboot which I didn't since I'm using Live CD.)

---

### Post by olebebo on 2007-11-18
Same here. My notebook has an ati radeon mobility x1400 256MB graphics card, and it won't install the restricted driver, giving the message:

"The software source for the package
   xorg-driver-fglrx
 is not enabled."

I tried installing the driver from the ATI website, but without any results.

the same goes for my wireless card, a Broadcom 43xx controller.

What am I doing wrong?:(

---

### Post by Mazza558 on 2007-11-18
> **jinnman said:**
> Same problem with my wireless.
I'm messing around with the Live CD of Ubuntu 7.10 64-bit.  I am connected via wire to my router fine, hence typing this post.  I tried the Restricted Drivers Manager and the firmware for my wireless pops up "Broadcom 43xx chipset family".  When I enable firmware, I get the error message:

The software source for the package
bcm43xx-fwcutter
is not enabled.

What am I doing wrong?

(The other driver was for my video, ATI downloaded and installed.  It asked me to reboot which I didn't since I'm using Live CD.)

Go to synaptic package manager and click reload. Then just try again.

> **olebebo said:**
> Same here. My notebook has an ati radeon mobility x1400 256MB graphics card, and it won't install the restricted driver, giving the message:

"The software source for the package
   xorg-driver-fglrx
 is not enabled."

I tried installing the driver from the ATI website, but without any results.

the same goes for my wireless card, a Broadcom 43xx controller.

What am I doing wrong?:(

See above ^

Simply restart for Wireless Goodness. (I say good, but it can be a bit wierd with WPA wireless networks.)

Oh, and OP, you need a wired connection to get the net working on those models.

---

### Post by ipatec on 2007-11-23
I'm having the same problem. I've tried with synaptc reload but nothing changed...

---

### Post by Ub1476 on 2007-11-23
> **olebebo said:**
> Same here. My notebook has an ati radeon mobility x1400 256MB graphics card, and it won't install the restricted driver, giving the message:

"The software source for the package
   xorg-driver-fglrx
 is not enabled."

I tried installing the driver from the ATI website, but without any results.

the same goes for my wireless card, a Broadcom 43xx controller.

What am I doing wrong?:(

Go to> System>Administration>Software Sources, and check:

[LIST]
[*](main)
[*](universe)
[*](restricted)
[*](multiverse)
[/LIST]

(note that some probably are checked already)

Now download the driver via Restricted Driver Manager. When the driver has installed (don't reboot yet), open Synaptic (System>Administration>Synaptic packagemanager) and download xserver-xgl. It can be installed through a terminal too: "sudo apt-get install xserver-xgl" 

Now reboot, enjoy your resolution and turn on Visual Effects;)

---

### Post by ipatec on 2007-11-23
Thanks, I've solved this.
Now I'm having another problem.
Every time when I start the computer I have to connect manually my Wireless Connection. I'm using an WPA connection... I've saved it with password and SSID at manual connection but it doesn't connect automaticaly every time I start my computer. Any advice?

---

### Post by ipatec on 2007-11-24
I've saved the wireless zone, but it doesn't connect automaticaly ... I mean, every time when I start my computer I need to go at manual connection and select the zone. Any help please?

---

