---
title: "Resolution issues with laptop and external monitor (Breezy)"
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by Earthling on 2005-09-23
Hi,
I just downloaded Ubuntu and am not totally new to linux. There are some issues which I would like to ask about. I have a Fujitsi P7010 laptp and need to get the WXGA display working. Does anyone have any idea how to do this with breezy? I have Googled and searched all the forums to try and solve this but the only really useful source is on Hoary and uses a different X11 (I think?) so the config files are not the same. (I tried....it broke and I had to reinstall)
Secondly, I can get the external monitor to display at 1600x1200 but the desktop is too big for the monitor. When I move the pointer the screen scrolls to get to the bits that are off the edge of the screen. It is a native 1600x1200 screen but actually only runs at 1280x1024 resolution with the additional pixels acessible by moving the pointer to the edge of the screen so that that part of the desktop scrolls into view.
The display is a Dell FP2000
Many thanks,
Earthling

---

### Post by mlomker on 2005-09-23
> I just downloaded Ubuntu and am not totally new to linux. There are some issues which I would like to ask about. I have a Fujitsi P7010 laptp and need to get the WXGA display working. 


Have you tried **dpkg-reconfigure xserver-xorg**?  I can't speculate beyond that without knowing the video card information and what driver you are using.

Breezy and Hoary are substantially the same.  A small number of things, such as the name of the keyboard change but that's unrelated to video.

> 
the screen. It is a native 1600x1200 screen but actually only runs at 1280x1024 resolution with the additional pixels acessible by moving the pointer to the edge of the screen so that that part of the desktop scrolls into view.


You might have to do some **modeline** tweaking to get that exactly how you want it.  Modelines can be a lot of trial-and-error.

---

### Post by Earthling on 2005-09-23
[QUOTE=mlomker]Have you tried **dpkg-reconfigure xserver-xorg**?  I can't speculate beyond that without knowing the video card information and what driver you are using.

Breezy and Hoary are substantially the same.  A small number of things, such as the name of the keyboard change but that's unrelated to video.



You might have to do some **modeline** tweaking to get that exactly how you want it.  Modelines can be a lot of trial-and-error.[/QUOTE]
 Many thanks.
Could you tell me how to get back into some kind of command line prompt if X fails to initiate? One of the problems with experimentation is I don't know how to recover apart from re-installing (I said I was a n00b)
thanks again

---

### Post by SilentCacophony on 2005-09-23
You should be able to get a console by pressing control-alt-F2, or see any error messages with ctrl-alt-F1. Ctrl-alt-F7 goes back to X.

---

### Post by mlomker on 2005-09-23
> One of the problems with experimentation is I don't know how to recover apart from re-installing (I said I was a n00b)


If X fails to start a command-prompt is the *only* thing you will get!  

If that happens then just run the reconfigure command again and try some other options.

---

