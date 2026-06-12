---
title: "Dapper Soundcard Problems"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2006-07-18
Hello All,

I recently upgraded an old Dell Optiplex G1 (dinosaur) to Dapper. 

It ran Breezy great but I am not convinced that Dapper is going to fly. BTW I had to start from scratch and installed clean from the cd. 

One issue is the sound. I can modprobe and it works. But what a pain! In Breezy I added:

[B]to /etc/modules:

snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5[/B]

And this worked. But it doesn't work with Dapper.

Does anyone know why? Or what else I could try?

Thanks!

---

### Post by gigi1234 on 2006-07-19
Anyone, please?

I have tried some of the suggestions in the "comprehensive soundcard guide" but still no luck.

I edited my /etc/modules file as suggested but nothing. 

The sound works fine if I do a modprobe to load the soundcard though. 

I doubt if reloading ALSA would help because I am already working from a fresh installation of Dapper. 

Does anyone have some thoughts about what to try next?

I am confused why the soundcard worked in Breezy but not in Dapper!

Thanks! Gigi

---

### Post by bernied on 2006-07-19
A vague possible - does alsa-utils run at startup?
I think you look in System - Services (sorry, haven't got Dapper with me)
Failing that, you could write a small script that runs at startup.

---

### Post by gigi1234 on 2006-07-19
I am not sure how to check the alsa utils issue.

Does this affect the loading of the soundcard at startup?

How do I write a script that will run alsa utils at startup?

I am pretty lost, haven't dealt much with these issues, kind of noob.

---

### Post by bernied on 2006-07-20
I'm sorry, I'm at work again and don't have access to my kubuntu pc. I'm sure someone here can give you the right place to go. From memory, I think you're looking for the Services section in the System Settings menu, and you need to be in administrator mode. There's a list of possible services on the left-hand side, and an indication of whether it should run at startup, and whether it is running now. I got my sound to work after selecting alsa-utils to run at startup, then restarting the machine. For some reason, running it now did not help. That may (or may not) be the issue with your machine as well.

I agree that Dapper was not as clean an install as the old Badger, I also had some issues that were most un-Ubuntu-like. But I think, with a little coaxing, it does fly !

It's generally a good idea to wait a couple of months after a new release before upgrading, for most the niggly bits to get ironed out, unless you're happy to be a part of the ironing process. Remember what happened when Bill Gates launched W98?

---

### Post by gigi1234 on 2006-07-20
Ah yes, Windows 98. What a beast!

I have somehow fixed the problem.

I added the line snd-cs4236 to /etc/modules and I open the alsa mixed and maxed all the levels. I am not sure which action led to the resolution of the problem, but at least it is working now.

Thanks for your help!

---

