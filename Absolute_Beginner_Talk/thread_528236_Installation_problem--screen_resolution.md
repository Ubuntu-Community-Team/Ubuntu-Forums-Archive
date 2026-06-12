---
title: "Installation problem--screen resolution"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by telegramsam on 2007-08-17
Hi;
I'm trying to install 7.04 on a machine I built with an nVidia GeForce 6100 onboard video chipset.

During the Live CD Installation, I am unable to see the bottom of the UI boxes to advance.  I got as far as the region, but can't go any further.  I am at the maximum screen resolution in System > Preferences.  

Any ideas?

---

### Post by Hobo Joe on 2007-08-17
Move the window above the top of the screen by holding alt and pressing and dragging any part of the window.

---

### Post by Amazona aestiva on 2007-08-17
After install(if you still have the problem)
Type:
```
sudo nvidia-settings
```

---

### Post by Hobo Joe on 2007-08-17
He/she would have to install the drivers before that.

But, speaking of, you NEED to use Envy for installing drivers. Trust me.

Check my sig for a link.

---

### Post by telegramsam on 2007-08-17
> **Hobo Joe said:**
> Move the window above the top of the screen by holding alt and pressing and dragging any part of the window.


Hey--thanks for the reply--

I already moved the window to the top of the screen (it's a 17" monitor), and I still cannot see the bottom of the dialog box.  

I've managed to guess all the Alt codes up to the very last screen after the partition editor.  I'm still working on that one...

---

### Post by Hobo Joe on 2007-08-17
No, I mean when you hold down ALT, you can grab any part of the window to drag it.

In other words, you can grab the middle of the window and pull it beyond the top of the screen.

---

### Post by jdfreshwater on 2007-08-17
sorry wrong info...my bad

---

### Post by logos34 on 2007-08-17
> **telegramsam said:**
> Hey--thanks for the reply--

I already moved the window to the top of the screen (it's a 17" monitor), and I still cannot see the bottom of the dialog box.  

I've managed to guess all the Alt codes up to the very last screen after the partition editor.  I'm still working on that one...

I have the same problem using my nvidia geforce 6100...it's trying to use the 'nv' driver...

There's an easy fix: you need to change that to 'vesa'.  So if you'd like to be able to see what you're doing during install rather than guessing, abort and open a terminal:

sudo dpkg-reconfigure xserver-xorg

Select 'vesa' driver.

You can just accept defaults on pretty much all the rest.  Do not write to configuration file.

Then restart desktop:

ctrl+alt+backspace

Menu>System>Prefs>screen resolution>change to 1024X768 (~75hz)

---

### Post by EXCiD3 on 2007-08-17
There is always the option of installing using the Alternate CD which just uses a terminal-like interface. It also includes lots of extra options not included on the Live CD.

---

### Post by telegramsam on 2007-08-17
> **Hobo Joe said:**
> No, I mean when you hold down ALT, you can grab any part of the window to drag it.

In other words, you can grab the middle of the window and pull it beyond the top of the screen.


Oh, guess I could read a little closer...

I did manage to make it through it by guessing the ALT commands

Mainly Alt + F until the last box, where you tab four times and enter, in case anyone runs into this again...

Thank you very much for your help, now on to driver installation!

---

### Post by telegramsam on 2007-08-17
> **Hobo Joe said:**
> He/she would have to install the drivers before that.

But, speaking of, you NEED to use Envy for installing drivers. Trust me.

Check my sig for a link.

Thanks for the Envy tip--worked perfectly, with no brain work on my part!  Appreciate your help!

---

