---
title: "About installing games"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by Fibre on 2005-12-17
Had my first stab at installing a game the other night and thought I had done well but after reading about someone elses problems found out I mustn't have done it right or it's not quite completed yet or something.

My 1st attempt was through Synaptic Package Manager the chosen game was 3DChess ? In the forum I read the person suggested to someone that if it isn't in applications then it's not installed. When I go to Synaptic there is only the choice to re-install or remove so I must be only half way there. It's not to be found on my pc.

If I'm having problems with this, I think I'm going to have heaps of problems when it comes to installing Native and Non-Native games. There are a few that I'd like to try. 

It seems there are a few programs involved with installing games relating to .exe to get them going. Online repositories I'm assuming is what I need to access as spoken of here - [http://www.psychocats.net/linux/installingsoftware.ph](http://www.psychocats.net/linux/installingsoftware.ph)

But I also read about another program relating to xwine and I think CVR is its name for the newer version of the program to install or execute the game? Which also had some negative things to say about the later of the two in relation to an old and new version of the main program which the name has slipped my mind for the moment.

I installed the latest drivers for the ATI graphics and my sound only works sometimes after booting, which I'm plum worn out trying to find a solution to, I tried something the other night to solve the problem and I thought it worked but then I entered a bit of script in my terminal relating to a simulation flight game on the game section of forum and when I enter the scipt it stated something about reverting back to the previous setup of my sound so whether it worked or not I'll never know and can't find where I got it from now ? This flight simulation game is somewhere to I'm guessing, but I don't see it. LOL

Installation Instructions:

* Add universe repository. Instructions at UbuntuGuide.org
* Refresh apt-get (i didn't know how to do that I just entered the code in my terminal)
Code:

sudo apt-get update

* Install
Code:

sudo apt-get install gl-117

I'm not sure if I had done the Universe repository stuff before and couldn't find it again anyway. I looked at the place suggested above the script but with out luck at least not the name of the **universal repository** stated?

I hope someone can help me get clarity even if it's just pointing me to some sites and letting me take it from there. There are some mixed messages in relation to what works and what doesn't and I think I've over stepped myself in knowing where I'm at.

Which programs are the most relaible for Native games, Non-Native?

Do I just follow this page and thats it for both software and games I'm assuming not - 
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)
Installing Software in Ubuntu

I've enabled extra repositories? is that the universal repository I guess not :( 

How do I make sure I've installed programs and games correctly or have I missed a step in the hole thing? I thought I was doing fine but I'm really not, there's a few things that need to be installed and scipting relating to it. But I'm not sure what exatly whether there is something relating to debian as well as some kind of game exe programs for both native and non-native - don't get me wrong I think ubuntu is good it's just this learning curve that's proving to be a challenge for me.

I understand it has to be this way even with windows it took me months before I could see what hardware i had or the size of the hardware ram size etc. 

Although it was easier to grasp with the knowledge I already have it probably is more just like learning windows all over again. I'm not giving up just venting my lack of knowledge LOL

And the other problem is the other partitions I have that I can't see, another O/S ntfs and a 6gb FAT32 formated partition I made up at the same time as ubuntu for extra storage for both systems?

But I can probably find and sought that out through searching the forums eventually on my own.

In closing at long last LOL the best solution for installing / executing native and non-native and software?

And where to / how to check what I've installed or where I've gone wrong?

That 3dchess and flight simulator have to be somewhere ? :confused: :rolleyes: :???: 

Any help as usual is much thanked

---

### Post by paulmilliken on 2005-12-17
[QUOTE=Fibre]Had my first stab at installing a game the other night and thought I had done well but after reading about someone elses problems found out I mustn't have done it right or it's not quite completed yet or something.

My 1st attempt was through Synaptic Package Manager the chosen game was 3DChess ? In the forum I read the person suggested to someone that if it isn't in applications then it's not installed. When I go to Synaptic there is only the choice to re-install or remove so I must be only half way there. It's not to be found on my pc.

If I'm having problems with this, I think I'm going to have heaps of problems when it comes to installing Native and Non-Native games. There are a few that I'd like to try. 

It seems there are a few programs involved with installing games relating to .exe to get them going. Online repositories I'm assuming is what I need to access as spoken of here - [http://www.psychocats.net/linux/installingsoftware.ph](http://www.psychocats.net/linux/installingsoftware.ph)

But I also read about another program relating to xwine and I think CVR is its name for the newer version of the program to install or execute the game? Which also had some negative things to say about the later of the two in relation to an old and new version of the main program which the name has slipped my mind for the moment.

I installed the latest drivers for the ATI graphics and my sound only works sometimes after booting, which I'm plum worn out trying to find a solution to, I tried something the other night to solve the problem and I thought it worked but then I entered a bit of script in my terminal relating to a simulation flight game on the game section of forum and when I enter the scipt it stated something about reverting back to the previous setup of my sound so whether it worked or not I'll never know and can't find where I got it from now ? This flight simulation game is somewhere to I'm guessing, but I don't see it. LOL

Installation Instructions:

* Add universe repository. Instructions at UbuntuGuide.org
* Refresh apt-get (i didn't know how to do that I just entered the code in my terminal)
Code:

sudo apt-get update

* Install
Code:

sudo apt-get install gl-117

I'm not sure if I had done the Universe repository stuff before and couldn't find it again anyway. I looked at the place suggested above the script but with out luck at least not the name of the **universal repository** stated?

I hope someone can help me get clarity even if it's just pointing me to some sites and letting me take it from there. There are some mixed messages in relation to what works and what doesn't and I think I've over stepped myself in knowing where I'm at.

Which programs are the most relaible for Native games, Non-Native?

Do I just follow this page and thats it for both software and games I'm assuming not - 
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)
Installing Software in Ubuntu

I've enabled extra repositories? is that the universal repository I guess not :( 

How do I make sure I've installed programs and games correctly or have I missed a step in the hole thing? I thought I was doing fine but I'm really not, there's a few things that need to be installed and scipting relating to it. But I'm not sure what exatly whether there is something relating to debian as well as some kind of game exe programs for both native and non-native - don't get me wrong I think ubuntu is good it's just this learning curve that's proving to be a challenge for me.

I understand it has to be this way even with windows it took me months before I could see what hardware i had or the size of the hardware ram size etc. 

Although it was easier to grasp with the knowledge I already have it probably is more just like learning windows all over again. I'm not giving up just venting my lack of knowledge LOL

And the other problem is the other partitions I have that I can't see, another O/S ntfs and a 6gb FAT32 formated partition I made up at the same time as ubuntu for extra storage for both systems?

But I can probably find and sought that out through searching the forums eventually on my own.

In closing at long last LOL the best solution for installing / executing native and non-native and software?

And where to / how to check what I've installed or where I've gone wrong?

That 3dchess and flight simulator have to be somewhere ? :confused: :rolleyes: :???: 

Any help as usual is much thanked[/QUOTE]


You may have installed 3dchess fine.  It is possible that you have to type the name of the program on the command line to run it.

Chances are that the program was insalled in /usr/bin or /usr/local/bin.

Paul

---

### Post by Fibre on 2005-12-17
Thanks for the reply I was beginning to think I wouldn't get an answer.

I'm still thick with this - so what would be the script for that - I should probably have a better understanding by now but I don't.

This is what it says in properties installed files:-

/.
/usr
/usr/games
/usr/games/3Dc
/usr/share
/usr/share/doc
/usr/share/doc/3dchess
/usr/share/doc/3dchess/README
/usr/share/doc/3dchess/TODO
/usr/share/doc/3dchess/ACKNOWLEDGEMENTS
/usr/share/doc/3dchess/3Dc-rules.html
/usr/share/doc/3dchess/copyright
/usr/share/doc/3dchess/changelog.gz
/usr/share/doc/3dchess/changelog.Debian.gz
/usr/share/man
/usr/share/man/man6
/usr/share/man/man6/3Dc.6.gz
/usr/lib
/usr/lib/menu
/usr/lib/menu/3dchess

If that helps at all, is it somehow through terminal/ apt get something or other as it's stated somewhere about opening software? if so I can probably work it out. I'll go have a look now and come back again.

Also do you think it's the same with the simulation game I spoke about also?

Thanks Paul, appreciate it. I think I might stick with native games for now I'm starting to look there at the moment and popped back here to see what was going on with this thread, thank you.

---

### Post by Fibre on 2005-12-17
so does paul mean just :-

sudo apt-get update

enter

sudo apt-get install /usr/games/3Dc

In the terminal or is there something I'm not seeing ???

And also can it hurt if I was to try something like that with out the knowledge first or it just won't work and no harm will come to my system ??

---

### Post by aragorn2909 on 2005-12-17
Your 3DChess is there, its installed properly, its just that /usr/games is not in your PATH, so typing 3Dc will do nothing.  All you need to do is type in terminal ```
/usr/games/3Dc
```

---

### Post by Fibre on 2005-12-17
I typed it in and got -

                                                         :~$ /usr/games/3Dc
3Dc version 0.8.1, Copyright (C) 1995,1996 Paul Hicks
3Dc comes with ABSOLUTELY NO WARRANTY: see the GPL file for details
This is free software: you are welcome to redistribute it
    under certain conditions (see the GPL file).
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
X connection to :0.0 broken (explicit kill or server shutdown).

It appears but I also get this stuff??

Does this mean I should perhaps re-install the program?

---

### Post by DigitalAxis on 2005-12-17
Does the game load at all?  I just installed it on Kubuntu Breezy to check, and it didn't show up in my normal menus either.  I do have a weird Debian menu that came from nowhere, and it's listed there... I suspect 3D Chess is putting its menus somewhere else.

It looks like the errors are related to X server fonts, you might want to consider installing the xfonts packages (search Synaptic for them) if they're not already installed.

---

### Post by DigitalAxis on 2005-12-17
As for your question about enabling other repositories, what you need to do is open Synaptic, go to the Settings menu, then Repositories, and then  find the one that says "Ubuntu 5.10 "Breezy Badger" (Binary).

If you find one that has "Community maintained (Universe)" below its name, you've got the Universe repository enabled.
(see [https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

I'm fairly sure 3D Chess is in the Universe repository though, so I think you've already got it enabled.

As for your drives, Linux still doesn't get along well with NTFS.  The FAT32 drive you made ought to be somewhere in /media if you set up Ubuntu to automount it.  
Try the 'disks-admin' program.  It should list all the storage on your drive, and the partitions on each.  You'll be able to see where they're mounted, if they  have mount points set up.
**BE CAREFUL** with disks-admin.  You have to run it as superuser, which means you'll have unrestricted access to your system.  Personally, I'd just make note of what it tells me and not touch anything.

---

### Post by Fibre on 2005-12-18
where do I look for /media I've got no idea lol.

I'd like it to appear in places/computer if possible.

I want to use it to save stuff to while I'm trying to work things out. 
Save info I'm picking up along the way and apps so that if I stuff up they'll be there as back up.

thanks for the replies DigitalAxis.

I  installed automatix and it saved me alot of installs etc - not sure if its good for Kubuntu but it's worth a look if you havn't looked at it yet. it's in here

[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295) big thanks to **Arnieboy**

---

