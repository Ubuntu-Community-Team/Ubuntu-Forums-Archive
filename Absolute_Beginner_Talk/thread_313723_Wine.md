---
title: "Wine"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2006-12-06
Hi i am really trouble in wine. plz give me the exact link for my Ubuntu 6.06 LTS (Dapper Drake) version. i am try several link but he said package not compatible or out of date.:confused:

---

### Post by an.echte.trilingue on 2006-12-06
It is in the repositories.

```
sudo apt-get install wine
```

Good Luck!
-mat

---

### Post by loyeyoung on 2006-12-06
For a more recent, "bleeding edge" version, copy and paste the following into your /etc/apt/sources.list file. Wine is definitely a work-in-progress, so I'm finding the backport to be better than the "official" in the repository.

> 
## Backport of wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

---

### Post by lucky_chouhan on 2006-12-06
i am try both option give me 10 minutes.

---

### Post by lucky_chouhan on 2006-12-06
1. sudo apt-get install wine

lakhan@root-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate


what i do:( :(

---

### Post by bodhi.zazen on 2006-12-06
[Enable repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Then:```
sudo aptitude update && sudo aptitude install wine
```

You can apt-get if you like.

---

### Post by lucky_chouhan on 2006-12-06
i am get this

lakhan@root-desktop:~$ aptitude update && aptitude install wine
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Couldn't lock list directory..are you root?
lakhan@root-desktop:~$ cd root
bash: cd: root: No such file or directory
lakhan@root-desktop:~$ root
bash: root: command not found
lakhan@root-desktop:~$

---

### Post by bodhi.zazen on 2006-12-06
:lol: You need to sudo that:```
**sudo** aptitude update && **sudo** aptitude install wine
``` 

:lol: root is not a directory, root is the ultimate administrative user.

[Root vs. sudo](https://help.ubuntu.com/community/RootSudo)

Although there is a directory /root, this is root's home directory not to be confused as the root user.

8)

---

### Post by S1NGH on 2006-12-06
> **lucky_chouhan said:**
> i am get this

lakhan@root-desktop:~$ [COLOR=Magenta]**aptitude update && aptitude install wine**[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Couldn't lock list directory..are you root?
lakhan@root-desktop:~$ cd root
bash: cd: root: No such file or directory
lakhan@root-desktop:~$ root
bash: root: command not found
lakhan@root-desktop:~$

Hey Lakhan Chouhan,

you forgot to add the sudo command if front of the command.
you should do it like this:

```
sudo aptitude update && aptitude install wine
```

cheers ;)

---

### Post by S1NGH on 2006-12-06
[bodhi.zazen]("http://www.ubuntuforums.org/member.php?u=89054"),
it looks like you beat me to it, and i don't think you need the other sudo command in it.

---

### Post by lucky_chouhan on 2006-12-06
i get this - 

lakhan@root-desktop:/$ sudo aptitude update && sudo aptitude install wine
E: Malformed line 65 in source list /etc/apt/sources.list (dist)
E: Malformed line 65 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.:(

---

### Post by bodhi.zazen on 2006-12-06
> **S1NGH said:**
> [bodhi.zazen]("http://www.ubuntuforums.org/member.php?u=89054"),
it looks like you beat me to it, and i don't think you need the other sudo command in it.

Hey, thanks for that tip. I have never tried it without both sudo but I'll check it out.

You post was more [color=red]c[/color][color=blue]o[/color][color=green]l[/color][color=brown]o[/color][color=pink]r[/color][color=darkred]f[/color][color=yellow]u[/color][color=cyan]l[/color]

---

### Post by bodhi.zazen on 2006-12-06
> **lucky_chouhan said:**
> i get this - 

lakhan@root-desktop:/$ sudo aptitude update && sudo aptitude install wine
E: Malformed line 65 in source list /etc/apt/sources.list (dist)
E: Malformed line 65 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.:(

LOL post the contents of /etc/apt/sources.list

---

### Post by lucky_chouhan on 2006-12-06
Here is the content - 



deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free                                               
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

deb [http://wine.sourceforge.net/apt/binary/](http://wine.sourceforge.net/apt/binary/)

:( :( :(

---

### Post by bodhi.zazen on 2006-12-06
Comment out this line, so it looks like this:

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

and re-try

It could also be the plf repositories....

---

### Post by S1NGH on 2006-12-06
> **bodhi.zazen said:**
> Hey, thanks for that tip. I have never tried it without both sudo but I'll check it out.

You post was more [COLOR=red]c[/COLOR][COLOR=blue]o[/COLOR][COLOR=green]l[/COLOR][COLOR=brown]o[/COLOR][COLOR=pink]r[/COLOR][COLOR=darkred]f[/COLOR][COLOR=yellow]u[/COLOR][COLOR=cyan]l[/COLOR]
lol... it was nothing :P

:rolleyes:

---

### Post by lucky_chouhan on 2006-12-06
as you say bodhi.zazen i do but result is nothing.

lakhan@root-desktop:~$ sudo aptitude update && sudo aptitude install wine
E: Malformed line 65 in source list /etc/apt/sources.list (dist)
E: Malformed line 65 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
](*,)

---

### Post by S1NGH on 2006-12-06
> **lucky_chouhan said:**
> as you say bodhi.zazen i do but result is nothing.

lakhan@root-desktop:~$ sudo aptitude update && sudo aptitude install wine
E: Malformed line 65 in source list /etc/apt/sources.list (dist)
E: Malformed line 65 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
](*,)

hmm, was that the whole file's content you posted, word for word?
the error states that the line 65 is malformed/incorrect/[anything you want to put here]

therefore, try counting right from the top of the file, the very first line till you get to line 65, remember blank lines should also be counted and finally try commenting that line out...

---

### Post by bodhi.zazen on 2006-12-06
> **S1NGH said:**
> hmm, was that the whole file's content you posted, word for word?
the error states that the line 65 is malformed/incorrect/[anything you want to put here]

therefore, try counting right from the top of the file, the very first line till you get to line 65, remember blank lines should also be counted and finally try commenting that line out...

```
cat -n /etc/apt/sources.lst | grep 65
```Should show us the offending line.

Of course you can count if you prefer ;)

---

### Post by lucky_chouhan on 2006-12-06
thanks S1NGH's now finally i run the  wine setup

thank you all of you for supporting me..
:) :) :) :) :) :) :) :)

---

### Post by lucky_chouhan on 2006-12-06
finally i am install internet download manager, real player, du meter, winamp, acrobat reader 7  lots more.

100% work fine.

Thanks Again All Ubuntu Users.

Happy X'.mas:KS :KS

---

### Post by tophatandy on 2006-12-06
really lost when it comes to wine..


repos says that I have it..

now i need to know how to use it so i can install some windows apps.

---

### Post by bodhi.zazen on 2006-12-06
> **tophatandy said:**
> really lost when it comes to wine..


repos says that I have it..

now i need to know how to use it so i can install some windows apps.

[How to wine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by lucky_chouhan on 2006-12-07
for installing & trouble wine see the stating of thread.

and use here is command.

lucky@root#wine realplayer.exe

setup is run in gui mode (exactly like windows.)

---

### Post by S1NGH on 2006-12-07
> **bodhi.zazen said:**
> ```
cat -n /etc/apt/sources.lst | grep 65
```Should show us the offending line.

Of course you can count if you prefer ;)

Thanks for the tip, could have made my life easier when i first got Ubuntu too lol :P

---

### Post by S1NGH on 2006-12-07
> **lucky_chouhan said:**
> thanks S1NGH's now finally i run the  wine setup

thank you all of you for supporting me..
:) :) :) :) :) :) 

No problem, glad to see that you are happy and joining the Ubuntu community :-D

---

