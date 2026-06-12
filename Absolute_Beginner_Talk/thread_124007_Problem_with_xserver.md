---
title: "Problem with xserver"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by Mad182 on 2006-01-31
I used Ubuntu for about one month and everithing was fine, but then I installet Bluefish and rebooted PC, comes "Failed to start the X server... ...Would you like to view the X server output to diagnose the problem?", something like that. I reinstall whole sistem, everithing was working for some time, but when I install OOo2 and reboot computer, there was the same error. What should I do?
I searched forum, but there was information onli about xsrever and ati video cards, but I have NVidia, and everything was working at the beginning.

---

### Post by steve.horsley on 2006-01-31
First off, from your console, use this command after logging in: ```
rm .ICEauthority
```
It deletes a hidden file. This file (it starts with a dot, that's what makes it hidden) sometimes gets scrambled, and it's always the first thing to try when X unexpectedly fails to start. Then try and start X again with the command **startx.** If that doesn't fix it, post us the error messages that startx generates and we'll see from there.

---

### Post by jackfjack on 2006-02-03
I get the same message - "Failed to start the X server... ...Would you like to view the X server output to diagnose the problem?" - when I try to use the Ubuntu LiveCD. Everything seems to be going along fine, up to the point where it says "check battery state" on the screen, and then I get the "failed to start server" message. 

Steve, is there some way that I can utilize your "rm .ICEauthority" suggestion at  the prompt that starts LiveCD process? I am new to Linux and to Ubuntu and hence not familiar with either the console or what can be typed at the beginning of the LiveCD process. I am using a Windows XP Dell Dimension machine. 

I am so tired of Windows, and so eager to get this to work! Would greatly appreciate suggestions/thoughts. Thanks.

---

### Post by rjwood on 2006-02-03
Don't panic when you get to a command line, your computer is working fine--just need to make adjustment for gui to start. You do not need to re-install when this happens. 
fron the command line type

'sudo dpkg-reconfigure xserver-xorg'

then answer the questions. Let the system read your hardware.If you have a nvidia card--choose 'nv' when you get to that point. After you finish--do

'sudo reboot'...

---

### Post by jackfjack on 2006-02-03
Thank you for replying, rjwood. 

I wasn't clear, sorry.  I haven't installed yet. At this point I'm just trying to get the Live CD to run. So the only opportunity I get to type anything in is at the "boot:" prompt, which won't take the 'sudo dpkg-reconfigure xserver-org' command. If/when I press 'return' at the boot prompt, a lot of configuration stuff scrolls by in white letters on a black screen. Then the 'ubuntu' splash screen comes on, and more set up and application startup scrolls by in orange letters, till it gets to the point where we are again back to a black screen and it tries to configure the printer (and fails) and then moves on to  check out the battery, after which point the 'failed to start the x server' message comes up: "Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?" on a blue screen. 

At that point it offers me a 'yes' and a 'no' option, but no command line.
If I take the 'yes' option it gives info about the x window system version and release date and asks "would you like to view the detailed x server output as well?" Again it offers 'yes' and 'no' options. If I choose 'yes' it gives further info, but now I only get an 'okay' button to press. When I do that, it responds with "the x server is now disabled. Restart GDM when it is configured correctly.' Again it provides an 'okay' button as the only option.

When I press 'okay' it goes back to a black screen - at the battery check, where it left off - and hangs there.

---

### Post by Mad182 on 2006-02-04
rm .ICEauthority and dpkg-reconfigure xserver-xorg didn't help. But, can this error be because i have 5.04 relase, but i used 5.10 repository?

---

### Post by CJay554 on 2008-01-21
Old thread but i got the answer.

I have a Thinkpad 240, what i did was install the Ubuntu to a hard drive from another laptop, then switch it into the thinkpad, (so its obvious that the graphics card wont be the same.

I do get the same error, with the same screens, and what i did get was the console.
What happens is SOMETIMES it loads, sometimes it doesn't i got it to load a few times before i knew what to do, then i just simply did "reboot" then i read this thread to find the answer, so i turned on my laptop, hopin to get that screen, but i didn't it was just blank with the text from where the loading was halted.

i rebooted and turned on again, then i noticed the console started Before the "X server" error that comes up, so that means sometimes ubuntu gives you the console sometimes it doesn't you just need to keep rebooting to get it up, then i ran the 'sudo dpkg-reconfigure xserver-xorg' command, asked me a few questions, and it configured now it loads fine!

This error is of course due to a incompatible video card from one laptop to another, a program ruining the xserver is a different story, but hopefully this works for you.

---

