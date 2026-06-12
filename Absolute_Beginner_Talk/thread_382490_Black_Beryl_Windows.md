---
title: "Black Beryl Windows"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by abstracthumor on 2007-03-12
I've done a fresh install of Edgy today, gotten Nvidia, Beryl, and Emerald working.  However, I'm running into a problem I was having before my fresh install.  When a certain number of windows become opened, any attempts to open a new window comes up with the Emerald border with a black interior.  Occasionally this can be solved by reloading the window manager, or even by simply minimizing the window in question.  However, this only happens on occasion.  Suggestions would be much appreciated.

---

### Post by siciliancasanova on 2007-03-12
How indepth have you gone into the Beryl manager?  I had a few display glitches on mine and after messing around with a few different settings I got it all cleaned up.

---

### Post by abstracthumor on 2007-03-12
I suppose I could peek around, but it's just so arbitrary.  Do you have something in mind?

---

### Post by siciliancasanova on 2007-03-12
Well your situation is very vague.  Unless there is someone else here who has experienced the exact same problem I think it's going to be difficult to pinpoint right off the bat what it is that's causing that problem.  

Since everything updates 'live' when you change settings I was just thinking maybe 20-30 minutes in the beryl manager may save you hours of discussion in the forums to figure this out, however arbitrary it may seem.

---

### Post by abstracthumor on 2007-03-12
I'm looking at the beryl forums, it's actually called the black window bug... apparently it's been "plaguing" people with nvidia.  As of yet, I've not found a cure.

---

### Post by NikoC on 2007-03-12
It is a confirmed bug in nvidia drivers: after a certain number of windows have opened, the graphics card runs out of memory! Perhaps you can try:

Beryl manager > Advanced beryl options > rendering path > copy

---

### Post by CyBuzz on 2007-03-13
I too am experiencing this issue.  Man I love these forums.  Everything I find, has been found and  either identified as a bug or fixed.

I have this problem when I have multiple tabs in multiple Firefox windows open....and when I have a bunch of window open and try and run Google Earth.

I have a Nvidia 5600 with 128MB.  Not a great card but not too shabby.  Actually I am impressed with what Beryl can do with it.  It is no 8800 GTX, but it will do.

I will dig around and see if I can consistently reproduce this issue and see if I can find a workaround.

---

### Post by Lexyboy on 2007-03-13
Yes, this is apparently a well known bug with the nvidia drivers.  A workaround that works for me is to change 'Rendering Options' (in beryl-manager menu) to 'Force AIGLX".  No more black windows, although it's a bit slower (mouse drags a bit when computer's busy).  

Hopefully the nvidia drivers will be fixed soon...  I'm not even sure it's a graphics card thing, I was getting black windows with only 3-4 windows open sometimes, with a 256Mb card!

---

### Post by leohart on 2007-03-14
Just to chip in some more thoughts on this "black window syndrome". It actually happens on a lot of nvidia cards (and mostly on nVidia beta drivers). I really hope that nVidia will fix this issue soon enough.

My beryl also has this problem, until I change Advanced Settings to Force AIGLX.

---

### Post by Pronker on 2007-03-20
> **leohart said:**
> Just to chip in some more thoughts on this "black window syndrome". It actually happens on a lot of nvidia cards (and mostly on nVidia beta drivers). I really hope that nVidia will fix this issue soon enough.

My beryl also has this problem, until I change Advanced Settings to Force AIGLX.

Yup, it's confirmed... same bug here on an nVidia Go 5200 64Mb (who was whining about bad graphics?? :p)
Well anyway I fixed it by forcing aiglx too... Weird thing is, after forcing aiglx, my cube wound up having 16 faces?? anyway it works fine now...

---

### Post by nardusg on 2007-03-20
Force AIGLX fixed it for me :)

Same issue 

Card: nVidia Corporation Quadro NVS 110M / GeForce Go 7300

---

### Post by spivak.d on 2007-04-01
Not useful to solve the problem (beyond motivating developers with sheer numbers), but I, too, have this exact issue. I run an NVIDIA Quadro NVS 110M.

---

### Post by 23meg on 2007-04-01
Nvidia acknowledged this problem quite a while ago; there's a good chance that the next major driver release will fix it.

---

### Post by phoenixfirebird on 2007-04-08
AIGLX might work for some, but what about those of us who get the black windows with ATI and glx?  I get it right away, even with one window open.  I have a X1100 in my acer laptop, and I finally got Beryl to work, but all the windows are black, and the panels as well.  The cube rotates and all just fine, but its far from usable.

---

