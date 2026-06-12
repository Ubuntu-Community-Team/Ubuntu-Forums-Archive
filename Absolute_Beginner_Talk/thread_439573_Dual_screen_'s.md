---
title: "Dual screen ?'s"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Shawn Dineley on 2007-05-10
Hello

       I'm trying to set up a edgy system to use as a kind of media player like device (apple tv). For my living room TV. So far I have the sytem up and running.  I got an Geforce4 Mx420 video card with a vga, s-video. and rca outputs. Got the Nvidia driver installed and the monitor and tv showing the desktop (separate x screens). But here are my questions.

1.) Is it possible to just use the Tv? When I tried it I just got a black screen. 
2.) If not, can I set it up so a  program starts and runs (from boot) on the tv only? and the desktop (gnome) runs on the monitor.Plus how?
3.) What should the resolution for the tv be? (Standard def tv) Right now I have it set at 800x600 50hz, and it work but I was wondering if it could like better. Right now it's hard to read the text.

 I'm sure there are more questions but I can't think of any more right  now.

                                                                       So I'll just say 
                                                                       Thank You

---

### Post by nicepants on 2007-05-16
> 
1.) Is it possible to just use the Tv? When I tried it I just got a black screen. 

it is possible, just make sure you're running at under 1024x768, as this is the highest resolution most "normal" tv's can handle. you can use nvidia-settings to enable the tv and disable the primary monitor, this should work.

> 
2.) If not, can I set it up so a  program starts and runs (from boot) on the tv only? and the desktop (gnome) runs on the monitor.Plus how?

this is how i run my primary system, though i just reinstalled and i'm still tweaking it to how i want it. basically if you just want your videos, etc to run fullscreen on the tv you can have your tv and monitor set to different displays and then pass your media player a variable like DISPLAY=0.1 when you run it. i used to do this with mplayer, though like i said i'm fresh back to linux and it's not all set up the way i used to have it yet.

> 3.) What should the resolution for the tv be? (Standard def tv) Right now I have it set at 800x600 50hz, and it work but I was wondering if it could like better. Right now it's hard to read the text.
i believe 1024x768 is the highest a non-hdtv will display, though the fonts will be even harder to read than at 800x600. you can either low the resolution to 640x480 (bleh), or use a larger font size. 

you may also want to look into mythtv, from what you say you want it seems perfect.

---

