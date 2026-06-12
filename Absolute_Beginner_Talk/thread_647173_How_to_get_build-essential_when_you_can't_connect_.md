---
title: "How to get build-essential when you can't connect to the internet?"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Cavalryman on 2007-12-22
I have installed Ubuntu 7.10 on an older laptop. Everything works fine except the 10/100 ethernet device. I have a Linux driver on a disk that came with the computer, but I think I need the tools in *build-essential* to compile it. The problem is...I can't connect to the Internet with that computer to download *build-essential* because the device that doesn't work is the very one I need to make the connection. I don't have a dial-up Internet service and the laptop doesn't have a wireless connection (It's rather old). Is there some way to download *build-essential* to another computer and transfer it on a disk or USB drive?

---

### Post by Buffalo Soldier on 2007-12-22
build-essential is available in the Ubuntu CD. I think you just need to insert the CD, add it to the repo list (if it's not already added before) and just apt-get as usual.

---

### Post by adityakavoor on 2007-12-22
```

sudo apt-get install build-essential

```

---

### Post by spiderbatdad on 2007-12-22
[http://ubuntuforums.org/showthread.php?t=449715](http://ubuntuforums.org/showthread.php?t=449715)

on the cd. Insert the CD into the drive and run

```


sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v


``` Pirated from Taurus

---

### Post by Cavalryman on 2007-12-22
I'll try that. Thanks for the speedy replies!

---

