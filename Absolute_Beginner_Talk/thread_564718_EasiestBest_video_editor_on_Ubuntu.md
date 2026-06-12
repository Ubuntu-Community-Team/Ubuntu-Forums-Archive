---
title: "Easiest/Best video editor on Ubuntu?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-10-01
Got feisty installed, now the kids want to start editing video and audio.

What programs are easiest to use? what are the best and why?

They have tried kino and did not like it... think it has sg to do with it being hard, much harder than what they used to use in the dreaded MS days...

so, what should I install for them?

thanks

robi

---

### Post by por100pre1 on 2007-10-01
Try Pitivi:

```
sudo aptitude install pitivi
```

---

### Post by Perfect Storm on 2007-10-01
Cinelerra (best IMHO);

The one in the repo is old

But adding this to your sourcelist will get your a newer version;

[b]## Cinelerra for Pentium4 ###
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./
[/b]

If you want it to another arch than i686 you can make changes in the line by checking here ; 
[http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/)

---

### Post by rsambuca on 2007-10-01
How about Avidemux (You can just install it via Synaptic Package Manager).

I agree that cinelerra is probably the best, but it is pretty tough to use.

Pitivi I have never heard of, but it looks interesting.  I think I will try it myself, too!

---

### Post by Samhain13 on 2007-10-01
Speaking for Cinelerra as well, and agreeing with rsambuca that it may take a while to get used to.

I tried using Avidemux just this morning. I think if you're coming from a multi-track ortientation (as in seeing video and audio tracks spanning a timeline) with resources visible in some window/collection near-by, Avidemux will be a bit of a puzzle to work on.

The Cinelerra I'm using though can be had from the resources outlined here:
[http://cvs.cinelerra.org/getting_cinelerra.php#feisty](http://cvs.cinelerra.org/getting_cinelerra.php#feisty)
(specifically "for i386, by muzzol").

Good luck! :D

---

### Post by swisscow on 2007-10-01
Kdenlive is worth a look - very similar to windows moviemaker. You will need to go to the website to work out how to install it - but did read somewhere it's coming with Gutsy

---

### Post by beanco on 2007-10-02
thanks.

my oldest son will be using these programs the most, his english is far from perfect so reading manuals is only going to make him angry. that is why I would like a program that is easy to use...

I will get them all and let him try them....

hope they all have easy to follow tutorials..


thanks again

robi

---

### Post by beanco on 2007-10-02
> **por100pre1 said:**
> Try Pitivi:

```
sudo aptitude install pitivi
```

ran that and got this




```
Unknown command "isntall"
aptitude 0.4.4
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
.....

....

This aptitude does not have Super Cow Powers.
```

what's that all about?

---

### Post by Perfect Storm on 2007-10-02
try check your spelling ;)

---

### Post by beanco on 2007-10-02
so I am not a spelling  genious but when I copied/pasted this is what I got

```

rob@rob-desktop:~$ sudo aptitude install pitivi
Reading package lists... Done
Segmentation fault (core dumped)

```

what is segmentation fault...?

robi

---

### Post by clesage on 2007-10-03
It should be

```
sudo apt-get install pitivi
```

Not "aptitude"

I tried pitivi which shipped with Ubuntu Studio, and dragging and dropping files to the "Drag And Drop Here" window doesn't work. I can import files, but once I have them in the timeline, there seems to be no way to play anything. All the buttons are greyed out and nothing works!

I wish you luck though.

---

### Post by rsambuca on 2007-10-03
> **clesage said:**
> It should be

```
sudo apt-get install pitivi
```

Not "aptitude"

I tried pitivi which shipped with Ubuntu Studio, and dragging and dropping files to the "Drag And Drop Here" window doesn't work. I can import files, but once I have them in the timeline, there seems to be no way to play anything. All the buttons are greyed out and nothing works!

I wish you luck though.Aptitude should work just as well as apt-get.

---

### Post by Incense on 2007-10-03
I really like kdenlive. It's only in the Gusty repos though.

---

### Post by Irihapeti on 2007-10-03
A Feisty version of Kdenlive is available from Trevino's repository 

[http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/)

---

### Post by Toadmund on 2007-10-03
Anyone got an opinion on LiVES?
[http://lives.sourceforge.net/]("http://lives.sourceforge.net/")
I just DL'ed it, seems the sound is garbled (.MOV format?)
And I don't know what file my saved works go to.
Other than that it seems easy to use.
I think it does not like the .MOV format?
Anyone use this?

---

### Post by Toadmund on 2007-10-03
> **clesage said:**
> 

I tried pitivi which shipped with Ubuntu Studio, and dragging and dropping files to the "Drag And Drop Here" window doesn't work. I can import files, but once I have them in the timeline, there seems to be no way to play anything. All the buttons are greyed out and nothing works!

I wish you luck though.
Hmmm, I also am trying (trying to try) PiTiVi and have this same problem, just doesn't work, buttons greyed out.

---

### Post by fivesmellydragons on 2007-10-03
> **Toadmund said:**
> Anyone got an opinion on LiVES?
[http://lives.sourceforge.net/]("http://lives.sourceforge.net/")
I just DL'ed it, seems the sound is garbled (.MOV format?)
And I don't know what file my saved works go to.
Other than that it seems easy to use.
I think it does not like the .MOV format?
Anyone use this?

Yeah I just tried it for the first time and it worked ok until I closed it out and it crashed KDE and I had to do a hard reboot just to get it back to normal again. I might try it again with a smaller video (something other than a DVD) to see if it doesn't crash that way.

---

### Post by Toadmund on 2007-10-03
Right now I am in browse mode, currently giving kdenlive a test drive.
There is a wiki on it, [http://en.wikibooks.org/wiki/Kdenlive/Quickstart#Tutorials_in_video]("http://en.wikibooks.org/wiki/Kdenlive/Quickstart#Tutorials_in_video")
There are a few tutorial videos at the bottom of the page.

I am going to monitor this thread, try out some of these apps, and make a decision with what to stick with from there.

I'd really like to improve and edit my video's so here I am learning how, and I'd like to keep the learning curve as straight as possible.

---

### Post by Incense on 2007-10-03
> **Toadmund said:**
> Hmmm, I also am trying (trying to try) PiTiVi and have this same problem, just doesn't work, buttons greyed out.

Maybe try the version from getdeb. I read some place this works bettter then the one shipped with Studio.

[http://www.getdeb.net/app.php?name=PiTiVi]("http://www.getdeb.net/app.php?name=PiTiVi")

---

### Post by Incense on 2007-10-03
> **Toadmund said:**
> Right now I am in browse mode, currently giving kdenlive a test drive.
There is a wiki on it, [http://en.wikibooks.org/wiki/Kdenlive/Quickstart#Tutorials_in_video]("http://en.wikibooks.org/wiki/Kdenlive/Quickstart#Tutorials_in_video")
There are a few tutorial videos at the bottom of the page.

I am going to monitor this thread, try out some of these apps, and make a decision with what to stick with from there.

I'd really like to improve and edit my video's so here I am learning how, and I'd like to keep the learning curve as straight as possible.

Kdenlive is in the openSUSE repos and it's really a great app. Very easy to use, and it shows a lot of promise. I'm happy Ubuntu is finally bringing it into the gutsy.

---

### Post by mramsey on 2007-10-03
Another Vote for kdenlive! :guitar:

---

### Post by beanco on 2007-10-04
ok i will try to get the boy Kdenlive

but I am too much of a n00b to understand how to get it.

somebody spare me and take merc on my sole.

what is the easiest way to get it?

cannot I just do

sudo apt-get install kdenlive?


thanks

robi

---

### Post by iconicmoronic on 2007-10-04
I can't call it the best, esiest; etc. because I'm not an editing Guru.
Reall I think it depends what you mean, if you would like to edit existent video, create animated videos, stop-motion; etc.

Anway, a non-linear video editor that seems to be getting high acclaim is this one:
[http://cinelerra.org/](http://cinelerra.org/)

It's easy enough to install using a .deb package or dpkg. Thing is, I didn't have any luck with apt-get, and wget would download and then fail to install. Really, I'm making it sound more difficult than it is though -- try it, you might like it.

---

### Post by beanco on 2007-10-05
what is linear and non linear video editing....????

just thoguth I would ask.

Aron tried cineralla before and foudn it far to difficult.

thanks

robi

---

### Post by Incense on 2007-10-05
> **beanco said:**
> ok i will try to get the boy Kdenlive

but I am too much of a n00b to understand how to get it.

somebody spare me and take merc on my sole.

what is the easiest way to get it?

cannot I just do

sudo apt-get install kdenlive?


thanks

robi

If you are on 7.04, then go [here]("http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html") to add the Trevino repo to your /etc/apt/sources.list. Then you will be able to apt-get kdenlive. If you wait for Gutsy to roll out in a couple weeks you can just get it from the offical repos. I never really understood why ubuntu really does not have any video editors in the repos.

---

### Post by Toadmund on 2007-10-08
Kdenlive, tried to add video with an mp3 soundtrack, and the sound on my video became de-sychronized (not the mp3)
How would I re-sych it?

How do I delete certain unwanted sounds from a video?

How do I save my work as a simple file and not as a DVD?

Simple things that should not be difficult but are.

Anyone?

Is Cinerella easier?

PS, I am also having major unresponsiveness, sliders lagging, video stopping some undetermined time after I hit the stop button.

---

### Post by Perfect Storm on 2007-10-08
> Is Cinerella easier?

Not actually. It require a little learning. It's quite powerful and it's aiming for pro users.

---

### Post by bliffle on 2007-10-08
Is VirtualDub available for ubuntu?

---

### Post by pixelnate on 2007-10-08
> **Irihapeti said:**
> A Feisty version of Kdenlive is available from Trevino's repository 

[http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/)


This would be thebest place for a person to start with video editing on Ubuntu. It is by far the easiest to set up and the easiest to use. Not to mention the fact that all the features work [cough] Pitivi [cough]. And you won't spend half your time trying to figure out the interface (Cinelerra, I am looking at you) or cursing the app for all the crashing it does (again, talking to Cinelerra here).

KDEnlive, try it, you'll like it.


:guitar:

---

### Post by Toadmund on 2007-10-08
With Kdenlive,
How do I at least do these: (from my post above)

-How do I delete certain unwanted sounds from a video?

-How do I save my work as a simple file and not as a DVD?
  
I don't want to burn DVD's (won't let me do it anyways) I just want to save a _file_ on my hard drive that will open up with a player, such as VLC.
I can't believe I can't figure out how to do these two simple things!

That's not all the things that could be retardified for my pleasure either!
I have more issues. But two at a time.

---

### Post by Incense on 2007-10-08
> **Toadmund said:**
> Kdenlive, tried to add video with an mp3 soundtrack, and the sound on my video became de-sychronized (not the mp3)
How would I re-sych it?

How do I delete certain unwanted sounds from a video?

How do I save my work as a simple file and not as a DVD?

Simple things that should not be difficult but are.

Anyone?

Is Cinerella easier?

PS, I am also having major unresponsiveness, sliders lagging, video stopping some undetermined time after I hit the stop button.

That's a lot of questions. I think you may want to take a look at the Kdenlive Wiki for your answers.

[http://en.wikibooks.org/wiki/Kdenlive]("http://en.wikibooks.org/wiki/Kdenlive")

This section may be quite helpful to you.

[http://en.wikibooks.org/wiki/Kdenlive/Using_Kdenlive]("http://en.wikibooks.org/wiki/Kdenlive/Using_Kdenlive")

Cinerella is a fantastic program once you get the hang of it. Out of the gate though, no it is not easier.

---

### Post by klange on 2007-10-08
I had some good times with Cinelerra over the past few weeks. It works quite nicely and the results are wonderful. Interface takes some getting used to. I'd love to see a GTK version in the future.

---

### Post by beanco on 2007-10-09
> **Incense said:**
> If you are on 7.04, then go [here]("http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html") to add the Trevino repo to your /etc/apt/sources.list. Then you will be able to apt-get kdenlive. If you wait for Gutsy to roll out in a couple weeks you can just get it from the offical repos. I never really understood why ubuntu really does not have any video editors in the repos.


n00b alert!!!!

how do I add the trevino repo to my /etc/apt/soruces.txt?

Can I just copy and paste it into the end of that .-txt file?


robi

---

### Post by Faud on 2007-10-09
> **Artificial Intelligence said:**
> Cinelerra (best IMHO);

The one in the repo is old

But adding this to your sourcelist will get your a newer version;

[b]## Cinelerra for Pentium4 ###
deb [url]http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/


Screenshot attached. This normal ?

Yes, my internet was working just fine; hence the streaming music playing in xmms

---

### Post by Incense on 2007-10-09
> **beanco said:**
> n00b alert!!!!

how do I add the trevino repo to my /etc/apt/soruces.txt?

Can I just copy and paste it into the end of that .-txt file?


robi

Open your terminal (Applications - Accessories - Terminal)

type

```
gksudo gedit /etc/apt/sources.list
``` 

At the bottom of the list add the following two lines

```
 deb http://download.tuxfamily.org/3v1deb feisty 3v1n0
deb-src http://download.tuxfamily.org/3v1deb feisty 3v1n0
```

Save and close.

```
sudo aptitude update && sudo aptitude install kdenlive
```

You should be set.

Cheers

---

### Post by Toadmund on 2007-10-09
I am now trying cinelerra, it looks really nice! However, when I try to render I get this:
(See attachment)
Any cinelerra users know how I can fix this problem?

Thanks

---

### Post by beanco on 2007-10-10
Incense,

thanks I tried it and got this

> 
rob@rob-desktop:~$ sudo aptitude update && sudo aptitude install kdenlive
Get:1 [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/main Translation-en_US          
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:2 [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty-updates/main Translation-en_US   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Get:4 [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty Release [57.2kB]
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]         
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/3v1n0 Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                     
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                           
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                           
  
Get:6 [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty-updates Release [50.9kB]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Get:7 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14.2kB]               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources               
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/main Packages                           
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/restricted Packages
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                                
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/3v1n0 Packages                         
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/main Sources       
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/restricted Sources
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/universe Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/universe Sources
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/3v1n0 Sources
Hit [http://hu.archive.ubuntu.com](http://hu.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 123kB in 0s (143kB/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  kdenlive 
The following packages have been automatically kept back:
  libfaac0 
The following NEW packages will be automatically installed:
  kdelibs-data kdelibs4c2a libakode2 libarts1-akode libarts1c2a libartsc0 
  libavahi-qt3-1 liblua50 liblualib50 liboggflac3 libopenexr2c2a libpcre3 
  mlt mlt++ perl-suid 
The following packages have been kept back:
  avidemux libmagick9 libmusicbrainz4c2a libsndfile1 openoffice.org 
  openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common 
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-style-human 
  openoffice.org-writer python-uno ttf-opensymbol wpasupplicant 
The following NEW packages will be installed:
  kdelibs-data kdelibs4c2a libakode2 libarts1-akode libarts1c2a libartsc0 
  libavahi-qt3-1 liblua50 liblualib50 liboggflac3 libopenexr2c2a libpcre3 
  mlt mlt++ perl-suid 
0 packages upgraded, 16 newly installed, 0 to remove and 24 not upgraded.
Need to get 24.2MB of archives. After unpacking 80.6MB will be used.
The following packages have unmet dependencies:
  kdenlive: Depends: libfreetype6 (>= 2.3.5) but 2.2.1-5ubuntu1.1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
kdenlive [Not Installed]

Score is -10001


any ideas what the problem is

robi

---

### Post by Irihapeti on 2007-10-10
Robi:

I have the same problem: I can't upgrade to the very latest Kdenlive for the same reason. I am guessing -and it is only a guess - that if the libfreetype6 were upgraded it would break a number of other things.

However, the Kdenlive version marked svn20070909 will work with the current libfreetype6. It's the one I have currently. If you can get hold of that, you should be in business. Unfortunately, I don't know where it would be available. Trevino's site doesn't appear to have it for download.

Perhaps someone else can help.

Irihapeti

---

### Post by Toadmund on 2007-10-10
I sort of got past my problem with cinelerra, I followed some of the pictorial instructions here:
[http://crazedmuleproductions.blogspot.com/2007/06/beginners-guide-to-exporting-video-from.html#webdownload]("http://crazedmuleproductions.blogspot.com/2007/06/beginners-guide-to-exporting-video-from.html#webdownload")
However, and of course, when I try to input my preferences they change back, why? Because the OK button is hidden (a you tube video said their was one) I've tried 'always on top', resize is greyed out, no handles to resize the window.
Waddo-Ido?
I cannot access the bottom portion of this window, or is their a hidden portion I can't access, not sure.
Please see attachment:

PS, the tabs at the bottom hide a bit, but not all of the bottom, I can 'always on top' over them.

---

### Post by rsambuca on 2007-10-10
You can move the window up by pressing alt and left mouse button anywhere on an open window. Then just drag the window up.

---

### Post by Incense on 2007-10-10
> **Irihapeti said:**
> Robi:

I have the same problem: I can't upgrade to the very latest Kdenlive for the same reason. I am guessing -and it is only a guess - that if the libfreetype6 were upgraded it would break a number of other things.

However, the Kdenlive version marked svn20070909 will work with the current libfreetype6. It's the one I have currently. If you can get hold of that, you should be in business. Unfortunately, I don't know where it would be available. Trevino's site doesn't appear to have it for download.

Perhaps someone else can help.

Irihapeti

I've been searching for an answer, and the only one I found is a bit dodgy, bit I'm sure it will work. 

[http://www.uluga.ubuntuforums.org/showthread.php?t=523683&page=2]("http://www.uluga.ubuntuforums.org/showthread.php?t=523683&page=2")

> I was getting the same error

Quote:
kdenlive:
Depends: libfreetype6 (>=2.3.5) but 2.2.1-5ubuntu1.1 is to be installed
what I did, and if you do it is UP TO YOU !!!

added a gutsy main to my sources list (currently using fiesty 4.07) and reload the package list. a new libfree6 was there. I installed it and some other files came with it too. about 9MB. I then removed the gutsy main and reload packages again. Then install kdenlive. It is working, I just have to work out how to use it right.

Hope this is some help to you.

If I have done something really, really bad please post here so someone does not follow my mistakes.


---

### Post by beanco on 2007-10-11
Thanks Incense,

when I am abel to decypher what it means to add this and remove that I will give it a try.. but for now I am at work, no ubuntu here, yet...

robi

---

### Post by Incense on 2007-10-11
> **beanco said:**
> Thanks Incense,

when I am abel to decypher what it means to add this and remove that I will give it a try.. but for now I am at work, no ubuntu here, yet...

robi

What that post is saying, is that the OP added 

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
``` 

to their /etc/apt/sources.list file, installed the missing file from the gutsy repo, then removed the lines they just added.

---

### Post by Toadmund on 2007-10-11
rsambuca said:
> You can move the window up by pressing alt and left mouse button anywhere on an open window. Then just drag the window up.
Thanks very much, now I can just get on with it!

---

### Post by beanco on 2007-10-24
Aron has been using 

avidemux
kino
pitivi

he would like to try out cinelerra

I still do not understand how to get it.

Please give me a step by step. sorry to be such a n00b


thanks

Robi

---

### Post by rsambuca on 2007-10-24
> **beanco said:**
> Aron has been using 

avidemux
kino
pitivi

he would like to try out cinelerra

I still do not understand how to get it.

Please give me a step by step. sorry to be such a n00b


thanks

Robi

You can get it [here]("http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu").

---

### Post by luckyluca on 2007-10-26
> **rsambuca said:**
> You can get it [here]("http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu").

Hello, I'm a n00b too and I've got a couple of questions:
1) can I install the feisty 7.04 cinerella from the link above on ubuntu studio 7.10?
2) and in case, since the laptop I'm going to install ubuntu studio to comes with the Intel GMA950 integrated video card, should I opt for the opengl release or normal i386 release?

Thanks!
Luca 
p.s.
I'm so looking forward to install ubuntu and get rid of Windows! ehehe

---

### Post by beanco on 2007-10-27
> **rsambuca said:**
> You can get it [here]("http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu").



got it and it worked.

Aron says thanks to everybody ehre and that so far cinelerra is the easiest to use for him.

robi

---

### Post by stbub on 2007-10-29
Well, I have a bunch of videos I recorded with my PVR card.  So, now I want to do some editing/tidying...

Kino: didn't like that it had to first convert perfectly fine .mpg files before allowing me to do any editing.  So I skipped this one.

Cinelerra:  Looks powerful.  Crashes all the time.  A real drag to figure out how to export to a proper file format.  And of course, it didn't like it when I offered it an .mpg file that is more than 4G.

kdenlive: Quick to accept my .mpg without a fuss.  UI seems ok.  Problem is that it crashes all the time when I start editing the video to remove unwanted parts.

Am I the only one to be experiencing constant crashes?

I'm on gutsy i386 (Core 2 Duo CPU, 2G of ram, lots of disk space)

---

### Post by Statik on 2007-10-31
STBub, I'm not experiencing crashes with KDENLive, but I am experiencing regular noise in the rendered video and video/audio desync with many of the HQ renders. Haven't found a solution yet.

Cinelerra is installed, but no video is shown in the compositor window so I can't do cuts.

Statik

---

### Post by stbub on 2007-11-01
> **Statik said:**
> STBub, I'm not experiencing crashes with KDENLive, but I am experiencing regular noise in the rendered video and video/audio desync with many of the HQ renders. Haven't found a solution yet.

Cinelerra is installed, but no video is shown in the compositor window so I can't do cuts.

Statik

For KDenlive, it could be that it has problems with the particular video I'm feeding it (though surely I can't be the first one to pass a video coming from a PVR150 to KDenlive)

For Cinelerra, I do see the video in the compositor window.

---

### Post by beanco on 2007-11-02
Aron has been having sound issues with cinelerra!

sometimes he gets no sound!

Anybody else with similar issues?

robi

---

### Post by bribaetz on 2007-11-04
> **Incense said:**
> If you are on 7.04, then go [here]("http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html") to add the Trevino repo to your /etc/apt/sources.list. Then you will be able to apt-get kdenlive. If you wait for Gutsy to roll out in a couple weeks you can just get it from the offical repos. I never really understood why ubuntu really does not have any video editors in the repos.

i use an Intel processor so i suppose i cant get it all of these downloads are for amd

---

### Post by rsambuca on 2007-11-04
> **bribaetz said:**
> i use an Intel processor so i suppose i cant get it all of these downloads are for amd

Actually, the .deb packages have been compiled for either 32bit (i386), or 64bit (amd64) architecture.    The 'amd' part of the package names is not specific to the AMD brand processors, but is usable by both intel and amd 64bit cpus.

---

### Post by bribaetz on 2007-11-04
then why wont it install

---

### Post by rsambuca on 2007-11-04
> **bribaetz said:**
> then why wont it install

To what "it" are you referring?  What version of Ubuntu are you running.  What architechture?

---

### Post by bribaetz on 2007-11-04
7.04 as it says to the right of my name i'm using 32 bit(i think) intel p4 (the it i am referring to is kdenlive).
i'm also wiling to learn to use cinelerra if  you know of any tutorials

---

### Post by P4man on 2007-11-04
I tried most video editors suggested here.. but the fact of the matter is that Linux doesn't have as good video editors as Windows. IMHO video editing and gaming as the real sour point of Linux at this point. 

In windows you have Moviemaker at the low end ("free" and very simple, yet pretty damn good), and stuff like Premiere, and Vegas if you are more demanding.   None of these work under Wine, but Im completely hooked to Sony Vegas, so I actually run it under Linux using virtualbox.

You can (briefly) see it in action here:
[http://www.youtube.com/watch?v=Kxk6oFqMJVY](http://www.youtube.com/watch?v=Kxk6oFqMJVY)
A how-to is in progress, click my signature to see it

I'm not saying that is the best solution for you, but its what works best for me. 
YMMV :)

---

### Post by Crafty Kisses on 2007-11-04
Pitivi.

---

### Post by bribaetz on 2007-11-04
i just want to se a good one kdenlive i think would work for me i just cant get it set up 
does anyone know of any good tutorials on cinelerra

---

### Post by rsambuca on 2007-11-04
> **bribaetz said:**
> 7.04 as it says to the right of my name i'm using 32 bit(i think) intel p4 (the it i am referring to is kdenlive).
i'm also wiling to learn to use cinelerra if  you know of any tutorials

I am not sure what you are having problems with.  Just [click on this link]("http://3v1n0.tuxfamily.org/apt-repository/pool/feisty/3v1n0/kdenlive_0.5+svn20070922~3v1ubuntu0_i386.deb") to download it, and then double-click on it to install it.

---

### Post by bribaetz on 2007-11-04
error: dependency not satisfiable: libfreetype6

---

### Post by rsambuca on 2007-11-04
Is that exactly what it says?  There must be more (ie.  What are the numbers?)

Also, are you sure you have all of your repositories enabled?  libfreetype6 is in the feisty repos.

---

### Post by bribaetz on 2007-11-04
nope thats all it says
edit:its on my computer as well

---

### Post by Dr Small on 2007-11-04
Try using "sudo dpkg -i *packagename*" in the terminal so it can give us a full error output ;)

---

### Post by bribaetz on 2007-11-04
if its not enabled how do i enable  that file

---

### Post by bribaetz on 2007-11-04
> **Dr Small said:**
> Try using "sudo dpkg -i *packagename*" in the terminal so it can give us a full error output ;)

out put being ```
   brian@brian-desktop:~$ sudo dpkg -i kdenlive
Password:
dpkg: error processing kdenlive (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kdenlive
brian@brian-desktop:~$ 

```

---

### Post by Dr Small on 2007-11-04
Is the file called kdenlive.deb ? If so, then that is what you put as "packagename"
```
sudo dpkg -i kdenlive_0.5+svn20070922~3v1ubuntu0_i386.deb
```

---

### Post by bribaetz on 2007-11-04
> **Dr Small said:**
> Is the file called kdenlive.deb ? If so, then that is what you put as "packagename"
```
sudo dpkg -i kdenlive_0.5+svn20070922~3v1ubuntu0_i386.deb
```

```
   brian@brian-desktop:~$ sudo dpkg -i kdenlive_0.5+svn20070922~3v1ubuntu0_i386.debdpkg: error processing kdenlive_0.5+svn20070922~3v1ubuntu0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kdenlive_0.5+svn20070922~3v1ubuntu0_i386.deb
brian@brian-desktop:~$ 


```

---

### Post by rsambuca on 2007-11-04
You have to change to the directory where you downloaded the file.  Then run the dpkg command.

---

### Post by bribaetz on 2007-11-04
how do i enable libfreetype6

---

