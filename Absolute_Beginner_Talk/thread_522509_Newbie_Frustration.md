---
title: "Newbie Frustration"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by TruthOrDare on 2007-08-10
I'm not really sure how to say this without sounding whiney...and in a way, I suppose it is.

Why do things in Linux have to be so difficult to install?

I want to download a movie/music player that can play common files. I don't frankly care anymore which one, I just want to be able to download and install one.

Every single one involves compiling and doing countless terminal commands and the install guides are out of date, or just don't work.

Why can't these be simple to install?

For example in windows it is: Download exe, run exe, install program, run program.

It can be done in Ubuntu/Linux. The program for a modem I have that someone made on the forums (which happened to be the first thing I installed), was exactly the same. It was a .deb file. Click, install, go. No messing around trying to get something to compile or anything, just simple.

If you want to install programs in windows, you don't need to go into dos and do whatever, you just point and click,

Now, I know I have to learn how to do things, but for just basic things like installing a program, I shouldn't have to spend ages trying to find a way for it to install, it should be simple.

Is this some sort of geek thing where making things easy is seen as bad? :confused:

I'm not sure whether my problem is a lack of someone to turn to, the learning curve being too high, missing the point, me being idiotic, or a combination of them.

For me, I want to learn, I want to switch for good one day, however it is so frustrating not being able to do basic things.

---

### Post by splintercellguy on 2007-08-10
Try VLC? sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc from the VLC d/l page.

---

### Post by Roaster on 2007-08-10
Hi, I'm very new at this too, but don't give up! In the Add/Remove there are sound players you can install very easily or in the Synaptic manager also. Try it, it's not hard. Good luck and best regards,

---

### Post by Steveway on 2007-08-10
Installing is much easier in Ubuntu than in Windows.
Open Synaptic, search for the program you want, mark it to be installed and if your have choosen everything you want then click apply.

---

### Post by overdrank on 2007-08-10
> **TruthOrDare said:**
> I'm not really sure how to say this without sounding whiney...and in a way, I suppose it is.

Why do things in Linux have to be so difficult to install?

I want to download a movie/music player that can play common files. I don't frankly care anymore which one, I just want to be able to download and install one.

Every single one involves compiling and doing countless terminal commands and the install guides are out of date, or just don't work.

Why can't these be simple to install?

For example in windows it is: Download exe, run exe, install program, run program.

It can be done in Ubuntu/Linux. The program for a modem I have that someone made on the forums (which happened to be the first thing I installed), was exactly the same. It was a .deb file. Click, install, go. No messing around trying to get something to compile or anything, just simple.

If you want to install programs in windows, you don't need to go into dos and do whatever, you just point and click,

Now, I know I have to learn how to do things, but for just basic things like installing a program, I shouldn't have to spend ages trying to find a way for it to install, it should be simple.

Is this some sort of geek thing where making things easy is seen as bad? :confused:

I'm not sure whether my problem is a lack of someone to turn to, the learning curve being too high, missing the point, me being idiotic, or a combination of them.

For me, I want to learn, I want to switch for good one day, however it is so frustrating not being able to do basic things.

HI you can install just about anything you want or need through synaptic manager or add and remove. As for a movie player that works it maybe that you don't have the restricted codecs installed
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
Linux is not windows and there is a learning curve and you must remember that they are two different OS. 
And maybe this link will help you on installing things that are not in the reop's
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
Good luck and hope this helps! :guitar:

---

### Post by Roaster on 2007-08-10
The person wants an easy way to install a music player, not how to use Terminal. Please, some of the folks on here are not ready for the Terminal yet. I know we need to learn to use it but for now just tell them how to install a music player:).

---

### Post by maharbA on 2007-08-10
Welcome to Ubuntu!

Most (but certainly not all) applications can be easily installed with .deb files. There is even a program , called a "package manager" which manages those .deb files (also called packages).
The basic package manager for Debian-based distros (Ubuntu is Debian-based) is apt-get. This is a command-line application and, while powerful and versatile, may be a bit daunting for newcomers. The GUI frontend for apt-get in Ubuntu (Gnome, rather than KDE or XFCE) is called Synaptic Package Manager. There is also a simplified frontend located under the APPLICATIONS menu (APPLICATIONS > ADD/REMOVE).

These programs automatically search websites called "repositories" for .deb files and can install and update programs easily. You can even add repositories yourself by using the repository manager iin System Administration or editing your /etc/apt/sources.list file manually (again, probably not for noobs -- but of all the manual things you can do in Ubuntu and Linux, editing your sources.list is probably the easiest -- if you want to get under the hood, start there).

I hope this helps. I have found that using package managers is just as easy -- if not easier -- than manually downloading an .exe file.
Best of luck!

---

### Post by jingo811 on 2007-08-10
> some of the folks on here are not ready for the Terminal yet. I know we need to learn to use it but for now just tell them how to install a music player.

Of all installation methods out there for Linux using Terminal is the most easy and painless one of them.  As long as you're given the right command lines when asking for your fix in the forums.

Using Terminal is no more than 
[LIST]
[*]Ctrl + C
[*]Ctrl + V
[/LIST]

(In Terminal)
[LIST]
[*]Ctrl + Shift + C
[*]Ctrl + Shift + V
[/LIST]

Let the veterans do the thinking for you that's how I use Terminal :)  Zero thinkage.

---

### Post by Roaster on 2007-08-10
> **jingo811 said:**
> Of all installation methods out there for Linux using Terminal is the most easy and painless one of them.  As long as you're given the right command lines when asking for your fix in the forums.

Using Terminal is no more than 
[LIST]
[*]Ctrl + C
[*]Ctrl + V
[/LIST]

(In Terminal)
[LIST]
[*]Ctrl + Shift + C
[*]Ctrl + Shift + V
[/LIST]

Let the veterans do the thinking for you that's how I use Terminal :)  Zero thinkage.

Ahh, yes there is the rub, the 'right command lines'. Give us time we'll master the Terminal yet:)

---

### Post by lemmy999 on 2007-08-10
Yes its different to Windows. Its not "more" difficult. Copy/paste works just as well in linux but occasionally you may have to use some  windows  keyboard shortcuts ie Ctl/v Ctl/c etc .

The main thing is to find which app you need and then use Synaptic. 

If that fails - ask here!

---

### Post by jmnormand on 2007-08-10
try this

System -> Administration -> Synaptic Package Manager

search for vlc

click on vlc and mark for install then click apply

learning the package manager actually makes installing software a lot easier than it is on windows.  The only problem is if your software is not in the package manager.

---

### Post by aysiu on 2007-08-10
While you're in Synaptic, you may want to install *ubuntu-restricted-extras*, *mozilla-mplayer*, and *mplayer-fonts*; and remove *totem-mozilla*.

If you don't know how to use Synaptic, read this:
[How to install anything in Ubuntu](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by proalan on 2007-08-10
Eventually you will have to use the terminal as a linux user.

The advantage of installing from apt-get is that you are guaranteed the latest most secure and stable versions of software. Further more it keeps ALL software you've already installed updated rather than just the system core.

The deb package system is the closest equivalent to the exe of that other operating system.

If you're looking for quick GUI based software installation heres a good place to get started. Just download double click and install.

[http://www.getdeb.net/browse.php](http://www.getdeb.net/browse.php)

---

### Post by bwtranch on 2007-08-10
sudo apt-get install <justaboutanything>

---

### Post by ocean223 on 2007-08-10
Ok, say i got a program installed and it does'nt put an entry in the drop down menu so I want to put an icon on the desktop.........


 The program that I wan,t to make a shortcut for has to be run from root. I right click on desktop
select "create launcher" what do I use for "command" I tried - sudo <program name >but that did'nt work. I can run from terminal with "sudo program name" however.:)

---

### Post by Steveway on 2007-08-10
If that program has a graphical interface then use:
$gksu programname
or
$gksudo programname
(But gksudo is just a symlink to gksu so they are the same.)

---

### Post by ocean223 on 2007-08-10
Thanks Steveway!, but here's what happened when I typed "$gksudo programnane":
Details: Failed to execute child process "$gksudo" (No such file or directory)

Soooooo. I typed in just gksudo programname (no $ ) and voila . It asked me for my pw and the gui appeared!


Thanks  agian.:)

---

### Post by Steveway on 2007-08-10
Yes, the $ was there so you know that that has to be typed into the terminal.
It's commonly used here.

---

### Post by bwtranch on 2007-08-10
change to that directory first

I like being root when I do this

sudo su

Be careful when you are absolute root! Do what you need to and get outta there with "exit". But, when you are in this mode, you are the superuser, not just a facsimile.

---

### Post by ocean223 on 2007-08-10
So sudo su makes me superduper root and sudo just makes me root? I'm a little cornfused.
And I want to be superroot when I install etc.?:confused:

---

### Post by overdrank on 2007-08-10
> **ocean223 said:**
> So sudo su makes me superduper root and sudo just makes me root? I'm a little cornfused.
And I want to be superroot when I install etc.?:confused:

Hi maybe this link will help
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

:)

---

### Post by ocean223 on 2007-08-10
Thanks Stever. I'm still trying to get down the basic conventions. And I kind of just learn as I go. Get great help from this forum.

---

### Post by ocean223 on 2007-08-10
Uh, yeah. Everything I need to know about root is there all right thanks. Right now I,m not too worried about security as I am the only user of this computer in the house. But I sure don't want to scew up the system again.  I'm on my second install of Ubuntu. First one whent fine but I too adventuresome and followed a guide to be able to us compiz fusion with my ATI graphics card. Wiped out my xp partition somehow. At least now I have this machine 100%linux. Heh Heh
Thanks for the help.

---

### Post by cjnkns on 2007-08-10
I couldn't agree more with the first post (that began this thread)
Nothing is easy with Linux! NOTHING....

People are making it easier but it's really hard to get around a Linux distro with out having to at some point resort to the command line.

To some extent I guess that's the point of Linux, but if Linux is to ever even come close to windows (which with the state of Linux right now that will not happen) the developers and or  community should really decide to distribute a common system and desktop. Unfortunately, that's what the masses are use to and that's what it's going to take for Linux to be taken seriously be the masses of people who are used to point and click operating systems.

Not everyone in this world is a hard core gamer or hard core computer user and just wants it to work. That means not having to surf forums and support groups to figure out how to install the MOST common used codecs. <- So STUPID i can't even get over that.. but I guess that's the separation of free software and non-free.

I mean until i can install EVERYTHING i need to be productive no matter what codec or what video player, jre and blah blah blah i need in order to make my system useful in a easy fashion ( no surfing outdated forums or wki's or getting help from my sons friend) then Linux will never even make a dent into the world of Windows... IMHO

---

### Post by ocean223 on 2007-08-11
Idunno, I kind of like fooling around with this stuff,after all, no one FORCED me to install Ubuntu.
Where else can you take an old beater machine and install the basic software and use it productively? I found the basic install of fiesty to be quite friendly. I did'nt get into any trouble untill I pushed the envelope a little bit to far for my ability. 
If you don't like the OS than get rid of it and go back to windows. Don't bitch about it here please.

---

### Post by TeaSwigger on 2007-08-11
> **cjnkns said:**
> I couldn't agree more with the first post (that began this thread)
Nothing is easy with Linux! NOTHING....

People are making it easier but it's really hard to get around a Linux distro with out having to at some point resort to the command line.

To some extent I guess that's the point of Linux, but if Linux is to ever even come close to windows (which with the state of Linux right now that will not happen) the developers and or  community should really decide to distribute a common system and desktop. Unfortunately, that's what the masses are use to and that's what it's going to take for Linux to be taken seriously be the masses of people who are used to point and click operating systems.

Not everyone in this world is a hard core gamer or hard core computer user and just wants it to work. That means not having to surf forums and support groups to figure out how to install the MOST common used codecs. <- So STUPID i can't even get over that.. but I guess that's the separation of free software and non-free.

I mean until i can install EVERYTHING i need to be productive no matter what codec or what video player, jre and blah blah blah i need in order to make my system useful in a easy fashion ( no surfing outdated forums or wki's or getting help from my sons friend) then Linux will never even make a dent into the world of Windows... IMHO

Do you or do you not believe that you should be free to do anything you want on and with your own computer system? 

Do you or do you not want free software? Free as in free to inspect, free to evaluate, free to keep, free to own and free to do what you darn well please to?

If you do, you will have to stop giving your money to those working against the way you'd like to see things go and basically put your time and brain where your mouth is to try and make things the way you think it should be. That's going to have to be with a *nix system, it's going to have to be with the kind help of others and you will have to bother to dig up work-arounds, codecs or whatever to play this or that format, because you are not free to use Windows or Mac and you are not free to play a number of those formats, except as their corporate owners allow you to, even after you pay them a load for it. It's their choice to make and the choice of all the people making a given format "the MOST common" to make it the most common, and not a choice made by ubuntu or anyone here.

That daunting command line, the mountains and mountains of hand-made codes and the kind people volunteering to help strangers for nothing do work and are all yours for free. Microsoft has taken billions of dollars from folks to deliver a system you do still have to learn things to operate. Linux has been tricky for me and no it doesn't become care free, but then I still remember that first learning to use Windows required plenty of learning, wasn't exactly incident free and also required upkeep. You may also want to observe that everyone involved here are doing it all for nothing. 

Maybe Linux users don't want to make another Windows. Maybe that's fine. Nobody has to help anyone, but we can look around here and see that people are trying a lot to help others inclined to go Linux as an alternative to Windows, etc. I do like many things about Windows and it can work superbly - as can ubuntu, and I like many things about it so...

I didn't think I had a choice to use Windows by the way; like a majority of people, I was under the impression that I had to pay Microsoft for Windows to buy a PC. Or MacIntosh to buy their Mac, but there we are again. Nobody obliged me to try ubuntu and nobody charged me a thin dime for all the work that's gone into it nor even to help me out. Nobody has had me call at $40 and hour and route my call to India so that I could be told I should reinstall the whole thing. How many people have thrown away working computers to the land fills because Windows was messed up?

So who was complaining about ubuntu and the ubuntu volunteers about what again?

:popcorn:

(I'll try to make this my last such ranting here, by the by... we'll see how long that holds! :) )

---

### Post by dangerpl on 2007-08-11
> **cjnkns said:**
> 

To some extent I guess that's the point of Linux, but if Linux is to ever even come close to windows (which with the state of Linux right now that will not happen) the developers and or  community should really decide to distribute a common system and desktop. Unfortunately, that's what the masses are use to and that's what it's going to take for Linux to be taken seriously be the masses of people who are used to point and click operating systems.

Now, why would they want to come close to Windows? And comparing Linux to Windows? If you've used Windows long enough I bet you've encountered a bunch of problems that you will most likely never face in Linux; for example viruses, unexplained system crashes, freezing programs, not even talking about all the money you spend on Windows and Windows compatible software. Did I mention viruses? Besides, for most Windows programs you will find a Linux program that will do exactly the same with one difference. It's absolutely free. Sometimes it takes a little time to get things working; believe me, I've had my share of frustration with several issues as well but I would never go back to Windows. And learning how to install and work in Linux is not rocket science or brain surgery. It's actually pretty simple if you do it a few times. And if we're talking about things working right out of the box, what does Windows have to offer after fresh installation? Same games you've seen in Windows 95? Notepad? Compared to Ubuntu which comes with quite a few pre-installed applications. If you can give me good reasons why Windows is better than Ubuntu, please share... :lolflag:

---

