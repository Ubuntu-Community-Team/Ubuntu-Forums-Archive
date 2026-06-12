---
title: "How to use the nano text editor with xorg?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by ccaazz on 2007-03-23
> Hey, i have a problem with my pc when i try to install ubuntu, the loader shows the boot screen ok, but once the installation gets past the ubuntu logo with the loading bar, i have a blue and grey screen saying something about xserver faiing.

I am using a dell dimension 1150, with 1 gig of ram, and a 256meg, x600 ati graphics card.

I have gathered that this problem is quite common for ati cards, and have even come accross a solution.


Quote:
1) type: sudo nano /etc/X11/xorg.conf (Remember, Linux is case sensitive)

2) Find the line driver "ati" change it to "vesa" and then press Ctrl+x, then "Enter" to overwrite.

Now You will be able to start the "X", to do it type: startx then "Enter"

3) Now The ubuntu was loaded and you will see a install shortcut in your desktop screen. Well, now just follow the install instruction and setup the system. After you complete the process you will be in a black terminal screen again. Don't worry it just happened because GDM wasn't full loaded and after restart it will not happen again. To restart type sudo shutdown -r "now"  

I complete step number one, and am then taken to the nano text editor.  This however displays a totally blank screen, and i can't find any text in the file.  I even pressed f6 to search the file for the words: "ati" and "driver", but still can't find anything.  I am sure that i must be going wrong here somewhere!

can someone please give me a step by step guide on how to use the nano editor to edit the file? 

thanks!

---

### Post by PartisanEntity on 2007-03-23
If its blank then you are not entering the right path:

/etc/X11/xorg.conf is not the same as /etc/x11/xorg.conf

It would appear that you are entering the wrong path and hence openening a new and empty file.

---

### Post by ccaazz on 2007-03-23
i tried what you said and i still get the same problem

---

### Post by PartisanEntity on 2007-03-23
I would recommend that you download the alternate CD and use that to install Ubuntu if you are having problems with the live cd.

Off the top of my head I can't remember, but I think the live cd has 'verbose' mode, which means a text only installation method, if that is to, try to install Ubuntu using that method.

---

### Post by igknighted on 2007-03-23
are you using "ell" "ell" or "one" "one"?  It should be one-one.  Try subbing gedit for nano, or even vi if you are adventurous (in vi you need to hit i to get into insert mode, escape exits insert mode, and :w[enter] saves the file while : x[enter] quits)

---

