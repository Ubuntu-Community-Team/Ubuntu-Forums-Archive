---
title: "webcam help needed"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by harry rao on 2008-03-15
hp  pavilion dv9000 series notebook with inbuilt webcam,

i have no idea how to get it setup - i tried 'camorama' and that failed miserably.

what am i supposed to do?

---

### Post by Pumalite on 2008-03-15
I have this collection of links related to dv9000. Maybe you'll find something useful:

[http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by pandu.rs on 2008-03-15
If you are using ubuntu 7.10, just install cheese using synaptic (available in universe repo)

[http://www.gnome.org/projects/cheese/](http://www.gnome.org/projects/cheese/)

---

### Post by ghost_ryder35 on 2008-03-15
+1 for Cheese

---

### Post by harry rao on 2008-03-15
i loaded cheese through synaptic but it's unable to detect the built in cam - is there some sort of script that i require to get cheese to detect the cam?

---

### Post by linuxwizard on 2008-03-16
harry rao
Have you installed any drivers for your cam ? If not post results of the command > lsusb

---

### Post by harry rao on 2008-03-16
it didn't come with any drivers,
it's not a usb device either -it's an inbuilt cam on a laptop...
i'm using ubuntu 7.10 and when i try the command advised, the reply is "command not found"..

---

### Post by DarinB on 2008-03-16
after reading this post i would say follow what pumalite recommends.
Pumalite is brilliant and has helped me very often.
all the rest just give possiblities.
sometimes ubuntu is about reading and learning not jsut quick easy fixes
good luck

---

### Post by harry rao on 2008-03-16
well thanks, i think i'll try n figure this one out on my own...
i don't quite understand why i have to change to feisty according to one of pumalite's links.

---

### Post by martyssweb07 on 2008-04-28
Hey All,

I was wondering if anyone has the webcam working in hardy yet on the HP dv9000?  I had it working great with cheese in gutsy, but with the kernel updates it killed my driver.  Here's the lsusb

Bus 005 Device 003: ID 05ca:1870 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Thanks for the help

---

### Post by Agapo on 2008-05-01
I have the same issue I got everything to work minus the webcam
I have a dv9000 running hardy 64bit

Bus 002 Device 003: ID 045e:0023 Microsoft Corp. Trackball Optical
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05ca:1870 Ricoh Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
thank you

---

### Post by charlemagne86 on 2008-05-23
HEY EVERYONE

for all those people who have got their webcams working on ekiga but after a sec or so they begin showing distortions with funny black/red/pink/green colors.....i found a sollution:

when you start ekiga webcam, when this distortion happens....just clik on the brightness slider in the video tab (even the minutest adjustment will do) and the distortions are all gone...even after you restart ekiga again....However you have to do this after each reboot.

---

