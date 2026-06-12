---
title: "Hey all, Im new around here =)"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Valk01 on 2006-08-09
Hey all. Im new around this place and the linux community as a whole. A few people over at the ocforums suggested this distro for a firstimer and i thought i might head on over and sign up.

Im not new to computer systems. I work in a computer store as a systems builder and technical support person. I play with windows based pc's on a daily basis, which for now is alright. the only downside of course, getting cheap parts... having no money left.

I have been interested in linux for a while now. since i picked up a copy of debian for $5 at a book store on clearance. I have also tried Yopar *which i thought was pretty bloated* but i havent had a lot of experience with the nitty gritty details. command line ect.

So, im here to try out ubuntu and perhaps get a little direction from linux users on the best way to pick up on it.

So i guess first.. my system and hardware ill be using.

Athlon 64 3200+ @ 2660mhz
MSI K8NGM2-FID
1gb Corsair PC3200XLPT
250gb Seagate 7200.9 sata2
200gb Seagate 7200.7 ATA100
Asus 16X DVD
XFX 7600GS 256mb pci-e
Soundblaster Live! pci


2x Samsung 712N 17" Analog
1x Samsung 215TW 21" Widescreen Digital
1x Samsung 710N 17" Analog

Logitech MX1000 USB
Logitech Cordless Access USB
Wacom Graphire 2 USB

of the motherboard devices, i use the onboard 10/100/1000 lan and the onboard geforce 6150. all of this should be covered by nvidia drivers, so im not worried. any issues with other hardware though?


Basicly, what i use my pc for is general use. Internet apps, chat, playing back Media files *mostly video* Graphic design and photo retouching with my 7mp camera and light gaming.
All i play is final fantasy xi so im sure i can plug away at that..
I just want a system that just works... cleanly. there is nothing wrong with my windows install, i just wish I didnt have to babysit it as much and the only reason i really keep to windows is game support. Also, being in my own groove with software i prefer heh.

Im not above learning new tools though. The gimp is just as good as photoshop for basic editing, opencanvas is available for linux for drawing, and im sure there are messloads of media players and chat apps. of course firefox/thunderbird.

I would love love love any help i can get around here. Ive installed a few linux distros and used them for general use. I havent delve too far into the command line though. I ran into issues in yopar when i tried to mount a ntfs filesystem for media playback. Of course, i didnt even know i had to install codecs for music files heh. the directory structure is kind of intimidating too. ack. lets just assume im a complete noob.

So uhhh. nice to meet you guys =D hope we can have some fun. ill help out anyway i can =D

---

### Post by em3raldxiii on 2006-08-09
Yay!  I'm the first to reply {does a little dance} ...

Welcome!  That was a fantastic introduction to yourself - it's going to give the techies around here a fantastic idea about how to help you if you have any troubles.

You ask about the best way to get started.  Well, you've got a 64bit processor, so I'd be mighty tempted to go with the 64 bit Ubuntu, wouldn't you say?  Haha.  You can DL it and burn it or you can order it for free and they will send you the disc.

You mention the nvidia drivers, and yes they should work passably out of the box.  Be aware that you may want to look up other threads in this forum about nvidia drivers.  Also, read everything there is to read on Ubuntu.com and all of it's documentation.  Mind you, I didn't ... I just dove right in and it all worked fine for me so there you are.

There is also a thread on here specifically for mounting your NTFS drives with read/write support ... I'll see if I can find that one, but otherwise just do some searching.

*EDIT:  [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=NTFS+write+support](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=NTFS+write+support)*

Also, if you really want to have tons of fun, check out compriz + xgl.  They're experimental (and therefore likely a great learning exercise for you), but it's really worth a look.  turns your every-day desktop into a rotatable cube with workspaces on each side (among other things).

Finally, note that the Ubuntu install CD is "live" ... that is, you can fire it up without installing just to see if it's going to support your hardware directly out-of-the-box.  No more messing with 15 different driver discs in Windows.  Just install and go (for most things).

Any other troubles, post in the forums!

Cheers, and again, WELCOME!

[i]EDIT:  for command-line-interface or terminal matters, check out a little program called **yakuake**.  It was designed for KDE, as opposed to gnome (which is what Ubuntu comes with by default), but it works fine in Gnome.  I believe you may have to edit your repositories (ask if you don't know what that is) before you can get yakuake.  Likely, you will edit your repository within the first hour of using Ubuntu anyway ;) ... so you can get all the coolest software ;)

---

### Post by Valk01 on 2006-08-09
Im gonna go noob and assume that works kinda like windows registry.. keeping track of a bunch of useless information =D
Nah. i know its not windows, but for learning purposes, im gonna have to make parallals to windows and dos systems untill i get it heh. 
Im gonna ship that cd over to a pc with a burner *solves his storage problem with more and more harddrives* and try the livecd. Is there any software i should track down prior to installing though? is installing drivers once running similar to windows drivers?

also, that environment you suggested sounds pretty cool.. only problem is i run multiple dispalys. I only wish there was a way to make ffxi run T_T. it doesnt make sense to dual boot for it since im a bad boy and use a third party program to window the damn thing <_</

---

### Post by em3raldxiii on 2006-08-09
Heheh, well ... you *can* read about most of this stuff in the official documentation, but I'll get you up to speed on a few things.

"Repositories".  The folks who bring us Ubuntu have a number of servers that contain ALL of the software you need to get your computer fully up-to-snuff, including TONS of stuff that isn't included on a standard base installation.  Sure, the base install is great for basics, like surfing the internet, playing solitaire, writing resumes, and burning CDs.  But what about the more advanced stuff, like the Gimp?  Well, instead of trying to track it down, there are a couple of easy ways of installing it.  Easiest way is to use your command-line (we'll get to that).  Another way is to use Synaptic package manager (kinda like Windows Add-Remove programs only better).  These utilities will quickly search a database (which is updated on your computer) and determine where to get the file from, and more importantly what else is needed (like in windows you have all those stupid DLLs and other crap).  It will then automatically add all the "dependencies" so that the programs actually work.  The nice thing is that in Linux, every component can talk to every other component of your software, so there is no need for those stupid duplicates (such as what happens to your registry in Windows).  

Installing drivers is similar in some ways, but totally different in others.  For example, all of your basic and intermediate drivers are contained in the standard ubuntu repositories.  Now, if you want something exotic, you sometimes have to add different repositories to your list so that your computer has a larger database to search through.  Sometimes you have to get more creative - that's definitely a good reason to come here and search and ask.

You may consider getting the Kubuntu variant of Ubuntu if you are REALLY dependent on the way Windows works.  Kubunut and Ubuntu are exactly the same thing, except the graphical user interface is KDE instead of Gnome.  KDE looks a little more familiar to people when the migrate over to Linux because it is set up in a slightly more similar way to Windows.  Gnome, I am told, is somewhat more like a Mac - though I have never used a modern Mac so I don't really know.  The jury is still out as to which is faster/better, but it seems that more people suggest that Gnome is more efficient.  I personally use Gnome, though I am comfortable with both.

There are other flavors as well, such as xubuntu which uses Xfce - another graphical user interface that is very stripped down and uses few resources.  This is a great GUI for legacy computer systems and/or when you don't want ANY bloat.

All of these are available in the Ship-it part of Ubuntu.com (where you order the CDs for free).

If you have any troubles at all during the installation process, it would be a good idea to make a clear note of when and how the problems occurred.  Then you can come here to the forums to resolve any difficulties you've had.  Most people have no trouble at all ... just slap in the disc and go.  Make sure you have your internet cable plugged in because Ubuntu will make extensive use of it during certain parts of the install (to get you the latest "packages")

Have a clear idea of what you're going to want to do in Linux.  If you know you want to record and edit audio, for example, you may want to look up a program called Ardour.  If you want to burn CDs, one of the most popular programs is K3B.  All of these programs can be SUPER simply installed just by using the command-line or by using Synaptic package manager.

A word about command line.

Just about any "serious" changes that you will want to make will require the use of the "super-user".  Luckily, Ubuntu makes the installer's username the super-user so it minimizes fuss.  This is all in the name of security, and is part of the reason why Linux computers are virtually immune to viruses and other malware.  In Ubuntu, a super user command will always include the first four letters *sudo* followed by the command.  Here's an example:

```
sudo apt-get update
```
sudo means "super user do" followed by *apt-get* which is something you will become very familiar with as you install new packages, and *update* which is what you want apt-get to do (update the repository database on your computer relative to the repositories contents).

The first time you use *sudo* in your terminal, it will ask you for your password.  For a few minutes thereafter, that terminal will remember your password to minimize the pain-in-the-a$$ factor of entering it over and over.  Eventually you may be required to enter it again if you issue more sudo commands.

There ... that should get you a little further along .... please don't be afraid to ask questions, and by all means go read some documentation!  Haha ... kinda like looking at the assembly instructions after you've put the parts together wrong .... ;)

---

### Post by Valk01 on 2006-08-09
Thank you very much for the replies and the very useful information. 
I have to say, i already prefer gnome to kde *experience with yoper* its clean and to the point. I burned the cd across the room and tried the live cd feature. played around with it for a while. 
I was trying to configure the gdmsetup but i couldnt sudo because i couldnt find a password heh. all i wanted was to make my other monitors work.

I guess ill have to do a real install to fiddle with that though. im sure its real easy. thinking of gettinga  320gb 7200.10 anyway.
Would reading and memorizing the command list be of any benefit? or should i just do searches when i want to learn things as i need them? 
incidently, about having my network plugged in. When i ran the livecd, it wouldnt access my network at all. My motherboard is only a few months old, im not sure if this version of linux would support the nvlan on it. is this going to be an issue? can i download a package to a usb drive to update with when i install to get net?

And as i interprete the repository, it connects to a server to add to the list already ony my harddrive? then i can add/remove what i want when I want? Do you get a full list in the terminal? how do you install =D
god, im going to be really annoying. so sorry.

Incidently, I was reading through the pages here and saw a thead about that apt-get function and how it was the same as aptitude. what is that?

---

### Post by dusu on 2006-08-09
Hi Valk01, welcome to Ubuntu ! (it always feels so nice to have one more user ! :D )

> Thank you very much for the replies and the very useful information. 
I have to say, i already prefer gnome to kde *experience with yoper* its clean and to the point. I burned the cd across the room and tried the live cd feature. played around with it for a while. 
I was trying to configure the gdmsetup but i couldnt sudo because i couldnt find a password heh. all i wanted was to make my other monitors work.

When asking the password, just press enter ! that should do if I remember correctly.

> 
I guess ill have to do a real install to fiddle with that though. im sure its real easy. thinking of gettinga  320gb 7200.10 anyway.
Would reading and memorizing the command list be of any benefit? or should i just do searches when i want to learn things as i need them?

For the moment, you won't remember the command, but you'll remember them after using them for a while
(it's like music, once you've heard a song a few times, you just know it ;) )

>  
incidently, about having my network plugged in. When i ran the livecd, it wouldnt access my network at all. My motherboard is only a few months old, im not sure if this version of linux would support the nvlan on it. is this going to be an issue? can i download a package to a usb drive to update with when i install to get net?

And as i interprete the repository, it connects to a server to add to the list already ony my harddrive? then i can add/remove what i want when I want? Do you get a full list in the terminal? how do you install =D
god, im going to be really annoying. so sorry.

For this I'm of no help, but be sure someone will try to help you.
Don't worry about asking many questions. As long as you're nice, people will be glad to help you.
Also, don't hesitate to have a look at the wiki [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/), where many questions are already answered.
It's always better to find the answer on ones own anyway, because one learns better :)

> 
Incidently, I was reading through the pages here and saw a thead about that apt-get function and how it was the same as aptitude. what is that?

aptitude and apt-get allow you to install/remove packages (programs if you want).
For example, if you want to install the pdf viewer called xpdf, type the following command in a terminal :
```
sudo apt-get install xpdf
```

Well as said, you'll find lots of information in the wiki, so why not start looking at it now ?
About aptitude, here's what I found : [https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)

I'm sure there's much more to be found in the wiki though...

Once again, welcome to the Ubuntu world !

---

### Post by petersjm on 2006-08-09
> KDE looks a little more familiar to people when the migrate over to Linux because it is set up in a slightly more similar way to Windows. Gnome, I am told, is somewhat more like a Mac

Um, shouldn't that be the other way around? Gnome is more like Windows and KDE more like Mac (if you want to use those comparisons) - at least as far as I understand it...

Gnome (Ubuntu) has what in Windows is called the Start menu - in Gnome it's called "Applications" which makes a heck of a lot more sense). KDE (Kubuntu) does not.

Or am I wrong? Maybe I'm going mad...! :p

---

### Post by 3rdalbum on 2006-08-09
> **petersjm said:**
> Um, shouldn't that be the other way around? Gnome is more like Windows and KDE more like Mac (if you want to use those comparisons) - at least as far as I understand it...

Gnome (Ubuntu) has what in Windows is called the Start menu - in Gnome it's called "Applications" which makes a heck of a lot more sense). KDE (Kubuntu) does not.

Or am I wrong? Maybe I'm going mad...! :p

Maybe you are! KDE has the "K menu" which performs the same function as the Start menu, and it's in the same part of the screen. KDE has the quickstart bit in its panel, which is just like the IE and Office icons you get in the Windows taskbar.

Gnome has the top panel which looks a bit like the Mac, and the Gnome applications menu is in the same place as the Apple menu in MacOS (but in this way it's more like OS 9 than OS X).

Also, in KDE you "safely remove hardware" then specify what you want to remove. In Gnome, you specify what you want to remove, then "unmount" or "eject" it - much more like the Mac.

However, KDE has a Mac OS behaviour setting, where the topmost KDE program puts its menubar in a panel at the top of the screen. But this only works with KDE programs unfortunately.

---

### Post by petersjm on 2006-08-09
> **3rdalbum said:**
> Maybe you are!

Obviously! :p I stand corrected (my excuse is I've never used KDE and thought of the Gnome panel in relation to Windows...) That'll teach me! Heh

---

### Post by em3raldxiii on 2006-08-09
LOL well they're all movable anyway, so you can make your Gnome Applications menu show up at the bottom if you want.  Or the sides.  So ... yeah ... whatever ... hehe :D

Just a brief clarification, you can use Aptitude in almost exactly the same way as apt-get, but it does a few things slightly better.  I am told that using aptitude is better for some reason, though I haven't taken the time to figure out why yet.  I starte out using apt-get many moons ago and developed the habit.

```
sudo apt-get install yakuake

does roughly the same as

sudo aptitude install yakuake
```

And as far as commands go, nah, don't go crazy about that just yet because it won't be apparent which ones are the more important ones to use.  One of the things you can do for more information about particular commands is this:

```
man -k <command>

OR

<command> --help
```
This will output some potentially helpful information.  At first, many of these "help" pages might just serve to further confuse you - I know *I* got more confused a few times.  So if this happens to you, just come on by the forums here and ask away.

As far as the network connection goes, if your motherboard is already a month or two old, you probably won't have any troubles getting it to work right out of the box.  The live CD has a few limitations in that it's doing everything directly from the CD and from your RAM.  It doesn't even acknowledge the existance of your harddrives for all intents and purposes.  Once you are doing a complete install, it should recognize your network adapter right away.  Plus, I don't think nVidia has changed their network hardware in quite some time.

---

### Post by petersjm on 2006-08-11
> **em3raldxiii said:**
> I am told that using aptitude is better for some reason, though I haven't taken the time to figure out why yet.

I believe it's because aptitude will (attempt to) auto-install all dependancies and will also (attempt to) remove all installed dependancies when you uninstall the app, rather than just the app... :D

---

### Post by djsroknrol on 2006-08-11
Welcome to our community Valk01..I'm sure you'll fine great help anytime you need it here in the forums..

Your setup sounds great and good to go...

Aptitude is a better way to do it, unless you go GUI, then Synaptic is the only way to go..it's very powerful. 

If you're going apt-get, use "&&" if possible to sort of "fail-safe" an install of a package and fend off possible breakage..

---

