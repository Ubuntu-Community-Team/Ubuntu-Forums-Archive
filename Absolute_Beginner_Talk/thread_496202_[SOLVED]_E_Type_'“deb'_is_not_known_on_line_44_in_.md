---
title: "[SOLVED] E: Type '“deb' is not known on line 44 in source list /etc/apt/sources.list"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by armin00as on 2007-07-08
Hi Guys,

I'm a 4-day Feisty newb, and I actually hate my first post on this board to be about a problem... - but this issue I created today, however, I don't find any help on: I get the following error message(s) when trying to run the Synaptic Package Manager (in order uninstall Automatix)..
I got those errors before when I tried the 'get-update' command... Don't really recall what I messed with, but it must have been the wrong thing to do.. ;-) :lolflag:

  [B]E: Type '“deb' is not known on line 44 in source list /etc/apt/sources.list
  E: The list of sources could not be read.
  Go to the repository dialog to correct the problem.
  E: _cache->open() failed, please report.[/B]

Can it have something to do with me trying to install/uninstall 'Automatix2'... ? I know it's not supported, but some guys seem to have got it running - so I gave it a shot. I read somewhere on the web (this board?) that the "deb is not known..." error may have something to do with the fonts (?? ...that correct?), so I deleted some of the repositories that showed errors... 
- Guess, that was a pretty dumb idea, huh?

Well... any ideas how I can get this problem resolved and the repos re-installed?
Would appreciate help on 'newb level' as was basically a happy camper with being able to get  Feisty running at all, not having any experience with Linux yet (...only got to page 5 of 176 in the "Unofficial Ubuntu 7.04 (Feisty Fawn) Starter Guide" so far...). :confused:

Many thanks in advance for your help and suggestions!!!
a:-)  ](*,) ](*,)

---

### Post by taurus on 2007-07-08
There is something wrong with line 44 in /etc/apt/sources.list so can you post it here?

```
cat /etc/apt/sources.list
```

---

### Post by eternalsword on 2007-07-08
for your information, all automatix related support issues should be directed over to [http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/) as that is where all support for automatix resides.

---

### Post by Tomosaur on 2007-07-08
Ok, first thing's first, could you open up a terminal (Applications > Accessories > Terminal) and run the following command?

```

cat /etc/apt/sources.list

```

Paste the output of the command here and we can see what's wrong :)

---

### Post by armin00as on 2007-07-08
Hi,
Thanks for your response...! 
This is what I get:

armin@E6400-UBUNTU:~$ sudo cat /etc/apt/sources.list
Password:
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main&#8221;
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
armin@E6400-UBUNTU:~$ 

There's a lot to read :confused: and I already tried to follow the instructions and figure out what "Uncomment the following two lines to add software from the 'backports' repository..." means, but to no avail. 

- Thanks!!
:-)

---

### Post by taurus on 2007-07-08
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the last two lines at the bottom.

```
&#8220;deb http://www.getautomatix.com/apt feisty main&#8221;
deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
```
Save it and exit the editing window.  Then run

```
sudo aptitude update
sudo aptitude upgrade
```

p.s.  If you need multimedia codecs stuff, read this, [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats).

---

### Post by Tomosaur on 2007-07-08
> **armin00as said:**
> Hi,
Thanks for your response...! 
This is what I get:

armin@E6400-UBUNTU:~$ sudo cat /etc/apt/sources.list
Password:
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main&#8221;
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
armin@E6400-UBUNTU:~$ 

There's a lot to read :confused: and I already tried to follow the instructions and figure out what "Uncomment the following two lines to add software from the 'backports' repository..." means, but to no avail. 

- Thanks!!
:-)

The second line from the bottom - remove the quotation marks. You need root privileges to edit the file, so use the following command to open it in an editor:
```

gksudo gedit /etc/apt/sources.list

```

Once you're done, save the file, and exit the editor, then run the following command:
```

sudo aptitude update

```

---

### Post by armin00as on 2007-07-08
Hi taurus / Tomosaur!

Thanks very much, your instructions have solved my problem!!!! Back in 'Synaptic' again... Anything else I should do now?

Also, and since I intend to learn from my mistakes (...), what exactly did I do wrong? 
Was it a mistake to delete those repos, or did I mess up trying to install 'Automatix', or is it the fonts?

Anyways, MANY THANKS for your help!!
a:-)  :)

---

### Post by overdrank on 2007-07-08
> **armin00as said:**
> Hi taurus / Tomosaur!

Thanks very much, your instructions have solved my problem!!!! Back in 'Synaptic' again... Anything else I should do now?

Also, and since I intend to learn from my mistakes (...), what exactly did I do wrong? 
Was it a mistake to delete those repos, or did I mess up trying to install 'Automatix', or is it the fonts?

Anyways, MANY THANKS for your help!!
a:-)  :)

HI just a hint, do you see the " " marks on the next to last entry on the list. ;-)

---

### Post by taurus on 2007-07-08
Your mistake was that you placed a " in front and at the end of a repo.  Can't do that in /etc/apt/sources.list.

---

### Post by armin00as on 2007-07-08
Thanks, taurus!
Thanks, Tomosaur!

Don't quite recall how I managed to do that, but I understand...

Thanks also for the "Restricted Formats" link, taurus; I'll check it out ASAP.


**You guys rock!** Thanks for the speedy help/support!!! 
:guitar:

A:-)

---

### Post by Tomosaur on 2007-07-08
> **armin00as said:**
> Hi taurus / Tomosaur!

Thanks very much, your instructions have solved my problem!!!! Back in 'Synaptic' again... Anything else I should do now?

Also, and since I intend to learn from my mistakes (...), what exactly did I do wrong? 
Was it a mistake to delete those repos, or did I mess up trying to install 'Automatix', or is it the fonts?

Anyways, MANY THANKS for your help!!
a:-)  :)

The problem was the quotation marks, nothing more, nothing less :P

It's hard to say exactly what led to those quotation marks being there, and I don't quite understand how fonts would have caused the problem (that'd be like saying bananas are responsible for fatal stabbings!). Anyway, it LOOKS like you added the offending quotation marks manually at some point - maybe you copied and pasted the lines from somewhere? In any case, it's no big deal, the software is just very picky about the formatting of each of the lines in that file, which is why it spits its dummy out as soon as it finds something out of the ordinary. If you come across this kind of problem again, the best thing to do is to just open whichever file the error message complains about (and if it gives you a line number, it'll help you greatly), and just look for anything which is obviously 'out of the ordinary' - misspelled words, random characters, etc etc etc, then just do whatever it takes to make it look ok.

Many programs create a backup when their config files are modified (although not all do), so if you can't find what's wrong in the actual file, you can take a look in the file's directory and see if there's a backup which you can use to replace the non-working file (usually all you have to do is just rename the backup so that the offending file is over-written).

---

