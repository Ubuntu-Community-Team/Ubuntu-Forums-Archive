---
title: "MP3 decoder and AC'97 ALC850 (I can't play mp3s)"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by halfpower on 2005-06-14
Problem:
I open up Ubuntu's music player and it refuses to load mp3's because it does not have an mp3 decoder.  How do I fix this?

Possibly Relevant Background:
I have an Asus A8V Deluxe which has the Realtek AC'97 ALC850 audio system built-in.  I also have an E-mu 1212M PCI audio/music recording card.  Ubuntu thinks that my E-mu 1212M is a Creative Labs Audigy card (Creative Labs recently acquired E-mu).  I am not trying to use the E-mu 1212M for audio, because it will not run in Linux.

---

### Post by netrattler on 2005-06-14
Not sure which version of Ubuntu you are running so here are the instructions for both.

Hoary:
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

Warty:
[http://ubuntuguide.org/4.10/index.html#codecs](http://ubuntuguide.org/4.10/index.html#codecs)

Joe

---

### Post by TristanMike on 2005-06-16
I am also having the same issue but my problem is I have no idea at all what any of this stuff means...I have spent too many years letting windows do everything for me, these don't explain it in laymans terms. 

I went to this [http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)   website and downloaded a pack that contains mp3 codecs (among others).  

Then I went to this website [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) and BOOM right there, like what is that?  What the heck does "Repositories" mean?  What's with the "code"?

How could I, a brand new user, who doesn't have any idea about "code" and stuff, suppose to make heads or tails of that?  Can someone please help a really stupid noob out.  I feel so overwhelmed....Please Help the Noobs  :( 

OHHHH, What happened to my beloved *.exe????  Woe is me!

Thanx - Tristan.

---

### Post by xmastree on 2005-06-16
[QUOTE=TristanMike]What the heck does "Repositories" mean?[/QUOTE]Well, literally [**repository**](http://dictionary.reference.com/search?q=repository) means:
A place where things may be put for safekeeping.
A warehouse.
A museum.
A burial vault; a tomb.
One that contains or is a store of something specified

Basically, it's an online source for all the things you might need but were too big to put on the CD, or left out for other reasons.

Adding extra repositories means giving ubuntu somewhere esle to look for programs.

For some reason I'm not sure about, certain codecs aren't technically "free", so they're not included on the CD, and their repositories aren't enabled by default, so you have to uncomment them to get at the goodies inside.

Hope this makes it clearer.

---

### Post by poofyhairguy on 2005-06-16
[QUOTE=TristanMike] What the heck does "Repositories" mean?  What's with the "code"?[/QUOTE]

Repositories are places where programs are stored. Instead of having *.exes that you pick up anywhere on the web and install, in Ubuntu there is the goal to package every free open source program and put it on the main repository. Those are the programs you are looking at if you ever open the synaptic program. 

The just of it is that you need to add this new repository in order to get the programs in it. This repo is hosted by Ubuntu, but it is not "official" (aka that means that if you pay for support you can't use it) so Ubuntu tries to make it a little harder to use. Its easy to fix though, and you don't have to know what any of it means.

[QUOTE=TristanMike]How could I, a brand new user, who doesn't have any idea about "code" and stuff, suppose to make heads or tails of that?  Can someone please help a really stupid noob out.  I feel so overwhelmed....Please Help the Noobs  :( 
[/QUOTE]

I'll tell you what. I'll help. First I need you to open the terminal. Its under applications, system tools, then terminal. Don't let it scare you, it is a way for me to help you with you completely needing to understand what going on.

when the terminal opens, put in this command (copy and paste it into terminal):

> sudo gedit /etc/apt/sources.list

If you want a translation of that line into english, it says "I am the administrator (any line that starts with sudo means that), and I want the program gedit to edit the /etc/apt/sources.list file). "

Gedit should open with a file full of text. Select every piece of text in the document and delete it.

Copy the text from the quote below into the document and save and close (in that order) gedit.

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Just so you know, that text you just replaced tells your computer where to find a new respotory to install new software (mp3 software).

Now I need you to copy the next lines, one quote at a time, and paste them into the terminal and hit enter. Then when the line is done (aka you are taken back to the $) add the next line and hit enter.

> sudo apt-get update
> 
sudo apt-get install sun-j2re1.5 flashplayer-mozilla acroread mozilla-acroread w32codecs gstreamer0.8-plugins gstreamer0.8-lame libdvdcss2 smeg totem-xine rar

Those two lines together tells Ubuntu to download from the internet the codec (or software) you need to play Mp3s. For good measure, this line will also install Flash, Java, and Windows Media Pluggins for you so you hopefully won't have any problems in the future.

when the last line is done, you are done. The program Rhythmbox will play all your mp3s, and the programs called totem will play mp3s and anything else.

If you have questions please ask them.

---

### Post by xmastree on 2005-06-16
[QUOTE=poofyhairguy]Now I need you to copy the next lines, one line at a time[/QUOTE]It might be worth mentioning that there are only two lines there, both of which begin with 'sudo'.
On my (1280 wide) screen the second line was wrapped, making it look like 'totem-xine rar' was the third command...

---

### Post by TristanMike on 2005-06-16
To "poofyhairguy" this is twice you have come to the rescue for me, :)  thank you very much.  :)  I haven't tested too much out yet but I'm pretty sure it all worked as I can play my mp3's now.  I must say, I can get pretty overwhelmed when things don't go smoothly.  I'M TOO USE TO POINT AND CLICK...GRRRR...WINDOn'tS! BTW, where do I find everything that I just installed?  How come my "Applications(Start)" menu hasn't added, let's say, Java?

I did get an update though and if someone could clarify what these "warnings" mean I'd appreciate.

[http://img.photobucket.com/albums/v420/TristanMike/Screenshot-1.png](http://img.photobucket.com/albums/v420/TristanMike/Screenshot-1.png)

[http://img.photobucket.com/albums/v420/TristanMike/Screenshot.png](http://img.photobucket.com/albums/v420/TristanMike/Screenshot.png)

Very good explanations of some of the terms you listed below.  So just to clarify a few things.

1 Repositories - "xmastree" - I can see the light at the end of the tunnell.  :) Where are these kept?  Is the "repository" aka "synaptic" or is there a folder?  Or is it web only?

2 Terminal - Is the "Terminal" is where all of my installations start from is it like the .exe for everything?

3 Apt-get - I see people talking about this, but I still don't really understand what it is.  If someone could clarify, it would be nice.  Is this a "program"? or an instruction like "sudo"?

Now with those few things out of the way, the question that keeps popping into my head is what if I wanna install, lets say, Azureus.  Where do I start?  I do love and appreciate the help you all offer here (ITS AWESOME!) and I understand time and patience will me my most valued friend right now, but is there a "standard" for installation of software as you can't be there all the time for me?  Will I need to run this particular "code" (I'm using code cause I'm not sure if this is the proper terminology for the series of commands you just had me run) many times or just after the install to get things going.

Sorry for so much to overwhelm you guys......
TristanMike

---

### Post by poofyhairguy on 2005-06-16
[QUOTE=TristanMike]To "poofyhairguy" this is twice you have come to the rescue for me, :)  thank you very much.  :)  I haven't tested too much out yet but I'm pretty sure it all worked as I can play my mp3's now.  I must say, I can get pretty overwhelmed when things don't go smoothly.  I'M TOO USE TO POINT AND CLICK...GRRRR...WINDOn'tS! BTW, where do I find everything that I just installed?  How come my "Applications(Start)" menu hasn't added, let's say, Java?[/QUOTE]

Everything I told you to install (like java) are programs that only come to life when other programs need them. No need (or use) for menus.

> I did get an update though and if someone could clarify what these "warnings" mean I'd appreciate.

[http://img.photobucket.com/albums/v420/TristanMike/Screenshot-1.png](http://img.photobucket.com/albums/v420/TristanMike/Screenshot-1.png)

[http://img.photobucket.com/albums/v420/TristanMike/Screenshot.png](http://img.photobucket.com/albums/v420/TristanMike/Screenshot.png)


Those warning mean you are using an unofficial repo. Ignore.

> 
1 Repositories - "xmastree" - I can see the light at the end of the tunnell.  :) Where are these kept?  Is the "repository" aka "synaptic" or is there a folder?  Or is it web only?

The Ubuntu repo is on the web, but a repo is any place where a lot of software pacakges are held.

> 2 Terminal - Is the "Terminal" is where all of my installations start from is it like the .exe for everything?

The terminal is the heart of Linux. Everything you see is actually doind something in the terminal as it works (you just can't see it). The terminal is for more than installing programs.

> 3 Apt-get - I see people talking about this, but I still don't really understand what it is.  If someone could clarify, it would be nice.  Is this a "program"? or an instruction like "sudo"?


Tis a program to install software from a repo.

---

### Post by TristanMike on 2005-06-16
As they say in french, Merci Beaucoup or Thanx, you are a really good tutor "poofyhairguy, aka Brian....lol nice avatar"  Is there an IRC channel or someother place I can get "live support"?

I guess I need to understand WHY I did what you asked me to.  Knowing WHAT the codes do and if they are interchangeable and what changes I need to learn I can make to codes and such in order to install things.

---

