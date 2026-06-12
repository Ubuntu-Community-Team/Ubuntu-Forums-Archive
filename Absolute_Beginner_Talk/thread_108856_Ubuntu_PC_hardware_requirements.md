---
title: "Ubuntu PC hardware requirements"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by Roland Bouman on 2005-12-27
Hi there,

(Im running ubuntu on a 266Mhz pentium, 92Mb RAM laptop, and things are rather slow.)

anyone out there that can tell me what the minimum and recommended hardware requirements are for running ubuntu on a personal computer or laptop for the folowing profiles

-home computing, some office, administration, photobooks, games etc
-developing internet applications, (mysql or postgres)database design

?

Thanks in advance,
Roland

---

### Post by poofyhairguy on 2005-12-27
[QUOTE=Roland Bouman]Hi there,

(Im running ubuntu on a 266Mhz pentium, 92Mb RAM laptop, and things are rather slow.)

anyone out there that can tell me what the minimum and recommended hardware requirements are for running ubuntu on a personal computer or laptop for the folowing profiles

-home computing, some office, administration, photobooks, games etc
-developing internet applications, (mysql or postgres)database design

?

Thanks in advance,
Roland[/QUOTE]


Personally, Ubuntu needs a 200+ mhz CPU and 128 MB of RAM to work worth a darn I think. Make that 400mhz and 256 MB of RAM to run well, and 400mhz and 512 MB of RAM to fly.

If you could not tell, its the ram that matters most. That machine you have with a 256mb upgrade would run Ubuntu great. 

Of course, there is THIS guide:

[http://ubuntuforums.org/showthread.php?t=98233&highlight=low+ram](http://ubuntuforums.org/showthread.php?t=98233&highlight=low+ram)

---

### Post by Roland Bouman on 2005-12-27
Thanks a lot! 

These requirements are actually quite a lot lower than I'd imagined :D 

Say, am I right in assuming that it is the gnome thingie that's hungry for memory? Would a minimal server installation lift the requirement for much memory?

---

### Post by chimera on 2005-12-27
yeah, try ditching gnome for icewm or fluxbox.

---

### Post by Lord Illidan on 2005-12-27
There's always XFCE if you want a better gui..

Also, consider other distros. Zenwalk and Damn Small Linux are great for old computers.

---

### Post by Roland Bouman on 2005-12-27
Ok, thanks all! 

The 266Mhz machine was just something I had available for hacking, I've decided I am going to run Ubuntu (or another Linux distribution, but Ubunto is my only point of reference now) on a modern machine. 

There's one little thing though, I did open a graphical system monitoring tool (cant' remember the exact name right now, it resembles the windows task manager alot); this told me the background activity of the system was consuming about 10% cpu and around 50Mb - 60Mb of physical memory. 

Also, I did not experience any disk thrashing (indicating swap activity, no?). 

So, my initial conclusion was that it really was the processor that was not really up to it. 

However, point taken. Once I got it up and running (having some installation troubles there to get unbunto to run from an external SCSI drive) on my desktop machine, I will try and install other window managers.

Thanks again for all of your time!

---

### Post by bernardfrancois on 2005-12-27
I have ubuntu running on a 366mhz laptop with 320mb ram. It runs fine for what I need it (surfing, chatting, programming).

I tried FC3 with XFCE before (on the same computer), and it didn't work as fast as Ubuntu does with Gnome.
Maybe it's because it's Ubuntu and not FC3, but I would rather think that Gnome is faster than XFCE. XFCE looks more basic, but I think it's not coded very good. I would prefer TWM above XFCE...

---

### Post by Lord Illidan on 2005-12-27
XFCE is definitely faster than GNOME...

about the RAM, well, firefox is a big hog...

---

### Post by poofyhairguy on 2005-12-29
[QUOTE=Lord Illidan]XFCE is definitely faster than GNOME...

about the RAM, well, firefox is a big hog...[/QUOTE]

Yeah use Epiphany.

---

### Post by Roland Bouman on 2005-12-29
Ok, guys 

thanks for all your input.

As of yesterday, I'm running Ubuntu from my desktop machine, a 2.8GHz Intel Hyper Threading desktop with 1Gb RAM. What I've seen on my old laptop's convinced me enough that it is well worth a more thorough exploration on a modern machine

The machine was already sitting on my desk running windows, and now it's a dual boot with ubuntu. Needless to say, it runs blazingly FAST :D . My impression is that it runs more smoothly than Windows, but I'll have to use it for a couple of weeks, do some administrative tasks etc before I can make a balanced judgement.

My first impressions are very, very favourable towards ubuntu :cool: , much more so than I would've guessed on beforehand. And I haven't even taken a look at other window managers. tsk...

---

### Post by towsonu2003 on 2005-12-29
have a machine 300 mhz 64mb ram (250mb swap) 4gb hdd, xubuntu runs well. slow to launch programs, but faster than windows I think... winmodem not working so dont know how it would perform on the web (flash or javascript-rich websites etc). 

for xubuntu: install ubuntu, connect to internet, ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
``` and choose XFCE for session in next login. use abiword instead of openoffice, epiphany instead of firefox... 

You could also experiment with window managers in Slackware. 

> 400mhz and 512 MB of RAM to fly on my hp pavilion zv5120us, with 2.80 ghz (celeron) 1GB ram 2 GB swap, it is *not* flying at all in my machine...

---

### Post by Rinzwind on 2005-12-29
Hey Roland. Just don't drop Ubuntu when you think you can't solve something. Post it here 1st ;)

Greetings from Eindhoven :)

---

### Post by mcduck on 2005-12-29
[QUOTE=Roland Bouman]O
As of yesterday, I'm running Ubuntu from my desktop machine, a 2.8GHz Intel Hyper Threading desktop with 1Gb RAM. What I've seen on my old laptop's convinced me enough that it is well worth a more thorough exploration on a modern machine

The machine was already sitting on my desk running windows, and now it's a dual boot with ubuntu. Needless to say, it runs blazingly FAST :D . My impression is that it runs more smoothly than Windows, but I'll have to use it for a couple of weeks, do some administrative tasks etc before I can make a balanced judgement.
[/QUOTE]
Have you installed the 686-smp kernel already? That should make Ubuntu even faster.. (if you haven't, run 'sudo apt-get install linux-686-smp')

---

### Post by Roland Bouman on 2005-12-29
[QUOTE=Rinzwind]Hey Roland. Just don't drop Ubuntu when you think you can't solve something. Post it here 1st ;)

Greetings from Eindhoven :)[/QUOTE]

Thanks dude, dankjewel vriend :D.

I was never thinking of dropping ubuntu or Linux, far from it. I just happend to have a machine doing nothing, so I decided that would be a perfect guinea pig for this experiment. 

I figured that particular box might be too low end to run, well, frankly any kind of modern software. I posted about the req's because I couldnt find any hint on the ubuntu site, and i was just curious.

CU

---

### Post by Roland Bouman on 2005-12-29
[QUOTE=mcduck]Have you installed the 686-smp kernel already? That should make Ubuntu even faster.. (if you haven't, run 'sudo apt-get install linux-686-smp')[/QUOTE]

As soon as I had it up and running, the system itself offered to perform a kernel update :cool:. Is that it, or is this another update?

---

### Post by Roland Bouman on 2005-12-29
[QUOTE=towsonu2003]
for xubuntu: install ubuntu, connect to internet, ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
``` and choose XFCE for session in next login. use abiword instead of openoffice, epiphany instead of firefox... 

Thanks for the tip! I will try this as soon as I got a more or less complete environment (I still need to install MySQL, eclipse/BIRT, Apache, PHP and so much more...)

---

### Post by Ruskie on 2005-12-29
[QUOTE=Roland Bouman]As soon as I had it up and running, the system itself offered to perform a kernel update :cool:. Is that it, or is this another update?[/QUOTE]

Yeah, it's correct, and it's a kernel update (only a subversion though). It happens quite frequently, I'd say at least once in a couple of months, often more. We're not on Windows anymore... ;)
Your grub is automatically updated so that you have the choice to boot with your new version or the old one. When you're confident that the new version works fine and you no longer feel the need for the old one, you can edit menu.lst to delete options, and you can alos dump the old kernel package....

Regards
Marco

---

### Post by Roland Bouman on 2005-12-29
> **Ruskie]It happens quite frequently, I'd say at least once in a couple of months, often more. We're not on Windows anymore...  said:**
> 

Ok, so that's a lot like other open source products. I love it :D 

[QUOTE=Ruskie]Your grub is automatically updated so that you have the choice to boot with your new version or the old one. When you're confident that the new version works fine and you no longer feel the need for the old one, you can edit menu.lst to delete options, and you can alos dump the old kernel package....

That's funny you mention it! Actually, I did notice that already even before rebooting...See, Because I want to have ubuntu installed on an external hard drive I had to follow a somewhat different installation procedure. You can read about it here: [http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

Anyway, I just reviewed that thread yesterday when this post cut my eye:
[http://www.ubuntuforums.org/showpost.php?p=593793&postcount=112](http://www.ubuntuforums.org/showpost.php?p=593793&postcount=112)
So, unlike unlucky Dave, I was in a position to edit my menu.lst before rebooting, and there, I noticed a total of 6 ubuntu related entries (instead of the three before). I already wondered where they came from.

I guess you just gave me the answer :cool:. Thanks!

---

### Post by Roland Bouman on 2005-12-29
[QUOTE=towsonu2003]for xubuntu: install ubuntu, connect to internet, ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
``` and choose XFCE for session in next login. use abiword instead of openoffice, epiphany instead of firefox... [/QUOTE]

Hey, thanks man! 

I just ran that, and logged in with a XFCE session. :cool:  

Q1: does it happen to be so simple for XFCE, or are most of these window managers so easy to set up? (I mean, no manual setup afterwards, questions during install etc?)
Q2: judging from the pattern of these lines of code, I would run 
```
sudo apt-get update
```
to update apt itself, and then 
```
apt-get install {some package}
```
to install a specific item.
Are these assumptions correct? If so, where can i find a list of valid items?

---

### Post by afhp on 2005-12-29
[QUOTE=Roland Bouman]
I figured that particular box might be too low end to run, well, frankly any kind of modern software. [/QUOTE]

This kind of old hardware makes a great firewall/router. Put a second ethernet card in, install IPCop, and forget it's even there.

---

### Post by Ruskie on 2005-12-29
[QUOTE=Roland Bouman]Hey, thanks man! 

I just ran that, and logged in with a XFCE session. :cool:  

Q1: does it happen to be so simple for XFCE, or are most of these window managers so easy to set up? (I mean, no manual setup afterwards, questions during install etc?)
Q2: judging from the pattern of these lines of code, I would run 
```
sudo apt-get update
```
to update apt itself, and then 
```
apt-get install {some package}
```
to install a specific item.
Are these assumptions correct? If so, where can i find a list of valid items?[/QUOTE]

First of all, yes: I think I answered your question about the menu.lst lines. ;)
A1: Basically, yes. That's because unlike Windows (tm) that is both an operating system, a graphical environment and windows manager, here the three things are made Unix style, that is: do just one thing, but do it good.
In Unix/Linux all the graphic "hard work" is made by the X Window system, and XFCE (KDE, Gnome, Blackbox etc. etc.) merely acts as window manager.
Comparing Windows setup to XFCE one would not be fair I think, because XFCE only does the job that in Windows does explorer.exe, and you don't have much to configure for explorer too...
A2: Yes they are. These two tasks can be graphically managed by synaptic as well, you don't need to go through command line if you don't want to.

---

### Post by Ruskie on 2005-12-31
[QUOTE=Ruskie]
A2: Yes they are. These two tasks can be graphically managed by synaptic as well, you don't need to go through command line if you don't want to.[/QUOTE]

While re-reading my answers, and your questions, I noticed I got you on the wrong line, and didn't show you correctly what apt-get should be blessed for.

*apt-get update* does NOT update itself: it scans ALL the packages you have installed, and if on the repositories founds a new version for any of those, it prompts you to update it. Even better, isn't it? ;)

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=Ruskie]
*apt-get update* does NOT update itself: it scans ALL the packages you have installed, and if on the repositories founds a new version for any of those, it prompts you to update it. Even better, isn't it? ;)[/QUOTE]
this is partly correct. basically, apt-get update scans the repositories and updates your local list of available packages. it stops there. from there, when I'm lazy, I usually do a ```
sudo apt-get -s upgrade
``` to check if there are any new versions are available. in there, apt-get upgrade upgrades all packages but -s tells it to stimulate (not to act). so if you wanna see what can be updated: ```
sudo apt-get update
sudo apt-get -s upgrade
```
if you wanna update packages (if available) ```
sudo apt-get update
sudo apt-get upgrade
```

well, either that or you can just use synaptic :) 
In Gnome: System>Administration>Synaptic (a front end to apt-get)
In Xubuntu: don't remember, but it is somewhere in the menus :)

I am guessing you'll like this even more after seeing the available package list from within synaptic ;)

---

### Post by mcduck on 2006-01-01
[QUOTE=Roland Bouman]As soon as I had it up and running, the system itself offered to perform a kernel update :cool:. Is that it, or is this another update?[/QUOTE]
No, it updated the default 386 kernel to a new version. You'll still have to install 686-smp kernel yourself. (but after you do that, it'll get automatic updates just like the default kernel does)

---

