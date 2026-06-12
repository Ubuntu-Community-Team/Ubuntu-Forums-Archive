---
title: "Ubuntu Installation"
date: 2008-03-20
forum: Apple Intel Users
---

### Post by Noob1234 on 2008-03-20
Hey guys,

I have a live copy of ubuntu and I have been playing around with it and now I wish to install it.  Im a huge noob when it comes to Ubuntu but I wish to learn.  Please help me out with my following questions.

Im running a MacBook with a core 2 duo processor.

1.  I want to partition my disk to give an amount to ubuntu only, and if anything goes wrong with ubuntu it wont mess with my more important stuff (using ubuntu for general web browsing and fun).  I have music etc on my current unpartitioned disk, how safe is it to create a partition as of now? What is the probability of me losing information?  Will Ubuntu create a partition during installation if I want it to? How should I create the partition?

2. When should I install the program to allow me to select between ubuntu/OSX at startup? Before or after Ubuntu installation?

3. When running ubuntu on my live cd I have no internet connection.  What program should I use and when should I install it?  How should I install it?  Same goes for touch pad problems, cant scroll using two fingers and cant right click, how should I fix those problems after installation?

I think thats all of my questions for now, I would appreciate some help.  I do know of and have read the wiki but some of it I simply didnt understand.  Please dumb down the process for myself.

Thanks A lot.

---

### Post by Noob1234 on 2008-03-20
anybody have any help and/or suggestions?

---

### Post by cyberdork33 on 2008-03-20
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by Noob1234 on 2008-03-21
Thank you, im going to start with that tomorrow and work from there.  For the mouse fix and the wireless fix, where do i go about changing that code? Where do i type it in? etc?

---

### Post by cyberdork33 on 2008-03-21
> **Noob1234 said:**
> Thank you, im going to start with that tomorrow and work from there.  For the mouse fix and the wireless fix, where do i go about changing that code? Where do i type it in? etc?
If you are on the latest Macbook Pros the touchpad and WiFi will likely not work anyway. The touchpad needs major software revision to work properly right now. The Wifi hardware changed to Broadcom, so you actually need to use ndiswrapper (and there are some other problems with that is Hardy right now. There are 3 or 4 threads here discussing the issues with the new Macbook Pros and I would look through them as well.

---

### Post by Noob1234 on 2008-03-21
I have my files backed up but instead of using bootcamp would you guys say its safe to use ubuntu's disk partioner?

---

### Post by cyberdork33 on 2008-03-21
> **Noob1234 said:**
> I have my files backed up but instead of using bootcamp would you guys say its safe to use ubuntu's disk partioner?use bootcamp, diskutility, or the commandline tools (diskutil resizeVolume) otherwise use gparted to resize your osx partition.

---

### Post by onshiv on 2008-03-21
...

---

### Post by Noob1234 on 2008-03-21
> **cyberdork33 said:**
> use bootcamp, diskutility, or the commandline tools (diskutil resizeVolume) otherwise use gparted to resize your osx partition.

it is my understanding that gparted is on the ubuntu install (as a prompt) and I can use that to partition.

---

### Post by cyberdork33 on 2008-03-21
> **Noob1234 said:**
> it is my understanding that gparted is on the ubuntu install (as a prompt) and I can use that to partition.yes it is on the live cd, but named "partition editor"

---

