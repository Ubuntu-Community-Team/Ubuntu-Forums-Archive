---
title: "[SOLVED] Working the kinks out"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Xnyper on 2007-11-15
Hello everyone,

I have been toying with the idea of switching to linux for a long time and... well... here I am.  I installed gutsy, chose the xfce desktop environment and was well on my way.  after some messing around I decided to switch to GNOME because I stumbled upon a tutorial that I wanted to follow, but it was written for GNOME.  That's right, I switched environments because of a tutorial.  Said tutorial set up gnome-terminal to run embedded in the desktop, which I think is pretty cool.  

I've been using it to launch applications because if my fingers are already set up for typing its much simpler to type 'firefox ubuntuforums.org' than to fuss with the touchpad.

My problem is this:  when I run a program from that terminal (or any terminal for that matter)  it runs fine, but half the time the terminal stays in this blank do-nothing space until I close the program--at which time any keystrokes I typed are evaluated as a command.  The other half of the time the terminal window returns me to a ':~$' prompt so that I can play around further.  I know that I can exit that do-nothing space by hitting ctrl-C, but that closes the program that I opened.

programs that behave properly (by which I mean return me to the prompt) include:
Firefox
Ktorrent
programs that prevent me from using that terminal window until they are closed include:
gimp
gplanarity

I assume that there is something I can do to get these programs to run independent of the terminal window that they were launched from.  It would be preferable if I could configure it so that I didn't have to type anything extra, edit some file somewhere, but if additional syntax is the only way, bring it.


Also...

the reason I told you the story about xfce is so I could ask you this question:
Why can't I orient the clock (in the panel) horizontally when it's in a vertical menu?  I encountered this problem in xfce and just installed a program called orage to display the time, which it did properly, but I can't seem to find any alternatives to GNOME's "clock".  Does one exist? if so, how do I go about installing it.

---

### Post by taurus on 2007-11-15
If you want to get a prompt back after you run a program, just send it into background.

```
firefox &
ktorrent &
gimp &
```

---

### Post by markharding557 on 2007-11-15
your terminal is working normaly nothing to worry about
you can open a new terminal tab for each app
you can run a program using a command in the run application box which you can add to the gnome panel
right click on panel select add to panel and you will get a list of things to add

---

### Post by Xnyper on 2007-11-21
> **taurus said:**
> If you want to get a prompt back after you run a program, just send it into background.
That's a handy trick, thanks!  I'll know my CLI stuff one day...

---

