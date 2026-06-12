---
title: "&quot;normal&quot; memory consumption?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2007-08-09
Hi, all.

What should "normal" memory consumption be? If there is such a thing.  On my desktop at home, if I have Firefox, Gaim, and Tomboy open, the system monitor tells me that approximately 50% of my memory is being used.  My system specs are as follows:

P4 1.5Ghz
512 RAM
nVidia GeForce 6200

Thanks for your help!  Let me know if any more information would be useful.  When I get home I can likely provide a full list of the processes running.

---

### Post by splintercellguy on 2007-08-09
Linux tends to allocate a majority of your memory space for buffering, but releases it when other applications require. To view actual memory utilization, use the command-line utility top.

---

### Post by Inxsible on 2007-08-09
Which application are you using to see that you memory usage is 50% ?

top ? or the system monitor ?

---

### Post by Inxsible on 2007-08-09
Given that you have 512MB of RAM, i think it would be just about right when you say it uses 50%. 

I have 2 GB of RAM, and when I start up my computer it uses about 300-350 MB. This with bluetooth, GAIM, and nm-applet running. Maybe a couple other apps, that I don't remember right now

---

### Post by Hospadar on 2007-08-09
That sounds relatively normal. If you want to trim down your memory usage you can look into removing stuff like tracker and beagle that run in the system tray, and in general remove or close applications that you don't need to be running.

---

### Post by limberlegs on 2007-08-09
Thanks for all of your replies!  I am using system monitor to keep tabs on things.  I like it because I can have a little icon on my panel to keep my eye on while I'm doing other things.  How do I use top? What are the benefits of using it instead of system monitor?  

So when my system monitor tells me that 50% of my memory is in cache, what does that mean exactly?  Sorry if this is an ignorant question...

---

### Post by igknighted on 2007-08-09
If you use the command 'free' you should get an output like this: ```
[dfitzg@xanserver ~]$ free
             total       used       free     shared    buffers     cached
Mem:        449560     441628       7932          0      76044     103344
-/+ buffers/cache:     262240     187320
Swap:       917496        416     917080

```

Note that it says that my used memory is nearly everything in the top line, but that the total in buffers & cache is high as well.  To find the true amount of memory available to the system, you look at the second line where it subtracts buffers and cache, and about half of my memory is available to the system.

The theory is that you paid for 512mb of ram... shouldn't you use it all?  If you allow the computer to cache data there while the space would otherwise not be used, you can increase the responsiveness of the system (without affecting apps that need more ram to run, as they would just grap the space for themselves and never know).  So while the free ram is reported as being used, it usually is not.

Note: I am using>50% ram because I am running several servers which list 512mb ram as the minimum on one machine, yours should be much less for simple desktop apps

---

### Post by splintercellguy on 2007-08-09
To run top, Applications -> Accessories -> Terminal and type top, or you can press Alt-F2 and type top there. top gives you the memory utilization of all the applications, not the cache (buffer) utilization by the kernel. Cache == buffer.

---

### Post by eentonig on 2007-08-09
These are two boxes I have currently access to.

You can see a disction in Mem between "|", "#" and "*". Only the "|" represents memory that is actually in use.

>  
  1  [________________________0.0%]     Tasks: 119 total, 1 running
  2  [_______________________  0.0%]     Load average: 0.00 0.00 0.00 
  3  [_______________________  0.0%]     Uptime: 00:42:49
  4  [________________________ 0.0%]
  Mem[|||#*******______________________73/2027MB]
  Swp[__________________________0/5679MB]

> 
  CPU[##########*__________________________________17.8%]     Tasks: 177 total, 2 running
  Mem[||||||||||||||#########***********************504/2019MB]     Load average: 0.19 0.58 0.62 
  Swp[|                                              61/3553MB]     Uptime: 10 days, 22:58:21


---

