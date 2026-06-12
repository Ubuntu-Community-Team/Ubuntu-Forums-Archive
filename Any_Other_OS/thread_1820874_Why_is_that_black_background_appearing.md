---
title: "Why is that black background appearing?"
date: 2011-08-08
forum: Any Other OS
---

### Post by brunces on 2011-08-08
Friends,

I've been using Linux Mint KDE 10. As you know, on KDE, when we launch a  program, while it is being loaded, the mouse cursor shows a small  animated icon (it keeps on "jumping") for that specific program.

On the attached picture, I had launched Google Chrome. Notice that we  can see Google Chrome's icon. Actually, it is next to the mouse cursor,  but the cursor won't appear on the screenshot.

Around the Chrome's icon there is a black square, I mean, the icon is  showing a black background instead of a transparency. Why is that  happening? What should I configure here to make that black background  turn into transparent?
 
I've used other KDE distros, even Kubuntu itself (which Mint KDE comes from),  and this had never happened before. The icon had always had a  transparent background.
 
Thanks for your attention, guys. :)

 brunces

P.S.: Guys, if this thread is at the wrong place, please move it to the right section. Thanks.

---

### Post by Kira_Belka on 2011-08-08
... so video card.. driver and theme of plasma

---

### Post by brunces on 2011-08-08
> **Kira_Belka said:**
> ... so video card.. driver and theme of plasma

But when I use Kubuntu, it's the same video card, same driver and same theme of plasma, and everything is OK, normal. What's wrong then? Thanks anyway. :)

brunces

---

### Post by Synoc on 2011-08-08
you can ask here and you may well get an answer. I used Mint for some time and came back to vanilla Ubuntu. Mint makes a good deal of changes from standard Ubuntu or Kubuntu in your case. The people that know this best, are the Linux Mint gurus. they have an IRC channel you can use and usually get better responses since they know their OS better than we do. I recommend later in the day to use it, when they are not at work. That's when I had the best luck. their forums CAN be useful, regrettably, not as helpful as here however. if you cannot fix the problem with their help, bring back what steps you took from their end and we might have a better feel for it.

---

### Post by Perfect Storm on 2011-08-09
Moved to Other OS/Distro Talk.

---

### Post by 23dornot23d on 2011-08-09
> 
I've used other KDE distros, even Kubuntu itself (which Mint KDE comes  from),  and this had never happened before. The icon had always had a   transparent background.
Why they asked about the video card - is just to get basic information .......

When the graphics shows like this ,,,, it can mean that the computer is not using your
graphics card from the drivers ...... so it runs in safe mode .

It helps if you give basic information ...... about your hardware .......

Lets start guessing and see how far we can get ..... from the information you have given
so far,

> 
But when I use Kubuntu, it's the same video card, same driver and same  theme of plasma, and everything is OK, normal. What's wrong then? Thanks  anyway. :smile:
Whats wrong then ?

The video card is probably not being picked up correctly ..... and its running in safe-graphics mode .....
or it could possibly be something to do with the theme ..... but hard to tell as we do not know
anything a bout what you are running yet .......

> 
... so video card.. driver and theme of plasma
The information asked for - is to give people here a clue and a chance to help you ......

---

### Post by brunces on 2011-08-10
23dornot23d, thanks for answering. Sorry, I hadn't understood Kira_Belka's answer before. Now I got it. I thought he (or she, sorry) was telling me the problem was related to those things, but actually he/she was asking me about those things. OK.

Well, video card is SiS Mirage 3 Graphics (671).

I can't tell you about the driver because I don't understand much about this on Linux. All I know is that I use this script to get it installed.

```
#!/bin/sh

sudo apt-get install git xorg-dev mesa-common-dev libdrm-dev libtool

sudo apt-get build-dep xserver-xorg-video-sis

git clone git://github.com/hellnest/xf86-video-sismedia-0.9.1.git

cd xf86-video-sismedia-0.9.1

./configure --prefix=/usr --disable-static

make

sudo make install

sudo reboot
```

The theme of plasma is Oxygen.

Any thoughts? :)

Thanks for your time, guys.

brunces

---

### Post by 23dornot23d on 2011-08-10
Cheers .... 
  There are a couple of more questions now ....  /etc/X11/xorg.conf  

[B]gedit  /etc/X11/xorg.conf  
[/B]
in a terminal will let you see it .......

This file sets your screen and resolution up as well as the graphics driver - if you use one ....  
So after reading this 

Blog post  [http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html](http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html) 

I wondered   1 .... what your screen resolution is ..... ? 

and  2 .... 

if you have a xorg.conf already set up can you post that too please ....

---

