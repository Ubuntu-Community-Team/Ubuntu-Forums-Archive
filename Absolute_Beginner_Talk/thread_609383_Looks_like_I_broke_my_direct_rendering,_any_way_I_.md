---
title: "Looks like I broke my direct rendering, any way I can fix this?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2007-11-10
Hi all,

A few days ago, I decided to attempt to get the desktop effects to work on my old ThinkPad (T23)  so after reading a few of the threads around here, I thought that if I installed xserver-xgl, my troubles would be over... I know, I know... don't say it. Anyway, it didn't work and now I no longer have direct rendering. I have attached a screenshot of the output of a glxinfo | grep dir and also a screenshot of what I think is the output that I was prompted to find, but I have no earthly idea what to do with it.

Any suggestions?  

Oh yeah, I have uninstalled xgl, but things didn't go back to their defaults and apparently, by installing xgl I either deleted, or overwrote my supersavage drivers. I would really appreciate any advice on how to get back to the default set-up.

TIA

Kent

---

### Post by oskar2000 on 2007-11-11
All you should need to get direct rendering is the right driver for your video card.
So what card do you have and which drivers are you using?

---

### Post by Carbonfish on 2007-11-11
Thanks for the reply Oskar. I have a SuperSavage video card, and I am using the correct driver. I can send screenshots of my settings or terminal output, but I am pretty sure that my settings are correct. Hence the confusion. Also, if you look at the second screenshot that I provided, you will see that the system is trying to use savage_dri.so, but says that there is a problem. When I search for the file savage_dri.so, I find it right where it should be.

Can this driver file have been corrupted, and if so, how do I repair/replace it?  

Thanks,

KC

---

### Post by oskar2000 on 2007-11-12
Look if this applies to you: [http://bugzilla.kernel.org/show_bug.cgi?id=7767](http://bugzilla.kernel.org/show_bug.cgi?id=7767)

If that's your problem the suggested solution is to compile the driver yourself - see the comments.

---

### Post by Carbonfish on 2007-11-14
Thanks for the suggestion, but I went through that with Feisty and got the workaround. The problem is that while the Devs got the savage.ko (and the savage.so) problem sorted out in Gutsy, I went and tried to get the desktop effects running on this thing and overwrote or disable the proper drivers, and rebuilding from the Feisty GIT tree doesn't work for Gutsy, I've tried.

As you can see from the terminal dialog, direct rendering is off for a reason, I just can't figure out what reason.

Oh well, maybe somebody will see this and have a suggestion.

Thanks again for trying. 

KC

---

### Post by Carbonfish on 2007-11-23
Since it seems like quite a few of us (judging from the posts in various forums) had this same issue and nobody seemed to have a solution, I reluctantly took a step backward to Feisty. There just weren't enough benefits to Gutsy to make it worth the instability (freezing, crashing, screwed-up rendering) and lack of support response on the boards. I realize that everyone has different hardware compatibility issues, and that it takes a while for the problems to be identified and updates to be written and released, but Gutsy was significantly diminishing my experience, not to mention interrupting my work flow.

So I did a clean install of Feisty from an ISO that I burned back in June, reinstalled all of my multimedia codecs, etc., and problem solved. No more freezing, crashing, etc., and I have high-speed 3D direct rendering back again.

Just thought that I'd update this thread for the sake of closure.

Cheers,

KC

---

