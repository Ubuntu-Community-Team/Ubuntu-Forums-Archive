---
title: "Karmic on 5.4 Blank screen after upgrade"
date: 2010-03-23
forum: Apple Hardware Users
---

### Post by demwz on 2010-03-23
Hi,

im running karmic on a macbook pro 5.4. everything worked fine for a couple of months until i upgraded yesterday. (apt-get upgrade)

now i'm getting a blank (black) screen when booting right after the splash screen appears tough the system comes up propperly since i can connet using ssh. the xserver is up and running regarding to the logs. i can't even switch to a console (alt-crtl-f1) nor booting in single user mode. the screen gets black after the kernel boot and init starts. 

any ideas ?

---

### Post by demwz on 2010-03-23
echo 100 > /sys/devices/virtual/backlight/nvidia_backlight/brightness

fixed it

I dont know why ACTUAL_BRIGHTNESS IST SET To "0" 

any ideas ?

---

### Post by xvila on 2010-03-23
I'm having the same issue
My guess is that it's related to the latest nvidia-bl-dkms update, but I'm not sure
Waiting for the next upgrade

---

### Post by _mario_ on 2010-03-24
Hi,

which version are you using? afaik, version 0.16.5 always sets brightness to maximum (or at least what the driver thinks is maximum) upon load, totally ignoring the present setting.

ciao,
Mario

---

### Post by xvila on 2010-03-24
> **_mario_ said:**
> Hi,

which version are you using? afaik, version 0.16.5 always sets brightness to maximum (or at least what the driver thinks is maximum) upon load, totally ignoring the present setting.



I was using 0.16.4.
Now I just upgraded (sudo apt-get update; sudo apt-get dist-upgrade) to 0.16.5 and it works fine. Brightness is set to maximum indeed.

xavi

---

### Post by demwz on 2010-03-25
ok -it was solved by the lates update of nvidia_bl driver.

thx

---

