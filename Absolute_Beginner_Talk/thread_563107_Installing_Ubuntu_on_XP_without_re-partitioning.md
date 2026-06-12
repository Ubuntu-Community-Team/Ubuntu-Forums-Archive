---
title: "Installing Ubuntu on XP without re-partitioning"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by papasworld on 2007-09-29
Is it possible to install Ubuntu on my XP machine without re-partitioning my existing drive?  I've tried Wubi but to no avail.   I've tried the Live CD (minus sound / internet / home network for some reason) and now want to install permanently.

Any ideas?  Am I the only person who is not willing to re-partition? 

Thanks

P

---

### Post by dpar on 2007-09-29
As far as I know, you would have to repartition.(I may be wrong though,it's happened before.:) )

Or you can install another drive and put it on that one.

---

### Post by madmatrixz3000 on 2007-09-29
I say it is best to just spend a few bucks on a small HD and just install it on there.  Or else I would say just deal with the partition.  Installed is the best way to go.

---

### Post by papasworld on 2007-09-29
Thanks for your replies.

Would you not recommend the Wubi route?   I'm getting the impression that Wubi is not as easy as the web-site makes it out to be.

---

### Post by bodhi.zazen on 2007-09-29
+1 Wubi 

[http://wubi-installer.org/](http://wubi-installer.org/)

It is in "beta" though ...

---

### Post by raycosm on 2007-09-29
Wubi did a funny thing for me, when I installed using Wubi, it separated /home and /, which I have no problem with, but /home was always about 1 GB, even when I chose to use 9 GB for Wubi. If that wasn't supposed to happen, I'm not smart enough to know how to fix it.

Unless that happens to you, you're probably fine, unless you want to use hibernate, then that won't work.

---

### Post by papasworld on 2007-09-29
Well, Wubi downloaded and installed the dual-boot 'thing' but when I rebooted to install Ubuntu, it got as far as 'detecting hardware settings' and then the screen went blue.  No amount of random key-pressing / chanting would bring it back so I had to reboot back to boring old XP.  Still can't work it out ...

Is it Wubi or is it Ubuntu or me?

---

### Post by papasworld on 2007-09-29
Oh forgot to ask, what is '/home' and why is that different to '/'?

I'm a total and utter noob btw :-) ...

---

### Post by bodhi.zazen on 2007-09-29
for basic partitioning see here : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

For wubi support see here : [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

You might want to search or post on that forum ...

---

### Post by papasworld on 2007-09-29
Yes looked there but couldn't find anything with a similar problem.

Is it definitely Wubi that's at fault then?  And there's no other way to install without re-partitioning?

---

### Post by papasworld on 2007-09-29
Did you say *basic* partitioning?  Because that thread just totally bamboozled me.

Maybe I'm not cut out for the world of Linux ...

---

### Post by oilchangeguy on 2007-09-29
> **papasworld said:**
> Is it possible to install Ubuntu on my XP machine without re-partitioning my existing drive?  I've tried Wubi but to no avail.   I've tried the Live CD (minus sound / internet / home network for some reason) and now want to install permanently.

Any ideas?  Am I the only person who is not willing to re-partition? 

Thanks

P

ok, this problem has already been addressed in another of your threads. so don't make another thread on the same subject. the answer is not going to change. you can't install ubuntu on the same partition as windows, they use different file systems. and do not use beta software (wubi) you're making this way to hard. simply insert the live cd, when the desktop loads, select the install icon. and follow the prompts. do not allow ubuntu to use the entire drive. and do not get wraped up in manually partitioning, i'd suggest using the largest space option. and let ubuntu set it's own partitions. and back up your windows data, BEFORE you do anything else.

---

### Post by bodhi.zazen on 2007-09-29
> **papasworld said:**
> Did you say *basic* partitioning?  Because that thread just totally bamboozled me.

Maybe I'm not cut out for the world of Linux ...

LOL, I know the feeling

It gets easier ...

---

### Post by papasworld on 2007-09-29
Thanks for replying.

To be fair, I didn't feel the question HAD been answered in my other questions - you're the first person to explain the differences in the operating systems to me (I didn't know they used different file systems for a start).  No-one had come outright and said I couldn't do it - they *suggested* I re-partition which is not something I'm comfortable doing.

Regarding posting other threads, using support forums like this, questions that get pushed down off the first page don't tend to get answered.  I'm sorry if I broke a forum rule but I'm totally new to this one.  Every forum has it's own etiquette and obviously I've over-stepped the mark - which is why I've tried to remain in the absolute beginners section because that's what I am (and isn't that what it's for?)

Lesson learnt an' all that.

Regards

P

---

### Post by bodhi.zazen on 2007-09-29
Well, we are here to help you if we can. Starting a with a new operating system is overwhelming and frankly frustrating.

You are welcome here and I do not think you offended the community, we all see you, and all new users, as welcome.

Let us know if we can be of further assistance ~ I see that spark of initial understanding ...

---

### Post by oilchangeguy on 2007-09-29
> **papasworld said:**
> Thanks for replying.

To be fair, I didn't feel the question HAD been answered in my other questions - you're the first person to explain the differences in the operating systems to me (I didn't know they used different file systems for a start).  No-one had come outright and said I couldn't do it - they *suggested* I re-partition which is not something I'm comfortable doing.

Regarding posting other threads, using support forums like this, questions that get pushed down off the first page don't tend to get answered.  I'm sorry if I broke a forum rule but I'm totally new to this one.  Every forum has it's own etiquette and obviously I've over-stepped the mark - which is why I've tried to remain in the absolute beginners section because that's what I am (and isn't that what it's for?)

Lesson learnt an' all that.

Regards

P



yes windows xp uses ntfs as it's file system, (the nt file system has been around since before win 95, scary huh. anybody remember windows nt?) and ubuntu uses ext3. you'll find as linux distro forums go. ubuntu has by far the best forum. but alot of people get way to wound up in doing everything they can manually. and will scold you if you want to do otherwise. when in fact most people just want an operating system to work, without having to look under the hood to do the slightest task. and i'm all for doing things as easily as possible. so dive in, set up your dual boot system. and if you have more questions feel free to come back and ask.

---

### Post by Pumalite on 2007-09-29
Fear of the unknown is as old as the Stone Age, but you are not the only one, and we are here to help you.

---

### Post by papasworld on 2007-09-29
Thanks guys for your help and words of encouragement.  I'll give the partitioning a go and see what happens.  Got to do my backing up first though ... :-)

I'm convinced it's going to be worth the effort!  It's like cheesecake - it's the future :D

Regards

P

---

