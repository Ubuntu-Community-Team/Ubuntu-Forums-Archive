---
title: "Ubuntu driver query"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Brendan Hart on 2007-06-10
Do i need to install my drivers, it seems they are already installed but i dont know, my sound is working didnt install sound drive, my monitor seems to be fine, no slow refresh rate, havnt installed my vga drivers.

also theres seems to be some command line to install programs but i dont know how to access let alone use it

---

### Post by KitChy on 2007-06-10
[http://wiki.freespire.org/index.php/Using_Apt](http://wiki.freespire.org/index.php/Using_Apt)

May help you out!

---

### Post by Rui Pais on 2007-06-10
> **Brendan Hart said:**
> Do i need to install my drivers, it seems they are already installed but i dont know, my sound is working didnt install sound drive, my monitor seems to be fine, no slow refresh rate, havnt installed my vga drivers.
No you don't. Linux kernel have usually the needed "drivers", they are called modules on Linux.
The only one that people usually need to install is for specific hardware for better support then the default one (usually proprietary ones, like nvidia) 
If you don't have slow refresh rates, sound and network works, save yourself more troubles :)

> 
also theres seems to be some command line to install programs but i dont know how to access let alone use it

command line is:
```
sudo apt-get install <package>
```
or (in some ways better):
```
sudo aptitude install <package>
```

to remove (uninstall):
```
sudo apt-get remove <package>
```

you can use Synaptic too (a graphical interface)
Is in menus (on System)

A good starting place for installing software:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Brendan Hart on 2007-06-10
I looked for packages using synaptic package thingy, i found bluefish and marked/installed it that way, is that a good way didnt see anyways of putting in commands

---

### Post by zzirf on 2007-06-10
Yes I am in the same boat.  A newbie and wondering how to install "drivers" for my canon printer which is not working under ubuntu (attempts to print went to postscript or whatever that is) and also for my DNTVLive! DVB-T TV card to use with mythtv I think.  It says to install the hardware drivers before mythtv but I don't have any linux drivers and even if I did I would not know how.

Is there a howto about installing drivers anywhere?  I have used synaptic but I have forgotten already what I did.  

Is there a howto about finding drivers anywhere on these forums.

Does anyone know what the drivers or modules or whatever you call them are for the DNTV Live! DVB-T are called and do I have any other things that I need that has to go with them (is it dependencies?)?

Thanks in advance for your help,

---

### Post by Rui Pais on 2007-06-10
> **Brendan Hart said:**
> I looked for packages using synaptic package thingy, i found bluefish and marked/installed it that way, is that a good way didnt see anyways of putting in commands

Yes thats the way, now you just press Apply. Thats all. :)

To type in command you need a terminal. 
Search in menus (Under Accessories i think) or Press Alt+F2 and type on the empty field: gnome-terminal.

---

### Post by zzirf on 2007-06-10
Hi Brendan,

I have no idea what bluefish is but yes that marking and applying does it as far as installation goes I think.

The command line you are looking for I think may be the "terminal".  Go to Applications > Accessories > Terminal.

I'd like to know a short cut key combo for opening it if anyone out there knows it please.

But getting back to installing stuff from there, all I can remember for now is that to istall anything you need to use the "sudo" command because it allows you to become a super user if you put in your password , which in turn lets you install.  But if it is available from synaptic then that is sure easier unless you are just copying and pasting code from these forums or some other howto site.

But do not ask me how to install anything that is archived on my desktop - like some dvb driver package I found somewhere in my search all bound up in a gzip.tar or some such name.  I can extract it...but then what?

It is frustrating being a newbie once again,

Cheers,

---

### Post by Rui Pais on 2007-06-10
> **zzirf said:**
> Yes I am in the same boat.  A newbie and wondering how to install "drivers" for my canon printer which is not working under ubuntu (attempts to print went to postscript or whatever that is) and also for my DNTVLive! DVB-T TV card to use with mythtv I think.  It says to install the hardware drivers before mythtv but I don't have any linux drivers and even if I did I would not know how.

Is there a howto about installing drivers anywhere?  I have used synaptic but I have forgotten already what I did.  

Is there a howto about finding drivers anywhere on these forums.

Does anyone know what the drivers or modules or whatever you call them are for the DNTV Live! DVB-T are called and do I have any other things that I need that has to go with them (is it dependencies?)?

Thanks in advance for your help,

Now, thats deep waters... 

Canon printer is famous for bad Linux support. Whats the model?
About your tv card... that should be a hard one. Do a search on Google and This forum.

---

### Post by Brendan Hart on 2007-06-10
i once pressed alt f2 came up with a dos like interface and i couldnt get out of it

---

### Post by Outrunner on 2007-06-10
> **Brendan Hart said:**
> i once pressed alt f2 came up with a dos like interface and i couldnt get out of it

I think you mean CTRL-ALT-F2 and it isn't a DOS interface, it's called a terminal (or tty). To get back to your GUI - CTRL-ALT-F7

---

### Post by Rui Pais on 2007-06-10
> **Outrunner said:**
> I think you mean CTRL-ALT-F2 and it isn't a DOS interface, it's called a terminal (or tty). To get back to your GUI - CTRL-ALT-F7

Alt+F2 (on gnome) -> a "Run App" thing it will run apps you choose or type the names.

Gnome-terminal is the terminal used in gnome

Alt+Ctrl+F2 (or F1...F6) gives you a console (non graphical Linux)

---

### Post by Rui Pais on 2007-06-10
> **zzirf said:**
> ...
The command line you are looking for I think may be the "terminal".  Go to Applications > Accessories > Terminal.

I'd like to know a short cut key combo for opening it if anyone out there knows it please.

But getting back to installing stuff from there, all I can remember for now is that to istall anything you need to use the "sudo" command because it allows you to become a super user if you put in your password , which in turn lets you install.  But if it is available from synaptic then that is sure easier unless you are just copying and pasting code from these forums or some other howto site.

But do not ask me how to install anything that is archived on my desktop - like some dvb driver package I found somewhere in my search all bound up in a gzip.tar or some such name.  I can extract it...but then what?

It is frustrating being a newbie once again,

Cheers,

sorry only now i saw this post of yours...

so for the first question:
```
sudo aptitude install nautilus-open-terminal
```
will give a 'Open terminal' on your context menu (the one when you click with right button of mouse on desktop)

About you dvb driver package you can extract. If its for Linux (and a gzip file it should be) thats probably a source code to compile. There must be a README or INSTALL file inside with instructions. In most cases is C/C++ code with a make file. You will need a compile and the usual  commands for a makefile. Check first the instruction and if indeed it is the source code install the compiler with:
```
sudo aptitude install build-essential
```

---

### Post by zzirf on 2007-06-10
> **Rui Pais said:**
> Now, thats deep waters... 

Canon printer is famous for bad Linux support. Whats the model?


Now that's scary!

Canon PIXMA MP460

---

### Post by zzirf on 2007-06-10
> **Rui Pais said:**
> sorry only now i saw this post of yours...

so for the first question:
```
sudo aptitude install nautilus-open-terminal
```
will give a 'Open terminal' on your context menu (the one when you click with right button of mouse on desktop)

About you dvb driver package you can extract. If its for Linux (and a gzip file it should be) thats probably a source code to compile. There must be a README or INSTALL file inside with instructions. In most cases is C/C++ code with a make file. You will need a compile and the usual  commands for a makefile. Check first the instruction and if indeed it is the source code install the compiler with:
```
sudo aptitude install build-essential
```

Thanks for the info.  Unpacked there are two green listings ending in .sh and two blue ones which I assume are directories.  I have cd'ed into one of them and saw a makefile and so ran that code above and it sure did do something.  This is what it looks like:

```
jude@jude-desktop:~/Desktop/Installs/DVB-cjp-20041127.tar.gz_FILES$ ls
[COLOR="Lime"]DVB-Build.sh  DVB-Init.sh[/COLOR]  [COLOR="RoyalBlue"]dvb-kernel  video4linux[/COLOR]
```

Thanks also for the context menu for terminal.  I've run that but right now it is not available.  Maybe I need to reboot first but I am busy doing the other code for the mo.

---

### Post by Rui Pais on 2007-06-10
Hi, again.

The PIXMA series are one of the canon series famous for bad support under Linux :( Bad luck.

There are several ways to try (note try, no results granted at least for free)
- You can try to install one of the supported drivers, one by one, and see if some work. 
 To do this run:
```
gnome-cups-manager
```
and go for install and check what is available for PIXMA (On feisty there is a MP150 and MP500 and several PIXMAs IPxxxx, maybe you have luck with one of them. Note that  you should have Feisty, cause there are new models supported that are not available on edgy or dapper.

- You can try the latest Linux drivers, gutenprint, directly from cvs (the development source code) hard and eventually buggy (they are work in progress) there is no guarantee that your model works, at least i don't see you model listed, but i just checked on a run. [Here is the link]("http://gutenprint.sourceforge.net/p_Download.php3").

- There is a site, Canon Japan, that strangely offers some Linux packages.
 [Check here]("ftp://download.canon.jp/pub/driver") if you found some here that may be for your printer...

- And there are [commercial drivers]("http://www.turboprint.info"), that of course, are paid. I read they work fine but you need to pay (i read posts of people that prefer to sell they printers on ebay and buy it HPs or Epsons). Even if you don't mind to pay them, check fist they free trial to see if it works on your case.

Sorry, Canon has not been nice for Linux, and they refuse to give a decent support is plain stupidity. They are obstinately and conscientious loosing clients... haven't never understand why (Linux users smell? wrong colors of skin? wrong colors of screen? ) You may wan to drop them a mail with your opinion. Others are doing that in the hope that that mules change they mind...

Just as an extra, for scanner there are a parallel development.
[Check here]("http://home.arcor.de/wittawat/pixma/ubuntu-howto.html") for more info.

---

### Post by Rui Pais on 2007-06-10
> **zzirf said:**
> Thanks for the info.  Unpacked there are two green listings ending in .sh and two blue ones which I assume are directories.  I have cd'ed into one of them and saw a makefile and so ran that code above and it sure did do something.  This is what it looks like:

```
jude@jude-desktop:~/Desktop/Installs/DVB-cjp-20041127.tar.gz_FILES$ ls
[COLOR="Lime"]DVB-Build.sh  DVB-Init.sh[/COLOR]  [COLOR="RoyalBlue"]dvb-kernel  video4linux[/COLOR]
```

Ok, for this i advise you to check where you get that and see if they are really drivers for what you want.
I don't have or know such hardware, so i can't say much on that. A good thing to do is open a thread on this topic on [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=138") where users with that specific kind of knowledge can give you more and better help.

As a general info, that is a script install, and when run it must compile or copy pre-compiled binary modules (drivers) for the kernel modules folder and load them or so.
To run scripts you need to do:
sudo ./DVB-Build.sh 
and the outher should be to install initialize them... run the same way.
Again: 
YOU SHOULD HAVE CERTAIN OF WHAT THEY ARE! DON'T RUN THEM BLINDLY.
Ask advise on the correct section of forum. Google for you hardware and Linux installations. 


> 
Thanks also for the context menu for terminal.  I've run that but right now it is not available.  Maybe I need to reboot first but I am busy doing the other code for the mo.

No need to reboot, but you may need to logout gnome and login again to have it on the menu. 

Good luck. You have difficult hardware that will give you some hard work. You will need it.
Post for any doubt.

---

### Post by Rui Pais on 2007-06-10
Hi, me again.
Just find this thread right now on forum:
[Canon MP600 - Anyone get it working in Ubuntu]("http://ubuntuforums.org/showthread.php?t=456751")

You may be interested in read it. Maybe it can be used to MP460 too... Ask for help there too.
Here the page for your printer:
[http://canon.com.au/products/all_in_one_printers/all_in_one_printers/mp460_support.aspx](http://canon.com.au/products/all_in_one_printers/all_in_one_printers/mp460_support.aspx)

good luck

---

### Post by zzirf on 2007-06-10
> **Rui Pais said:**
> 
Again: 
YOU SHOULD HAVE CERTAIN OF WHAT THEY ARE! DON'T RUN THEM BLINDLY.
Ask advise on the correct section of forum. Google for you hardware and Linux installations. 


oh Rui now you got me worried,

I ran the code you first gave me already inside the directories so I guess it is too late.  So how do I uninstall that?  I have probably stuffed something up.  Is there such thing as system restore in ubuntu?

When it comes to ubuntu and linux I really have no idea what I am doing and I have noticed my cpu monitor thingy going up really high for no apparent reason.  

Thanks for the links and I will take your advice and go to the specialist areas on here.

My printer is listed in the add printer gismo but when it asks for the location of a pdd, I have no idea where to tell it to go.  What is a pdd?

Anyway, thanks for your help,

---

### Post by Rui Pais on 2007-06-11
> **zzirf said:**
> oh Rui now you got me worried,
:p
> 
I ran the code you first gave me already inside the directories so I guess it is too late.  So how do I uninstall that?  I have probably stuffed something up.  Is there such thing as system restore in ubuntu?

that should not be a problem. It was just a general warning, to avoid install random stuff from internet without knowing exactly what it dids. You can open the *.sh files with a text editor and check what it does (or past here if you don't understand bash... usually is easy to read it). It looks by the name they are just compile instructions for a module and for v4linux (that you should have already with ubuntu kernel). Some time those drivers for Linux are just the code for already installed or compile modules.

> 
When it comes to ubuntu and linux I really have no idea what I am doing and I have noticed my cpu monitor thingy going up really high for no apparent reason.  

Thanks for the links and I will take your advice and go to the specialist areas on here.

My printer is listed in the add printer gismo but when it asks for the location of a pdd, I have no idea where to tell it to go.  What is a pdd?
ppd is the configs for a specific printer. 
gnome-cups-manager deals with them "under the table"... if you have a sript ask for it you can either look for them on the install folder (if you get asked for them running some software installation) or search for some compatible under /usr/share/ppd/

Have you tried to install drivers for some model close to the one you own using gnome-cups-manager?

---

