---
title: "Massive Update? Computer dosent start!"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-05-31
Well I was installing Beryl, and then I did some huge update.  It took about.. an hour and a half.  and now my computer starts up in the terminal and when I put my username and password in, it says something like, 7.04 Fiesty something, BUT I dont HAVE FIESTY.  I have KUBUNTU.  Everything with linux I have had is BAD.  Anyway to fix this before I go back to windows.

---

### Post by lazyart on 2007-05-31
There is ubuntu feisty, kubuntu fiesty, xubuntu feisty, etc.

Are you getting a message about X server not starting?

---

### Post by LollYouSuckZor on 2007-05-31
No.  I dont know whats happening, I Just know that when I updated, it dosent work anymore.  Isint there something I can type to start the beryl? or.. KDE desktop?

---

### Post by lazyart on 2007-05-31
I wonder if you get the kernel update and it hosed the video driver.

Try this:

Boot up your machine.  When you see the Grub loader hit ESC.  See if you have multiple kernels.  You might have one with .16 on the top and .15 in the middle.  Choose .15 -- but not the recovery variant.

See if that brings you to your desktop.

---

### Post by LollYouSuckZor on 2007-05-31
Hahaha, Thanks :)

---

### Post by lazyart on 2007-05-31
That's half the battle-- everytime you start up you'll get this.

Edit your grub menu and comment out the blocks of lines that reference .16 by preceding them with a #.

---

### Post by LollYouSuckZor on 2007-05-31
Nope.  That didnt work either.


**** Linux.

---

### Post by LollYouSuckZor on 2007-05-31
Nothing works.  It boots up and says something, no image, blah, no supprise,  LINUX.  I swear.  If I had a windows CD, i would have gone back two weeks after installing this linux crap

---

### Post by Outrunner on 2007-05-31
> **LollYouSuckZor said:**
> Nothing works.  It boots up and says something, no image, blah, no supprise,  LINUX.  I swear.  If I had a windows CD, i would have gone back two weeks after installing this linux crap

Well, what can I say? Good luck with Windows. Use what works for you.

---

### Post by sessine on 2007-05-31
> **LollYouSuckZor said:**
> Well I was installing Beryl, and then I did some huge update.
What did you update and how did you initiate the update?  Was it with one of the built-in tools like synaptic/adept? or was it something else?
> **LollYouSuckZor said:**
> 
It took about.. an hour and a half.  and now my computer starts up in the terminal and when I put my username and password in, it says something like, 7.04 Fiesty something, BUT I dont HAVE FIESTY.  I have KUBUNTU.  

Which version of Kubuntu did you originally install? I have read that a dist-upgrade (e.g. from Edgy to Feisty) can break things if you have some non-standard config.

If you can log in at the command line try removing/moving the config files from your home area, not sure which ones they are in Kubuntu but things like .gconf or .kde in your home area might be a good start.

---

### Post by lazyart on 2007-05-31
> **LollYouSuckZor said:**
> Nothing works.  It boots up and says something, no image, blah, no supprise,  LINUX.  I swear.  If I had a windows CD, i would have gone back two weeks after installing this linux crap

If you want help perhaps explaining the error better than "something, no image, blah" can assist us in assisting you.  If you're done with Linux, well that's fine too. Thanks for trying.

---

### Post by Outrunner on 2007-05-31
> **lazyart said:**
> If you want help perhaps explaining the error better than "something, no image, blah" can assist us in assisting you.  If you're done with Linux, well that's fine too. Thanks for trying.

Well, I'm fairly certain the 'error' he's referring to is the new -16 kernel that causes problems. Since you've addressed that problem earlier, he should have gotten it fixed but... ohh well!

---

