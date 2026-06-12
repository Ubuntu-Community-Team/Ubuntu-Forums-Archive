---
title: "A Wine About Wine"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by rube1947 on 2007-07-06
I installed Feisty Fawn in order to save a underpowered PC which was running very slow on XP homer.  I find Feisty to be a great way of doing the common tasks but I have had fits installing the two or three Window's programs I need.  Wine does not install either Quicken or a couple of other windows only programs.  IE4 loaded which I need for one application but nothing else.  Also no version of iTunes seems to load.  Rythmbox is not the solution and video podcasts are a no show.  I am running out of patience with Wine and have tried Parrallels and that has turned into a non functioning nightmare.  Windows 2000 on Parallels is very bad and XP doesn't want to load.  

I think that the solution is to ditch Feisty buy that Apple iMac when it comes out in the fall and run parralllels and XP on the Apple.  

Sorry for the Wine, but that is my experience.

---

### Post by moredhel on 2007-07-06
IE4? ie5/5.5/6/7 all work in wine if you didn't know.

itunes 6 works in wine: [http://frankscorner.org/index.php?p=itunes6](http://frankscorner.org/index.php?p=itunes6)

Quicken doesn't run in wine. live with it.

If parallels if giving you issues, then try vmware server or virtualbox or qemu.

Remember wine is a very hit and miss. I run jedi knight 2, steam & notepad++ all perfect in wine. Researching before hand is a good idea. 

go on here to search [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by lbelloq on 2007-07-06
rube1947:

1. Seems Quicken is not supported under Wine.
2. For IE, search for [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page").
3. iTunes is not supported either, AFAIK. I think gpodder is your choice.

---

### Post by 3rdalbum on 2007-07-06
Parallels is primarily a Mac program, so it's no wonder it doesn't work properly on Windows or Linux.

I use Virtualbox on Linux - it's very good, and free. Pretty easy to install - it's a Debian package and then one command in the terminal, and there are wizards to help you set up virtual machines and disk images and stuff.

I don't think you're comparing apples to apples. Wine is a reverse-engineered compatibility layer for Windows programs, which tries to map Windows system calls to Linux equivalents. Parallels and Virtualbox are virtualisation - they run an operating system within a "virtual machine", making use of your real processor but running within a window on your real operating system.

So you wouldn't achieve anything by moving to the Mac, as Wine is not as functional on the Mac, and you'd still need to virtualise or dual-boot Windows anyway!

---

### Post by rube1947 on 2007-07-06
Thanks for the thoughts.  I have tried a number of the banking programs for LINUX and all are very cludgy.  Do any of you have experience either with a good on line personal finance program or something that works well with LINUX.  

I will try the various suggestions on VM ware as I think that will be my best current solution.  I owned a copy of parallels which is why I used it first.

Thanks for the links to WINE.  I will do a little research before I try anything else.

---

### Post by cogadh on 2007-07-06
> **rube1947 said:**
> I installed Feisty Fawn in order to save a underpowered PC which was running very slow on XP homer.  I find Feisty to be a great way of doing the common tasks but I have had fits installing the two or three Window's programs I need.  Wine does not install either Quicken or a couple of other windows only programs.  IE4 loaded which I need for one application but nothing else.  Also no version of iTunes seems to load.  Rythmbox is not the solution and video podcasts are a no show.  I am running out of patience with Wine and have tried Parrallels and that has turned into a non functioning nightmare.  Windows 2000 on Parallels is very bad and XP doesn't want to load.  

I think that the solution is to ditch Feisty buy that Apple iMac when it comes out in the fall and run parralllels and XP on the Apple.  

Sorry for the Wine, but that is my experience.
Wine is beta software. It is still under heavy development. If you were looking for perfection, you probably won't find it, but maybe you should wait until version 1.0 comes out... eventually.

---

### Post by jleckie on 2007-07-06
For a great online personal finance program, try ClearCheckbook:

[https://www.clearcheckbook.com/index.php/](https://www.clearcheckbook.com/index.php/)

I've maintained all of my bank and credit card accounts with this application for almost a year, and never had a problem.

---

