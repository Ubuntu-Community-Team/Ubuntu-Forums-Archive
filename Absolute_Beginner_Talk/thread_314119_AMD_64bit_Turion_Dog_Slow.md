---
title: "AMD 64bit Turion Dog Slow"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-12-07
Hi,

I have finished installing Ubuntu Dapper on a AMD 64 bit Turion Laptop with an Ati PCI-X 200M Display adapter and 384Mb RAM. This thing is dog slow! Can anybody please give me some advice?

---

### Post by RudolfMDLT on 2006-12-07
Got the Ati drivers to install and load, In system monitor the CPU is running at 98% when the system is just sittin there doing nothing? nothing in the processes seems to use 100% cpu, most things are "sleeping".

Please help! :)

---

### Post by robinl on 2006-12-07
View/All Process in System Monitor? Or some nifty command line command like this will show up all the processes running.

```
ps aux
```

---

### Post by RudolfMDLT on 2006-12-07
Thanks,

I ubdated the BIOS in windows and now Ubuntu is a little quicker. I've tried installing a new Kernel, the K8 one but it takes forever to configure! I'm installing Xubuntu on a machine desinged to Fly with windows! Sucks!

Any ideas on why a 64bit Turion would crawl when no apps are runnig, not when using top, as aux or the system monitor...

I'm about to chuck Ubuntu on this machine because it's really not working at all.
(This ain't a rant - I'll still use Ubuntu on my other machines but I'm really getting pressed for time and something that works.)

---

### Post by fatneck on 2006-12-07
I had the exact same problem on my laptop - see spec in sig. The only way I could fix it was by ditching Dapper and installing Edgy. I went for Edgy i386 (not the 64 bit version) and it worked fine. On it now in fact...

---

### Post by RudolfMDLT on 2006-12-07
Fatneck....

Your telling me to load 32bit Edgy onto a 64 bit system - sounds dodgey but I'll try it!

Then a question for all:

1) Ati Radeon PCI-X 200M, will it be able to run composite in Edgy?
2) I want to install Kubuntu Edgy 32bit - any reasons not to?


Sorry if the questions seem stupid but I haven't slept in 39 hours due to Dapper 64bit and AMD Turion.

Thanks,

Rudolf

---

### Post by drphilngood on 2006-12-07
> **RudolfMDLT said:**
> ...Your telling me to load 32bit Edgy onto a 64 bit system - sounds dodgey...

Nothing ¨dodgey¨ about it. :)  My guess is that most Edgy users, including myself, ¨load 32bit Edgy onto a 64 bit system¨.

edit:
You might be interested in this link:

[BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

the notes section at the bottom, in particular.  However, I see no reason why you shouldn´t ¨install Kubuntu Edgy 32bit¨.

---

### Post by renzokuken on 2006-12-07
have you checked to see if both cores are actually working, being used, recognised?

im not sure how you do it in XFCE though.

---

### Post by RudolfMDLT on 2006-12-08
How would I check that both cores are being used in Gnome or Bash for that matter?

THanks for the Binary Driver how to - But I can install the driver, see my sig, the problem is that with my previouse ati card I had to disable Composite rendering which is like disabling the turbo on your new porche... stupid!:)

---

### Post by renzokuken on 2006-12-08
in gnome you can go to System -> System Monitor -> and its one one of the tabs (second one in think) if it shows the graphs for two cores then you are ok, if not, you may have to enable SMP in your kernel

---

### Post by RudolfMDLT on 2006-12-08
It's a 64bit machine, not hyper threading? Or do I mis understand how the CPU works? What is SMP? Thanks for the help thus far.

---

### Post by fatneck on 2006-12-08
you don't have 2 cores in a turion and i shouldn't worry too much about not using 64 bit edgy. just whack on the normal, 32 bit edgy and away you go. let us know how it runs...

---

### Post by drphilngood on 2006-12-09
> **fatneck said:**
> you don't have 2 cores in a turion and i shouldn't worry too much about not using 64 bit edgy. just whack on the normal, 32 bit edgy and away you go. let us know how it runs...

What makes you say it doesn´t have two cores?  They do [make them]("http://www.tomshardware.com/2006/08/22/amd_dual_core_laptops_have_arrived/") but he hasn´t said.  However, I too, believe that he should stick to a 32 bit distro.

> **RudolfMDLT said:**
> How would I check that both cores are being used in Gnome or Bash for that matter?

List  # of CPUs 
```
cat /proc/cpuinfo | grep '^processor' | wc -l
```
detailed cpu info
```
cat /proc/cpuinfo
```

> **RudolfMDLT said:**
> THanks for the Binary Driver how to - But I can install the driver, see my sig, the problem is that with my previouse ati card I had to disable Composite rendering which is like disabling the turbo on your new porche... stupid!:)

I did see your sig and also your post below.  Since your problems started after you installed the ATI drivers, I thought you might want to make use of the troubleshooting section.  However, now I see that I am too ¨_stupid_¨ to be of help to one so wise and will remember this the next time I see your ¨Please help!¨ plea.  

> **RudolfMDLT said:**
> Got the Ati drivers to install and load, In system monitor the CPU is running at 98% when the system is just sittin there doing nothing? nothing in the processes seems to use 100% cpu, most things are "sleeping".

Please help!

---

### Post by fatneck on 2006-12-09
from your quoted site:

"Be that as it may, ATI offers two chipset variants for Turion 64 X2 laptop processors: the Radeon Xpress 1100 and 1150."

that isn't what he has according to his first post, but apologies all round if you do have a dual core! anyway, come on rudolf, what have you tried - is it working yet?!

---

### Post by anaconda on 2006-12-09
My Turion 64 x2 (1,6GHz)
works at half the speed (0,8GHz) if there isn't much load. If I do something heavy it jumps up to 1,6GHz though..

when I run 'more /proc/cpuinfo' it shows 800MHz or 1,6GHz depending of the load.

If you are runnig edgy, and your turion is x2 then both your processors should be in use (edgy:s generic kernel is SMP-kernel and has support for dual core processors.) I first installed dapper without dual core support and then I only had 1 core and it was runnig at 800MHz.. and it as realy slow... 

If you want to run always with max speed then you need to disable the energy saving function from your BIOS. Something like "cool and quiet" (different BIOSses have different name for it)

---

