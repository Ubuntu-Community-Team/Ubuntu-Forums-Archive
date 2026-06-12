---
title: "Day two - installing programmes"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by gbswales on 2007-08-08
This seems now to be one of the most baffling areas of Ubunti - with many different ways of installation. One thing seems certain - the days of double clicking "install" and a routine opening up to guide you through the process, dont as yet appear to have arrived for Ubuntu.  Or am I missing something? Is there a way to simply download an application and install it without having to understand command lines. gars tars debs and so on?  It is beginning to strike me that Ubuntu, maybe linux generally, is still not a comfortable area for beginners who do not want to know how the thing works.

Anyway some software I am looking for includes

*Instant Messaging that includes voice and video chat support for msn at least
*Easy to use video editing software for my home movies
*DVD / Video player that comes with codecs bundled so I dont have to go and look for them
*Easy to use photo editing for cropping, resizing, touching up red eye and maybe adding some pre-defined fun effects etc - the GIMP is awful and too complicated to use

Also I did find one package - truecrypt which had a dowload for ubuntu 7 - I downloaded this, extracted the folder and double clicked the deb file which reported it had installed ok - but where?? it doesnt seem to appear in the the list of programmes automatically like it would in windows - arghhh even when you think you win you lose!

Anyway dont let me give up - give me some ideas please:lolflag:

---

### Post by diatribe on 2007-08-08
try opening a terminal and typing truecrypt to run it, also if it helps just think of a .deb file as an installer heh

---

### Post by anaconda on 2007-08-08
> the days of double clicking "install" and a routine opening up to guide you through the process, dont as yet appear to have arrived for Ubuntu

Heh.. actually it is the other way around. Ubuntus repositories are a much easier,  more sophisticated and safer system than double clicking some unknown .exe installers. 

Just try to learn how to use synaptic package manager. You can also download readymade .deb file and install them by doubleclicking if you prefer..

DVD/Video players, codecs, flash and java  aren't THAT hard to install, and if you would have chosen eg. linux Mint they would have been installed by default. 

Krita is one of the good photo editing programs.

and programs wont add themselves automatically to the menu in windows either if the programmer wont make them to add themselves there. eg. not ubuntus fault.

---

### Post by mattmole on 2007-08-08
Hi,

I read an interesting article the other day about the differences between linux and windows ([http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)). Basically, because it is different doesn't mean it cannot be better and easy to use.

To install software go to System->Administration->Synaptic Package Manager (and enter password when prompted)

From this piece of software you can search for and install thousands of different packages!

For MSN, ICQ etc use GAIM, this should be preinstalled and under Applications->Internet->Gaim Internet Messenger. In later versions of Ubuntu I presume that Pidgin will be included instead of GAIM. This is the same program with a different name.

What version of Ubuntu have you got installed? I presume the latest? 7.04 (Feisty Fawn). On this versions if you click on a file and the codec isn't installed then it should prompt you for a password etc and then install it with only a few clicks needed.

For DVDs I would recommend VLC (In Synaptic search for gnome-vlc). For me the default viewer (Totem) doesn't play the audio properly.

Im not sure about the other utilities I am afraid.

Good luck with it! I hope I have helped a bit. Please post again for clarifications etc! I have been Ubuntu only now for a couple of years and I don't look back!

mattmole

---

### Post by gbswales on 2007-08-08
> **anaconda said:**
> 

and programs wont add themselves automatically to the menu in windows either if the programmer wont make them to add themselves there. eg. not ubuntus fault.

Can anyone tell me how to edit the programme menu and how to add programmes to it.

Also I have GAIM installed for MSN which seems fine for voice chat - I cant however seem to find any option for video / audio as there is in messenger - am I missing something

---

### Post by mattmole on 2007-08-08
Applications->Alacarte Menu Editor

HTH, things are pretty self explanatory in the menus!

mattmole

---

### Post by sawjew on 2007-08-08
To edit menus you just right click on the menu bar and select 'Edit Menus'.  You can't get easier than that.

PS: if you want a good site for extra software check out this link [http://www.getdeb.net/]("http://www.getdeb.net/")
All you have to do is find what you want and then click on it and it will install.  The easiest way to install software is by using "Add/Remove' (Applications>Add/Remove).  Just browse for what you want and select install and it will download and install it for you.

---

### Post by gbswales on 2007-08-08
> **mattmole said:**
> Applications->Alacarte Menu Editor

HTH, things are pretty self explanatory in the menus!

mattmole

Please - almost nothing so far has been self-explanatory:(
have no idea what HTH means
and cannot find an application called Alacarte Menu Editor
even if I could find it I am not sure where Truecrypt has installed itself (if it has)

the good news is - found VLC works fine on my divxx movies
Does anyone know software that will mount an ISO as a virtual drive - in windows I use the one from elby but I dont think they have a linux version

this is like learning to play :guitar::lolflag:

---

### Post by mattmole on 2007-08-08
Hi again.

HTH - Hope That Helps ([http://en.wikipedia.org/wiki/List_of_Internet_slang_phrases](http://en.wikipedia.org/wiki/List_of_Internet_slang_phrases)).

Have you tried right clicking on the Applications menu and clicking edit?

Im glad that VLC is working for you.

Not sure about truecrypt. Try the following link 

[http://ubuntuforums.org/showthread.php?t=149561](http://ubuntuforums.org/showthread.php?t=149561)

I found it by googling for "truecrypt ubuntu"

You will probably find that this question has been answered elsewhere on the forums. I cant help unfortunately as I have not used truecrypt before.

mattmole

---

### Post by mattmole on 2007-08-08
Out of interest, what do you want to accomplish with truecrypt?

I found this other link for how to install and use:

[http://ubuntuforums.org/showthread.php?t=199367](http://ubuntuforums.org/showthread.php?t=199367)

---

### Post by sailor2001 on 2007-08-08
amsn has video and voice support.....

---

### Post by lisati on 2007-08-08
> **anaconda said:**
> Heh.. actually it is the other way around. Ubuntus repositories are a much easier,  more sophisticated and safer system than double clicking some unknown .exe installers. 



Here I am whiling away the time on my laptop while my desktop chugs away cleaning up my wedding video......

There's one program I sometimes use on* another OS* to track down music, which is good as far as it goes. The catch is that it's loaded with spyware. Fortunately the spyware is easily removed, but doing an uninstall immediately after an install is a nuisance.

"Add/Remove Programs" is useful.....

---

### Post by forestpixie on 2007-08-08
> **gbswales said:**
> ..even if I could find it I am not sure where Truecrypt has installed itself (if it has)

if you are trying to find something you've installed, open a terminal (accessories > terminal) and use this command.
```

whereis <nameofprogram>
```


Once you've got the repos sorted - you'll find that using terminal to install is sooo much easier - than searching for a file, downloading it, then dble clicking and then answering questions - I'd rather sudo apt-get install 'program' and then y :)

> **mattmole said:**
> Hi again.

HTH - Hope That Helps ([http://en.wikipedia.org/wiki/List_of_Internet_slang_phrases](http://en.wikipedia.org/wiki/List_of_Internet_slang_phrases)).


I'd never seen that page before - Godwin's Law had me spitting tea at the screen :D

---

### Post by Nekiruhs on 2007-08-08
The linux truecrypt is CLI only. You can install forcefield which is a GUI for it.
Go to System > Prefences > Main Menu to edit the menu.
To install things, go to Applications > Add/Remove or System > Administration > Synaptic Package Manager

---

### Post by mattmole on 2007-08-08
I also much prefer the terminal for installing software. To me things can just be done so much quicker!

---

### Post by capink on 2007-08-08
[http://www.youtube.com/watch?v=AYuXRLdPQvg]("http://www.youtube.com/watch?v=AYuXRLdPQvg")

---

### Post by philinux on 2007-08-08
I can remember poking about in win 95 for the first time. nothing was self explanatory. But now with poking about for a few years I haven't found Ubuntu hard at all. Right click context stuff just the same. Things just work. 
Synaptic is great cos you know its safe and if you find something else that has a .deb file thats just the same as setup.exe could not be simpler. It's just different! :lolflag:

---

### Post by Hospadar on 2007-08-08
If you are looking for apps to do stuff on ubuntu, I would start with the add/remove applications in Applications->Add/remove applications (make sure in the top right corner you select "all open source applications") try searching for "photo editing"/"video editing".  just about any basic program you might need is in here somewhere, and if it's not there, you can go to System->Administration->Synaptic and search there, this interface is a little more detailed the add/remove programs, but it does the same thing.

Most applications will add themselves automatically to the menu when installed this way.

Also, if you do install a program without one of these tools, and you need to manually add it to the menu, the executable you want to target with the shortcut is probably going to be in /usr/bin, or /bin (or perhaps in your home folder if not there) and the executable will probably be named after the program.

good luck!

---

