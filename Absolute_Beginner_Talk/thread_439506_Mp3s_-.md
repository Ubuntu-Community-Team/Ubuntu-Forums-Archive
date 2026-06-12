---
title: "Mp3s -"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-05-10
Well I'm trying to extract a file called


Tec2007.part3.rar ( which is a Techno CD ) I downloaded.

For some reason I cant extract it.
I get this message.
"The utility runrar is not in your PATH
Please install it or contact your system administration"

Wwondering... What do I do from here to get this extracted?

---

### Post by jvc26 on 2007-05-10
You don't have the unrar package installed by the looks of things - try:
```

sudo apt-get install unrar

```
Il

---

### Post by diatribe on 2007-05-10
what command are you running when you get this message?  but it seems you need to install unrar; 
sudo apt-get install unrar

---

### Post by LollYouSuckZor on 2007-05-10
nic@nic-desktop:~$ sudo apt-get install unrar
Password:
E: Type '-e\n' is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
nic@nic-desktop:~$

---

### Post by stmiller on 2007-05-10
> **LollYouSuckZor said:**
> nic@nic-desktop:~$ sudo apt-get install unrar
Password:
E: Type '-e\n' is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
nic@nic-desktop:~$

Line 34 in the file /etc/apt/sources.list has a problem. Post the output of this:

cat /etc/apt/sources.list

---

### Post by LollYouSuckZor on 2007-05-10
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
-e\n## Beryl repository\ndeb [http://www.ubuntu.beryl-project.org/](http://www.ubuntu.beryl-project.org/) edgy main

sudo tee -a /etc/apt/sources.list
sudo apt-get update

lol
okay
******* a

[ The, F****** a was something I typed out of frustration ^^ ]

---

### Post by aktiwers on 2007-05-10
Do you have all parts ?
.part3 means there are atleast 2 other zip files you need.
Proberbly called  Tec2007.part1.rar and  Tec2007.part2.rar.

If you have all parts I know you normally use Hjsplit to join them.. I think I remember just extracting them from one archive without Hjsplit on Ubuntu, but really dont remember. If it doestnt work, get hjsplit for Linux.. should help you.
[http://ubuntuforums.org/showthread.php?t=160228](http://ubuntuforums.org/showthread.php?t=160228)

---

### Post by diatribe on 2007-05-10
-e\n## Beryl repository\ndeb [http://www.ubuntu.beryl-project.org/](http://www.ubuntu.beryl-project.org/) edgy main

on this line remove -e\n

---

### Post by aktiwers on 2007-05-10
By the way.. this line is wrong in your sourcelist:
```
 -e\n## Beryl repository\ndeb [http://www.ubuntu.beryl-project.org/](http://www.ubuntu.beryl-project.org/) edgy main
```Should be
```
 ## Beryl repository\ndeb [http://www.ubuntu.beryl-project.org/](http://www.ubuntu.beryl-project.org/) edgy main
```

And then run this from terminal:
```
sudo apt-get update
```

To update your sourcelist.

---

