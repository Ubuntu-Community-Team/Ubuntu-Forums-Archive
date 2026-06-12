---
title: "Mp3/gst reamer help"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by stevenash on 2006-05-22
I was looking through the wiki and trying to follow the steps to be able to play mp3 files.  I enabled all the universes and made them multiverse.

Then I tried to install the gst reamer plugins, but got some errors.  Here is the code from the terminal:

```

sudo aptitude install gstreamer0.8-mad
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  gstreamer0.8-mad:  Depends: libid3tag0 (>= 0.15.1b) which is a virtual package.                    Depends: libmad0 (>= 0.15.1b) which is a virtual package.

```

My mp3's still won't play in Rhythmbox or Totem.  Anyone know what's wrong?

---

### Post by Sef on 2006-05-22
> I was looking through the wiki and trying to follow the steps to be able to play mp3 files. I enabled all the universes and made them multiverse.

You should have added Multiverse to Universe.  Not changed Universe to Multiverse. Is that what you did?

Your repository should look like this:

```
deb http://kr.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://kr.archive.ubuntu.com/ubuntu/ dapper universe multiverse
```

Note:  The kr is because of where I live.  If you are using Breezy, then the source will list Breezy instead of Dapper.

---

### Post by stevenash on 2006-05-22
I followed this instructions outlined here:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

I just added Multiverse on to the end of Universe.

---

### Post by stevenash on 2006-05-22
I also got the same error trying to install Totem-xine

---

### Post by stevenash on 2006-05-22
This is what my sources.lst file has:

```

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy universe multiverse

```

---

### Post by catlett on 2006-05-22
Type this in the terminal and then copy paste it here in a reply.
```
sudo gedit /etc/apt/sources.list
```
You might not have the repository set up right. Did you enable the repositories through the gui synaptice package manager or did you just edit this file?

---

### Post by stevenash on 2006-05-22
I did it through the Synaptice Package Manager.  Here's my source.lst file:

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy universe multiverse


```

---

### Post by catlett on 2006-05-22
When there is a "#" htat means it is uncommented. Which means it will be ignored. For some reason all the repositories weren't enabled. If they were there wouldn't be any # before the URL.
Just delete the # in front of the urls that say multiverse and universe and restricted. then run ```
sudo apt-get update
``` Then try to reinstall.

P.S. Not all the # only the ones with deb after them. You don't want to remove it from in front of the lines of text that describe the urls

---

### Post by stevenash on 2006-05-22
[QUOTE=catlett]When there is a "#" htat means it is uncommented. Which means it will be ignored. For some reason all the repositories weren't enabled. If they were there wouldn't be any # before the URL.
Just delete the # in front of the urls that say multiverse and universe and restricted. then run ```
sudo apt-get update
``` Then try to reinstall.

P.S. Not all the # only the ones with deb after them. You don't want to remove it from in front of the lines of text that describe the urls[/QUOTE]
As usual catlett, you are my Ubuntu savior.  I'm going to have to put you on speed dial for all of my linux problems!  j/k.  Thanks though, for everything.

---

### Post by catlett on 2006-05-22
Just passing along the help I got. Believe it or not this is my recreation. After work I have my basement area and I mess with my computers and keep one logged into the Ubuntu forums. If I see something I happen to know I jump in.
Your learning (at least from what little I have seen of it) the same way most learn linux. Just get started and post your errors in a forum. Someone directs you through the problem and  you always remember the solution because you worked through the problem.Little by little you get exposed to all the different aspects of your system.
 In other forums I've seen people get their info and leave. There is something different about Ubuntu. People stay connected to the forum and have a genuine willingness to help for the sake of helping.
Anyways I wish I could say that was the last thing that you'll have trouble with, but I would be lying.:---) 
Just post and if I can't help there are smarter people than me around.:-D

---

