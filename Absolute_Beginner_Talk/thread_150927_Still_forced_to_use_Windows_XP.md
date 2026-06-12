---
title: "Still forced to use Windows XP"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by lonelypauly on 2006-03-26
Until dual monitor support becomes built into Ubuntu (or at least made easier to configure) I will have to stick with XP.  I really like Ubuntu and would much rather use* it*.  I couldn't possibly run it right now if I can't have 2 seperate desktops for GIMP, web design, etc.

Any chance that dual monitor support (preferably Nvidia) will show up for the next release?  

I think I speak for many people when I issue a plea for dual monitor support that is built into the OS or at least something that works as it should!

---

### Post by IYY on 2006-03-27
I don't know what you're talking about. Dual monitor support, especially for nVidia cards, works very well and takes less than 3 minutes to configure. Yes, it requires manual editing of a file, but it's only a matter of copy/pasting a couple of lines from the internet.

And why stop at two? Add another video card, and you can have 3 monitors, all at different resolutions and refresh rates if you so desire.

---

### Post by Jason_25 on 2006-03-27
I think you should probably get over not wanting to do it and spend a few minutes on google and on this site looking up how to configure your xorg file.  It's an absolute must to know how to configure it.  Also, Xinerama is built into the OS and has dual display support.  Although Nvidia's dual display does the job for me.  I would be glad to post my xorg file for you that is setup for clone mode, and has commented sections for hdtv out, etc.

Here are some useful links:
[http://www.avsforum.com/avs-vb/archive/index.php/t-546124.html](http://www.avsforum.com/avs-vb/archive/index.php/t-546124.html)

[https://wiki.ubuntu.com/NvidiaTVOut?highlight=%28tvout%29](https://wiki.ubuntu.com/NvidiaTVOut?highlight=%28tvout%29)

---

### Post by lonelypauly on 2006-03-27
Thanks for the links but neither apply to me.  When you mention clone mode, you mean both monitors display the same thing right?  If so, that is not what I need.  I need 2 independent desktops, do you have a config file for that?

---

### Post by Jason_25 on 2006-03-27
Something like this?

[http://gentoo-wiki.com/Twinview_Example](http://gentoo-wiki.com/Twinview_Example)

Also, even though this is for solaris, it's very useful.  Take a look at appendix o if this is not what you want.

[http://download.nvidia.com/solaris/1.0-8178/README/appendix-g.html](http://download.nvidia.com/solaris/1.0-8178/README/appendix-g.html)

---

### Post by IYY on 2006-03-27
> Thanks for the links but neither apply to me. When you mention clone mode, you mean both monitors display the same thing right? If so, that is not what I need. I need 2 independent desktops, do you have a config file for that?

Are you sure you want two independent desktops, or do you want one desktop stretched across two monitors? Both are possible.

---

### Post by KingBahamut on 2006-03-27
Spanning with dual monitors is very doable. 

I dislike using the words "forced to use", nobody is forcing anything. 

However, if you ask the right questions, perhaps you wont be "forced". 
=)

---

### Post by Gordonbp531 on 2006-03-27
[QUOTE=lonelypauly]Until dual monitor support becomes built into Ubuntu (or at least made easier to configure) I will have to stick with XP.  I really like Ubuntu and would much rather use* it*.  I couldn't possibly run it right now if I can't have 2 seperate desktops for GIMP, web design, etc.

Any chance that dual monitor support (preferably Nvidia) will show up for the next release?  

I think I speak for many people when I issue a plea for dual monitor support that is built into the OS or at least something that works as it should![/QUOTE]

You do realise that you can have two or more desktops (workspaces) on the SAME monitor, do you?

---

### Post by lonelypauly on 2006-03-27
Perhaps I should be more clear about what I need.  Sometimes I need GIMP on one monitor and my website project on another monitor.  I need to spread my work across two monitors.  That would be "span" right?  what apps do i need and which config files should i use?  Thanks.

---

### Post by KingBahamut on 2006-03-27
[http://www.ubuntuforums.org/showthread.php?p=842187](http://www.ubuntuforums.org/showthread.php?p=842187)

That work?

---

