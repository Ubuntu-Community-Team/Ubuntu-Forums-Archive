---
title: "edubuntu 6.10 screen resolution HELP..."
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by rabideau on 2006-12-18
I hate to be dumb, but luckily it is easy for me to do.

I have just installed edubuntu 6.10 on a Gateway PC and am unable to get the screen resolution to recognize anything beyond 800x600 :confused: 

When I installed ubuntu 6.10 I did not experience the same problem.  Is there an easy fix to this problem?  I've searched the forums and not fiound anything that matches my problem, or if it does, has a response that I am able to understand.](*,) 

Any help is appreciated!:KS 

Pax vobiscum,
...mark

---

### Post by troymcdavis on 2007-01-15
You might have to manually edit your xorg.conf file. I know that sounds a bit frightening, but it's the easiest way I know how to do it. Just to be safe, you should back it up. First, open your terminal of choice and type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
It will ask you for your password and then copy the first file to the second location.
```
sudo nano /etc/X11/xorg.conf
```
In a section labeled "monitors" near the end (use the down arrow and PgDn to scroll), there will be a listing of the resolutions available, yours will probably look like this:
```
"800x600" "640x480"
```
You'll just want to tack your resolution at the beginning. Then hit "Ctrl+X" and then "y" and then you're done! Let us know how that works out for you.

---

