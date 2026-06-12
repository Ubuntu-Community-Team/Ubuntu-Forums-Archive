---
title: "[SOLVED] Help1 can't watch this dvd"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-01-03
I've installed libdvdcss, and the movie starts to play, but about 15 seconds in I get an error saying "Could not read resources" or something along those lines.

What's the problem?

---

### Post by ~LoKe on 2008-01-03
Which player are you using?  Are you sure it's not a damaged DVD?

---

### Post by jordank on 2008-01-03
Totem movie player. and i'm positive the dvd isnt damaged. i just took it out of the package.

---

### Post by jordank on 2008-01-03
the actual error reads "could not read from resource"

---

### Post by ~LoKe on 2008-01-03
> **jordank said:**
> Totem movie player. and i'm positive the dvd isnt damaged. i just took it out of the package.

Try installing VLC and see if it works.
```
sudo apt-get install VLC
```
Then, to play it:
```
vlc dvd://
```

---

### Post by jordank on 2008-01-03
how do i make a player my default viewer? like i want to try using mplayer, but i dont know how to open up the dvd with mplayer

---

### Post by ~LoKe on 2008-01-03
> **jordank said:**
> how do i make a player my default viewer? like i want to try using mplayer, but i dont know how to open up the dvd with mplayer

```
mplayer dvd://
```

There's a section for preferred applications in system -> preferences.  You should be able to set it as default there.

---

### Post by jordank on 2008-01-03
also:


jordan@Jorcomp:~$ sudo apt-get install VLC
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package VLC

---

### Post by ~LoKe on 2008-01-03
You'll need to enable the multiverse repository in /etc/apt/sources.list by removing the comments in front of it.

---

### Post by jordank on 2008-01-03
i tried mplayer dvd:// but it only player like 20 seconds then went black.  What's wrong?

---

### Post by ~LoKe on 2008-01-03
> **jordank said:**
> i tried mplayer dvd:// but it only player like 20 seconds then went black.  What's wrong?

Where did you get the codecs to play these movies?  Are you using the medibuntu repository?

---

### Post by jordank on 2008-01-03
Here's my sources.list file, to me it looks like multiverse is enabled.

# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main


and here's the error still.

jordan@Jorcomp:~$ sudo gedit /etc/apt/sources.list

jordan@Jorcomp:~$ 
jordan@Jorcomp:~$ sudo apt-get install VLC
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package VLC
jordan@Jorcomp:~$

---

### Post by ~LoKe on 2008-01-03
Odd...I can't remember which repository it's in.  Add this one:

> ## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
And the gpg key:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by metalpancake on 2008-01-03
You could try gettin xine movie player from add/remove.
It worked for me when I had a similar problem.
:)

---

### Post by jordank on 2008-01-03
Thanks man. Xine worked :)

I'd thank you if i knew how

---

### Post by ~LoKe on 2008-01-03
> **jordank said:**
> Thanks man. Xine worked :)

I'd thank you if i knew how

Looks like you figured it out.  There's also Thread Tools at the top, then select "Mark as Solved".

---

### Post by ugm6hr on 2008-01-03
```
jordan@Jorcomp:~$ sudo apt-get install VLC

```

It's **vlc**, not VLC.

```
sudo apt-get install vlc
```

---

### Post by ~LoKe on 2008-01-03
> **ugm6hr said:**
> ```
jordan@Jorcomp:~$ sudo apt-get install VLC

```

It's **vlc**, not VLC.

```
sudo apt-get install vlc
```

Oh dear God. *smacks self*.  Didn't catch that one.

Time for bed, good night! :lolflag:

---

