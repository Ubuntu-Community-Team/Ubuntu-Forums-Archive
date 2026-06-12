---
title: "[SOLVED] Feel like an idiot"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by mongoose_za on 2007-12-28
Hi all,

Damn i can see i'm not the only one who's started a thread like this. BUT SERIOUSLY!!!
It's to much, i've only had Ubuntu for a day and i've spent all day trying to get my Ati drivers loaded. I'm not even sure if it's done properly cause i don't know anything. Staring at a screen on 60hz all day is enough to make anyone want to to just weep.

Not sure what the point of this post is.  just to vent maybe..
Sigh...

---

### Post by Tyke91 on 2007-12-28
what methods have you tried so far? My dad has an ATI card, and when we wanted to install his drivers on Ubuntu, we lucked out and it was easily done in the restricted drivers manager. 

Have you tried using the program ENVY?

---

### Post by overdrank on 2007-12-28
> **mongoose_za said:**
> Hi all,

Damn i can see i'm not the only one who's started a thread like this. BUT SERIOUSLY!!!
It's to much, i've only had Ubuntu for a day and i've spent all day trying to get my Ati drivers loaded. I'm not even sure if it's done properly cause i don't know anything. Staring at a screen on 60hz all day is enough to make anyone want to to just weep.

Not sure what the point of this post is.  just to vent maybe..
Sigh...

HI and a good start would be to tell us the graphics card model and I see you are running feisty correct?
This link may help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by stijngysemans on 2007-12-28
I had an nVidia card and I pressed the "autoconfigure" button on my LCD panel: the screen configured and adapted itself to the new refersh rate.

---

### Post by PPAAUULL on 2007-12-28
Don't worry about havinf a graphics card problem they are among the most common. I infact spent a week trying to get my drivers loaded only to find out my card was not supported and all that time was a waste, or was it.... in that week I spent more time in the terminal and reading how everything worked then anyone should ever do. I am sure you will get the help you need and that you will learn a lot about Ubuntu by just getting your card working, as long as it isn't a radeon 9250!!! :p

---

### Post by r4ik on 2007-12-28
> **mongoose_za said:**
> Hi all,

Damn i can see i'm not the only one who's started a thread like this. BUT SERIOUSLY!!!
It's to much, i've only had Ubuntu for a day and i've spent all day trying to get my Ati drivers loaded. I'm not even sure if it's done properly cause i don't know anything. Staring at a screen on 60hz all day is enough to make anyone want to to just weep.

Not sure what the point of this post is.  just to vent maybe..
Sigh...

Don't be to hard on you're self i know the feeling you will get there, heads up ! :popcorn:

---

### Post by Paqman on 2007-12-28
> **Tyke91 said:**
> 
Have you tried using the program ENVY?

I'd second that, [Envy](http://albertomilone.com/nvidia_scripts1.html) is generally the easiest way to get yourself out of graphics driver hell.

---

### Post by mongoose_za on 2007-12-28
haha thanks guys. fast replies, just what i need to keep motivated. OK so i've taken a break and going to have ago later again with the ATi card. 

Here's some info
Using the ATI Radeon 9600XT Sapphire 
I was using 2 guides to try install it [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
and some FAQ on the actual ATI website. It was a combination of the two, when some commands were not working from the one guide i switched to the other. Probably not a good idea...
I'm noob.

I think the my biggest problem is a lack in understanding in how Linux actually works. Not having .exe files really sucks to a degree. All of a sudden i'm supposed to type random commands into something called a terminal. But.. persistance. I'll give ENVY a shot.

---

### Post by philinux on 2007-12-28
From reading on here envy is the best method.

---

### Post by dstew on 2007-12-28
> I think the my biggest problem is a lack in understanding in how Linux actually works.A good introductory tutorial for all Linux (not just Ubuntu) can be found [here.]("http://www.linux.org/lessons/")

---

### Post by r4ik on 2007-12-28
Like suggested and you have not installed the drivers yet try Envy,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

ATI also.

Good luck !

---

### Post by mongoose_za on 2007-12-28
haha i thought i had it,:popcorn::lolflag:
but i did the impossible.. i crashed linux... sigh..
i realised that i had installed the ATI drivers installed but i re instaleld them using ENVY anyway(Thanks for the suggestion, good program)
So the MONITOR was the problem (thanks overdrank! [https://help.ubuntu.com/community/Fi...esolutionHowto](https://help.ubuntu.com/community/Fi...esolutionHowto)). I followed the guide and figured that i could manually change my screen settings, getting the actual refresh rate settings from the manual. I was editing sudo gedit /etc/X11/xorg.conf 
      BUT
after i saved, linux won't boot using the GUI. It puts me into the Terminal.
Is it the end for me or :(can one edit the xorg.conf via the terminal?

---

### Post by overdrank on 2007-12-28
> **mongoose_za said:**
> haha i thought i had it,:popcorn::lolflag:
but i did the impossible.. i crashed linux... sigh..
i realised that i had installed the ATI drivers installed but i re instaleld them using ENVY anyway(Thanks for the suggestion, good program)
So the MONITOR was the problem (thanks overdrank! [https://help.ubuntu.com/community/Fi...esolutionHowto](https://help.ubuntu.com/community/Fi...esolutionHowto)). I followed the guide and figured that i could manually change my screen settings, getting the actual refresh rate settings from the manual. I was editing sudo gedit /etc/X11/xorg.conf 
      BUT
after i saved, linux won't boot using the GUI. It puts me into the Terminal.
Is it the end for me or :(can one edit the xorg.conf via the terminal?

Ok from the command line try and reconfigure your xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
```  or you can use ```
startx
``` Hope this helps and good luck!

---

### Post by mongoose_za on 2007-12-28
OVERDRANK YOU ROXXORS!! IT WORKED!
Never been happier to see my 60hz GUI back in action.
Ok time to try the screen thing again.. following that guide.

but overdrank the command you gave me.. has it now overridden my previously installed ati drivers? And how would i check for myself what i have installed and which compnents are part of my machine?

Thanks for all your help.

---

### Post by overdrank on 2007-12-28
> **mongoose_za said:**
> OVERDRANK YOU ROXXORS!! IT WORKED!
Never been happier to see my 60hz GUI back in action.
Ok time to try the screen thing again.. following that guide.

but overdrank the command you gave me.. has it now overridden my previously installed ati drivers? And how would i check for myself what i have installed and which compnents are part of my machine?

Thanks for all your help.

Hi and yes that command reconfigures your xorg (graphics). You can few your xorg  and see what driver is being used with the command ```
cat /etc/X11/xorg.conf
```

---

### Post by mongoose_za on 2007-12-28
Wow i got the screen at the right refresh rate.
Got my drivers working.
Thank you all and especially OVERDRANK
Problem Solved:)

---

### Post by overdrank on 2007-12-28
> **mongoose_za said:**
> Wow i got the screen at the right refresh rate.
Got my drivers working.
Thank you all and especially OVERDRANK
Problem Solved:)

Great, really glad to hear. Please mark the thread solved under thread tools. Thanks and good luck! :KS

---

