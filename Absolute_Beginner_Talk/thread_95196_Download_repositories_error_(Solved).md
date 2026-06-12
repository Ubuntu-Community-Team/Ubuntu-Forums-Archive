---
title: "Download repositories error (Solved)"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Granduke on 2005-11-26
When I try to install this repository thru Synapric, I get:
cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Can someone please tell me the syntax for the 'apt-cdrom' command in this instance?

---

### Post by aysiu on 2005-11-26
What are you trying to do exactly?
And can you post the output of this command ```
cat /etc/apt/sources.list
```?

---

### Post by Granduke on 2005-11-26
What I did was:
1)Thru Synaptic, I choose Repositories 
2)There was no check mark by "CD Ubuntu 5.10 "Breezy Beaver" (Binary)
3)Checked it and hit OK (I'm new to this. I'm thinking more repositories the better- Right?)
4)Then the message in my first post occured.

Here's the text you wanted:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by aysiu on 2005-11-26
The problem is that you have the CD as a source in your repositories list. I don't know why this poses a problem, but I guess it might conflict somehow with the online repositories. (I'm just guessing here.)

Try doing this: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
``` Put a # sign in front of the first line and then press Control-X, y, and Enter.

Then pop open Synaptic and click Reload.

---

### Post by Granduke on 2005-11-26
Thanks aysiu,
That did the trick.
This is the second  time you have helped me.  I really appreciate it.
I have one more problem for which I will start a new thread.  I hope you will read it.
Also, can you tell me how long it took you to get comfortable/proficient with Linux?

thanks for your help.

---

