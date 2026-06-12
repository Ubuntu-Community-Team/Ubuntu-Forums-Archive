---
title: "I need help synching my iPod"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by TheFourElements on 2006-12-11
I got an iPod ofr my birthday and I can't for the life of my figure out how to put music from my linux machine on it. So far I have just been using my sister's windows machine. Could someone give me step by step instructions on using amarok or gtkpod or if anyone has anyother programs that work better. Also, I am still using breezy if that makes any difference. Thanks a million in advance.

---

### Post by x64Jimbo on 2006-12-11
It would help a lot to know what you've already tried and what hasn't worked, so we can get an idea where to start. There are plenty of end-to-end tutorials out there.

---

### Post by TheFourElements on 2006-12-11
basically I haven't tried anything. I plugged it in to my computer and couldn't find out where it mounted so I kind of gave up. That's it.

---

### Post by dolphinsonar on 2006-12-11
I have been using my ipod mini with amoroK and it works great for managing my music on my ipod.

---

### Post by Paul41 on 2006-12-11
I have been using Banshee with my iPod Nano and that has worked good for me.

---

### Post by x64Jimbo on 2006-12-11
To mount the ipod, just click on it on the desktop. The path that it gives you (probably something like /media/ipod or /media/sda1) is what you plug into amarok, gtkpod, or whatever else you want to use.

---

### Post by TheFourElements on 2006-12-11
I'm using window maker so I don't really have a desktop. That's why I couldn't find outv where it mounted.

---

### Post by x64Jimbo on 2006-12-11
That's the kind of info that's needed earlier. If you're new to Linux I highly suggest moving to a more supported window manager until you know more about how the insides of Linux work. As for finding out what your iPod's device is, you can probably get that from running
sudo fdisk -l
but that won't mount it for you, and it needs to be mounted for it to be managed. Gnome and KDE both automount iPods.

---

### Post by Kingfield on 2006-12-13
if its the new iPod nano, most likely it won't automount - search for iPod nano and then click on the appropriate thread - it's pretty easy

---

