---
title: "What We're Actually Doing: Ndiswrapper"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by tgbrowning on 2007-06-10
Folks, 

I've been trying to get a WiFi card to work, followed various threads here and there and confess myself mystified.

I've poked around and discovered a couple of things, such as it *appears* that ndiswrapper is a Perl script of some kind (not that I know anything about Perl scripts) and some of the "error" messages might be a little bit more helpful. 

What exactly is going on when one does the following:  

Use the sudo command (that I know, allows me adminstrative rights) on ndiswrapper, which is followed by one of several possible options, such as -i (install) -l (list what's been *wrapped* I guess), -e (for remove, I think) and the always helpful -h for help.

I apparently am doing some things right because there are no explosions, large scale or otherwise, when I try to install something via ndiswrapper, but it's clearly not working. The why of it puzzles me greatly.  The message I get when I try to have ndiswrapper list out what's gone before is a surly and short little phrase saying *xxxx* is either not a valid something or other or not a proper driver or some such.  

Why?  I'm using 6.06, btw. 

A great point was made that the .inf files to be used could come from the LinkSys windows install CD, which is where I got them. There were three in the Drivers folder:  rt73.inf, WUSB54GSC.cat and WUSB54GSC.inf.  

The LinkSys wireless card is, in actual fact, a USB WUSB54G device.

[One nice thing, I've been able to remove all of the ones that I've installed that don't qualify as valid whatever. Some progress is being made, anyway.

---

### Post by tdrusk on 2007-06-10
enter
```
lspci
```
and post that so we know what card you have.

---

