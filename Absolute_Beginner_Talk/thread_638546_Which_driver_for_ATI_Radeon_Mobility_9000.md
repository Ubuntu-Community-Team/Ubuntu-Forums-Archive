---
title: "Which driver for ATI Radeon Mobility 9000"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by laffinet on 2007-12-12
Hi,

I'm using a BenQ Joybook 5100 with a ATI Radeon Mobility 9000 with Gutsy 7.10

Can someone tell me what the best driver for this card is, how I install it and what settings I have to use. 
I'm fairly new to Ubuntu and have searched around the forums quite a bit but  what I found hasn't really made a lot of sense to me. Any (relatively) simple instructions would be greatly appreciated. I'm not computer illiterate, just new to Ubuntu.

Many thanks.

---

### Post by Fungal Fractoids on 2007-12-12
This might help, I had terrible trouble trying to get my ATI 1700 working, people here though were very helpful and dumbed it right down for me so it might give you some idea of what you need to do

[http://ubuntuforums.org/showthread.php?t=636652](http://ubuntuforums.org/showthread.php?t=636652)

---

### Post by Fungal Fractoids on 2007-12-12
After a quick search I think you need the same driver as I used, the FGLRX... There is an installation guide

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide). I had trouble with this though, was missing certain dependencies. Have a look, see how you go, if not I'm sure some of the helpful folk here will do their best to get your ATI driver working :)

---

### Post by laffinet on 2007-12-12
Thanks for the quick answer.

My current driver (which shows up as ati-ATI Mach8 etc.) in the screens an graphics preferences)seems to work alright, but a "glxinfo | grep direct" returns a "direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)" which means direct rendering is not working, I guess.

How do I get it to work ?

Thanks again.

---

### Post by Fungal Fractoids on 2007-12-12
Have you looked in the Restricted Drivers Management menu?

---

### Post by umlungu64 on 2007-12-12
Hi!

I'm not at my thinkpad at the moment, but I do know, that with the 9000 you don't use the restricted driver from ATI. The ATI9000 is not supported anymore. As far as I remember, you can select the driver in the graphic-card selcetion (under system) which says something like ATI & mobility. There is also a very good thread on this forum, about how to get compiz fusion running on this card. Don't have the link handy, but search for "status ATI 9000 compiz".
I might be let you know tonight, what settings I've got.

Regards Heinz

---

### Post by laffinet on 2007-12-12
> **Fungal Fractoids said:**
> Have you looked in the Restricted Drivers Management menu?

Yep, I have, the graphics card doesn't even show up there.

---

### Post by laffinet on 2007-12-12
> **umlungu64 said:**
> Hi!

I'm not at my thinkpad at the moment, but I do know, that with the 9000 you don't use the restricted driver from ATI. The ATI9000 is not supported anymore. As far as I remember, you can select the driver in the graphic-card selcetion (under system) which says something like ATI & mobility. There is also a very good thread on this forum, about how to get compiz fusion running on this card. Don't have the link handy, but search for "status ATI 9000 compiz".
I might be let you know tonight, what settings I've got.

Regards Heinz

I don't remember a driver entry for something like "ATI&mobility". I'm not at my laptop at the moment, but will check as soon as I get home. 
I also had a look at a few threads dealing with ati 9000 compiz, but I have to admit they seem fairly complicated to me. I'm probably too much of an Ubuntu noob to understand. Any simple walktrough would be great.
I also tried using the FGLRX, but that gives me a screen that is unreadable, so I had to go back to my current driver (which shows up as ati-ATI Mach8 etc.)

---

