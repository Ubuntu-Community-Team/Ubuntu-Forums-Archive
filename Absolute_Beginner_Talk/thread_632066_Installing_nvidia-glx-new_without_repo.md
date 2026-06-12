---
title: "Installing nvidia-glx-new without repo"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by CheeseEatingBulldog on 2007-12-05
I am installing a laptop at work and cannot get on internet with it. I can however download deb files and dump them accross with a usb stick.

I am trying to install the nvidia-glx-new.deb package but it won't install due to the error: dependency is not satisfiable: nvidia-glx. Now I tried installing the nvidia-glx package and then the nvidia-glx-new package but that just gives a conflict and also won't install. Why won't it install the package???

---

### Post by GSF1200S on 2007-12-05
> **CheeseEatingBulldog said:**
> I am installing a laptop at work and cannot get on internet with it. I can however download deb files and dump them accross with a usb stick.

I am trying to install the nvidia-glx-new.deb package but it won't install due to the error: dependency is not satisfiable: nvidia-glx. Now I tried installing the nvidia-glx package and then the nvidia-glx-new package but that just gives a conflict and also won't install. Why won't it install the package???

Have you thought about trying the actual website drivers? You can install them by killing X and it will custom compile a kernel (nvidia kernel) for the install. Just make sure the nvidia common kernel is completely removed after you install the driver, or X will fail to load with an API mismatch error...

**Let me know if you need any more info- I did this a thousand times on Edgy, lol

---

### Post by CheeseEatingBulldog on 2007-12-05
I did try that but then it fails on needing libc headers, as far as I can tell libc is installed...

---

### Post by GSF1200S on 2007-12-05
> **CheeseEatingBulldog said:**
> I did try that but then it fails on needing libc headers, as far as I can tell libc is installed...

hmm.. give me a few while I research that one.. ill edit this post when I got a solution (if :))

**EDIT** Are these the headers that the laptop said it had? Check this thread out:

[http://ubuntuforums.org/showthread.php?t=418380](http://ubuntuforums.org/showthread.php?t=418380)

---

### Post by CheeseEatingBulldog on 2007-12-05
Thanks for the effort...bloody annoying not having internet and installing ubuntu. Maybe I should start downloading the dvd. 

Anyway, I can't figure what header package it needs...

---

### Post by GSF1200S on 2007-12-05
> **CheeseEatingBulldog said:**
> Thanks for the effort...bloody annoying not having internet and installing ubuntu. Maybe I should start downloading the dvd. 

Anyway, I can't figure what header package it needs...

I think the header files listed in that thread are actually on the Ubuntu LiveCD. You could open up the lappies sources.list and comment out all http sources, and uncomment the cdrom source. Then apt-get the packages from that thread and it should pull them from the CD.. just a thought

---

### Post by CheeseEatingBulldog on 2007-12-05
I installed the libc6-dev package and re-run the Nvidia.run installer, but still gives me the error that my libc dev package is not installed????

---

### Post by GSF1200S on 2007-12-05
> **CheeseEatingBulldog said:**
> I installed the libc6-dev package and re-run the Nvidia.run installer, but still gives me the error that my libc dev package is not installed????

What about the packages referred to by HymmToLife? I think the Linux-headers and xorg-dev are the key ones.. once again, you should be able to pull them from an Ubuntu CD if you edit the sources.list. Im not sure if its on the LiveCD or if its on the Alternate; you may need to bring both..

---

### Post by CheeseEatingBulldog on 2007-12-05
right the linux headers are apparently already installed. (an i next to all of them when doing a aptitude search for headers). ....weird

edit: There is no xorg-dev package..will look on the online rep.

---

### Post by GSF1200S on 2007-12-05
> **CheeseEatingBulldog said:**
> right the linux headers are apparently already installed. (an i next to all of them when doing a aptitude search for headers). ....weird

edit: There is no xorg-dev package..will look on the online rep.

Must be on the online rep- this is what shows up for me in the repos.. I would presume the internet ones are the same...

---

### Post by CheeseEatingBulldog on 2007-12-05
Thanks for your help, I installed a crapload of dependency packages for the xorg-dev, but got it to work.

---

### Post by ruibernardo on 2007-12-05
> **CheeseEatingBulldog said:**
> I installed a crapload of dependency packages for the xorg-dev, but got it to work.
Hi CheeseEatingBulldog,

to know which dependencies to download to install a given package for your offline computer, you can use a website i'm developing: [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net). 

It uses 1 file from your system (/var/lib/dpkg/status - ~1 MB) that you upload and runs apt-get --print-uris with it, giving you the list of package files you need to download. You can do it even from Windows.

To see how to set it up, check [this]("http://ubuntuforums.org/showpost.php?p=3742162&postcount=11").

---

### Post by GSF1200S on 2007-12-05
> **CheeseEatingBulldog said:**
> Thanks for your help, I installed a crapload of dependency packages for the xorg-dev, but got it to work.

Cool ;)

---

