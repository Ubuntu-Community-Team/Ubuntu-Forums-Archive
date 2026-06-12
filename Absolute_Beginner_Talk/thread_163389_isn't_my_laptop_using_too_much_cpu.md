---
title: "isn't my laptop using too much cpu?"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by gardara on 2006-04-20
I just placed the CPU Frequency Monitor to my panel. And I have been wathcing my CPU today. The frequency monitor newer shows a lower number than 972 MHz, even when I just turned my laptop on. I am not running many programs now only firefox, gaim, xchat and I have the weather and cpu panels. When I load pages on firefox (two or more at the same time) my cpu is used 100% and is 1.66 GHz.

Is this normal? on my desktop pc with win xp on it I am getting much lower number than 927 MHz.

Is the CPU maby used so much on my laptop because I only have 256mb ram? And Would this be fixed by getting a 1gb ram to it?

I'm thankful for all tips/help.

---

### Post by cleverselfreferentialname on 2006-04-20
Mobile CPUs aren't quite as powerful as the ones in desktops most of the time. If your CPU usage is that high all the time, install rcconf and disable unneeded services.

Oh, also, I intend to post a guide on optimizing ubuntu by tomorrow or Saturday, so your problem should be fixed either way within a few days time.

---

### Post by catlett on 2006-04-20
Go to Applications, scroll down to System Tools and scroll down to System Monitor. This will at least give you an idea of what is running all the time. Your CPU shouldn't be higher than running under Windows. There might be an application that is running at start up that you don't know about. Sorry I don't have an exact answer.

---

### Post by gabruo on 2006-04-20
I have experienced the same thing when using karamba cpu monitor and gdesklets, which I found the longer they run the more they consume.  They look nice but are hogs.  My 2 cents anyway.  Try running the 'top' command in a terminal and see what is using what.

---

### Post by cleverselfreferentialname on 2006-04-20
If its at startup it can't be gam_server leakage....maybe ACPI issues? Whats your laptop model?

---

### Post by gardara on 2006-04-20
this is strange, I am watching the system monitor and it's popping from 9% cpu load to 70% cpu load when Im doing nothing, when I clicked the reply button to post this message I get 100% cpu load in the system monitor.
I don't see any processes that I don't thinks should be there and I don't see any processes that are using much cpu. I'm looking at CPU time isn't that what I'm supposed to be looking at?

---

### Post by gardara on 2006-04-20
[QUOTE=cleverselfreferentialname]If its at startup it can't be gam_server leakage....maybe ACPI issues? Whats your laptop model?[/QUOTE]
I have a hp compaq nx9005

---

### Post by cleverselfreferentialname on 2006-04-20
Well....if it is ACPI, there's [this]("http://emeitner.f2o.org/nx9005/#acpi") .

---

### Post by gardara on 2006-04-20
[QUOTE=cleverselfreferentialname]Well....if it is ACPI, there's [this]("http://emeitner.f2o.org/nx9005/#acpi") .[/QUOTE]

how can I know if  it's a acpi problem? Can I do this and check if this will fix my prolem or can this harm my laptop and make the problem worse than before?

---

### Post by catlett on 2006-04-20
If I'm interpreting the link correctly it is saying the CPU throttling can be caused by runnig on the battery. Do you have a way to run your laptop without the battery? If so try it and see if the CPU usage is still high. That solution looked involved. Any time they say "recompile" it's advanced stuff (you may be an advanced user though) Good luck.

---

### Post by gardara on 2006-04-21
Well I'm a advanced computer user but pretty new to ubuntu (just been using it for a week or two)
Running on ac power doesn't change anything :(

Any other solutions? Could it be using so much cpu because of heat or lack of ram or anything?

---

### Post by gardara on 2006-04-23
Ok, I found info about a guy that is running linux on a hp nx9005, the same laptop version as I. You can read about it here: [http://emeitner.f2o.org/nx9005/#proc](http://emeitner.f2o.org/nx9005/#proc)

he say's this about the CPU > There are problems with the nx9005 system not returning a correct CPU ID, thus preventing the kernel scaling drivers from working.(see [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml)) The 2.6.6 kernel does not require any patches for the Powernow driver to recognize the CPU. See the Kernel section on how to fix this to enable Powernow! scaling in older kernels.

To implement load-based CPU frequency scaling I am using the CpuDyn daemon. You can download a backport for Woody here. It is already in Sarge and Sid. Using this, my CPU clock frequency will drop to 532MHz from 1788MHz when the system load is low. The designer of CpuDyn created it so that the system load of 'nice' processes is ignored when deciding whether to jump to the maximum CPU frequency. This allows a lot of flexibility for controlling how your system resources are used. 

Ok, so I installed CpuDyn and hoped it would help me with my cpu problems but it didn't do anything so I thougt oh well and tryied some other programs like CpuDyn, powernowd and some others but I couldn't get any of them to work.
But some of them seem to have worked because now my CPU is allways stuck at 100% :( and when I turn on my laptop I get the error message > **CPU frequency scaling unsupported**
You will not be able to modify the frequency of your machine. Your machine may be misconfigured or not have hardware support for CPU frequency scaling

Can anyone please help? 100% CPU usage at my laptop isn't really great as the cooling system goes to max with a lot of noice and yesterday my cpu heated up to 70°c ](*,)

*edited: I put the exact error message I get on startups*

---

### Post by trent dillman on 2006-04-23
Check if you have a buggy dsdt. I had some problems with my hd on a HP zd7000:

start a root shell:
```
sudo -s -H
```
install the Intel asl compiler:
```
apt-get install iasl
```
extract your dsdt:
```
cat /proc/acpi/dsdt > dsdt.dat
```
disassemble it:
```
iasl -d dsdt.dat
```
recompile it:
```
iasl -tc dsdt.dsl
```

Any errors or warnings means a buggy dsdt.

*This was taken from [http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)*

---

### Post by gardara on 2006-04-24
I seem to have a buggy dsdt:

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20051216 [Jan  9 2006]
Copyright (C) 2000 - 2005 Intel Corporation
Supports ACPI Specification Revision 3.0

dsdt.dsl   572:                     Method (DRUL, 1, NotSerialized)
Warning  2085 -                                ^ Not all control paths return a value (DRUL)

dsdt.dsl  2146:                     Name (_HID, "*SYN0105")
*SYN0105
dsdt.dsl  4031:                     Method (SMSL, 0, NotSerialized)
Warning  2085 -                                ^ Not all control paths return a value (SMSL)

dsdt.dsl  5528:     Method (_WAK, 1, NotSerialized)
Warning  2078 -                ^ Reserved method must return a value (_WAK)

ASL Input:  dsdt.dsl - 5864 lines, 224833 bytes, 2616 keywords
Compilation complete. 1 Errors, 3 Warnings, 0 Remarks, 751 Optimizations
```

What can I do about it? To fix the buggy dsdt?

By the way, the error message I allways get on startups is
> **CPU frequency scaling unsupported**
You will not be able to modify the frequency of your machine. Your machine may be misconfigured or not have hardware support for CPU frequency scaling
It must by misconfigured because as I said earlier there was a guy with the same laptop model as I that was able to use CpuDyn....
...Any thoughts?

---

### Post by Jindro on 2006-04-28
[QUOTE=gardara]
Can anyone please help? 100% CPU usage at my laptop isn't really great as the cooling system goes to max with a lot of noice and yesterday my cpu heated up to 70°c ](*,)

*edited: I put the exact error message I get on startups*[/QUOTE]

look at "top" command
you can see what process is behind

---

### Post by [h2o] on 2006-04-28
I seem to have a buggy DSDT as well (If the method stated above is suitable for AMD Turion64 as well). What is one to do about it? I am running Dapper Beta btw...

---

