---
title: "Synaptic Package Manager"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by kagoole on 2005-12-16
I'm lost again,
Trying to start the Synaptic Package Manager and this is the
information I get.

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/deb Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_deb_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_cdrom:%5bUbuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)%5d__binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/breezy Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_breezy_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/deb Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_deb_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_cdrom:%5bUbuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)%5d__binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/breezy Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_breezy_binary-i386_Packages) - stat (2 No such file or directory)
What is it telling me, can anyone help.

Kagoole

---

### Post by Mustard on 2005-12-16
Hit the 'Reload' button in synaptic.

Also when you post 'code' in threads...try putting your code between these .....

[noparse]```
..enter code in here...
```[/noparse]

Currently the way you have pasted it into the thread is throwing the thread out of wack. :)

Here is an example of what it does...

[noparse]```
This is a whole bunch of code
```[/noparse]

Will appear like this on the screen

```
This is a whole bunch of code
```

---

### Post by endersshadow on 2005-12-16
Close Synaptic, and then type this into a terminal:

```
sudo gedit /etc/apt/sources.list
```

Then, comment out any lines that say "backports" by placing a # in front of them.

Save and exit, and once back in the terminal:

```
sudo apt-get update
sudo -k
```

Then go ahead and open up Synaptic again.

---

### Post by Mustard on 2005-12-16
endersshadow, that would definitely stop the error occuring, but backports for breezy are available now, so they shouldn't be coming up as not found.

kagoole, can you actually paste the contents of you /etc/apt/sources.list in this thread too?

You can display it in terminal with this command...

```
cat /etc/apt/sources.list
```

---

### Post by endersshadow on 2005-12-16
Lo siento, mi malo.

---

### Post by aysiu on 2005-12-16
See the first link of my sig... please.

---

### Post by kagoole on 2005-12-16
endersshadow, 
Many thanks your fix worked, but I still don't know what caused it.
kagoole

---

### Post by kagoole on 2005-12-16
Mustard,
allthough I now have Synaptic working the following is the sources list.
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

#deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://gb.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 #deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by endersshadow on 2005-12-16
You can uncomment the deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse line by taking the # out from it now, and just do this command in the terminal:

```
sudo apt-get update
sudo -k
```

It should give you no errors.  Then you can boot up Synaptic again.

---

### Post by Mustard on 2005-12-16
As well as doing what endersshadow said above, you could edit this line too...

```
#deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```

It needs the second part of it to be on a seperate line.  Somehow you've got them on the same line.

It should look like this...

```
#deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```

Now that you've done that you can actually remove the reference to breezy backports that is just above the deb cdrom line, because if you have done as endersshadow has instructed you already have a line that is referring to backports further down the page, making this one now redudant.  Its currently commented out, so synaptic won't use it, but for the sake of having a tidy sources.list its worth taking out the duplicate line.

---

### Post by kagoole on 2005-12-17
Gents,
This is the latest error I am getting

```
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
```

and this my source code 

```


#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://gb.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 #deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

Can you help again if poss.
Thanks in advance
kagoole

---

