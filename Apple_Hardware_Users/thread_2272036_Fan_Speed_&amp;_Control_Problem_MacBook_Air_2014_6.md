---
title: "Fan Speed &amp; Control Problem MacBook Air 2014 6.2"
date: 2015-04-03
forum: Apple Hardware Users
---

### Post by giacomoalbe on 2015-04-03
Hi all, gentle Ubuntu users, 

I recently upgraded my LinuxBox and I decided to switch to Mac because I think they are really good computers and I had a really big deal.
So I bought a MacBook Air, which is recognised by the system as the 6.2model. 

After some days playing around with OSX I become to get tired of all that "macthings" and I wanted to start to be really productive, so I decided to install Ubuntu on top of it (I was missing him, too :) )

The procedure wasn't really painful and after 2 hours I had my Ubuntu Linux fully working (except for the things that are not recognised, but generally Ubuntu runs great)

The only issue I encountered was related to the fan and overall heat control problem.

My Air started silently and then suddently became really hot and the fan started to make it look and sound like an elicopter!

So I installed macfanctld, because I've read that it should have solved the fan and heat probelm (someone reported his mac was "nice and cool").

But exactly after I installed it via ppa the fan went to maximum and never came back from there!
I thought it was a problem of reloading some modules, so I rebooted and soon after Ubuntu loads the GUI the fan go to the maximum and there's no possibility to make them run under 5800 (5800!) rpm.

I installed lm-sensors and I saw that the temp are really high for the usage. 

It's really a mess beacuse I think that Ubuntu is een faster than OSX, but with this problem I'm not really able to work with it (even beacuse the battery should suffer from this energy hungry fan usage).

Can anyone help me? Is there a way to solve this problem with heat? Maybe some conf file that I missed to set?

I'm not new to Ubuntu, so I should be able to follow not-newbie commands.  

Thank you a lot, I would really appreciate any hint with this very annoying problem!

giacomo

---

### Post by este.el.paz on 2015-04-03
@GM:

I went through this approx. 5 or 6 months or more ago, I think there are a couple other modules to add, and then you have to make some adjustments to a file so it knows how to read the sensors . . . .  

You might read the "mactel" sticky at the top of the page, or search the forum for threads from "mike braxner" . . . he provided some good tips to me, or, search my screen name looking for "fan control issues on MBPro"??? thread and see if you can follow the suggestions there.  It took a bit of effort to get it all to work, I just got it somewhere close, because to get it "perfect" was taking more time than I had--linux still seems to "run hot" on my computer, the fan also blows more with it, etc, i.e., more noisy.

The ****safest**** way to go, would be to get Parallels or VMFusionWare and then install whatever OSs you want to use there, and then it's always OSX that is running the machine, so the fan control will be to Apple's specifications, etc.  Or, Virtualbox installed in OSX, same reason, I think it takes some learning since VB is freeware . . . .

e...

---

### Post by giacomoalbe on 2015-04-05
Hi este.el.paz!

Thank you for the answer provided and happy Easter!

I will follow your instruction in this days and maybe I'll be prompting here some other problems/way of resolving that problem!

And I know that it would be safer to install Linux on a VM but I think I can get more from it if I hard install it (I just had a test of the overall performance and I think that it's just as speedy as I want an OS to be! Sometimes better than OSX!)

For now, thank you very much!

g.

---

### Post by este.el.paz on 2015-04-05
@GM:

Up to you, I don't think the speed difference would be noticeable or worth the extra time to get the fan issue covered, but, one of the threads I was mentioning just posted a few hours ago 4 threads down or so in the list of Apple Hardware users . . . . 

[http://ubuntuforums.org/showthread.php?t=2227348&p=13258786#post13258786](http://ubuntuforums.org/showthread.php?t=2227348&p=13258786#post13258786)

---

### Post by krumm2 on 2015-04-13
> **este.el.paz said:**
> @GM:

Up to you, I don't think the speed difference would be noticeable or worth the extra time to get the fan issue covered, but, one of the threads I was mentioning just posted a few hours ago 4 threads down or so in the list of Apple Hardware users . . . . 

[http://ubuntuforums.org/showthread.php?t=2227348&p=13258786#post13258786](http://ubuntuforums.org/showthread.php?t=2227348&p=13258786#post13258786)

I'm runnning a 2013 Macbook Air (6,2). Also it's running mint 17.1, but it's more-or-less the same. I initially had the same issues where the machine would get hot and the fan starts blasting. I quickly found that one CPU core was running constantly at over 70% utilization. This is a well known problem with kworker. I had to disable gpe66 interrupt. That IMMEDIATELY solved my problem. It's an easy fix - A good answer is at [http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high](http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high)

Additionally, I installed powertop and TLP to manage the power usage. I'm now running around 4 - 5 watts, nice and cool and long battery life.

---

### Post by este.el.paz on 2015-04-13
> **krumm2 said:**
> I'm runnning a 2013 Macbook Air (6,2). Also it's running mint 17.1, but it's more-or-less the same. I initially had the same issues where the machine would get hot and the fan starts blasting. I quickly found that one CPU core was running constantly at over 70% utilization. This is a well known problem with kworker. I had to disable gpe66 interrupt. That IMMEDIATELY solved my problem. It's an easy fix - A good answer is at [http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high](http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high)

Additionally, I installed powertop and TLP to manage the power usage. I'm now running around 4 - 5 watts, nice and cool and long battery life.

@k2:

This looks interesting, might be helpful for the whole "mactel fan control/heat" problem . . . busy lately in the MBPro using OSX, and over on my iBook working on a fresh install of PPC 14.04.2 . . . so maybe some day I'll be able to look at this "kworker" problem . . . .  I went the "macfanctld" route, it's more or less "OK" . . . still runs the computer hotter than OSX does . . . which is why I was suggesting the use of running linux in a virtual program, then all the hardware issues are covered by OSX . . . .

e...

---

### Post by krumm2 on 2015-04-13
I'd guess controlling the fan isn't the problem; the reason it's running hot is the CPU is really busy! Open the system monitor - see what the load average is on your idle system. Should be around .02 - .08. If it's really high, look at the kworker process. If that's rocking, then you very likely have the kworker issue.

---

### Post by este.el.paz on 2015-04-13
@k2:

Personally I don't do a whole lot of processor intensive stuff . . . and looking at Sys Monitor doesn't usually show a whole lot of action . . . just emailing and hanging out on forums . . . but, for some who do, getting the fans to come on earlier helps to keep the busy CPU cooler . . . .  I don't think I do enough to get the kworker thing up on the screen . . . but, might be worth checking at some point.

e...

---

### Post by giacomoalbe on 2015-04-28
Hi Guys!

Hi want to report to you all that the problem was solved with the solution given by krumm2! 

I had to disable the interrupt he said and now the Mac is quiet and cold :) I0m very happy!

Now I've got another problem (this is a good metaphore of life, there's always a new problem but hopefully there could be a solution too), the Wifi is no more working. I'm trying to install againt the kernel module needed by it. Hope this would solve the problem.

I think I'm going to as to modify/extend the wiki page related to this topic in order to help others with this issue to solve it!

Thank you for the help!

In the end, going a bit OT: krumm2 can you please point me some good resources (maybe the one you used) for installing and configuring powertop and TLC on the Air? Again, thank you a lot!

-g

---

