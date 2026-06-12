---
title: "Headphones hell!"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by sammi.jo on 2008-03-31
Hi, I'm an absolute newbie, so please pardon my idiocy!

I have ubuntu 7.10 and my sound from my laptop speakers work without a single problem! It only starts when I plug in my headphones.

It doesn't seem to recognise them! I've tried going into my sound properties, and there's no option for headphones or surround, when I've enabled all of the checkboxes.

I've tried updating all of the Alsa drivers, but it doesn't seem to be doing anything. Nothing is muted; I've already checked that one!

I don't know how to find my chipset or anything, and it's not a specific laptop; it's a custom built laptop from my LEA, and it originally had Vista on. 

Contacting the LEA came to nothing, so I've installed Ubuntu after a massive Vista failure, but all of them worked OK on Vista.

Please help? x

---

### Post by original_jamingrit on 2008-03-31
Is this a USB headset (??) or just normal headphones you'd plug into a headphone jack?

Also, what did you use to check your volume settings?  If you haven't already, open up a terminal and check them with the command
```
alsamixer
```

---

### Post by sammi.jo on 2008-03-31
I used alsamixer, and nothing was muted. I went though all of them and sent them through the cycle MM-M just in case it needed a poke.

Nothing happened.

And it's a bog-standard in-the-green-slot headphones.

---

### Post by stchman on 2008-03-31
> **sammi.jo said:**
> Hi, I'm an absolute newbie, so please pardon my idiocy!

I have ubuntu 7.10 and my sound from my laptop speakers work without a single problem! It only starts when I plug in my headphones.

It doesn't seem to recognise them! I've tried going into my sound properties, and there's no option for headphones or surround, when I've enabled all of the checkboxes.

I've tried updating all of the Alsa drivers, but it doesn't seem to be doing anything. Nothing is muted; I've already checked that one!

I don't know how to find my chipset or anything, and it's not a specific laptop; it's a custom built laptop from my LEA, and it originally had Vista on. 

Contacting the LEA came to nothing, so I've installed Ubuntu after a massive Vista failure, but all of them worked OK on Vista.

Please help? x

What happens when you plug the headphones in?

My Toshiba laptop did not mut ethe laptop speakers when I plugged in the headphones.

I fixed it with this:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

---

### Post by sammi.jo on 2008-03-31
The sound goes off the main speakers (internal laptop ones) but nothing comes out of the headphones.

Also, the output on lspci is 

04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10).

Oh, and if it helps:

**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by sammi.jo on 2008-03-31
Bump?

---

### Post by stchman on 2008-03-31
Have you checked in the gnome-volue-control if there is a headphone switch.  If there is check the box.

---

### Post by sammi.jo on 2008-03-31
That's the problem; there IS no headphone switch

---

### Post by stchman on 2008-03-31
Try updating to the latest ALSA.  I have a tutorial on it with an automated script.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

---

### Post by kamitsukai on 2008-03-31
> **sammi.jo said:**
> 
I've tried updating all of the Alsa drivers, but it doesn't seem to be doing anything.

He already has updated it appears:lolflag:

---

### Post by sammi.jo on 2008-03-31
> **stchman said:**
> Try updating to the latest ALSA.  I have a tutorial on it with an automated script.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

I have the latest ALSA drivers, apparently, but it still shows no option. I'm getting stressed here; I need these drivers before I can get streaming software,

---

### Post by sammi.jo on 2008-03-31
Does nobody know, or has nobody had this problem? The headphone jack worked OK in Windoze, funnily enough. All the solutions on the net seem to sway towards Intel, as opposed to VIA

---

