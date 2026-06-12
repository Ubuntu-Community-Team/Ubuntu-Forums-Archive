---
title: "total newb trying to install rosetta"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by petalumaslim on 2007-06-08
heya,

this is my first five hours on ubuntu. so far i'm not impressed or very happy. installation went ok, i was notified there were 50 updates available for feisty fawn. i downloaded all the updates then restarted. i downloaded 4 more updates then restarted again, even though i was not prompted the second time. then i downloaded boinc for AMD64. then i downloaded  nvidia drivers for my rig. i could not get either one to install because i don't know how. i read the wiki and it told me to use the ad/remove program icon. it does not even recocnize what i have downloaded. the rosetta@home file had a sh ending. After sifting through the wiki i selected the properties option on the boinc software. i selected run as an excecutable and double clicked the icon. now i have boinc in my folder under the boinc  heading. when i click on the boinc folder it selects the contents of that folder. in the folder there are three icons; boinc, boincmgr and something else. clicking on any of them yields nothing. what am i doing wrong. ? i just want to use this computer for rosetta. why is it so counterintuitive to install basic software ?Uubuntu was advertised as the no brainer os alternative to windows/mac. i have built over 20+ computers using the windows operating system. i would love to use a different os, but until the os is more intuitive and easy to use i guess i'm stuck.  
help a brother out,
cancer fighter

---

### Post by viciouslime on 2007-06-08
You won't have had to restart for the other updates, only kernel updates require a restart. In other words you could have installed 53 of the 54 without restarting.

You're going the windows way about things. You don't have to go to differnt websites to download things anymore, you install software from the repositories. These are browseable either via add/remove programs or synaptic found under System/Administration/Synaptic Package Manager

For the nvidia driver, you can go to System/Administration/Restricted Drivers Manager and tick the box next to nvidia graphics card. This will download, install AND configure the driver for you. Much easier than windows :)

Some software isn't available in the repos, though there are over 20,000 packages last time i checked. This software can come in many different forms, just as it does under windows. The only way you can no what to do with it, is reading the documentation that comes with it.

---

### Post by locke.dragon on 2007-06-08
hey.  i just wanted to point out that ubuntu and linux in general isn't a copy of windows, it's an entirely different os.  and if you're talking about rosetta stone (the language program), that's a windows program and probably won't work under ubuntu/linux.  you could possibly get it running under WINE (do a forum search), but other than that, i don't know.  just keep in mind that ubuntu is NOT windows.  but, is much more organized and user-friendly once you get used to it.  and my advice would be to not download anything from sites to try to install a program.  if you absolutely must, at least try to get a .deb file.  that one functions pretty much like an installer in windows would.  just double click and let it do it's job.  let us know if there's anything we can help with!  :)  

p.s.  and it's better to start a separate thread for each question, it's hard for us to address each question you have if you post them all in one thread.

---

### Post by joejr on 2007-06-09
I just started with Ubuntu about 2-3 months ago.  I have been confused on and off as well, but at the end of it all it is becoming more fun than windows.  Getting stuff to do what I want is sort of puzzle like.  
     I got Rosetta Stone for Windows going through Wine, I just can't get the language pack CD to be recognized by Rosetta in Wine.  Not sure what to do there.  

                                              Joe

---

### Post by kditty on 2007-06-21
i believe this was resolved here, good luck.

[http://ubuntuforums.org/showthread.php?t=290699&highlight=rosetta+stone](http://ubuntuforums.org/showthread.php?t=290699&highlight=rosetta+stone)

---

### Post by vaughan-AMD on 2007-06-27
The op is asking for help using BOINC. No mention of rosetta stone but they do ask about Rosetta@Home which is a BOINC project.

I get the same problems as the op.

Anybody able to answer this BOINC installation / running question?

---

### Post by xzero1 on 2007-08-25
Assuming you have the 64-bit version of Ubuntu...
I have installed the BOINC client for rosetta (Beta version for 64-bit) a couple of hours ago. To install: download the file, open a terminal and run sh [name of file].  Now run boincmgr to start the program. Note: this is beta software and I have not yet completed a work unit. Will update.

Linux rosetta 64-bit beta version:
[http://boinc.berkeley.edu/download_all.php]("http://boinc.berkeley.edu/download_all.php")

UPDATE:
Boinc 64-bit beta runs fine, uses both cores but will occasionally crash. The crash seems to happen when I am running other apps but it is simple to restart boinc and I prefer a 64-bit client.

---

### Post by oldos2er on 2007-08-25
Boinc is in the repositories, but I can't recall now if they're the default ones. Try Synaptic, or in a terminal "sudo aptitude install boinc". Also I don't know if this applies to the 64-bit version, sorry.

---

