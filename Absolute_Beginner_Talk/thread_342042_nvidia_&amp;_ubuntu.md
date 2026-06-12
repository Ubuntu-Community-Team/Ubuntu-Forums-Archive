---
title: "nvidia &amp; ubuntu"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2007-01-19
how can i get this card to work like in windows or close to it???

---

### Post by taurus on 2007-01-19
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by mand0 on 2007-01-19
> **antgul3382 said:**
> how can i get this card to work like in windows or close to it???

Are you talking about gaming performance?  That is just not possible right now.  But anyways, just install the drivers like taurus said.

---

### Post by edwardLS on 2007-01-19
Not exactly sure what you problem is from the description; however, in some ways I had a similar problem.  See: [http://www.ubuntuforums.org/showthread.php?t=340630](http://www.ubuntuforums.org/showthread.php?t=340630) for some detail.  I don't pretend to know all the details of my success, but it is working now.

---

### Post by antgul3382 on 2007-01-19
i have two monitors and with windows  i would have a normal desktop on monitor 1 and just the desktop with no menus on the other and it was like on big one i drag a window off trhe screen and it would got to the next is ....there a way??? when i started the monitor was al snowy and wird lookin and after the above driver install it doesnt even light up its sleeping

---

### Post by igknighted on 2007-01-19
browse the stickies in the multimedia forum... you have several options (Twinview and Xinerama), each with their own benefits.  Read whats there and there are easy instructions for both.

---

### Post by bodhi.zazen on 2007-01-19
> **antgul3382 said:**
> i have two monitors and with windows  i would have a normal desktop on monitor 1 and just the desktop with no menus on the other and it was like on big one i drag a window off trhe screen and it would got to the next is ....there a way??? when i started the monitor was al snowy and wird lookin and after the above driver install it doesnt even light up its sleeping

Install the beta drivers **as advised from taurus**

Open a terminal

```
nvidia-settings
```

Add configured via nvidia settings gui.

You want the twinview option :)

---

### Post by antgul3382 on 2007-01-19
this is what i get when i put that code in

there no "view" options

---

### Post by bodhi.zazen on 2007-01-19
That's it,

Except you need the beta driver :p

---

### Post by antgul3382 on 2007-01-19
I Told You I Did And It Didnt Do A Dan Thing But Turn The 2nd Monitor Off](*,)

---

### Post by taurus on 2007-01-19
> **antgul3382 said:**
> I Told You I Did And It Didnt Do A Dan Thing But Turn The 2nd Monitor Off](*,)

Easy there, now.

---

### Post by bodhi.zazen on 2007-01-19
> **antgul3382 said:**
> I Told You I Did And It Didnt Do A Dan Thing But Turn The 2nd Monitor Off](*,)

LOL

You have nvidia 1.0-8776

You need the beta driver, nvidia 1.0-9631

The beta driver has been stable for me and has a option
"X Server Display Configuration" in the menu on the Left you simply do not have :(

Link: [http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

Oh, and look 1.0-9746 is out :p

If that fails, can you post the monitor sections for you monitors from /etc/X11/xorg.cong :p

They should look something like this:

> Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "DEL"
    ModelName      "DELL P1110"
    HorizSync       29.0 - 121.0
    VertRefresh     50.0 - 180.0
    Option         "UseEdidFreqs" "1"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "IBM"
    ModelName      "IBM P202"
    HorizSync       30.0 - 107.0
    VertRefresh     50.0 - 160.0
    Option         "UseEdidFreqs" "1"
    Option         "DPMS"
EndSection

---

