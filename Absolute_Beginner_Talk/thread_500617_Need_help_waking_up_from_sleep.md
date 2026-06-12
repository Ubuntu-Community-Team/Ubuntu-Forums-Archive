---
title: "Need help waking up from sleep"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by applegrew on 2007-07-14
I just now suspended my computer (Kubuntu Fesity on a Laptop). When I tried wake up using the keyboard or a swipe on the touchpad; all the lights in my computer turned on (as it should do when waking up) but the computer never woke up.:( I tried hitting many buttons and even power off button but no response. I had to forcibly shut it down and restart.

I have tried reading the many threads, but they were of no help, except the 'uswsusp' package. I haven't tried this yet. Has anyone tried this. Does this work? Are there any side effects? Is there any better way of fixing it?

---

### Post by rax_m on 2007-07-14
Unfortunately I think suspend/hibernate on laptops is one area where linux is still lagging. I have a Toshiba P100 and suspend hibernate doesn't work well. 

I have installed the uswsusp package and it does the following for me:

Suspend to ram - works but when I recover the sound no longer works
Suspend to disk - seems to work better but I noticed that the CPU/GPU fans no longer work. 

The package also has a whitelist of computers that are known to work. I think there's a link to a wiki on the opensuse site.. sorry but I can't find the link at this moment in time.             

So for me, I tend to either leave my laptop running or shut it down for now. Hopefully with the newer kernels things will improve. 

Rax

---

### Post by freebird54 on 2007-07-14
This a 'left field' thought that crossed my mind.  Try closing and reopening the top (screen) - or manipulating the switch it probably hits.

Apparently some people have had an issue with the switch not 'toggling' properly - and it might be pertinent here...

Disclaimer:  The only laptop I own came with Win98 (barely) so I'm not relating personal experience here! (can't even get a Linux on it yet!)

Good luck!

---

### Post by applegrew on 2007-07-14
Thanks for the replies. I will try to search for the link of whitelist. If I find it I will post it here.

---

### Post by randytuggle on 2007-07-14
I learned a valuabl lesson with my laptop recently. This might help - or it may not...Check your power settings in the preferences. Make sure your laptop is set to operate at a slower setting so as not to overheat the laptop. If it overheats (which you may not really notice at times), it will do all kinds of weird stuff. Run it on a cool setting. I would tell you which one to use, but I am on Windows XP at this time and this is where I found out the problem. I've been bitching about my hard drive for awhile and I found that Acer laptops need to run on cooler settings - or they take a huge crap.

---

### Post by applegrew on 2007-07-14
> **randytuggle said:**
> I learned a valuabl lesson with my laptop recently. This might help - or it may not...Check your power settings in the preferences. Make sure your laptop is set to operate at a slower setting so as not to overheat the laptop. If it overheats (which you may not really notice at times), it will do all kinds of weird stuff. Run it on a cool setting. I would tell you which one to use, but I am on Windows XP at this time and this is where I found out the problem. I've been bitching about my hard drive for awhile and I found that Acer laptops need to run on cooler settings - or they take a huge crap.
You have got me really worried. I can't find or understand the settings u r talking of.

BTW in Power Control->Laptop Battery->Power Control (tab) what does the options userpace and ondemand in Not Powered and Powered stand for? and what does LAV stand for (it is also in that tab)? Also what is the difference between Power Control and Default Power Profile tabs? (Again ) also what is the difference between the options System Power Off and Off in the Button Actions tab?

---

### Post by applegrew on 2007-07-15
Hi,

Here is the link to the white list of computers supported by uswsusp. Goto [http://applegrew.blogspot.com/2007/07/swsusp-or-uswsusp-or-suspend-whitelist.html]("http://applegrew.blogspot.com/2007/07/swsusp-or-uswsusp-or-suspend-whitelist.html")

---

### Post by ReaderRat on 2007-07-15
[quote=applegrew]BTW in Power Control->Laptop Battery->Power Control (tab) what does the options userpace and ondemand in Not Powered and Powered stand for? and what does LAV stand for (it is also in that tab)? Also what is the difference between Power Control and Default Power Profile tabs? (Again ) also what is the difference between the options System Power Off and Off in the Button Actions tab?[/quote]

Do you have the manual for the laptop? If so, try looking it up there.

---

### Post by applegrew on 2007-07-17
Unfortunately my laptop's manual doesn't give any in-depth info about the system. The manual is written for noobs in handlingling computer.:(

---

### Post by ugm6hr on 2007-07-23
> **applegrew said:**
> Hi,

Here is the link to the white list of computers supported by uswsusp. Goto [http://applegrew.blogspot.com/2007/07/swsusp-or-uswsusp-or-suspend-whitelist.html]("http://applegrew.blogspot.com/2007/07/swsusp-or-uswsusp-or-suspend-whitelist.html")

My Acer Aspire 5050 doesn't seem to be there, but I suspend just fine with this (haven't tried hibernate - I never do):
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by applegrew on 2007-07-23
> **ugm6hr said:**
> My Acer Aspire 5050 doesn't seem to be there, but I suspend just fine with this (haven't tried hibernate - I never do):
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)
In this case you should inform the developers about it, so that they can add your model to the white-list, hence you won't need to force s2ram then.

---

