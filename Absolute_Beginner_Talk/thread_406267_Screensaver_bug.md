---
title: "Screensaver bug???"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-04-10
It's my second day using Xubuntu. With the help of several members here, I managed to activate the sound, and now I have system sounds and can listem to MP3 on cd.


In this second day I found a problem while trying to configure the screensaver. Don't know if it's a bug, or if I'm doing something wrong.

In the screensaver config panel, I tried several screensavers.. There is a small window wich previews the screensaver. While browsing through the savers, I came across one called "Molecule". When i tried to preview it, the computer seemed not to respond anynore. The mouse pointer moved, but I couldn't do anything else. The computer sort of freezed out. I has the restart the system using the switch on the PC case.
It restart fine, but when I leave to computer for 10 minutes, the screensaver activates and it freezes again. One phrase on screen: "Building molecules". I wave waited more than an hour for the molecules to build, but simply nothing happens.

It seems to be a bug in the screensaver, or an installation problem. Since it takes some time to re-install, I was hopping that there's a way of disabling the screen saver on the terminal.

Can anyone give me an hint?

Thank you!

---

### Post by Ganda_Melga on 2007-04-10
Anyone? Please?

---

### Post by Ganda_Melga on 2007-04-11
What a shame. I was really liking Xubuntu. But an OS that freezes the computer just doesn't cut it.

I guess it's back to Windows.... :( 


Thanks for all your help.

---

### Post by silverglade00 on 2007-04-11
Go back into the screen saver settings and switch it to a different one. There could be something wrong with that one or most likely it needs 3D acceleration that has not been set up yet. No need to run back to Windows yet over a screen saver. I understand your frustration at not getting any help for a few hours. Sometimes it takes a while for people to answer on here. Everyone who is here to help out does so on a volunteer basis. For example, I work in a college computer lab. Basically, I babysit printers all day and reset passwords when students need it. After I finish my homework, I come on here and see if there are any questions that I can help with.  I am not paid by Ubuntu in any way, except for them letting me use their OS for free. 

Anyway, try a different screen saver and see if that helps any. If it does, then we either need to get your 3D going or maybe you did indeed find a buggy screensaver. :)

---

### Post by Ganda_Melga on 2007-04-11
> **silverglade00 said:**
> Go back into the screen saver settings and switch it to a different one. There could be something wrong with that one or most likely it needs 3D acceleration that has not been set up yet. No need to run back to Windows yet over a screen saver. I understand your frustration at not getting any help for a few hours. Sometimes it takes a while for people to answer on here. Everyone who is here to help out does so on a volunteer basis. For example, I work in a college computer lab. Basically, I babysit printers all day and reset passwords when students need it. After I finish my homework, I come on here and see if there are any questions that I can help with.  I am not paid by Ubuntu in any way, except for them letting me use their OS for free. 

Anyway, try a different screen saver and see if that helps any. If it does, then we either need to get your 3D going or maybe you did indeed find a buggy screensaver. :)


I apologise if I was incorrect, too much work, I'm just too tired.

I cannot try another screensaver. Every time I go back to choose another screensaver, the preview enters and freezes the computer again. So I can't really choose another, unless it's possible to do so in a terminal window.

Since I don't know anything about the terminal, I can't even figure out what to type....

---

### Post by Ganda_Melga on 2007-04-11
> **silverglade00 said:**
> Go back into the screen saver settings and switch it to a different one. There could be something wrong with that one or most likely **[COLOR="Red"]it needs 3D acceleration that has not been set up yet[/COLOR]**. No need to run back to Windows yet over a screen saver. I understand your frustration at not getting any help for a few hours. Sometimes it takes a while for people to answer on here. Everyone who is here to help out does so on a volunteer basis. For example, I work in a college computer lab. Basically, I babysit printers all day and reset passwords when students need it. After I finish my homework, I come on here and see if there are any questions that I can help with.  I am not paid by Ubuntu in any way, except for them letting me use their OS for free. 

Anyway, try a different screen saver and see if that helps any. If it does, then we either need to get your 3D going or maybe you did indeed find a buggy screensaver. :)


Errr....how do I do that? :confused:

---

### Post by silverglade00 on 2007-04-11
You are doing fine. I just wanted to encourage you to stick with it. I know how frustrating it can be the first time. I have problems all the time too. Just yesterday, I finally got my wireless working at my school. I had to break the networking software to do it. Yep, I fixed it by breaking it. :)

I am not sure how to change your screen saver. Hopefully someone else can help with this. Hopefully, if we can get your 3D drivers in, it will let the preview work without crashing so you can change it.

As for 3D, it depends on which video card you have. Do you have Nvidia or ATI or maybe built in Intel graphics? If you can tell that, we can get started. If you need help finding out let me know.

---

### Post by silverglade00 on 2007-04-11
Ok, you might be able to get rid of the screen saver by trying this:

```
rm -rf ~/.xscreensaver
```

I'm installing XFCE so hopefully I can help you out a little better.

---

### Post by Ganda_Melga on 2007-04-11
> **silverglade00 said:**
> You are doing fine. I just wanted to encourage you to stick with it. I know how frustrating it can be the first time. I have problems all the time too. Just yesterday, I finally got my wireless working at my school. I had to break the networking software to do it. Yep, I fixed it by breaking it. :)

I am not sure how to change your screen saver. Hopefully someone else can help with this. Hopefully, if we can get your 3D drivers in, it will let the preview work without crashing so you can change it.

As for 3D, it depends on which video card you have. Do you have Nvidia or ATI or maybe built in Intel graphics? If you can tell that, we can get started. If you need help finding out let me know.


Ok...the graphics card... 

By typing LSPCI in the terminal I got this result as far as the graphics card is concerned:

VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

The memory size of the card is 32 Meg. 

This is an old computer, a friend of my mine gave it to me because it didn't worked anymore . Its a very very basic and old computer. I replaced the power source and now it's running ok. The computer only had 64K of memory, so I upgraded to 192K in order to run Xubuntu. The graphics card was a PCI graphics card with 2 meg memory. So I bought this ATI with 32 meg, to give a little more breathing space. 

Then for the OS... I have a copy of windows 98 (original), but it seemed too primitive. So I decided to try Lunix. A friend of mine recommended BSD. I tried several live CDs (NetBSD, Gentoo, Xubuntu, Fluxbuntu, Kurumin) The one that felt right for me was Xubuntu. So i went and tried it out. I'm still trying it, theres lots of things wich I don't know how to do. Even basics things are a bit of a mystery to me. I dont know how to add shortcuts, don't know how to install the CLAM anti-virus wich I already downloaded, don't know how to place GAIM in the upper menu bar, etc...
But in time I will get there (I hope)

The funny thing is I have xubuntu installed for 2 or 3 days, but I'm getting addicted to it. I almost don't switch on the main computer, and spend all my spare time in this relic of a computer, trying to figure out how to work with xubuntu.

Anyway...

Sorry about all this verbosity. :)

---

### Post by silverglade00 on 2007-04-11
Looking at the molecule screensaver, it definitely needs a 3D video card driver installed.

For now, you can either do the rm command I gave earlier, or you can open that file

```

cd ~
cp .xscreensaver .xscreensaver.original
mousepad .xscreensaver

```

Go down to the line that says GL molecule -root -shells and put a minus sign as the first character. That will disable the molecule screensaver and I believe remove it from the list. You should do this for all of the entries that begin with GL for now. They all require a 3D driver and might do the same thing that molecule did.

Once your 3D is working, you can change it back by typing
```

cp .xscreensaver.original .xscreensaver

```

Now we just need to figure out your video card...

---

### Post by Ganda_Melga on 2007-04-11
> **silverglade00 said:**
> Ok, you might be able to get rid of the screen saver by trying this:

```
rm -rf ~/.xscreensaver
```

I'm installing XFCE so hopefully I can help you out a little better.


Great! It did the job. It reseted the screensaver to the original definitions. Now I can choose another one!

Is there any site where I can learn these commands? Or must I have to buy books about linux?

Once again I apologise, because of my faulty English. There had been many years since I did not write in English (and it shows), since the times of the Commodore Amiga. 

Note: I installed the Xubuntu in my native language (Portuguese). but the menus are a bit of a mix between Portuguese and English. Anyway, that doesn't bother me.


I appreciate the time and effort you took to help me. :) 


Thank you so much!

---

### Post by Ganda_Melga on 2007-04-11
Oh yes.... the 3d on the graphics card.... whenever you have the time. ;)

---

### Post by silverglade00 on 2007-04-11
Ok, after a little research, and your video card specs, it seems that getting 3D drivers working on that card is a pain in the butt and probably won't let you run the 3D screensavers anyway. That doesn't seem right to me because I used to have that same card and it would run Quake 2 just fine. I think it's mostly because it is such an old card that the drivers from ATI don't support it anymore.

So it seems that editing the .xscreensaver file and adding a - in front of all the GL lines is the way to go until you can find instructions here for getting 3D acceleration working on that card. Be sure to put a minus sign and space before the GL like:
- GL    <--- like this
-GL      <--- not like this

As for links and Gaim, what you want is called a launcher. RIght click the desktop and pick add launcher. Fill in the blanks and you will have a link to an application. Other links are drag and drop easy. To add Gaim, rightclick on the bar and choose add new item. You want the very first one, Launcher. In the box that pops up, give it the name Gaim and put gaim in the command line.

I agree that it is very fun exploring this new OS. Your new best friend will probably be Applications Menu -> System -> Add/Remove. Open that, type clam into the search box and soon you will see Virus Scanner in the result. That's clamav. You don't need to go from site to site anymore looking for programs like you did in Windows. Things run different in the Linux world, as you have found out. All the programs you need can be found in that Add/Remove program. Just check the ones you want and click ok and it will install them for you. Even better, you don't have to find upgrades either! Just run Applications -> System -> Update Manager once a day and it will tell you the available upgrades for your Xubuntu system AND all the programs.

I just realized that I do not know which version you have, so the locations of things in the menu may be different. I have done a lot of customizing to my system, basically making it Ubuntu/Kubuntu/Xubuntu all in one, so some of the things might not be there. If they aren't, just look in the add/remove programs for it.

---

### Post by silverglade00 on 2007-04-11
Great, I'm glad it worked. Stick with it and I know you will enjoy it! 

It takes a while to learn the commands, but I find that it helps to keep a notebook by my computer and write stuff down. Soon I don't have to look at the book to remember the command anymore.

---

### Post by silverglade00 on 2007-04-11
There are a lot of places online to read about the command line. I picked up most of my knowledge just from reading the forums for Ubuntu and PCLinuxOS, which is my favorite Linux. 
[URL="http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=224"]
The Linux Tutorial[/URL] is a good place to start reading about the commands.

---

### Post by Ganda_Melga on 2007-04-11
> **silverglade00 said:**
> Ok, after a little research, and your video card specs, it seems that getting 3D drivers working on that card is a pain in the butt and probably won't let you run the 3D screensavers anyway. That doesn't seem right to me because I used to have that same card and it would run Quake 2 just fine. I think it's mostly because it is such an old card that the drivers from ATI don't support it anymore.

So it seems that editing the .xscreensaver file and adding a - in front of all the GL lines is the way to go until you can find instructions here for getting 3D acceleration working on that card. Be sure to put a minus sign and space before the GL like:
- GL    <--- like this
-GL      <--- not like this

As for links and Gaim, what you want is called a launcher. RIght click the desktop and pick add launcher. Fill in the blanks and you will have a link to an application. Other links are drag and drop easy. To add Gaim, rightclick on the bar and choose add new item. You want the very first one, Launcher. In the box that pops up, give it the name Gaim and put gaim in the command line.

I agree that it is very fun exploring this new OS. Your new best friend will probably be Applications Menu -> System -> Add/Remove. **[COLOR="Red"]Open that, type clam into the search box and soon you will see Virus Scanner in the result.[/COLOR]** That's clamav. You don't need to go from site to site anymore looking for programs like you did in Windows. Things run different in the Linux world, as you have found out. All the programs you need can be found in that Add/Remove program. Just check the ones you want and click ok and it will install them for you. Even better, you don't have to find upgrades either! Just run Applications -> System -> Update Manager once a day and it will tell you the available upgrades for your Xubuntu system AND all the programs.

I just realized that I do not know which version you have, so the locations of things in the menu may be different. I have done a lot of customizing to my system, basically making it Ubuntu/Kubuntu/Xubuntu all in one, so some of the things might not be there. If they aren't, just look in the add/remove programs for it.


Negative. It says: There is no matching application available.

---

### Post by silverglade00 on 2007-04-12
You need to enable the extra software repositories. [This tutorial tells you how]("http://psychocats.net/ubuntu/sources"). That is a great site to tell you all about working with Ubuntu. Be careful when following directions from there. They give directions for Dapper and Edgy. Be sure you are following the correct instructions. After you do the things on that page ( be sure to do the update command after the large code chunks), you will be able to find clam in the Add/Remove programs along with a ton more other programs.

[Another great place to learn how to do stuff in Ubuntu.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

---

### Post by Apollo17 on 2007-04-12
Hey there,

Silverglade00 knows a lot more about this than I do, but I had the same problem (yes, with Molecules too, and with the same apparent basic video card - mine is a ATI Rage Fury Pro which shows up in the list the same as Ganda's) and I wanted to share the fix I found searching the forums:

You can use gconf-editor by typing that in the terminal.
The screensaver settings are under: apps > gnome-screensaver

Go to Themes and remove the offending one and change it to one that didn't lock up your system, or change the "mode" from "single". That worked for me. And now I'm careful to just not load any of the screensavers requiring 3D. 

I had tried to enable 3D by typing some gl commands recommended at some help sites, but they didn't seem to work with this card for some reason. So be careful if you try enabling 3D, and then trying out say Molecules again, or you might encounter the same lock ups.

Perhaps Silverglade00 can find a fix to correctly enable 3D on this card. That would be great. I'm wanting to try Beryl, but knowing that these ATI cards have a bad reputation working in 3D on Linux makes me leery as I've read about other systems getting pretty hosed by trying it.

Funny thing (sort of) is that at this point, all the people who've moved to Vista on PC's are having the opposite problem: Nvidia has been slow to write decent drivers for it, but ATI has done well. Strange world indeed.

Good luck,

Ross Warren
North Carolina

---

### Post by Ganda_Melga on 2007-04-12
> **silverglade00 said:**
> You need to enable the extra software repositories. [This tutorial tells you how]("http://psychocats.net/ubuntu/sources"). That is a great site to tell you all about working with Ubuntu. Be careful when following directions from there. They give directions for Dapper and Edgy. Be sure you are following the correct instructions. After you do the things on that page ( be sure to do the update command after the large code chunks), you will be able to find clam in the Add/Remove programs along with a ton more other programs.

[Another great place to learn how to do stuff in Ubuntu.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")


Well, I must be a little obtuse, for I continue not to find clam, after the tutorial. Nor Opera. Where did I go wrong? I did exactly what's on the tutorial.

In the terminal typed:

sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo mousepad /etc/apt/sources.list

Then in the empty file I pasted the instructions:

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main 


Then saved the file.

Then in the terminal typed:


sudo aptitude update


Still no luck....


I didn't understood one part though...


[COLOR="Red"]**## Uncomment the following two lines to fetch updated software from the network**[/COLOR]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

[COLOR="Red"][B]## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.[/B][/COLOR]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted



What is "Uncomment"? Is there something in the lines that I should have deleted, or modified?

---

### Post by Ganda_Melga on 2007-04-14
Anybody can help me with this issue of installing apllications? Clam and others?

Thank you.

---

### Post by Ganda_Melga on 2007-04-18
Still waiting for some kind soul to tell me how to install programs. Clam, or another good anti-virus....


:popcorn:

---

### Post by kurtstricker on 2007-05-06
> **silverglade00 said:**
> Ok, you might be able to get rid of the screen saver by trying this:

```
rm -rf ~/.xscreensaver
```

I'm installing XFCE so hopefully I can help you out a little better.

I tried this and it didn't work.  I'm running root terminal and copying code as is.  Any ideas?

---

### Post by kurtstricker on 2007-05-07
> **silverglade00 said:**
> Looking at the molecule screensaver, it definitely needs a 3D video card driver installed.

For now, you can either do the rm command I gave earlier, or you can open that file

```

cd ~
cp .xscreensaver .xscreensaver.original
mousepad .xscreensaver

```

Go down to the line that says GL molecule -root -shells and put a minus sign as the first character. That will disable the molecule screensaver and I believe remove it from the list. You should do this for all of the entries that begin with GL for now. They all require a 3D driver and might do the same thing that molecule did.

Once your 3D is working, you can change it back by typing
```

cp .xscreensaver.original .xscreensaver

```

Now we just need to figure out your video card...

I get this:

"kim@kim-desktop:~$ cp .xscreensaver .xscreensaver.original cp: cannot stat `.xscreensaver': No such file or directory"

when I try to fix this problem. Help?:(

---

### Post by Ganda_Melga on 2007-05-08
> **kurtstricker said:**
> I get this:

"kim@kim-desktop:~$ cp .xscreensaver .xscreensaver.original cp: cannot stat `.xscreensaver': No such file or directory"

when I try to fix this problem. Help?:(

I haven't  a clue. It worked for me.  Do you have the same problem I did? The molecule screensaver feeezes  the system?

---

### Post by kurtstricker on 2007-05-09
I have the exact same problem.  I can't change the screen saver because the preview freezes the OS and after 10 minutes of inactivity it also freezes.  It is set to the Molecules screen saver which turns the screen back and reads "constructing molecules" and freezes...this is bad guys.

I tried both command suggested:, the one above to copy off the settings and this one: 

rm -rf ~/.xscreensaver

Should I be doing this in Root Terminal?  This does nothing, no reply when entered.

---

### Post by Ganda_Melga on 2007-05-09
> **kurtstricker said:**
> I have the exact same problem.  I can't change the screen saver because the preview freezes the OS and after 10 minutes of inactivity it also freezes.  It is set to the Molecules screen saver which turns the screen back and reads "constructing molecules" and freezes...this is bad guys.

I tried both command suggested:, the one above to copy off the settings and this one: 

rm -rf ~/.xscreensaver

Should I be doing this in Root Terminal?  This does nothing, no reply when entered.


I can't remember exactly how I dit it. Did you try the sudo command? Like:

sudo rm -rf ~/.xscreensaver


Maybe I'll freeze my system again, justo to find out how to unfreeze it again. Anyway, try using the sudo.

---

### Post by A*p on 2007-06-16
> Still waiting for some kind soul to tell me how to install programs. Clam, or another good anti-virus....

Do you need an anti virus program? or is it just the scars of windows conditioning.  Linux does not suffer from the same ills that the Microsoft offering does.

Only time I have used a virus scanner in linux was on a file server and it was for scanning for windows viruses. 

You should be able to fid ClamAV in the universe repositories I think.

---

### Post by A*p on 2007-06-21
Workaround to this screensaver bug is here

[http://ubuntuforums.org/showthread.php?t=479520](http://ubuntuforums.org/showthread.php?t=479520)

---

### Post by wkulecz on 2007-08-02
Disable the screensaver, all of them.  6.06 and now 7.04 lock up if the screensaver is left running overnight.  I'm using Nvidia 5500 and 6200 series video cards with the proprietary Nvidia drivers.

Our 6.06 systems are rock stable once the screensaver and powersaving were disabled.  Seems no improvement in 7.04.

To install/remove software, go to the menu: System->Administration->Synaptic
and type your password in the box that pops up.   Find what you want and click the box and choose "Mark for Install" for what you wnat.  Then click apply and it'll download and install what you want.

If the  software is not in the listings (use the search) IMHO forget about it as a begineer unless you've a local guru to help or near infinite time and serious motivation to learn.

--wally.

---

### Post by aperomsik on 2007-08-29
I have a similar video card as the original poster, Rage128-related, and a similar problem. The strange thing is, most of the GL screensavers work just fine once I added "Load GLCore" in xorg.conf. But molecule still freezes X. (I can still ssh to the machine and restart the X server.) Seems that there is a specific bug related to molecule itself.

---

### Post by headcronie on 2007-10-23
Just upgraded to Xubuntu 7.10 (Gutsy) and now we can't select which screen savers we want, unless we pick one specific one.  The Molecule screen saver is a sure crash.  

How do we go about disabling this specific one, so that we can leave it on random?

I'm relieved to know that there are others out there with this video card and having the same problems.  I am not alone... :)

---

