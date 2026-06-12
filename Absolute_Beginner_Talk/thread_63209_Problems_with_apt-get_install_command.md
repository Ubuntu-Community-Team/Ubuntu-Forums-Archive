---
title: "Problems with apt-get install command"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by ronlondre on 2005-09-07
Hi, 
I am not having success with the apt-get install command.
Last night I installed ubuntu.
Thus far (following the starter guide) I have added extra repositories, manually updated ubuntu, attempted to install menu editor (not yet sure if that worked), and rebooted.

Now I am trying to install Downloader for X.
I have downloaded it and saved it to my desktop. I extracted it to the desktop by right clicking and choosing "extract here"

I opened a terminal and here is what is hapening:
ronlondre@ubuntu:~$ sudo apt-get install d4x
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package d4x

What am I doing wrong

Additionally, should I have utared the file using the terminal. If so how do I do this in ubuntu. I'm not really familiar with how to untar a file.

---

### Post by Lord Illidan on 2005-09-07
apt-get install only installs packages from the repository.
If you have downloaded d4x as source code, "tar", then you do something else to install, either run a .sh file or compile it..

However, are you sure you enabled all the repositories for apt-get?
And did you run ```
sudo apt-get update
``` before you tried getting d4x?

---

### Post by madjo on 2005-09-07
'apt-get install' does not install files you have downloaded locally, instead it grabs the install files from a repository in the internet.. I think you should read the README file (or INSTALL file) in the folder where 'downloader for x' is unpacked... or read the ubuntuguide for more info.

---

### Post by izmaelis on 2005-09-07
Can you show us yours **/etc/apt/sources.list** file. By the way, what happens if you run ```
sudo apt-cache search d4x
``` in your terminal?

---

### Post by ronlondre on 2005-09-07
Here is my **/etc/apt/sources.list** file:
[SIZE=1]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted[/SIZE]

---

### Post by ronlondre on 2005-09-07
Nothing happens when I run "sudo apt-cache search d4x"
Here are the results:
[SIZE=1]ronlondre@ubuntu:~$ sudo apt-cache search d4x
ronlondre@ubuntu:~$[/SIZE]

---

### Post by aysiu on 2005-09-07
[QUOTE=Lord Illidan]
However, are you sure you enabled all the repositories for apt-get?
And did you run ```
sudo apt-get update
``` before you tried getting d4x?[/QUOTE] You never answered this second question. Updating is very important after enabling more repositories.

---

### Post by ronlondre on 2005-09-07
Alright, I see my mistake thank you for redirecting me to **/etc/apt/sources.list** I realize that I did not enter all of the lines I should have.

Thanks much!

---

