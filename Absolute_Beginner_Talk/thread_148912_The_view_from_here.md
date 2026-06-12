---
title: "The view from here"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by DavidFourer on 2006-03-22
Ubuntu Breezy 5.10 installed on new Dell notebook (inspiron 6000). Tried the Live CD first and thought things looked good.  Internet is up with the cable.  Screen good. Keyboard good.  Mouse OK.  Camera downloads good.  Browser and mail good.  file/bookmark/mail/address imports done.  Software generally good.  Sleep mode - bad.  wireless - bad.  

Problem is I do really need to fix a few things and I'm making little progress.  

I worked really hard on the wireless with the wikis but I'm stuck.  The mouse needs some help.  Those two things.  This is really dense stuff.  I'm going to go to a local Chicago computer geek club meeting tomorrow night and meet some real people.

Here's questions to throw out.  I'm getting irritated by the touchpad problems.  I found  the SynapticsTouchpadHowto and this looks solveable.  How do I find out if a touchpad driver is installed and activated?  How do I identify my touchpad hardware?  System>Administration>Device Manager reveals nothing.   What is the Breezy 5.10 file equivilent of [Warty]/etc/X11/XF86config-4  ? 

And I have to get the wireless up sometime.  I expect it will work but I don't know if I can do it.  (I got the universe/multiverse, ndiswrapper, Windows driver downloaded/unzipped/installed and I thought I was doing pretty good)

At some point I'll sit down with a book on unix terminal commands, but I really just want to use my computer and I'd like to get these two problems fixed.

---

### Post by celloandy on 2006-03-22
The X config is now located at /etc/X11/xorg.conf.  As for shell commands, you really don't need a whole book to learn the basics.  Google "linux shell tutorial" or something like that, and I'm sure you'll find a couple of pages of summary that'll give you all the commands you need.  If you have more specific questions about making ndiswrapper, or anything else, work, feel free to ask.

Andrew

---

### Post by jimrz on 2006-03-22
Welcome,

   The Dell site (or maybe even the documentation that came with your LT) can tell you which touchpad you have. Once you find out, search these forums for intructions on how to set up for full functionality. You may even find it and other useful info faster by searching for "Insperion 6000". On my ThinkPad it took a little work to get full function from the touchpad, but it was neither difficult nor too time consuming. 

   You can use the same proceedure to find help getting your wireless working. Afraid I can't be of much help with that since mine was recognized "out of the box" and has worked well since intall. I do know that my son had to use ndiswrapper to get his Dell m600 wireless working, but was able to acheive this in pretty short order.

---

