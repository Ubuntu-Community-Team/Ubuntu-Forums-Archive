---
title: "wth is wrong with that monkey?"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by aks44 on 2007-10-31
OK, so I just did a clean install of Gutsy (Kubuntu).

After much struggle (Adept SIGSEV/SIGABORT'ing with no apparent reason, Kopete SIGSEV/SIGABORT'ing with no apparent reason, ......), [dealing with incorrect DPIs]("http://ubuntuforums.org/showthread.php?t=585012") etc I finally managed to have a somewhat "stable" (ahem) system.

My main concerns with 7.10 currently being:

- When I boot up the computer, X goes wild and [displays giant fonts]("http://ubuntuforums.org/showthread.php?t=585012"). I have to Ctrl+Alt+F1 / sudo kill kdm / startx to have a correct display.
- kdesu barely asks me for a password, most of the time it just runs the root application... is that a new Microsoft-style security thing?


[B][SIZE="3"]Well anyway the most annoying thing is the font DPI problem (see my other post), the strange part is that when I use startx it is OK.
Would it have something to do with that bulletproof thing? If so, how can I disable it?
[/SIZE][/B]

I was so happy with Feisty, I really wonder why I installed this Gutsy thing... And I am still waiting to see any single promise that Gutsy is supposed to bring...

---

### Post by zhanglini on 2007-10-31
> **aks44 said:**
> I was so happy with Feisty, I really wonder why I installed this Gutsy thing... And I am still waiting to see any single promise that Gutsy is supposed to bring...

Yeah, from the experience I have had so far with Linux (Feisty and Gutsy) since Sept, I would rather they do a new version every year, instead of every 6 months.  Probably they can spend more time making the thing better this way.
And on users' side, is it not too nerdy to upgrade/install the operating system every 6 months?
Just a thought.

---

### Post by aks44 on 2007-10-31
Bump... anyone have an idea about how to disable BulletproofX ?

---

### Post by aks44 on 2007-10-31
That's the part I like the most about UF... ask a trivial question, you get hundreds of answers... Ask anything even remotely specialized, and noone seems to be able to answer.   :mad:
Thanks for the "help" anyway, I guess I'll get back to a working version (Feisty).

---

### Post by ThrobbingBrain66 on 2007-10-31
Have you ruled out a bad burn?  checked the iso with md5sum?
Those errors with adept and kopete shouldn't be happening on a fresh install.  Did you stop to think the errors with Adept are causing all of your other problems?

I guess what I'm saying is, a slow reburn of a md5sum'd iso and new install might not be a bad idea.

I think you just answered your own question.  Something "remotely specialized" means not many people have had experience with it.  Therefore, you may have to wait more than 3 hours (number of hours this thread was open at time of posting) for a reply.  Not everyone reads UbuntuForums all day....people have jobs, families and other commitments.

Sorry if my post got a little heated....I'm sick of everyone complaining about Gutsy.  I'm sure it's not perfect for everyone, but it's not nearly as bad as some people make it out to be.

---

### Post by linuxlizard on 2007-10-31
> Yeah, from the experience I have had so far with Linux (Feisty and Gutsy) since Sept, I would rather they do a new version every year, instead of every 6 months.

Just use the long term support version (I forgot- is that breezy badger?) it's supported 3 years and more stable. hardy heron is going to be another lts release. 

From the user side, if stability is most important, then simply don't install every release. I've done that in the past- I'll wait a month or so and visit the forums- if there are lots of problems I'll just wait for the next release.

---

### Post by st33med on 2007-10-31
FYI, LTS doesn't mean it is more stable, it just means it is supported longer.

---

### Post by -grubby on 2007-10-31
> **linuxlizard said:**
>  (I forgot- is that breezy badger?

dapper drake

---

### Post by NT4usB on 2007-10-31
That would be Dapper Drake...
I had it on my mythmaster. It worked ok for a year. Which is to say, I only ever thought about it and/or restarted it for kernel upgrades.
HD playback was flaky so I tried to fix it the 'Windows way"... upgraded to Feisty.
Feisty sucks on it. I have to restart every night, if I want to watch HD. Backend crashes 3-4 times a week and I lose a day of programming. Really thinking of going back to Dapper on this one.

I tried Breezy,  Dapper, Edgy, Then Feisty, on a couple PIII's I have laying around. Took days to get anything resembling an install on them.
And they sucked. Slower than when they had 2K on them. 

All this babble, and I finally get to my point.
I put Gutsy on the PIII's and it's sweet! Boxes are fast enough to be usable.
Windowsthinking says the older, less 'advanced' (bloated) releases should run better but in this case, Gutsy worked best.
So, the latest greatest is not all around bad. Like any other software, it's not perfect on all platforms and configurations. But it works.

---

### Post by aks44 on 2007-11-01
> **ThrobbingBrain66 said:**
> Have you ruled out a bad burn?  checked the iso with md5sum?
Those errors with adept and kopete shouldn't be happening on a fresh install.  Did you stop to think the errors with Adept are causing all of your other problems?

I guess what I'm saying is, a slow reburn of a md5sum'd iso and new install might not be a bad idea.

I did md5 checks before / after burning the disk, and burnt it at 4x. 


> **ThrobbingBrain66 said:**
> Something "remotely specialized" means not many people have had experience with it.  Therefore, you may have to wait more than 3 hours (number of hours this thread was open at time of posting) for a reply.  Not everyone reads UbuntuForums all day....people have jobs, families and other commitments.

Of course you're right, sorry for being a bit harsh in my previous post, that thing was driving me mad.
Now that I have Gutsy installed, I may as well try to fix it I guess.



The display is all messed up when I boot up (the login screen has unreadable tiny fonts, the desktop has giant fonts), resetting the X server changes nothing, but killing it from the terminal and restarting it fixes the display problem.

This has to have something to do with some autodetection performed at boot time that startx doesn't do.

Any ideas where I should look at?

---

### Post by OldTimeTech on 2007-11-01
Maybe it's your display...instead of X.

---

