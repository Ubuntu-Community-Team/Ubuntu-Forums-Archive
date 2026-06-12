---
title: "System freezes and or locks up, but mouse still moves"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Cathead Fred on 2006-08-10
Hello,

 I am a Kubuntu user. I know that I should be posting this in the Kubuntu Forums, but it seems that the expertise and experience are located in these forums. I am experiencing the issue that as soon as I install Dapper Drake 6.06 my KDE Screen will freeze, but I can still use my mouse. After a few minutes my mouse will then stop moving. I have tried Ctrl+Alt +Backspace but that does not work. I have to do a full reboot and then the process will start all over again. Sometimes when I log  in I will get the error pop up message,"The process for media protocol died unexpectedly". But this error message does not happen all the time. Sometimes my screen will freeze immediately and sometimes it will freeze after a couple of minutes.

Before I installed Kubuntu I was running Windows 2000 and everything was running fine. No problems. I then ran the Kubuntu 
live cd from Connical and everything ran well except for being a little slow.

I first thought this issue was a RAM issue or a hard drive space issue or a virus issue or a spyware issue. I don't think it is any of those things.

I then lurked on the Ubuntu Forums, the Kubuntu Forums, and I also Googled for the answer. Currently, I believe that my issue 
has something to do with the Nvidia Driver not being installed or configured properly.


So Far I have tried:

(1). Downloaded Automatix and installed the Nvidia drivers. Result: Screen froze 

(2). Borrowed an ATI Card (I think a Radeon 7800?) and installed it. Computer did not like it. The screen would just flicker. I tried this with both the live cd and with the full install of Kubuntu

(3). I read a post by Tseliot that showed me how to get into recovery mode and select in the Section Device "vesa" instead of 
"nv". This seems to make things stable enough so I can get into KDE to attempt to try different video card driver installs.

(4). Found Tseliot's "Latest Nvidia Dapper...HOWTO: Latest NVidia drivers" and attempted Method #1. Everything appeared to install beautifully, then when I downloaded updates I my computer locked up again. It says in the Howto that if you change your kernel or your kernel is updated then you need to reinstall the driver. I checked my kernel before trying Method #1 and after and it said it was 2.6.15-23-386. I used uname -r in the terminal to check.

(4a). When I tried Method #1 I installed it with the standard Nvidia driver. The Nvidia GeForce2 MX 200 card that I have does 
not appear on the legacy driver list.


My questions are:

(A). Am I on the right track here? Is the issue I am seeing a video card driver issue? Or is it something elese? Could it be 
a combination of problems?

(B). If this is a video driver card issue should I try Tseliot's Method #1 using the Nvidia legacy driver? Or should I try Method #2 with either the supported or the legacy driver?

(C). Should I try a different way of installing the Nvidia driver? I have seen slightly different ways mentioned in the Ubuntu and Kubuntu Forums.


My current setup is:

Kubuntu Dapper Drake 6.06
Motherboard: Gigabyte GA-6BXE
CPU: Intel Pentium III, 450 MHZ
RAM: 256MB (PC100 SDRAM)
HD: 40 Gig WD
Video Card: Nvidia Geforce2 MX 200


If you need a xorg.config file or a log file of some kind point me to instructions on how to get them and post them so I can 
provide this information to you.

Thank you for your time!

Cathead Fred

---

### Post by Cathead Fred on 2006-08-16
Update - I found information on various threads written by tseliot in the Ubuntu Forums. Also, he did include some of this particular troubleshooting info in his latest HOWTO: Latest NVIDIA drivers. This was my process.

1. Install Kubuntu. Within a minute or two the system will freeze in KDE but your mouse will work
2. Reboot your computer. 
3. While your computer boots you will see the GRUB Menu. Select and go into the GRUB Menu and select the line with "Recovery Mode" and press ENTER.
4. You will get a command line
5. At the command line type -w /etc/X11/xorg.conf and hit the Enter key
6. Scroll down the file with your keyboard (using your arrow keys) until you get to the section that says, "Section Device"
7. Set the driver to "vesa" instead of "nv" (you will have to type this)
8. Press CTRL+X (this will save and exit out of the file)
9. You should be at the command prompt. type reboot and hit the enter key
10. Your computer will then re-boot into KDE. Your video should work and be stable but it won't look that great. 
11. Use tseliot's Method #1 at [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
12. Once the Nvidia driver is installed by Method #1 the system will freeze but the mouse will work
13. Repeat steps 2 through 6 then go directly to step 14
14. Follow tseliot's instructions in the Problems Section #4, Titled: "If you have an AGP graphic card and your system 
freezes but you can still move your mouse pointer" located at [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
15. Reboot and hopefully your screen looks better and it is still stable

I am sure there is probably an easier way to do this but it is working right now for me. I'm going to play with it for a week or two until I am satisfied and close this.

These are the threads I got the information from:
[http://www.ubuntuforums.org/showthread.php?t=175726&highlight=install+driver+freeze](http://www.ubuntuforums.org/showthread.php?t=175726&highlight=install+driver+freeze)
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)


Tseliot, if you are reading this, please put the information on rebooting into grub and changing "nv" to "vesa" (in your HOWTO) so one can install using your Method #1. And implementing Problem Section #4. You can't use a terminal if you system is frozen!

---

### Post by daynah on 2006-10-04
I use an ATI Radeon 9500 Pro and after using a wiki guide for the Latest ATI Driver, the same thing started happening, but not as frequently as you describe, so it's difficult to test if the process "worked." For me, it would have gone on for hours before freezing up and I would stare at my screen and go, "Hey wait, this is why I swtiched FROM windows!"

So... in a day or two I'll be able to tell if helps ATI users who are having similar symptoms...

With me: Computer frozen, mouse moving. No error messages, though. I may get more error messages, and my mouse may freeze after a while if I had the patience to wait longer than 3 minutes but I never do. Never.

---

### Post by Cathead Fred on 2006-10-04
Hi daynah,

 Yes, you are absolutely right! It is frustrating trying to figure this one out ](*,) . When I first installed Kubuntu and got the problem I first thought it was my fault. I did something wrong or the hardware wasn't working correctly. 

 Don't wait for the error to occur. Keep playing with your computer until you need to go to bed and leave it on. If it is fine when you wake up in the morning you are good to go!

---

### Post by rickc on 2006-10-04
> **daynah said:**
> I use an ATI Radeon 9500 Pro and after using a wiki guide for the Latest ATI Driver, the same thing started happening, but not as frequently as you describe, so it's difficult to test if the process "worked." For me, it would have gone on for hours before freezing up and I would stare at my screen and go, "Hey wait, this is why I swtiched FROM windows!"

So... in a day or two I'll be able to tell if helps ATI users who are having similar symptoms...

With me: Computer frozen, mouse moving. No error messages, though. I may get more error messages, and my mouse may freeze after a while if I had the patience to wait longer than 3 minutes but I never do. Never.

I have this problem too, with my Radeon 9500, though I thought it might be a hard drive issue... Have you found anything to fix this? thansk in advance rickC

---

### Post by h2gofast on 2006-10-04
this in an nvidia issue.  I've run nvidia cards for the last 6 years and it pops up every once in awhile
[http://www.nvnews.net/vbulletin/showthread.php?t=74073&highlight=mouse+pointer+bug](http://www.nvnews.net/vbulletin/showthread.php?t=74073&highlight=mouse+pointer+bug)

---

### Post by Cathead Fred on 2006-11-14
This issue is solved!:mrgreen: 

My guess is that when I first used the Kubuntu Dapper Drake 6.06 LTS Live CD on my machine it used the VESA video driver. That is why everything worked! When I installed the operating system it then put in the driver it thought I needed. Kubuntu did everything right. The Nvidia driver is just messed up. Kudos to Tseliot and his Howtos! I wish I saw them when I first started researching this issue. I believe his workaround for this issue was for an AGP Card and probably this is what threw me off of my search. I have a PCI card. Oh well, live and learn. Also, my machine isn't the latest and greatest. I have a controller card so I can use two hard drives. The motherboard is really old. That slows things down a bit, but it still goes.

I am sold on Kubuntu. Some days though I feel that I am not learning anything new and some days I feel that this is too hard for me to understand. Also, I keep comparing it to Windows which is wrong, but it is the only other operating system that I am familiar with. My wife says, "Even though it is different, that doesn't mean it is wrong". I need to remember this when ever I get frustrated with Kubuntu. 

Lessons Learned:

(1). Identify the problem as best I can
(2). Research the issue
(3). When all avenues are exhausted, ask on the Forums (Pick the right Forum for my questions)
(4). Don't expect an answer right away or the right answer
(5). Keep looking and asking questions until you get your answer
(6). Sometimes it's a good idea to leave the problem alone for awhile, then come back to it with fresh ideas
(7). Just because it is different doesn't mean it is wrong

Linux is an amazing operating system! I can't wait until Vista comes out and then having my friends give me their old computers because they will be too slow to run Vista! Guess what I'm going to install on them?!

My wife is happy because she doesn't hear me complain everyday about my home machine being infested with viruses and spyware. Now, my secret plan is to get her to start using Kubuntu. Maybe this problem will take care of itself when she finds out how much Vista costs.

Daily, I am amazed that I have an operating systems that works so well and is truly free! Thank you to everyone who posted.:p

---

### Post by jaiagreen on 2007-02-07
Hi Cathead Fred,

My problem is very similar to the one you describe -- Ubuntu 6.10 freezes a minute or so after startup, but the mouse still moves. However, I have a Radeon S120 video card (9550 series). How should I modify the procedure you describe? Sorry for a question like that, but I'm a COMPLETE Linux newbie and need things spelled out!

---

### Post by Cathead Fred on 2007-02-12
Hi jaiagreen,

  Sorry for not responding to you sooner. Hey, join the club! I'm new at this myself. I just learned by reading, asking questions and finding stuff out on my own. I don't have experience with Radeon cards, but here is a link that may help!

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

 If that doesn't work, then I recommend you post your question in the Multimedia & Video section of the forums. You will probably get a faster response.

Good luck and post your progress

Cathead Fred

---

