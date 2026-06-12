---
title: "No HAL!"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by notjohn101 on 2007-11-08
ok so i installed gusty gibbbon after wiping fawn (mainly cuz i think upgrading makes everything buggy) so i customize it to the way i like it and install the updates....i restart it and get this (attached) when i boot....i put the dmesg in as well if thatll help diagnose

[IMG]http://i17.tinypic.com/832bvhf.png[/IMG]

---

### Post by Eddie Wilson on 2007-11-08
> **notjohn101 said:**
> ok so i installed gusty gibbbon after wiping fawn (mainly cuz i think upgrading makes everything buggy) so i customize it to the way i like it and install the updates....i restart it and get this (attached) when i boot....i put the dmesg in as well if thatll help diagnose

[IMG]http://i17.tinypic.com/832bvhf.png[/IMG]

For some reason I couldn't see your attachment.
Eddie

---

### Post by notjohn101 on 2007-11-08
bump

---

### Post by Conquestor1 on 2007-11-08
If you have a Windows 98 Start-Up Floppy. Boot from the floppy. At the command prompt type "LOCK C:", hit Enter. Then type "FDISK C:" hit Enter. This will delete your master boot record. Try installing Gutsy again.

---

### Post by Eddie Wilson on 2007-11-08
Sorry, still can't see the attachment.
Eddie

---

### Post by notjohn101 on 2007-11-08
ok sounds good but before i do that....i need to no ill itll ruin windows in anyway especilly cuz C; is my docs hard drive

here the link to the picture for those who cannot see it [pic]("http://i17.tinypic.com/832bvhf.png")

---

### Post by Bruce M. on 2007-11-08
> **Eddie Wilson said:**
> Sorry, still can't see the attachment.
Eddie

Two positives that make a negative:   Yea, Right!
You forgot to turn your monitor on and your voice package read the message!
hahahahahahaha

wait a sec:  BUMP

---

### Post by notjohn101 on 2007-11-08
bump

---

### Post by skymera on 2007-11-08
i had this,.

do you use concurrent booting?

---

### Post by notjohn101 on 2007-11-08
yea.....should i turn it off?

---

### Post by skymera on 2007-11-08
nope,

ok

```
 sudo nautilus 
```

navigate to folder /etc/rc2.d

rename hal12 to hal13

tthis will make HAL load AFTER! DBUS
thus making no error, try that now

---

### Post by notjohn101 on 2007-11-08
ok, done rebooting to test now

---

### Post by Therion on 2007-11-08
If your /etc/init.d/rc file shows: 

CONCURRENCY=shell

You want to change it to: 

CONCURRENCY=none

Fixed that same error for me.

---

### Post by skymera on 2007-11-08
he shouldnt have to disable, i havent had to.

lets see what the result from my suggestion is :wink:

---

### Post by notjohn101 on 2007-11-08
haha ohhh some competition? WELL?!? skymera wins his tricked work but thanks to all of u who suggested tricks

Therion, you should do what he said so u can have a concurrent boot

---

### Post by skymera on 2007-11-08
o yes, 10 points :)

glad its alll goood :D

---

### Post by Therion on 2007-11-08
> **notjohn101 said:**
> 
Therion, you should do what he said so u can have a concurrent boot

I intend to!  I was bummed concurrent booting killed HAL.  Nice fix; I look forward to trying this out.  

Do you reeeally see a difference using concurrent booting?

---

### Post by skymera on 2007-11-08
ha...ermm

no :P

---

### Post by Therion on 2007-11-08
> **skymera said:**
> ha...ermm

no :P

:lolflag:

Yeah... uh... me neither.  Just thought I'd ask.

---

### Post by Belerophon on 2008-01-18
> **skymera said:**
> nope,

ok

```
 sudo nautilus 
```

navigate to folder /etc/rc2.d

rename hal12 to hal13

tthis will make HAL load AFTER! DBUS
thus making no error, try that now


What is HAL?
One starting after the other doesnt matter???

I had the same problem...that fixed it! Thanks a lot!!!

By the way, i notice diference using concurrent booting :D!

---

