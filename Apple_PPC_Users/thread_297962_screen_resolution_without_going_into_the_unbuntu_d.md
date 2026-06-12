---
title: "screen resolution without going into the unbuntu desktop?"
date: 2006-11-12
forum: Apple PPC Users
---

### Post by casta_baga on 2006-11-12
screen resolutions ... / .. 

i installed 6.10 ubuntu with a free space indeed,, thank you for all the outputs that made me understand some  directions..

going into the direction of outputting  a resolution of 1152X768 with a ATY RAGM6 video card on powerboog G4....

i can not start the actual  ubuntu, i mean, i can start the powerbook but it starts with a message saying that does not apply conf on xorg.conf
and..
theres a very messy windonw asking me if i want to display the cause of the incident but does not let me fix it..

how can i change screen resolution without going into the unbuntu desktop?
 i know i screw up...

---

### Post by scrooge_74 on 2006-11-12
you have to reconfigure the xserver resolution, read  the message error that appears after booting up, it will tell you if it can recognize your video card or if the problem is something else.

Then you can dpkg-reconfigure xserver-xfree86 (old version) or is it xserver-xorg ? don't remember that one very well

---

### Post by scrooge_74 on 2006-11-12
first read the error log then sudo dpkg-reconfigure xserver-xorg

---

### Post by casta_baga on 2006-11-12
i know that i have to reconfigure xserv seroluttion but i can not change nothing,, i'm using a single touch mouse...

is that the problem?

it got to be a way of going into a command  line and input the command to output those changes..

please..
give me some reply to fix this problem that is killing me..

---

### Post by john8520 on 2006-11-12
Could you not also edit /etc/X11/xorg.conf (or XF86Config-4) to add the resolution?

---

### Post by scrooge_74 on 2006-11-12
first read the error log then sudo dpkg-reconfigure xserver-xorg

All changes you have to made them through the keyboard, it can even be your mouse.

That you can correct also with the xserver-xorg reconfiguration

you may have to adjust the monitor information the horizontal and vertica sync, it appears in the back of your monitor or on the manual.  You may also have to adjust the resolution of the system

It may take you a few tries until you get things right.

I had the same troubles the first time I installed a Debian base system, problems with the video card and then with the mouse.

All the changes you have to do will go in to a file in /etc/X11/xorg.conf

from command line you can do ... sudo nano /etc/X11/xorg.conf

---

### Post by casta_baga on 2006-11-12
first read the error log then sudo dpkg-reconfigure xserver-xorg..


thank you very much 4 u're reply ,,
i could find a way to try that but nothing happens..
if i press enter the cursor just goes down and nothing comes out..

this is confusing, how came in theses days stuff like ubuntu are popping out on the web

---

### Post by scrooge_74 on 2006-11-12
yes the xorg.conf file manages video card, mouse, monitor, keyboard and a few other things, that will let you get into a desktop enviroment.

in the mean time you are stuck in the command line only.

you need to carefully read the error log when it try to go into Desktop to know what is the problem. you may think is the video, but it could well be the mouse

---

### Post by scrooge_74 on 2006-11-12
you will be surprise how easy it is to work with Ubuntu, you just need more experience.  I had the same trouble first time around like 10 months ago.  Just went reading a lot of stuff until found the answer

it just the xserver is having some trouble with some part of your hardware

Maybe one step at a time, boot the equipment again and read through the log

---

### Post by scrooge_74 on 2006-11-12
Also since I see you lack experience I will recommend you install version 6.06 which is just a few months older, has bugs fixed and is working very well.

6.10 is basically brand new, and brand new software is always in need of bug fixes, and this version is Edge, and on the edge. Myself probably I'm going to stick with Dapper for a long time.

---

### Post by casta_baga on 2006-11-12
hey hey..

I .... we ...  kind of found the way to fix it ... 
if I go back to 6.06?
 it was a motive to look through..

hey hey..

thank you
t-

---

### Post by scrooge_74 on 2006-11-12
Well yes, is the same as buying a new car from the first batch of a new model.  Those are the ones that have all the problems and quirks, that dissapear after they fix the production line.

It is most likely the problem will go away if you install the 6.06 version, maybe even running it as a live CD that way you can see if there are any problems.  First version of Ubuntu 6 did not run on a previous machine I had do to problem with processor not been Intel base, when 6.06 came out, Ubuntu ran with no problem on same machine.

---

### Post by casta_baga on 2006-11-12
Well yes, is the same as buying a new car from the first batch of a new model. Those are the ones that have all the problems and quirks, that dissapear after they fix the production line.

I see the thought traffic on that calculation listen to red snapper - making bones ..

why the DNA... if we can
67[67]67

before the crash comes I'm out of here like I did before the last Ontario's crash...


if I stay here more than 3 years my investment are going to be
with the girrasol plant as what?  symbol..?

---

