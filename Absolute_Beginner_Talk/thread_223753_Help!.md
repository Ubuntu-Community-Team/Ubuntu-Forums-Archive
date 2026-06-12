---
title: "Help!"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2006-07-26
Ok...I was trying to remove an application I had added (xmmm) and suddenly everything froze...and the computer rebooted..now im having all sorts of problems.  First, the 'updates' icon is there..up by the time, and when i mouse over it say:

"A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: 'Error: Opening the cache (E:Encountered a section with no package: header, E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.)' "

I try running the Paclage Manager as suggested, but the only thing it does is give me an empty list, and the three errors mentioned above. I also attempted to go to the Add/Remove part, and get the following error:

"This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'."


HELP! please...what did i do? what can i do to fix it?

---

### Post by abowman on 2006-07-26
Did you check the sources.list file?
Post the contents of it if it still exists.

---

### Post by ndyguy on 2006-07-26
> **bladefallcon said:**
> 
I try running the Paclage Manager as suggested, but the only thing it does is give me an empty list, and the three errors mentioned above. I also attempted to go to the Add/Remove part, and get the following error:

"This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'."


HELP! please...what did i do? what can i do to fix it?

I'm not really sure what happened, but it sounds like something may have corrupted your sources.list (like something added an invalid repository).  This might help:

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by bladefallcon on 2006-07-26
> **abowman said:**
> Did you check the sources.list file?
Post the contents of it if it still exists.

# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by T700 on 2006-07-26
What version of Ubuntu are you running?

Also, just FYI, it is best to give your question a descriptive title rather than, "Help!".  Doing so gets the most number of eyeballs on your problem.

Paul

---

### Post by bladefallcon on 2006-07-26
I believe it is 6.06

And your right...i know better than to use a subject so generic..sorry bout that..lol

---

### Post by John.Michael.Kane on 2006-07-26
You have brezzy repo's mixed with dapper repo's thats a no no. you need to change all lines to match.


Clean Dapper Sources.list
```
**[COLOR="Red"]sudo gedit /etc/apt/sources.list[/COLOR]**

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

**[COLOR="Red"]sudo aptitude update[/COLOR]**
```

---

### Post by bladefallcon on 2006-07-26
so if i take that, and use it to replace my current sources.list...that should fix the problem? Do I have to do anything else afterwords? restart, etc?

---

### Post by Footissimo on 2006-07-26
Replace what you have in source.list with the above then type```
sudo apt-get update
```

---

### Post by bladefallcon on 2006-07-26
no such luck...did everything...still getting same errors..

---

### Post by John.Michael.Kane on 2006-07-26
bladefallcon did you try ```
**[COLOR="DarkOrange"]sudo aptitude dist-upgrade [/COLOR]**
```

---

### Post by bladefallcon on 2006-07-26
just tried...same errors

---

### Post by trent dillman on 2006-07-26
This is bad. You may have to reinstall...

...Although, you might try this:

```
cd /var/lib/dpkg/
diff status status-old
```

If there's a large amount of output, try copying the old as the current:

```
sudo cp status status-backup
sudo cp status-old status
sudo apt-get update
```

Note: I don't know if this will work or screw things up more.

---

### Post by bladefallcon on 2006-07-26
now by re-install...i assume you mean re-install the entire OS? (my god...i feel like such a frickin noob...lol)

---

### Post by trent dillman on 2006-07-26
yeah, total reinstall :-/

I'd take a shot at the steps above first, though. The error message you posted mentions /var/lib/dpkg/status, so I assume that's where the problem is. That file on my machine is over 42000 lines long, and is the list of every installed package. Hopefully for you, the status-old in /var/lib/dpkg/ is the old, working copy...

---

### Post by bladefallcon on 2006-07-26
ok...ill give that a try in a few mins...hopfully you are right, and it will work..not that istalling the OS is so terribly hard, that i can stand to do it again....its actually quite easy...but id just as soon not do it if i dont have to..

---

### Post by bladefallcon on 2006-07-26
nope...no good...still same error..looks like maybe a re-install

---

### Post by trent dillman on 2006-07-26
```
sudo chmod 644 /var/lib/dpkg/status
```??

---

### Post by bladefallcon on 2006-07-27
nope..

no worries man...I'll just do a re-install later..after im done eating dinner..thanks for all the help though

---

