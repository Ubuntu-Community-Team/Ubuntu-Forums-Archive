---
title: "Problems installing codecs"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by zip2kx on 2007-11-01
I finally installed ubunut, and it seems too work. I double clicked on a divx file and it tried to search for codecs to play it. It finds this gstream ffmpeg video plugin for me, but when i double click to install it tells me to reload the list, it reloads, i double click same thing. It's the same thing with all other packages too... 
I have no idea whats wrong, been a pure windows user before.. so Im kinda new to this..

---

### Post by por100pre1 on 2007-11-01
Please read [this]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by ddrichardson on 2007-11-01
Sorry, is this happening with everything you install?

---

### Post by zip2kx on 2007-11-01
yes everything.
I click add/remove program and the first thing it says is that the application list is out of date, I press the refresh button and it seems to download some info and then the list gets presented to me. I Double click on something to install and then the same message about the list being out-of-date pop-ups. And im stuck in this loop,

---

### Post by por100pre1 on 2007-11-01
Try this:

```
sudo apt-get update && sudo apt-get install -f
```

post any error results you may get. :-k


```
cat /etc/apt/sources.list
```

post this too.

---

### Post by zip2kx on 2007-11-01
this is going to be so silly, but i dont know what to do with that.. do i paste it in a terminal?

---

### Post by por100pre1 on 2007-11-01
> **zip2kx said:**
> this is going to be so silly, but i dont know what to do with that.. do i paste it in a terminal?

Oh, yes, sorry for not explain it!

---

### Post by ddrichardson on 2007-11-01
por100pre1, I've seen you answering a lot of posts in the same threads as me and keep meaning to ask - what does your username mean?

---

### Post by zip2kx on 2007-11-01
sudo apt-get update && sudo apt-get install -f gave:

```
arman@arman-laptop:~$ sudo apt-get update && sudo apt-get install -f
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-sv_SE
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-sv_SE
Läser paketlistor... Färdig
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.

```

Um some parts are in swedish, they say "reading packagelist...done" and "reading allowance information... done" (sorrry dont have better words for it) and at the bottom it says "0 upgraded, 0 newinstalled, 0 to remove and 0 not-upgraded.

cat /etc/apt/sources.list gave

```
arman@arman-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://se.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by por100pre1 on 2007-11-01
> **ddrichardson said:**
> por100pre1, I've seen you answering a lot of posts in the same threads as me and keep meaning to ask - what does your username mean?

Hi DDR! I spell it "por-cien-pre-uno", it is meant to sound like "por siempre uno" it means "forever one". :)

---

### Post by por100pre1 on 2007-11-01
> **zip2kx said:**
> sudo apt-get update && sudo apt-get install -f gave:

```
arman@arman-laptop:~$ sudo apt-get update && sudo apt-get install -f
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-sv_SE
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-sv_SE
Läser paketlistor... Färdig
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.

```

Um some parts are in swedish, they say "reading packagelist...done" and "reading allowance information... done" (sorrry dont have better words for it) and at the bottom it says "0 upgraded, 0 newinstalled, 0 to remove and 0 not-upgraded.

cat /etc/apt/sources.list gave

```
arman@arman-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://se.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

Try this:

```
gksu software-properties-gtk
```

and enable main, restricted, universe and multiverse. Let us know if this fixes the issue.

---

### Post by eapache on 2007-11-01
Go into system>admin>Software Sources and enable all the checks until 'source' in the first menu. When you exit, click 'don't reload'. Then go into add/remove and click reload there.

---

### Post by ddrichardson on 2007-11-01
> **por100pre1 said:**
> Hi DDR! I spell it "por-cien-pre-uno", it is meant to sound like "por siempre uno" it means "forever one". :)
Ah I see, cool. I've been reading it as POR-LOOP-REL ;-)

Out of interest, regarding this chaps problem, who decided to comment out the internet sources during installation if there is no network set up in 7.10? I'm sure this wasn't in 7.04 and this is atleast the 5th post I've seen this week with the same issue.

---

### Post by por100pre1 on 2007-11-01
> **ddrichardson said:**
> Out of interest, regarding this chaps problem, who decided to comment out the internet sources during installation if there is no network set up in 7.10? I'm sure this wasn't in 7.04 and this is atleast the 5th post I've seen this week with the same issue.

I think the installer does that if it doesn't detect a web connection, not completely sure about that.

Another way is this:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

```
gksudo gedit /etc/apt/sources.list
```

and then replace the whole contents of the file with this:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://se.archive.ubuntu.com/ubuntu/ gutsy main restricted
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://se.archive.ubuntu.com/ubuntu/ gutsy universe
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates universe
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://se.archive.ubuntu.com/ubuntu/ gutsy multiverse
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
#deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by zip2kx on 2007-11-01
Thank you very much guys! 
It works perfectly now. I have one last question then I wont bother you guys hehe. This will be so stupid, if you want to turn off the computor, is the hibernate button the right one? I was looking for something like "shut down" or something but couldnt find it... I feel like moron but I deicded to ask before i do something stupid..

---

### Post by ddrichardson on 2007-11-01
To turn off you should see a Shutdown button when you click System/Quit

---

### Post by ddrichardson on 2007-11-01
There are no stupid questions, only stupid answers.

---

### Post by eapache on 2007-11-01
That's weird, there should be a shut-down button right next to the hibernate button. There should be two rows like this:

Log Out | Lock Screen | Switch User
Suspend | Hibernate | Restart | Shut Down

---

### Post by por100pre1 on 2007-11-01
Check [this]("http://ubuntuforums.org/showthread.php?t=215110"). Have you KDE installed? :-k

---

### Post by zip2kx on 2007-11-01
Thanks! Looks like there is a lot of box-checking needed to be done lol, Thank you all for your help! Very friendly and helpful!

---

### Post by eapache on 2007-11-01
Just so you know, you should mark the thread as solved with the thread tools near the top of the page.

---

### Post by kajicky on 2007-11-06
> **por100pre1 said:**
> Try this:

```
gksu software-properties-gtk
```

and enable main, restricted, universe and multiverse. Let us know if this fixes the issue.

THANKYOU THIS WORKED PERFECTLY FOR THE SAME PROBLEM, I WASN'T GOING TO POST THE SAME QUESTION AGAIN. I HAVE USED MANDRIVA BEFORE UBUNTU AND COULD NOT UNDERSTAND WHY IT WAS WORKING OFF THE LIVE CD, BUT ITS RESOLVED NOW MANY THANKS AGAIN!!!

---

