---
title: "Installing Downloaded Programs"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by Woggie on 2006-02-22
I have DL'ed a few things, MPlayer, GPF (Financial Planner), and Blender.  I cannot figure out how to get these installed so I can use them.  Help Please.

---

### Post by Stelmate on 2006-02-22
Okay, did you download them in a .deb package format or a .tar.gz format?

---

### Post by mostwanted on 2006-02-22
Why not just install them from Synaptic, do you need a more recent version?

---

### Post by Woggie on 2006-02-22
> Okay, did you download them in a .deb package format or a .tar.gz format?

MPlayer and Blender are in .tar.bz2.  The GPF was a .zip file.

---

### Post by Perfect Storm on 2006-02-22
mplayer and blender you can get through apt-get.

```

sudo gedit /etc/apt/sources.list

```

Uncomment the lines (where it says # <lines>, but don't touch the ones with two #)

add:

[b]## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
[/b]

Save it.

```
sudo apt-get update
sudo apt-get install mplayer-386 blender

```

Done.

Are you sure that GPF (Financial Planner) are avaible for linux? A link perhaps.

---

### Post by Bionic_Beefpile on 2006-02-22
[QUOTE=Woggie]MPlayer and Blender are in .tar.bz2.  The GPF was a .zip file.[/QUOTE]
For the tar files, go to the directory (in your terminal) and then
```
tar -xvf <file name>
```
After that you might have to configure the file with ./configure
then
```
make
sudo make install
```

::EDIT:: D'OH, beaten to the punch.  Artificial's solution is easier anyhow :)

---

### Post by Woggie on 2006-02-22
> Uncomment the lines (where it says # <lines>, but don't touch the ones with two #)

Dumb question, how do I Uncomment?

---

### Post by Perfect Storm on 2006-02-22
Just remove the #

Example:

## Multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

So it says:

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

---

### Post by Woggie on 2006-02-22
Ok, I get a bunch of could not connect to and could not stat source package and connection timedout errors.  The last thing I get is:  "E: Some index files failed to download, they have been ignored, or old ones used instead.

Any suggestions?

---

### Post by kaamos on 2006-02-22
can you post the output of
```
cat /etc/apt/sources.list
```

---

### Post by Woggie on 2006-02-22
Here ya go...


> ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras


---

### Post by kaamos on 2006-02-22
Looks ok to me. Probably just some servers are down.. Try the install command from the previous page and see if the needed packages are found.

---

### Post by Woggie on 2006-02-22
Here is the reply I got:


> Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libdirectfb-0.9-22 but it is not installable
               Depends: libggi2 (>= 1:2.0.5) but it is not installable
               Depends: libglib1.2 (>= 1.2.0) but it is not installable
               Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
               Depends: libjack0.80.0-0 (>= 0.99.0) but it is not installable
               Depends: libmad0 (>= 0.15.1b) but it is not installable
               Depends: libpolyp0 but it is not installable
               Depends: libsvga1 but it is not installable or
                        svgalib-dummyg1 but it is not installable
               Depends: xmms (>= 1.2.10+cvs20050209) but it is not installable
E: Broken packages


---

### Post by Perfect Storm on 2006-02-22
The sourcelist you shown seems to be cut? 
Perhaps I should ask this first (my mistake) which version of ubuntu are you using and which struckture (x86 ppc etc.)

---

### Post by Woggie on 2006-02-22
I'm not sure, where can I find that?

---

### Post by Perfect Storm on 2006-02-22
```
sudo gedit /etc/apt/sources.list
```
Just as before, but what you posted ended with a #backports-extras, that just seems odd...

---

### Post by Woggie on 2006-02-22
i386

---

### Post by Perfect Storm on 2006-02-22
ubuntu 5.04 or 5.10?

---

### Post by mostwanted on 2006-02-22
Shame on me for suggesting otherwise but you *have* run
```
sudo apt-get update
```
after you edited the sources.list, right?

---

### Post by Woggie on 2006-02-22
> ubuntu 5.04 or 5.10?


Here's the whole title:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

---

### Post by stalefries on 2006-02-22
Before trying to install these programs, make sure you type 
```
sudo apt-get update
```

In fact, do that every time after you update /etc/apt/sources.list

It's a crucial step.

---

### Post by Woggie on 2006-02-22
That's kind of where the problem is right now.  It won't get the updates.

---

### Post by dvarsam on 2006-02-22
Dear "Woggie":

After you fix your sources.list file, then go read my Tutorial - it is a step-by-step procedure & posted it Today!

It is about on How to work with the "Synaptic" program (took me 6 hours man...)

Article No: 134921

It is going to help you a lot !!!

---

### Post by franonubu on 2006-02-22
Hi
I get a message like that zhen I write apt-get update: 

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Do you know how to deal with that?

fran

---

### Post by franonubu on 2006-02-22
I tried with sudo before apt-get update but it seems there are some unfindable Packages . Would anybody know how to find theses packages?

Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
  404 Not Found
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [4747B]
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
  404 Not Found
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Get:31 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release

E: Some index files failed to download, they have been ignored, or old ones used  instead.

---

### Post by Perfect Storm on 2006-02-23
Make sure that synaptic package manager are closed.

---

