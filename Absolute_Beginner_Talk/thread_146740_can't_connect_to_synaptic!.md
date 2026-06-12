---
title: "can't connect to synaptic!"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by stefenkillsit on 2006-03-18
every time I try and download things, it always times out, my internet works though, what's wrong?

0% [Connecting to us.archive.ubuntu.com (1.0.0.0)]
it just stays like that, what should I do?

---

### Post by jasay on 2006-03-18
The US archieves are flakey sometimes.  I'd ```
sudo gedit /etc/apt/sources.list
``` and remove the "us." from each line.  Then ```
sudo apt-get update
``` and see if works.

---

### Post by WoodyMahan on 2006-03-18
From another user when I had similar problems.

Synaptic uses a file called sources.list which tells it where to look on the internet for it's files.

To open the editor referenced below use this command in the terminal:
sudo gedit /etc/apt/sources.list

To open the terminal, go to Applications, Accessories, Terminal.
To remove the sources.list as referenced below use:
sudo rm /etc/apt/sources.list

Now if this doesn't work, open the sources.list (referenced above) and highlight and delete all content.  Save it as an empty file, open Synaptic and reload.  Then open the sources.list again, and paste back in the info below.

This is what I had to do.  Hope it helps.

Ok, for testing purposes, backup your /etc/apt/sources.list (I would call it BACKUP_sources.list some people use sources.list.bak Use whatever is memorable for you). Then take the copy that is called sources.list (remember you now have a backup) and remove it. Now open an editor and put this into a file called sources.list:
Quote:
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

