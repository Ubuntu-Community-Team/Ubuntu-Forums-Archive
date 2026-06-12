---
title: "Beryl: Getting Started"
date: 2007-05-21
forum: Apple Intel Users
---

### Post by erakepio on 2007-05-21
Ok, I'm trying to get Beryl installed on my Ubuntu partition in my Macbook (using Core 2 Duo).  I have inbuilt graphics chipset and ive already applied the 915resolution package.

According the wiki, installing Beryl on Feisty, Ive got 4 options.. AIGLX, XGL, ATi and NVidia.  Im not 100% sure which i should follow (gut feeling says XGL).

I've not used Beryl before and my Linux experience is quite thin on the ground as I've only really used it before to play around with..these days im looking to switch full from windows.

Thanks Again

---

### Post by benanzo on 2007-05-21
If you have a MacBook (not Pro) installing and running Beryl should be really easy.

First, verify that your X server is setup correctly.
Run this command in a terminal:
```
glxinfo | grep direct
```

if it returns:
```
direct rendering: Yes
```

then you're ready for Beryl:
```
sudo apt-get install beryl beryl-manager beryl-ubuntu emerald
```

If it returns:
```
direct rendering: No
```

Then you need to fix the X server to use AIGLX (which is part of the default X server)
You only need to use XGL (extension to the X server that provides composite rendering) if you use an ATI card (as in the MacBook Pros.)

---

### Post by ronocdh on 2007-05-21
> **benanzo said:**
> If you have a MacBook (not Pro) installing and running Beryl should be really easy.)
Oh, Benanzo, you spoiled brat with your open hardware integrated graphics chipset. ;) Unfortunately, setting up Beryl on the MBPs is a bit more work than for the MacBooks, but it's not at all impossible; with the Restricted Drivers Manager in Feisty, it's a lot easier for many people.

Check out [this guide]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m"), which is what I used to get Beryl running smoothly.

---

