---
title: "How can i install my VGA Drivers please"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Forked Tongue on 2008-02-06
Hello and thanks for checking my post,

well i bought a new laptop to enable me to use the High Graphics of Ubuntu.

the VGA Card is Nvidia 8600 GS, on an hp laptop.

however iam facing a new issue :(

[[img]http://xs124.xs.to/xs124/08064/screenshot-1507.png[/img]](http://xs.to)

anything i can do cauz i bought this whole new laptop to use it for Ubuntu now that the graphics card is not recognized by Ubuntu :(

Many thanks and appreciation in advance :)

Regards,
Forked.

---

### Post by Presto123 on 2008-02-06
Simply go into Add/Remove in the Applications menu and in the search bar, type Nvidia. That driver will show up, check it and hit apply, then go back into your Restricted Drivers Manager that you have pictured there and enable the Nvidia card.

Restart.

That should get you to a happy place. :)

---

### Post by wolfen69 on 2008-02-06
you also want to go to system>admin>software sources and enable all repos.

---

### Post by Presto123 on 2008-02-06
> **wolfen69 said:**
> you also want to go to system>admin>software sources and enable all repos.

Agreed. I usually forget to say this step.

---

### Post by Forked Tongue on 2008-02-06
Ok ive done what you gents said, but when i click on any update, it says its going to update the list then goes back and doesnt select it :(

and when i click again it keeps loading and never lets me click it :(

your kind assistance please

Regards,
Forked

---

### Post by erfahren on 2008-02-06
> **Forked Tongue said:**
> Ok ive done what you gents said, but when i click on any update, it says its going to update the list then goes back and doesnt select it :(

and when i click again it keeps loading and never lets me click it 
something may be wrong with your sources.list

open up a terminal (Apps > Accessories > Terminal) and enter:
```

cat /etc/apt/sources.list

```
... and post the output here

---

### Post by Forked Tongue on 2008-02-06
ok this is too much for me to type lol so Screen shot is the answer hehe

[[img]http://xs124.xs.to/xs124/08064/screenshot-2352.png[/img]](http://xs.to)

[[img]http://xs124.xs.to/xs124/08064/screenshot-3544.png[/img]](http://xs.to)

hoep this helps :/

please advice :)

---

### Post by erfahren on 2008-02-06
Forked Tongue -

instead of using a screenshot - just copy the output text that's in the terminal and paste it here (between "code" tags)

---

### Post by Forked Tongue on 2008-02-06
"lucifer@lucifer-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://ftp.u-picardie.fr/mirror/ubuntu/ubuntu/](http://ftp.u-picardie.fr/mirror/ubuntu/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
lucifer@lucifer-laptop:~$ 
"

i hope this does it cauz i can't actually use CTRL+C on the stuff in the terminal

---

### Post by erfahren on 2008-02-06
ok -- I cleaned up your sources.list a little - do this

back up your current sources.list (always a good idea to back up system files before editing)
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_back

```
open your current one in Gedit (the text editor) with root permissions
```

gksudo gedit /etc/apt/sources.list

```
"Select All" (Ctrl+A) in there and copy and paste what is below in there (overwriting the contents) - and save
```

## CD-ROM
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb-src http://ftp.u-picardie.fr/mirror/ubuntu/ubuntu/ gutsy main restricted #Added by software-properties

deb http://sa.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://sa.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sa.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://sa.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://sa.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://sa.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://sa.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://sa.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://sa.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://sa.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://sa.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://sa.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://sa.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://sa.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## MEDIBUNTU REPOSITORY
deb http://packages.medibuntu.org/ gutsy free non-free

```
enter the following into the terminal to add the key for the Medibuntu repo and update
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
that should do it

---

### Post by erfahren on 2008-02-06
oh - that "update" I mentioned just updates the repository information on your computer - there will also be software updates

you'll see the notification or in the terminal you can just do
```

sudo apt-get upgrade

```

---

### Post by Forked Tongue on 2008-02-07
> **erfahren said:**
> oh - that "update" I mentioned just updates the repository information on your computer - there will also be software updates

you'll see the notification or in the terminal you can just do
```

sudo apt-get upgrade

```

Ok ... just to make things clear Erfahren :)

Iam proud to say that iam a 200% Windows user, since 3.1 ....

so what you just said is gibberish to me lol 

what is backup my data ?
where do those lines u just said go ?

this is so confusing lol i just want bought this laptop and i want to enable the High Graphics on it like the cube and those fun programs lol

so please is there anything i can do that is simple ? because ill be honest iam like the king of the noobs here i have no idea what your talking about,

Regardless thanks for your time and help i do appreciate it alot :)


Regards,
Forked

---

### Post by erfahren on 2008-02-07
ok -- you just enter all those commands into the terminal. I try to write out what the commands do so you know what's going on.

open up a terminal by going to Applications > Accessories > Terminal (from the Gnome menu up top)

look back at [my post](http://ubuntuforums.org/showpost.php?p=4283988&postcount=10) -

so when I said "back up your current sources.list" - the command I give below that does just that - that command basically says "copy the /etc/apt/sources.list file and name the copy "sources.list_back". 

the "sudo" is a command to do something with adminstrative (or "root") permissions. "gksudo" does the same, but is used to open GUI based applications with root permissions (Gedit is a GUI based text editor).


Note: In that sources.list file I added the repository for Medibuntu. That repo has some programs and codecs that are proprietary and aren't available in the regular Ubuntu repos. I include that since you'd probably want it eventually. At the bottom there I give the command to add the key for it. 

At the end of the command to add the key is the "&& sudo apt-get update" part - the "&&" says to continue with the next command if the previous one worked. (so it says to add the key, and if it worked, update the list of available repositories on the computer.)

---

