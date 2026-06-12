---
title: "worth buying a mac air to install ubuntu?"
date: 2014-03-30
forum: Apple Hardware Users
---

### Post by grainbarcelona on 2014-03-30
Hi,
I'm a fan of ubuntu and I need to buy a new super light ultrabook - something that doesn't weight much more than a kilo. So I'm considering buying a Mac air and put Ubuntu on it. Is it worth it? Or will I get compatibility issues, and am I better off buying a windows machine?
Thanks!

---

### Post by buzzingrobot on 2014-03-30
Either way -- Windows or Mac -- you need to do your homework to find out how to correctly install Ubuntu.  Going for dual-boot will complicate matters.

Mac Airs seem to get good marks for running Ubuntu.  Various releases of Airs are out there, old and new. When I had MacBooks I found it was very important to focus on the specific version of the hardware when looking at running Linux. Apple hardware can often change from release to release.

Either way, if you are going to be the one installing Ubuntu on the new machine, you'll be helped if you can find a write-up from someone who had already done that on the same hardware.  You don't want to be the one to find out that some brand new just-released model has problems with Linux.

---

### Post by grainbarcelona on 2014-03-30
Thank you!
Now I hope to get a reply from someone who's got ubuntu running on the latest Mac Air! :-)
I'm sure I can handle the installation part, but I was wondering about the release of drivers and general compatibility issues.

---

### Post by dblreedr on 2014-03-31
I bought a Macbook Air 6,2 on Saturday and installed 14.04 (latest beta) as a dual boot.  I don't know exactly how long it took because we had supper in between as well as getting hubby packed for a trip, but I started around 4:30pm and it was fully done well before 11pm. 

First a little background - I was a total Windows user (but without any MS software) until January 2013 when my husband finally convinced me to switch to Ubuntu. My plan was to wait for a new machine and start clean, so I had been holding off. Anyway, we installed Ubuntu 12.04 on my Toshiba netbook with no issues and it didn't take me long to get used to a new O/S. 

My beloved Toshiba is now almost 5 years old and is struggling to keep up, so after a lot of research, the MBA was the best hardware option for my needs (Sturdy, long battery life, very light). I went for the 13 inch model because it was on sale for the same price as the 11 inch model. After almost 5 years on a 10 inch screen, the MBA seems gigantic even though it is only about 200 grams heavier than my Toshiba.

Okay, on to the install. I did most of it myself, with just a bit of help from my husband when doing any command line stuff, editing the refind.conf file (he uses emacs all the time, so it was quicker and easier to have him do this for me), and resizing and partitioning the flash drive

I used this step by step guide and it worked very well

[http://www.sourceprojects.org/installing-ubuntu-13-10-on-a-macbook-air-6-2](http://www.sourceprojects.org/installing-ubuntu-13-10-on-a-macbook-air-6-2) 

I deviated a bit:

I didn't start the download of the ISO first - waiting for the download ended up extending my install time by quite a bit longer than I anticipated.

When editing the refind.conf file, I used this page: [http://www.rodsbooks.com/refind/configfile.html](http://www.rodsbooks.com/refind/configfile.html) where the instructions are a little different from what is shown on the Ubuntu install page when changing the scanfor line - > The default is: internal, external, optical, manual on most systems, **but: internal, hdbios, external, biosexternal, optical, cd, manual on Macs**.

Make sure to just **resize** the Mac part of the flash drive - don't make another partition (that comes in the Ubuntu install). We accidentally made a second partition. It was very easy to reverse it all and get it right, but better to have it right the first time. 

I installed the most recent 14.04 beta instead of 13.10 (because it is so close to being released) - I used the AMD64 ISO (not the +Mac) 

We didn't do the step of changing the grub config file. (to be honest, I didn't notice that step until just now) - on my machine, Ubuntu shows as my first boot option

I went ahead with the install even though it didn't acknowledge the wifi  - once the install was complete, wifi was there and I had no problem logging onto my network. So I had no need to wire up to the network as mentioned in the instructions.

I am slowly getting it set up for use (transfering data, loading software, etc), but I'm on a deadline, so I am still working on my old machine.

Issues I've had so far:

The touchpad is very sensitive and somehow toggles between open applications like* alt+tab* does - I'm still trying to figure out how I'm doing that.

The webcam doesn't work, but it seems that it is something Ubuntu is working on. Nice to have, but not a huge issue for me. 

Bottom line, it was a lot quicker and easier than I anticipated. While I don't have it work functional yet to really test it out, what I've experienced so far, beyond some frustration with the touchpad sensitivity, has been reallly positive.

---

### Post by PartisanEntity on 2014-03-31
> **dblreedr said:**
> The webcam doesn't work, but it seems that it is something Ubuntu is working on. Nice to have, but not a huge issue for me. 

You may have done so already, but if not perhaps this may help. After installing Ubuntu 12.04 on my iMac I was not sure if the iSight was working. I tried using gucview and it worked perfectly, I also felt I had better quality than in Cheese (another webcam application).

---

### Post by dblreedr on 2014-03-31
> **PartisanEntity said:**
> You may have done so already, but if not perhaps this may help. After installing Ubuntu 12.04 on my iMac I was not sure if the iSight was working. I tried using gucview and it worked perfectly, I also felt I had better quality than in Cheese (another webcam application).

Thank you for the suggestion. Sadly, but not suprisingly, I got the following message:

> Guvcview error:
unable to open device
please make sure the camera is connected and that the correct driver is installed


Here's the link to the bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1276811](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1276811)

---

### Post by Mk32 on 2014-03-31
As a long-time Apple user, I would rather buy a Lenovo ThinkPad X240 with FHD (1920x1080) display. I believe that adds another $700 to the price tag, but...

---

