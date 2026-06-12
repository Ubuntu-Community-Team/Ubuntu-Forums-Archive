---
title: "Noob Has Questions: Graphics, File Extensions, and Resources"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by mnemonicus on 2007-08-21
I am most definitely a noob, and I will probably make 20 or 30 posts in the next week that will be elementary and irritating to some... But I got Ubuntu installed, and I'm ready to learn this poo! Should be fun.

First, I want to get my graphics drivers going on top of the one that comes with Ubuntu... my problem is that the driver that comes from nvidia (for a 6800 GS) appears to be a script... but it was advertised as being an executable... which is it? How can I tell? How can I get the thing to execute (I already checked "executable" in the properties menu - no dice)... It appears that there's file extension problem going on, and I wouldn't know where or how to solve it... Ubuntu keeps trying to open it with gedit... WHY!!!

Second, I want to get compriz going, but I'm not sure how to. Do you use a package manager like kpackage or something? If so, can someone please write instructions how to make it work?

Third, what are some good apps I should find that are Linux-exclusive (once I figure out how to run executables)?

Last - aside from ubuntuforums.org, what are some good resources for noobs like myself to get the hang of this OS? Books, magazines, and websites will do...

Thanks in advance for your help!

---

### Post by hyper_ch on 2007-08-21
If you have Ubuntu Feisty Fawn 7.04 then you have a restricted driver manager that should take care of the installation for the nVidia drivers.

In Linux and Unix a file is not made executable by adding an certain extension to it (which is really a bad thing to do) but to change its file modes and ownerships. 

[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)
[http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown)

And this site is great to start with the basics in Ubuntu:   [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Ubuntu Feisty comes with compiz integrated but you need to activate it (after you have enabled 3d drivers for your video card by the restricted driver manager)

---

### Post by overdrank on 2007-08-21
> **mnemonicus said:**
> I am most definitely a noob, and I will probably make 20 or 30 posts in the next week that will be elementary and irritating to some... But I got Ubuntu installed, and I'm ready to learn this poo! Should be fun.

First, I want to get my graphics drivers going on top of the one that comes with Ubuntu... my problem is that the driver that comes from nvidia (for a 6800 GS) appears to be a script... but it was advertised as being an executable... which is it? How can I tell? How can I get the thing to execute (I already checked "executable" in the properties menu - no dice)... It appears that there's file extension problem going on, and I wouldn't know where or how to solve it... Ubuntu keeps trying to open it with gedit... WHY!!!

Second, I want to get compriz going, but I'm not sure how to. Do you use a package manager like kpackage or something? If so, can someone please write instructions how to make it work?

Third, what are some good apps I should find that are Linux-exclusive (once I figure out how to run executables)?

Last - aside from ubuntuforums.org, what are some good resources for noobs like myself to get the hang of this OS? Books, magazines, and websites will do...

Thanks in advance for your help!
HI and welcome, For you graphics driver it would be hard to say why ubuntu is wanting to open with gedit but I would say that it is a windows executable applications not linux. You may try Envy to install you drivers
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Here is a link that may help with compiz-fusion after you get the graphics solved. 
[http://ubuntuforums.org/showthread.php?t=481314&highlight=nvidia+6800+GS](http://ubuntuforums.org/showthread.php?t=481314&highlight=nvidia+6800+GS)
This link may help with some apps
[http://howtoforge.com/the_perfect_desktop_ubuntu7.04](http://howtoforge.com/the_perfect_desktop_ubuntu7.04)
As for learning I did purchase a couple of books but you can learn alot just from the documentation on ubuntu in the little blue circle with the question mark in it on the top panel. The forums are a great place to learn also. Good luck! :popcorn:

---

### Post by mnemonicus on 2007-08-21
Thanks... Envy appears to be working as we speak. 

I'll work on compiz after that... thanks for the resources and info, both of you.

---

