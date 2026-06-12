---
title: "Creative Zen Xtra 30gb not detected in Edgy"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by soulfly7x on 2007-02-16
I can't seem to get my Creative Zen 30 GB to be detected in Ubuntu 6.10 Edgy. I have searched the forums but don't understand any of the instructions. I have exactly zero experience with any OS other than Windows prior to installing Edgy eight days ago.

Last night looking through the add/remove programs list, I noticed there was a program called Gnomad2. I thought, "Cool," I can set up my Nomad to work using that," so I installed it. Then I plugged in the player and I got a message saying that a camera was detected, would I like to transfer photos. I checked "No." It's not a camera, it's an mp3 player.

Aside from that, it seems entirely undetected. I ran gnomad 2 and it tells me no player is detected. I've searched the forums for help, but I always reach a point where I must be missing a step that it is taken for granted that I know what to do, because every single time, I get stuck.

the last thing I tried was this:
[http://ubuntuforums.org/showthread.php?t=199250&highlight=micro+zen+mtp](http://ubuntuforums.org/showthread.php?t=199250&highlight=micro+zen+mtp)

I get to step 3, click the link copy and paste the instructions to step 4 and get told 
[INDENT]tar: gnomad2-2.8.10.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mike@mike-desktop:~/gnomad_install$ [/INDENT]

Up to that point it seems fine, then I copy/paste the instructions and get that. Is there something in the process of [INDENT]3. Next, download the latest version of Gnomad 2.8.10 to the folder you just created:

4. Navigate to the folder where you downloaded the file and extract it:
[/INDENT] that I am missing? 

I just don't understand what I'm doing wrong.

---

### Post by TheNewbie on 2007-02-16
what program did you use your Zen with in XP?

---

### Post by soulfly7x on 2007-02-16
Hi, I had to get away from the computer for a while. I used Creative MediaSource Player/Organizer 3.30.21 and it's running firmware version 2.10.03

---

### Post by soulfly7x on 2007-02-17
Okay. I still haven't solved the problem, nor do I know what I'm doing wrong.

---

### Post by TheNewbie on 2007-02-17
Soulfly,
   Have you tried just plugging your Zen into the PC and just trying to play music off it using the default media player? That maybe an idea....

---

### Post by soulfly7x on 2007-02-17
Ubuntu only detects it as being a camera, which is wrong. Aside from that it's completely undetected.

EDIT: I just ried to "Scan removable Media" and came up empty in Rythmbox.

---

### Post by legzelda on 2007-04-07
I had the same problem you're having.  Using Feisty seems to work MUCH better than Edgy.  However, I was able to get my Nomad working in Edgy by following this guide:

[http://www.linuxquestions.org/questions/showthread.php?p=2624632#post2624632](http://www.linuxquestions.org/questions/showthread.php?p=2624632#post2624632)

When you open Terminal (Applications > Accessories > Terminal), make sure to copy and paste each command one line at a time.  Let the command fully run until it's done before moving on to the next line.

I'd be happy to help you if this does not solve your problem, assuming you're still having the same problem.  Let me know if you would like additional assistance.

Be persistent--it will work (I fought this problem for weeks and eventually came out on top).  Good luck!

---

