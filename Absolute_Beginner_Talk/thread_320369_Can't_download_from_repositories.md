---
title: "Can't download from repositories"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by steveandarchie on 2006-12-17
Hello all, I'm using edgy and I have followed the instructions here: [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
for enabling extra repositories.

Since then I can't install anything, the following error message comes up on 'add/remove programs'

E: The package flashplayer-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

It also comes up on Synaptic. It looks like I'm stuck. It seems the problem is a flash standalone .swf program that I tried to download (unsuccessfully) but I have tried to purge this and can't.

Any ideas for sorting this out or resetting the whole thing? Sorry if it's a dumb question.
Thanks

---

### Post by maxamillion on 2006-12-17
did you get an error when doing "sudo aptitude update" or "sudo apt-get update"? (depending on which one you use)

---

### Post by deadgobby on 2006-12-17
Please copy and paste your repo listing here.  You have a back up copy if you followed cats directions and easy to restore.
GObby

---

### Post by steveandarchie on 2006-12-17
Thanks all, when I input [COLOR="SandyBrown"]sudo aptitude update[/COLOR] I get:

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

#deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free
#deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free 

I also came across this:

[   ]:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
[    ]:~$ gksudo gedit /etc/apt/sources.list

(gedit:28477): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Many thanks again - Have to log out now but I'll be back a bit later

---

### Post by dannystaple on 2006-12-17
> **deadgobby said:**
> Please copy and paste your repo listing here.  You have a back up copy if you followed cats directions and easy to restore.
GObby

That is, paste both your sources.list, and the sources.list_backup you should have.

It may be worth restoring the backup, and enabling the additional sources from the Gui in aptitude if you are not entirely comfortable with deb sources. The synaptic Gui has simple tick boxes for most of the standard repos - Universe, multiverse, security updates, backports etc. You should also be able to change the base server for these so you can get a local one.

Start synaptic with System->Administration->Synaptic Package Manager. To add new repos, go to Settings->repositories. 

You can also set the repositories via System->Administration->Software Sources which will take you to the same dialog.

There you will see a country selection "Download from" (mine is set to server from the UK), as well as Tick boxes for main, universe, multiverse and restricted. I generally uncheck the CD-rom listing as well so I don't have to insert it again. In the updates tab, you can enable, and disable updates. Backports are your call, if you want a seriously solid system, it is probably best left alone, if you want the latest and greatest (nearly) then backports is for you. 

There is a "third party repositories" tab. As for completely third party repos not listed there, you should really not be adding them unless you are pretty experienced with Debian systems, and are prepared for the world of pain which can come from third party repos. I am speaking here from bitter experience of package database messes caused by using third party repos.

In the authentication tab, you can import keys that are used to sign packages in the repos. In the statistics tab, it allows you to participate in a survey of packages installed so the maintainers know which parts are more popular.

---

### Post by Sef on 2006-12-17
> Any ideas for sorting this out or resetting the whole thing? Sorry if it's a dumb question.
Thanks
Reply With Quote

It is not a dumb question.  Please post any question you have here concerning your problems with ubuntu.

---

### Post by steveandarchie on 2006-12-17
Thanks all, I'm feeling pretty dumb - I don't know what the sources list backup is - I think I posted the sources list above. I followed the instructions on the link and tried the trouble shooting but I have just been cutting and pasting (and unfortunately deleting) where I have been told. I didn't backup anything before I started the process because I'm not used to Ubuntu folding in this way - only been at it a week or two though - lesson number 1 of the day learned.

When I try to access Synaptic now I get this:

E: The package flashplayer-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

So I can't access anything. If I get past that error message then there is nothing there. The error started as a dpkg error and seems to have grown into something serious. Is there simple way of starting from scratch? I need a video cd creator pretty soon and it looks like I'll have to reinstall the whole show (again).

It's a bit frustrating following instructions to the letter and wiping out a major part of what I like about Ubuntu:( . Danny, I think I have entered the third party world of pain:-D

---

### Post by dannystaple on 2006-12-17
> **steveandarchie said:**
> Thanks all, I'm feeling pretty dumb - I don't know what the sources list backup is - I think I posted the sources list above. I followed the instructions on the link and tried the trouble shooting but I have just been cutting and pasting (and unfortunately deleting) where I have been told. I didn't backup anything before I started the process because I'm not used to Ubuntu folding in this way - only been at it a week or two though - lesson number 1 of the day learned.

When I try to access Synaptic now I get this:

E: The package flashplayer-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

So I can't access anything. If I get past that error message then there is nothing there. The error started as a dpkg error and seems to have grown into something serious. Is there simple way of starting from scratch? I need a video cd creator pretty soon and it looks like I'll have to reinstall the whole show (again).

It's a bit frustrating following instructions to the letter and wiping out a major part of what I like about Ubuntu:( . Danny, I think I have entered the third party world of pain:-D
The problem with following instructions to the letter, is it depends on who's instructions. I think it may be time to go back to basics a bit.

Go to System->Administration->Software Sources.

Now click on the Third Party tab, and remove ALL ENTRIES in there. Now click on the Ubuntu 6.10 Tab, and make sure that a server appropriate to your location is in the "Download From" box.
Then enable Universe, main, multiverse and restricted.

Click on Internet updates Make sure you have enabled "Important Security updates", "Recommended Updates" and probably not proposed or backported.
Click on the authentication tab, and make sure that only 2 keys show - The CD Image signing key, and the Ubuntu Archive Automatic signing key. Delete the rest. 
Click close.

Now try to open synaptic, and click the reload button to get it to pick up the repos, it may refuse.
If so, start a terminal, and do "sudo apt-get update" to get it to take the changes. Try opening synaptic again. If it still refuses, it may be time to wipe out the flashplayer-nonfree package on your system, and install it again later.

You can wipe it out with "sudo dpkg --purge flashplayer-nonfree", and then try to start synaptic. Let me know how you did...

---

### Post by steveandarchie on 2006-12-17
Cheers Danny, back to basics is probably what I need - I was in a rush (lesson number 2 of the day) to get the video cd creator (did it on win XP in the end). The site that I picked the instructions up from looked ok but it's left me high and dry a bit. To be fair the flashplayer was hanging around since yesterday but it only caused problems when I started messing around with the repositories.

When closing the 'software sources' after those steps I got the flashplayer error again but I carried on.

At <sudo dpkg --purge flashplayer-nonfree> I get this:

dpkg: error processing flashplayer-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplayer-nonfree

I then get the flashplayer error again in Synaptic. It looks like one of those awful windows apps that you can't properly install and then can't uninstall because you can't properly install it ......

---

### Post by dannystaple on 2006-12-17
> **steveandarchie said:**
> Cheers Danny, back to basics is probably what I need - I was in a rush (lesson number 2 of the day) to get the video cd creator (did it on win XP in the end). The site that I picked the instructions up from looked ok but it's left me high and dry a bit. To be fair the flashplayer was hanging around since yesterday but it only caused problems when I started messing around with the repositories.

When closing the 'software sources' after those steps I got the flashplayer error again but I carried on.

At <sudo dpkg --purge flashplayer-nonfree> I get this:

dpkg: error processing flashplayer-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplayer-nonfree

I then get the flashplayer error again in Synaptic. It looks like one of those awful windows apps that you can't properly install and then can't uninstall because you can't properly install it ......

Okay - maybe it is time to force its hand a little.
```
sudo dpkg --force-remove-reinstreq --purge flashplayer-nonfree
```

---

### Post by steveandarchie on 2006-12-17
Thanks again:-D 

Here's what I get with that command.......

[INDENT][/INDENT]dpkg - warning, overriding problem because --force enabled:
 [INDENT][/INDENT]Package is in a very bad inconsistent state - you should
 [INDENT][/INDENT]reinstall it before attempting a removal.
[INDENT][/INDENT](Reading database ... 
[INDENT][/INDENT]dpkg: serious warning: files list file for package `flashplayer-nonfree' missing, [INDENT][/INDENT]assuming package has no files currently installed.
[INDENT][/INDENT]96704 files and directories currently installed.)
[INDENT][/INDENT]Removing flashplayer-nonfree ...

Yikes:o , that looks serious

---

### Post by steveandarchie on 2006-12-17
Thanks again:-D 

Here's what I get with that command.......

[COLOR="Orange"]dpkg - warning, overriding problem because --force enabled:
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `flashplayer-nonfree' missing, assuming package has no files currently installed.
96704 files and directories currently installed.)
Removing flashplayer-nonfree ...[/COLOR]

...and then I'm returned to the $ promt

Yikes:o , that looks serious

---

### Post by Bachstelze on 2006-12-17
The package was removed the hard way. Can you install other stuff now ?

---

### Post by steveandarchie on 2006-12-17
HOLD ON...........:cool: 

Just tried Synaptic and it looks like I'm back where I began - repositories there and no error messages. Flashplayer is in the trash and I'll try not to rush and adopt a more methodical approach in future.

You're a star:KS

---

### Post by steveandarchie on 2006-12-17
All sorted - many thanks;) :D

---

