---
title: "live cd: x server fails to start"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by zetapotential on 2007-01-25
Hello,

I am very interested in trying ubuntu, so I obtained 6.10 and am trying it out.  The live CD boots up fine on my laptop, but on my desktop it gives the message "Failed to start the x server"

I tried following the instructions at

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

and it even detects my exact model of video card (ATI Radeon X600) and correct monitor.  But when I retry startx it still craps out again, saying "no devices detected".  I tried specifying VGA instead, and that didn't work; I finally got it to work by specifying VESA, but the graphics quality really sucks (for example scrolling in firefox is painfully slow)

Any advice is most appreciated.  Thanks!

---

### Post by zetapotential on 2007-01-25
Nothing new to add, but it's been 45+ minutes and nobody has even viewed my thread :(   I feel slightly ostracized... since I'm new around here, is there something wrong with the way I asked the question?  Thanks

zetapotential

---

### Post by The Tronyx on 2007-01-25
Well my first advice is not to get discouraged.  My linux machine is pretty low on hardware resources and also has problems with loading X servers for some Live distros.

First of all, let me make it clear I am far from an expert on matters like this, but I would be more than happy to try and assist you if possible.  

Moving on, when you get the error about starting the X server, does it give you an option to view the X server log for error output?  If so, what errors are you getting?

> I finally got it to work by specifying VESA, but the graphics quality really sucks (for example scrolling in firefox is painfully slow)

Did you install it with the VESA settings or are you still running it off of the CD with the VESA settings?  How much ram does your machine have?

---

### Post by alxjl on 2007-01-25
What was your goal in trying out ubuntu's live cd? Was it to test the applications on it? Or were you expecting the works? (like 3D acceleration?, etc)

---

### Post by zetapotential on 2007-01-25
Thanks for you response :)

The specific error I get in the log is

(WW) ATI: PCI MACH64 in slot 1:0:0 could not be detected

and a similar one for slot 1:0:1.

I'm running everything off the live cd, my machine has 1 gig of RAM.   My goal is to see if all the hardware would work right away before I switch to ubuntu...

---

### Post by alxjl on 2007-01-25
Don't be discouraged if you encounter problems with the x-server. I suggest you try out other live cd's from different distros. Plenty to choose from like Sabayon, Knoppix, Mandriva One, etc. Go check out Distrowatch.com for all the linux distros out there. Good Luck with your Linux experience!

---

### Post by zetapotential on 2007-01-25
Huh... thx for the advice.  I've heard more and more about ubuntu so I really wanted to try it out :(

---

### Post by zetapotential on 2007-01-25
but is that really the only option?  one type of linux doesn't work, go try another one?

---

### Post by The Tronyx on 2007-01-25
Ubuntu is definately worth having a look at, if you are having problems with slowness on the live CD, I would say give installing it a shot, if you can afford to that is.  Once you install it, the swap configuration might help to speed up performance problems that you are having running the live CD.  Other than firefox what applications have you tried?  Have they been slow as well?

I can attest to the fact that I have rarely had any hardware configuration problems with my Ubuntu install(s) BUT as of now, or rather last time I had to muck with it, ATI support was relatively...terrible.  Not the necessarily impossible, but it did take a bit of effort to get it all configured correctly(Asus EAX-1600 pro).  Again your call.  Keep us posted either way.:)

EDIT:  Also give [http://ubuntuforums.org/showthread.php?t=265483](http://ubuntuforums.org/showthread.php?t=265483) a look to see my experiences and what I was referred to just so you have an idea of what to expect.

Also one other question, which architecture does your version of Ubuntu say it uses, 64 or i386?

---

### Post by alxjl on 2007-01-25
Let me tell you that Ubuntu may not be as great as all the other live cd's out there (and believe me if i tell you that i've tested a lot of them), but once you install it on a hard drive and have it properly configured, you'd never want anything again.

---

### Post by zetapotential on 2007-01-25
Other applications (like open office) run reasonably fast; it's actually the video refresh that's painfully slow.  For example, just dragging a window around is very very slow, same with scrolling down in firefox.  

I also just realized that I don't have any audio... apparently it doesn't recognize my sound card either :(   I guess no ubuntu for me :(

Thanks for your help :)

---

### Post by zetapotential on 2007-01-25
> **2point0 said:**
> 
EDIT:  Also give [http://ubuntuforums.org/showthread.php?t=265483](http://ubuntuforums.org/showthread.php?t=265483) a look to see my experiences and what I was referred to just so you have an idea of what to expect.

Also one other question, which architecture does your version of Ubuntu say it uses, 64 or i386?

Ummm, i386 I believe.  Where would I check?

---

### Post by alxjl on 2007-01-25
Not having been successful running an ubuntu live cd according to your expectations should not be the end of your Linux experience. Like i said, you can try out all the other live cd's out there. It's still Linux you'll be trying out. And the forums here aren't closed to just ubuntu users. Even if you decide to install other linux flavours, you can still seek help from the guys here. Coz this community is one of the most friendly, if not the best there is.

---

### Post by The Tronyx on 2007-01-25
Well if you have a 64 bit system I don't think the live CD would even make it very far before telling you that it isn't compatible and quitting.  Assuming you are on an intel machine or you burned the CD from an .iso file, it should say something like "Ubuntu_6.10_Edgy_i386.iso.  

I'm no master on configuring hardware as I mentioned before, though as another posted (I forget off-hand) mentioned that it really was a very comfortable and stable distro.  Perhaps before making a final decision you should search the forums a bit about troubleshooting sound cards, drivers, and something like "Sound card model XXX-17" problems, or AGP video card problems.  Linux is all about tinkering and configuring, rarely will you find a distro that does it all for you, it's also a great way to learn.:wink:

Who knows, you might find that after you install you can get your video/sound card drivers right from synaptic package manager.

---

### Post by scrooge_74 on 2007-01-25
I had a bad encounter with a SONY the other day which was painfully slow doing things with the Live CD installation was impossible.  But I try running the Live CD in recovery mode and after that everything was ok and could install in no time

---

