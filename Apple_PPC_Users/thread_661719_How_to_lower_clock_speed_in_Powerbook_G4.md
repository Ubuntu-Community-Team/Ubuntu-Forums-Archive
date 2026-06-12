---
title: "How to lower clock speed in Powerbook G4?"
date: 2008-01-08
forum: Apple PPC Users
---

### Post by HanDuo on 2008-01-08
Hi,

I just put ubuntu 7.10 for PPC on my PowerBook G4 / 1Ghz 12". It works but its really getting hot!
While I was running the installation app the fan was off and the PowerBook was getting hotter than ever. I didn't know how to cool it, so I just took some ice out of the freezer, put two bags around and placed it just below the area were the cpu is located. Nice cooling though but not really feasible. 

Since ubuntu is starting from the HD the fan is detected and really - it works but is getting louder and faster then ever (I guess under OSX it's never working with more than 60-70% of the max. speed). 

Even when I just have the OS and the GUI runnin' (no extra Apps activated) the fan gets totally busy just two minutes after I launched the system.
First thing I did was checking the CPU speed which is at 100% all the time. But do I really need 100% speed just for the OS and the GUI? 
Makes no sense to me. Besides: It's no fun to work with a machine as loud as my one when always at max. speed.
Curiously the fan stays off and the Mac is not getting hot when I launch ubuntu from the live-CD.

So, long talk short question: How can I lower the clock speed? Would be good to set the max. clock speed to 90%.

Regarding Linux I am a greenhorn (first time I use it).

Thanks for replies.

HanDuo

---

### Post by Bliepo32 on 2008-01-08
If I understand you correctly, you want to underclock your system. This is possible. Be warned however: underclocking **CAN damage your computer**. **My advice would to replace the fan with a more powerful one**.

If you still want to underclock your system, you first need to read this [overclocking tutorial](http://www.pcstats.com/articleview.cfm?articleID=1804). Next, read about their [underclocking experiment](http://www.pcstats.com/articleview.cfm?articleID=1798). Notice that the temperature drop was minute.

---

### Post by HanDuo on 2008-01-08
Well, changing the fan of a 12-inch PowerBook is quite a task. No real option to me, because I don't like the noise of the fan while I just e.g. read a pdf-document or write some lines of text. Means: I want to quiet that thing and don't make it louder. 

Maybe someone can tell me why my PB is acting normal when running ubuntu from the live-img CD and why it starts bustling when I run ubuntu from HD?

Thanks

HanDuo

---

### Post by nokia87 on 2008-01-08
> **HanDuo said:**
> Hi,

I just put ubuntu 7.10 for PPC on my PowerBook G4 / 1Ghz 12". It works but its really getting hot!
While I was running the installation app the fan was off and the PowerBook was getting hotter than ever. I didn't know how to cool it, so I just took some ice out of the freezer, put two bags around and placed it just below the area were the cpu is located. Nice cooling though but not really feasible. 

Since ubuntu is starting from the HD the fan is detected and really - it works but is getting louder and faster then ever (I guess under OSX it's never working with more than 60-70% of the max. speed). 

Even when I just have the OS and the GUI runnin' (no extra Apps activated) the fan gets totally busy just two minutes after I launched the system.
First thing I did was checking the CPU speed which is at 100% all the time. But do I really need 100% speed just for the OS and the GUI? 
Makes no sense to me. Besides: It's no fun to work with a machine as loud as my one when always at max. speed.
Curiously the fan stays off and the Mac is not getting hot when I launch ubuntu from the live-CD.

So, long talk short question: How can I lower the clock speed? Would be good to set the max. clock speed to 90%.

Regarding Linux I am a greenhorn (first time I use it).

Thanks for replies.

HanDuo

Your problem is that a program is hogging all your cpu power. Can you please paste the information you get when you type ```
top
``` in your terminal?

---

### Post by stream303 on 2008-01-17
> **nokia87 said:**
> Your problem is that a program is hogging all your cpu power. Can you please paste the information you get when you type ```
top
``` in your terminal?

I had a similar issue with my G4 iBook and Gutsy, but it can be two problems.

Indeed, Network Manager was hogging my cpu as verified by TOP  (although now my favorite is to download HTOP).  So I removed Network Manager.

So far so good, but my system was still set to run at max speed of 1.2 ghz.  It ran warmish, but at least now I had no runaway processes and fast spinning fans.

I don't know if this will help Powerbook users, but with my iBook, turning the Powernowd service off, rebooting, and then re-enabling that service seemed to do the trick.  I *love* that cpu-frequency scaling applet for the top panel. :)

---

### Post by Gen2ly on 2008-01-17
you can use the cpufreq tools to scale your processor down.  I'm not sure of the package in ubuntu but it's probably something like cpufreq-tools and cpufreqd.  The scaling can be configured in /etc/cpufreqd.conf.

---

### Post by stmiller on 2008-01-17
remove cpu-freqd is that is installed and then make sure  to install powernowd. You can set the performance mode to conservative and it will stay low...

---

