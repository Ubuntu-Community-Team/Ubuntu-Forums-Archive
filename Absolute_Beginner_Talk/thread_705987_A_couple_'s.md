---
title: "A couple ?'s"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by hottshot104 on 2008-02-24
Hey everyone. 

I have a few more questions that I hope some of you seasoned veterans can help me with.

1. What's the best video player for Ubuntu? 

2. Is there a way to fix the "huge" login text that I have? I've already tried changing login themes, fonts, and I have tried a method involving editting gdm.conf, which bricked the OS and forced me to reinstall.

3. Could you recommend a good way of backing up all of my data in case another catastrophe happens? I tried using Keep but got kinda stuck.

---

### Post by Tyke91 on 2008-02-24
1. VLC movie player

2. dunno

3. when you install ubuntu, create a separate /home partiton. that way when you install again, you don't have to lose any personal data. If you don't want to do that, you can just copy/paste the contents of your home folder to a dvd or removable hard drive...

---

### Post by InfinityCircuit on 2008-02-24
1. I recommend mplayer.  It is robust and full of all the codecs you might need.

2. I'm unsure of how to fix this.

3. The first step to backing up is to have multiple media.  I recommend monthly backups to DVDs at the very least.  If you want an automated backup solution, you can use Retrospect.  It is proprietary but it has a nice linux client.

---

### Post by gsmanners on 2008-02-24
1) mplayer
2) probably a DPI issue
3) use a separate partition for /home

---

### Post by vishzilla on 2008-02-24
1. Rhythmbox. I recommend trying all mentioned above and deciding for yourself.
2. Dunno
3. Separate /home partition or backing up in DVDs

---

### Post by hottshot104 on 2008-02-24
One more question. I installed the virus scanner via add/remove programs, and when I went to update the virus signature it said I must be root to do it. What does that mean?

Also, can anyone direct me in how I can partition my home folder to another partition without messing up my settings currently I would appreciate it tons.

---

### Post by InfinityCircuit on 2008-02-24
[http://forums.debian.net/viewtopic.php?t=19519](http://forums.debian.net/viewtopic.php?t=19519)

This is a guide that explains how to create a new /home partition.  Note that you will have to use gparted or something else to make free space for your new partition.  When it says "su to root" that means type "sudo su"

---

### Post by hottshot104 on 2008-02-24
Thanks everyone.

As it stands, I still have yet to see an answer to question 2. I've looked it up on here and I couldn't find anything. 

*sigh* This is going to continue to bother me because I'm very meticulous about getting my computer running perfectly the way I want...

---

### Post by hottshot104 on 2008-02-24
Two new problems have arisen.

One, when I start up it tells me something about the video not being defined and then asks me to select a number between 0-9 or type scan. I can still load up after but that's weird.

Also, I installed wine, but even programs I successfully installed prior to this reinstall wont install saying there isn't a program that can handle a .exe.

Any help?

---

### Post by oedha on 2008-02-24
1. VLC
2. have you set the screen resolution ?
3. separate /home or you can install bacula ( from terminal :==> sudo apt-get install bacula )
4. what AV did you install ? for avg you have to work on terminal (not sure about clamav)

---

