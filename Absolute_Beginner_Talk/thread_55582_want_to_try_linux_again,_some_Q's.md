---
title: "want to try linux again, some Q's"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by yellowband on 2005-08-09
Hello everybody.

a little while ago, i tried linux out by installing Fedore Core 4.  that left a bitter taste in my mouth as it was super frustrating and confusing to use.  I have been reading good things about ubuntu so i thought i woudl at least give it a try. I ahve a couple of Q's before i do though:

1. I need a program that can enlarge my screen.  Fedore core had one built in but it sucked pretty bad. The image was choppy and left artifacts all over the screen, it was unusable.  Now i use zoomtext for windows ([www.aisquiared.com)](www.aisquiared.com)). Is there any software available for ubuntu that works well?

2. I could not grasp the idea of setting up my hardware. Is there a list anywhere where i can check to see if my hardware is supported?  I have 2 other SATA drives formatted with NFTS that i could not get working in fedora core.  I could not figure out how to mount my optical drives either. Also i'm not sure if i even got 3d acceleration working or not.  Are there guides for all of this stuff?

That's all for now. I appreciate any advice andbody could give me. Thanks a lot!

---

### Post by Juergen on 2005-08-09
> I need a program that can enlarge my screen.
In the accessibility-settings there is a 'Magnifying glass' and a screen reader (text to speech). 
I don't use them, though, so I don't know if they work properly.

> Are there guides for all of this stuff?
Look at the Wiki (link at the top of this forum). 
And this: [http://ubuntuguide.org](http://ubuntuguide.org) has loads of info, too.

---

### Post by yellowband on 2005-08-09
thanks for the help juergen.  

If you have time, do you think you could run the magnifier app on your computer and tell me how well/smooth the screen moves around? haha i realize it would be hard to give an opinion if you havn't ever used a screen magnifier, but i'm just trying to find out if its even usable/readable.  If you can't that is cool too, and if anybody else could try it i would really appreciate it.  I'm using a sapphire radeon 9800 SE graphics card.  

I'll also take a look at that wiki about my hardware problems. i did try to seach it for the screen magnifier but nothing came up. 


thanks again.

---

### Post by cnayak on 2005-08-09
Fedora Core 4 is pretty harsh on newbies. Though it is blindingly fast and very polished, it is for the pros. Given the fact that a good number of users have an onboard Intel-chipset based cards, didn't they have the foresight to make  sure audio worked fine out of the box?  How many newbies know about alsa and other stuff?

---

### Post by Juergen on 2005-08-09
> haha i realize it would be hard to give an opinion if you havn't ever used a screen magnifier, but i'm just trying to find out if its even usable/readable.
Well, the readable part was easy - I just took my glasses off ;-)
Contrary to most others you don't want to have font-antialiasing, but other than that I found clear graphics and readable texts.

Handling I can't compare... (and the default-settings are for 640x480, so on my monitor it appeared somewhere in the top/middle. It's intended to cover one half of the screen)

You have several methods to scroll the magnified portion of the screen. 
Bumping the mouse to the border, 'center' (didn't find out exactly how this works), and two other - one of those is 'off', don't know how **that** should work.

BTW: 'gnopernicus' installed a lot of dependencies, but IMHO 2 are missing.
You need to explicitly install 'at-spi' and 'gnome-mag' to get it to work

---

