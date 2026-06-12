---
title: "Changing the refresh rate: modeline generators?"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by some_random_noob on 2006-11-26
Ok I know nothing about this but I'm trying it anyway. I'm using this: [http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)

Is that exactly the tool I need? I'm also doing it on this monitor: [http://support.dell.com/support/edocs/monitors/E176FP/En/about.htm#Specifioications](http://support.dell.com/support/edocs/monitors/E176FP/En/about.htm#Specifioications)

And in the modeline tool I have entered: 640x480vga in the top box on the left and "60" in the bottom box on the left. Anything I should know? I'm 15 and screwing with linux, so if anyone could prevent me from blowing stuff up then that'd be great :D

Hello?? I'm still here. And yes this is for dapper drake.

---

### Post by drphilngood on 2006-11-26
According to the specs of the monitor you posted the link to, 1280 x 1024 at 60 Hz is your optimal resolution.

edit: See here:

[**HOWTO: change resolution/refresh rate in Xorg**]("http://ubuntuforums.org/showthread.php?t=83973")

Pay close attention to the _**Adding custom modeline**_ section.

You should be very careful.  You can do damage if you don´t know what you are doing.

---

### Post by some_random_noob on 2006-11-26
Errr... I read that and it was posted in april 2005...

Anyway, trying it. I think I have almost narrowed it down to whether it will work or not. 

- Cheers! :cool:

edit: wait... what is all the "xga" and such stuff on the modeline generator?

---

### Post by some_random_noob on 2006-11-26
YAY!!! I pressed the menu button on my monitor and it says its running at 61hertz. So thats the monitor telling me, not the computer :D Don't know where the 61 came from though :confused: 

Ubuntu rocks, once I get my dvd drive and internet set up everything should be back to normal. Thanks to everyone who has helped ubuntu kick ***, its a great substitute for windows xp and now I won't have to constantly upgrade os's and fork out retarded sums of money to security firms. Bonus points if some fat geek/script kiddy in a gaming forum tries to hack me. They'll have to figure out what linux is before they can try anything :-D 

I'm going to play a game of robots to celebrate my victory!

---

### Post by CatKiller on 2006-11-26
> **some_random_noob said:**
> its a great substitute for windows xp

I think you'll find that you've got that entirely the wrong way round. XP is a very poor substitute for Ubuntu :) 

Glad you got your problem fixed.

By the way, the age of a guide doesn't normally matter - especially if it is for standard configurations from the command line. Some of the syntax for these commands has been carefully preserved for thirty years - all the UNIXy stuff, basically.

---

