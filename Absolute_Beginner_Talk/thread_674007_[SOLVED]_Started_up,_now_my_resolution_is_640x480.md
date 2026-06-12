---
title: "[SOLVED] Started up, now my resolution is 640x480"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by penguinbreath on 2008-01-21
My computer was working fine yesterday, and all the sudden this morning my resolution is at 640x480. It wont let me set it higher. 

Whats going on?


I am running Kubuntu 7.04.

---

### Post by markyb86 on 2008-01-21
what graphics card and what driver are you using?

---

### Post by penguinbreath on 2008-01-21
I am using a system someone gave me.

It is using  an nvidia 128mb series 4000 or something. I checked and restricted drivers seems to be enabled, but in the kubuntu system settings it says the driver is "generic".

---

### Post by penguinbreath on 2008-01-21
This is a screenshot:


[[IMG]http://img301.imageshack.us/img301/7002/imagesoftware3ek2.th.png[/IMG]](http://img301.imageshack.us/my.php?image=imagesoftware3ek2.png)

---

### Post by markyb86 on 2008-01-21
ok try the following and see if this helps

```
kdesu nvidia-settings
```

see if you can detect your monitor and set your resolution there. It is using the nvidia driver.

---

### Post by penguinbreath on 2008-01-21
I reconfigured Xorg and the problem is gone. 

I still wonder why it did what it did. At least now its working.


Thanks for the support and input.

---

### Post by bobdebouwer on 2008-01-21
It could be that the drivers have just corrupted themselves and you are now in low resolution mode.

Try installing envy

sudo apt-get install envy

You then have the option to re/install nvidia/geforce drivers.

David

LOL ok too late

---

