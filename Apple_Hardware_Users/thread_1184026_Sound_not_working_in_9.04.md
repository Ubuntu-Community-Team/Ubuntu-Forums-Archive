---
title: "Sound not working in 9.04"
date: 2009-06-10
forum: Apple Hardware Users
---

### Post by AtomicCheese on 2009-06-10
I just upgraded to Ubuntu 9.04 on my iMac, but the sound stopped working. Any ideas on why this would happen?

---

### Post by 311005901 on 2009-06-10
What iMac version do you have?
In "Applications>Accessories>Terminal" type in ```
sudo dmidecode -s system-product-name
```
Post back with what you've got.

---

### Post by AtomicCheese on 2009-06-10
iMac7,1

---

### Post by AtomicCheese on 2009-06-12
Any ideas?

---

### Post by 311005901 on 2009-06-14
Ok, sorry for the long pause. I've been busy. :neutral:

[This post]("https://bugs.launchpad.net/mactel-support/+bug/360866") says that what you're encountering is an ALSA bug that they've been trying to patch for a while, but there's a workaround.

Open up a terminal. (Applications>Accessories>Terminal)
Type in ```
gksu gedit /etc/modprobe.d/alsabase.conf
```
Type in your password and paste this into the editor: ```
options snd-hda-intel model=asus-a7m
```

Then, restart your computer and boot into Jaunty.
Open the terminal again and type ```
alsamixer
```
Turn everything up and you should have sound out of the internal speakers and also through the headphone/line out jack.

Post back if that works for you. ;)

---

### Post by AtomicCheese on 2009-06-14
That doesn't seem to work. If it matters, I got the iMac in late 2007.

---

### Post by knattlhuber on 2009-06-22
Got the same iMac model (7,1) and had the same problem after upgrading to Jaunty.
I followed the instructions in this thread
[http://ubuntuforums.org/showthread.php?t=1130384]("http://ubuntuforums.org/showthread.php?t=1130384")
and then added
```
options model=mbp3
```
as per iMac Wiki ([https://help.ubuntu.com/community/Intel_iMac]("https://help.ubuntu.com/community/Intel_iMac"))
to /etc/modprobe.d/alsa.conf and it worked.

---

