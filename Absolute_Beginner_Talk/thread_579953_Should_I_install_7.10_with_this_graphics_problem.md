---
title: "Should I install 7.10 with this graphics problem?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by MattR37 on 2007-10-18
I have the Live CD of Gutsy and can only boot using it if I select the safe graphics mode.  Otherwise I get a bunch of garbled displays on my screens.

I have an eVGA 7900 GT, and my question is will those Nvidia restricted drivers work once I install Gutsy to my HD?  I also have a dual display: Dell 2407WFP and a Samsung SyncMaster 172N.  I'm hoping that all this will work. 

Matt

---

### Post by pchr on 2007-10-18
Same here with live CD.  Though my monitor turns itself off!  Works OK if I run live CD in safe mode.  Trouble is if I get to the same place in actual install I wouldn't have a clue what to do.  You getting anywhere?

---

### Post by MattR37 on 2007-10-18
No I still haven't gotten anywhere.  I really don't want to do the install to my HD if I'm going to have to troubleshoot a bunch of stuff to get it working.

Looks like Windows will be keeping me for a while longer.

Matt

---

### Post by vitku on 2007-10-18
Hi

The problem seems to be that ubuntu is unable to show splash on newer Nvidia cards.

The bug [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/147623](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/147623) 
has couple of workarounds for different scenarios like this on newer nvidia cards. Vasilii posted a clue on the bug for how to boot the live cd. I think it should work on final release as well as RC.

---

### Post by pchr on 2007-10-18
Think my problem must be something else.  I've got intel on-board graphics.  Plain and simple.  gets as far as loading X.  I see my mouse pointer on a slightly dull plain orange desktop - with no icons or panels.  Then Monitor switches off.  I'll have a look at the link you've provided though and see if that tells me how to sort out the problem once I get gutsy installed.  Holding off till I've got a solution.  Though who knows, If I do the install in from the live CD in safe graphics mode perhaps it wont be a problem once it's properly installed?  Might do it anyway, though I wouyld then be reduced to researching the problem in Windows which I try to avoid booting if I can help it.  Makes me feel dirty.

---

### Post by Hobo Joe on 2007-10-18
What is your graphics card?

I'd say go ahead and install, you should be able to boot up into the GUI without problems. If you do have problems though, we can walk you through how to install drivers via the command line.

---

### Post by MattR37 on 2007-10-18
I have an eVGA 7900 GT.  Ok, I'll give it a try.  Thanks for offering to help Hobo Joe! :)

Matt

---

