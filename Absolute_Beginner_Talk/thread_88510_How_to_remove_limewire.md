---
title: "How to remove limewire?"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by Animus on 2005-11-10
I installed Limewire (using the instructions from the Ubuntu 5.04 starters guide) but have found that it make Ubuntu crash when I use it, and is also a resource hog.  I'm trying amule now, and want to get rid of limewire, but the command sudo apt-get remove limewire turns up a "could not find package" response.  I also cannot find it anywhere in synaptic.  Does anyone know how I can uninstall limewire from my system?

---

### Post by patrick295767 on 2005-11-10
[QUOTE=Animus]I installed Limewire (using the instructions from the Ubuntu 5.04 starters guide) but have found that it make Ubuntu crash when I use it, and is also a resource hog.  I'm trying amule now, and want to get rid of limewire, but the command sudo apt-get remove limewire turns up a "could not find package" response.  I also cannot find it anywhere in synaptic.  Does anyone know how I can uninstall limewire from my system?[/QUOTE]
  
a bit strange... 
apt-get remove limewire
(apt-get clean         to clean the downloaded install files) 
  
try in xterm
: limewire &
is it working ?

---

### Post by Animus on 2005-11-10
I'm afraid I'm not quite sure what the xterm is you're referring to, or how to use it.

I tried sudo apt-get clean remove limewire, still nothing

Kinda frustrating, but hopefully it'll get worked out...

---

### Post by Animus on 2005-11-11
bump

---

### Post by ibanez88 on 2006-01-02
I just started experiencing this same problem.  Started up Limewire for the first time on this install, worked fine all day.  But now it locks up Gnome entirely when I try and start the app, have to ctrl-alt-backspace and log in again.

So I figured I should try and remove it, then reinstall... but sudo apt-get remove limewire gives "Couldn't find package limewire".  And sudo apt-cache search limewire gives no output.  In Synaptic, searching for "limewire" or "Lime Wire" gives no results.  What gives?

EDIT:  I can run it without freezing, started in a terminal by running /user/bin/runLime.sh (as discovered from Gnome menu editor).

Here is my /etc/apt/sources.list if it helps:

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


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
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by cstudent on 2006-01-02
[QUOTE=Animus]I installed Limewire (using the instructions from the Ubuntu 5.04 starters guide) but have found that it make Ubuntu crash when I use it, and is also a resource hog.  I'm trying amule now, and want to get rid of limewire, but the command sudo apt-get remove limewire turns up a "could not find package" response.  I also cannot find it anywhere in synaptic.  Does anyone know how I can uninstall limewire from my system?[/QUOTE]

If you installed using the 5.04 UbuntuGuide then apt-get will not uninstall it because you didn't install it that way. The bulk of the software is under the /opt directory. To remove it following the UbuntuGuide's install instructions you would do the following using the terminal.

```


sudo rm -rf /opt/LimeWire

sudo rm /usr/bin/runLime.sh

sudo rm /usr/share/applications/LimeWire.desktop


```

---

### Post by hesjnet on 2008-05-18
> **cstudent said:**
> 
```


sudo rm -rf /opt/LimeWire

**sudo rm /usr/bin/runLime.sh**

sudo rm /usr/share/applications/LimeWire.desktop


```

Thanks! My limewire got removed, i think..

The only problem is that when wrote on of the commands, i got this error:
```
root@Gullbarren:~# sudo rm /usr/bin/runLime.sh
rm: cannot remove `/usr/bin/runLime.sh': No such file or directory

```

Limewire doesnt show in my program menu anymore but is it still in my system?

Ubuntu 8.04LTS

---

