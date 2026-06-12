---
title: "Screen resolution &amp; input language problems"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2006-11-04
Hello to all of you !

I'm quite new to Ubuntu and I'm very pleased with it. I want to slowly move on to Linux and abandon the world of M$.

Until now I have encountered a few problems but I managed to resolve them, mainly by reading this forum, which is a really, really great thing. Congrats!

My first problem is that I'm kind of used with high screen resolution and the classical 1024 x 768 @ 75 Hz (which is the highest I get by default) just won't do for me. I'd like to be able to use 1280 x 1024 and I don't know how to do that. I took a look in my repositories and installed the "Resolution switcher" utility (it goes under Applications), but when I launch it I can only switch between existing screen resolutions and I cannot add a new one. My monitor surely supports the 1280 x 1024 resolution, I can get it under WinXP. I also have a video card: it's nVidia GeForce MX 4000 and my hunch is that my problem is somehow related with the driver for my video card, which I failed to find. Could someone please tell me where I might download the appropriate driver from ?

My second problem is that sometimes I need to write "official" documents which need my native characters (Romanian), and I don't know how to switch between input languages. Although I added the input language I need from System -> Preferences -> Keyboard... :oops: I don't know how to switch between them.

Could anyone be kind enough and give me a hand, please ? :)

---

### Post by Ecthelion on 2006-11-04
For your resolution problems you should reconfigure your xserver...

```
sudo dpkg-reconfigure xserver-xorg
```

But first read a bit about it because if you do a mistake you'll have to find a solution without using your pc...
Live cd can be usefull be still you might want to avoid making mistakes

There's a handy keyboard switcher that you can add on your top panel

right-mouse button on it , then add to panel
then search the keyboard switcher and add it...

hope this helps

EDIT: 
Before you do anything about your resolution problem, backup your Xorg.conf..
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by LLRNR on 2006-11-04
Thanks, Ecthelion ! 

The language switcher is ok now, and for the resolution problem I backed-up my xorg.conf, I ran the xserver-xorg, I selected from the list the resolution I want and after restart, I didn't get 1280 x 1024 as I asked, but a lower one with an awful refresh rate... well that's alright guess I don't want to kill my monitor after all (it's a 17" one), so I'll just stick with the 1024 x 768 for now.

To be more specific, is there any place where I can get nVidia drivers for Linux or they don't exist at all and the only way to configure the display is running dpkg-reconfigure xserver-xorg, as Ecthelion pointed out ?

---

### Post by Ecthelion on 2006-11-04
You can use step 2 of [this]("http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl") HOWTO

I used option 2, works fine

If you dont want the beta version, google for "nvidia edgy" and I'm sure you'll find a lot of good stuff after some searching

EDIT:

You can also use one of the nvidia driver install links that are on that howto

---

