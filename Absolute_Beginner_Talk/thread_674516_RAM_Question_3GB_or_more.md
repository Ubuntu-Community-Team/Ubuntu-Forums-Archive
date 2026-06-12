---
title: "RAM Question: 3GB or more?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-21
I just switched to Ubuntu (love it!) at home on my Dell Optiplex GX620, with 1GB of RAM.

I want to improve the performance somewhat since having multiple desktops open is causing my processor & fan to go crazy...I can get an additional 2GB for around $50. I'd be willing to buy a bit more but from what I've googled it looks like getting more than 4GB working under Gutsy 32-bit desktop is either tricky or won't work (not sure).

So I guess I'm looking for people who have done this - added 3GB or more of RAM - and their advice for doing so. Thanks!

---

### Post by jleaker01z on 2008-01-21
More RAM is never a bad thing.  Just make sure you motherboard supports it.  Some top out at 2gb.

---

### Post by jleaker01z on 2008-01-21
Oh and as for how, its a matter of seeing how many open slots you have for memory, buying the correct kind, and sticking them in the slot(s).  You won't have to do anything within Ubuntu to get it to recognize it.  I don't know anything about a 4gb maximum tho so I can't help you there.  I use 1gb and it runs considerably faster than XP.  Good enough for me. ;)

---

### Post by Tatty on 2008-01-21
4GB is the maximum possible amount of RAM you can use with a 32-bit operating system.
This is simply because 32-bits can only give you enough memory-addresses to account for 4GB of data  (2^32 = 4,294,967,296).
To use more than that you will have to start using a 64-bit OS which will allow you to use up to 8 terrabytes of RAM.


But lack of RAM shouldnt cause your CPU to work harder.  It might cause your Hard Drive to start working harder because if you run out of RAM then it will start using your Hard Drive instead.  As your hard drive is much slower than RAM, this will slow your computer down considerably,  But it shouldnt (as far as im aware anyway - im no expert, lol) affect your CPU.

What do you use your computer for exactly?  Perhaps you need to look at upgrading your CPU?  But i couldnt really give you any advice on doing that as i have never done it myself.

---

### Post by Paulmd on 2008-01-21
> **jjsonp said:**
> I just switched to Ubuntu (love it!) at home on my Dell Optiplex GX620, with 1GB of RAM.

I want to improve the performance somewhat since having multiple desktops open is causing my processor & fan to go crazy...I can get an additional 2GB for around $50. I'd be willing to buy a bit more but from what I've googled it looks like getting more than 4GB working under Gutsy 32-bit desktop is either tricky or won't work (not sure).

So I guess I'm looking for people who have done this - added 3GB or more of RAM - and their advice for doing so. Thanks!


This computer supports a maximum of 4GB ram. But read the Note about "Addressing Memory With 4-GB Configuration." It applies to all 32 bit OSes.

[http://support.dell.com/support/edocs/systems/opgx620/en/ug/A02/memory00.htm#wp1105370](http://support.dell.com/support/edocs/systems/opgx620/en/ug/A02/memory00.htm#wp1105370)

I think, also, that this computer only supports 32-bit processors.

[http://support.dell.com/support/edocs/systems/opgx620/en/ug/A02/mtspecs0.htm#wp1133451](http://support.dell.com/support/edocs/systems/opgx620/en/ug/A02/mtspecs0.htm#wp1133451)

---

### Post by jjsonp on 2008-01-21
Yes, I believe it is a 32-bit processor. But it's a P4 3GHz so it's not especially slow or anything (single core though I think).

As far as the 'working' of the CPU...all I know is that since I switched from XP to Ubuntu about two weeks ago I can hear the fan in my PC much more; right now it is whirring like crazy. It really spins up when I open certain apps (like Konqueror, GoToMyPC, or more than a couple of desktops). I'm hopeful that adding RAM will help alleviate this...aside from the slowdown in responsiveness the sound of my fan getting louder and louder is annoying.

---

### Post by jjsonp on 2008-01-21
Tatty: all I can tell you is that on my work PC when I switched from 2GB to 6GB the performance improvement was unbelievable. No more waiting for apps, no more hanging; everything just starts up immediately. I can have dozens of windows/apps open (and this is on XP 64 bit), whereas before at some point I'd hit a wall and things would slow to a crawl.

So I'm hopeful that upping the RAM on my home machine will, a) slow down the incessant loud whirring of my fan and, b) speed up response time on opening new windows, even if I've already got a dozen open on multiple desktops.

---

### Post by A4006 on 2008-01-21
I do not think that buying more RAM would help with your CPU fan problem in the slightest.  You might want to see if your BIOS have options for adjusting the fan RPM's (mine do) before you go and spend money.  Plus, 1 GB of RAM is plenty for normal usage of a PC, especially with Ubuntu.  If you are determined to buy something, you could always look into a newer, quieter CPU fan and heatsink ([http://www.newegg.com/Store/SubCategory.aspx?SubCategory=574&name=CPU-Fans-Heatsinks]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=574&name=CPU-Fans-Heatsinks") has quite a selection).

---

### Post by Paulmd on 2008-01-21
> **A4006 said:**
> I do not think that buying more RAM would help with your CPU fan problem in the slightest.  You might want to see if your BIOS have options for adjusting the fan RPM's (mine do) before you go and spend money.  Plus, 1 GB of RAM is plenty for normal usage of a PC, especially with Ubuntu.  If you are determined to buy something, you could always look into a newer, quieter CPU fan and heatsink ([http://www.newegg.com/Store/SubCategory.aspx?SubCategory=574&name=CPU-Fans-Heatsinks]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=574&name=CPU-Fans-Heatsinks") has quite a selection).

I would concur. Fan noise isn't going to be affected in the least by RAM.

However, you won't find a compatible fan for a Dell on Newegg, I don't think, Not without some modification. The Fan connector on a Dells are usually special. I can't tell for sure from here, but it usually turns out to be the case. Check the connectors.

[http://support.dell.com/support/edocs/systems/opgx620/en/ug/A02/mtprcsr0.htm#wp1142453](http://support.dell.com/support/edocs/systems/opgx620/en/ug/A02/mtprcsr0.htm#wp1142453)


What Will affect fan noise is CPU usage. Programs that run the cpu at a higher duty cycle generate more heat, and when you get more heat, the fan runs faster, and therefor louder.

Disabling hyperthreading (in the bios) can reduce the amount of heat generated, for a small penalty in performance.

Cleaning out the dust can help too. Dust insulates, and the processor can't cool properly if the heatsink is coated with dist. The fan, of course responds to the increased heat by running faster, in an attempt to bring down the temperature.

---

### Post by jjsonp on 2008-01-21
A4006 & Paulmd: thanks for the tips; you may be right. However given my experience with my work PC and its tremendously improved ability to handle multiple tasks after I tripled the RAM I wonder; it may be that the CPU works harder when there's insufficient RAM because it has to shuttle more bits back and forth to virtual memory? All I do know is that my fan never ran like this at home for the past two years on XP, so somehow my CPU is working harder than it used to.

Since I can pick up 2GB for $50, that seems like the cheapest/easiest thing to try to improve performance. I'll post back after I do so to let you know if it has any effect on the fan speed when I'm doing intensive tasks.

---

### Post by finer recliner on 2008-01-21
> **jjsonp said:**
> A4006 & Paulmd: thanks for the tips; you may be right. However given my experience with my work PC and its tremendously improved ability to handle multiple tasks after I tripled the RAM I wonder; it may be that the CPU works harder when there's insufficient RAM because it has to shuttle more bits back and forth to virtual memory? All I do know is that my fan never ran like this at home for the past two years on XP, so somehow my CPU is working harder than it used to.

Since I can pick up 2GB for $50, that seems like the cheapest/easiest thing to try to improve performance. I'll post back after I do so to let you know if it has any effect on the fan speed when I'm doing intensive tasks.

the CPU does not work harder if virtual memory is in use. the CPU will simply have to wait longer while the next instruction is fetched. this means wasted clock cycles of the CPU doing nothing while waiting. if virtual memory is being used, the HDD will be going crazy, not the CPU. 

to see how much swap space you're using (virtual memory) type this command at the terminal:
```
free
```

and next time you're fan starts getting noisy, or you suspect heavy CPU load, type this command to see which application(s) is using the most resources:
```
top
``` 
(type 'q' to quit when finished viewing the results

---

### Post by newbeeman on 2008-01-21
Just as a matter of interest on noisy fans. My machine works in a rather dusty environment, after a while the fans get noisy, especially when I'm transcoding.
Give it a blow out with compressed air, making sure you stop the fan blades from whirring in the air stream. Quiets mine down.

---

### Post by JoshuaRL on 2008-01-21
I would seriously look at your video card.  If it isn't configured correctly then it will cause your processor to do the work it's supposed to do.  Try:

```

glxinfo | grep direct

```

That will say whether direct rendering (3D hardware acceleration) is turned on instead of indirect rendering (doing all the heavy lifting through the processor).

---

### Post by jjsonp on 2008-01-21
finer recliner: thanks. I just ran those...WTF is hogging all my memory?

"free":
Mem:
Total: 1034188
Used: 735444 (buffers/cache 372188)
Free: 298744 (buffers/cache 662000)

Swap: 
Total: 3028212
Used: 0
Free: 3028212

"top":
firefox-bin
xorg
init

I opened up System Monitor, which I believe shows the same thing, and it's showing Firefox as using 128MB, which isn't unusual on Windows anyway. But the next largest is the deskbar applet with 21.7MB, a 13.5 (gnome-panel --sm-client-id), a 12.4 (trackerd), and all the rest are single-digits.

I can't see how that adds up to 735MB. Any ideas? Maybe that 372188 in cache is actually available for something.

---

### Post by jjsonp on 2008-01-21
Thanks JoshuaRL...I ran that and it says 'direct rendering: Yes'.

---

### Post by JoshuaRL on 2008-01-21
> **jjsonp said:**
> Thanks JoshuaRL...I ran that and it says 'direct rendering: Yes'.

So that means that your card is working.  The next thing I would try is to go into Settings -> Preferences -> Indexing Preferences and turn off indexing preferences.  That is for a desktop search applet that indexes what you do for faster and better results.  I turned mine off and it dropped CPU and RAM usage a bunch.  Something to try if you don't care about indexing.

---

### Post by Paulmd on 2008-01-21
> **jjsonp said:**
> A4006 & Paulmd: thanks for the tips; you may be right. However given my experience with my work PC and its tremendously improved ability to handle multiple tasks after I tripled the RAM I wonder; it may be that the CPU works harder when there's insufficient RAM because it has to shuttle more bits back and forth to virtual memory? All I do know is that my fan never ran like this at home for the past two years on XP, so somehow my CPU is working harder than it used to.

Since I can pick up 2GB for $50, that seems like the cheapest/easiest thing to try to improve performance. I'll post back after I do so to let you know if it has any effect on the fan speed when I'm doing intensive tasks.

So many factors can change the fan speed.

In the natural course of things, your computer can have gotten dusty. 2 years seems about right for that to happen.

Your applications may have changed from your usage under XP vs your usage under Ubuntu.

Even given identical applications, the OSes behave differently in terms of allocating tasks to the cpu. XP seems to put less load on the CPU when applications are open, but idling than Ubuntu does. 

Adding ram MAY well help, by improving performance, and reducing the amount of TIME the cpu is at 100%. For some applications. Maybe. Less time at 100% may translate to less heat, and possibly the fan won't trigger as often. I wouldn't bet much on it though.


Even really arcane things, like the processor producing more heat as it ages, or the thermal compound drying out and becoming a less efficient means of transferring heat could be a factor. 

Ram's cheap, you'll get a performance boost anyway, It's probably not going to  be a major factor in reducing fan noise, though.

---

### Post by poisonkiller on 2008-01-22
```
             total       used       free     shared    buffers     cached
Mem:        515848     509780       6068          0       3700     187024
-/+ buffers/cache:     319056     196792
Swap:      1510068      34700    1475368

```
How come I'm using most of my RAM (512mb), I just recently turned my computer on (~30min ago)?!

---

### Post by A4006 on 2008-01-22
Well, what applications do you have open?

---

### Post by poisonkiller on 2008-01-22
Nothing big, Opera and aMsn.

---

### Post by stchman on 2008-01-22
> **jjsonp said:**
> I just switched to Ubuntu (love it!) at home on my Dell Optiplex GX620, with 1GB of RAM.

I want to improve the performance somewhat since having multiple desktops open is causing my processor & fan to go crazy...I can get an additional 2GB for around $50. I'd be willing to buy a bit more but from what I've googled it looks like getting more than 4GB working under Gutsy 32-bit desktop is either tricky or won't work (not sure).

So I guess I'm looking for people who have done this - added 3GB or more of RAM - and their advice for doing so. Thanks!

Ubuntu is not THAT much of a memory hog.  I have 1GB and it runs fine.  If you want to go to 2GB then go ahead, but I doubt you will see much of an improvement unless you are running 10 or more apps simultaneously that use lots of memory.

---

### Post by A4006 on 2008-01-22
First, you should try turning off Hyperthreding in your BIOS (if it is even enabled) and then you might want to try adjusting the fan speed in the BIOS also.  Then go and clean your compute out with compressed air, especially the fan and heatsink.  If that doesn't work, then you might want to consider reapplying your thermal paste to your CPU (thermal paste is available at Radio Shack or NewEgg), or just plain upgrading the CPU.  If you have to go as far as buying a new CPU then it probably wouldn't hurt to upgrade your RAM then as well.

---

