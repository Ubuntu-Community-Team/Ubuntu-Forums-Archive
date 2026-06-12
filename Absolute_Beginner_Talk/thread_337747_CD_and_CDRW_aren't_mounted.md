---
title: "CD and CDRW aren't mounted"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-01-13
Hey folks. I'm running on Edgy now for a couple weeks, and I'm enjoying it for the most part. I am having issues, however, with certain things that used to work in Dapper.
My two CD drives aren't mounted, and I never had to mount them in Dapper for them to work . . .How can I mount them now?
Also, every time I have updates available, there's always two that don't update . . .Libggi2 and Mplayer. They had issues in Dapper as well. It's not causing any obvious problems for me, but I'd like to have it fixed anyhow.

---

### Post by taurus on 2007-01-13
```
sudo mount /dev/hdc /media/cdrom0
```
(If the drive is /dev/hdc...)

---

### Post by CheshireMac on 2007-01-13
> **taurus said:**
> ```
sudo mount /dev/hdc /media/cdrom0
```(If the drive is /dev/hdc...)
No medium found

---

### Post by taurus on 2007-01-13
Insert a CD into a CD drive and paste this output here then!

```
dmesg | tail
```

---

### Post by CheshireMac on 2007-01-13
What does that do? This is what I get :
mac@mac-desktop:~$ dmesg | tail
[17179604.556000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179604.580000] Bluetooth: RFCOMM socket layer initialized
[17179604.580000] Bluetooth: RFCOMM TTY layer initialized
[17179604.580000] Bluetooth: RFCOMM ver 1.7
[17179605.136000] eth1: no IPv6 routers present
[17179605.208000] eth0: no IPv6 routers present
[17185326.756000] eth0: link down.
[17185333.248000] eth0: link up.
[17185340.160000] eth0: link down.
[17185342.380000] eth0: link up.

---

### Post by taurus on 2007-01-13
So you have two CD drives, right?  Do you know what they are?  Look in /var/log/messages to see exactly what they are.

```
sudo more /var/log/messages
```

Or you can look in /etc/fstab to see what they are called.

```
more /etc/fstab
```

---

### Post by CheshireMac on 2007-01-13
> **taurus said:**
> So you have two CD drives, right?  Do you know what they are?  Look in /var/log/messages to see exactly what they are.

```
sudo more /var/log/messages
```Or you can look in /etc/fstab to see what they are called.

```
more /etc/fstab
```
I'm having trouble, Taurus . . ./var/log/messages is giving me an immense list of activities, and fstab is denied.

---

### Post by taurus on 2007-01-13
You mean you get an error message from running this command?

```
more /etc/fstab
```

---

### Post by CheshireMac on 2007-01-13
> **taurus said:**
> You mean you get an error message from running this command?

```
more /etc/fstab
```
Sorry . . .I was entering the wrong cmd . . .here we go . . 
```
mac@mac-desktop:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=581942b1-447c-48ab-b033-f6123c0e229c / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb5 -- converted during upgrade to edgy
UUID=d3728f8f-c5d5-483b-abc1-9fec83dcbd9f none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=ac3e8ad1-4134-46f1-a681-6357624e4f6c /storage ext3 defaults 0 0

```

---

### Post by taurus on 2007-01-13
According to /etc/fstab, you only have one CD drive, /dev/hdc.  Therefore, put a working CD into the top drive and see if you can mount it with the command above!  Otherwise, look in "dmesg" to see what happens.

```
dmesg | more
(hit the space bar for the next 24 lines...)
```

---

### Post by CheshireMac on 2007-01-13
That's odd . . .My RW drive is working now, but my regular CD drive isn't being detected at all?!?!? Do you know what's going on here?

---

### Post by taurus on 2007-01-13
So the CD-RW is /dev/hdc and the regular CD drive is off the radar for now!  How did you connect your regular CD and did you set the jumper in the back right?  Look in the BIOS to see if it detects both CD drives at all?

---

### Post by CheshireMac on 2007-01-13
> **taurus said:**
> So the CD-RW is /dev/hdc and the regular CD drive is off the radar for now!  How did you connect your regular CD and did you set the jumper in the back right?  Look in the BIOS to see if it detects both CD drives at all?
I didn't put this machine together, actually. I'm not sure how it's connected . . .I'll check BIOS now . . .

---

### Post by CheshireMac on 2007-01-13
> **taurus said:**
> According to /etc/fstab, you only have one CD drive, /dev/hdc.  Therefore, put a working CD into the top drive and see if you can mount it with the command above!  Otherwise, look in "dmesg" to see what happens.

```
dmesg | more
(hit the space bar for the next 24 lines...)
```

There's only one CD-Rom option in BIOS, and then there's a USB CD option as well . . .but the drive isn't USB connected.

---

### Post by taurus on 2007-01-13
Well, you may have to open the case and look at the jumpers on the back.  The first CD drive should be a master, connecting to the end of the cable, while the second one should jump as a slave, connecting to the middle cable.

---

