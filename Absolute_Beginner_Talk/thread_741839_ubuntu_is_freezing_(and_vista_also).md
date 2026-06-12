---
title: "ubuntu is freezing (and vista also)"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by codpawn on 2008-04-01
i have
intel pentium d 3.0ghz
intel d101ggc
seagate 320+80 ide hard drive
xfx 86gt 256
hynix 2gb ddr ram


on this config i can run xp
but i cant run vista and ubutu
both os freezes after some time

ive checked my ram theres nothing wrong with it

can any 1 tell me what the hell is wrong with my system

ive properly installed all 3 os's (xp,vista,ubuntu7.10)

i dont wanna run vista on my pc but i wanna run ubuntu

plz help me!!!!

---

### Post by ByteJuggler on 2008-04-01
**_How_** have you checked your RAM?  Have you run an exhaustive memory test?  

I would also suggest you run a CPU stress test, perhaps [Orthos]("http://www.techpowerup.com/downloads/385/").  (Note, it is a Windows application, and it has several modes to run in, some of which is more CPU focussed than others which is more RAM focussed.)

The fact remains the problems you describe basically suggest hardware problems of one sort or another.

---

### Post by Bushfire on 2008-04-01
If it is the system that's frozen (i.e. not just X; try <ctrl>+<alt>+<f1>, does anything happen?), and it happens in both Ubuntu and Vista, then it is most likely a hardware problem of some description. I assume you've ran memtest and got nothing. The only way we can figure out what's wrong is if you can reproduce it. Has any hardware been acting strange lately (other than the computer as a whole, obviously)? Try taking out your CD drive and run for while, that kind of stuff. See if you can isolate the problem.

---

### Post by codpawn on 2008-04-01
ive checked my mem with the memtest

and ive also tried usin my friends memory 

i faced the same prob!!!

---

### Post by Xiong Chiamiov on 2008-04-01
Though it usually will cause restarts, a good thing to check is air ventilation, since it's an easy fix.

But what the others said is true, that it is a hardware problem, not software, as far as we can tell from the information you've given us.

---

### Post by codpawn on 2008-04-01
yeah i know thats hardware problem 

but how can i fix this 

and one thing xp runs completly fine on my system

---

### Post by codpawn on 2008-04-01
> . Has any hardware been acting strange lately (other than the computer as a whole, obviously)?

my hardware runs fine on all oprating systems

---

### Post by Xiong Chiamiov on 2008-04-01
> **codpawn said:**
> my hardware runs fine on all oprating systems

...except for the fact that they freeze.

Also, it's the operating systems that run on the hardware, not the other way around.
You seem to be a little confused about how computers work (which is not bad!), but think that you you aren't (which is), and I'm just getting more and more confused as to what you're talking about.  It could possibly be just a communication problem, but you should know that I don't quite understand you.

---

### Post by ByteJuggler on 2008-04-01
Can you please run Orthos for several hours in each of its modes, and report back whether or not that succeeds.  Thanks.  If it fails, post back under what mode it failed.

---

### Post by codpawn on 2008-04-01
iam doin that test right now 

& for how much time do i have to run that test?

---

### Post by codpawn on 2008-04-01
> ...except for the fact that they freeze.

Also, it's the operating systems that run on the hardware, not the other way around.
You seem to be a little confused about how computers work (which is not bad!), but think that you you aren't (which is), and I'm just getting more and more confused as to what you're talking about. It could possibly be just a communication problem, but you should know that I don't quite understand you.


ohh yeah 

sorry my hardware works fine on win xp 

but i dunno what goes wrong with other oprating systems

---

### Post by codpawn on 2008-04-01
ive checked with the orthos

it says no problems detected for the stress cpu-stress cpu with gromacks core(in 3hrs)

and 

and the test of blend- stress cpu and ram 
says 0 errors, 0 warnings.(in 3hrs)

to the both cores

---

### Post by ByteJuggler on 2008-04-01
What about "Small FFT's - Stress CPU"?  Does that pass for several hours?

---

### Post by tango_ninja on 2008-04-01
Are all 3 systems on the same HD ?  Does Vista/Ubuntu not run at all or just freeze for extended periods of time?

You could have a physical disk error (bad sectors / deteriorating drive). I had this problem a few weeks ago where certain parts of the HD were failing and another partition was untouched. Eventually ended up getting a new drive......

---

### Post by codpawn on 2008-04-01
[QUOTEYou could have a physical disk error (bad sectors / deteriorating drive). I had this problem a few weeks ago where certain parts of the HD were failing and another partition was untouched. Eventually ended up getting a new drive......[/QUOTE]

my 320 h/d is 4 months old and its perfectly fine

---

### Post by Bölvaður on 2008-04-01
There are only 2 things I can think of you could try.

Run the Ubuntu livecd for a while and see if it freezes.
Replace your videocard and try to see if it solves anything.

---

### Post by codpawn on 2008-04-02
@Bölvaður

yes the live cd also freezes evan i was freezed while i was installing 

and ill try using my friiends video card

---

### Post by codpawn on 2008-04-03
I've tried replacing my 86gt wi my friend's xfx7950,


and again same problem popped up!!!:confused:#-o

---

### Post by Bölvaður on 2008-04-03
ok let us check what we have done.

RAM - ok (might be an obscure error)
Graphic - ok
CPU - ok
HDD - ? (probably ok)
Audio - ? (probably not the reason)
...
,,,
...

It is very strange but something like your audiocard might be causing the problem. You just have to make a list of your main components in the computer and check every one of them.

---

### Post by Dabbill on 2008-04-03
90% sure its your HD causeing the problems. I agree with the post above that part of your HD is dieing. HD's do just randomly fail, or random parts fail no matter how old the drive is. 

Like i tell my HP customers when they call in for support. I have a HD from 15 years ago that runs fine still today, but i also bought a HD a few months ago that had to be warranted out after 3 days cause it failed. Your best bet after you try useing your friends video card is to purchase a cheep HD.

---

### Post by codpawn on 2008-04-03
@Bölvaður's 

I don't use any external audio card I use onbord audio,

and no one in my friend circle use audio external audio card.


Are u sure that its audio card problem? 
If yes then I'll buy a new card tomarrow.


----------------------------------------------------------------------------------------------------
@Dabbil

I dont think its hard disk problem,
cuz I always defragment my hard dirve time to time.

---

### Post by Bölvaður on 2008-04-04
> **Dabbill said:**
> 90% sure its your HD causeing the problems. I agree with the post above that part of your HD is dieing. HD's do just randomly fail, or random parts fail no matter how old the drive is. 

True but his computer froze during a live-cd session.. that has nothing to do with hard disks.. as you know :D

I am not sure about the audiocard, but it is just an example of one of the things that might cause small problem that affects other hardware parts. It could actually be everything that is in your computer that is wrong, this is very tricky one.

But like I said, just make a list of all the hardware and unplug it one at a time to eliminate the items on your list.
There are programs that try to find hardware problems like these.

I am terribly sorry that I cannot help you any further through the internet :(

btw check all the wires on the motherboard and unplug every unnecessary ones (but write down where each wire was connected or take photo of it. It is obviously (or perhaps not) some electronic... stuff... problem.

---

### Post by ByteJuggler on 2008-04-05
> **ByteJuggler said:**
> What about "Small FFT's - Stress CPU"?  Does that pass for several hours?

I'm still suspicious of your CPU (and possibly your RAM.)  Have you tried the above yet, and what was the outcome, and also, I would suggest you try some other memory checkers as well as a control.  Also, for how long did you run the memory checker for?

---

### Post by codpawn on 2008-04-05
> **ByteJuggler said:**
> I'm still suspicious of your CPU (and possibly your RAM.)  Have you tried the above yet, and what was the outcome, and also, I would suggest you try some other memory checkers as well as a control.  Also, for how long did you run the memory checker for?

I've tried testing memory by  the memtest for 11hrs and I also tried cpu test  with the Orthos it said no problems found!!! :(

And also another thing, till now I've  tried everything but nothing solved my problem, can I buy new motherboard please tell me.

Iam willing to get 
Abit p35/XFX 650i ultra

---

### Post by ByteJuggler on 2008-04-07
> **codpawn said:**
> I've tried testing memory by  the memtest for 11hrs and I also tried cpu test  with the Orthos it said no problems found!!! :(

And also another thing, till now I've  tried everything but nothing solved my problem, can I buy new motherboard please tell me.

Iam willing to get 
Abit p35/XFX 650i ultra

You could... but I would suggest you swap out RAM and CPU first to try and isolate what the problem is.  (Easier to swap them out than the motherboard.) If you can't do this yourself easily, perhaps you can take the machine to a reputable computer shop to test/swap parts out.  By the way, what PSU have you got?

---

### Post by codpawn on 2008-04-08
I've already tested by swaping ram, not tried cpu I'll surely do that today 

Thanks

---

### Post by codpawn on 2008-04-09
i have umax 550w psu

---

