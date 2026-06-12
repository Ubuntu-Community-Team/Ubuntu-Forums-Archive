---
title: "Simple Wine Download needed please!"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-04-14
[LEFT]1. I know Wine is a program that allows you to play some if not all Windows programs,  right?[/LEFT]

2. How do I download wine? What is the command? According to a forgotten site I once researched in they mentioned something about downloading the "correct" download, whatever that means. And, if it serves any purpose to downloading the "correct" wine download, I use Ubuntu Dapper.

PS. I forgot to mention, if this is of any importance at all, that I need wine to play DOS games.

---

### Post by qpieus on 2007-04-14
1. Yes, wine allows you to run some windows programs. Some work, some don't. You just have to try 'em out.

2.  Add this line to your /etc/apt/sources.list file:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

then in a terminal type:

sudo apt-get update

then

sudo apt-get install wine

This will install the latest (I think) version of wine.

There's a decent how-to here:
[http://ubuntuforums.org/showthread.php?t=149585]("http://ubuntuforums.org/showthread.php?t=149585")
for further information on using wine.

---

### Post by fice on 2007-04-14
the easiest way to download wine in ubuntu is just to open synaptic package manager and search for wine, once it shows up just right click on the main program(it should only say wine) and click on install from the menu. This will download the wine compilation thats already fitted to your ubuntu box. 

Usually wine is in the universe repository in synaptic, so if you have not activated the universe repo you should activate it and then click on update so that you can update the repositories and then search for it. 

To activate the universe repo you should go to the settings menu in synaptic and then click on repositories there you will see in the first tab a bunch of check boxes, the first one should say "community maintained open source software (universe)" check that box. Now after updating you should be able to search for wine. 

Wine, as the acronym stands for is not an emulator (Wine Is Not an Emulator), what it does is simply have the usual libraries windows uses to run programs(the .dll files) for them to work properly. Not all programs work through wine or rather not all programs are easy to run through wine. Once installed you can try running it but if it doesnt work theres a big chance your wine configuration is not compatible with the program your trying to run, sometimes you can find "how to's" to run a specific program in wine so you can try searching the web for those how to's as well. If your interested in running games on linux you should try Cedega ([www.transgaming.com/](www.transgaming.com/)) which will make it easy for you to run many of the windows games easily, including the most popular ones but this software is not open source so you have to buy it, it is however not expensive at all so you might want to consider it as well only if wine doesnt cover your gaming needs.

I hope this helps.

---

### Post by machoo02 on 2007-04-14
Remember,  Windows != DOS.  If you are only looking to play DOS games, then I think you don't actually want WINE, but either [DOSEmu]("http://dosemu.sourceforge.net/") or [DOSBox]("http://dosbox.sourceforge.net/news.php?show_news=1").  Both are in the repositories.

---

### Post by YokoZar on 2007-04-15
> **fice said:**
> the easiest way to download wine in ubuntu is just to open synaptic package manager and search for wine, once it shows up just right click on the main program(it should only say wine) and click on install from the menu. This will download the wine compilation thats already fitted to your ubuntu box. The version of Wine this will give you is about a year old, ie the one that came out with dapper.

Go here first: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

There are two commands to cut/paste into a terminal, then you're done.  Make sure you use the Ubuntu Dapper (6.06) ones.

> Wine, as the acronym stands for is not an emulator (Wine Is Not an Emulator), what it does is simply have the usual libraries windows uses to run programs(the .dll files) for them to work properly. Not all programs work through wine or rather not all programs are easy to run through wine. Once installed you can try running it but if it doesnt work theres a big chance your wine configuration is not compatible with the program your trying to run, sometimes you can find "how to's" to run a specific program in wine so you can try searching the web for those how to's as well. If your interested in running games on linux you should try Cedega ([www.transgaming.com/](www.transgaming.com/)) which will make it easy for you to run many of the windows games easily, including the most popular ones but this software is not open source so you have to buy it, it is however not expensive at all so you might want to consider it as well only if wine doesnt cover your gaming needs.Wine runs a lot of games better than Cedega now.  There's an ongoing discussion in the gaming forum.

---

