---
title: "major failure of your software management system"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by ratbagradio on 2007-03-30
This is my second session trying to handle Ubuntu 6.60. I wanted to 
[LIST]
[*]download and install Audacity audio editor
[*]upgrade/date Firefox to the latest version
[/LIST]

When I tried to follow the codes for this I kept getting protest messages on the terminal. Then I got this when I tried to check for results  via Add/Remove:

[I]Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.[/I]

So from the discussion here I gather you'll need my source list. But my error messages when I filled in the stuff on TERMINAL kept asking me for "localization" and throwing error messages  for line 34 and "deb" ???????

I really have no idea and should not have played with Terminal but I was desperate to get a working version of Audacity Audio editor so I could catch up on my edting and all the info I found said do these things with terminal....

dave riley

PSL I still want to upgrade to Firefox 2 and code chasing that got me into troble in the first place.

**Here's my source list:**

________________



deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”

---

### Post by ratbagradio on 2007-03-30
POSTSCRIPT: My Update Manager won't "boot" spo I've freally cut myself off from everything.

dave riley

---

### Post by yabbadabbadont on 2007-03-30
All those automatix lines are probably causing the issue.  Here is my sources.lst file just as a reference:
```
/home/daffy $ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

---

### Post by compmodder26 on 2007-03-30
Somebody correct me if I'm wrong, but I don't think those your able to have quotes around repository lines.  Remove all those lines with the quotes around them:

```
“deb http://www.getautomatix.com/apt dapper main”
“deb http://www.getautomatix.com/apt dapper main”
“deb http://www.getautomatix.com/apt dapper main”
“deb http://www.getautomatix.com/apt dapper main”
```

Also, they are the same repository.  You only need one.

---

### Post by ratbagradio on 2007-03-31
What happens if I copied and pasted in your source file script rather than fiddle around? 'Cause I'm green around the Ubuntu gills....and I just wanna get rolling and learn from my mistakes.

---

### Post by nixclusive on 2007-03-31
If you're using the same version you might as well copy and paste the reference file. Make sure to do an ```
sudo apt-get update
``` after that.

---

### Post by STREETURCHINE on 2007-03-31
you could remove the " from the front and rear of the get automatix lines
so it looks like this

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

then just delete the last three

“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”

as they are duplicates and are not needed

then remove the # from the front of the remaining deb packages
so they look like this

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

then

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by mcduck on 2007-03-31
Here's the edited version of your sources.lst, you can just replace the old one with this.

```
deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.getautomatix.com/apt dapper main

```

You cannot upgrade to Firefox 2 with the package management, it's not available for 6.06. Many programs depend on Firefox to do HTML rendering for them, and upgrading Firefox would mean that all those programs would have to be upgraded, and also all their dependencies, and perhaps dependencies of dependencies and who knows what. Ubuntu developers decided that it would be too big of a task to do all that while still making sure that everything stays stable and no bugs are introduced.

But there are many thread in this forum providing instructions how to install Firefox 2 while still keeping the old version so nothing breaks. And I believe that there's some automatic script to do the task too..

---

### Post by ratbagradio on 2007-03-31
Thanks. That seemed to work after I replaced the source list. I'll read up on installation issues before I proceed further. I downloaded 127 updates yesterday in the lead into my problem but I still have to work out how to get and install Audacity . ..And for the moment I'll forget about Firefox 2.0.

I find that there is this language barrier with Linux that imakes it hard to comprehend in the first instance....another paradigm.

---

### Post by STREETURCHINE on 2007-03-31
audacity is in the repositories  so open synaptic and install or just do 

         ```
sudo aptitude install audacity
```

as to fire fox you are on your own..lol

---

