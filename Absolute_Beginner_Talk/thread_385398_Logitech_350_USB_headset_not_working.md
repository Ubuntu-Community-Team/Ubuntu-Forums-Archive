---
title: "Logitech 350 USB headset not working"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Netspeed on 2007-03-15
Here's what aplay -l lists. It looks like the system knows it's there. Alsamixer has the levels up and no mutes but yet there is still no sound. Anything else to check?



**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by rockstar on 2007-04-04
[http://www.linuxforums.org/forum/suse-linux-help/63903-logitech-usb-headset-not-working.html](http://www.linuxforums.org/forum/suse-linux-help/63903-logitech-usb-headset-not-working.html)

---

### Post by panth0r on 2007-10-16
I'm still not able to get my headset to work, currently using 7.04 Ubuntu.

---

### Post by Netspeed on 2007-10-16
I threw mine in the trash....piece of junk. I used the headset for my voip phone and after having many people not be able to hear me, I took it apart. The wires from the headset to the circuit board were breaking off the from the solder. I went out and got a Plantronics M214i. Cheaper and it works great! It even has an inline adjustment for headphone volume and mic gain.

---

### Post by rustybronco on 2007-10-16
[http://ubuntuforums.org/showthread.php?t=509598](http://ubuntuforums.org/showthread.php?t=509598)

---

### Post by phuck_windows on 2007-12-30
I'm sure by now many of you have probably fixed this problem.  Others however may be having the same problem.  For me, my problem was that it worked fine in Skype but nothing else (movies, music, webpages, etc.).  What I did to fix this problem was open my symantic package manager and search for the "asoundconf-gtk" package.  After you install it, under system, prefences you should have "default sound card".  When I want to use my usb headset I first plug it in, click system, prefences, and default sound card.  From there just select headset and click close.  That should solve your problem.  Hope that works as good for you as it did for me.  If not I'm sorry as I am a newb at Ubuntu.  I am using Gutsy Gibbon 7.10.

---

