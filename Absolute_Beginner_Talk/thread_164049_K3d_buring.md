---
title: "K3d buring"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by ice.man on 2006-04-22
how to make it burn at full speed at it will only burn at 1.3 when the dvd is 12 speed and it will only durn cd's at 10 not 40 any idears

---

### Post by bscbrit on 2006-04-22
The drive might be able to burn at 40x, but if the computer cannot provide data fast enough then K3d might be backing off to a speed at which it knows it can write a disk without errors.

Without more details of your system, and a clear statement of why you say K3d will not let you burn (are the options greyed out? Has it identified your drive correctly? etc) , it is hard to say.

---

### Post by htinn on 2006-04-22
The main thing to check is how fast your blank media is rated. Not all blanks can burn at top speed.

---

### Post by bscbrit on 2006-04-22
Yes, of course htinn is correct.  I had assumed that you were using disks rated for the speed that you are trying to burn at.

(Make note to self - Never assume, CHECK)

---

### Post by taurus on 2006-04-22
And make sure you have DRM enable for your CD drive!!!

---

### Post by louis_nichols on 2006-04-22
I think what you have to do is simply

```
$sudo hdparm -d 1 /dev/hdc
``` (assuming /dev/hdc is the device you are using)

If it says it can't find the command, install the package first:

```
$ sudo apt-get install hdparm
```

then try again. If you want this work after a rebot, you have to

```
sudo gedit /etc/hdparm
``` (or kedit /etc/hdparm)

and enter at the end of the file (again, assuming /dev/hdc is your writer device)

```
/dev/hdc {
dma=on
}
```

---

### Post by bscbrit on 2006-04-22
[QUOTE=taurus]And make sure you have DRM enable for your CD drive!!![/QUOTE]

I think that was a typo and you mean DMA? [Or are you a closet Microsoft fan? :-D ]

---

### Post by taurus on 2006-04-22
[QUOTE=bscbrit]I think that was a typo and you mean DMA? [Or are you a closet Microsoft fan? :-D ][/QUOTE]
Am I a closest to MicroSuck fan?  Now, those are the fighting words around here!!!  :)

---

