---
title: "can someone please help me :("
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by taintedheir on 2007-08-09
I cant run the live cd... dont want to install just yet...  But I've heard so many great thinks about Linux and Ubuntu and want to try it out.. I got the live CD in the mail a few hours ago and cant seem to get it to work... it boots yes.. but when I select for it to (start or install) it takes me to a black dos like screen with numbers and letters at the bottom.. with bits of code like (err 00000000 and *flag blah blah)  and there is a blinking |  on the top left (god I feel like such a n00b...haha)

please help?

---

### Post by tdrusk on 2007-08-09
> **taintedheir said:**
> I cant run the live cd... dont want to install just yet...  But I've heard so many great thinks about Linux and Ubuntu and want to try it out.. I got the live CD in the mail a few hours ago and cant seem to get it to work... it boots yes.. but when I select for it to (start or install) it takes me to a black dos like screen with numbers and letters at the bottom.. with bits of code like (err 00000000 and *flag blah blah)  and there is a blinking |  on the top left (god I feel like such a n00b...haha)

please help?
How much RAM do you have?

---

### Post by bren on 2007-08-09
what is your hardware (processor / memory)

---

### Post by phr0ze on 2007-08-09
please provide details about your PC. How much ram, what processor, what video card, what sound card. THanks.

---

### Post by taintedheir on 2007-08-09
running 1024MB ram, celeron 2.53GHz, Vid is intergraded into motherboard (good enough for newer win based pc games ;) ) realtek AC'97 audio card.  my comp might be old... but it is able to run window xp and vvv well

---

### Post by CowzRule on 2007-08-09
You might have a bad CD. There's an option in the boot menu for testing it.

---

### Post by por100pre1 on 2007-08-09
It should run fine with those specs... Keep in mind that it takes a while to load because it doesn't touch your hard disk. Does it freeze somehow? Any error messages?

---

### Post by spur on 2007-08-09
I agree sound like a bad disk. Can you download a new one? If not you may have to get another sent or find a magazine with a live cd.

---

### Post by philinux on 2007-08-09
In the meantime, reboot your live cd , go and make coffe watch tv come back. It takes ages to unpack the OS.

---

### Post by taintedheir on 2007-08-09
I had this copy mailed to me because my burner drive is dead... just using my read only drive :(
I'll test my disc and see if its ok... how long does it take to boot?

---

### Post by splintercellguy on 2007-08-09
Like probably 5-10 minutes, since CD media can be quite slow.

---

### Post by taintedheir on 2007-08-09
cool..trying that now... be back in a bit
(hopefully with good news!)

---

### Post by philinux on 2007-08-09
On my old old pentium III about 10 minutes. But once installed it really goes

---

### Post by taintedheir on 2007-08-09
okok... i get the same thing when i go to test disc as if i try to run Ubuntu from Live disc...; same blinking | in top left corner.. and 2 lines of code at bottom... do I need to change some setting before trying to run live disc?
help..maybe? or should i just have a pint or two and worry about it later... I'm just excited about trying (maybe switching to)something that allot of my mates are using.
p.s. sorry for sound like a pain... just excited :biggrin:

---

### Post by toidi on 2007-08-09
You shouldn't need to change anything other than your boot options (which you clearly have done.  Sounds like a dodgy disk or a dodgy drive.

Also I downloaded the x86 version of ubuntu and when I tried to install it (got to the desktop first) it just hung at 76 percent.  Got the 64 bit and it worked a treat.  Might have a little relevance to your problem.

---

### Post by raylu on 2007-08-09
> **taintedheir said:**
> okok... i get the same thing when i go to test disc as if i try to run Ubuntu from Live disc...; same blinking | in top left corner.. **and 2 lines of code at bottom**... do I need to change some setting before trying to run live disc?
help..maybe? or should i just have a pint or two and worry about it later... I'm just excited about trying (maybe switching to)something that allot of my mates are using.
p.s. sorry for sound like a pain... just excited :biggrin:

Sounds like you need to turn acpi off.

---

### Post by taintedheir on 2007-08-09
explain this acpi option please :)

---

### Post by EXCiD3 on 2007-08-09
Here's a little bit if information from my HP laptop thread on this:

> 
If boot hangs or fails, reboot. At the menu press F6 and add these parameters
Code:

noapic

NOTE: Only adding 'noapic' to the boot parameters has been reported to disable the USB ports. Only adding 'nolapic' has been reported to prevent the NVIDIA driver from loading correctly. However use of both 'noapic and 'nolapic' is not know to cause these problems. Also if you use "IRQPOLL" or "IRQFIXUP" along with "noapic" will enable usb support. Feedback on this would be appreciated.

You can view the full thread here: [http://ubuntuforums.org/showthread.php?t=512059]("http://ubuntuforums.org/showthread.php?t=512059")

---

### Post by taintedheir on 2007-08-09
alright... going to try this.. *crosses fingers*

---

### Post by EXCiD3 on 2007-08-09
hmm, 40 mins w/no reply... Guess I'll just assume the worst, it installed fine and he's having so much fun using Ubuntu he can't take a min to post the good news... ;)

---

### Post by taintedheir on 2007-08-09
i cant get past this (and this is even after adding the ```
 noapic
``` as EXCiD3 recommened

the two lines of code at the bottom are
```
Int 14:  CR2 ef800000 err 00000000 EIP c020c384 CS 00000060 flags 00010007
stack: c00f8050 c03f129b c0371d8c 00000002 c00f8059 000f8050 00000000 00000000
```

but sat on that same screen... with that damn blinking | in the top left corner

pfft... thats all i can say pfft

---

### Post by taintedheir on 2007-08-10
??? anyone??

---

### Post by EXCiD3 on 2007-08-10
You wanna post your exact specs of your computer for us.

---

### Post by UK-Wobbie on 2007-08-10
> **taintedheir said:**
> I cant run the live cd... dont want to install just yet...  But I've heard so many great thinks about Linux and Ubuntu and want to try it out.. I got the live CD in the mail a few hours ago and cant seem to get it to work... it boots yes.. but when I select for it to (start or install) it takes me to a black dos like screen with numbers and letters at the bottom.. with bits of code like (err 00000000 and *flag blah blah)  and there is a blinking |  on the top left (god I feel like such a n00b...haha)

please help?

What's your CD/DVD Drive speed? 
If you made a ISO DVD or CD disk it is better on burning it as slow like 2x
And i say it's better on a DVD disk then a CD it will run better :)

---

### Post by henriette_holm on 2007-08-10
I'm guessing that you have Windows on your computer? Maybe you should try and boot into that, out the cd in the drive and test the md5sum to see if the cd is ok.

Can somebody provide a link? Don't have one at hand.

/Henriette

---

### Post by raylu on 2007-08-13
I figured that, by merely mentioning "acpi," you guys would be able to get at what I was thinking...

Instead of using noapic, use:
```
acpi=off
```
There are some similar options in help (read the F#s at the bottom of the screen)

---

