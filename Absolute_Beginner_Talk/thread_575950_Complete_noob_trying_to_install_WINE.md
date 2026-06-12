---
title: "Complete noob trying to install WINE"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by rock4217 on 2007-10-14
I am brand new to ubuntu my friend installed it for me and I can't even figure out how to install Wine can someone point me to a tutorial for someone who has been using windows his entire life? Also I am using a laptop if that changes anything.

---

### Post by rock4217 on 2007-10-14
I have been using Ubuntu for an hour and I'm about to blow up my computer. Yes it makes my computer run faster yes it is clean and smooth. No it is not fun trying to install WINE no it is not fun being completely lost when trying to figure out how to do no it is not fun trying to find a single thing in this user unfriendly system. I AM LOST HELP ME OUT HERE oh and help with this [http://ubuntuforums.org/showthread.php?t=575950](http://ubuntuforums.org/showthread.php?t=575950)

---

### Post by Shazaam on 2007-10-14
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by smartbei on 2007-10-14
I'm not next to my Ubuntu PC right now, but I think:
```

sudo aptitude install wine

```
should work. Keep in mind that WINE is not always simple to set up and use for all windows applications.

---

### Post by mivo on 2007-10-14
You install it like every other application that is in the repository: *System -> Administration -> Synaptic Package Manager*, then search for Wine, mark it, press "Apply", and the system will take care of getting the files and installing everything.

For the latest version, you will need to add the Wine repository, but try the above first. One step at a time.

---

### Post by ukripper on 2007-10-14
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Pumalite on 2007-10-14
[http://www.winehq.org/site/docs/wineusr-guide/index](http://www.winehq.org/site/docs/wineusr-guide/index)
Linux is not for everyone. Usually patience and a desire to learn is needed.

---

### Post by ukripper on 2007-10-14
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by rock4217 on 2007-10-14
Thanks i've been going insane trying to work it and i'm just not good at this but time changes everything

---

### Post by pizzutz on 2007-10-14
Sure, we can help you with that.  First thing you are going to want to do is go to system->administration->synaptic package manager from your top menus.  This will require your password, and will be how you install most of your software. click search, and type wine. it will bring up a list of a few packages, right click on wine and select mark for installation, then click apply.  It should auto install for you.  After it's done, hit alt-F2 (same as run program from windows) and type winecfg.  this will allow you to configure wine, and it will create a .wine/drive_c directory in your home folder.  (directories starting with a . anre normally hidden, so if you are looking for it from nautalas (windows my computer equivalent) you will have go to view->show hidden files to be able to see it.

Let us know if you need anymore help getting programs to run under wine.

cheers

p.s. don't give up, it's really not harder, just different from what you are used to.

---

### Post by bobplano on 2007-10-14
ok i'm going to give you terminal commands but you can just copy and paste them. i'll explain what each line basically does. 

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

this gets the 'key' which means ubuntu will trust this repository, i think ubuntu or canonical assigns these. 

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
``` 

this adds the repository, which is just a server that has downloadable software on it. you don't have to go anywhere on the internet to get them though, there are commands for you.

```
sudo apt-get update
sudo apt-get install wine
```

this will update your repository information, meaning if there are any updates it will tell you. also any added repositories will be checked for software. it will also install wine, there isn't supposed to be any kind of wizard so don't worry about that. 

for the sudo command it will ask you for your password. this is the password you logged on with

---

### Post by mivo on 2007-10-14
And try to relax some. I don't mean this to sound patronizing or anything, but if you are so angry and frustrated after one hour of learning a new "thing", you cause yourself unnecessary stress. Think of how long it took you to learn and understand all the subtleties of Windows. Be patient with yourself, use the search function of the forum, and explore.

---

### Post by ukripper on 2007-10-14
And don't forget your best friend  while searching- Google

---

### Post by rock4217 on 2007-10-14
Alright thanks again I hope you can understand why i am so frustrated.

---

### Post by Bloch on 2007-10-14
Forget about wine!!!!
Wine only works out-of-the-box for very simple windows programs. For others you need to find dll files etc etc

You know what wine is, don't you? It enables you to run (some) windows programs. 

For the first few days in ubuntu just install stuff from the Add Programs menu - it downloads them and installs them.

Don't try to compile stuff, DO NOT search the web for linux programs, and don't use wine.

Here's a blog with some recommended cool applications to install
[http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html](http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html)

and read the stickies at the top of the forum here, or at least glaance through them

---

### Post by mivo on 2007-10-14
We have given you a number of different ways to do what you want, so let me mention that they are only different ways of achieving the very same thing. You can use the graphical interface (Synaptic), a text/terminal interface, or a mixture of both. They all use the same underlying packaging system that handles getting, installing, managing and configuring software. Any of the ways will work, you can just use whichever you prefer, or all of them at different times. Only important is that you try to understand what is happening.

Just adding this so that you don't get confused because you asked for one thing and got three or four *seemingly* different answers. :)

---

### Post by rock4217 on 2007-10-14
No I understand that they are different ways and I understand how this works sorta but understanding how it works and actually using it are two completely different things

---

### Post by HermanAB on 2007-10-14
...and if you wish to complain about Ubuntu, then you should post on a Windows bulletin board like this one: [http://forums.pcworld.com/index.jspa](http://forums.pcworld.com/index.jspa)
;)

---

### Post by Pumalite on 2007-10-14
Starting different threads on the same subject it only leads to confusion on the part of those who try to help you.

---

### Post by -grubby on 2007-10-14
it's natural to get frustrated when learning ANYTHING new. Just because its hard for a Windows user ,doesn't mean it will be AS hard for a new computer user. Think of Ubuntu as a second language

---

### Post by NeBiRuSs on 2007-10-14
If you want to install wine just

sudo apt-get install wine

---

### Post by Pumalite on 2007-10-14
Here is what to do right after installing Ubuntu:

[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by xpod on 2007-10-14
> And try to relax some. I don't mean this to sound patronizing or anything, but if you are so angry and frustrated after one hour of learning a new "thing", you cause yourself unnecessary stress. Think of how long it took you to learn and understand all the subtleties of Windows. Be patient with yourself, use the search function of the forum, and explore.

This always cracks me up,the self proclained (win)power user spends X amount of years learning how to make his system run to best of his ability but then one day with Linux and all hell breaks loose with machines blowing up,Ubuntu eating Windows and of course .....how the hell are mom & pop ever going to manage if teh power users cant eh:???:

Not directing that at you rock4217 but we see it soooo many times.
Years of dedication,patience,frustration & of course anger with Windows but then one day with Linux will often result in first posts full of crazy assertions about Linux.

Being very very new to computers at the time i`m not saying Linux was/is easy to get the head round but then neither really is Windows,especially if your starting from scratch.
Having gave both a more equal chance this last 19 months than many have i think i can say without a shadow of a doubt that ...Ubuntu in particlar, is just so much easier to run well and keep running well.It`s more logical in it`s approach,more educational,safer in a family environment and it`s certainly much more of a pleasure to use.........it`s a joy to use.

All i can say is that with Windows, i spent the few months i used it learning how to keep a pc usable but with Linux,i`ve now spent 15 months learning how to actually *use* a pc:)
Ubuntu/Linux is of course not for everyone rock 4217 but if you`re at least trying it out then you must surely afford it just a little of that time & patience you`ve no doubt given Windows over the years.
That much at least eh??

Good luck either way ok
p.s...dualbooting is a wonderful thing...If needs must of course:)

---

### Post by aysiu on 2007-10-14
> **Pumalite said:**
> Starting different threads on the same subject it only leads to confusion on the part of those who try to help you.
Which is why I merged the two threads and deleted the "bump."

---

### Post by Pumalite on 2007-10-14
Thanks. It helps a lot.

---

