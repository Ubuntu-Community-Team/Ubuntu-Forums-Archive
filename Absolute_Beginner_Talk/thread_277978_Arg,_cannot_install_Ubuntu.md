---
title: "Arg, cannot install Ubuntu"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by rhlowe on 2006-10-15
Okay guys, here's the deal, I have an older PC I want to run Ubuntu on:

Pentium II running just under 400MHz
256mb PC100ram
6GB IDE HDD

I am unable to get Ubuntu running on this system. It runs all the way through the install, and when it comes time to run the Live CD, nothing happens. The install docs say it could take awhile, so I let is run for 2 hours with no luck.

I thought, maybe the Cd was bad, so I downloaded the .iso from another source, made a new Cd and tried again, no luck.

I tried running Knoppix to see if it works, it does.

I don't need to run the live CD of Ubuntu to know I want to install it, is there any way I cam bypass that portion and go straight to the installation?

Also, I will be running this box as a web server and have managed to successfully install the server version of Ubuntu, however I want the GUI, so I am attempting to install the desktop version over it. Since I have the server version working, is it possible to install the GUI over that?

---

### Post by taurus on 2006-10-15
At the prompt,

```

sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start

```

---

### Post by ReaderRat on 2006-10-15
> I thought, maybe the Cd was bad, so I downloaded the .iso from another source, made a new Cd and tried again, no luck.
How did you burn the  ISO file?....As a file (data) or as an image? Did you burn the image at a slooow speed (4X)?
These can cause your problems.
ISO - Downloading & Burning
          [http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)
          [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by rhlowe on 2006-10-15
Taurus,

Thanks, I will try that.

ReaderRat,

Yes, I burned all those isos as data at 4x.

---

### Post by NeoLithium on 2006-10-15
You may want to try to use the Alternate Install CD instead; which is usually better set up for older systems that are similiar to yours.

---

