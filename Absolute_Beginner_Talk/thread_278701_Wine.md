---
title: "Wine"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by Linux Penguin on 2006-10-16
I have installed Wine, or so i thought, using the synaptic package manager but i cant find it installed anywhere on my desktop or in any of my applications
P.S I also tried to install it manually using the ATP channel but that didnt work so any suggestions on how to find it?

---

### Post by PriceChild on 2006-10-16
Nope it isn't a gui really.

use
```
winecfg
``` to bring up a gui to configure your wine install then...
```
wine /path/to/something.exe
```or
```
wine "C:/path/to/exe"
```(after setting up a location for your c drive)

btw i've always found the gui's for wine really lacking and buggy.

---

### Post by Linux Penguin on 2006-10-16
Sorry im kinda new at this is there an easier way to do this or another way to expalin it?

---

### Post by PriceChild on 2006-10-16
You've still got to use winecfg to configure it... pretty self explanatory.

From the official howto:
[http://www.winehq.com/site/docs/wine-faq/index#HOW-DO-I-RUN-AN-MS-WINDOWS-PROGRAM](http://www.winehq.com/site/docs/wine-faq/index#HOW-DO-I-RUN-AN-MS-WINDOWS-PROGRAM)

---

### Post by bodhi.zazen on 2006-10-16
[How to Wine](http://doc.gwos.org/index.php/HowToWine)

wine is not easy and I have never considered it for noobs. =;

consider :[CrossoverOffice](http://www.codeweavers.com/products/cxoffice/)

Or: [Xandros](http://www.xandros.com/products/home/home_edition/features.html)

You can "do it yourself" with wine, but expect to do some home work... 8-)

---

### Post by Ambimom on 2006-10-16
Wine only works on some Windows exe programs.  There's a list here: [http://frankscorner.org/](http://frankscorner.org/)

You can right click on a windows program exe you want to open in Linux and it will ask if you to open in windows emulation.  Say yes.

But in my experience the programs never work the way they should.  If you can't find the program equivalent in Linux, then dual boot back to Windows.  In the long run, it's easier.

For instance MIRC allegedly works with Wine; and it does, sort of, but I've since discovered XChat[which is free]actually is far superior to MIRC [for which I paid $20).  

For bittorrent and usenet, I'm still booting to Windows; though I occasionally use Linux's Opera browser for bittorrent.

---

### Post by emarkay on 2006-10-16
So Wine causes whining.

Let's say I have an esoteric program that may never see the light of day in Linux.

[www.efilive.com](www.efilive.com) - scan and tune tool.

How would you gurus go about gettig it to run in Ubuntu?

THANK YOU!!!!!

---

### Post by bodhi.zazen on 2006-10-16
> **emarkay said:**
> So Wine causes whining.

Let's say I have an esoteric program that may never see the light of day in Linux.

[www.efilive.com](www.efilive.com) - scan and tune tool.

How would you gurus go about gettig it to run in Ubuntu?

THANK YOU!!!!!

Do you have an install CD?

First do some warm-ups: ](*,)  ](*,) , Repeat. ](*,)  ](*,) 

[list=number][*]Install wine.[*]Attempt to install your software from CD.[*]If that fails, configure wine with sidenet and Install IE5.5 and re-try.[*]Retry with Sidenet and IE 6.[*]Remove and re-install wine.[*]Configure wine with winetools & Re-try.[*]If that fails again remove and re-install wine.[*]Configure wine with wine-doors and re-try.[/list]

](*,) 

IE= Internet Explorer. You usually need IE to install most software.

See my previous post "how to wine" for more detailed description on how to do all this.

---

### Post by emarkay on 2006-10-17
MSIE in Linux - Ewww, that's like putting sand in the KY Jelly!

(EFILive is a stand alone installation and needs no help from Bill Gate$)

Will be looking into getting this going, but I am learnin gmuch about Linux, and for now, I want to avoid the ubiquitous ](*,)   :)

I'll post back here if I get it!

---

### Post by Linux Penguin on 2006-10-17
is there any other equivelant for wine thats easy to install

---

### Post by Billquinn1 on 2006-10-17
bodhi.zazen 

Is the Wine-doors project ready? I Thought it was still just a framework.


Bill

---

### Post by bodhi.zazen on 2006-10-17
> **Billquinn1 said:**
> bodhi.zazen 

Is the Wine-doors project ready? I Thought it was still just a framework.


Bill

LOL :lol: It is on my to do list. I downloaded it, but am running wine on a "production box" and can not afford to experiment on it. Can not be any worse then what we already have.

Have not had the time to wine on my test box, too many projects, not enough time.

[[color=darkred]How to wine-tools[/color]](http://doc.gwos.org/index.php/HowToWine#Method_3_-_Wine-Doors)

---

### Post by bodhi.zazen on 2006-10-17
> **Linux Penguin said:**
> is there any other equivelant for wine thats easy to install

[Look here for alternates](http://doc.gwos.org/index.php/HowToWine#Alternates_to_WINE)

---

### Post by hollaburoo on 2006-10-17
wine really isn't that hard to use, you just have to use the command line a bit.  since you already have wine installed, open a terminal and type winecfg, click on the drives tab and click autodetect, that should get wine pretty much set up.  Next look for you windows app at the [appdb]("http://appdb.winehq.org/") for your app, and if it's there try to follow the instructions in the comments on the page.
To install, just install it the same you would on windows, by doubleclicking on the .exe file.  Keep in mind that not every app will work though.

---

### Post by bodhi.zazen on 2006-10-17
> **hollaburoo said:**
> wine really isn't that hard to use.....

No, I agree wine is easy. The hard part is getting your application to work. Configuration and installation can be complex or fail outright.

---

