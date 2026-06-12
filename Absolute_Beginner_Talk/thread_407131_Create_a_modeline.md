---
title: "Create a modeline?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-04-11
Anyone help me with this modeline business?

I am trying to edit xorg.conf in order to have widescreen display.  Using the procedure at this thread:

[http://ubuntuforums.org/showthread.php?t=326864]("http://ubuntuforums.org/showthread.php?t=326864")[http://ubuntuforums.org/showthread.php?t=326864](http://ubuntuforums.org/showthread.php?t=326864)

I have reset the mode in 915resolution to my widescreen specs (1440x900).  The next step, according to the procedure, is to 

> 
Insert the Modeline into your /etc/X11/xorg.conf file

I am not sure how to do that.  When I look at my xorg.conf , I don't see any modeline and I'm not sure how to insert one.  When I have seen various modelines, I am not sure what all those numbers are.

Please help a noobie!

Thanks,
Lance

---

### Post by freebird54 on 2007-04-11
Assuming you have the modeline created (or found) that you wish to use, you insert it in the 'Monitor' section of your xorg.conf file.  This is explained about 1/2 way down the second link in your previous post.  Just take it slow, and have a backup available in case of 'unintended consequences'. :)

---

