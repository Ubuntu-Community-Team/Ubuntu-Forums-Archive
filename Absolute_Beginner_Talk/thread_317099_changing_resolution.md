---
title: "changing resolution"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by j002 on 2006-12-11
I can't do any resolution other than 800x600 and 640x400 in Ubuntu.

I assume that it doesn't recognise my video card because its on an expansion card rather than embedded ?

Yes I know there's a help page on this site but its as clear as mud.

What is the linux command to probe the video card and install it ?  A generic driver would be fine as long as I can get 24-bit colour and a higher resolution.  This res. is no good because the bottom bar covers up "OK" or "Forward" in some windows (like sound prefernces for instance).

---

### Post by chalex on 2006-12-11
You can try typing in a terminal:

sudo dpkg-reconfigure xserver-xorg

Select all the defaults except for the screen about resolutions; there just select the res you want.

The alternative is to manually edit /etc/X11/xorg.conf

---

### Post by j002 on 2006-12-12
Doesn't work.

xorg.conf shows 1024x720 as the default resolution for a "Generic monitor" (the probe will not recognise my very common monitor (ViewMaster)), but it will NOT display this resolution.

---

### Post by neemz on 2006-12-12
Can you open a terminal and run this command please?
lspci 

and paste the results in the window for us to see, this way we can discover what kind of graphics card you have.

---

### Post by j002 on 2006-12-12
it's a Cirrus Logic GD5446.  It can recognise the video card, just not the monitor.

---

### Post by neemz on 2006-12-12
Right.

In these situations more information = more chance of someone chiming in with the correct answer. If you attach your /etc/X11/xorg.conf I will see if I can edit in the correct values for that particular monitor for you.

---

### Post by j002 on 2006-12-12
I don't have internet, I'm at the council library.

I'm just about to look up the monitor, but why won't it display the higher (default) resolution ?  The Generic Monitor in xorg.conf should be able to display 1024 x 720 ?

---

### Post by j002 on 2006-12-13
Okay, here's the xorg.conf file, for what its worth :

(its a cut and paste copy, the original is read only and I didn't want to change the permissions)

---

### Post by j002 on 2006-12-14
I'm doing this to get the thread further up the list.

Now, I've tried with an IBM C51 monitor and it can't recognise that either.
It can't recognise an IBM monitor !

---

