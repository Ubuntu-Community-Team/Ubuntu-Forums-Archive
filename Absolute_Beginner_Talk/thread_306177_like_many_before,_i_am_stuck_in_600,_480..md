---
title: "like many before, i am stuck in 600, 480."
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by meteora184 on 2006-11-24
I am stuck in the installer of UBUNTU because i can't even see the bottom of the screen to click next :-? 

so i tryed changing the resolution, but it only gives me 1 option of 600,480, which it's already in.  so i looked into it and found that it might be that you have to change the BIOS from 1mb to 10, or something like that.  how would this be done?

---

### Post by deadgobby on 2006-11-24
what is your vid card?

---

### Post by meteora184 on 2006-11-24
to be honest i don't know, i just got an old windows 98 computer from a friend, formatted it, and thought that it would be interesting to try out linux.  I got knoppix to work on it before already, so i know its possible.

so how would i find out?

---

### Post by deadgobby on 2006-11-24
Please provide system specs. I am assume that it is a p2 with at least 64 megs of ram.
Gobby

---

### Post by apapadop on 2006-11-24
Sorry, didn't notice the problem was with the installer. How can one delete one's own messages?

---

### Post by CatKiller on 2006-11-24
If you're definitely going to install it, you can use the Alternate cd, which uses a text-mode installer. If, after it's installed, you still have resolution problems you can look at installing drivers or making permanent changes to your xorg.conf then.

---

### Post by Kobalt on 2006-11-24
You must specify the resolutions you want as avaliable in your Xorg configuration. To do so, open command line and type this : 
```
sudo dpkg-reconfire -phigh xserver-xorg
```
Then, select the resolutions you want **with the spacebar**, and then click OK. Now restart X with Ctrl+Alt+Backspace. You should have more resolutions...

Cheerio !

---

### Post by Derek Tomes on 2006-11-24
HOT TIP for when the screen resolution is too small.

You can move a window that is larger than the screen by using the ALT key and clicking on part of the window and moving the mouse.

Been there, done that, feel sympathetic for you!!!  :D

---

### Post by ardvark71 on 2006-11-24
Hi...

As another idea (even if it is kind of a long shot,) try swapping out your monitor and see what happens. I have another system with a Nvidia TNT2 card loaded with Win ME that had the same problem....wouldn't go beyond 600x480. I was about to try different drivers until by chance I swapped monitors for another reason and I gained an additional two or three resolutions off the bat. 

Best regards...

:KS

---

### Post by meteora184 on 2006-11-24
ok well i figured out that alt technique for movigng the window, i will try out your method once its done installing.

---

### Post by meteora184 on 2006-11-24
now that its installed, i tried out the thing in the terminal
sudo dpkg-reconfire -phigh xserver-xorg
and it just gave me a list of options and stuff, i don't know what i would want to pick.

i also kown that there may be a way to change the xorg.config file.

but, everything outside of my user folder is read only, saying that i don't have any permissions.  This is the only username or account on UBUNTU, so i don't know that would mean, you would think that meant i'm administrater.

---

### Post by CatKiller on 2006-11-24
> **meteora184 said:**
> but, everything outside of my user folder is read only, saying that i don't have any permissions.  This is the only username or account on UBUNTU, so i don't know that would mean, you would think that meant i'm administrater.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by meteora184 on 2006-11-24
i'm slowly getting past my problems :P, now i need to set up sound.  how would this be done?

---

### Post by Cardmaster91 on 2006-11-24
if your computer cant support the resolution, b/c its to out of date. i recomend xubuntu, its like ubuntu but for less powerful computers.

---

### Post by CatKiller on 2006-11-24
> **meteora184 said:**
> i need to set up sound.  how would this be done?

In a new thread :) 

The people that might know about your sound aren't necessarily the ones that might read about your graphics.

---

### Post by meteora184 on 2006-11-24
> **CatKiller said:**
> In a new thread :) 

The people that might know about your sound aren't necessarily the ones that might read about your graphics.

don't worry :P i figured it out anyways.

---

