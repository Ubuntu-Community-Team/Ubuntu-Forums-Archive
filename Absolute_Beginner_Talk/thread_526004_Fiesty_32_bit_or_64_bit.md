---
title: "Fiesty 32 bit or 64 bit?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by mikawber on 2007-08-15
I've browsed through the forums but haven't really found a solid answer. I am about to build a new computer and am wondering if I should install the 32 bit version of Feisty or the 64 bit version. What are the benefits and drawbacks of the 64 bit? I already run the 32 bit version on a different computer so I'm just curious about the 64 bit. Heres what the specs of the computer will be: 

Intel Core 2 Quad 2.4GHz
2GB DDR2 1066 RAM
XFX GeForce 8600GT 256MB

Thanks

---

### Post by tgm4883 on 2007-08-15
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by ravenus on 2007-08-15
A friend of mine uses the 64-bit version and he is mostly happy with it but he has problems with some applications.

As for benefits, isn't one of the main benefits of 64-bit that it can address more than 4GB of RAM? I don't know how useful that is right now.

All this is just layman talk fro me, I'm sure more informed opinions will come after this :)

---

### Post by Arthur Archnix on 2007-08-15
To summarize the above (very informative!) link, let me say:

Download the 32 bit version. 64 offers very real benefits, but at present, only to very specific people. Those who do intense scientific mathematic calculations, or those doing professional (I mean Hollywood movie level) image and video editing. 

Unfortunately, at this time, and for the next few years, unless you're in one of these two groups, you should go with 32.

EDIT: and yes, if you have LOADS of ram, +4Gigs, then you should also look at 64. Thank you above poster.

---

### Post by tgm4883 on 2007-08-15
> **Arthur Archnix said:**
> To summarize the above (very informative!) link, let me say:

Download the 32 bit version. 64 offers very real benefits, but at present, only to very specific people. Those who do intense scientific mathematic calculations, or those doing professional (I mean Hollywood movie level) image and video editing. 

Unfortunately, at this time, and for the next few years, unless you're in one of these two groups, you should go with 32.

EDIT: and yes, if you have LOADS of ram, +4Gigs, then you should also look at 64. Thank you above poster.

What!?!  Any number crunching app written for 64-bit can see an improvement.  Encoding Video (say, into an xvid perhaps?) can see a 30% reduction in the amount of time it takes.  Get your facts straight before you start spewing out nonsense.

And lets just for a second pretend that what you said about the two groups is true.  Why would it be detrimental to install the 64-bit version instead of the 32 bit version.  Anything that can be done on 32-bit can be done on 64-bit.

To the OP, read the advantages and disadvantages of 64-bit (the link I posted above).  Don't listen to these losers that don't know a computer case from a wet paper bag.

---

### Post by Arthur Archnix on 2007-08-15
tgm4883  is rigtht, though, I was answering simply from the question that you asked. The fact is that your life will be easier using 32bit, though tgm4883 is right you may see some benefits from 64.

Despite the fact that tgm4883  is technically correct, based on your original question, I would still recommend installing the 32bit version of Ubuntu.

If you'd like, you can always keep 8 gigs free at the end of your hard drive during partitioning (you'll have to use manual install during the installation) and then after getting comfortable with Linux and ubuntu installing the 64 bit version. That way, if you decide that the 64 bit version is worth it you can delete your 32 bit ubuntu and go straight with the 64. Note that some extra partitioning effort will be required to do this. You should make two 8 gig ext3 partitions, a swap partition of 512MB-1GB, and the remainder a files partition (ext3, set to /mnt/myfiles). Install root and home (/ and /home) to the first 8gig partition, mount the second 8 to /mnt/ubuntu64).

Anymore questions please ask.

Best wishes,

---

### Post by wolfen69 on 2007-08-15
dont be stupid, 32.

---

### Post by PurposeOfReason on 2007-08-15
> **wolfen69 said:**
> dont be stupid, 32.
So is it stupid to use 64bit? I use it with no problems at all and everything I need works fine.

---

### Post by RomeReactor on 2007-08-15
Hi. Please, let's take this calmly. No need for aggression or name-calling.

There are some very real benefits to running a 64-bit OS (increased speed in processor-intensive applications), as well as problems (while not catastrophic by any means and they can be solved, flash and java can be troublesome to set up for new users); however, it all really depends on what **mikawber** is planning to do with the computer. **mikawber**, please post your intended use, and we'll try to provide you with a more concrete answer.

I don't think we should be bickering; this is a support forum, not the Cafe.

---

### Post by Arthur Archnix on 2007-08-15
Of course it isn't stupid to use 64. But you will encounter problems that 32 users will not. You need to ask yourself if the benefit of using 64 bit programs (i.e.  the 64bit compatible programs)  you'll be using, versus the 32 bit programs you'll have trouble -- not impossible, but more trouble than if you were running 32 bit OS - is worth it.

A good general answer, for those that don't know whether or not to use 64 or 32, is to use 32 and then change up afterwards once they learn more about the specific programs their using and the benefits that they will get from switching to a 64bit OS.

Remember that this is Ubuntu, and our goal in these forums is usability. Those that are hardcore performance freaks use Slack, or Arch, or Gentoo... Ubuntu can do performance, but newb questions like the OP deserve to hear what's easiest to use.

EDIT: You should know that my own answers are only based on what I've read in other places, as I have no direct experience with using a 64 bit system. I was, as I hope you'll understand, only trying to relay that small bit of "education" (if I may call it that)  to you. I'm sure you will come to your own informed decision.

Best wishes,

Arthur

---

### Post by tgm4883 on 2007-08-15
> **wolfen69 said:**
> dont be stupid, 32.

Open Source/Open Mind
Ubuntu User #15003
Linux User #448521

Open Source/Open Mind my ***.  

I must be 3X Stupid for running 3 64-bit machines.

---

### Post by Kilz on 2007-08-15
> **wolfen69 said:**
> dont be stupid, 32.

Please tell me you didnt really think about what you wrote before you posted it. How many new users are going to read your comments and follow the (imho) bad advice you give?

Exactly how smart is it to buy 64bit hardware and put a 32bit operating system in it? Would you buy a corvette and pull out 4 spark plugs? How about buy a car and take off 2 tires? 

I will read my own signature, I will read my own signature, I will read my own signature!

---

### Post by mikawber on 2007-08-15
Thanks for your replies and advice. 

Well I won't be using the computer for advanced video editing but I will be doing some. I'm rather new to Ubuntu so I don't want to get into trouble that I can't handle.

---

### Post by Kilz on 2007-08-15
Give 64bit a try, there isnt anything the average computer user has to fear from the 64bit version.
Both versions have their problems, 32bit users seem to not notice the thousands of 32bit related posts all over the Ubuntu forums. But instead seem to focus on the past problems of the 64bit version. Try the version made for your hardware, give it a month. Post any issues you have to the 64bit sub forum, and like every other part of the forums, people will jump in to help you.

---

### Post by mikawber on 2007-08-15
> **Kilz said:**
> Give 64bit a try, there isnt anything the average computer user has to fear from the 64bit version.
Both versions have their problems, 32bit users seem to not notice the thousands of 32bit related posts all over the Ubuntu forums. But instead seem to focus on the past problems of the 64bit version. Try the version made for your hardware, give it a month. Post any issues you have to the 64bit sub forum, and like every other part of the forums, people will jump in to help you.

Ok I think I'll try it out. Will any 32bit program work on the 64bit version?

---

### Post by Hobo Joe on 2007-08-15
I'm happily using 64 bit with no problems. Not even flash. 
Also, I would like to say that it has a DEFINITE speed increase. From things as simple as opening an application, to doing 3D renders, or to doing high-level image editing or render that is processor-intensive.

With 3D renders I get at least a 40% speed increase, and with image editing/rendering I get abut 60% speed increase.

To put it simply, 64-bit owns.

EDIT:

> Ok I think I'll try it out. Will any 32bit program work on the 64bit version?

There are 64-bit versions of nearly every Ubuntu program. For most of the rest, you can just compile them for 64 bit.

---

### Post by RomeReactor on 2007-08-15
> **mikawber said:**
> Ok I think I'll try it out. Will any 32bit program work on the 64bit version?

You *might* have trouble setting up wine; to get java working for Firefox 64 bit, install the Blackdown Java package (search for **j2re1.4** in Synaptic); for flash, use [this script by Kilz]("http://ubuntuforums.org/showthread.php?t=476924").

Otherwise, you should be fine. I'm using Feisty 64 bit, and the system **is** slightly faster; for processor-intensive applications, it is noticeably faster. For me, the difference in speed was worth the switch, and the system is perfectly stable. I suggest you at least download both Feisty CDs (the 32 and 64 bit versions) and try them both, either running them as Live CD or, if you can afford to make room for both on your hard drive, dual boot for a couple of weeks and see with which one you are most comfortable.

---

### Post by Hobo Joe on 2007-08-15
> **RomeReactor said:**
> You *might* have trouble setting up wine; to get java working for Firefox 64 bit, install the Blackdown Java package (search for **j2re1.4** in Synaptic); for flash, use [this script by Kilz]("http://ubuntuforums.org/showthread.php?t=476924").

Otherwise, you should be fine. I'm using Feisty 64 bit, and the system **is** slightly faster; for processor-intensive applications, it is noticeably faster. For me, the difference in speed was worth the switch, and the system is perfectly stable. I suggest you at least download both Feisty CDs (the 32 and 64 bit versions) and try them both, either running them as Live CD or, if you can afford to make room for both on your hard drive, dual boot for a couple of weeks and see with which one you are most comfortable.

The live CD isn't a very good representation of speed though, even though it loads to RAM, it still accesses the CD a lot, which slows things down considerably. I look at the live CD as more of a way to see if things WORK, not how fast they go.

---

### Post by RomeReactor on 2007-08-15
> **Hobo Joe said:**
> The live CD isn't a very good representation of speed though, even though it loads to RAM, it still accesses the CD a lot, which slows things down considerably. **I look at the live CD as more of a way to see if things WORK**, not how fast they go.

That's **exactly** one of the reasons I suggest he uses them. Note that I also suggested a dual boot as a sort of trial period.

---

### Post by Hobo Joe on 2007-08-15
> **RomeReactor said:**
> That's **exactly** one of the reasons I suggest he uses them. Note that I also suggested a dual boot as a sort of trial period.

Oh, I thought you meant more as a speed test, my mistake. :)

In that case, I totally agree with you.

---

### Post by Kilz on 2007-08-16
> **mikawber said:**
> Ok I think I'll try it out. Will any 32bit program work on the 64bit version?

There may be some 32bit application that doesnt work. 
But you will not need to install any 32bit applications. What applications are you concerned about?


> **RomeReactor said:**
> **You *might* have trouble setting up wine**

Nope, wine is available for Feisty as a 64bit deb[ from wine]("http://www.winehq.org/site/download-deb"). They even have a repository you can add so it you get updates.

---

### Post by RomeReactor on 2007-08-16
> **Kilz said:**
> Nope, wine is available for Feisty as a 64bit deb[ from wine]("http://www.winehq.org/site/download-deb"). They even have a repository you can add so it you get updates.

Yes, [I'm aware of that]("http://ubuntuforums.org/showthread.php?p=3187410#post3187410"); the issue is not with the installation process itself, but with the actual setup, according to some websites and a few posts around here. In any case, the problems seem to have been [reduced to Gutsy now]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/43324"), so it should run properly in Feisty.

By the way, nice Watchmen avatar! :biggrin:

---

### Post by mikawber on 2007-08-16
> **Kilz said:**
> There may be some 32bit application that doesnt work. 
But you will not need to install any 32bit applications. What applications are you concerned about?

I'm mainly concerned about Firefox, Thunderbird, AmaroK, Audacity, and a few others. Those are my main programs that I couldn't do without.

---

### Post by PurposeOfReason on 2007-08-16
> **mikawber said:**
> I'm mainly concerned about Firefox, Thunderbird, AmaroK, Audacity, and a few others. Those are my main programs that I couldn't do without.
They'll all work. I'm pretty sure you can get 64bit packages for most, if not all of those.

---

