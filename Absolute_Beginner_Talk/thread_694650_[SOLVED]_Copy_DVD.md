---
title: "[SOLVED] Copy DVD"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-02-12
Hello!
I have one dvdrw drive. I have to copy some dvds. How can I do that? Is there any program to do so in ubuntu? + How can I make an image from a dvd/cd? + By right click on the drive icon and copy, it'll copy just the icon and not files! what should I do?
Thnak you.

---

### Post by LaRoza on 2008-02-12
[https://help.ubuntu.com/community/K9Copy](https://help.ubuntu.com/community/K9Copy)

---

### Post by bumanie on 2008-02-12
> sudo apt-get install k9copy
Is essentially the linux equivalent to dvd shrink, ie shrinks a double layer down to a single layer, with minimal loss of quality.

---

### Post by Thelasko on 2008-02-12
I have never done this, but in theory you can click on the "places" button on the GNOME menu bar and go to burn to DVD.  A new window will open and then you can copy the **contents** of your DVD into that window.  Then select burn and it will ask for a device.  Select burn to ISO.  Once it's finished burning the ISO you can then burn that ISO to DVD as you would normally. 

I can't think of a reason this wouldn't work.  As far as a one step solution I'm guessing the K9copy program is the way to go.  But I have never tried it.

---

### Post by Dr Small on 2008-02-12
> **LaRoza said:**
> [https://help.ubuntu.com/community/K9Copy](https://help.ubuntu.com/community/K9Copy)
+1
K9copy works good, unless you have a bad sector on the disc, like I did one time ... :|

---

### Post by Hoom@n on 2008-02-12
Thank you, but please tell me what is "sudo apt-get install libdvdread3 "?

---

### Post by yabbies on 2008-02-12
that command installs libdvvread3
which allows the playback of encrypted dvds

---

### Post by Hoom@n on 2008-02-12
Thanks, but to rip dvds, should I install "sudo apt-get install dvdrip" or I can use k9vopy->mpeg4? Which is better?

---

### Post by Hoom@n on 2008-02-12
And: That program is just for dvd movies. How can I make image from data dvds/cds? I mean something like nero in windows.
+++
How can I use an .iso as a cd/dvd. I mean a virtual drive. Like ultraiso in windows.
____
Thanks.

---

### Post by Keith Hedger on 2008-02-12
right click on the dvd on your desktop select copy copy disk and in the copy disk dialog select copy disc to : file image,that will create an iso and then just right click on the iso and select write to disk

---

### Post by LowSky on 2008-02-12
FYI:
nero make a linux version based on nero 7 called nerolinux3, its about $30 for a download off their website with a password key

---

### Post by Hoom@n on 2008-02-14
Thank you. I'm in iran and because of my goverment problems with us I can't pay money on the net! It's funny that's we can't do that just because of our goverment, we are iran people and they are iran goverment! Ok, thanks that copy image worked for me!

---

