---
title: "Malformed line..."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by TarsierSpectral on 2007-08-08
I've been trying to install Beryl but every time I get this message:
E: Malformed line 43 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

Also when I open sources.list I get a message:
"Found a swap file by the name "etc/apt/.sources.list.swp"

I have no idea how to fix that.
Can anyone help?

---

### Post by ThrobbingBrain66 on 2007-08-08
```
cat /etc/apt/sources.list
```

could you paste the contents of that command please?

---

### Post by TarsierSpectral on 2007-08-08
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty

---

### Post by Dr Small on 2007-08-08
it looks like to me, that the last line is unfinished...

---

### Post by apetresc on 2007-08-08
> **Dr Small said:**
> it looks like to me, that the last line is unfinished...

Correct. Change the last line to ```
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```
and run:```
sudo rm /etc/apt/.sources.list.swp
``` Then do an update and you'll be fine :)

(You may need to do that second step BEFORE the first step if it doesn't let you write the file on account of the .swp file)

---

### Post by ThrobbingBrain66 on 2007-08-08
> **Dr Small said:**
> it looks like to me, that the last line is unfinished...

Yup, the whole line should be:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by TarsierSpectral on 2007-08-08
OK I did everything you guys said except "Then do an update and you'll be fine"
what do you mean by update?

---

### Post by ThrobbingBrain66 on 2007-08-08
```
sudo apt-get update
```
This updates your sources.list to reflect the changes that were made.

---

### Post by apetresc on 2007-08-08
> **ThrobbingBrain66 said:**
> ```
sudo apt-get update
```
This updates your sources.list to reflect the changes that were made.
Sorry, I should've specified :) I meant ```
sudo apt-get update
``` This actually goes to all the servers listed in the sources.list file and asks them "Give me your newest list of packages, so I know what I can upgrade."

EDIT: Haha, ThrobbingBrain :) I beat you on the first one, but you beat me on this one. Next one's the tiebreaker! ;)
Although your explanation is a little bit wrong. "sudo apt-get update" does not update your sources.list file. It USES the sources.list file to update the internal package list.

---

### Post by ThrobbingBrain66 on 2007-08-08
> **AdrianP said:**
> Sorry, I should've specified :) I meant ```
sudo apt-get update
``` This actually goes to all the servers listed in the sources.list file and asks them "Give me your newest list of packages, so I know what I can upgrade."

EDIT: Haha, ThrobbingBrain :) I beat you on the first one, but you beat me on this one. Next one's the tiebreaker! ;)
Although your explanation is a little bit wrong. "sudo apt-get update" does not update your sources.list file. It USES the sources.list file to update the internal package list.

I guess I should have been more clear this time.:)
I just meant that he won't get the error anymore and can install beryl.

---

### Post by TarsierSpectral on 2007-08-09
thanks.
Everything worked except that I still don't know how to run Beryl.  I got it installed but when I restart the comptuer I don't have anything special.  The same thing I had before.  Under sessions in Startup Programs I see Beryl Manager but how the heck do I run it?  Perhaps this should be another post

---

### Post by sailor2001 on 2007-08-09
I put the beryl icon on the top panel (right click icon and add) from there I can launch. Select window manager from that

---

### Post by TarsierSpectral on 2007-08-09
> **sailor2001 said:**
> I put the beryl icon on the top panel (right click icon and add) from there I can launch. Select window manager from that

where do I find beryl icon?

---

### Post by TarsierSpectral on 2007-08-09
the only thing about beryl on my computer I can find is Beryl Settings Manager

---

### Post by ThrobbingBrain66 on 2007-08-09
I know you said you have Beryl Manager in the Startup Programs, but do you have the package called 'beryl-manager' installed?

Actually, the better question might be: What happens when you type 'beryl-manager' into a terminal window?

---

### Post by TarsierSpectral on 2007-08-10
thanks, I got beryl installed and running. it's all cool now

---

