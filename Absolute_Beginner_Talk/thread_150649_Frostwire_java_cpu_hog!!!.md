---
title: "Frostwire java cpu hog!!!"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-26
I cant get frostwire to run good. I even switched the Java platform to Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM) It still maxes my CPU to 100%
All my Linux buddies tell me Java is a CPU Hog!!!! I did not have this issue (hate to admit it) with xp pro WHY!!!

---

### Post by Bloch on 2006-03-26
[QUOTE=wolfee]I cant get frostwire to run good. I even switched the Java platform to Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM) It still maxes my CPU to 100%
All my Linux buddies tell me Java is a CPU Hog!!!! I did not have this issue (hate to admit it) with xp pro WHY!!![/QUOTE]

Are all your java programs slower when running linux as opposed to windows?
It's possible windows is simply better in this regard.

---

### Post by wolfee on 2006-03-26
No the download speed is better!! It just uses 100% cpu I think Java is linux based anyway so it should run better on ubuntu

---

### Post by jetpeach on 2006-03-26
Which version of Frostwire are you running?  One of the slightly older revisions, I believe the one installed with Automatix, has a 100% cpu bug that recently was fixed.  I can't remember the details about it, but it's on the frostwire web site...

For me, frostwire is comparable speed in ubuntu and on windows.

---

### Post by Gnowm on 2006-03-28
Was this issue resolved?

top reports java using 70%+ cpu

Frostwire 4.10

---

### Post by wolfee on 2006-03-28
No I need to figure out how to install the latest frostwire because the bug (as far as I know) is not fixed. I jut installed my 1st tar.gz file!!!!!!!!!!!!!!
It was ies4linux which I'm not sure why I did. I think because some wine installed programs (like 3d max 7 which i'm not sure will run yet) will say "you need at least ie 6 to install this version #$%^ microshaft what the $%^&* does ie6 have to do with 3d max? Any how thanx for asking and for your help I will get back to you. Well I tried to install Adobe photoshop 7.o .........................It installed no desk icon so I can't find it to use it!!!!!!!!!

---

### Post by Mustard on 2006-03-28
Applications are run by using the wine command from the command line, or you can write a startup script that will do the same thing. An example of a command to start an app in wine is..

```
wine /path_to_application/application_name

#subsitite the correct pathname and application name
#below is one I use for starting Picasa

wine .wine/drive_c/Program\ Files/Picasa2/Picasa2.exe

```

I suppose you could still add this to the menu using the menu editor, but installing windows software in wine is not going to create shortcuts for you on desktop.

All the apps are installed in a hidden directory in your $HOME folder called .wine.  Select show hidden files/folders in nautilus so you can see them.

---

### Post by wolfee on 2006-03-28
[QUOTE=Mustard]Applications are run by using the wine command from the command line, or you can write a startup script that will do the same thing. An example of a command to start an app in wine is..

```
wine /path_to_application/application_name

#subsitite the correct pathname and application name
#below is one I use for starting Picasa

wine .wine/drive_c/Program\ Files/Picasa2/Picasa2.exe

```

I suppose you could still add this to the menu using the menu editor, but installing windows software in wine is not going to create shortcuts for you on desktop.

All the apps are installed in a hidden directory in your $HOME folder called .wine.  Select show hidden files/folders in nautilus so you can see them.[/QUOTE]



 Dude you ROCK!! now I found adobe photoshop!!! And IT WORKS!!!! THANX THANX THANX!!!! how do I install frostwire tar.gz or .deb files? I did it with ies4linuxtar.gz without which i could not have installed photoshop but i got lucky after unzipping it in terminal by typing

ies4linux/ies4linux

which gave me 
Please choose an option:
cool I chose #1 for ie 5, ie5.5, and ie6

---

### Post by Gnowm on 2006-03-29
why are we talking about wine for frostwire? Is there not a native Linux version, or is it a bug regarding systems with wine + java thats causing the issue?

---

### Post by Gnowm on 2006-03-29
Update, I have Frostwire 4.10.5 installed. I found Frostwire 4.10.9xxx.deb.

Tried apt-get upgrade, I come from Fedora, is apt-get  = yum ie remote installs with dependencies resolved? So my question would be is there an rpm equiv in debian?

Double clicking the .deb file opened fileroller and it failed (obviously).

I have a standard Ubuntu 5.10 breezy install with an Automatix update of most things. no other seperate updates

---

### Post by wolfee on 2006-03-29
Qrk's Avatar
 
Join Date: Aug 2005
Dapper Drake Testing/ User
Beans: 402
	
Default Re: I can't install Frostwire tar.gz
I've heard there is a problem with the latest frostwire. I just tried to install it on my system and I also couldn't get it to work at first. A look back in the forum suggests that something wasn't configured right for Linux systems (one of the files is still for windows)

Anyway this is the fix:

Code:

sudo apt-get install sysutils
 sudo dos2unix /usr/lib/frostwire/runFrost.sh

---

### Post by Mustard on 2006-03-29
[QUOTE=Gnowm]Update, I have Frostwire 4.10.5 installed. I found Frostwire 4.10.9xxx.deb.

Tried apt-get upgrade, I come from Fedora, is apt-get  = yum ie remote installs with dependencies resolved? So my question would be is there an rpm equiv in debian?

Double clicking the .deb file opened fileroller and it failed (obviously).

I have a standard Ubuntu 5.10 breezy install with an Automatix update of most things. no other seperate updates[/QUOTE]

This thread is going at the same time as yours.  It might help to answer some of your questions.

[http://www.ubuntuforums.org/showthread.php?t=151977](http://www.ubuntuforums.org/showthread.php?t=151977)

---

### Post by Gnowm on 2006-03-29
Thanks Mustard, dpkg = rpm. You are most kind  :+)

Done and done. But it has now broken my Frostwire totally. But at least i know how to use dpkg  :+)

[HTML]unFrost.sh: line 24: syntax error near unexpected token `
'unFrost.sh: line 24: `look_for_java()
[/HTML]

is the error

---

### Post by jetpeach on 2006-03-29
Yes, I believe from 4.10.5->4.10.9 is when they fixed the 100% cpu bug.  to install the deb, see
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2523844](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2523844)
That wiki guide has a lot of other useful information to.
Unfortunately, there is one more step after that that took me a while to figure out- it's a bug the frostwire guys need to fix.  Follow the simple commands in this thread.  Hmm, there forums appear down, so here is the google cache:
[link to google cache of gnutella forums thread]("http://72.14.203.104/search?q=cache:O2v73QhqR4MJ:www.gnutellaforums.com/showthread.php%3Fthreadid%3D54234+frostwire+linux+dos&hl=en&gl=us&ct=clnk&cd=1&lr=lang_en")
It's just a simple step to change the format of one of the installed files from a DOS text file to a normal txt file- I guess somehow the deb they distribute installs the wrong file... maybe this is fixed by now, but I doubt it.
Good luck,
jet

Edit: I hadn't seen your most recent post gnowm, but now that I have I'm almost certain that is the same error I got.  It really bugs me that they release a version of Frostwire that just plain doesn't work after installing it... I'm sure it's an easy enough fix too.  Maybe I should take the initiative and repackage the deb file with the proper format of the script file in it.  Although I've never packaged a deb file, I read it isn't that hard.
Maybe tomorrow :)

---

