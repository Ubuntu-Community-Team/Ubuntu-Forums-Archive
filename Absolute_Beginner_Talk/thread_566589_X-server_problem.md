---
title: "X-server problem"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by ZTR1760 on 2007-10-03
I got that whole x-server not setup right problem I read that if u use the sudo dpkg-reconfigure xserver-xorg that it will fix it.  I went thru it all chose my vid card (ATI 700pro running ubuntu 5.1) selected all the resolutions I have a 20 inch LCD widescreen monitor, and chose the 24bit option, and selected all those programs to run at startup. And it still comes up with the error.  What do I do now?

---

### Post by Mazza558 on 2007-10-03
What's the error?

---

### Post by ZTR1760 on 2007-10-03
[IMG]http://img.photobucket.com/albums/v307/ZTR1760/PICT0646.jpg[/IMG]
[IMG]http://img.photobucket.com/albums/v307/ZTR1760/PICT0648.jpg[/IMG]

---

### Post by Mazza558 on 2007-10-03
Which driver are you currently set up as? Vesa?

---

### Post by ZTR1760 on 2007-10-03
uh i guess so i mostly just clicked all the defaults but i never saw anything that said vesa

---

### Post by Terl on 2007-10-03
Did you install your video drivers?  Did everything work ok before you tried the reconfigure (well, except the resolution was not what you wanted).?

---

### Post by ZTR1760 on 2007-10-03
I didnt install any drivers all I installed was the ubuntu CD.   And the farthest I get is loading all the stuff at the loading screen then it loses the graphical interface and goes into like a C prompt type screen then it finishes with all the stuff (this is after I loaded ubuntu as Im trying to run it) then it brings me to the X server problem thats as far as I  get and it hasnt changed at all after I setup the whole X-server with that command

---

### Post by Terl on 2007-10-03
Sorry to ask lots of questions, but it will help get you up and running quicker :)

Did you install from the live cd?  Or did you use the alternate cd?

Are you getting this error on the first boot after installation or did it work okay before?

What made you reconfigure the xserver?

---

### Post by ZTR1760 on 2007-10-03
i installed form thee install cd i think thats what u mean by alternate (not live)

This is from the first boot I could never get it to boot fully into ubuntu

I reconfigured because I searched the error message and thats what everyone told them to do , so I thought it would work for me.

---

### Post by Terl on 2007-10-03
Okay, I have been searching a bit for you and need just a little more information.  :)

What are your system specs?  Like ram, processor, monitor (or is it a laptop), we know your graphics card.

Are you really running Ubuntu 5.1?  There are newer versions available.

---

### Post by dichtbijzee on 2007-10-03
There seems to be a problem here. the ubuntu version you are using will be very hard to configure with your graphics card. 5.10 isn't supported anymore and is problably to old, as in older then the graphics  card itself. try 7.04 please.

You can see that it is old, the X-server is 6.8.2 compiled in 2005.

---

### Post by ZTR1760 on 2007-10-03
I know but the order CD option thingy isnt working or something and I didnt want to wait 6 weeks when I had this cd, also I downloaded 7.04 but for some reason I cant burn the ISO to be bootable on startup 

system: Pentium D 805, 2gb DDR 800 @ 166 mhz, running ubuntu off of 6.3 gb IDE hard drive, have win xp pro on sata 250 gb, IDE set as master, monitor is 20 inch Optiquest running at 1650x1050 on xp thats about it

---

### Post by Terl on 2007-10-03
What program are you using to burn the cd?  You need to burn it as an image.

You really, really need to use the more current version.  You will find it easier to configure and the older version no longer is supported.

---

### Post by ZTR1760 on 2007-10-03
I tried using nero but it just burned the file and not as a bootable

---

