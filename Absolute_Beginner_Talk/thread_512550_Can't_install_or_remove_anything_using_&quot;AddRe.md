---
title: "Can't install or remove anything using &quot;Add/Remove&quot;"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by 100%J on 2007-07-29
I have just install Ubuntu 6.06LTS on my computer, It's really cool and everything but I can't install or remove any applications. I'm clicking applications=>add/remove and it takes my to the menu, it informs me that "the list of available applications is out of date" so I'm reloding it. It dosen't really matter whether I reload it or not cause it won't work anyway ( I have checked) after reloding it dispalys lists of available and already installed applications. The problem is that when I try to install something it says that it's "not available in any software channel, the application may not support your system architecture" and it goes like that every time I try to install something, It goes the same when I'm trying to uninstall applications. It's driving me nuts, please help me.

---

### Post by aysiu on 2007-07-29
Can you close Add/Remove and open a [terminal](http://www.psychocats.net/ubuntu/terminal)?

Once the terminal is open, paste in these commands: ```
cat /etc/apt/sources.list
sudo apt-get update
``` and then paste the output back here.

---

### Post by 100%J on 2007-07-29
Here it is, do you know what the problem is?

> j@j-desktop:~$ cat /etc/apt/sources.list

# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ erse multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
j@j-desktop:~$ sudo apt-get update


---

### Post by moffa on 2007-07-29
Almost all of your repositories are commented out.  Take the # infront of the deb and deb-src lines

---

### Post by 100%J on 2007-07-29
I have no idea how to do that to be honest, seriously mate, I have just started this whole Ubuntu experience and I have just used terminal for the first time few minutes ago

---

### Post by Paul820 on 2007-07-29
Open the terminal, type: sudo gedit /etc/apt/sources.list
This will open a text editor, now go through the file and remove the # from the beginning of each line with the word beginning with deb
When that's done save the file and exit. Now sudo apt-get update from the terminal.

---

