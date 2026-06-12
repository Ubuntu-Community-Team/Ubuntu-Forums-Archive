---
title: "Vizio VX37L as monitor"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by karrank% on 2007-11-13
Just installed Dapper and  being new to Ubuntu, wonder if there's a way to use my Vizio home TV as a monitor. Got a Nvidia 5500 w/ dual outputs and the home tv is connected via DVI out to RGB input of the Vizio. nothing but video gibberish with a display from the vizio saying 640X350@69HZ.(?)

Eveything else more or less works, I'm very pleasantly surprised considering how much of a #@^&! I am re 'puters. 

Thanks for considering my question,


-K

---

### Post by kcox5342 on 2007-12-29
I just got one last night, and a VGA cable connects my Acer laptop with Gutsy to its PC input...  very nice indeed, once the video signal is worked out.  It's 1280X800 @ 60hz, and the only display issues I have are an annoying amount of interference, both on my laptop's screen and the TV, when playing 720p Quicktime previews.  This didn't happen before plugging it in to the TV.

But I am taking the TV back today... apparently, the Wal-Mart one has some features removed to make it cheaper.  The feature that's missing that I can't live without: "Zoom", the widescreen mode for non-anamorphic content.  The VX37L has zoom, the VW37L does not.  Beware the VWs, sold at Wal-Mart and K-Mart.  If I had a VX I would be keeping it.

---

### Post by SpacePilot on 2007-12-29
I have been setting up a lot of dual screen lately at work.  Both Monitors and and laptop with flatscreen digital tv.

Running linux you do in general want a nvidia card, and you want ot be running the nvidia drivers. That being said, this is how I usually go about it.

Back up the existing xorg.conf 
Find out what the optimum resolution and refresh rate are for the monitor/tv you are about to plug in.


Plug in the tv/monitor.

Run the nvidia-settings app by typing gksudo nvidia-settings 

The nvidia settings is pretty much self explanatory. It will detect you other screen. Configure it and try first with the auto modes. If you don't get optimum refresh rate and resolution or you can not set it. Just hard code it in the xorg.conf later.

You need to restart xorg every time you plug it in or out. (ctrl +  alt + backspace)

Done

---

### Post by karrank% on 2008-01-06
Yeah, that's why we got the vx37L  @ costco, plus walmart's was actually more expensive at the time.... Love the display, especially for the money, now onto the OS interoperability issues....
-and thanks for the reply, been awhile since I checked in, sorry...
-K

---

### Post by karrank% on 2008-01-06
Thanks for the reply, took me awhile to get checked in here... Will take your advice and plunge over the command-line cliff (yikes!) 
-Will advise as to progress--or lack thereof..
-K.

---

### Post by karrank% on 2008-01-22
Mark this as solved, thanks to the advice in this thread:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)
used envy and worked as intended! (Vizio as clone in twinview)
took just a little while to plow through but man was it worth it! 
-Thanx again to you all out there!

---

### Post by karrank% on 2008-01-23
Ack! not solved! in the sense of it works, but keeps resetting to disable the Vizio every reboot. 
Ideas anyone?

---

