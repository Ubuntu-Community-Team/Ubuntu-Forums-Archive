---
title: "Remastersys"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2007-12-19
I've created my mastersys live boot, or so I believe. It finished what it was doing in bash, and there is a 4.5gB folder called 'remastersys' in my /home/   folder. Do I just burn that whole folder to a DVD? Because I looked at the iso that I named it as, and it's nowhere near 4.5gB

---

### Post by B34ST1Y on 2007-12-19
has anyone even heard of this?

---

### Post by bt224 on 2007-12-26
Inside that folder is your iso file, that's what you burn to the CD (or DVD).

[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

---

### Post by darthchaosofrspw on 2007-12-30
> **B34ST1Y said:**
> I've created my mastersys live boot, or so I believe. It finished what it was doing in bash, and there is a 4.5gB folder called 'remastersys' in my /home/   folder. Do I just burn that whole folder to a DVD? Because I looked at the iso that I named it as, and it's nowhere near 4.5gB

In /home/remastersys there should be an .ISO file. Right-click on it and select "Write image to disc". If it's over 700 MB, you'll have to burn it to a DVD. And after you burn the image to a CD/DVD, test it by running it live, and if it runs live okay, reboot, take the disc out, and boot into Ubuntu, go into your console, and type sudo remastersys clean, and that will clean it up.

---

