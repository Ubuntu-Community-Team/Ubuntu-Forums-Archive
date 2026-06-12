---
title: "Problems with resolution in Xubuntu"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by yayalose on 2006-10-13
Hello everyone!!! This is my first post here (I've already posted in a lot of linux forums and I'm pretty desperate)... I've been using Suse 10 for a year but i though it was very slow, so I decide a few weeks ago to change to Xubuntu 6.06... I'm very pleased with it, I love its speed and its easy way to update and install software... but it couldn't be a piece of cake at all... I've configured everything but the screen. It's supposed that I've already installed the nVidia drivers (I've got an nVidia 6600 Go PCI Express, 256 MB and so on...) but i can't set a resolution higher than 1024x768... and my screen does support a 1680x1050 resolution!!!... I've tried to reconfigure the Xserver but I don't know the correct parameters of some settings and, in the end, I always break it down...

---

### Post by ske1fr on 2006-10-13
> **yayalose said:**
> It's supposed that I've already installed the nVidia drivers (I've got an nVidia 6600 Go PCI Express, 256 MB and so on...) but i can't set a resolution higher than 1024x768... and my screen does support a 1680x1050 resolution!!!... I've tried to reconfigure the Xserver but I don't know the correct parameters of some settings and, in the end, I always break it down...

Not sure quite what you mean, but if you haven't actually taken steps to install the proprietary nVidia drivers then you'll be using the free ones, and I think they may be limited in resolution settings.  There are quite a few ways to do it - last time I used Automatix.

If your monitor isn't in the standard list available then you will just have to go and find the technical data for it from the manufacturer's website, as the default ranges will restrict the refresh rates available.  I find dpkg-reconfigure xserver-xorg in a terminal easier than changing the xorg.conf file directly, although I still have to do this sometimes.

If you know this already - just ignore me!

---

### Post by Bobajot on 2006-10-13
I loaded Automatic2 last night to fix exactly the same problem [http://getautomatix.com]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38") worked a treat for the Nvidia driver.

See my thread for xorg.conf changes I made.[http://www.ubuntuforums.org/showthread.php?t=276381]("http://www.ubuntuforums.org/showthread.php?t=276381")

---

### Post by Medieval_Creations on 2006-10-13
nVidia drivers are always tricky... I had the same problem with my 6200.

I've done it both ways, downloading the nvidia module soure and compiling it... (which I don't recommend, if you enjoy having a full head of hair) :)

I apt'ed nvidia-glx and used dpkg-reconfigure xserver-xorg...

But, I would suggest using Automatix2 as well, even though I like to fix and load everything my self I had such a pain with the nvidia drivers that I broke down and tried it and it worked beautifully.  The only thing I had to change was edit xorg.conf with my resolution settings...

Good luck...

---

