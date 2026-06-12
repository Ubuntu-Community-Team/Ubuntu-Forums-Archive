---
title: "quickbooks pro"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Mumbutu on 2007-10-08
Is it possible to use the Windows version of Quickbooks Pro in Ubuntu?
If the answer is yes what will be the procedure to enable and run this software?
Thanks in advance for your input

---

### Post by llamakc on 2007-10-08
Unlikely. It would have to be run through WINE, and I don't know if QB Pro will run at all. I've heard of folks having luck with the smaller versions of QB though.

Another option is to run it inside of a VM from within Ubuntu (by installing VMWare & Windows or VirtualBox & Windows).

---

### Post by macogw on 2007-10-08
Perhaps with Crossover Office... I don't think any recent ones work with it though.  As llamakc said, VirtualBox would work.  You can make VirtualBox run such that your Windows apps are integrated with Ubuntu instead of all stuffed inside a Windows window.

---

### Post by HermanAB on 2007-10-08
Older versions of QB works on CxOffice/Wine.  I'm using QB Pro from 2000 and it works fine.  I don't know about newer versions.  However, you should consider switching to GnuCash, since it is very similar.

Cheers,

H.

---

### Post by Linux_Man on 2007-10-08
Try running it in Wine, but type in your version onto google and put wine after it to see if someone on the wine or other forums have a shell script that can help you

---

### Post by strabes on 2007-10-08
> **Linux_Man said:**
> Try running it in Wine, but type in your version onto google and put wine after it to see if someone on the wine or other forums have a shell script that can help you

I'm almost sure that quickbooks pro doesn't work with wine at the moment. Virtualization is probably the best option.

---

### Post by mrhirsh on 2007-10-09
It will NOT work inn Linux.  QB will only work as part of an enterprise system with a Linux server.  I am searching for a substitute.  GNU cash is not a good substitute for QB but might work for Quicken, which is a home bookkeeping program.

---

### Post by freshspinach on 2007-10-10
I'm running Quicken XG 2007 on VMWare. It works great.

---

### Post by osaurus on 2007-12-01
> **HermanAB said:**
> Older versions of QB works on CxOffice/Wine.  I'm using QB Pro from 2000 and it works fine.  I don't know about newer versions.  However, you should consider switching to GnuCash, since it is very similar.

Cheers,

H.
I've installed QB Pro 2000 using wine but it won't load, saying that it can't find IE5. I installed ies4linux which looks like IE6, but still can't load QB. Any suggestions are much appreciated.

Thanks, Dan

---

### Post by HermanAB on 2007-12-01
Install Office 2000 on Wine to get IE5.  I used to run it like that, but since a few months ago, I'm using Vmware with WinXP instead - less hassle.

Cheers,

Herman

---

### Post by GerryH on 2007-12-01
I am running QB 2007 in Win$Lin with great success. Nice to be able to see the Gutsy files and drives too. It makes file transfer simple. 
 I've been through the Wine, not impressive and not for QB, Qemu will do it but file transfer, and printing issues abound. 
Win4Lin works for me and is the best 46 bucks I've spent to end my frustration

---

### Post by osaurus on 2007-12-02
> **HermanAB said:**
> Install Office 2000 on Wine to get IE5.  I used to run it like that, but since a few months ago, I'm using Vmware with WinXP instead - less hassle.

Cheers,

Herman

My QB disc has IE5 but it would not install with QB or separately with wine. This seems like a lot of work compared to just using an old version of windows (2000 pro).

Dan

---

### Post by Gary Stout on 2008-01-12
I am also using QB 2003 pro with no issues. My setup is Ubuntu 7.10, Win4Lin 4.5.63958, win2kpro and quickbooks 2003 professional. It works just like any other windows installation.

HTH,
Gary

---

### Post by argraff on 2008-02-01
> **GerryH said:**
> I am running QB 2007 in Win$Lin with great success. Nice to be able to see the Gutsy files and drives too. It makes file transfer simple...Win4Lin works for me and is the best 46 bucks I've spent to end my frustration

Anyone else have this experience? What's your hardware setup? I have a non-profit desperate to go away from Windows, but QB 2007 is holding us back!

---

### Post by cwmoser on 2008-02-01
I have Ubuntu Gutsy and before that Feisty Fawn.  For over a year I have been running Quick Books 2004 and Quicken 2005 using the CrossOver product.  

[http://www.codeweavers.com/](http://www.codeweavers.com/)

Its well worth the cost.  Both products work great with CrossOver.

If I could not have gotten these two products to work, it would have been a show stopper for me and Ubuntu.  Don't care about Microsoft Office - personally, I like Open Office better.

I also use Wine to run E-Sword and Spider Solitaire.


Carl

---

