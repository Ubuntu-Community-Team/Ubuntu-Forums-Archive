---
title: "Speed comparison Win2k VS Edgy"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Bobus on 2007-05-01
OK, I've been using Linux for a few months now and have to say I managed to find replacement for almost all applications I was used to on Win2k. The only issue I have with Ubuntu Edgy Desktop is it's speed (not really the system but rather applications).

Here are some results - tested on my overclocked AMD Athlon 4000+, 1024MB RAM. Both systems are 32bit. Time measured manually, so may not be exact, but makes the image.

**Test 1:** System boot time (seconds):

Lin: 106
Win: 56

*Note: both systems initialize Apache2+MySQL5 servers, desktop enhancements (Beryl and WindowBlinds). Windows also runs a screenshot program (Hypersnap), antivirus (Norton 2003), PocketPC synchro tool (MS ActiveSync), graphic card overclocking tool and ad blocking tool (AdMuncher). Other settings are default*

**Test 2: **Mozilla firefox 1.5 (cold boot / warm boot) (seconds):

Lin: 7.3 / 1.9
Win: 5.2 / 1.7

[I]Note: Same extensions were used on both systems
Note: I tried prelink and Swiftfox and didn't prove any of these additions make radical difference.[/I]

**Test 3:** Opera 9.20 (cold boot / warm boot) (seconds):

Lin: 5.3 / 1.2
Win: 3.4 / 1.2

*Note: Winner of the whole "advanced webbrowsing" competition (no Galeon, Epiphany, Kazehakase, Lynx or IE) is MyIE2 (Maxthon) with 1.7 / 0.8 boot times. Sorry that it does not run on Linux...*

**Test 4:** Image manipulation tools (cold boot / warm boot) (seconds):

Lin (GIMP): 3.6 / 2
Win (PhotoshopCS): 8.3 / 2.5

**Conclusion:** WHATTA?! Do I miss something?! Linux seems to be slower in almost all applications I use, not mentioning the best applications don't even run on it... Anyone has an idea how to fix that?

---

### Post by starcraft.man on 2007-05-01
Ummmm.... is 2 seconds the end of the world? I don't see your point. If you think you can make Ubuntu load programs faster than do so, otherwise take ubuntu for what it is. A linux distribution. Its NOT a windows replacement, people should remember that.

Not to mention, I don't see how its a valid comparison, win2k and Ubuntu are coded very differently... from the foundation up. Anyway, this isn't really a "problem" per se, and this forum is for well beginner problems....

EDIT: I just thought of something, if your so concerned with speed. Just consider this... with Ubuntu you will never have to defrag or virus scan again. That alone will save you hours. So there we go, I think thats a good enough response. This pseudo problem is resolved.

---

### Post by LaurelLynn on 2007-05-01
Actually the average of Tests 2-4  seems to be about the same.  And the longest program delay was about 2sec longer for Ubuntu and almost 5sec for XP. Also these test probably have less to do with the os, than with how the programs were ported.  The Win->Lin aps clearly seem slower, and GIMP is faster.

Test one is 2 - 1 in favor of XP. That doesn't indicate much though as startup times very greatly from one computer to the next.  Windows is particularly known for getting bogged down with vendor added startup programs as time goes by.  Virus scannes also can produce major slowdowns in all programs.

Also, that ratio might change quite a bit if you follow one of the guides on speeding up the boot process. Several steps probably are not needed on your machine.  XP has fewer options for this as the os kernal and much of the boot process are off limits.

Once a program is running though there is no inherent advantage either way, as ultimately the same machine code is being run on the same processor. It is a question of the OS and library calls which can very widely from one library to the next even on the same OS.

---

### Post by Rui Pais on 2007-05-01
Startup apps time is not an indicator of speed. 

Whats the importance of an app that runs heavily and for a long time to load a few secs sooner or later. 

With Gimp resize or unsharping the same very big image on both system, uncompressing the same big file, rendering something, formating an identical long text, running a test code with some loops with numerical calculus+io file... that will get a much decent comparison, although identically useless, since, as mentioned before, both system are too different to be compared.

Another thing. With you specs your edgy takes more then 1,5 min to boot? You must have a problem somewhere. whats take that long?

---

### Post by starcraft.man on 2007-05-01
> **Rui Pais said:**
> 
Another thing. With you specs your edgy takes more then 1,5 min to boot? You must have a problem somewhere. whats take that long?

I didn't really pay attention to that but I've got to say I'm at a loss for that too, in my experience Ubuntu always boots real fast. I boot into Ubuntu in less than 10 seconds from cold, including my login.

---

### Post by LaurelLynn on 2007-05-01
Actually, I think I know what may be the culprit.

I read somewhere else that the timeout default for DCHP is 60sec. So if like me, you use a modem connection, and/or have static addresses on your local net. You could end up spending as much as a minute longer looking for a DCHP server that isn't there, unless you disable this check.

---

### Post by juxtaposed on 2007-05-02
> Speed comparison Win2k VS Edgy

Comparing an operating system that came out 7 years ago and one that came out in the last few months isn't going to be that balanced.

But anyway, I think Windows 2000 is probably faster then linux on most things, sure. It's older and has less in it.

---

### Post by Bobus on 2007-05-02
OK guys, thanx a lot for the answers.

Running applications will not get any faster, right? OK, I take that. Really, 2secs will probably not kill anyone.

DHCP issue is a good idea. Might be turned off.

So:

1. How do I actually find out what exactly is being started during boot?
2. starcraft.man, what do you not run to make it boot THAT fast?
3. Will running 64bit version make it any faster?

---

### Post by Rinzwind on 2007-05-02
> **Bobus said:**
> OK guys, thanx a lot for the answers.

Running applications will not get any faster, right? OK, I take that. Really, 2secs will probably not kill anyone.

DHCP issue is a good idea. Might be turned off.

So:

1. How do I actually find out what exactly is being started during boot?
2. starcraft.man, what do you not run to make it boot THAT fast?
3. Will running 64bit version make it any faster?


1st question: ctrl alt F1 during boot :) 
2. my laptop takes 29 seconds to boot :) 
3. No.

---

### Post by Rinzwind on 2007-05-02
> **Bobus said:**
> OK guys, thanx a lot for the answers.

Running applications will not get any faster, right? OK, I take that. Really, 2secs will probably not kill anyone.

DHCP issue is a good idea. Might be turned off.

So:

1. How do I actually find out what exactly is being started during boot?
2. starcraft.man, what do you not run to make it boot THAT fast?
3. Will running 64bit version make it any faster?


1st question: ctrl alt F1 during boot :) 
2. my laptop takes 29 seconds to boot :) 
3. No. 

> **starcraft.man said:**
> I didn't really pay attention to that but I've got to say I'm at a loss for that too, in my experience Ubuntu always boots real fast. I boot into Ubuntu in less than 10 seconds from cold, including my login.

Proof it :)  Cuz I want that too. 
Even Grub takes a few seconds. 
Oh and we are talking about a boot from a hard-disc not a ram-disc, I hope  ;)

---

### Post by timzak on 2007-05-02
What hard drives are each OS on?  If the same hard drive, which OS is installed first on that hard drive?  Hard drive performance difference could be enough to cause the discrepency you're seeing (especially when you consider the "warm boot" results--which factor the hard drive out by running from mostly ram--are so close).  If both OSes are on the same drive, then the OS that was installed first will have the advantage because it is closer to the inside platters, where transfer rates are always faster.

---

### Post by thefoolisme on 2007-05-02
Timzak's question about the different hard drives is a valid one.  Plus, how can you compare Win2K to Edgy?  Edgy's not 7-8 years old, and has more capabilities added to it.  Compare Win XP or Vista to it would be a better comparison.

---

### Post by starcraft.man on 2007-05-02
> **Rinzwind said:**
>  Proof it :)  Cuz I want that too. 
Even Grub takes a few seconds. 
Oh and we are talking about a boot from a hard-disc not a ram-disc, I hope  ;)

Lol, why do I suddenly get the feeling I must defend myself from prosecution :p.

Honestly though, my computer does boot cold, my bios page only flashes for 1 second, and I get grub right after that and I set it to 2 second delay (I don't often boot xp). Then my bar well just fills up fast, in 2-4 seconds, then I log in. Maybe its just over 10 seconds, I didn't count exactly.

I didn't do anything special to get it to boot that fast. I even run a 5 year old P4 with ata hard drive. :) I do keep my startup list short though, only added beryl and emerald, and removed restricted manager and evolution, don't use either.

I can't really prove it though, I don't have a working vidcamera... both of our old ones are junky. Maybe I can get a cameraphone from a friend.

---

### Post by Rinzwind on 2007-05-03
> **starcraft.man said:**
> Lol, why do I suddenly get the feeling I must defend myself from prosecution :p.

Honestly though, my computer does boot cold, my bios page only flashes for 1 second, and I get grub right after that and I set it to 2 second delay (I don't often boot xp). Then my bar well just fills up fast, in 2-4 seconds, then I log in. Maybe its just over 10 seconds, I didn't count exactly.

I didn't do anything special to get it to boot that fast. I even run a 5 year old P4 with ata hard drive. :) I do keep my startup list short though, only added beryl and emerald, and removed restricted manager and evolution, don't use either.

I can't really prove it though, I don't have a working vidcamera... both of our old ones are junky. Maybe I can get a cameraphone from a friend.

You betcha. Consider yourself sued :+

Thing is: my laptop doesn't have to do alot and still it takes a rather long time. And I don't see anything about errors. And a 10 sec boot would be a nice goal for my laptop :D

---

### Post by starcraft.man on 2007-05-03
> **Rinzwind said:**
> You betcha. Consider yourself sued :+

Thing is: my laptop doesn't have to do alot and still it takes a rather long time. And I don't see anything about errors. And a 10 sec boot would be a nice goal for my laptop :D

Lucky I'm in canada, makes me immune to law suits :p 

sorry though, I dunno what I did to make it boot fast... it just does. Only thing I can suggest is to reduce the wait time for grub before selecting and remove some things from sessions, other than that I didn't do anything >.>

---

### Post by Rui Pais on 2007-05-03
> **starcraft.man said:**
> Lucky I'm in canada, makes me immune to law suits :p 

sorry though, I dunno what I did to make it boot fast... it just does. Only thing I can suggest is to reduce the wait time for grub before selecting and remove some things from sessions, other than that I didn't do anything >.>

do you use any proprietary driver like nvidia or fglrx? (they are always slow loaders to me)
do you install it using default install method or server/alternative/minimal? do you used the x/k or u of the _buntu ones? 
what do you mean "remove things from session"? do you mean from boot process? do you used bum, sysv-rc-conf or something like that?

aren't you sure that your 10s aren't those kind of 10s that usually take 20 secs to happen? ;)

i have a core 2 duo (the ones that use electrical energy to produce speed instead of heat :)) and my boot time at best chances is 20s with nv, a minimal install "cleaned" with sysv-rc-conf...

btw, here is a better and much more informative ways to "measure" boot time, [bootchart]("http://www.bootchart.org/samples.html"). It's in repos (never tried).
[here]("http://www.bootchart.org/images/bootchart.debian.mcrae.0.png") and [here]("http://www.bootchart.org/images/bootchart.debian.mcrae.1.png") and "pics" from an  normal and an optimized boot process.

---

### Post by Rui Pais on 2007-05-03
ok i decided to try it...
here are a "pic" of my boot :)

---

### Post by hartz on 2007-05-03
Hi Bobus,

I really don't care how long my Linux takes to boot - I only do it about twice a year, and that is because of power failures.

But I agree that your tests indicate a possible problem - Responsiveness is important in an application/desktop environment, and affects the users' perception of how well the system is performing.  

However, there are many factors that could affect your experience.  For example which desktop/window-manager are you using?  If you switch to Xfce or fluxbox, you might find that it makes a large difference.  Give Xfce and Fluxbox a whirl to see if it makes a difference.  Other considerations are what file systems are you using, how is your swap-space configured (Don't make the mistake of thinking that you have enough RAM and not giving Linux some swap space), and even silly things like how many fonts you have installed.

Most Importantly:  Where on the hard drive is your Linux partition(s) located, compared to where your Windows partition is?  Did you use a dual-boot setup with Windows near the start of the disk and Linux near the end?  I have seen a performance difference of between 4 to 10 times slower between the very first and very last tracks on hard drives.  So if your Linux is near the tail end of the hard drive, you may not be comparing apples-to-apples.

Note: You can also get The Gimp for Windows.

But Linux does not guarantee faster performance - it is often achieved and you can tweak the living daylights out of a Linux system, but sadly it is not guaranteed to be faster, at least not out-of-the-box.

---

### Post by 3rdalbum on 2007-05-03
> **starcraft.man said:**
> I boot into Ubuntu in less than 10 seconds from cold, including my login.

Impossible. The LinuxBIOS guys have a minimal Linux with a minimal X and a minimal window manager come up from cold in 9 seconds; and that thing is running straight from the Flash on the BIOS.

---

### Post by Rui Pais on 2007-05-03
ok, playing around a little more with boot services, redo profile and setting CONCURRENCY=shell (a danger one) the shorter i get is going from charted 21s to 18s :P

I tried with and without readahead, and boot time remained the same, so i let it stay. 
Funny thing, readahed delays kjourlad section begin from the 8s to12s... although it seems to end at same time.

pic as attach.

---

### Post by InuyashaDuelist on 2007-05-03
Edgy ran a lot faster than Win2k for me, and Feisty runs even faster than that.

---

### Post by Nekiruhs on 2007-05-03
I actually have actually seen Ubuntu boot alot faster than XP, my machine boots in about 30 seconds. And my comparison between open office on XP and Ubuntu is that Ubuntu starts WAYY faster (Like 15 Secs) faster on Ubuntu (With systray quickstart disabled).

---

### Post by starcraft.man on 2007-05-03
Ahhhhhhhhhhh, geez, this thread still going? Can't we all just live with what time we boot with? I mean I do leave my computer on most of the time, I usually have a movie transcoding, a file downloading or some other process running...

I think I'm gonna hide from this thread >.>

---

### Post by lakersforce on 2007-05-03
My experience is that WinXP boots quite a lot faster than Ubuntu to the desktop. At the desktop WinXP takes a long time  to initiate everything, while it is fast on Ubuntu.

Ubuntu becomes slower at boot over time, just as windows does.

---

### Post by Rui Pais on 2007-05-03
> **lakersforce said:**
> 
Ubuntu becomes slower at boot over time, just as windows does.
Ubuntu or your desktop environment (gnome, i presume)?

---

### Post by syadnom on 2007-06-12
the reality is that a fresh copy of XP will boot quite a bit faster than any ubuntu BUT a used XP will boot quite a bit slower.  

to be clear here, from the first day one uses an ubuntu system on, the system boots in roughly the same amount of time or within 5 seconds or so depending on a couple of daemons that start.  XP will quickly get clocked up and take longer and longer to be at a usable desktop.

---

