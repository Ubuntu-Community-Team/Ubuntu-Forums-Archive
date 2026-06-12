---
title: "install ubuntu and my screen is black"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by moose4204l on 2007-12-10
i just installed the ubhuntu 7.10 and after everything is done my screen become black.

i hear the sound for the log in screen. by my screen is black. i even type my name and password and i hear the loading music. by my screen still is black. 

whats going on here and how do i fix it?

thanks

---

### Post by Law506 on 2007-12-10
what kind of video card?

---

### Post by BatPenguin on 2007-12-10
Can you switch to a terminal and log in just fine? (By pressing CTRL+ALT+F2)

You should either post more information about your system (laptop/desktop), video card etc. or, rather, just look for information here on the computer type (if laptop) or video card. Sounds unlikely that you're the first one with this problem.

If you have a laptop that could well be that your tv-out or monitor out is detected as the first video out and you need to change that, that at least brings up a completely black screen. Happened to me once with an ASUS latop and Feisty. In this case editing /etc/X11/xorg.conf will fix it but we'd need more information. You might be able to test this by plugging in an extra monitor/TV. Better do this while the system is off and then boot and see if the other screen shows your desktop.

I suggest you start by searching for information on your equipment (laptop model if that's it) here in the forums. If it doesn't help, post here with computer information and /etc/X11/xorg.conf file contents.

Good luck.

---

### Post by toasterofirony on 2007-12-10
Also, and don't complain about this suggestion - is the monitor turned on and plugged into the video card?

Try hitting ctrl+alt+F2 to get a terminal to log into. If you can get the terminal to pop-up, you've probably got something odd going on in your xorg.conf.

---

### Post by moose4204l on 2007-12-10
well i can log into it with command line through the ctrl alt f2 but when i did that i can manuever through the folders and stuff but every once in awhile i got an error code which was

[    100.586280 ] bcm43xx: Error: Microcode "bcm43xx_microcide4.fw" not available or load file

then i got the same message a couple more times after a short period with other numbers

[167.040480 ]
[144.889955]
etc etc

i know bcm43xx is broadcom wireless driver chip thing but i figured id post it

also is there a way to maneuver to find my card. my laptop is a dell inspiron 5100 with factory equipment for the most part. it is roughly 4 -5 years old. 

my fiesty fawn work absolutely fine. but i deleted that since i had 7.10.

---

### Post by BatPenguin on 2007-12-10
OK, do a search on "Dell Inspiron 5100" here on the forums and start going through what you find. The previous threads are likely to help you a lot. Actually you should send follow-up questions to whichever thread there is the most active / appropriate. We might be able to help more but you'll probably get much better answers there with people who have the same hardware and might've already solved the same issues :)

I saw at least one thread where someone else is having the same problem, no solution posted though, but you could probably just ask on that thread and send a private message to them (in case not watching the thread anymore) to find out how they solved it. There's also a thread about "Troubleshooting the Dell Inspiron 5100"...go read up and good luck!

OK, looks like a solution (with VESA driver): [http://ubuntuforums.org/showthread.php?t=583559&highlight=dell+inspiron+5100](http://ubuntuforums.org/showthread.php?t=583559&highlight=dell+inspiron+5100)

---

### Post by BatPenguin on 2007-12-13
OK, it's been a few days and since there hasn't been new posts here, I assume you got the problem fixed, Moose?

If that's the case, it'd probably help the next person with the same problem if you posted a quick explanation of what you did (or a link to the solution) and marked the thread as "SOLVED" from the Thread tools. I know I at least enjoy looking for answers to my problems and seeing that beautiful word next to the thread's name :)

---

### Post by aonegodman on 2007-12-13
Not sure if this info will help, but while trying out different screen resolutions in "Gutsy" I tried one that caused my monitor to go "black". I tapped on the keyboard, nothing helped, I findly noticed that the power light on my monitor had gone from green to a dull flashing yellow, I powered off the monitor(NEC FE990) and back on. Came back up with desktop there again. I think my monitor or video card coudn't handle the resolution and refresh rate I tried and sorta went into "lmp mode". Perhaps this is what you have, perhaps not. Just a thought. :)

---

