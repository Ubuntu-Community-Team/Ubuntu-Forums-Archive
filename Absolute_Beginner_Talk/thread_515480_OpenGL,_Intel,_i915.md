---
title: "OpenGL, Intel, i915"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-08-02
I read somewhere that anything regarding graphics is ultimately tied to OpenGL...My problem is that anything that relies on OpenGL suffers serious issues. I've got cpufreq enabled and anytime I do something as simple as watch a Flash video my cpu shoots up to an ungodly percentage and cause my fan to go non-stop (i've got a laptop). Here's what I have problems with:

-games, even simple ones like billiards or 3D chess
-watching flash videos, or any video for that matter (can cause firefox to crash, shoots up cpu)
-multimedia apps that involve any graphics
-75% of the screensavers...I'm forced to use either black screen or flurry (i think that's what it's called)
-heck, even just running glxgears causes the cpu to shoot up and thus cause the fan to start

I'm not saying that nothing multimedia-wise doesn't work. It's just a little annoying to have to keep on setting my cpu to a lower setting via cpufreq just to watch a simple video or dvd or something. I would be fine if the cpu would eventually come down...but it never does and it keeps running my fan at a constant rate and my cpu temps hotter. Is there a simple workaround fix for this...perhaps a package I'm missing or to disable something? I'm surprised I haven't found more people complaining about this...and if I missed any threads concerning this could you guys post links so I could read them? Here's my comp specs if it is useful

Acer Aspire 1642WMLi laptop:
Pentium M 1.73
1.2 gb
intel i915 chipset
Fiesty 7.04

---

### Post by wolfen69 on 2007-08-02
are you using "915resolution"?

---

### Post by isaacj87 on 2007-08-02
yeah...that and xserver-xorg-i810 not the xserver-xorg-intel drivers...but 915resolution only corrects the resolution

---

### Post by isaacj87 on 2007-08-02
sorry...but bump

---

### Post by Milk &amp; Toast &amp; Honey on 2007-08-03
Same issue here.

I'm using Acer Travelmate 4021, specs:
Centrino 1.6Ghz
2GB DDR
i915GM
xserver-xorg-intel driver.

Are u using Beryl or Compiz ?
Actually, when I'm not using Beryl, the processor usage is lower.

> ... I'm surprised I haven't found more people complaining about this...
Well, maybe everyone think "it just what it has to be" ? I don't know, because I have that thought, 
until I read your post.

It would be nice, if the processor usage isn't that high.
Anyone knows how to get rid this problem ?

---

### Post by Hospadar on 2007-08-03
I really don't know about your specific situation, but my advice would be that if intel has some proprietary linux drivers, you should install them.  I use an nvidia card and always have no end to crappy graphics until I install the proprietary nvidia drivers.

Also, try running glxgears, if your opengl is running like it's supposed to be the gears will look smooth and you will get a good framerate.

If opengl is working fine but your problem is getting your cpu to cool off after you do something with opengl, I wouldn't know where to send you, but if you can't figure any way to get it to stop working so hard other than cpufreq, you might try looking into writing a little bash script you can put on your desktop so you can just double click to kill it instead of having to open a terminal

---

### Post by Milk &amp; Toast &amp; Honey on 2007-08-03
> Also, try running glxgears, if your opengl is running like it's supposed to be the gears will look smooth and you will get a good framerate.
I got this result from glxgears:
```

2608 frames in 5.0 seconds = 521.527 FPS
4217 frames in 5.0 seconds = 843.385 FPS
4143 frames in 5.0 seconds = 828.443 FPS
4357 frames in 5.0 seconds = 871.237 FPS
4298 frames in 5.0 seconds = 859.580 FPS
4163 frames in 5.0 seconds = 832.510 FPS
4002 frames in 5.0 seconds = 800.388 FPS

```
With about 50% of CPU usage. The resulting graphics has no lag at all, just smooth.
But can the CPU usage reduced somehow ?

---

### Post by isaacj87 on 2007-08-03
My glxgears output is similar to yours...I think I found some proprietary drivers for intel's i915 but am a little hesitant to compile and install it...But my CPU usage is outrageous and the fan goes uncontrollably...it's really annoying...I filed a bug on LaunchPad, but I don't think it'll do any good..I guess I'll try the proprietary drivers..

---

### Post by Steveway on 2007-08-03
The official Inteldrivers are Open-source.
It's normal that when you use 3D-apps or watch movies CPU-usage rises and it speeds up the fans to prevent the CPU from burning.

---

### Post by isaacj87 on 2007-08-03
> **Steveway said:**
> The official Inteldrivers are Open-source.
It's normal that when you use 3D-apps or watch movies CPU-usage rises and it speeds up the fans to prevent the CPU from burning.

True, but I don't think flash videos should spike the cpu like it does...

I found a deb called xf86-xserver-intel on this forums released 3 weeks ago, but all it did was marginally increase my glxgears output...

---

### Post by Steveway on 2007-08-03
Flash is also pretty CPU-intensive.
It sometimes slows my Firefox to a crawl on a 3000MHz Pc  with 512MB Ram and a Geforce FX Go 5200.
EDIT: Forgot one thing: Blame Adobe for that.

---

### Post by jordanmthomas on 2007-08-03
If it helps any, I don't think this is an Ubuntu-only issue and more an issue with the driver itself.  I use Arch and I get similar results in glxgears and the same problems with flash.

I was using the performance cpu governor for the tests, and both times CPU usage was at about 35%.
[first ss]("http://jordanmthomas.googlepages.com/Screenshot.jpg"):  with compiz running.
[second]("http://jordanmthomas.googlepages.com/Screenshot-1.jpg"):  metacity
compiz didn't seem to make a difference.

(maybe a useless post here, but I was just confirming the "problem")

One way to make your computer's fans shut up (at the cost of performance) is to use the powersave governor for your processor (assuming it supports it).  I usually use ondemand, but flash always cranks it up to max speed unless it's on powersave.

---

### Post by isaacj87 on 2007-08-03
> **Steveway said:**
> Flash is also pretty CPU-intensive.
It sometimes slows my Firefox to a crawl on a 3000MHz Pc  with 512MB Ram and a Geforce FX Go 5200.
EDIT: Forgot one thing: Blame Adobe for that.

Wow, didn't realize that Flash was a pain in the behind for other people too...
I wonder why it causes problems on linux machines but never really for windows machines. My firefox often crashes due to Flash, thankfully Firefox has the restore feature!

---

### Post by Milk &amp; Toast &amp; Honey on 2007-08-04
> **jordanmthomas said:**
> If it helps any, I don't think this is an Ubuntu-only issue and more an issue with the driver itself.  I use Arch and I get similar results in glxgears and the same problems with flash.
Yes indeed, my openSuSE box also has similar problem with flash. And the box using 945GM.

> The official Inteldrivers are Open-source.
Is the official Interdrivers is xorg-xserver-intel in the repo?

Long time ago, when I still using SuSE 10.0 on my laptop, I tried to install the Intel driver from Intel's website, but that doesn't improve the performance, whereas it makes compiz doesn't work at all at that time.
Well, it maybe just me that wrongly configured the driver :) .

---

