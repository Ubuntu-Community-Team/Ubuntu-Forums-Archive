---
title: "Screen Resolution and Color Depth"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2006-07-22
Hello there,

First of all, I must say that I've been using Ubuntu for a couple of weeks, and I haven't missed Windows one bit!  

I really appreciate the wealth of information available on these forums.  

OK, now on to my question.

My machine is a Toshiba Sattellite A10 laptop, running Dapper Drake.  It seems that most of my hardware works without any problems.  I am able to get the proper screen resolution to work ("1024x768").  I presently have a refresh rate of 60Hz.  I'm not sure if that's what it should be, but it does seem to be a bit choppy.  

I also recently learned how to edit my color depth in xorg.conf file.  I was running at 16 bit, and I recently changed it to 24 bit without a problem.  However, I do recall being able to run my display settings at 32 bit color and would like to change this if possible.  

My problem is that I would need to ADD a subsection to my xorg.conf display settings to make room for 32 bit color, and I'm not sure if this safe to do (I'm sorry, I'm a bit of a noob).  Also, is it safe to just CHANGE the range of refresh rates?  I imagine I'd have to find out the exact specs of my monitor, but I'm not sure what I'd really be looking for.  What are the dangers of messing with these display settings in the xorg.conf file?  How can I do this safely?

Thanks for any help you might be able to provide.

---

### Post by robio376 on 2006-07-22
You can try to add another section to xorg.conf file. I went through a similiar problem a while ago. The worst that would happen is that you will not be able to start X. And you would have to delete your addition to the xorg.conf file in the console. Also make sure you backup your working xorg file in case it doesn't work.

---

### Post by Ares Drake on 2006-07-22
> **limberlegs said:**
> I presently have a refresh rate of 60Hz.  I'm not sure if that's what it should be, but it does seem to be a bit choppy.

I suppose 60 Hz is just fine as your laptop has an LCD monitor and LCDs run with 60Hz anyhow.

> **limberlegs said:**
> My problem is that I would need to ADD a subsection to my xorg.conf display settings to make room for 32 bit color, and I'm not sure if this safe to do (I'm sorry, I'm a bit of a noob).  What are the dangers of messing with these display settings in the xorg.conf file?  How can I do this safely?

As robio already posted, adding a subsection should not be a problem. You do however need to follow the syntax, e.g. dont forget a " or something. In this case your graphical desktop would not load. It is best to make a backup copy of /etc/X11/xorg.conf in advance, so in case your work goes wrong, you can copy the backup over.

Good luck and welcome 2 ubuntu!

---

### Post by limberlegs on 2006-07-22
OK, so I tried just adding another subsection to xorg.conf and changing my default depth to 32, but when I restarted it freaked out, I got some screen saying that it was having trouble with the display settings, and then it went straight to the command line.  After a brief panic period (and a reboot to Windows to find out how to edit text from the command line), I managed to set things back to the way they were (default depth 24).

Any other ideas as to how I might do this?  I suppose I can deal w/ 24 bit color, but it would be nice to run my machine to it's full capability.

Thanks for the tips, though.

---

### Post by agurk on 2006-07-22
Being required to find out resolutions and refresh rates (both vertical and horizontal) for a monitor and then to painstakingly manually add and/or edit cryptic stuff in a text file and restart, only to have your monitor possibly wrecked, is simply astounding for an OS aiming for desktop use.

Sorry, not really helpful, I know, I just had to vent some.

---

### Post by limberlegs on 2006-07-22
This does seem a bit tedious.  Nevertheless, I am committed to making this work!  Right now 24 bit color depth will suit my needs, but I'll keep looking for an answer around these parts.

---

### Post by agurk on 2006-07-22
It looks like 24 is max, read this: [http://www.ubuntuforums.org/showthread.php?t=217770](http://www.ubuntuforums.org/showthread.php?t=217770)

---

### Post by srunni on 2006-07-22
Why don't you attach a copy of your xorg.conf file? Someone who knows how to properly edit it might post the correctly modified version then.

---

### Post by limberlegs on 2006-07-22
Good idea!  I've attached it to this post.  It seems from that thread that you mentioned above that 24 bit depth is really the same as 32.  But it seemst that I'm having a bit of trouble reading antialiased fonts, etc.  Perhaps I'm just seeing things.

---

### Post by dolphinholmer on 2006-07-22
According to [this thread]("http://ubuntuforums.org/showthread.php?t=4317&highlight=color+depth+xorg")
"24-bit is the same as windows in 32-bit mode, the extra 8-bits aren't use to enhance colours" and
"24 it is the highest "true" depth. 32 bit is basically 24 bit with enhancements"

---

