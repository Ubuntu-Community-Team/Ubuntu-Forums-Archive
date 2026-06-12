---
title: "GeForce FX 5200 Problems"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Crafty Kisses on 2007-10-14
Well my Nvidia GeForce 6800 GT, was not working so I switched cards, and the card I switched to was a GeForce FX 5200, when I plugged it in, It says "Please Check Signal Cable" nothing else, any ideas?

---

### Post by maduranga on 2007-10-14
then it means the card don't send signals to the display. I have the same graphic card. I try different distros when they available, for my pleasure. but i never had any problem with dis  graphic card. it maybe a hardware fault

---

### Post by mendingo84 on 2007-10-14
same card here, no problem! ( a little slow with Compiz-Fusion though but hey...it's an old card :) ). make sure you connected the cable properly. or maybe the hardware is borken

---

### Post by PmDematagoda on 2007-10-14
> **Codename said:**
> Well my Nvidia GeForce 6800 GT, was not working so I switched cards, and the card I switched to was a GeForce FX 5200, when I plugged it in, It says "Please Check Signal Cable" nothing else, any ideas?

Why doesn't the Nvidia 6800GT work?

---

### Post by maduranga on 2007-10-14
> **PmDematagoda said:**
> Why doesn't the Nvidia 6800GT work?

ye it should work also.. hey frnd... its u.. :) dis is a small wrold.. :):)

---

### Post by PmDematagoda on 2007-10-14
> **maduranga said:**
> ye it should work also.. hey frnd... its u.. :) dis is a small wrold.. :):)

Well, this is a small country we are living in:).

---

### Post by Crafty Kisses on 2007-10-14
I have some screenshots if you want them, to show you why it wont work.

---

### Post by PmDematagoda on 2007-10-14
Ok, post them.

---

### Post by Crafty Kisses on 2007-10-14
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-9.png[/IMG]
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-1-4.png[/IMG]
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-8.png[/IMG]

---

### Post by Perfect Storm on 2007-10-14
After switching card, did you ran the ** sudo dpkg-reconfigure -phigh xserver-xorg**

---

### Post by Orbital75 on 2007-10-14
Interesting, I'm running the same Card but in a Virtual Machine.
This makes me think twice about going Native.

---

### Post by Crafty Kisses on 2007-10-14
> **Artificial Intelligence said:**
> After switching card, did you ran the ** sudo dpkg-reconfigure -phigh xserver-xorg**

It said "Signal Cable Not Found" so I couldn't even get to a black screen, so I switched back to the 6800.

---

### Post by Perfect Storm on 2007-10-14
Have you the option to test the card on another PC to check if it's broken.

---

### Post by PmDematagoda on 2007-10-14
Did you try the usual stuff for the nvidia card such as "sudo dpkg-reconfigure xserver-xorg"?

---

### Post by Crafty Kisses on 2007-10-14
> **Artificial Intelligence said:**
> Have you the option to test the card on another PC to check if it's broken.

Yes, and it was working, also the below question, It was at a "Please Check Signal" cable screen I couldn't do anything.

---

### Post by PmDematagoda on 2007-10-14
> **Codename said:**
> Yes, and it was working, also the below question, It was at a "Please Check Signal" cable screen I couldn't do anything.

No, not about the new VGA card, your old 6800 one.

---

### Post by Crafty Kisses on 2007-10-14
> **PmDematagoda said:**
> No, not about the new VGA card, your old 6800 one.

The old VGA one was doing it. The 6800 one works fine if I just plug it in, it's when I install the drivers when it gets messed up.

---

### Post by PmDematagoda on 2007-10-14
Now, when you use the 6800 card, is the wallpaper part the only part of the desktop that malfunctions?

---

### Post by Crafty Kisses on 2007-10-14
> **PmDematagoda said:**
> Now, when you use the 6800 card, is the wallpaper part the only part of the desktop that malfunctions?

Nope, the applications tab and everything, I've been dealing without no drivers for about 8 months now, it kinda sucks. :(

---

### Post by Crafty Kisses on 2007-10-14
Bump.

---

### Post by PmDematagoda on 2007-10-16
Did you check your VGA on another computer as suggested by Artificial Intelligence?

---

### Post by Joeb454 on 2007-10-16
If you read he did check, and for now I'd uninstall the drivers, so you can continue to use the comp.

Which drivers did you install?

---

### Post by drinkpepsi on 2007-10-16
When the 6800 is plugged in try changing to another resolution. I had similar lines on my screen, and when I changed the resolution they went away. You can also download this,

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu12_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu12_all.deb)

Select the option to install the nvidia driver automatically.

---

