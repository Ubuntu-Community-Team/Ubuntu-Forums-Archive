---
title: "newbie wanting to install Guickbooks"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by unicorn91899 on 2006-10-12
HI, I am a newbie who just loaded ubuntu on a machine and want to use it for work but I need to use QuickBooks Pro 2006. Has anybody had success and if so can you help explain in easy to understand directions? THis is my first experience with anything Linux so I am not real good at this yet.

---

### Post by Paul41 on 2006-10-12
GNUCash is is similar to QuickBooks and is available in the repository.  If that is not an option for you, you might be able to run QuickBooks in WINE.

---

### Post by kevinlyfellow on 2006-10-12
well, I've never used that program or tried this, but one thing you can try is wine.  Open up synaptic (System -> administration -> Synaptic Package Manager) and search for wine.  When you find it, install it.  

Run the setup program for quickbooks with wine (right click and open with other application, if its not listed, just put in the command wine).  

There are programs like codeweaver that will make it easy to use wine and have a very good configuration so that you won't need to mess with it.  [http://www.codeweavers.com/](http://www.codeweavers.com/).  I hope it helps you get started

---

### Post by unicorn91899 on 2006-10-12
Wine did not work so I am trying crossover by code weavers. I will report how that works. Thanks.

---

### Post by Matchless on 2007-01-16
Gnucash is related to Quicken and is not a proper business accounting program, regardless of what some people seem to think. It is actually a personal finance program and very old and outdated in looks and most of the support is going into bug fixes and none into getting it into the fast lane. Unfortunately Gnucash is about the best you will get for linux at the moment, and is very much lacking in features.

Quickbooks up to version 2004 can be installed in Ubuntu Edgy and earlier using Wine or Crossover Office 6.0.0. There is a demo version available for download. I have personally tested 2004 and version 6.0.
 
Hope this info is useful to those seeking Quickbooks.

---

### Post by Marsolin on 2007-01-16
Neither are in the repositories, but two QuickBooks competitors that run on Linux are [TurboCASH]("http://linuxappfinder.com/package/turbocash") and [MyBooks Professional]("http://linuxappfinder.com/package/mybooks").

TurboCASH is free and open source.  MyBooks Professional is not.

---

### Post by Matchless on 2007-01-17
Thanks, I was not aware of a Turbocash  linux version. I have had a look at the windows version a while back and it was not really on par with Quickbooks, but on the other hand it seemed to be fairly useful.

Edit: On the Turbocash website there is lot about their intention of writing a linux version, but the download states that the windows version can run in Wine. So yes if it fits your requirements its free and so is Wine. A combination I have yet again to look at more closely. If it has customisable invoices it may be of interest to me.

---

### Post by tvor on 2007-01-19
I seems to having trouble finding GNUCash in repository of 6.10.....Are the part of the list or do I have to  modify my sources?

---

### Post by Matchless on 2007-01-20
It is in the universe, just make sure you have enabled it in the sources.list.The easiest is to enable in Synaptic, reload and find it under search. It seems as if gnucash 2.0.1-3ubuntu3 is available for edgy.

---

### Post by Sef on 2007-01-20
How to enable [universe and multiverse repositories]("https://help.ubuntu.com/community/Repositories").

---

### Post by goanna300 on 2007-10-20
Running Quickbooks -or anything approaching it- on Linux is a Holy Grail quest for many.
After several failures, I have retained my dual-boot machine. Here's why:
1) Quickbooks' proprietary data files are binary;
2) Every country's version of Quickbooks varies slightly;
3) Accountants use Quickbooks. Any solution must generate /export the accountant can use.

That said, Quickbooks is an ordinary database. It  is *not rocket-science*! The fact that a comparable, open-source alternative does not exist is astonishing. The missing link: import and export to Quickbooks, is a task which may entail copyright negotiations.

Telling users that Quickbooks works on Wine is irresponsible. Some U.S. pre-2004 versions are on Wine's bronze list.  That's all.

---

### Post by unicorn91899 on 2007-10-22
goanna300, thank you for your reply. I had given up hope for this working but will continue to search and ask around til somebody finds a way (including asking Intuit to add support).

---

### Post by argraff on 2007-11-30
Yeah, out of curiosity I tried QB07 Prof tonight through Codeweaver's Crossover. No such luck - needs the .net stuff (whatever that is) and that's why CC hasn't been able to get farther.

Grrrrrrr. It's the only thing holding the non-profit I volunteer for back from Ubuntu (currently on ANCIENT Pentium III running awfully unstable XP - and spending most of their days rebooting computers, servers, modems and the like!).

The suggestion (from my expert husband who rocks!) - have a Windows box somewhere in the building, plunk [VNC]("http://www.realvnc.com/products/free/4.1/download.html") on it and just access that when needed. We tested it before for other reasons and it seemed pretty good. I'll be looking into that. Will post back here if anyone's interested! :) It's not ideal, but it's all about getting it done at this point!

PS There's $$$ to be had in a native solution - I kid you not! It would start an Ubuntu WAVE!

---

### Post by chipwich on 2007-11-30
Recent versions of QB have some frustrating dependencies, even if you are attempting to get it installed in Windows.  .Net Framework 2.0, Flash 8, and IE to name a few.  The install routine will halt if any of these are not to its liking, and good luck getting help from their technical support, which has been rather hit or miss IMHO.

I wonder if it would run in a virtual machine, say a VMWare install of Vista.

---

### Post by argraff on 2007-12-02
> **chipwich said:**
> ... good luck getting help from their technical support, which has been rather hit or miss IMHO.

I wonder if it would run in a virtual machine, say a VMWare install of Vista.

Yeah, no kidding. Their tech support stinks! The last time I called, she kept insisting that it was a Windows problem and that I needed to call M$. She was wrong. :)

VMWare's not a bad idea - although I don't think I'd use the everything-hog of Vista...probably the earliest version possible (just for size!).

---

### Post by Brian96 on 2008-01-20
> **chipwich said:**
> Recent versions of QB have some frustrating dependencies, even if you are attempting to get it installed in Windows.  .Net Framework 2.0, Flash 8, and IE to name a few.  The install routine will halt if any of these are not to its liking, and good luck getting help from their technical support, which has been rather hit or miss IMHO.

I wonder if it would run in a virtual machine, say a VMWare install of Vista.

Yes, it will run in a VMWare install. Remember, running an OS in VMWare is going native as far as the application is concerned. You will have to install any dependencies (like .NET), just as you would from a native install.

So far it seems that everyone who has not found a suitable replacement for QB in Linux is running it in a VM. Every once in a while I toy with moving to something else, but setting up my accounts from scratch is intimidating. I am basically a standard home user, except that we do some independent contracting and need to be able to create invoices. That slight complication has kept me running QB 2003 in a VM. That and ESPN360 is pretty much all I use my Windows VM for anymore.

---

### Post by unicorn91899 on 2008-01-21
Thank you for the help on this problem. I will give this a try some day soon.

---

