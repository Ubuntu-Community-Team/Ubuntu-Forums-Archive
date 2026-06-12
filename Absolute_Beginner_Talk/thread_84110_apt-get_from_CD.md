---
title: "apt-get from CD"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by Lilac Haze on 2005-10-30
I am still plugging away trying to install my SpeedTouch 330 on this machine and not really getting anywhere.

Apparently I will need to use gcc at some point and not knowing if (or how to check if) I already have this I thought it would be easiest if I just got it off my CD. Guess what it tells me? I dont have permission! I am not the owner! I only downloaded the iso file myself and burnt my own CD! So how come I am not the Owner?

Help me please...........:confused:

---

### Post by aysiu on 2005-10-30
First of all, do you not have an internet connection? I'm just wondering why you're trying to get it off CD.

Secondly, what CD is this? Is this just a data CD full of .deb files, or is the Ubuntu installer CD?

Apt-get has to use sudo (or "root") to install stuff.

---

### Post by Lilac Haze on 2005-10-30
Hi
 In answer to your questions:

1. the only internet connection I have is in *Windows XP*
2. I'm using my installation CD
3. I use alt-F2 gksudo nautilus when I'm trying to do this.

Thanks

---

### Post by aysiu on 2005-10-30
I believe a default install (if you haven't changed your /etc/apt/sources.list) uses the installer CD as a source. What I would do is make a backup of your current list: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` then edit the list ```
sudo gedit /etc/apt/sources.list
``` Highlight everything and replace it with this line ```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
``` Then, pop in your CD in the CD-ROM drive (the installer CD) and ```
sudo apt-get update
``` Did it work?

---

### Post by Lilac Haze on 2005-10-30
:KS By the way Aysiu I have just been looking at your link to software installation and I see that everything is coprighted. Do you have any objections to us newbies printing off the odd page for our own reference?

Thanks

---

### Post by Lilac Haze on 2005-10-30
Thanks Aysui

Just gotta log off and fire up ubuntu to try it out.

Will let you know how it goes.

Thanks again

---

### Post by aysiu on 2005-10-30
[QUOTE=Lilac Haze]:KS By the way Aysiu I have just been looking at your link to software installation and I see that everything is coprighted. Do you have any objections to us newbies printing off the odd page for our own reference?

Thanks[/QUOTE] No, not at all. In fact, I believe it would fall under the "fair use" clause for copyright. Go for it!

---

### Post by Lilac Haze on 2005-10-30
Back again, sorry it took me so long.

I'm afraid it didn,t work. This is what happened:


[COLOR="Purple"]$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup[/COLOR]

[COLOR="Black"]then nothing so I [/COLOR]

[COLOR="Purple"]alt-F2 gksudo nautilus
Password:
$cp /etc/apt/sources.list /etc/apt/sources.list_backup
cp: cannot create regular file `/etc/apt/sources.list_backup': Permission denied 
$
[/COLOR]

[COLOR="Black"]Do you think there is something wrong with my installation? Or is it me just being thick?
[/COLOR]

Thanks :???:

---

### Post by aysiu on 2005-10-30
[QUOTE=Lilac Haze]Back again, sorry it took me so long.

I'm afraid it didn,t work. This is what happened:


[COLOR="Purple"]$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup[/COLOR]

[COLOR="Black"]then nothing so I [/COLOR][/quote] What do you mean--"nothing"? The point of that command is to make a backup copy of your sources.list. It probably worked. Go into the /etc/apt folder and see if there's a file there called sources.list_backup. If there isn't, then it didn't work. Just because it went to the next line in the terminal doesn't mean it didn't work.

> 
[COLOR="Purple"]alt-F2 gksudo nautilus
Password:
$cp /etc/apt/sources.list /etc/apt/sources.list_backup
cp: cannot create regular file `/etc/apt/sources.list_backup': Permission denied 
$
[/COLOR] I didn't ask you to do an alt-F2 gksudo nautilus. Please follow the exact instructions I gave you in the fourth post of this thread. The only part I'm not sure will work is the last part.

---

### Post by Lilac Haze on 2005-10-31
Thank you, Aysui for being so patient with me.

I have now checked out my /etc/apt folder and there is a file there called sources.list_backup. This is exactly what is in there:-

 [COLOR="Purple"]deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe[/COLOR]


As I understand it any line beginning with "#" or "##" is not recognised by the program, so I then did the 

[COLOR="Purple"]sudo apt-get update[/COLOR]

with my installer CD inthe CD-ROM drive but nothing happened (as far as I know). No sound of the disc being read or anything. 
Just a thought, I was supposed to do that last command in Terminal wasn't I? Not in gedit.

---

### Post by aysiu on 2005-10-31
[QUOTE=Lilac Haze]Thank you, Aysui for being so patient with me.
with my installer CD inthe CD-ROM drive but nothing happened (as far as I know). No sound of the disc being read or anything. 
Just a thought, I was supposed to do that last command in Terminal wasn't I? Not in gedit.[/QUOTE] Yes. Save what was in Gedit. Close Gedit. Then type the command ```
sudo apt-get update
``` in terminal.

---

