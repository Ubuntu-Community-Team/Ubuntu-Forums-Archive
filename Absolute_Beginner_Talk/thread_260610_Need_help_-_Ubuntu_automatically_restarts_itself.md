---
title: "Need help - Ubuntu automatically restarts itself"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by pribnowbox on 2006-09-19
Hi all,

I'm completely new with linux and Ubuntu. I installed Ubuntu Version 6.06 LTS last week. Everything's perfect for me except sometimes Ubuntu automatically restarts itself, especailly when i'm running many programs at the same time, and I lost all my work!!

Does anyone have this problem and how to fix it?

For more information, I installed Xgl and Compiz, some mp3 codecs, and some other programs from universe and maltiverse. I'm not sure if these some programs cause my problem?

And If I would like to remove all those programs and go back to my stable Ubuntu, can i do that? (I don't want to format and reinstall Ubuntu, because last time I installed, it damaged all files in my Windows drive.)

Thank you in advance for all anwsers and suggestions,
Oak

---

### Post by nalinde on 2006-09-19
Humm I've got this problem when i used to run Windows...
Not that it has anything to do with windows... but.. well back in the days :) ... 

First time it was a power drop in my power PSU. It couldn't deliver even though it should.

The second time it was because my comp. was overheated.. :(.. hehe

Well don't know if that's your problem. But why not investigate it?
Otherwise I'm sorry to say that i can't help you..

---

### Post by benfindlay on 2006-09-19
The xgl and compiz could be causing your problems. Equally, it could be a piece of hardware that ubuntu simply doesn't like (from personal experience, laptop docking stations come to mind!). I'd advise you to post your hardware specs for people to take a look at.

With regards to uninstalling, if you used aptitude to install the programs, open a terminal and type ```
sudo aptitude remove [application]
```
This will remove all the dependencies too. If you used apt-get, open a terminal and type ```
sudo apt-get remove [application]
```
You will have to remove all the dependencies manually however.

If you installed using synaptic, then right click on the packages in synaptic and choose the complete removal option.

Hope this helps

---

### Post by junglepeanut on 2006-09-19
If it occurs while running xgl and compiz you need to turn off your screensaver,...I think.

Or just run gnome when doing normal work. 

This is only if it is occuring when you have not touched the pc for a few minutes(screensaver start time) i.e. rereading something you wrote etc.

If not I don't know.

---

### Post by pribnowbox on 2006-09-19
This is my hardware spec:

Procesorius:  	Intel® Pentium® M Processor with 1.40-1.70 GHz. Intel® new generation 90 NM process processo *A 1MB On-Die L2 Cache 

Chipset:  	Intel 855GME and ICH4-M Chipset

Atmintis:  	512 MB, DDR 333 DRAM 1x uSO-DIMM socket expandable to 512 MB

Video chip: 	Embedded Intel 855GME internal graphics Up to 64MB VRAM shared for display cache with IntelR DVMT technology

Ekrano tipas: 	12.1-inch XGA (1024x768) TFT Display
------------------------------------------------------------------

on Windows, I heard that computer will restart automatically when CPU is running overheated, but we can setup to turn that function off. Can I do anything like that in Ubuntu.

And, I will turn off xgl and compiz for a while and see if it can solve my problem.

Thank you so much for all your suggestions,
Oak

---

### Post by aleemriaz on 2008-04-05
Hi,

I am also having this same problem with Ubuntu 7.10, it was working fine for a couple of weeks and then lately it just automatically restarts/reboots after a couple of minutes of being active. PLEASE HELP!! this is a really annoying problem, I can't get no work done.

Has anyone been able to fix this problem?? Thanks

---

