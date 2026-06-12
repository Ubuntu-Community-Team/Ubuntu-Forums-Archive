---
title: "Repositry help"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by at0mik on 2007-03-23
Well I've just uninstalled Windows from my system and only have Ubuntu 6.06 as my OS (runs perfectly :D), went to go install some things in the repositries but now I have a problem. I went to install VLC media player and added "ftp://ftp.videolan.org/pub/videolan/ubuntu" in the APT line instead of "**deb** [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) **dapper universe**" with the latter being the correct one.

Now I'm getting error messages of whenever I startup the Synaptic Package Manager:
> E: Type 'ftp://ftp.videolan.org/pub/videolan/ubuntu' is not known on line 31 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.

Anyone able to tell me what to do or where the repositry dialogue is (I've looked everywhere but can't seem to find it :().

---

### Post by Perfect Storm on 2007-03-23
You can edited it away the (ftp link) by;
```
sudo nano /etc/apt/sources.list
```

When done;
```
sudo aptitude update
```

---

### Post by taurus on 2007-03-23
Can you post your /etc/apt/sources.list because there is something wrong with line 31 in there?

```
cat /etc/apt/sources.list
```

Edit:  Hello, AI.

---

### Post by at0mik on 2007-03-23
> **taurus said:**
> Can you post your /etc/apt/sources.list because there is something wrong with line 31 in there?

```
cat /etc/apt/sources.list
```

Edit:  Hello, AI.
Where would I be able find that?

---

### Post by taurus on 2007-03-23
Open a terminal with Applications -> Accessories -> Terminal and type that command in from the prompt.

---

### Post by at0mik on 2007-03-23
Here:
> ## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

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
[ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu)

Also, thank you for the help :).

---

### Post by taurus on 2007-03-23
From the same terminal, edit /etc/apt/sources.list with

```
gksudo gedit /etc/apt/sources.list
```
Don't worry about the warning message.  A new GUI text edit should open and scroll down to the end and remove the last line from it.

```
ftp://ftp.videolan.org/pub/videolan/ubuntu
```
Save it.  Then, run these two commands again from the same terminal.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by at0mik on 2007-03-23
Thank you very much taurus :). I was wondering if you could help me with what I was installing (so not to run in the same problem again.

The program is VLC Media Player and the installation incstructions are here; [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) :D.

---

### Post by taurus on 2007-03-23
Okay,  I think this is what you tried to do.  Edit /etc/apt/sources.list from a terminal again with

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
deb ftp://ftp.videolan.org/pub/videolan/ubuntu dapper universe
```
Save the change.  Now, run these from a terminal

```
sudo aptitude update
sudo aptitude install vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2
```
You can now run vlc from Applications -> Video & Sound -> VLC.

---

