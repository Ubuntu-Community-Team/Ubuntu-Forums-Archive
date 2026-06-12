---
title: "Brand-New Ubuntu 7.04 - Two Issues"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Spektyr on 2007-06-23
Okay, not only am I brand-new to Linux in general and Ubuntu specifically, but the install is literally days old on the computer I'm testing it with.  Currently my wife is the main user of this computer, since she primarily web surfs and other non-demanding tasks (and my XP machine is trying very hard to have a severe mental break-down, so it has to be treated with kid gloves).

There's just two things that the Ubuntu machine does or doesn't do that need to be addressed so that my wife doesn't drive me nuts.

Video Issue:

I can't figure out why, how, or reproduce this effect on demand, but any image seems to have the capability to become permanently corrupted.  It reminds me of when another image overlays something, and then when it's removed the display forgets to refresh the image underneath properly.  Except the Ubuntu machine never, ever refreshes.  In fact, it maintains this after-image vehemently.  If you reload the screen, the artifact reloads in the picture just as before.  If you right-click the image and select View Image or anything of that sort, the artifact remains.

As near as I can tell, nothing short of a reboot will fix the problem.  Is there some kind of keystroke combination that will force the machine to reload images from original source rather than memory?  (Or better yet, some way to avoid the issue to begin with?)

Relevant data:

Ubuntu 7.04
Via Technologies VT8633 [Apollo Pro266 AGP] Integrated video.

If you need more hardware data let me know.

This problem shows up most in Firefox (because that's what my wife uses most) but also showed up in some of Ubuntu's packaged games included the one that's basically Othello.


The "Other Issue".

My XP machine, for reasons that are anyone's guess, absolutely refuses to work with my wife's Dell Pocket DJ.  Now I'd read a thread here the other day about how to make it work on Ubuntu... it had something to do with Gnomad2 and lbj-something (?) and so forth.

What I need is an idiot's guide to making that work - something step-by-step a monkey could follow.  Or at the very least a pointer back to that thread (I can't seem to find it now).  I'd prefer the moron-proof version, as this will be the absolute first thing I've ever installed on a Linux box, but I can poke it with sharp sticks and grunt my way through if I have to... I just need some idea of what to get and where to hammer it into the OS, and that thread had links.

I *thought* I'd bookmarked it, but clearly I didn't.

Thanks in advance.

---

### Post by Spektyr on 2007-06-23
Okay, just discovered something else that's a bit disturbing:

I plugged the DJ in just to make sure it didn't already work (it doesn't seem to).  Then I went to Places and clicked Computer.  It opened a button on the bottom that said "Starting Computer" and the mouse went to the working icon for a bit, then went back to normal and the button disappeared.  The Computer will not open.  Nor will anything else on the Places menu.

So I figured I'd restart.  I clicked the Power button at the upper right and nothing happened.  Then, while I'm typing this a few minutes later, the shutdown window pops up.  I reboot and the computer works normally, allowing me to open things on the Places menu for a little bit, then as I'm working in the Network window the window spontaneously closes and the problem shows up again.  Nothing works from the Places menu once more.

Help?

---

### Post by molly_001 on 2007-06-23
Spektyr --

When is the last time you tested this machine for memory problems?  (testing RAM modules)

I would strongly suggest to do that.  The LiveCD of Ubuntu will provide you with that option from its main menu -- let it run overnight.

Or you can burn MemTest86 (.iso image) to a bootable CD, same difference.

---

### Post by abn91c on 2007-06-23
on the windows XP PC sounds like you may have a virus or a Trojan, try running ad-aware
or spybot. Also this website [http://probemyports.com](http://probemyports.com) will check the security of you windows machine for free. Another good site for windows diagnostics is [www.pcpitstop.com](www.pcpitstop.com), you have to register(free also)

---

### Post by Spektyr on 2007-06-23
I know what's wrong with the XP machine.

I need help with the Ubuntu machine.

---

### Post by Spektyr on 2007-06-23
I ran the RAM test twice (I'm looking to find out what's wrong quickly, rather than slowly if possible).  On test #5 it spit out about 254 errors each time through in the upper end of the memory range.

Before I place the order for new memory (which I plan to do shortly) how likely is it that this is the problem causing the artifacts in the pictures?  99%?  90%?  50%?  Same with the things not opening in the Places menu?

If it's not pretty certain to be the cause I need to track down and eliminate other potential causes.  (I do not want to tell my wife that all we have to do is shell out 50-some bucks on memory to fix that problem, only to find out that we spent the money and the problem persists.  I like being married.  Happily married.  And not sleeping on the couch.)


Also, I still need some help with the Dell DJ.

---

### Post by Spektyr on 2007-06-24
Still need some input on the picture issue.  (Got the Dell DJ working, though.)

---

### Post by swoll1980 on 2007-06-24
I would say your looking at a 99% chance that this is whats causing your issues

---

### Post by swoll1980 on 2007-06-24
I would say 100% but I guess nothings 100% exept  death and even that might change

---

### Post by Taliskerd on 2007-06-24
Ubuntu-newbie myself, I'll stick to what I Do know;
"how likely is it that this [RAM] is the problem causing the artifacts in the pictures?"

I'd put that in the upper 90% range!
...and then the question is What Ram?
Video cards have a Lot of onboard memory these days, so start by swapping that for a borrowed card and see if the problem show up within a day or two.

Once Ram start to go bad, you can usually expect anything to go wrong without warning.
Since the errors show up in the higher memory areas, I guess that if it's not the video card, problems should not show up in the first few hours (at least), since most applications /OS:es fill memory from 'below'.

Please keep us posted.

---

### Post by Spektyr on 2007-06-24
Okay, next question:

This computer's move to Ubuntu was prompted by the sudden and complete death of its previous hard drive.  I mean this thing failed in a way I've never seen or even heard of before.  It actually makes a sound like a small alarm klaxon if you simply plug it into a power supply and turn it on.  "BEEEooop" over and over, every 15-20 seconds.

Do you think it's just coincidence that the memory is going bad at the same time, that one caused the other, or should I be looking for perhaps a third problem that caused both the hard drive and memory damage?  Like I said before, I don't want to tell my wife I've found the problem and fixed it only to have it fall apart again in a couple weeks.

EDIT: no video card is installed - it's running off onboard video which is sharing 32 MB from the system memory.

---

### Post by Taliskerd on 2007-06-24
The klaxon would be your bios complaining about something, but the 15 second interval is new to me. If you have the manual for the motherboard, check the beep pattern.

From now on, my money is on Bad Ram.

---

### Post by Spektyr on 2007-06-24
No, I know what the computer beep sounds like.  This sound is coming from the hard drive.


EDIT: just in case it isn't clear, this is not the hard drive that is currently in the computer - it's already been replaced.

---

### Post by molly_001 on 2007-06-25
Spektyr --

At this point, have you yet tested your RAM with the Ubuntu install option from its main menu?

Or with a MemTest86 bootable CD?

You can run it while you are away, or asleep.

---

### Post by Spektyr on 2007-06-25
That question was answered on the previous page.

I'm now hoping to get an answer to my next question above, which concerns whether it's most likely just coincidence that the previous hard drive failed right around the same time as this memory problem, or if one problem probably caused the other, or whether I should check for a third problem that caused the other two.

After all, if something ate the hard drive and chewed on the RAM, replacing both doesn't help much unless you fix the cause.

---

### Post by molly_001 on 2007-06-25
Sorry I missed your earlier answer.

It's impossible to answer with sureness the question.  First, you don't know that the problems occurred (originated on a time scale) at or near the same time.  Instead -  you merely (it seems to me) *detected* the presence of the two problems at or near the same time.  Resident memory problems can easily remain undetected until the hardware is pushed to its highest memory addresses consistently.

On the other hand, if your house was hit by lightning last weekend, then you have your answer.

Unfortunately, the only way to diagnose -- and fix -- is to test each component separately, eliminating all other possible factors as much as can be attained, to diagnose the issue.  And that's generally a problem, since only geeks like myself have spare, tested motherboards, CPUs, power supplies, memory modules, etc lying around the house.

---

### Post by Spektyr on 2007-06-25
Heh, I've got a few computers worth of spare parts laying around, but almost all of them fall into the "suspects of earlier hardware failures" category.  Things I know for certain are bad usually get labelled in Sharpie, but the pack rat in me is loathe to throw away even a blown motherboard for some reason.

Of course this makes component-by-component testing more difficult, to say the least.  (My hope is to some day build 2 or more identical computers, thus making it blindingly simple to swap parts in and out to find the problem.)


I'm not necessarily looking for a definite answer - I'm mainly trying to determine how reasonable it is for me to accept this as the problem and move on without further investigation.  When it only affects me I don't particularly care, but my wife frustrates easily.


I had a thought earlier that I want to run by you guys.  According to the memory test the problems were in the upper registers of the memory.  Also, the computer was recently switched from an AGP GeForce 4 to the onboard memory (since a different computer had a fan freeze up on its ATI Radeon card, and had to "borrow" the GeForce card from this computer).  So now 32 MB of the system memory - complete with problems - is being shared with the onboard video.

I could be wrong, but my brain vaguely remembers learning something about how when onboard video shares system RAM, it generally borrows from the upper end.  If that's true, wouldn't it fit perfectly with what's going on with the images and explain why the problem went undetected until now?

---

### Post by Spektyr on 2007-06-26
Okay, I just swapped in and out a whole bunch of different RAM.  It had two 256 MB sticks in it.  When tested independently they produced more errors than they do tested together.

Every single stick of RAM I tested produced errors on the same test (test #5).  This motherboard even allows DDR and SDRAM, and I tested both types.  Both types failed test #5.


So either every stick of RAM I tested has the same problem, or there's something else wrong.


Anyone want to help me figure out what it is?

---

### Post by molly_001 on 2007-06-26
Memory controller chip on the mobo.

Time for a new mobo, bud.

You did a good and thorough test by using all the RAM in that way.  Now you know it's the motherboard.  Would highly recommend you order a new motherboard and move forward towards productivity with the machine.

---

### Post by Spektyr on 2007-06-27
I ran a few more tests just to be 100% sure.  I jumpstarted the motherboard and memory off another computer (propped it up next to an open case and wired that case's power and CDROM drive to it to run a memory test) and then tested the memory in that known-good computer.

It is definitely the motherboard.

I've come up with a good spare motherboard that's older and slower, but will work.  Not certain if I'm going to go with that solution or just get a whole new motherboard, but now I need Ubuntu geeks for the final (I hope) step in this repair:


So I've installed a new motherboard... how do I adapt Ubuntu to the new hardware?  Do I have to start all over or can I retain the basics of the previous install - desktop settings, installed software, stuff like that?

How's it done?

---

### Post by molly_001 on 2007-06-27
The good news is that the configuration of Ubuntu (or any OS) is held on the hard drive, and not the motherboard.

The bad news is that you are not replacing the motherboard with an equal twin.

So this means that the config for Ubuntu which is expecting A Certain X motherboard chipset will find itself running on A Certain Y motherboard chipset.  Same for the sound controller, integrated graphics controller, etc.

So I think you should just make sure you have backed up your data (both NTFS and ext3) onto something external, and just start over from scratch with the new motherboard.  That way, both Windoze and Ubuntu (if dual booting) can configure themselves right at the installation of the OS.

---

