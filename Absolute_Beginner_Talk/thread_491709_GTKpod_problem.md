---
title: "GTKpod problem"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-07-03
I'm getting this message every time I try to "load" my ipod in GTKpod: "Error initialising iPod: Problem creating iPod directory or file: '/media/ipod/iPod_Control'."  Do I need to create that folder? What the heck do I do to get this darn thing to work?

I'll be doing my homework on this as I await a reply.

Thank you.

---

### Post by Raineer on 2007-07-03
Well, I would make sure the system is really calling your iPod "ipod"

Open Nautilus (or Konqueror) and navigate to "/media" with your ipod plugged into a USB port.  Does it show up as "ipod" or something else?  Remeber case is sensitive here.

---

### Post by Protagonistics on 2007-07-04
Ok, I used nautilus and scoped out /media/ipod but it was actually IPOD, so I switched that, and all my files appeared- yay.

But what I really wanted to do was put a movie in mp4 format on my iPod. when I clicked "add file" in gtkpod, I get this message:

Import of '/home/ael/Desktop/Music/Humans Vs Zombies Documentary.mp4' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library.
The following track could not be processed (filetype is known but analysis failed): '/home/ael/Desktop/Music/Humans Vs Zombies Documentary.mp4'

Soooo... I have a feeling compiling means doing something like apt-getting "mpv42" but after that I'm lost... I'm guessing I need to Terminal something in like "sudo compile gtkpod mpv42" but I don't know these things.

Whaddya think- and is this a common problem?

---

### Post by ralphz on 2007-08-06
Hi
Have you solved your problem have the same thing here :(

---

### Post by ricardisimo on 2007-10-23
No luck here... I have a 5th Generation 60GB White Video iPod (model xA003) that appears on my computer as /media/disk, and I try to set that as the mountpoint, with no success. Same error:
```
Error initialising iPod: Problem creating iPod directory or file: '/media/disk/iPod_Control/Music'.
```
It was originally formatted on iTunes on a Mac - don't know if that makes any difference. Any help would be very much appreciated. Thanks.

---

### Post by fululian on 2007-11-05
concerning the ".mp4"-problem, there is an answer over here - [http://ubuntuforums.org/showthread.php?t=601429&highlight=gtkpod]("http://ubuntuforums.org/showthread.php?t=601429&highlight=gtkpod") hope they update this soon - because i don't seem to be able to "compile this library with gtkpod".

---

### Post by samhuri on 2007-11-08
I wrote a quick post explaining how to get a working gtkpod.  I didn't do any real work myself, I only read the solution in the bug report.

[http://sami.samhuri.net/2007/10/30/gtkpod-in-gutsy-got-you-groaning](http://sami.samhuri.net/2007/10/30/gtkpod-in-gutsy-got-you-groaning)

---

