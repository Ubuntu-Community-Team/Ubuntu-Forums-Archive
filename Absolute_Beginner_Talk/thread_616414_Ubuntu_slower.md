---
title: "Ubuntu slower"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by William S on 2007-11-18
My Ubuntu (7.10, 64 bit) has suddenly become slower (like lagging when scrolling a webpage)
I can't use any desktop effects any more either. I have no logical explaination for what happened, it just happened. 
I tried to check restricted drivers, my fglrx was on. I removed it and reinstalled it again, didn't go any faster. 
I hope some of you know, thanks.

---

### Post by tyggna1 on 2007-11-18
Check out your system monitor (right click on bottom, add to panel, system monitor).   If you click on that, check out how your resources are, and then look under processes, you might find the culprit (you can sort the results by clicking at the top of each column).   Some java-based applications can hog memory like you wouldn't believe, and they get worse over time e.g. Azureus.

---

### Post by William S on 2007-11-20
Well I think I have managed to get a virus... :P 
It says several applications got 17000 GB RAM (no joke)

---

### Post by HermanAB on 2007-11-20
Run 'top' and 'kill' the offending processes.

Cheers,

Herman

---

### Post by William S on 2007-11-20
If I am going to kill them I will kill the whole system (like killing explorer.exe in Windows)

---

### Post by jordanmthomas on 2007-11-20
which processes are they?

---

### Post by William S on 2007-11-21
The processes are: gnome-panel, gnome system-monitor (!), mixer_applet 2, notification demon, nm_applet and metacity. 
Killing these doesn't help a thing as other processes take over using such a lot memory... 
I look on the CPU usage, and just scrolling this page takes 45 % of the CPU...

---

### Post by William S on 2007-11-21
Anyone got any more suggestions? Or is simply reinstall? :(

---

### Post by Chayak on 2007-11-21
Well try restarting X with a "Ctrl-Alt-Backspace" you'll have to log in again but if it was a memory leak that should clear it out.  If it's still doing it I would get my vital data off onto something and reinstall.  I have less an idea of what's wrong than you because I can't see your system but there is certainly something wrong.  My systems barely use 153 MB of ram with a Gnome desktop and system monitor up.

---

### Post by twiceasworn on 2007-11-21
I ran into an issue with my box here at work where gnome would just run rampant, chew threw memory and I would have to kill the gnome-settings daemon to get it back.  Although, since I was running fluxbox as my window manager I didn't need any of the gnome crap running.  It very well may just be an issue with Gnome.  Perhaps try a new DE?  I dunno, just throwing out ideas.

PS Chayak--

What boat are you on, if you are on one?

---

### Post by jamere on 2007-11-21
You might have an indexing issue. The new feature is turned on by default in 7.10. When the sytem starts indexing, it can nearly grind to a halt using high cpu and HD activity.

system>preferences>indexing preferences [uncheck the two boxes to turn off indexing feature]

hope this helps

jim m

---

### Post by William S on 2007-11-23
Alright kinda got what is wrong now. I tried logging into terminal mode and it said something about no resume image found, doing normal boot. 
Kan this halt my system to nothing other than slow?

---

### Post by kpkeerthi on 2007-11-23
> **William S said:**
>  no resume image found, doing normal boot.

No that is normal. The resume image gets created if you 'hibernate' your machine. Next time when you startup, it picks that image so it can 'resume' the hibernated session. If you did not hibernate, then resume image does not exist and hence that message. Its just an informational message and is  no way related to the issue you are having.

---

### Post by bobpur on 2007-11-23
I think the CPU going nuts is less of an issue than the memory hogging. I moniter CPU Usage and noticed that it often shoots to 100% during normal use. It might be a problem if it maxed out and stayed there for a while, but spiking to a 100% is normal.

---

