---
title: "Problem... A big one..."
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by ruza on 2007-06-27
First of all I would like to say helo to all ubuntu users. 

And then the problem. . . 

I have NVIDIA mx400 and I installed restricted drivers to use compiz. Everything looks just fine but after 10-30min of using my computer just stops working. Everything but mouse - I can move mouse but I can not do anything with it. 

Please help me. . .

Oh yes I must say that problem has got nothing to do with compiz. Even with compiz turned off the computer crashes after 30min max.

---

### Post by ruza on 2007-06-27
And that happened with other distros to.

---

### Post by hvc123 on 2007-06-27
press crtl+alt + f2 

log in then type  'top'

see whats hanging your machine up probably some rubbish service or apt updates

---

### Post by ruza on 2007-06-27
I can not do that. I tried that but computer is dead and not responding to anything. The only thing I can do when that happens is to restart it.

---

### Post by lamalex on 2007-06-27
so do it before it crashes and keep it visible, then when it happens you can see if some processes is killing you

---

### Post by ruza on 2007-06-27
I tried by looking at active proceses and system monitor. Is that the same? Nothing uncommon happens. And it happens even if I start ubuntu, log in and do nothing.

---

### Post by ruza on 2007-06-27
Do I really have to give up nvidia drivers?
And I just started to get used to compiz...

---

### Post by ruza on 2007-06-27
No one?

---

### Post by moredhel on 2007-06-27
try getting the drivers in another way, like envy.

---

### Post by ruza on 2007-06-27
Ive tried every way of installing drivers envy, manual, and res. dr. man...

---

### Post by ruza on 2007-06-30
Hello. I have already posted this on this forum but I can not find that post here(forgot the post name), so please forgive me for making another post with similar problem. 

My problem is not Ubuntu disto problem. It happens with every distro I tried. that  includes Gentoo and its derivates (Sabayon), Debian (same thing), SUSE, even Puppy linux. I have not tried Mandriva and Fedora but I cannot see why would it make any difference. 

Problem is rather annoying... When I install NVIDIA(restricted) drivers, using any method of installing (manual, restricted drivers manager, even if it comes with distro (like sabayon)), after 15-30 min of using my computer stops working (the best way of saying it without saying anything rude :) ). It does not respond to any command I give to him. Desktop is dead. I can only move mouse but I cannot do anything with it (does not respond to click). Ctrl-Alt-F(n) does nothing. 

Now my hardware confiiguration is rather poor one and I would have thought that was the problem but I know a guy with almost same configuration that has everything working just perfect. 

-NVIDIA GF2 mx400 64MB
-512MB RAM(that guy has 256)

If anything else is relevant to this problem and  I forgot it please say and I will give my best to provide that information. 

And just to add I am terrified that my XP windoze is more stable than linux. I cannot accept that so please help!!!

---

### Post by sad_iq on 2007-06-30
Well to be honest...I have no clue about your problem...could be hardware related...boot from a live cd and try  **memtest** and see if it shows any errors. Another thing you should do is open the case and see if everything is well in it's place. Also overheating can lead to the same result(happend to me with Linux and Windows)...so if you can verify that....well it's worth a try...and make sure there is **no** dust blocking your fans !!! 
 Also overclocking can screw things up sometimes...so make sure you run factory default on processor and GPU, and double check your bios settings.
 And about getting completely blocked(happened to me for overheating reasons) read this link...it should give you a controled reboot(avoid hard reset!!!):
 [http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html)

---

### Post by ruza on 2007-06-30
Makes sence... But that thing does not happen to me on windoze (thing that that annoy me most). I use hardvare defaults. I clean my computer and check my hardware every sunday :) (weah I know that is not normal but I am dust alergic). No overclocking has been done on my computer. 
Opening a window with a lot of colours speeds up the blocking. 

And the only thing i know for sure that it has to do something with refresh rate. 
I had the same problem without NVIDIA drivers when I had my rr low. 
So I tried to rise up my refresh rate by editing xorg.conf. But that does nothing no matter how big is refresh rate it looks like nvidia conf bypassed xorg.conf and editing it just makes no diference.

---

### Post by Jimmyfj on 2007-06-30
It does sound like a faulty RAM block/bank to me. It's not that your system specs are THAT poor, My daughter has an old PII 266 with 192 MB RAM and nVidia G-Force 2 mx400 32 MB, and that computer runs Feisty Fawn just perfect, slow, but perfect.

Since the freeze happens no matter what distribution you try it can't be GNU/Linux at fault there but something in your computer, and you do mention it yourself: You said that it happens every time you install the nVidia restricted driver for your graphics card thus in my view the faulty device MUST be your graphics card and not Linux.

There are a few things that you can try out before dooming your choice of Linux. First, try to enter your computers BIOS and reset this to the factory default settings: Look for this point in the BIOS: "Load BIOS default setup", mark it up and press Enter then save and exit your BIOS to reboot the computer.

Second, enter your computers BIOS once more, go to the Advanced BIOS setup and look for the Graphics Aperture Size setting - This must be the same as the amount of RAM om your graphics card, in your case the value should be set to 64.

Otherwise I'm pretty sure it is your graphics card that is faulty

---

### Post by ruza on 2007-06-30
I never even thought of dooming linux. I guess that updating bios should solve the problem (saw that somewhere). But in windoze I installed that driver and works pefectly that is the thing that confuses me the most. I know that problem is with me not with gnu\linux because I guess I am the only one with that problem... 
So I will post after BIOS update... Wish me luck!

---

### Post by sad_iq on 2007-06-30
Also make sure that the video card and memory sticks are properly plugged in(sometimes they just stick out a little from one side), you should remove them and clean the contact surface with something just to make sure they are dust free!!!
 I had exactly your problem(windows ok .. linux not)...and it was a pain...but reinserting them correctly solved the issue!!!
 Also try looking at the X (and other)logs and see what errors it gives...forgot how to do it with gnome...as i use kde :(

---

### Post by ruza on 2007-06-30
Problem is it does not report any errors...

Is it possible that nvidia drivers somehow bypass xorg.conf settings?

---

### Post by ruza on 2007-06-30
I dismembered the whole computer. I even moved away chips from motherboard. Everything is cleaned. 

And then. I started ubuntu and it all seamed to work for about 15min. Again it froze! I almost threw It through window. HELP! I am desperate!

---

### Post by bapoumba on 2007-06-30
@ ruza: I've merged your other thread in this one.
You can find all the threads you've started or all your posts in the "search" menu (tool bar just below the main forum panel).

---

### Post by ruza on 2007-06-30
Thanks!

---

### Post by alienexplorers on 2007-06-30
Did you try using an older nvidia driver.  I had problems with the newest drivers and had to switch to an older one.  Also did you run memory test to see if your memory chips are OK.  It almost sounds like something in the computer itself is dying.

---

### Post by ruza on 2007-07-01
Well to an older driver... Which one? I thought envy would find the most proper driver for my card...

---

### Post by Raineer on 2007-07-01
ruza - 

Try 97.55, I had some issues with newer drivers and had to backtrack to that one and everything works great now. I **did** also have some intermittent lockup issues among other things.

---

### Post by ruza on 2007-07-02
I have tried almost every driver and it does not help. . . Guess I will be forced to buy new computer. . .

---

### Post by chronic on 2007-07-02
this sounds more like you have a hardware problem that software.

make sure all the fans in your computer are spinning and that your your heatsinks are seated properly on your cpu/gfx card etc.

you should also into the bios and check all your temperatures and make sure they at least around 60-70c max (lower is better) leave it in the bios for a while. with your particular gfx card there is no way to check the temps.

otherwise it is likely to be the power supply or ram and possibly the motherboard.

if you have a spare hard disk reinstall your os and leave everything as defaults, then run an application that will stress the hardware to a degree. if you still have your problem then take it to a computer repair shop.

---

### Post by ruza on 2007-07-03
Looks like I have to buy a new computer... Thats great!!!

---

### Post by RD4UBN2 on 2007-07-03
I'm another Ubuntu newbie, but does it help to know that NVIDIA is also having problems with Windows? I only mention it because I saw another thread here earlier where someone was having big issues with NVIDIA.

I have been considering Linux for awhile, but in just the past two weeks of having increasing instability in my XP have I really been ready for the big leap. My system was doing random shutdowns, with error reporting blaming everything from power supply to software conflicts to RAM. Then it blamed NVIDIA drivers. They were suddenly unsigned. Oh the horror. :-|

So yesterday I followed the link from error reporting and got new ones. And then things got worse. All kinds of programs no longer wanted to cooperate. So I did a recovery. Now the random shutdown issue has stopped. And I am ready to stop the madness and start making my own choices instead of eating what they give me.

So anyway guy, it's probably not just you. I don't think it was the whole of my problem by a long shot. But whatever NVIDIA did recently, doesn't work. Which leads me to ask, what are my other options? Is NVIDIA something I have to work with, or do I have a choice here too?

Best of luck,
Jeannie

---

