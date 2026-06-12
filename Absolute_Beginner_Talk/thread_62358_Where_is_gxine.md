---
title: "Where is gxine?"
date: 2005-09-04
forum: Absolute Beginner Talk
---

### Post by Irony on 2005-09-04
I've installed gxine via synaptic because I'm trying to get a .wmv to play - I was expecting gxine to pop up under Applications>Sound and Video but can't find it anywhere.

Is it an actual player or a sort of add on?

---

### Post by aysiu on 2005-09-04
Looks to me as if it's just some part of Xine:

[http://xinehq.de/](http://xinehq.de/)

---

### Post by Irony on 2005-09-04
.

---

### Post by Irony on 2005-09-04
Not sure about gxine or xine but I eventually installed totem-xine which uninstalls totem-gstreamer and for the first time totem actually plays stuff.

I'm trying to install w32 codecs but it seems my repositories do not have them;

[PHP]## Uncomment the following two lines to fetch updated software from the network
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse universe main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted[/PHP]

Could someone post a sources list that has the codecs?

---

### Post by TristanMike on 2005-09-04
Copy/paste over current list with list from step number 4 here [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories).

Then don't forget to save and "sudo apt-get update" via the terminal.

---

### Post by Steve1961 on 2005-09-05
To get xine installed you need to install xine-ui in synaptic.  You can then install the win32 codecs by following this thread:

[http://ubuntuforums.org/showthread.php?t=54399](http://ubuntuforums.org/showthread.php?t=54399)

I think you can install win32 codecs with synaptic if you're using Ubuntu 386i, but not Ubuntu 64, unless they've updated the repositories.

---

### Post by Irony on 2005-09-05
xine has popped up in Applications on booting up today. The repositories listed is the one from ubuntuguide but didn't seem to have w32codecs in it.

Its actually a wmv9 file I'm trying to get play - I'm gradually getting more types of files to play!

---

### Post by Steve1961 on 2005-09-05
Is a wmv9 file a music file created in windows media player 9?  If so, I can play these in Xine after downloading the win32 codecs mentioned in the previous thread - from the mplayer website.

---

### Post by Irony on 2005-09-07
Its a microsoft asf video - I can hear the sound but nothing visible.

---

