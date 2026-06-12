---
title: "complicated problem"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by keenwerkz on 2006-03-14
I started using ubuntu about 6 months ago, started w/ ubuntu 5.04 (using dual boot in my office), upgraded to 5.10 and then recently i tried kubuntu 5.04. when i resigned from my work and stayed at home ;)

I was really pleased with kubuntu 5.04, i was able to installthe drivers of my motherboard (nvidia nfoce 4) and video card (geforce 6600), install libraries in order to play dvd's and other win-based media formats.

Now I tried upgraded to kubuntu 5.10 my problems are the following:

1. It cant detect my usb hard drives (fat file system) [error message: "The file or folder media:/sdbxx: does not exist."]
2. I cant install the drivers for my mother board and videocard; sort of something wrong with the linux headers

I am using 5.10 install CD, and unfortunately I have no internet access at home so i download my files thru internet cafes. ;( meaning i cant update using apt-get...  :'( is there a way i can download my needed upgrades from the cafe and install them when i get home?  ???

Hope some one can help me remedy my problems.

---

### Post by derelict on 2006-03-14
You can use "apt-get -d" to only download the files without installing them

---

### Post by LordBug on 2006-03-14
1.  Can you post the lines from dmesg from when you plug in a USB device?  I've had no issues with USB drives in 5.10...

2.  The nVidia video drivers, at least, are in the repositories.  'sudo apt-get -d nvidia-glx' will grab them and a few other things.  Not sure about the board drivers, though I should look as I have an nForce board too :)  If you want to compile them all anyway, 'sudo apt-get -d build-essential' should get the headers and lots of other things you'll need.  This is assuming the cafe has apt-get :)  If not, you can grab the packages from the Net (though I cannot remember the site anymore).  Use dpkg to install once you get them all home.

---

### Post by keenwerkz on 2006-03-15
thanks alot for the replies. ;)

---

