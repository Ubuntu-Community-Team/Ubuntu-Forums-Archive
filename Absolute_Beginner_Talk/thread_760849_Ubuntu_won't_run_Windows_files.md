---
title: "Ubuntu won't run Windows files"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Stephen Budensiek on 2008-04-20
Hello,  I've just installed Ubuntu Ver 7.10 on an older HP machine with a Pentium 3 processor at 550 mhz, 256m RAM, and 17.5GB HD.  Everything loaded normal, the screens came up normal.
   Problem started when I tried running some Windows CD's (designed for Win 98 thru XP).   The autorun.inf program didn't start.   So I tried double clicking on it, but no go.   Tried some other Win prgrams with EXE start files.   Everything I tried only popped up a window with the program name at the top, then it gives the program name and path, then below that it says What should Firefox do with this file, and 3 options are available that won't start the usually exe file.   I see an OS that won't start exe files as useless, what am I missing?
   During startup, I get a line that says it cannot read the BIOS year, so it can't load ACPI drivers.   Is this machine un-useable, is something in Ubuntu screwed up, or what?
   Thank you.

---

### Post by PurposeOfReason on 2008-04-20
Linux is not windows and it can't run .exe files.

---

### Post by Saint Angeles on 2008-04-20
exe is windows executable... just like windows can't run mac or linux files... 

with an exception... linux CAN run some programs through wine.

---

### Post by TeoBigusGeekus on 2008-04-20
Linux can never read window$ executables by itself - they are specifically written for that operating system.
What you can do, is install wine (sudo apt-get install wine) and check its site to see which window$ software cooperates well with it and which doesn't.
[http://appdb.winehq.org/]("http://appdb.winehq.org/")
With wine, you can run some window$ programs in Linux without major problems.

---

### Post by pseudo-random on 2008-04-20
Ubuntu won't run Windows files...because it isn't windows.
Learn about WINE.

---

### Post by gpilkay on 2008-04-20
Congratulations on joining the old computer club!  I run an old Windows ME machine that's now running 7.10.  Bought the entire machine or ten bucks as it was being hauled to the dumpster, and outfitted it with recycled parts.  It's now my Grandma's sudoku and old-radio-show player.

To clarify the previous poster's point, they are correct, Ubuntu, and Linux in general, is NOT Windows of any sort.  EXE files don't work, there's no way they could.  The file installation methods are totally different, and there's almost no relation between them. If you want a double-click program install, you'd need .deb files, made for debain-based machines.  getdeb is the most common website I know of for these, though add/remove gives you most of what you may need.

What sort of program are you trying to run?  While the exe files won't run natively, you could try WINE, which, I admit, is rather hit-or miss and with such low hardware specs is probably not your best bet.  You could also do what I do, and set up a duel-boot.  I have two hard drives on my slightly newer Celeron D, one for XP and one for Ubuntu.

There is also VirtualBox, but again, the low memory works against you, as you basically have to support two different OS's at the same time.

On such a low-powered system, though, I tend to run linux-only, as it works far better for me to have the latest and best linux on hand then an older unsupported Windows OS that's attracting every malware like a fly to a bad steak.

So, what kind of applications or files do you need?  We may be able to point out a Linux program that can do it.

---

### Post by skymera on 2008-04-20
> **pseudo-random said:**
> Ubuntu won't run Windows files...because it isn't windows.
Learn about WINE.

There's you answer. Pure and simple.

---

### Post by SunnyRabbiera on 2008-04-20
if you need help installing software in linux this is a good place to start!
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by phillipchandler on 2008-04-21
Wow. The replies to his post are rather polite. Normally under other distros, and maybe this one. if anyone asked a question like that then someone would have questioned the legitimacy of his parentage, for not at least finding out basic info, about the differences between Windows, Linux and Mac. You people are getting too polite in your old age(s), rather like me. hahahaha

---

### Post by FredB on 2008-04-21
Indeed. But it smells to me like a troll... It stinks to be clear ;)

---

### Post by Cannaregio on 2008-04-21
Agree with the probability this is just a troll.
Classical trolling phrases are indeed there:

> I see an OS that won't start exe files as useless, what am I missing?
> is something in Ubuntu screwed up, or what?

And if he is just a moron, I also agree that correctness towards idiots might be a tag excessive on this forum.

---

### Post by phillipchandler on 2008-04-21
When I started using Linux it was a BIG massive learning curve. Coming across from windows way of doing things made it hard work to relearn. But now its been worth the work.
Problem for me was learning the termanology. If your not sure of what the problem is, then you dont know how to correctly ask the question.
Its like if you enter a search term in Google, you can change the words around and get different results. 5% max will be the same, but diff word entry gets slightly diff search results. Plus a lot of seasoned linux users who know the termanology tend to forget they had to learn once, so tend to talk techno talk to newbies who then get extra confused, and some newbies need an extra helping hand than other. Theres an old belief that if your using linux then you must be VERY technical and know what your doing. Good point but slightly misguided, some people learn quicker than others as their that way inclined.

Dont get me wrong, Im no thicko, but Im not the smartest bulb in the pack either. I can generally get the drift, or get clues from answers to then know what to google on, and then hopefully work it out. But I also think that with some basic things it is easy to search google and get the low down basics, especially on the diff between linux and windows. All Id do is go to wikipedia, that has some great pages on linux and how diff it is, then theres distrowatch.

So I guess what Im saying is that maybe we shouldnt be so hard if we get a newbie who has genuinly tried looking if they say their getting confused with what terms to google on, but politely rip the hell outta the people who just havnt tried. This is especially as say with a belkin wireless card, Ive looked at this in ubuntu and its supported with the net8185 driver under ndiswrapper, and is setup in less than five mins and thats going slow, but fedora 8 and below (plus others) just dont wanna see it on that driver, they see it as something completely different. Hence how you need to be a lot more hands-on and knowledgeable than the basics. But thankfully suse 11 and fedora 9 for some reason, now see's my belkin wireless card natively ????? Strange !!

Its a shame that theres no uniformity in linux. And that its maybe a bit hit-and-miss because of the hardware, and drivers, issue. Linux is in a catch 22 situation. The hardware vendors wont port drivers because linux hasnt taken off that much. And people wont flock to linux because its a case of your hardware may not be properly support, for example an all in one printer/scanner etc, Ive heard that all-in-one jobs work under windows but inder linux only the printer works. This would reaaly upset someone if they purchased a £100 all in one job, then decided to dual boot with linux, to then find that not all the printer works. They wouldnt have though to go search to see if it did work, they would assume it would, but this is the way windows makes you think.

Shall I shut-up now and go away for a couple of hours ? OK !!!!!

---

### Post by louieb on 2008-04-21
> **Stephen Budensiek said:**
> ...During startup, I get a line that says it cannot read the BIOS year, so it can't load ACPI drivers.   Is this machine un-useable, is something in Ubuntu screwed up, or what?
   Thank you.
Its a normal startup message for PCs with BIOS dated before 1999.  We all get it on our old P2s and P3s.  Hasn't stop me from doing anything on my old machine I can't do on a more modern PC. :) (Just slower).

---

### Post by gpilkay on 2008-04-21
> **phillipchandler said:**
> Wow. The replies to his post are rather polite. Normally under other distros, and maybe this one. if anyone asked a question like that then someone would have questioned the legitimacy of his parentage, for not at least finding out basic info, about the differences between Windows, Linux and Mac. You people are getting too polite in your old age(s), rather like me. hahahaha

Nah, it's a perfectly legitimate question.  I've made that mistake myself.  How is someone supposed to learn if they never get told anything useful?  Windows files ARE supported to some extent.  Look at ZIP or docx (with a converter).  As such, why would EXE be much different?  And in reality, it isn't, with WINE or the like.  Though I prefer to keep my Windows and Linux files separate to reduce headaches, there's really no technical reason anyone has to.  If there was, stuff like Crossover would not exist.

Besides, the software is free, so I figure the information should be free too.  Some call me an open-source activist.  I'd like to think so, but in reality I'm just a cheapskate.

---

### Post by phillipchandler on 2008-04-21
> **gpilkay said:**
> Nah, it's a perfectly legitimate question.  I've made that mistake myself.  How is someone supposed to learn if they never get told anything useful?  Windows files ARE supported to some extent.  Look at ZIP or docx (with a converter).  As such, why would EXE be much different?  And in reality, it isn't, with WINE or the like.  Though I prefer to keep my Windows and Linux files separate to reduce headaches, there's really no technical reason anyone has to.  If there was, stuff like Crossover would not exist.

Besides, the software is free, so I figure the information should be free too.  Some call me an open-source activist.  I'd like to think so, but in reality I'm just a cheapskate.

Well someone is supposed to learn by getting their hands dirty. How do you learn to ride a bike ? You get on, fall of, get back on, fall off again, and finally it sinks in. When I took driving lessons, I had some very basic understanding because I watch my parents drive, blah, blah, blah. The bloke still should have googled, even if he entered "Linux V Windows" he would have found wikipedia. The VERY basic info is basically VERY easy to find, no need to be an einstein here, or even ask the basic question that common sense & google would have given you the answer.
I hate to disagree but even I found out that exe files dont run under linux, and I didnt even have to ask, and Im a dumb smeghead. And before you all go off into one mentioning about wine and crossover, wine is crossovers poor brother, and crossover is limited to what you can run, ie dreamweaver, ms office etc, etc, etc.

And Im going to drop myself in the brown stuff by saying  that EXE files could basically be the same as installing a deb or rpm, except its done differently, MS takes all the effort out of installing it, just double click and two mins later its installed, no need for you to use a terminal. Crossover needs support, funds and major work to get even more win software supported, untill then its only going to be a small project, and will always make it better to keep your win partition and run win software from within win.

---

### Post by psycot on 2008-04-22
Hummm... and I choose a linux variant simply because, I don't want .exe files to run. That is what happened to my last install. Freaking malware put the smackdown on my MBR and the partition table. I still got back the few files I lost, and things are looking better than ever. I am actually having less driver problems now than with the other win product.

---

