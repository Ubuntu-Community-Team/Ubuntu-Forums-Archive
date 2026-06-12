---
title: "Synaptic Package Manager"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-04-03
For some odd reason the Synaptic Package Manager locks up when opened, any ideas anyone? Worked last night before I shutdown now locks up.

---

### Post by taurus on 2007-04-03
What happens when you run this command from a terminal?

```
gksudo synaptic
```
Otherwise, update your system with

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by lamalex on 2007-04-03
try running from the command line and see if it gives some debugging info.
```
sudo apt-get <install, remove, etc.> package-name
```

---

### Post by compmodder26 on 2007-04-03
How long are you waiting?  On older systems it can take a little longer to query the internal package database when it first starts up.  Even on my T60 with a dual core processor and 1 GB of RAM, it can take upwards to 20 seconds the first time after a reboot.

---

### Post by J11Gyro on 2007-04-03
I had been waiting close to 20 min but not to worry now did the command and somehow the drive got unmounted and everything turned into a mess so am going to reload and start fresh again:lolflag:

---

### Post by J11Gyro on 2007-04-03
Ok I have booted to the live cd and am wondering if there is any way to repair grub for the boot so I do not have to do total reinstall

---

### Post by bodhi.zazen on 2007-04-03
Hmmm ...

From synaptic to grub ...

Perhaps a better description of the problem ...

---

### Post by zvacet on 2007-04-03
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub")

---

### Post by J11Gyro on 2007-04-03
Finally got re install done but that was plain strange. I ran 'gksudo synaptic' and everything went odd. not sure if current install is stable or not at this point,

---

### Post by taurus on 2007-04-03
What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by J11Gyro on 2007-04-04
Just got new install of edgy done, updating now

---

### Post by J11Gyro on 2007-04-04
Well that was a disaster, heh up and running now.

---

