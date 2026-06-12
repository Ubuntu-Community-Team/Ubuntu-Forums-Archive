---
title: "Why Does Ubuntu Boot Faster Then XP?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Samanathon on 2007-11-10
After using Ubuntu for a while, I've noticed that it boots much faster then XP did. I realize that's because Linux doesn't have to load the Registry and every single library on on every boot. So, then I would imagine that these files would have to be loaded when the applications are launched (since they're not already loaded into memory) which should mean that these application would be slower to launch (because they have now have to load all of the files) - but this has not been my experience: every application loads relativity fast - and I would dare say faster then their Windows counterparts.

I'm running a Centrino Duo, 1.8Ghz, 1GB RAM, without any processor prioritization or other customization - a standard Ubuntu install.

Any thoughts?

---

### Post by oilchangeguy on 2007-11-10
some people say windows boots faster, some say ubuntu boots faster. i've not timed it. but it's probably something like "beauty is in the eye of the beholder". meaning all things being equal, they're probably about the same, as far as boot time goes.

---

### Post by mikewhatever on 2007-11-10
A lot of windows programs tend to add themselves to the startup list, which could be one reason for slow bootup. Use a boot manager to check what loads in Windows.

---

### Post by osxcapades on 2007-11-10
On my setup, both operating systems boot at about the same speed. I don't usually have very many programs installed on either operating system, however. Also note that I have MySQL running as a Windows service, and my boot time was not noticeably affected.

---

### Post by Tux.Ice on 2007-11-10
its because ubuntus better

---

### Post by bulldog on 2007-11-10
> **mikewhatever said:**
> A lot of windows programs tend to add themselves to the startup list, which could be one reason for slow bootup. Use a boot manager to check what loads in Windows.

...........or try msconfig :)

---

### Post by oilchangeguy on 2007-11-10
> **mikewhatever said:**
> A lot of windows programs tend to add themselves to the startup list, which could be one reason for slow bootup. Use a boot manager to check what loads in Windows.

and go to start, all programs, startup. and delete everything there. reboot. and if you still have many program icons to the left of the clock, right click on the icons, and see if there is a way to not have them load at startup. last but not least, go to start, run, type msconfig. click on the startup tab. and uncheck anything that's not needed (some items may require a google search to find out what they are). reboot, and it should start faster.

---

### Post by bulldog on 2007-11-10
There's an option to hide all what windows thinks it need to boot properly,ofcourse it doesn't  mean you can't disable it,but if this is a wise move..................I have some doubts :)

---

### Post by HermanAB on 2007-11-10
Well, don't try Redhat Linux, since that one beats the sox off XP in the slow boot competition...

The better Linux distributions (Ubuntu, Mandriva and a few others) have implemented a parallel initialization system whereby a lot of hardware is configured at the same time.  Redhat and XP does everything one after the other in a serial fashion.  Much of the hardware initialization time consists of timeouts - waiting for something to happen (or not if the hardware doesn't exist).  Doing these idiotic discovery routines in parallel saves a lot of time.

I configured a laptop for my son with Xubuntu and it boots from cold faster than most X machines take to come out of hibernation.

Cheers,

Herman

---

### Post by sgtbob on 2007-11-10
I have Ubuntu 7.10 on two boxes, both also running Win XP - each OS is on its own HDD and Ubuntu can load in about 1/10 the time it takes Win XP to boot.  Besides, I can see the programs  and data (except for this one program) by opening the 'computer --> then the volume' and can open files, work on them and even save them to the WIN side.  Great OS this Ubuntu....


I have one program that I have to use on Win XP or I would trash it altogether.  Its so buggy and always sloooooooooooooooooooooow to start. I doubt I will make the Vista jump - expense is one issue and all the headaches in comparison to Ubuntu isn't worth it.

Bob:)

---

### Post by oilchangeguy on 2007-11-10
> **sgtbob said:**
> I have Ubuntu 7.10 on two boxes, both also running Win XP - each OS is on its own HDD and Ubuntu can load in about 1/10 the time it takes Win XP to boot.  Besides, I can see the programs  and data (except for this one program) by opening the 'computer --> then the volume' and can open files, work on them and even save them to the WIN side.  Great OS this Ubuntu....


I have one program that I have to use on Win XP or I would trash it altogether.  Its so buggy and always sloooooooooooooooooooooow to start. I doubt I will make the Vista jump - expense is one issue and all the headaches in comparison to Ubuntu isn't worth it.

Bob:)

if xp is slow to start, don't blame it. YOU'VE allowed too much crap to load at start-up.

---

### Post by LaRoza on 2007-11-10
Use the command in Windows, msconfig, to remove any unwanted software. You'll be surprised.

---

### Post by oilchangeguy on 2007-11-10
> **LaRoza said:**
> Use the command in Windows, msconfig, to remove any unwanted software. You'll be surprised.

it's not a command. you go to start, run, type in msconfig, click ok. then click on the start up tab.

---

### Post by r3m0t on 2007-11-10
XP certainly doesn't load every single library when you boot, but it does load all your installed fonts. If you've added a font pack to your Windows, that would definitely make Ubuntu faster.

---

### Post by atlfalcons866 on 2007-11-10
its because all of the files needed to boot on windows are all fragmented:)

---

### Post by stchman on 2007-11-10
> **Samanathon said:**
> After using Ubuntu for a while, I've noticed that it boots much faster then XP did. I realize that's because Linux doesn't have to load the Registry and every single library on on every boot. So, then I would imagine that these files would have to be loaded when the applications are launched (since they're not already loaded into memory) which should mean that these application would be slower to launch (because they have now have to load all of the files) - but this has not been my experience: every application loads relativity fast - and I would dare say faster then their Windows counterparts.

I'm running a Centrino Duo, 1.8Ghz, 1GB RAM, without any processor prioritization or other customization - a standard Ubuntu install.

Any thoughts?

I find that a fresh install of XP is a fast boot.  What happens is that after a while XP's registry gets corrupted and the OS becomes more bloated.  SO after a while XP goes from snappy to slow.  I have not seen this using Ubuntu.

---

### Post by badguyanil on 2007-11-10
jud for the records... there is an exact opposite thread topic posted as  Why Does Ubuntu Boot Slower Than XP?"...lolz..any new user sould be confused!!! 

[http://ubuntuforums.org/showthread.php?t=609300](http://ubuntuforums.org/showthread.php?t=609300)

---

### Post by devnoob on 2007-11-11
I'm finding my UbuntuStudio 7.04 box boots faster than XP, and I used WUBI to install that to a 15GB virtual.disk file!  Kinda sad, in a way.  I'm about to install Kubuntu 7.10 on my main PC on one of my 80gb sata drives on my "fakeraid" controller and see how much faster that is than the 'virtual disk box' :D

/dev/noob

---

### Post by LaRoza on 2007-11-11
> **oilchangeguy said:**
> it's not a command. you go to start, run, type in msconfig, click ok. then click on the start up tab.

You can also do it in the command line, the "run" gui is just a shortcut to that.

---

