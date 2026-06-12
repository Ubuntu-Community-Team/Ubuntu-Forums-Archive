---
title: "Synaptic idiot"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Airman Basic on 2006-09-25
I just installed Ubuntu 6.06 tonight and I'm trying to enable mp3 support. I've downloaded the "ugly" file to the desktop and even unzipped it to a folder. How do I get the package handler to give me the option of installing it. I can navigate windows but don't know squat about Linux. Heck, I can't even bring up the command line to try some of the text strings I see to accomplish the mp3 thing. Anybody help a TOTAL newbie with this stuff?

---

### Post by henriquemaia on 2006-09-25
Can you give more details on the file you're trying to install? 

e.g. fullname, with extension.

---

### Post by mongooseman1128 on 2006-09-25
I'm pretty new to linux too, but I cantell you how to get to the command line. Go to applications> accessories> terminal.

---

### Post by JimmyLightning on 2006-09-25
You can get the command line (also called the Terminal) by going to Applications>Accessories>Terminal.

At least that's in Ubuntu 6.06.

Jimmy

---

### Post by nudnik on 2006-09-25
To access the terminal from Gnome: Applications>Accessories>Terminal

The applications tab is in the upper left hand corner of the desktop. 

Once you have access to that, everything should go smoothly.

---

### Post by Airman Basic on 2006-09-26
The files are here:
[https://help.ubuntu.com/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/ubuntu/desktopguide/C/codecs.html)
I guess they're .tar files, but even when I uncompress them into folders, I don't know what's next?

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg

---

### Post by nudnik on 2006-09-26
Use the terminal and type the following:

sudo apt-get install gstreamer0.10-plugins-ugly

Use the same prefix for the rest of your files. This will install them automatically from Synaptic.

---

### Post by CatKiller on 2006-09-26
> **Airman Basic said:**
> The files are here:
[https://help.ubuntu.com/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/ubuntu/desktopguide/C/codecs.html)
I guess they're .tar files, but even when I uncompress them into folders, I don't know what's next?

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg

These are all in the repositories, so can be installed easily with Synaptic.

First, you need to enable the Universe and Multiverse repositories:

Open Synaptic (System -> Administration -> Synaptic Package Manager)
Select Settings -> Repositories
Find the Ubuntu 6.06 LTS (Binary) and Ubuntu 6.06 LTS Updates (Binary) repositories in the list, click on Edit and tick the Community maintained (Universe) and Non-free (Multiverse) boxes for each. It will then prompt you to refresh the repository list, which you should do.

Then you can just install the packages - find them in the list, click on the box and select install, and then click on Apply.

The Universe packages aren't officially supported, but they generally work OK, and the Multiverse bits may be illegal, depending on where you live, or unethical, depending on how your community feels about Free software, or both.

---

### Post by megamania on 2006-09-26
> **Airman Basic said:**
> I just installed Ubuntu 6.06 tonight and I'm trying to enable mp3 support. I've downloaded the "ugly" file to the desktop and even unzipped it to a folder. 

I'm quite surprised to see that nobody suggested you the easiest way to solve the problem: use a ready-made script. I used BUMPS, but I believe Automatix is already installed in your system.

Running either one should get you going with all the main codecs/programs needed to make your system work for most daily tasks.

---

### Post by TheMono on 2006-09-26
If all you're looking to do is those codecs, you're better off using the terminal and "sudo apt-get install gstreamer0.10-plugins-ugly" and so on as suggested by nudnik. Scripts are better when you're doing lots of things, but for a single task like this they can cause more problems than they solve.

---

