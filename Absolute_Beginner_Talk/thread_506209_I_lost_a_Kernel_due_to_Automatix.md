---
title: "I lost a Kernel due to Automatix"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-07-21
Hi,
 Yes you all told me so, but anyways, my GUI (Xserver) broke down on one kernel after trying to install some programs with Automatix. It doesn't take that much with my ATI X-1650 video card to breakthe GUI anyways and other things have "broken" it too. But I REALLY need some advice.

Th point of this thread for me is to get advice on whether to change or reinstall anything. Here are my facts:

-When I choose the second,15 (as opposed to 16) kernel, I STILL have my graphic desktop/interface. Everything still works there. So could this serve as my kernel and I could just ignore the broken kernel?

- I used the Envy program to get my correct 1680 x 1050 resolution; it's the ONLY way I've EVER gotten my correct resolution to come through and even with Envy, it doesn't always work. I have to install it right after installing Ubuntu when everything is fresh and I'm just getting my online connection.  I say this to point out that to try and "fix" all this and still keep my current desktop with all my programs etc is almost impossible.

So what should I do? Just go with the kernel that works and thank my lucky stars? Or reinstall everything (AGAIN...:() ? I hope someday. they really fix this.

Many Thanks for any assistance, ...Frank B.

---

### Post by testube_babies on 2007-07-21
"Automatix2 is a proprietary script that tries to install some software, and often fails and breaks systems. The Ubuntu community doesn't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to install a fresh copy of Ubuntu."

So...you could either reinstall or just use what works.  Successfully roubleshooting Automatix problems is near impossible.

Personally, I would reinstall.  But if you can do everything you want to with the older kernel, I don't see any reason why it's necessary.

And if you ever find yourself needing an easy way to install software the official way, go to [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by Zzl1xndd on 2007-07-21
What you might wanna try is running Envy from the command line in almost all cases this has fixed a broken xserver for me.

---

### Post by gn2 on 2007-07-21
Lots of help with Automatix here: [http://www.getautomatix.com/forum/index.php](http://www.getautomatix.com/forum/index.php)

If it was me I would sell the ATI card on ebay and get an NVidia instead......

---

### Post by bigfox on 2007-07-21
Try typing this at a command prompt.

sudo dpkg-reconfigure -phigh xserver-xorg

It restores the X server to a default config.

You will have to re configure 3D acceleration after that.  Try the Restricted Driver Manager.

---

### Post by Brightbelt on 2007-07-21
Thanks guys, for the tips... I'm VERY familiar with this:

```
sudo dpkg-reconfigure xserver-xorg
```

And I'm also familiar with the "-phigh" part which you can put in there. I can get my system back to Vesa this way but the highest resolution I've EVER gotten from this is 1280 x 1024 and that does not work for my wide-screen monitor. 

I would like to ask TweakedEnigma, if you're still there, How to I install Envy from the command line?
Is it this?
```
sudo apt-get install envy
```???

Because really, that's the crux of this issue: that in the past it has taken a full reformat/reinstall of Ubuntu to get my resolution back to square. And even then, Envy does NOT work perfectly 100% of the time.

Thanks for any further clarification. My tendency at this point (since I can't even count the number of times I've reinstalled Ubuntu...:)) is to just use what works and be patient. The ATI fix may come through someday when we least expect it. 

Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-07-21
Also, I DO have an Nvidia GeForce 7300 LE card I could try again. BUT,...I tried that once and I could not get my resolution above 1280 x 1024. And I read many other posts from people who have NOT found a solution for that card as well. 

If anyone could recommend a good card that will enable me to use Beryl/Compiz, PLEASE tell me!!! I would want it to be compatible with Vista as well if at all possible. I know that's asking a lot but :)

Many Thanks for any tips here as well,....Frank B.

---

### Post by forestpixie on 2007-07-21
you get envy here 

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

have no idea how it works though - I got mine to work without.

this is his thread

[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by misfitpierce on 2007-07-21
ENVY didnt work first time for me for ATI card I guess cause I had restricted... I installed...rebooted... removed... rebooted... installed and rebooted and waalaaa

---

### Post by Brightbelt on 2007-07-21
Thanks for the help guys, but with all due respect, please read the posts more carefully before replying. I've mentioned several times that I've already used Envy successfully....the point is that it ONLY seems to work when I install it  fresh just after a fresh Ubuntu feisty install.

And TweakedEnigma recommended installing ENVY FROM THE COMMAND LINE. Th implication is that installing Envy from the command line might work more efficiently and I could get results without having to reformat and start from zero again etc. That's what I want to learn more about. I have already installed Envy many times using the Deb package.

Again Many Thanks for replying. ....Frank B.

---

### Post by Zzl1xndd on 2007-07-21
> **Brightbelt said:**
> Thanks for the help guys, but with all due respect, please read the posts more carefully before replying. I've mentioned several times that I've already used Envy successfully....the point is that it ONLY seems to work when I install it  fresh just after a fresh Ubuntu feisty install.

And TweakedEnigma recommended installing ENVY FROM THE COMMAND LINE. Th implication is that installing Envy from the command line might work more efficiently and I could get results without having to reformat and start from zero again etc. That's what I want to learn more about. I have already installed Envy many times using the Deb package.

Again Many Thanks for replying. ....Frank B.

I said you might wanna run it from the command line, I was assuming you already had it installed. If you do its just Envy -t in the kernel with the broken Xserver.

---

### Post by Brightbelt on 2007-07-21
OK, Thanks TweakedEnigma. I stand corrected.  :)

Given that, I guess the question still stands: Will running Envy from the command line make a difference as to its performance? That is, would it work better than running it thru the GUI so as to prevent me from having to reformat and reinstall?

Thanks for helping out and following up, Frank B.

---

### Post by Zzl1xndd on 2007-07-21
> **Brightbelt said:**
> OK, Thanks TweakedEnigma. I stand corrected.  :)

Given that, I guess the question still stands: Will running Envy from the command line make a difference as to its performance? That is, would it work better than running it thru the GUI so as to prevent me from having to reformat and reinstall?

Thanks for helping out and following up, Frank B.

It should Fix your Xserver for that kernel and have you back into your Gui, other then your xserver being broken what else is wrong as thats not normally a reason to format and reinstall.

---

### Post by Brightbelt on 2007-07-21
Well I tried running Envy from the command line in Safe mode but it did not bring back my GUI. I get the same black screen on startup. :(

Again, if anyone knows of a video card that excels with Ubuntu Linux, (and is supported for Beryl), I'd love to hear about it. 

Many Thanks, Frank B.

---

