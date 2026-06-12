---
title: "On/Off Ubuntu User...Have a LOT of questions on a few things in Ubuntu..."
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2008-03-27
I'm a frequent on/off ubuntu user and I have a lot of questions.  Please bare with me because I'm semi-noob at Ubuntu =).  Ok, here comes my questions.

1)  Everytime I install Ubuntu, to me, it's slower than windows and I'm thinking it shouldn't be as my PC is decent and it runs perfectly on Windows.  Is is the version of Ubuntu I've been installing or something else?

2)  I can never find the fonts that Windows has, I"m a web developer and I sometimes need fonts that come with Windows so I can view things with real Windows fonts.  (it helps to when viewing websites, etc)

3)  Gaming, the only game I really play is GrandChase, don't know if you've heard of it, but it uses nProtect GameGuard and I've had a LOT of problems trying to get that to work in WINE.  Would a virtual machine be better for that and are there any free ones that don't hog memory up a lot?

4)  Web developement editor or something similar to Notepad2, Notepad++, etc.

5)  How does Photoshop CS3 run via Wine?

6)  Network sharing from WinXP and Vista (laptop, got as replacement, and hard as hell to get linux working right on it :( I'd use it if Ubuntu or ANY linux worked right on it :(  )

I'm semi-noob on it and would really like some help on setting up a working, speedy, system.  My system specs are listed below.

Mobo: SOYO KT880v2
Processor: AMD Sempron 2.2ghz Socket A
Multiplier: x11
Graphics: Nvidia Geforce 6200gt
Memory: DDR 1gb
Sound: Onboard sound
HDD: 250gb Maxtor IDE
WinXP Pro SP2

I think that's all you'll need.

I currently have Ubuntu 5.04, 6.10, 7.04, 7.10, Fedora 3, Fedora 4

Remember, I'm semi-noob with this so please explain so I can understand LOL.  Also, any wanna be a 'mentor' I can talk to over AIM/MSN if I have any problems?

Thanks in advance,

~Bryce a.k.a zetsumei

---

### Post by DBrocks on 2008-03-27
Well, if you design web pages, Photoshop, and Game, its best to dual-boot between ubuntu and windows. Thats the best way. Any questions: feel free to ask

---

### Post by DBrocks on 2008-03-27
And also: PM me. I could possibly mentor you. I'm not too great at it either, but I know what I'm doing. I also have alot of Ubuntu-savvy friends who could help you.

---

### Post by Joeb454 on 2008-03-27
I don't think the CS3 suite runs under Wine.

CS2 however, does run under Wine, I think it's listed as a platinum app :)

---

### Post by zetsumei on 2008-03-27
I sortof of needed CS3 for my college class I'm in now.  Also, anyone know how to get a working, speedy ubuntu install on my system?  All the other times I tried installing, I'm either missing file that I didn't delete, forget to install, etc. or something else that happens for no apparent reason and causes havoc later on when I need something to work lol.

---

### Post by virtuallinux on 2008-03-27
well, as far as a good text/html editor, there's gedit, which is already installed (Application > Accessories > Text Editor, or open a terminal and type "gedit").  It's not quite as robust as Notepad++, but it does syntax highlighting for a number of markup/programming languages, and it supports tabs.  I also noticed today that there were some cool sounding plugins, although I've never tried any of them. 

A second option would be Geany, which you can find in Add/Remove.  It's really more geared towards programming, but it'll work for a web developer and has many of the same capabilities as Notepad ++.

I should be able to help you with network file sharing, but that's going to take a little more thought on my part.

---

### Post by Joeb454 on 2008-03-27
If you need it, I'd recommend dual booting your Ubuntu installation with Windows so you can continue using CS3 :)

---

### Post by DBrocks on 2008-03-27
> **Joeb454 said:**
> If you need it, I'd recommend dual booting your Ubuntu installation with Windows so you can continue using CS3 :)

Ah yes, a genius and I finally see something the same way!

---

### Post by zetsumei on 2008-03-27
> **Joeb454 said:**
> If you need it, I'd recommend dual booting your Ubuntu installation with Windows so you can continue using CS3 :)

I just realized, it's on my laptop, so I don't need it on my desktop no more.  Also, the only game I play daily runs fine on my laptop, so throw that issue out.

So, with those two things not a problem no more.  What can I do about the fonts, network sharing, etc?  Also, is it normal for like fluxbox, blackbox, or any other window manager to be screwed totally up after a fresh install?  Because EVERY time I try to install one of them, it screws up and I'm missing like half the files I need for menus, etc, etc.  I would like a fluxbox window manger, but I would want some fluxbox guru to walk me through making a menu, auto starting apps (volume controls, etc.) installing movie plugins and mplayer plugins, etc.

I'm going to get some paper and write down exactly what I need to install to get it working just as my windows system does.  Movie/MP3 plugins, etc, etc.  I also have an ipod video 30gb black, anyway to get a program that allows me to manage music on that working properly?  Last few times I've tried to get that working, it never did, there were always problems.

---

### Post by Joeb454 on 2008-03-27
Try running Fluxbuntu instead then (I can't remember the website right now...Google will tell you though :))

---

### Post by zetsumei on 2008-03-27
I have tried fluxbuntu, but I like the option of having a choice if I wanna test out a new wm or something.  Any noob-friendly guides on fluxbox wm (installing, customizing, etc)?

---

### Post by virtuallinux on 2008-03-27
Ok, there are several ways to go about accessing you're windows file shares. This is the way I do it; it's probably the most transparent, but it's also the most cryptic.

First, you need the computer name of you're Windows machine, and the names of the file shares.
For the computer name, in windows, right click on My Computer and select "Properties", then select the "Computer Name" Tab.
For the name of the Shared Folder, right click on the folder you're sharing and select "Sharing and Security".

Once you've got that information, open up a terminal in Ubuntu, and type this:
```

sudo gedit /etc/fstab

```

This will open up you're filesystem configuration file in a text editor.  Don't do anything to what's already there, as that could cause significant problems.  Go to the end of the file and add the lines:
```

#you can use the # symbol to add comments, lines starting with # are ignored
//nameofwindowsmachine/nameofsharedfolder   /mnt/nameofsharedfolder  smbfs password=mypassword,uid=myuserid,username=myusername,defaults,allow_other,umask=0,users,nls=utf8,noexec 0 0

```

one problem I've had in the past is that the name of the windows machine sometimes gets misinterpreted, so you may need to use the machine's IP address instead.  Also, I'm not quite sure of what the difference is between the uid=myuserid and username=myusername, as I got this code in the same way that you're getting it.  Is there anyone else that can explain this to us?

once you've added those, you'll need to do a couple of other things.

first, create the directories that we're going to mount the file shares too, type:
```

sudo mkdir /mnt/nameofsharedfolder

```

then we need to install the package that allows us to use the *mount* command for network shares:
```

sudo apt-get install smbfs

```

then, to mount the shares:
```

sudo mount /mnt/nameofsharedfolder

```

These instructions are kinda complicated, more so than I remember;  Try this, and let me know if you have any problems.

---

### Post by cisforcojo on 2008-03-27
Well, re: using Microsoft fonts, run:

```
sudo apt-get install msttcorefonts
```

You can actually pull (some of) the truetype fonts from your windows folders and use them but try this first and see if that's what you need. 

Re: your iPod, I use Floola and it's fantastic! [http://www.floola.com](http://www.floola.com)
It's a lot better than GTKPod and Amarok for iPod management.

---

### Post by zetsumei on 2008-03-28
> **virtuallinux said:**
> Ok, there are several ways to go about accessing you're windows file shares. This is the way I do it; it's probably the most transparent, but it's also the most cryptic.

First, you need the computer name of you're Windows machine, and the names of the file shares.
For the computer name, in windows, right click on My Computer and select "Properties", then select the "Computer Name" Tab.
For the name of the Shared Folder, right click on the folder you're sharing and select "Sharing and Security".

Once you've got that information, open up a terminal in Ubuntu, and type this:
```

sudo gedit /etc/fstab

```

This will open up you're filesystem configuration file in a text editor.  Don't do anything to what's already there, as that could cause significant problems.  Go to the end of the file and add the lines:
```

#you can use the # symbol to add comments, lines starting with # are ignored
//nameofwindowsmachine/nameofsharedfolder   /mnt/nameofsharedfolder  smbfs password=mypassword,uid=myuserid,username=myusername,defaults,allow_other,umask=0,users,nls=utf8,noexec 0 0

```

one problem I've had in the past is that the name of the windows machine sometimes gets misinterpreted, so you may need to use the machine's IP address instead.  Also, I'm not quite sure of what the difference is between the uid=myuserid and username=myusername, as I got this code in the same way that you're getting it.  Is there anyone else that can explain this to us?

once you've added those, you'll need to do a couple of other things.

first, create the directories that we're going to mount the file shares too, type:
```

sudo mkdir /mnt/nameofsharedfolder

```

then we need to install the package that allows us to use the *mount* command for network shares:
```

sudo apt-get install smbfs

```

then, to mount the shares:
```

sudo mount /mnt/nameofsharedfolder

```

These instructions are kinda complicated, more so than I remember;  Try this, and let me know if you have any problems.

Thanks.  I'll save this for after I get Linux installed again.  I'm backing up some data first now and then going to try to re-install linux with the 7.10 dvd I have of Ubuntu.  If that doesn't work, I'll just go grab a new download of it XD.

> **cisforcojo said:**
> Well, re: using Microsoft fonts, run:

```
sudo apt-get install msttcorefonts
```

You can actually pull (some of) the truetype fonts from your windows folders and use them but try this first and see if that's what you need. 

Re: your iPod, I use Floola and it's fantastic! [http://www.floola.com](http://www.floola.com)
It's a lot better than GTKPod and Amarok for iPod management.

How would I install Floola?  Will I need to compile it, etc?  If so, how do I get the compilers for it?  But thanks for that app =).

---

### Post by cisforcojo on 2008-03-28
No, you don't need to compile it.
You can go to [http://www.floola.com/modules/wiwimod/index.php?page=download_linux](http://www.floola.com/modules/wiwimod/index.php?page=download_linux)
and select the torrent option or the direct download option. That'll give you a .tar.gz.

You'll first want to install libnotify-bin, though:

```
sudo apt-get install libnotify-bin
```

Then, decompress floola using File Roller (double click on the icon on your GNOME desktop) or you can use:
```
tar zxvf filename.tar.gz
```

Enjoy!

Since you asked about compiling, a REALLY useful site is [http://www.getdeb.net](http://www.getdeb.net)
First check there for anything before you compile. It makes life so much easier. There is some sort of server problem with the site now but it won't last long and it's really helpful.

---

### Post by zetsumei on 2008-03-28
Do I need to run anything to install it?  Or just untar it and it's in my home dir and then what?  I should say, I'm addicted to fluxbox, so commands only please XD.

---

### Post by zetsumei on 2008-03-28
Anyone have any other answers to my questions?

(i.e. speeding up the system, it seems to slow LOL )

---

### Post by regomodo on 2008-03-28
> **Joeb454 said:**
> I don't think the CS3 suite runs under Wine.

CS2 however, does run under Wine, I think it's listed as a platinum app :)

the suite doesn't. i know for a fact bridge and imageready cs2 doesn't . Photoshop cs2 compatibility is 90%

I don't know if anyone has mentioned it yet but turning off the indexing service in Ubuntu (beagle?) may help

---

### Post by lswest on 2008-03-28
yeah, i run a dual boot system of Vista and Hardy Heron (i need vista for cs3, which i in turn need for my school yearbook and web design clubs XD).  And yeah, i'd be happy to add you to my msn, maybe not become your mentor, but i'm always happy to help, my email is listed on this account, so feel free to add me if you need or feel like it.  I can't promise you i can fix everything, but i do a pretty good job fixing problems i do have :P  Anyways, i agree with what was said before, dual boot is best for cs3, a notepad program like notepad++? some people like emacs, personally i just use gedit :P  Also, the msttcorefonts should be all the fonts you need, and regarding fluxbox, i personally don't use it much, so i'm not one to be asked regarding customizing it :P

Also, about the slow computer, can you post the output of ```
free
``` and answer this question: when does it seem slow? booting? or just during everyday use?

---

### Post by zetsumei on 2008-03-28
> **lswest said:**
> yeah, i run a dual boot system of Vista and Hardy Heron (i need vista for cs3, which i in turn need for my school yearbook and web design clubs XD).  And yeah, i'd be happy to add you to my msn, maybe not become your mentor, but i'm always happy to help, my email is listed on this account, so feel free to add me if you need or feel like it.  I can't promise you i can fix everything, but i do a pretty good job fixing problems i do have :P  Anyways, i agree with what was said before, dual boot is best for cs3, a notepad program like notepad++? some people like emacs, personally i just use gedit :P  Also, the msttcorefonts should be all the fonts you need, and regarding fluxbox, i personally don't use it much, so i'm not one to be asked regarding customizing it :P

Also, about the slow computer, can you post the output of ```
free
``` and answer this question: when does it seem slow? booting? or just during everyday use?

Last time I had ubuntu installed on my desktop, it seemed slow booting and it just wasn't as snappey as I thought it would be.  My winxp partition was actually faster than it and it's so crapped up.

---

### Post by anjilslaire on 2008-03-28
> **zetsumei said:**
> 
Mobo: SOYO KT880v2
Processor: AMD Sempron 2.2ghz Socket A
Multiplier: x11
Graphics: Nvidia Geforce 6200gt
Memory: DDR 1gb
Sound: Onboard sound
HDD: 250gb Maxtor IDE
WinXP Pro SP2 cracked


It concerns me more than a bit that people are suggesting the OP dual-boot, when it seems clear that the XP being used is pirated...

I realize we like to think of ourselves as superior (for lack of a better word) for using FOSS when possible, but when using MS software I think we shouldn't just ignore blatant piracy when advertised. If the OP needs to dual-boot, then XP should be gotten lawfully. Or use his Vista laptop.

I'll crawl back into my corner now, thanks
/soapbox off

---

### Post by lswest on 2008-03-28
i didn't even notice that...thanks for pointing that out anjilslaire

last suggestion about the slow ubuntu, check the splash screen size & vga settings, that can slow down the splash screen load, and Gutsy is a bit slower at booting than previous versions, Hardy is quicker again, so either downgrade or upgrade.  And again, we do not condone piracy or otherwise illegally obtained software.

---

### Post by zetsumei on 2008-03-28
Maybe I shouldn't of mentioned that.  That's a reason why I'm moving BACK to ubuntu now.  I don't justify paying for a POS OS.  Just my opinion.  So, what things should I do after a clean install?

-install ubuntu
-get updates RIGHT AFTER, am i right?
-install gfx drivers
-install other drivers that i need
-install fluxbox
-install mp3/movie players
-install torrenting program
-customize fluxbox
-anything else?

---

