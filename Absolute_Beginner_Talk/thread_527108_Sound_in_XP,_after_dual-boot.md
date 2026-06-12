---
title: "Sound in XP, after dual-boot"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by parrisjoeyey on 2007-08-16
So I reformatted, started again, installed XP, then Ubuntu, all went smoothly, 

Ubuntu works great, 
XP unfortunatly didnt pick up sound device, in my device manager it doesnt have a sound device, funny how Ubuntu picks it up, but Windows doesnt, just proves how good Ubuntu is, 
So now I need to put sound on XP ? any ideas anyone ?
Even if you tell me how to get my motherboards name would be great, without opening my notebook.

---

### Post by RaZer0r on 2007-08-16
if you have some onboard sound device, you might need some drivers, check the website of the manufacturer :) They should have drivers for you ;)

---

### Post by xpod on 2007-08-16
```
lshw
```

That in a terminal will list all your hardware for you in Ubuntu.

In Windows i always used a program called "everest" for listing all a computers hardware,drivers and the respective sites from which to get them from.

---

### Post by Steve1961 on 2007-08-16
First things first, go into device manager, right click the device which isn't recognised (a little yellow question mark) and select update driver to see if there's a copy of the driver on the windows update site.

Failing that - and it often fails - download siw from [http://www.gtopala.com/siw-download.html](http://www.gtopala.com/siw-download.html)

Get the multilanguage version as it seems to work better,  Save it to your desktop and then double-click to run it.  You should be able to get all teh hardware info you need from this.

---

### Post by oilchangeguy on 2007-08-16
> **parrisjoeyey said:**
> So I reformatted, started again, installed XP, then Ubuntu, all went smoothly, 

Ubuntu works great, 
XP unfortunatly didnt pick up sound device, in my device manager it doesnt have a sound device, funny how Ubuntu picks it up, but Windows doesnt, just proves how good Ubuntu is, 
So now I need to put sound on XP ? any ideas anyone ?
Even if you tell me how to get my motherboards name would be great, without opening my notebook.

if you're running a legal copy of windows. go to microsofts website, and allow the computer to do updates. select custom, so you can view and select updates other than just critical ones. also from the device manager, right click the item, and delete it. then reboot into windows, and see if the driver will load.

---

