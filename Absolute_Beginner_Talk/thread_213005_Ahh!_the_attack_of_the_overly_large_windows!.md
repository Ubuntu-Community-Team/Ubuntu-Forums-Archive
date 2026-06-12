---
title: "Ahh! the attack of the overly large windows!"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by OzzBozz on 2006-07-10
seriously though, everything on Linux (ubuntu) is oversized.

Like... when i open up Mozilla and go on myspace, it takes like awhile just to scroll down. 

All of the text that i write is a bit bigger than normal, and it's just a huge pain because everything is big... even my Buddy List. It takes like 10x longer than normal to scroll down because it's so big and the names are all spaced apart.

What should i do???

---

### Post by richbarna on 2006-07-10
> **OzzBozz said:**
> seriously though, everything on Linux (ubuntu) is oversized.

Like... when i open up Mozilla and go on myspace, it takes like awhile just to scroll down. 

All of the text that i write is a bit bigger than normal, and it's just a huge pain because everything is big... even my Buddy List. It takes like 10x longer than normal to scroll down because it's so big and the names are all spaced apart.

What should i do???

Er? Click "view" + "text size" ?

---

### Post by OzzBozz on 2006-07-10
that works for the text
but the windows are still long and big
like it's giving me a headache
it takes 3x longer to scroll down than it normally would...

what do i do?!!!

---

### Post by chameleonkid on 2006-07-10
Check your resolution

---

### Post by OzzBozz on 2006-07-10
yeah
it won't let me change the resolution!!!

i'm at 640x480 with 60 Hz refresh rate... and when i click to change it, it won't let me!!!

---

### Post by chameleonkid on 2006-07-10
Ahh yes that's a terible resolution if you hate large windows.
What type of monitor do you have? (it is important to know what resolutions it can handle refresh rates, sync rates, video card info)
if you have all this info you may want to try ```
xorgconfig 
``` or ```
 xorgcfg
``` I believe that ```
X -configure
``` (as root) might work if you want to let the computer handle it but it will probably not give you the right resolution. I would recomend looking at your **/etc/xorg.conf** for the specs, or some sort of hwdinfo for your monitor specs, then try to do it manually if you can.

---

### Post by Tom Brokaw on 2006-07-10
I couldn't set my resolution either, and ended up breaking the GUI temporarily.  The fix was to type  

sudo dpkg-reconfigure xserver-xorg

at the command line.  That took me through a reconfig of everything.  

I entered the defaults for everything except one part, where it lists all the screen resolutions.  I made sure that my desired res was marked (with the space bar) and continued to press enter until I was done.  When I restarted Xserver, I was able to select my resolution.

BTW, typing startx restarts the GUI if you're at the command line.

I suspect this may be nuking a molehill for your problem, but it worked for me.

---

### Post by OzzBozz on 2006-07-10
didn't work.

hmmm
should i download linux drivers for my ATI 9800 pro? when i did, it wouldn't let me open them because the code was not able to be detected?

i have some Old dell monitor, probablly can't handle to high of a setting...

---

### Post by OzzBozz on 2006-07-10
> **Tom Brokaw said:**
> I couldn't set my resolution either, and ended up breaking the GUI temporarily.  The fix was to type  

sudo dpkg-reconfigure xserver-xorg

at the command line.  That took me through a reconfig of everything.  

I entered the defaults for everything except one part, where it lists all the screen resolutions.  I made sure that my desired res was marked (with the space bar) and continued to press enter until I was done.  When I restarted Xserver, I was able to select my resolution.

BTW, typing startx restarts the GUI if you're at the command line.

I suspect this may be nuking a molehill for your problem, but it worked for me.

yeah...

i'm on the part where i change my screen resolution

any ideas on what to change it to? i've had this monitor for around 6-8 years... it's old.

---

### Post by chameleonkid on 2006-07-10
Well I doubt you are going to get 1280x1024... aim for 1024x768 then 800x600.

---

### Post by OzzBozz on 2006-07-10
well i almost just crashed my linux

but when i select which one... what do i press? Enter?

and the only thing i change is the resolution, i don't enter like my Bus code or whatever and stuff like that... right?

---

### Post by OzzBozz on 2006-07-10
well hmm
i reset the resolution
and restarted my pc

nothing happened

what should i do now then?

---

