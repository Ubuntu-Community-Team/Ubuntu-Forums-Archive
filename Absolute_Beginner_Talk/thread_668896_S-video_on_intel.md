---
title: "S-video on intel"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by OrionFyre on 2008-01-15
On my laptop I'm following some posts here about enabling s-video. I have a movie I want to play for my mother.

I can't even BEGIN to follow the posts that exist because when I do 'xrandr' I get a bad request error!?!

COMPLETE NEWB here.

when I run xrandr i get
```
orionfyre@orionfyre-laptop:~$ xrandr
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  6 ()
  Serial number of failed request:  9
  Current serial number in output stream:  9

```

---

### Post by veloce on 2008-01-16
By any chance did you upgrade from Feisty to Gutsy?

If so then you need to remove the package "xserver-xgl" either with Synaptic or the command:

sudo apt-get remove xserver-xgl

---

### Post by OrionFyre on 2008-01-19
no, fresh install from 7.10

---

### Post by motin on 2008-01-26
Just around a week ago, there was a temporary glitch in the display system caused by a security update. It should be resolved now - how does it work if you update to the latest packages and try again?

---

### Post by OrionFyre on 2008-01-26
I can get it working only be restarting X or booting the laptop with the s-video connection plugged into the tv.

I can find no information on how to enable it "live" so to speak.

Then to resume my display back to normal resolution (since it's a widescreen display) I once again have to restart X or reboot the computer. 

I find this is doable, but rather unnaceptable because i have to close everything just to do this.

---

