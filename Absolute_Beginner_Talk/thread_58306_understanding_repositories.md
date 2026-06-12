---
title: "understanding repositories"
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-08-19
Hi, I tried to install mplayer but before I get to that, can anyone tell me what repositories are?  Also, is xine a better media player than mplayer?  If so why?

---

### Post by Kvark on 2005-08-19
I don't know the official definition of what a repository is. But what it means to a user is "add all repositories that you trust (usually the ones ubuntuguide.org mentions) to your sources.list file and then just click away in synaptic to install programs". The good thing about it (besides that synaptic is the easiest way around to install programs) is that you don't have to search for program downloads on random websites or filesharers, instead you get the programs from central sources/repositories that you trust.

Edit: almost forgot about music players, not sure which one is 'best' but... all players suck without the codecs (the package called w32codecs in synaptic) but with the codecs even totem (with the totem-xine package added, NOT totem-gstreamer) works.

---

### Post by Brunellus on 2005-08-19
[QUOTE=racermike1967]Hi, I tried to install mplayer but before I get to that, can anyone tell me what repositories are?  Also, is xine a better media player than mplayer?  If so why?[/QUOTE]
 1) [www.ubuntuguide.com](www.ubuntuguide.com)

2) A "repository" is just like it sounds:  a place where various software packages are stored.  When you add them to /etc/apt/sources.list you instruct apt and synaptic (the package-managers, or installer programs, if you like) to search through those repositories for the program that you like

The old multimedia howto that advises you to compile mplayer from source is deprecated, and should not be used.  Open synaptic, go to 'repositories,' enable 'universe' and 'multiverse,' and install mplayer from there.

Again, you will also be looking for the W32 codecs.  read the relevant section on ubuntuguide.

---

### Post by poofyhairguy on 2005-08-19
[QUOTE=racermike1967]Hi, I tried to install mplayer but before I get to that, can anyone tell me what repositories are?  Also, is xine a better media player than mplayer?  If so why?[/QUOTE]

In Windows you get your software from boxes sold at the store (and other ways....but lets just use one please for the example). To get software, you pay for it, take it home and install it. Each "package" of software holds a different program that is used by Windows. The store in this case is the "repository" and the clerk is the "pacakge manager" (lets you get software pacakges).

In Ubuntu the store is Synaptic. Synaptic holds each pacakge and gives it to you for the cost of the download. The server where Synpatic connects to and gets the software is called a respository. Mplayer is in the multiverse repository:

[https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu](https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu)

But I don't really like it. I say Gxine (in the Universe repository) works better after you do this:

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

Also a program called "Vlc" works well.

---

