---
title: "No libdvdcss2 available"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by indigenous71 on 2007-05-27
I have done exactly as I've been instructed by **Enabling Multimedia in Feisty (HOW-TO)** (which is sticky-ed on the Absolute Beginner Talk section), however on the last step where it tells me to

> install libdvdcss2 and w32codecs using the following command:
```
sudo apt-get install libdvdcss2 w32codecs
```


it installs w32codecs, but it says
```
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
```

What should I do?

All help appreciated;)

---

### Post by moma on 2007-05-27
Hello, 

You will find libdvdcss2 in the Medibuntu repository.
Do as instructed in this guide --> [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

Also, **step 8 )** in [this guide...]("http://www.futuredesktop.org/") will solve your case.

---

### Post by RomeReactor on 2007-05-27
Hi. Do you have the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories? If you're not certain (and using Feisty), go [here]("http://ubuntuforums.org/showpost.php?p=2727375&postcount=3").

---

### Post by spartan777 on 2007-05-27
I'm not sure what this means, but i might mean that you don't have the repository you need. the easiest way to do this is to install automatix, which which do all the dirty work for you. click on this:

[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb)

then after it is installed, it shows up under the main menu in system tools. launch it, agree to stuff, and go to "Codecs and Plugins" on the top left pane. tick the box by "AUD-DVD Codecs" and click install. while you are at it, you can also install "Multimedia Codecs" and the plugins for firefox too.

---

### Post by indigenous71 on 2007-05-27
Thanks, I can now play all video formats I've tried and regularly use, however it has a grainy look, I've seen a thread on the Multimedia section about grainy video quality, however being a complete n00b I don't understand the advice given, can anyone help me improve the quality of video playback?

[The original topic is here...]("http://ubuntuforums.org/showthread.php?t=443465&highlight")

Thanks, as before, all help very much appreciated.

---

### Post by spartan777 on 2007-05-27
so all the first person said to get rid of the grain was to use another video player, VLC. This wouldn't make any difference, so that advice was misguided. However, the last guy mentioned some XY junk I don't even understand, but he did mention that ATI (AMD recently bought out ATI, so you can consider AMD and ATI interchangeable) cards have issues with grainy video on linux, so you can check if you have an ATI card or not. If you do, all you can do for now is hope that AMD gets their act together and puts out some better Linux drivers.

I did have a similar issue before with dvd's. I have an NVIDIA card. However, once I installed the NVIDIA linux drivers I didn't have any issues. 

Bottom line: If you have an AMD/ATI card, or integrated Intel graphics, all you can do is complain to them about their poor products. If you have an NVIDIA card, you can install their (really good) drivers.

---

### Post by indigenous71 on 2007-05-27
Thanks, I'm pretty sure this £350 laptop won't have an NVIDIA card, so I'm a little annoyed, no DVD's for me then :(

---

