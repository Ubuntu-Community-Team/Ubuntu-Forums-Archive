---
title: "Updating Program"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Aspra on 2007-02-12
Id like to know how to do it for all programs but ill start with Firefox. I tryed something someone told me and it didnt mork. It just said Permission Denied. so i dont know what ot do form there.

---

### Post by teaker1s on 2007-02-12
terminal [COLOR="Red"]sudo synaptic[/COLOR]
hit reload tab
hit mark all upgrades
apply



or 

there is also **apt-get** command line


both will need sources edited if you want universe or multiverse programs installable

---

### Post by Aspra on 2007-02-12
> **teaker1s said:**
> terminal [COLOR="Red"]sudo synaptic[/COLOR]
hit reload tab
hit mark all upgrades
apply



or 

there is also **apt-get** command line


both will need sources edited if you want universe or multiverse programs installable


im guessing that theres not an update for firefox then. i did the snaptic (the only thing i knew how to do out of the things you said) and nothing came up for firefox.

---

### Post by Maestro23 on 2007-02-12
> **Aspra said:**
> im guessing that theres not an update for firefox then. i did the snaptic (the only thing i knew how to do out of the things you said) and nothing came up for firefox.

FF 2.0 is there. You need to enable extra repositories.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by teaker1s on 2007-02-13
that's the link I'd been looking for:lolflag:  if you update your repositories then your install options with synaptic will be vast:guitar: :guitar: :guitar: :guitar:

---

### Post by whitefort on 2007-02-13
> **Maestro23 said:**
> FF 2.0 is there. You need to enable extra repositories.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Um...  I've just worked my way through the instructions on that page, and I'm still only seeing  Firefox 1.5 in synaptic.  Is there some other step missing?

---

### Post by teaker1s on 2007-02-13
I find "save file as" works better rather than save 

have you hit the reload tab?


post your sources contents to this thread and we will look

---

### Post by whitefort on 2007-02-13
Hi,

First, when I type the gksudo line, I'm getting some sort of error message before the window opens:

> ~$ gksudo gedit /etc/apt/sources.list

(gedit:5904): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Anyway, disregarding that, at present my sources.list is:

>  
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main 


Then I go to synaptic and reload, but the latest Firefox I can find is still 1.5

Sorry to be such a newbie, but any advice will be much appreciated!

---

### Post by Crooksey on 2007-02-13
The best option and the fastest is to use the aptitude command.

```

crooksey@phil0d0x-64:~$ sudo aptitude upgrade firefox
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

---

### Post by whitefort on 2007-02-13
> **Crooksey said:**
> The best option and the fastest is to use the aptitude command.


Thanks, Crooksey.

Just before I do that, can I ask another newbie question?  Is there any danger this will confuse or mess up my Synaptic?

Thanks!

---

### Post by Crooksey on 2007-02-13
None at all, as Synaptic is a "front end" for apt, so all its doing is that command, but slower due to the graphical interface of the program.

For a complete list of aptitude commands

```

man aptitude
```

---

### Post by whitefort on 2007-02-13
Ok...  I did this:

> 
sudo aptitude upgrade firefox
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used. 

... and at the end of it, I still have Firefox 1.5   
Nothing downloaded, upgraded, installed. :confused:

---

### Post by Crooksey on 2007-02-13
Thats because 2.0 isnt in the repo's, you need to follow this [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

(already posted)

Then try again :)

---

### Post by whitefort on 2007-02-13
> **Crooksey said:**
> Thats because 2.0 isnt in the repo's, you need to follow this [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

(already posted)

Then try again :)

Uh, thanks again - but my original post was because I'd already tried that and it didn't work.

---

### Post by Crooksey on 2007-02-13
sudo gedit /etc/apt/sources.list

uncomment all the lines that start with "deb"

sudo aptitude update
sudo aptitude update firefox

---

### Post by whitefort on 2007-02-14
Hi, Crookesy, and thanks again for trying to help - but all the deb lines are already uncommented.  Can you see anytthing else missing in the following?

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main 


---

### Post by Crooksey on 2007-02-14
Ahh, i see you are on Dapper, Firefox 2.0 is within the edgy repo's, you can try and use mine:

```



deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
 deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
 deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb http://security.ubuntu.com/ubuntu edgy-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe

 deb http://ubuntu.beryl-project.org edgy main

```

---

### Post by teaker1s on 2007-02-14
be careful it is possible to  use different repository versions,but may break system. also when you have used the edgy repositories make sure you change back to dapper.

Could always download directly from firefox site and run it I believe ages back thats how I did it thinking about it

---

### Post by whitefort on 2007-02-14
Great!  Thanks for solving the mystery.

I have to admit, I'm a bit nervous about starting to mix Dapper and Edgy in case I break something in Dapper (I already managed to do this once already, and it's made me nervous!)

Perhaps the best way forward would be to backup all the essential stuff on this PC, then do a complete reinstall with Edgy.  Or with Feisty on the horizon, maybe I should just wait for that.

I'm a total noob to all this stuff, and the extra couple of month would give me time to do a lot more reading and learn a bit more about Linux/Ubuntu.

Thanks again for all the help!

---

### Post by Crooksey on 2007-02-14
Just do this..

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.b
sudo gedit /etc/apt/sources.list
<copy my sources then close>
sudo aptitude update
sudo aptitude update firefox
sudo cp /etc/apt/sources,list.b /etc/apt/sources.list
sudo aptitude update

```

Now its back as it was, with 2.0.

I have feisty on a test machine, not ready to use yet.

---

