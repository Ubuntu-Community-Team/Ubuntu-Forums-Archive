---
title: "My questions ..."
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by andrikas on 2008-03-01
So, I'm a total beginner, just installed ubuntu a few minutes ago ..
Now, these are my questions ..

[LIST=1]
[*]Do I need to install drivers ( Monitor, Intel desktop smthn etc ) And if I do, how ?
[*]How to install programs ?? Such as Razer diamondback driver, Adobe photoshop, avg antivirus, counter strike source, iTunes, nero, soulseek, skype, msn, winamp, flashget etc ?
[*]As I asked in my previos question, how can I install my razer diamondback ?
[*]And the third one that goes for the 2 ones above, how the hell do I install stuff ?
[*]Why cant i make the @ sign ? I have to copy it from someone elses e-mail :/ annoying.
[/LIST]

---

### Post by Victormd on 2008-03-01
Gonna try to answer a few of your questions...
1) Drivers - yes. Even though Ubuntu recognizes most of your hardware, some drivers such as video card, wireless are not readilly available and you have to install restricted drivers to get full functionality.
2) Windows programs don't run on linux and you can't install EXE files UNLESS you use a piece of software called WINE that allowes you to run windows based programs. However, not all of them will work.
AVG antivirus... you don't need an antivirus for Linux!
Photoshop - you can install using WINE but might want to try Gimp as an alternative
skype - [www.skype.com](www.skype.com) and download the linux version
msn - try the alternatives amsn and pidgin
soulseek - haven't tried to use with ubuntu - I use bit torrent (installed by default)
razer diamondback driver - don't know
counter strike - I think it works with WINE
winamp - there are alternatives for ubuntu, such as rythm box but if you must have winamp, use WINE.

Ok... now what's wine? visit [www.winehq.org](www.winehq.org) to learn more about it and what programs will work with it.

How to install? go to System>Administration>Synaptics Package Manager
there you can search for programs to install and since everything is open source, all you need is an active internet connection.
As for the @ sign... try going to System>Preferences>Keyboard and play around with the settings.

Hope these help you get started... and welcome to Ubuntu

---

### Post by herbster on 2008-03-01
Make use of the search function of these forums. Many common questions such as yours have been answered numerous times.

The programs you mention don't all work on linux because they are mostly Windows-based. You would be looking for equivalents of many of them, for example Photoshop's linux equivalent would be Gimp, which comes installed with Ubuntu.

You install programs in Ubuntu using the apt-get functionality:

```
sudo apt-get install programname
```

Alternatively you can click Applications > Add/Remove and find programs there just the same.

As for drivers, it depends on your hardware. Most hardware works out of the box, but things like Nvidia graphics cards need the Nvidia drivers and it's simple, again, use the search function and also, the [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) page has lots of good stuff for beginners.

---

### Post by justin whitaker on 2008-03-01
> **andrikas said:**
> So, I'm a total beginner, just installed ubuntu a few minutes ago ..
Now, these are my questions ..

[LIST=1]
[*]Do I need to install drivers ( Monitor, Intel desktop smthn etc ) And if I do, how ?
[*]How to install programs ?? Such as Razer diamondback driver, Adobe photoshop, avg antivirus, counter strike source, iTunes, nero, soulseek, skype, msn, winamp, flashget etc ?
[*]As I asked in my previos question, how can I install my razer diamondback ?
[*]And the third one that goes for the 2 ones above, how the hell do I install stuff ?
[*]Why cant i make the @ sign ? I have to copy it from someone elses e-mail :/ annoying.
[/LIST]

This might be a case where you should stay on XP. 

Most of the programs you ask for can be made to run via WINE, but it's hit or miss. Mainly, people switch to open source alternatives (Gimp instead of Photoshop, or K3B instead of Nero).

Photoshop can run on Crossover Office or WINE-I'm not sure which versions are supported, but I bet you can get a better sense at winehq.org. 

You don't need an antivirus on Linux, although whether you should use one is up for debate. 

Steam can be made to run on WINE with a bit of futzing, and on Crossover with less. 

Nero? There is a Linux version that you can download for free if you have a valid Nero Windows license, and there are about 1000 alternatives on Linux. 

Skype runs on linux. 

MSN can be used via amsn, pidgin, and others...not sure what features you need, but basic chat is well covered. 

There are several winamp clones on Linux...you probably want to look at Amarok, Rhythmbox, Banshee, and some others since you are interested in iTunes.

iTunes supposedly can run on WINE, but it takes some work, and it does not support every feature (cd writing is out, for example). 

Other than the Razer, which I have no experience with, there are alternatives...but if you really have to have all of those things, you might want to stay with XP. 

There is a popular refrain that linux is not windows: it takes some effort, and some of the things that you are used to are either not available, or are done a different way.

---

### Post by PeterJS on 2008-03-01
> **andrikas said:**
> So, I'm a total beginner, just installed ubuntu a few minutes ago ..
Now, these are my questions ..


*Do I need to install drivers ( Monitor, Intel desktop smthn etc ) And if I do, how ?

The vast majority of drivers are Open and can be built directly into the kernel itself so you won't need to look for extra drivers. The exceptions to this are ATI and Nvidia graphics drivers, and wireless card drivers (except for Intel cards which are built int). All of the drivers that aren't built in can be installed with the restricted drivers manager if they are needed.
> 
*How to install programs ?? Such as Razer diamondback driver, Adobe photoshop, avg antivirus, counter strike source, iTunes, nero, soulseek, skype, msn, winamp, flashget etc ?

Those are (mostly) windows only software, and won't run directly. The are are programs that can do the same thing. Anti-virus isn't needed because Ubuntu has a real permissions and security system paired with the fact there are no know viruses in the wild. As for games there is a project called wine for running windows software under Ubuntu. It works some of the time. I can tell you from personal experience that steam and source run very well. You can see the application listing for other programs:
[http://appdb.winehq.org/](http://appdb.winehq.org/)
> 
*As I asked in my previos question, how can I install my razer diamondback ?

Have never heard of this particular device I couldn't tell you, what is it?
> 
*And the third one that goes for the 2 ones above, how the hell do I install stuff ?

Most software is installed through the package management system. There are several interfaces to APT, there is Add/Remove Programs in the application menu, Synaptic package manager in System > Administration, and on the command line there is apt and aptitude.
> 
*Why cant i make the @ sign ? I have to copy it from someone elses e-mail :/ annoying.


Depends on you keyboard layout, but every keyboard I've even seen it's shift+2

---

### Post by andrikas on 2008-03-02
> **PeterJS said:**
> The vast majority of drivers are Open and can be built directly into the kernel itself so you won't need to look for extra drivers. The exceptions to this are ATI and Nvidia graphics drivers, and wireless card drivers (except for Intel cards which are built int). All of the drivers that aren't built in can be installed with the restricted drivers manager if they are needed.

Those are (mostly) windows only software, and won't run directly. The are are programs that can do the same thing. Anti-virus isn't needed because Ubuntu has a real permissions and security system paired with the fact there are no know viruses in the wild. As for games there is a project called wine for running windows software under Ubuntu. It works some of the time. I can tell you from personal experience that steam and source run very well. You can see the application listing for other programs:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Have never heard of this particular device I couldn't tell you, what is it?

Most software is installed through the package management system. There are several interfaces to APT, there is Add/Remove Programs in the application menu, Synaptic package manager in System > Administration, and on the command line there is apt and aptitude.


Depends on you keyboard layout, but every keyboard I've even seen it's shift+2

A razer diamondback is a gaming mouse, needs its own software.

---

### Post by billgoldberg on 2008-03-02
Dump the windows programs and use linux programs.

Most are better anyway.

For soulseek, there is nicotine+ you can use. It's basicly soulseek for linux.

Just go to "applications -> add/remove", make sure the box on the right says "all available applications" and search for "nicotine".

[[img]http://xs125.xs.to/xs125/08090/nicotine500.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs125&d=08090&f=nicotine500.png)

---

