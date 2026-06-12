---
title: "Success story: dual boot Ubuntu 7.0.4 and Windows XP Home Edition"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by vmsda on 2007-08-29
(Warning: this is bound to be a longish append)

A. Project Objective: Achieve the projected dual boot situation with minimum time investment, and in a responsible way, technically speaking. Hardware environment: HP Pavilion dv5000.

B. Preparation: I read as much as I could about problems encountered by others with the same hw. Also found from dual boot related appends that there were many solutions, but somehow practically all of them failed for one reason or another.  Eventually, I settled for the approach described in _[http://help.ubuntu.com/community/WindowsDualBoot](http://help.ubuntu.com/community/WindowsDualBoot)_ (which I will outline below for the benefit of scapegoats like me), because it offered a step-by-step which I could control at key points.

C. Execution (from section Issues with Windows XP and NTFS of above referenced document)
     Step 1: Do a Windows backup [ok]
     Step 2: Defragment the Windows disk [ok]
     Step 3: Download System Rescue CD ISO image [ok]
     Step 4: Burn ISO into a CD [ok]
     Step 5: Boot from the CD and Enter when prompted with boot: [ok]
     Step 6: On command prompt, enter: run_qtparted [ok]
     Step 7: Select your disk on the graphical screen [no graphical screen on show; had to 
                   read a whole screen of text to find out that i had better type: startx]
     Step 8: Select NTFS partition to be resized (likely /dev/hda1) [have to find in the screen
                   something resembling a disk box, click on it]
     Step 9: Choose Resize option [ok]
     Step 10: Set the new partition size [ok]
     Step 11: Commit your changes in the File -> Commit menu [no such menu available; 
                     chose Apply option instead]
     Step 12: Remove System Rescue CD and insert Ubuntu 7.0.4 Live CD [here I interrupted
                    the sequence to check things out: (a) tried to shutdown gracefully from the 
                    Rescue CD but had to do it the ugly way (power off); (b) Switched on, Windows 
                    came up, smelled a fish, did a chkdsk, asked to be restarted, restarted just fine,
                    I checked and Windows only saw 30 GB disk (previously 89). This was my first 
                    control point.]
     Step 13: Inserted Ubuntu CD, chose Install [ok]
     Step 14: In the Prepare Disk Space, chose option Guided: use largest continuous free 
                    space [ok]
     Step 15: System did a lot of copying, configuring, etc; downloaded and installed 118
                    sw updates, everything ran absolutely without a itch. [Second control point done]
     Step 16: Shutdown and let Ubuntu come up again to make the updates firm [ok]
     Step 17: Shutdown, power on again, chose Windows, everything working normal [last
                    control point]. :lolflag:

It feels good to bask in the glory of such a minor success, but I cannot help reflecting about
all I went through to get to this point. I think that Ubuntu as an organization in particular 
and Linux as a solution in general have serious CREDIBILITY and CONSISTENCY issues.

D. Many of the appends on dual boot make for stark reading indeed: myriad solutions
    attempted and failed. It is not at all clear, for a newcomer to the Linux world, how to hit 
    upon a solution with no ifs and buts, the success odds are just as good as in the lottery.

E. A newcomer wants one of two things: (i) a Linux clean install method (not the most likely),
    or (ii) a dual boot alternative (probably the most realistic in the day-to-day). A newcomer 
    does want to read something like the following, written in a Ubuntu official doc, obviously 
    written by someone in-the-know: "Although the Ubuntu Installer does now include support
    for resizing NTFS partitions, it is not 100% effective". Being 90% effective may be ok for a
    knowledgeable techie, but for a beginner it may mean he does not have his old Windows,
    his new Ubuntu, or both. So please come up with solutions that not only WORK, but work
    AS DOCUMENTED. Or, in other words, adopt RESPONSIBLE SOLUTIONS that provenly do NOT
    WASTE OTHER PEOPLE'S TIME.

F. Part of the problem may come from a siege mentality one detects while reading the fora:
    (i) "well, you came to us, you are disappointed, you know what is best for you, go back to
    Windowze"; (ii) "you have to be prepared to spend a lot of time, Linux is good for who 
    wants to tweak things"; or still (iii) "you know, bottom line, going Linux is an ideological
    thing, man, for run-of-the-mill daily grind stuff, don't come here". This holier-than-thou
    attitude is just what Mr. Gates needs to laugh all the way to the bank; with enemies this
    entrenched in their own backyards, he can even afford to scale down on his friends.

G. Now, ideologues such as those depicted in the previous paragraph are not as stuffy as 
     one might think: they are the ones whose dedication and downright soul are vital to any
     project; but we must also recognize that, marketing wise, ideologues are their own
     preferred market segment, the rest can join in after they learn all the ropes.

H. The other day I was reading some article written by or on behalf of Mark Shuttleworth, at
     the end of which he voiced the hope that the Ubuntu project would pay for itself: I beg to
     differ, if things go as others and I have experienced. The Ubuntu organization must make
     a conscious overarching effort to bring on board as many people as possible, possibly with
     a two-pronged solution: a responsible, consistent and credible migration-from-Windows
     offer; and, to give the people a realistic chance to really appreciate Linux from the inside,
     step-by-step projects of the "Linux from Scratch" or "Pocket Linux" persuasion, which will
     help people learn the ropes through a sense of achievement.

I submit to you that the failure of Ubuntu and like-minded organizations to catch a 
significant share of the desktop market place is a two-fold tragedy: first, the principles and
values imbued in the free software environment are destined to remain the privilege 
of a few; second, countless people will be prevented from exercising their creativity, 
for lack of access to an environment such as Linux, uniquely suited for that very purpose.

Thank you for listening.

---

### Post by hyper_ch on 2007-08-29
> **vmsda said:**
> I submit to you that the failure of Ubuntu and like-minded organizations to catch a significant share of the desktop market place is a two-fold tragedy: first, the principles and values imbued in the free software environment are destined to remain the privilege of a few; second, countless people will be prevented from exercising their creativity, for lack of access to an environment such as Linux, uniquely suited for that very purpose.

What failure? Linux is about freedom and choice... even the choice to not use it... that's up to everyone... those that do not want to learn it don't have to... we don't wanna force them... however if you want to learn, then you will get the help you need ;)

And regarding transition from windows to linux: Most problems arrive with incompatible hardware... that's not the fault of linux or ubuntu but of the hardware manufacturer that don't release drivers or don't help coders write opensource drivers...

What might be working for you, may not work on a different system, hence all the different tutorials are fine. And regarding the partition may work or may not work... this has not much to do with the tech-knowledge of one... either the partitioner works or it doesn't... if it does not you need to use an alternate method ;)

However the precautiosn you have taken and the time you actually took to make clear what you're going to do and where the risks may lay... not many people do that... so that deserves respect... and good you have a good lineout in section a ;)

---

### Post by anewguy on 2007-08-29
I don't understand why you went to such an extent to install Ubuntu,  If you just boot the LiveCD, choose install and do a manual configuration of the hard disk, you are allowed right there to resize the Windows partition and create your Linux partitions, and the installation just goes on from there.

Is this a simple, trouble-free OS?  Of course not.  I've worked with OS's that cost us over $10,000 a year just for the PRIVILEGE of USING IT not even owning it.  Those OS's are not problem free either. 

The biggest problem there is for Linux is trying to keep everything free.  This provides little attraction to hardware manufacturers to create drivers for their hardware in an environment where their effort would be free (you know they have to make money or they have no need to stay in business).  The result is thousands of people trying to find ways to make things work.  Sometimes it's not as simple as "run this file" or "put in this CD".  Additionally, Linux was and still is too technically oriented, because that's the people who are making it work.  Believe me, if you have seen Slackware in 1996 and look at Ubuntu now, the difference in installing, configuring, etc., is huge.  Big steps have been made.  Does more need to happen?  Sure.  It will always be that way - it's the nature of an OS beast.  Remember that manufacturers are forced to make their hardware work with Windows as dictated from Microsoft.  Microsoft is large enough it can make such demands of manufacturers.  And all of that revolves around nothing more that just dollars.  So with Linux, or any other free OS, you are going to see varying opinions of what works and what doesn't.  Most of that is centered on purely hardware issues.  A video card that works in box A in Linux may not work in box B.  This is because of the various and endless combinations of hardware and then drivers without a profit driven company behind the scenes saying "you must do it this way, period".  Thus it becomes a matter of interpreting what you read, not just taking it as gospel that my machine will work if I just do "x".  

The confusion you seem to have is reading the posts (a good thing) but not being able to ***interpret*** them.  If you are looking for a "how to" you need to look in that forum.  You also need to be able to read something, do some thinking for yourself, then try things out.


Linux is not a perfect world, neither is Windows or any other OS.  There are only a select few people here who make the judgemental sayings you mention:  (1) people who don't know, but rather than just admit ignorance (ignorance is not a crime) they instead get defensive  (2) the old techie die hards.  But here's the thing - the people making those statements are few compared to those of other OS's.  I don't give a darn what anyone uses - what ever works for them is fine for me, but there are people with everything in life who think their way is the only way and you are a fool for thinking differently.  If you can't defend yourself against those opinions, then you also probably shouldn't  bring them up in any context.

Now, don't think I'm up on some throne preaching Linux.  Linux can be trying, if not downright difficult to get installed and running with all of your hardware as you want.  There is a lot of trial and error involved by the individual.  Sometimes you do see some one give a smart-*** answer or talk condescendingly.  That is unfortunate and doesn't do much for promoting Linux.  Ubuntu, and Linux as a whole, is not yet ready to be a true competitor in the home user market.  Sorry my fellow Linux friends, but it is the truth.  Sometimes these types of remarks are replied to with comments saying "if you want it as easy as "x" then just choose "x" and leave Linux alone".  My take on these people is that they are from the die hard techie group who don't want things screwed with just to make it more competitive with something like Windows.  They instead say "learn it or go away", when instead (in my opinion) they should be saying "hey, it lets me do all of this great stuff so I want to help you in your journey as well".  There has been a big push in the magazines, etc., about Ubuntu and it being a replacement for Windows.  The problem is that the vast majority of Windows user don't know and don't care to know squat about their machine - all they know is they bought it with Windows installed, took it home, plugged it in, and everything has been working".  To push for a larger Ubuntu/Linux presence in that group of users, there has been a failure to keep things so stupidly easy that any one can install it and use it.   But that is also, ironically, caused by one of the principle differences between a Microsoft or whoever product and a free product like Linux.  It's built on the idea that you have the right to choose the things you want and don't want in your OS.  Don't like the default Window handler?  Try one of the myriads of others.  This basic ideology of freedom is what makes Linux possible.  It's just a matter of so many more choices than "x" OS that it's almost impossible to automate a good install.  Ubuntu, and other distros, should be congratulated on the progress towards this they have made.  While you may not care or need to know the reasons why, it is a major development to have a LInux distro that is made as easy as possible to be installed and usable "out of the box".  Very large steps have been taken, and yes, some big ones still remain.

For me, and only by my choice (like I said I'm not preaching about any OS), I decided to go with Ubuntu as my installed OS and for the 1 thing I need Windows for I have a virtual machine running Windows XP I can use - network access, usb device, etc., access all given.
For me, it took a while to make that choice.  Am I an expert at Linux?  To paraphrase something from the old Rosanne show, "I'm so far from ever being an expert it takes the light from expert a million years just to reach me"!:)

We all have our individual reason for choosing what ever OS we want, and we shouldn't bother someone just because some chose something different than what we might have.  It's not fault free here, but it's far cry from where it started, and it's free!:) (I just had to throw ONE of those in you know!:) 

Best of luck on whatever road you choose.  :)

---

