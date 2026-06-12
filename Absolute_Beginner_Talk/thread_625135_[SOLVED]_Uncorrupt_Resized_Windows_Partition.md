---
title: "[SOLVED] Uncorrupt Resized Windows Partition?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Thinker-Philosopher on 2007-11-27
Hello, this would be my first question to ask on this wonderful forum.  I have been working on a problem for about 3 days now.  Sorry for the read :(

First, let me give some background before I ask my question.  I have a dual-booting (XP and Ubuntu) Dell Inspiron 6400 that had 75 gb (57% free space) partitioned to XP SP 2 (/dev/sda1) and 15 gb partitioned, including swap, to Ubuntu (/dev/sda5).  After having Ubuntu since Feisty's release, I finally decided to move to Ubuntu for most of my day-to-day computing.  The problem is that the webcam that I had bought before I installed Ubuntu (Logitech Quickcam for Notebooks Pro (2006)) does not work in Ubuntu for IM video (or in Skype).  So I had to keep Windows (yes this is all relevant).

Now, with this in mind, I decided to allocate some more room for Ubuntu (about 8 more gb, for now).  After reading around and prepping my computer for this task (I defraged like 12 times :lolflag:), I felt confident enough to shrink the Windows partition, resize the extended partition, move the swap, move the ext3 partition, and resize the ext3 partition.  This went off without a hitch.

After I finished the process, I restarted my computer.  I then selected my XP SP 2 partition.  After this, Windows began to boot for about 3 seconds and then it flashed a blue screen really, really fast (all I could tell was that it was blue and had text on it).  It then restarted my computer.  And it keeps doing this no matter what I have tried.

After searching for a linux based work-around (and failing), I figured that I needed my XP SP 2 disc to initiate the recovery console.  The issue with this is that I am on the other side of the Atlantic (Italy), from where my disc is (USA).  I have no way to get it back at the moment because all my stuff is in storage, and I unintentionally placed my disc in there.  So, I can't use my disk.  And I really want to use my webcam (it's the only way I talk to my girlfriend right now :()

Now, for my question(s):

Is there someway to uncorrupt my resized XP partition in Linux?  If so, how?

Thank you very much for your time.

*Forgot to mention, Ubuntu runs fine.

---

### Post by Cochise on 2007-11-27
when the screen goes blue quickly press pause on your keyboard and post the error here, its tricky to do but possible with practice, without the error code or message, its going to be guess after guess as to what the actually problem is.

---

### Post by Thinker-Philosopher on 2007-11-28
Thanks for the reply.  I tried to do that last night to no avail.  The only thing that I was able to catch was "anti-virus".  But I could very well be mistaken.  I will attempt it again tonight when I get off work.

---

### Post by Cochise on 2007-11-28
yeah cool, let me know how you get on

---

### Post by hyper_ch on 2007-11-28
Thinker:

You're not student anymore? If you were, there would be good chances that your university is participating in the MSDNAA --> from there you could then downlaod a Win XP ISO....
But that's only if you are a student.

---

### Post by samuel.rajesh on 2007-11-28
> **Thinker-Philosopher said:**
> Hello, this would be my first question to ask on this wonderful forum.  I have been working on a problem for about 3 days now.  Sorry for the read :(

First, let me give some background before I ask my question.  I have a dual-booting (XP and Ubuntu) Dell Inspiron 6400 that had 75 gb (57% free space) partitioned to XP SP 2 (/dev/sda1) and 15 gb partitioned, including swap, to Ubuntu (/dev/sda5).  After having Ubuntu since Feisty's release, I finally decided to move to Ubuntu for most of my day-to-day computing.  The problem is that the webcam that I had bought before I installed Ubuntu (Logitech Quickcam for Notebooks Pro (2006)) does not work in Ubuntu for IM video (or in Skype).  So I had to keep Windows (yes this is all relevant).

Now, with this in mind, I decided to allocate some more room for Ubuntu (about 8 more gb, for now).  After reading around and prepping my computer for this task (I defraged like 12 times :lolflag:), I felt confident enough to shrink the Windows partition, resize the extended partition, move the swap, move the ext3 partition, and resize the ext3 partition.  This went off without a hitch.

After I finished the process, I restarted my computer.  I then selected my XP SP 2 partition.  After this, Windows began to boot for about 3 seconds and then it flashed a blue screen really, really fast (all I could tell was that it was blue and had text on it).  It then restarted my computer.  And it keeps doing this no matter what I have tried.

After searching for a linux based work-around (and failing), I figured that I needed my XP SP 2 disc to initiate the recovery console.  The issue with this is that I am on the other side of the Atlantic (Italy), from where my disc is (USA).  I have no way to get it back at the moment because all my stuff is in storage, and I unintentionally placed my disc in there.  So, I can't use my disk.  And I really want to use my webcam (it's the only way I talk to my girlfriend right now :()

Now, for my question(s):

Is there someway to uncorrupt my resized XP partition in Linux?  If so, how?

Thank you very much for your time.

*Forgot to mention, Ubuntu runs fine.




So did u get this solved ? ,if so please do post and mark the thread as solved ,it might help others

---

### Post by gn2 on 2007-11-28
Have you tried adding the ntfsprogs package and using ntfsfix?

It's in the repos and available through Synaptic.

---

### Post by Thinker-Philosopher on 2007-11-28
@ hyper-ch

I can't take use of it since I am not enrolled in this semester for school (though I am for this next semester).

@ samuel.rajesh

This problem is not yet solved because I haven't been able to access my personal computer (using work computer at the moment).  But I be able to access it in about 3 hours.

@ gn2

I installed ntfs-progs yesterday and used ntfsfix, but I got an error.  I can't remember what it was, but I'll post once I am off work (in about 3 hours).  Thanks for your help.

---

### Post by hyper_ch on 2007-11-28
thinker:

I was just asking because you said you have no XP cd with yout ;)

---

### Post by Thinker-Philosopher on 2007-11-28
Okay, I figured out a way to make this work.  I got a hold of someone else's XP disc and got to the recovery console.   All is well again, thanks for your help.  Sorry about all this, I feel like an idiot.

---

