---
title: "How do you maintain your Ubuntu?"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by DeadEnd on 2006-01-17
Hi
I have used windows for many years and know enough about to repiar any problems.
I know nothing of Ubuntu and its inner working of linux and it is rather daunting when faced with any problem at the moment exactly what to do.
So my question what do I need to do to maintain Ubuntu.
And if at any time I get an error due to packages or dependancy issues , failed installs, is there a automated process, package, that could give me a bit of a hand hold while getting to grips with finding my way round.

---

### Post by 23meg on 2006-01-17
When you get such errors, it's best to post them here and ask for help if you know absolutely nothing, and learn in the process.

Regarding software installation, if you absolutely don't want to break anything you'd do best by sticking to the official repositories.

---

### Post by Mustard on 2006-01-17
[QUOTE=DeadEnd]Hi
I have used windows for many years and know enough about to repiar any problems.
I know nothing of Ubuntu and its inner working of linux and it is rather daunting when faced with any problem at the moment exactly what to do.
So my question what do I need to do to maintain Ubuntu.
And if at any time I get an error due to packages or dependancy issues , failed installs, is there a automated process, package, that could give me a bit of a hand hold while getting to grips with finding my way round.[/QUOTE]

If things are pretty straightforward and you understand what you are doing then I would just do it.  If you have doubts about how to proceed or what will happen if you do something, then come to the forums and just ask.  There is even an IRC channel in which a large number of ubuntu users hang out in and help each other with issues they might be having.  I learnt most of what I know concerning keeping my system stable and working from IRC.  There is the ubuntuguide, the ubuntu starters guide, the ubuntu wiki as well.  Then there is the search function in the forum, and finally searching via google.  All the information you need is out there, it just a case of learning how to efficiently find it and use it.

I found that hanging out in the ubuntu support channel on IRC while I was doing things on the computer was the easiest way to learn.  You don't have to chat with everyone.  You just leave it idleing and when you hit a problem you can pop up the irc channel and throw a question out there for everyone to read.  It's not always instant feedback, as sometimes people take there time answering questions, but it a bit faster than the forums at times.

---

### Post by dueY on 2006-01-17
[QUOTE=DeadEnd]

And if at any time I get an error due to packages or dependancy issues , failed installs, is there a automated process, package, that could give me a bit of a hand hold while getting to grips with finding my way round.[/QUOTE]

The good thing about Synaptic is if you use it you probably won't have these problems. :D

---

### Post by earobinson on 2006-01-17
I dont do anything, not defrag, no av scan, no firewall, no anti-spyware programs. ubuntu maintains its self very well and I have never had a problem

---

### Post by az on 2006-01-17
[QUOTE=DeadEnd]
And if at any time I get an error due to packages or dependancy issues , failed installs, is there a automated process, package, that could give me a bit of a hand hold while getting to grips with finding my way round.[/QUOTE]

Ususally, if you have the needed repositories, apt can fix itself.  Otherwise, anyone here on the forums can hold your hand if you post the error message you are getting.

Don't be shy.

---

### Post by DeadEnd on 2006-01-17
[QUOTE=dueY]The good thing about Synaptic is if you use it you probably won't have these problems. :D[/QUOTE]

Well major problem so far is actualling the damn thing to install.
Each and everytime time I install, after taking the CD out and it processes the packages I always get something along the lines of "not all packages were installed.
It is only a mtter of minuets before I attempt to download something or use a feature I know what package failed. 
So when ever I eventually get to the desktop half the features are missing, not only that some of the features are there but they have only half the function.
For example the synaptic manage at one time when I click reposeretries used to pull up a form where I could add or deleate source, but at other times after reinstall it just displays a page where all the sources are there but instead off add remove they are all there but with check boxes and ticks.
sometime I have gedit other times I dont,sometimes I have 15-16 choices in Administration other times I only have 5 or 6, at time I have a desktop but nothing else.
So in this case it has been difficult fix as I have to date, no clue what a fully functional default Ubuntu looks like.
This box I am attempting to install on runs server 2003,but non the less I have changed every moving part, CD/ hard drive even swopped Ram but still get errors.
MEMtest reports everythig is Ok and CD disc integrity check repors evreything fine but again I burned a cpl to be sure.
At one point the installation stopped and gave me a message" could not find kernal apt This is very strange and possibably fatal."

All in all I have had 30-40 errors all different all related to the installtion and only occur after I take CD out and it starts unpacking configuring.
So basically I need to know if there is some command line kung fu which if I get to desktop again I can type in terminal to check the installtion and repair or at least detail all the errors .
I have tried looking in Var but unfortunaly file browser seems to be a victim also.
BTW here is another thread where I actually assumed I was up and running again after stripping out hard drive but unfortunatly I spoke too soon
[http://www.ubuntuforums.org/showthread.php?t=115325&highlight=NTFS+samba](http://www.ubuntuforums.org/showthread.php?t=115325&highlight=NTFS+samba)

---

### Post by dueY on 2006-01-17
Your problem sounds very weird to me.  Does apt-get actually complain of any specific broken packages?  If you have broken packages it won't let you download new ones until you fix the broken ones.

---

### Post by dragonfyre13 on 2006-01-17
honestly, I would worry about my drive. Have you tried going into bios and playing around with the settings for the optical drive yet?

---

### Post by Mustard on 2006-01-17
Yeah, I would agree with others in that it sounds like a hardware problem of some kind, because its a very unusual problem to be having.

There probably are a number of 'magical commands' you could put in to complete the installation, but from your description it sound much more serious than just packages not being installed correctly.

---

### Post by DeadEnd on 2006-01-17
[QUOTE=dueY] Does apt-get actually complain of any specific broken packages?  .[/QUOTE]
No only message is t " some packages were not installed" .
it seems to be random what packages are actually missing after install compleates..

I have changed the CD drive twice and burned a cpl of copies , image intgrety check states they are fine .

---

### Post by DeadEnd on 2006-01-17
Just to say I am going through installtion again, I have basically stripped out all the parts apart from MOBO and replaced hard drive  /   CD drive / memory with known working hardware
Just to clarify this is not the sharpest pc in the draw its a p3  128mb pc100 RAM but quite happily runs server 2003 for days but I wish to run Ubuntu only on it instead, so its not even a multi boot ,just 2 partitions EXT3 and swap

---

### Post by dueY on 2006-01-17
[QUOTE=DeadEnd]Just to say I am going through installtion again[/QUOTE]

This sounds like your best bet.  Let us know if anything goes wrong again.

---

### Post by DeadEnd on 2006-01-17
Hi

Ran through CD install, took out cd rebooted it began configuring packages, around half way though this meassege appeared on the screen.

configuring tk8.4
453.411001 ex-fs error (hdc1) EXT3_xattr.delete
inode bad block 1 4296453.412000

---

### Post by az on 2006-01-17
[QUOTE=DeadEnd]Hi

Ran through CD install, took out cd rebooted it began configuring packages, around half way though this meassege appeared on the screen.

configuring tk8.4
453.411001 ex-fs error (hdc1) EXT3_xattr.delete
inode bad block 1 4296453.412000[/QUOTE]

Using the live cd run badblocks on the hard drive partition.  Then partition the drive to work around the bad blocks.


badblocks -w /dev/hdc1
(This erases all your data)

Or just go out and buy another hard drive....

---

### Post by DeadEnd on 2006-01-17
[QUOTE=azz]Using the live cd run badblocks on the hard drive partition.  Then partition the drive to work around the bad blocks.
Or just go out and buy another hard drive....[/QUOTE]

Ok so so far I have used 3 hard drives which run windows bfr I used Ubuntu.
2 are oldish drives so I will try your suggestion on badblock see if that fixes them thnx for info on that.

But for now I will try again with my 200GB hard drive 3 months old. 
Only problem is the BIOS will not recognise 200GB but Ubuntu does. but if I install like this at end of installation I get error "no operating found" but if I set the jumpers so it reports as 32 GB drive Ubuntu recognises it as 200GB and goes through installtion and I actually get to dektop but with package errors.

Trying install again:(

---

### Post by DeadEnd on 2006-01-17
Ive just had a thought after reading some threads, is it possible I could use my USB 2.0 hard drive caddy to install Ubuntu from my main machine and then place the drive in the older machine or will it throw a wobbly,they are worlds apart in tems of specs and procesor r is linux clever enough to recognise the change and load the appropriate drivers etc, if this is possible it could help me find the culprit

---

### Post by ras on 2006-01-17
I am a beginer too.  I think I had a similar problem, but I re-burned the iso at a slower speed and the next installation went fine, except for the GUI load-up...but thats another story.

---

