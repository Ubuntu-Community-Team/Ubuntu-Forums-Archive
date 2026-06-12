---
title: "[SOLVED] &amp;quot;Whats owle this thean&amp;quot;?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-08-03
[IMG]http://i72.photobucket.com/albums/i189/tito0096/Screenshot-3.png[/IMG]
I get this after I got an error and it told me to run something in the terminal and I forgot the code. . . .

---

### Post by heimo on 2007-08-03
What additional repositories have you used to install software, especially virtualbox? Package with that name doesn't exist in official Ubuntu sources. If you've removed repository in Synaptic Package Manager, add it back and try again. Or completely remove virtualbox if you don't need it.

---

### Post by ~~Tito~~ on 2007-08-03
Huh? how do I remove it? I never installed it or at least couldn't.

---

### Post by ~~Tito~~ on 2007-08-03
Bump.

---

### Post by Inxsible on 2007-08-03
run this command to see if you have virtualbox installed

```
apropos -M / virtualbox
```

---

### Post by Paulmd on 2007-08-03
> **~~Tito~~ said:**
> [IMG]http://i72.photobucket.com/albums/i189/tito0096/Screenshot-3.png[/IMG]
I get this after I got an error and it told me to run something in the terminal and I forgot the code. . . .

This is virtualbox
[http://www.virtualbox.org/wiki/VirtualBox](http://www.virtualbox.org/wiki/VirtualBox)

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

It's not part of the official Ubuntu distribution. Therefor it must be part of an unofficial repository (or something that depends on it is). which are in the etc/apt/sources.list file To open it up (read only), go to the terminal:

```
gedit /etc/apt/sources.list,
```

 copy and paste what's there, so we can find the cuplrit.

These are the supported repositories:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

```

---

### Post by splintercellguy on 2007-08-03
sudo dpkg --force-remove-reinstreq --remove virtualbox

---

### Post by ~~Tito~~ on 2007-08-07
Thanks ^ that helped it. It updates **Sighs**

---

