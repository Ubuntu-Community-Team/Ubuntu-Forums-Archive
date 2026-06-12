---
title: "hardware problem (maybe)??"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by MarkSheely on 2006-06-23
Hi everyone,

I was wondering if someone might be able to help me out.  My laptop has crashed 6 times from using the program Celestia (a graphics intensive application).  I tried uninstalling and reinstalling, but that doesn't help.  What happens is that after starting the program, within a few minutes, my laptop shuts itself off and restarts.  When I log back in, my file browser is opens up automatically, and Celestia restarts itself.  

On a hunch, I looked at my CPU monitor while I was running the program.  It turns out that just having the application open uses up 85 - 95% of CPU.  So I would imagine that trying to do anything with the applicaiton would make my CPU overload, and shut the computer down, right?  Does this mean that my celeron m processor is trying to do a job that some other piece of hardware should be doing?  

I typed "sudo lshw" into terminal, and found the following:

* - display:1 UNCLAIMED
   description: Display controller
   product: Mobile 915GM/GMS/910GML Express Graphics Controller
   vendor: Intel Corporation
   physical id: 2.1
   bus info: pci 000:2.1
   version: 03
   size: 512KB
   width: 32 bits
   clock: 33 MHz
   capabilities: bus_master cap_list
   resources: iomemory:dff80000-dfffffff

Does the "UNCLAIMED" up there mean that my hardware isn't being detected correctly - and might this be the problem?

Thanks so much for any help or advice you can give me,
Mark 
[email]marksheely@gmail.com[/email]

---

### Post by Kurt` on 2006-06-23
This may not be totally relevant but,

When my sister's new Dell laptop runs anything intensive (3d games in particular), the entire system overheats and shuts off/BSODs/reboots.

Do you have a temperature monitor? (in your bios, or a sensor)

---

### Post by nitricacid on 2006-06-23
I think Dell laptops have this problem/bug.
My old lady had a dell laptop and the thing had such heat issues that it had to be sent back to the manufacturer to get the CPU & CPU cooling fan replaced, Twice.

If you ask me computers are not ment to be crammed in to such a small space and not expect to have some kind of heating issues do to the lack of vent spacing.

---

### Post by MarkSheely on 2006-06-23
I'm not sure if I have temp monitor or not - I will get right on it. 

The thing is, I can use Google Earth for linux without any problems.  I don't understand why Celestia should pose a larger problem.....

Also, I can use Celestia without any difficulties in my windows partition.

Thanks for the advice, I'll look into the temperature thing.

--Mark
[email]marksheely@gmail.com[/email]

---

### Post by MarkSheely on 2006-06-24
The temperature seems to be the problem.  When running Celestia, there is a huge spike in temperature from 50 degrees C to 60 degrees C within a minute. 

My question is, then, why should this happen only with this particular program?  I know, thats not really a question anyone here can answer.  

But maybe someone can tell me what the "* - display:1 UNCLAIMED" means up in my original post?

Thanks for all of your help, everyone.  I really appreciate it.

-Mark
[email]marksheely@gmail.com[/email]

---

