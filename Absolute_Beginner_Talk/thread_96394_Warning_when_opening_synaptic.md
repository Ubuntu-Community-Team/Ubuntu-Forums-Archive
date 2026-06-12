---
title: "Warning when opening synaptic"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by Jubal on 2005-11-28
I just installed the 5.10 Breezy 64 bit, I then completely some updates, and installed some programs in synaptic I am interested in.  I then started following some instructions for installing cinelerra.  I installed easy ubuntu (2.4 I believe)  I now get this error message when opening synaptic

W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)

I am very much a newbie and have very little command line experience.  Please be as specific as possible when helping me fix this problem.

Thank you so much, looking forward to being an ubuntu user.

---

### Post by ecobuntu on 2005-11-28
just click 'Reload' in Synaptic and see if that works

---

### Post by Jubal on 2005-11-28
ok did that and it started downloading some things then got this message

[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:) 404 Not Found
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:) 404 Not Found
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-amd64/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-amd64/Packages.gz:) 404 Not Found
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-amd64/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-amd64/Packages.gz:) 404 Not Found

I opened synaptic again and got same message again

---

### Post by Turtle.net on 2005-11-28
Hi
If it doesn't work could you post the result of ```
$ grep freecontrib /etc/apt/sources.list

```

Maybe ther is something wrong with the adress of the mirror ?

---

### Post by ecobuntu on 2005-11-28
yeah copy and paste you /etc/apt/sources.list file here
so go to a terminal and type gedit /etc/apt/sources.list and copy that on to this forum

---

### Post by ecobuntu on 2005-11-28
One other thing it's likely that the repository might be down temporarily and you just need to wait for a bit and try to reload it again

---

### Post by Turtle.net on 2005-11-28
or try an other mirror for plf. I use [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) and it works perfectly ;)

---

### Post by Jubal on 2005-11-28
[QUOTE=Turtle.net]Hi
If it doesn't work could you post the result of ```
$ grep freecontrib /etc/apt/sources.list

```

This was completely blank

yeah copy and paste you /etc/apt/sources.list file here
so go to a terminal and type gedit /etc/apt/sources.list and copy that on to this forum

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse

## PLF repositories, contains litigious packages, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
deb [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free

---

### Post by Jubal on 2005-11-28
How do I change the mirror?

---

### Post by Turtle.net on 2005-11-28
First of all (just in case) make a backup of your repository list ```
sudo cp /etc/apt/sources.list/etc/apt/sources.list_backup 
```
Open your sources.list ```
sudo gedit /etc/apt/sources.list
```
and replace the lines ```
## PLF repositories, contains litigious packages, see http://wiki.ubuntu-fr.org/doc/plf
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
deb http://antesis.freecontrib.org/mirro...u/freecontrib/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirro...u/freecontrib/ breezy free non-free
```

by
```
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
```

and now type in a terminal
```
sudo apt-get update
sudo apt-get upgrade
```

Now your PLF repository should be back online :smile:

---

### Post by Jubal on 2005-11-28
Ok, I think we are making progress, it updated and upgraded, I had a shorter error message, 

W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)


then when I hit reload it had this

[http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:) 404 Not Found

---

### Post by Turtle.net on 2005-11-28
Oups....I do not think we are progressing...that's the same message, there is less repositories ... so less error messages...

---

### Post by Turtle.net on 2005-11-28
And There is something weird...I do not understand why when you did "grep freecontrib /etc/ept/sources.list" nothing happened
you had a "freecontrib" line, normaly this instruction should answer 
```
$ grep freecontrib /etc/apt/sources.list
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```

---

### Post by Turtle.net on 2005-11-28
Ok, I maybe have a last idea
Open your sources.list
```
$ gedit /etc/apt/sources.list
```
Select all (Ctrl+a) and delete (yes delete everything).
save and exit
Now:
```
$ sudo apt-get update
$ sudo apt-get upgrade
```
This should clean everything. Now you can reconstruct your repository list from your backup (you made a backup, isn'it?). In any case you have posted your previous sources.list in this thread ;)
```
$ sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list

```
and redo ```
$ sudo apt-get update
$ sudo apt-get upgrade
```

after that if there is still some errors...

---

### Post by Jubal on 2005-11-28
ok, I need some help when I do

$ gedit /etc/apt/sources.list

The list comes up completely empty

$ sudo apt-get update

It says cannot display location

Am I not supposed to put in the $

when I don't the source list has something in it but it is read only.

---

### Post by Jubal on 2005-11-28
ok I was able to open sources.list and clear using 

sudo gedit /etc/apt/sources.list

I did everything else without the $ in front

New error message after using reload

cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/dists/breezy/main/binary-amd64/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/dists/breezy/restricted/binary-amd64/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Then

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)

Do I need to add the install Cd and try again?

Thanks for your help, sorry it's turning out to be a hassle.

---

### Post by Jubal on 2005-11-28
wow, ok added the install Cd and voila, no error message.  Thank you so much!

---

### Post by Turtle.net on 2005-11-29
[QUOTE=Jubal]ok, I need some help when I do

$ gedit /etc/apt/sources.list

The list comes up completely empty

$ sudo apt-get update

It says cannot display location

Am I not supposed to put in the $

when I don't the source list has something in it but it is read only.[/QUOTE]
Ok you manage to solve yourself your problem. It's good, isn't it ?
Let me explain some few things :)
The $ is the sign to say "you type this instruction in a terminal in user mode, that is to say non root"
The # is the same thing for root user (it's more or less equivalent to $ sudo...)

Obviously you do not have to tape the $ or # it's just to give you some indications 

When you want to change a configuration file for your system (placed in /etc...) most of the times you will have to be root to edit. That's why ```
$ gedit /etc/apt/sources.list
```
will open the file in read-only
on the other hand 
```
# gedit /etc/apt/sources.list
```
or
```
$ sudo gedit /etc/apt/sources.list
```
will open the file in editing mode.

I am just curious what do you have now in your file /etc/apt/sources.list ?

---

### Post by Jubal on 2005-11-29
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by Jubal on 2005-11-29
Oh wait sorry, wrong computer.  

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

