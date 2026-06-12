---
title: "Touchpad horizontal scrolling goes 'back' and 'forth' in firefox"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-02-18
I was trying to view a very large image in firefox, I used my touchpad to try and scroll horizontally, but instead of scrolling the image, I was sent back and forth seeing the pages I had viewed in that session.

Anyone else experience this?

(To simplify, if I scroll to the left on my touchpad it is as if I pressed the back button in firefox)

---

### Post by solar george on 2007-02-18
Open a new tab in firefox and type "about:config".

Type scroll into the search bar,

All that I can say is that you'll have to experiment with these options (My mouse doesn't do horizontal scrolling).

It may be best to create a new profile in order to experiment.

---

### Post by zorkerz on 2007-03-26
PartisanEntity did you ever solve this for yourself.  Im experiencing the same problem and was wondering if you found a solution. None of the options in about:config were clearly appropriate so i have held off on messing with the numbers yet. Please post your solution if any.

---

### Post by zorkerz on 2007-03-26
Problem solved thanks to the gentoo wiki. [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Horizontal_Scroll_Issues_with_Firefox](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Horizontal_Scroll_Issues_with_Firefox)

in firefox's about:config set "mousewheel.horizscroll.withnokey.action" to 0 and "mousewheel.horizscroll.withnokey.sysnumlines" to true. This allows normal horizontal scrolling and prevents forward back movement between pages.

---

### Post by PartisanEntity on 2007-03-26
Hi, thanks for the input, I reinstalled Ubuntu since posting this thread and have not set up my touchpad yet. But thanks again for the info.

---

### Post by zielak on 2007-04-24
Thnx a LOT zorkerz - works like a charm :D

---

### Post by p1977p on 2007-06-12
> **PartisanEntity said:**
> Hi, thanks for the input, I reinstalled Ubuntu since posting this thread and have not set up my touchpad yet. But thanks again for the info.
thanks a lot. the wiki post is awesome.

---

