---
title: "Tried to update miro and got this error in synaptic package manager"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Shazmar on 2008-03-23
Hi guys, I'm more or less brand new to linux so i've obviously made some mistake, hope you can help. This is the error message 

E: Malformed line 45 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

Cannot report this in synaptic as it is totally greyed out.

I've looked at another thread with a similar problem and they were asked to post the source list. Here's mine, and I haven't got a clue what I'm looking at, or for.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy

If anyone has any ideas could they please advise but try to keep it simple as I'm not the brightest bulb in the lamp. Thanks in advance.

---

### Post by spiderbatdad on 2008-03-23
I don't recongize these two lines, and they look malformed:
deb [http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu](http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu) gutsy/
deb [http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu](http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu) gutsy

You could comment them out for the time being, and run the update again.

To comment out the line run: ```
gksu gedit /etc/apt/sources.list
```

add a # in front of each of those two lines. Click the floppy disk image near the top of the window to save.

---

### Post by wormser on 2008-03-23
The error is telling you that something is wrong with line 45.  Where did you get the last two lines?  I would remove them then run:

```
sudo apt-get update
```

---

### Post by Shazmar on 2008-03-23
Thanks very much for the speedy replies and help, Did not expect to resolve problem so quick. Thanks spiderbatdad and wormser. Went straight for wormsers remedy and am pleased to say I am now back to full function in synaptic. Will leave the update for miro until a later date. The help on this forum is phenominal. Again thank you. Resolved

---

### Post by forestpixie on 2008-03-23
The line should read 

```
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu gutsy/
```

try to add that to your sources.list then do an apt-get update, or follow instructions here
[http://www.getmiro.com/download/ubuntu.php](http://www.getmiro.com/download/ubuntu.php)

---

