---
title: "Resolution Help"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by CloudyHaze on 2006-05-07
Alright....very new to the world of linux here.... enjoying it so far.

Installed Ubuntu today....everything went smoothly i think..

The only problem im having is that the screen resolution is at 640 x 480. So everything is huge.

I go to system>preferences>screen res ........ but only the one option is there.  Why is this?

I have a generic 17" monitor......had nice high res when i was running windows.......

NVidia GEForce2 video card........ AMD Semperon Processor

Any help appreciated please

---

### Post by nalmeth on 2006-05-07
Not a problem. There are a couple ways of fixing this, but with usual success, I recommend this way:
APPLICATIONS --> ACCESSORIES --> TERMINAL
enter this command:
sudo dpkg-reconfigure xserver-xorg
pick the defaults across the board unless you know / can_guess better.
When you get to resolution's, add the ones you need. 
Reboot is probably not needed, but do it anyway
sudo reboot
log in normally (into gnome session of course), and hopefully you'll have your extra resolutions!

---

### Post by CloudyHaze on 2006-05-07
Nice!! Thank you very much.  

That worked like a charm.  

Now what exactly is that command i used though? Is that a general config thing? Is there a place to learn more about general stuff like this so i dont have ask on here everytime i have a problem :)

---

### Post by nalmeth on 2006-05-07
Well, the hope is that Ubuntu is becoming an OS that reduces the need for the command line, and allow's total GUI configuration an use.
This has not been achieved yet, but is coming closer and closer.
That command was just what it looks like, a way to configure the "Xserver", the display in which you use the GUI tools, like your desktop environment, and window manager, etc.
If you would like to know the command line better, there are some good guides around (I will try to dig some up if you can't find any), but hopefully you will not need to know much of anything more technical.
Don't hesitate to use the forum's if you have difficulties.
Use the [Advanced search]("http://ubuntuforums.org/search.php"). I find it more useful to search for titles of thread's rather than text in general, but play around with it.
There's tons of good info in the forums.
Here are some good links to documentation:
[UDSF]("http://doc.gwos.org/index.php/Main_Page")
[Ubuntu Wiki]("https://wiki.ubuntu.com/UserDocumentation")

---

