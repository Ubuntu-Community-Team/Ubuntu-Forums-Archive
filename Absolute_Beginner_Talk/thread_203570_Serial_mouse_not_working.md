---
title: "Serial mouse not working"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by PVK on 2006-06-25
Hi all,

I'm absolutely new to Linux, so I thought it was a smart idea to try Ubuntu version 5.10 with the Live-CD. Unfortunately, my mouse doesn't work. It's a serial mouse, located at the COM1-port. I tried the HOWTO at this page 
( [http://ubuntuforums.org/showthread.php?t=3839](http://ubuntuforums.org/showthread.php?t=3839) ), but that didn't work out.
After step 3, I get a message like this: 
"Package 'xserver-xfree86' is not installed and no info is available"
and some other text.

So what do I do now? Thanks in advantage!

PS I hope this thread is in the correct forum?

---

### Post by IYY on 2006-06-25
xfree86 is the old version. Nowdays we use xorg, so the command is:

```
sudo dpkg-reconfigure xserver-xorg
```

If this still doesn't solve your problem, read this thread:

[http://ubuntuforums.org/showthread.php?p=1177046](http://ubuntuforums.org/showthread.php?p=1177046)

---

### Post by PVK on 2006-06-25
Using x-org didn't work, but I'll try the instructions in the other topic. Thanks a lot!

---

### Post by thibeaz on 2006-08-13
well here is what you do
press ctrl+alt+F1. Log in and then type
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup

Then to open a text editor, type
sudo nano /etc/X11/xorg.conf

Scroll down through the file until you find the section for the mouse.
Change the line area that says
/dev/mouse/generic

to read /dev/ttyS0

Note: that 0 is a zero, not a big letter O. I messed that up, and it took me hours to figure out why.

I've also found that you should change to protocol section to read "Microsoft." I've only found this in some help guides, so I'm not sure how neccesary it is.

All you do now is hit ctrl+x to leave the editor, and y to say you want to save, and press enter to save the new file over the old one.

Hit alt-F7 to get back to the mouseless X window.
Hit ctrl-alt-backspace to exit X.
In the console that X exits to, start X again by typing startx&
Serial mouse should now be working.

That was kind of complicated for me, so I just rebooted after saving the file. It worked for me. :)

---

### Post by thibeaz on 2006-08-20
I hope this was helpful too you

---

