---
title: "Wine (Windows Emulator)"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-08-05
I Am wanting to play my games on Ubuntu Linux, and have heard that Wine would do just that. 
However, could you tell me the capabilities of it, would it run complex games, Such as RollerCoaster Tycoon 2, Or just really old Basic, barely 3D games.

Also, can someone provide me with the entire Sudo command i need to get the package i type into Terminal.

Thanks Alot!

---

### Post by Captain Kirk76 on 2006-08-05
Bump

---

### Post by mustang on 2006-08-05
> **Captain Kirk76 said:**
> I Am wanting to play my games on Ubuntu Linux, and have heard that Wine would do just that. 
However, could you tell me the capabilities of it, would it run complex games, Such as RollerCoaster Tycoon 2, Or just really old Basic, barely 3D games.



You're going to have to look this up. Support is full for some and lacking for others. I would suggest searching first on the ubuntu forums for the game you're looking for. If no luck, try google.



> 
Also, can someone provide me with the entire Sudo command i need to get the package i type into Terminal.

Thanks Alot!

I'm guessing you're asking the command to get wine? If so, look here:

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by 3rdalbum on 2006-08-05
If you want to try playing games on Ubuntu, you should check out [Transgaming Cedega]("http://www.transgaming.com/index.php?module=ContentExpress&file=index&func=display&ceid=29"). It is a commercial fork of WINE which is designed for games. A subscription costs a certain amount of money but the CVS version is free... since you're new to Linux it would be much easier for you to buy the subscription. (the CVS version relies on the command-line).

Sometimes WINE works perfectly out-of-the-box with a particular program. Sometimes you need to install Windows DLLs for it to work. Some programs won't work at all.

In order to get WINE, here is what you must do:

```

sudo nano /etc/apt/sources.list

```

Add the following line to the end of the file:

```
deb http://wine.budgetdedicated.com/apt dapper main
```

Press Control-X, the Y key, then Enter. Now type:

```

sudo apt-get update
sudo apt-get install wine

```

That will download and install the *latest* version of WINE. From there, you should go to the Wine HQ website to find out how to use it. Good luck.

(By the way, if you want to play any ID Software games on Linux, there are native versions available).

---

### Post by Captain Kirk76 on 2006-08-05
I dont mean to be a complete n00b, but if i require these windows  .DLL's where would i find them? If it helps, i do have MS Windows XP Home installed, Its a Double OS System i use.

---

### Post by Captain Kirk76 on 2006-08-05
Okay, i got Wine installed, i clicked on my Game's .exe and i get NoCD/DVD Drive detected!!! Yet Ubuntu recognized when i inserted the disc!

Ideas?

---

### Post by Captain Kirk76 on 2006-08-05
Bump

---

### Post by Captain Kirk76 on 2006-08-05
This isnt going well...
BUMP!

---

### Post by jimmygoon on 2006-08-05
What game?

---

### Post by Captain Kirk76 on 2006-08-05
RollerCoaster Tycoon 2
Says No CD/*DVD Drive found, yet Ubuntu recoognized the CD when i inserted the CD.

Theme Hospital
Unable to load Language Files

StarTrek:Armada 2 
Wont even attempt this one...

---

### Post by Linux4HumanBeings on 2006-08-05
How do you know if you ahve wine?

---

### Post by Jjohn on 2006-08-05
Did you do:
<winecfg> in the terminal? If not you may need to.
then if you do:
<wine> it will give you the commands for wine
regards John

---

### Post by Captain Kirk76 on 2006-08-05
Forget Terminal! I found it in Add/Remove aafter i enabled all the extras, so in the end i didnt do any terminal inputs. Also it ounds like i hae to get Wine from the terminal, instead of double clicking on the exe file?

---

### Post by TFX360 on 2006-08-05
What's that Bump thing?

---

### Post by Captain Kirk76 on 2006-08-05
pardon?

---

### Post by bobpur on 2006-08-05
Get Automatix. Wine can be installed from there.

---

### Post by Linuturk on 2006-08-05
I got the same message in the beginning "No CD Detected"

Go to a terminal, and type 

winecfg

Under the drives tab, hit autodetect.

Your D: drive should be set to /media/cdrom0 or something similar.

Highlight the D: drive, and click the Advanced Button.

There is a dropdown box where you select the type of drive it is. You will want to select CD-ROM

---

### Post by Captain Kirk76 on 2006-08-06
I get this error can't create mcop directory

---

### Post by Captain Kirk76 on 2006-08-06
bump

---

### Post by Kurt` on 2006-08-06
If I recall, in ~/.wine/dos_devices/ there should be a C: symlink. What I did was put my CD in my drive, then symlink it to the dos_devices folder.

e.g.:

# ln -s /media/cdrom0 ~/.wine/dos_devices/D:

Then when <your game> tries to read the cd-rom drive, it actually reads from the folder where your cd-rom is mounted. ;)

Not sure if that's the proper way to do it, but I had Starcraft and Morrowind working under WINE that way.

You may need to install a no-cd crack to get the game working, as certain Win32 API calls (GetDriveTypeA() particularly) may not work correctly being run under WINE. megagames.com has a large section under "Game Fixes", watch out for all the ads though.

---

### Post by Captain Kirk76 on 2006-08-06
May i ask, does anything in Ubuntu Actually work? 

Wine Wont work any program ive tried, even with cracks for no-CD

---

### Post by Captain Kirk76 on 2006-08-06
Bump!

---

### Post by qrm on 2006-08-06
ive had photoshop running on wine and atm i have WoW running on it

---

### Post by Bagnaj97 on 2006-08-06
To see how well a program runs using Wine check [http://appdb.winehq.org/](http://appdb.winehq.org/) It's a database of windows apps and how well they run under wine, it's usually fairly up to date.

---

### Post by Captain Kirk76 on 2006-08-07
Im afraid im not convinced, it says here that StarTrek Armada 2 works on it [http://appdb.winehq.org/votestats.php](http://appdb.winehq.org/votestats.php)
Yet i cant get it to work.

---

### Post by Upochapo on 2006-08-07
captain, if you click on the link at the bottom of the wine application database, that tells you that that list is only for programs one would like to see run on wine.  this does not necessarily mean that it will run.  It's a way for the end user to have a say in what programs they would like to see wine support.


here is the link you need to know which apps will run on wine in ubuntu:

[http://appdb.winehq.org/distributionView.php?iDistributionId=163]("http://appdb.winehq.org/distributionView.php?iDistributionId=163")
also, it looks as if it is bronze, meaning it will run but has a tendency to crash.

---

### Post by Captain Kirk76 on 2006-08-07
Thankyou for Clearing that up, Anoter question, can i run it from my NTFS Partition, the same install Windows uses, or install in Ubuntu, ive tried both, but nothing workss for me, ive tried Theme Hospital, which is platinum, but doesnt work.

---

### Post by Captain Kirk76 on 2006-08-07
bump......Again

---

### Post by jamespi on 2006-08-07
try this for the mcop thing:

mkdir ~/.kde/socket-ubuntu

it may/may not work. i just found it by using google, this isnt a problem i've encountered personally so i can't vouch for its effectiveness. 

its worth bearing in mind wine isnt a plug-and-play type of application, you really do have to mess about to get the vast majority of things to run with wine so don't expect an easy ride.

---

### Post by Captain Kirk76 on 2006-08-07
> you really do have to mess about to get the vast majority of things to run

Alo appears thats true in EVERYTHING for Ubuntu

---

