---
title: "Wacom Bamboo Pen &amp; Touch - Ubuntu 12.04"
date: 2012-06-28
forum: Art &amp; Design
---

### Post by snowz on 2012-06-28
I'm getting my new **Bamboo Pen & Touch** third generation tablet today.
It will be my first tablet to try out on **Ubuntu**.
[IMG]http://www.cancomuk.com/images/products/9f/8271077/163917/large.jpg[/IMG]
Does it work perfectly on **Ubuntu 12.04** or are there any complications?

---

### Post by snowz on 2012-06-28
Here is the 1st image I've drawn ;)

[http://ubuntuone.com/3hD09ARFeoOFM7weYyMUis](http://ubuntuone.com/3hD09ARFeoOFM7weYyMUis)

Pretty good for the first one right? :D

---

### Post by BcRich on 2012-06-29
Hi snowz 
Does the "touch" feature also work, including multi-touch (like zooming in and out of a webpage using pinch and spread gestures, and flicking to scroll a webpage). Are there any special settings you had to do in order to get the pen working?
congrats on your first image :)

---

### Post by snowz on 2012-06-29
The touch is working yeah. Scrolling works just fine, but I had difficulties with the zooming. It works but I'm not used to it and did some pretty weird zooming :P

There is this interesting thing. As it is a PEN and TOUCH tablet you have the option to disable TOUCH when you want so. For example, if you want to draw it might bother you because you would be clicking something all the time. 

To disable the TOUCH function on your tablet you have to:


[LIST]
[*][SIZE=3]Open the **Terminal**[/SIZE]
[*][SIZE=3]Type: **xsetwacom --list**[/SIZE]
[*][SIZE=3]**You will see many ID's like this:**[/SIZE]
[/LIST]
[IMG]http://ubuntuone.com/5nt3FOs2jT2ujSiKVvMnjy[/IMG]


See the second [COLOR=DarkOrange]ID[/COLOR] for FINGER TOUCH: Mine is **12** in this case


[COLOR=DarkOrange]**Your IDs might be different**[/COLOR]


Now to disable TOUCH:

[LIST]
[*]Type: **xsetwacom** **set** [COLOR=DarkOrange]YOUR_ID_HERE[/COLOR] **touch** **off**
[/LIST]
To enable it back type the same thing and put **on** at the end


Like that you can disable the eraser, pen and so on...


Pretty simple but it works ;)

---

### Post by argument on 2012-07-03
I just hooked it up, but for me touch is not working out-of-the-box with Kubuntu 12.04

---

