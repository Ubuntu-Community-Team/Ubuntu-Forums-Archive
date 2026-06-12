---
title: "Wish me luck..!"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by NT4usB on 2006-05-20
Been putting off building a PVR for too long so I got after it this weekend.
Zero experience with Linux so I figured I'd use this project to learn it.
Just fired up the box and started the install of Ubuntu 5.10.
Right now we're downloading the 153 updates it found...

Here's what I put together. Maybe all y'all (plural form of y'all) can have a look at it and tell me what might give me troubles...

Gigabyte GA-8I945GMF, P4 631, 2x Kingston KVR667D2N5K2/1G, 2x WD 250 GB 16MB SATA 3.0, HAUPPAUGE WINTV-PVR-150, LiteOn SHM-165H6S DVD.

Updates are done. Time to see what we can screw up!

---

### Post by dlai on 2006-05-20
I would recommend you this site!!! [http://hyams.webhop.net/mythtv/myth_ubuntu.html]("http://hyams.webhop.net/mythtv/myth_ubuntu.html")

---

### Post by NT4usB on 2006-05-20
Thanks for that! 
...so much to learn

---

### Post by mostwanted on 2006-05-20
If you want a very graphical guide (even has screencasts now) teaching you how to install new software in Ubuntu, [look here]("http://monkeyblog.org/ubuntu/installing").

---

### Post by NT4usB on 2006-05-20
Thanks for the link!
First thing I did after the install finished was go out and grab the latest Firefox and Thunderbird from ftp.mozilla,org... then stare at it for an hour trying to figure out how to install it.

I'm finding tons of useful links here... great site!
Thanks all!

---

### Post by NT4usB on 2006-05-25
Well... 5 days and ~50 hours into this and I'm having a blast! (not).
Managed to get through the install of mythtv in about 20 hours thanks to the howto posted above.
Realized I didn't have any way to get TV out of my box so picked up a video card (GIGABYTE GV-NX73G128D GEFORCE 7300GS) along with another PVR-150 and stuck them in... and promptly broke the video (crashed the X thingie in linux speak *g*)
Struggling to get video back, finally got a picture using vesa drivers.

Now mythtv is broke.

Are things in linux dependant so that messing with (or messing up) something like video drivers will jack other applications?

...the quest continues

---

### Post by mostwanted on 2006-05-25
Thunderbird and Firefox are not like typical source code bundles, they're precompiled. You ca search for both on the wiki, there are pages on how to install them next. You can also use Automatix (a search away).

X can be reconfigured with your new video card using the command:

sudo dpkg-reconfigure xserver-xorg

---

### Post by nalmeth on 2006-05-25
I'm guessing that's an NVIDIA? Pick the nv driver if so, then you can setup the accelerated driver afterward.

---

### Post by Koech on 2006-05-25
All the best man!

---

### Post by NT4usB on 2006-05-25
[QUOTE=mostwanted]Thunderbird and Firefox are not like typical source code bundles, they're precompiled. You ca search for both on the wiki, there are pages on how to install them next. You can also use Automatix (a search away).[/QUOTE]

Got firefox going ok (thanks to a skript found in the howto section)

> 
X can be reconfigured with your new video card using the command:

sudo dpkg-reconfigure xserver-xorg

Been there, done that. The nv driver and nvidia driver just broke X. Vesa got it going.
Stepping through that process also appeared to reset other functions... sound was back on (I had it turned off), etc.
I'm wondering if resetting these things could have broke mythtv..?
I have the new nvidia drivers... going to try to install them tonight.

Thanks for the input!

(btw..., ~10 of the 50 hours was spent googling and searching these forums for solutions. I'm surprised keyword searches on (EE) errors and the like don't return very many hits. I would think they would be the basis for many, many *Help me!* posts)

---

### Post by NT4usB on 2006-05-28
Ok, after struggling with getting the nvidia to work for another 20 hours or so, tried Alberto Milone's fresh new skript and it worked a treat!
Big **Thank you!** to Alberto.
find it here:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

