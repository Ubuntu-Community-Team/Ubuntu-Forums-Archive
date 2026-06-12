---
title: "getting rid of windows"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2008-03-31
Here's the skinny.

I need to figure out if I can record using my midi plug in using linux.  If that works I'm going to back up all my ebooks (I have a lot) and music (equally as much) and then ditch windows.  I never boot into it and it's taking up 130 some gigs worth of my HD.  This, to me, doesn't make sense.

I am running a website on joomla, so I don't want to delete my linux partition and start over.  I do, however, want to get rid of windows (assuming all goes well) and petition my HD that way I can have an optimum linux system.

I've read having a seperate "/home" partition is a good idea.

Anything else you guys could say?

Thanks a bunch, hopefully all will be well and I"ll be on the otherside shortly.

Long live the 'buntu.

---

### Post by Matthewslf on 2008-03-31
Try out JACK (look in synaptic for jackd and qjackctl) for your midi plug. There is a nice synthesizer called zynaddsubfx, which should work right away. I am not the best person to give you help with JACK, though. gParted has always worked for me, but i'm not sure it works as well with larger hard drives, though. I just got through getting rid of windows two weeks ago. It's nice to have a completely empty HD. Good luck.  <8^)

---

### Post by AnLGP on 2008-03-31
Thanks.  I've heard of (and tried to use) JACK but couldn't get it to work.  I suppose that's a different thread at a different time.

---

### Post by Matthewslf on 2008-03-31
Do you remember what the problem was?

---

### Post by AnLGP on 2008-04-01
It said my server wasn't connected or something similar to that.

---

### Post by miesnerd on 2008-04-01
im assuming you're using regular ubuntu. Maybe, if you want more tools to use JACK with (and other midi tools as well) you might want to check into Ubuntu Studio. We have a machine hooked up in our lab to help students out with the audio/ video engineering projects and they're all pleasantly surprised.

Since no one has hit the topic of a separate /home partition, I'll say its really up to you. Keep in mind that you cant (or shouldn't) have a machine with two forms of linux on it sharing one /home partition, because different flavors use and save different (hidden) files in there differently. {To see these files, you can plress Cntrl- H} in your home folder.

 Anyways, there are several advantages I can attest to. The most obvious is  if you screw up royally, you can go in, do a fresh install, and all your precious files are still there -- important for you since you have a lot of songs. Basically, its the same concept as having an external backup drive.

---

### Post by AnLGP on 2008-04-01
Ah I understand.  I have checked into ubuntu studio from a wubi standpoint, but never from a fresh install from a disc.  Is there anything on studio that I can't get on Ubuntu?

Also, just so it's clarified; I'm not using a wubi install anymore.  I requested a disc from canonical a while ago.

---

### Post by miesnerd on 2008-04-01
no. Part of the beauty of linux is that you can add packages usually with no problem. To convert from ubuntu to ubuntu studio, in the terminal type:

sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video

and you should  be there. Warning though, it will take a while. Whereas ubuntu ships on a cd, ubuntu studio ships on a dvd and those packages are big. Personally, i like the default dark studio theme better.

---

### Post by AnLGP on 2008-04-01
Thanks.  I think I'll back up my data and ditch windows first.  I have a different theme I use all together anyway, so that's not an issue.

---

### Post by Matthewslf on 2008-04-01
I'd just like to say that I had Ubuntu Studio for a while until I did something really stupid with SDL that killed all my games. I loved it will I had it and fully reccommend it.

---

### Post by AnLGP on 2008-04-01
Thanks for the recommendation.  I don't game much so that's not really an issue.

---

### Post by Matthewslf on 2008-04-01
Just for clarification, Ubuntu Studio supports games just as well as regular ubuntu. I just installed SDL from terminal on top of a synaptic install, which was stupid and crippled SDL. It had nothing to do with Ubuntu Studio.

---

### Post by NightwishFan on 2008-04-01
I read the thread title and I had to post my thoughts:
```
YAAAAYY!!!!
```
No im just kidding. I believe Ubuntu Studio and Ubuntu are essentially the same thing with different default look/apps.

---

