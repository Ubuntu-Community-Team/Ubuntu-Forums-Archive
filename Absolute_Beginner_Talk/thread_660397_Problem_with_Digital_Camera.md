---
title: "Problem with Digital Camera"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by kadath on 2008-01-06
I just bought a Kodak C613 digital camera. I'm running Xubuntu 7.04 (yes, still). When I plug the camera in, nothing happens. Turning the camera on doesn't do anything either. It doesn't ask me if I want to import the photos.

What am I doing wrong? HALP!

---

### Post by PurposeOfReason on 2008-01-06
I'm assuming you use f-spot? In a terminal run f-spot-import.

---

### Post by califman831 on 2008-01-06
I had trouble with my kodak z650 until i updated kubuntu to the latest release and used digikam.

---

### Post by kadath on 2008-01-06
> **PurposeOfReason said:**
> I'm assuming you use f-spot? In a terminal run f-spot-import.

Nope, Xubuntu doesn't come with F-Spot. Is it the best app to use? Or are there others than can handle my camera?

---

### Post by philinux on 2008-01-06
Any specific reason for running xubuntu? System specs etc. 

gthumb works great for me for downloading from my canon g5. I'm running gutsy

---

### Post by SunnyRabbiera on 2008-01-06
> **kadath said:**
> Nope, Xubuntu doesn't come with F-Spot. Is it the best app to use? Or are there others than can handle my camera?

you can get fspot in xubuntu though in the repo's, its a good thing that gnome and XFCE are based around the same code so you should not have any worries

---

### Post by PurposeOfReason on 2008-01-06
> **kadath said:**
> Nope, Xubuntu doesn't come with F-Spot. Is it the best app to use? Or are there others than can handle my camera?
It's always been the easiest for me and does the job relatively quick.

---

### Post by kadath on 2008-01-06
> **philinux said:**
> Any specific reason for running xubuntu? System specs etc. 

gthumb works great for me for downloading from my canon g5. I'm running gutsy

I run Xubuntu because I like Xfce over Gnome.

I guess I'll try looking into gThumb and F-Spot. Are there any lighter apps? All I need is something that can transfer my photos from the SD card to ~/ and nothing else. I use GIMP for editing and GQView for managing, currently.

---

### Post by PurposeOfReason on 2008-01-06
> **kadath said:**
> I run Xubuntu because I like Xfce over Gnome.

I guess I'll try looking into gThumb and F-Spot. Are there any lighter apps? All I need is something that can transfer my photos from the SD card to ~/ and nothing else. I use GIMP for editing and GQView for managing, currently.
A default XFCE arch install with fspot does this for me. It makes a directory, ~/Photos. From there it has folders per date so it looks like so.

--Home folder
---Photos
-----2008 (year)
-------01 (month)
--------06 (date)

With a default Ubuntu install it just dumped them in ~/.

---

### Post by kadath on 2008-01-06
> **PurposeOfReason said:**
> A default XFCE arch install with fspot does this for me. It makes a directory, ~/Photos. From there it has folders per date so it looks like so.

--Home folder
---Photos
-----2008 (year)
-------01 (month)
--------06 (date)

With a default Ubuntu install it just dumped them in ~/.

Alright, I'll try out F-Spot then. Thanks!

---

### Post by darkazurka on 2008-02-07
Did it work? I'm asking because I have thoughts of buying one of those cameras (where I live it costs 85,00 € , so it is affordable for me) . A simple "yes, it worked" would be enough.

---

### Post by doom3d on 2008-03-03
Hi,

I have Ubuntu 7.04, a Kodak C330 and gthumb is working fine for me, but..
Actually it doesn't allow to UPLOAD files to my SD stick. The devive is listed by lsusb, but it's missing from /etc/fstab.
 I want to share files by uploading files to my camera, and bringing the SD memory stick with me. I don't want to buy a card reader. 

So how can I mount my camera? 
Thanks.

Doom3d

---

