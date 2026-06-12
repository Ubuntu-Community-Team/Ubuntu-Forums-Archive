---
title: "Not Registering DV Camera"
date: 2007-10-13
forum: Art &amp; Design
---

### Post by burning_man13 on 2007-10-13
It isn't saying that my camera is mounted, the camera isn't even registering when I put my Canon GL2 in through the USB or through Firewire... Everything else registers through USB... What drivers would be needed or what can I do to make it register so I can Edit the media that I have???

---

### Post by kayosiii on 2007-10-15
connect the camera via firewire...
install and use the app "gscanbus" to check out if you can detect your camera when it is plugged in.
If it does not show up - try running it using sudo....

type into a terminal 

sudo gscanbus

let me know if your camera is picked up by this command or not.

---

### Post by burning_man13 on 2007-10-15
I have gscanbus installed... and it's still not registering... What could possibly be the next step??? You see... I have a Firewire card... and I'm not even 100% sure that that's even registering... I don't really have another Firewire device to use... So checking to see if that works is a little out of the question...

---

### Post by Hallis on 2007-11-02
same thing happends with me.. i also have a canon gl2:), but it does not respand, i have tried my other camera to,, but same thing happends,, help anyone?

---

### Post by jackal_twister on 2009-02-20
I am using Intrepid ibex (ubuntu 8.10) and am having problems trying to set this up

I have loaded the raw1394 libraries. when i plug in the dv cam into the firewire slot and turn it on, I tried to chmod the rights for /dev/raw1394 but this file doesnt exist (niether does dv1394)

this problem is now officially annoying me can someone please post a cohesive response.


here is my results from lsmod | grep 1394

pouyan@pouyan-ubuntu-g1s:/$ lsmod | grep 1394
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394

as you can see i have the correct libraries loaded (or maybe I dont)
please help

---

### Post by Meow27 on 2010-05-27
i have the same problem 
canon gl2
ubuntu lucid 10.04

HALP!

---

