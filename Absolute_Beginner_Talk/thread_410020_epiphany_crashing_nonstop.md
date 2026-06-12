---
title: "epiphany crashing nonstop"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-04-15
Hi all,

I have been using epiphany lately, I like it.

But it keeps crashing.

Now I cannot get it to open.

I was viewing sg on youtbue when it was last opened.

I have tried rebooting the computer. I have tried to restart epiphany.

both to no avail.

robi

---

### Post by bapoumba on 2007-04-15
Hello, not sure I can help you all the way, but d you get any error message starting epiphany from a terminal? (> Applications > Terminal)

---

### Post by beanco on 2007-04-15
Hi.

I got this:


(epiphany:26524): libgnomevfs-WARNING **: Failed to create service browser: Bad state


** ERROR **: file ephy-node.c: line 913 (ephy_node_new_from_xml): should not be reached
aborting...


robi

---

### Post by bapoumba on 2007-04-15
Running first error gave:
[http://ubuntuforums.org/showthread.php?t=256210]("http://ubuntuforums.org/showthread.php?t=256210")
User reinstalled epiphany and that fixed it (user first removed epiphany along with the conf files).
Second error line did not bring up anything usable.

Did you upgrade recently? Did it all go smoothly?

---

### Post by beanco on 2007-04-15
> **bapoumba said:**
> Running first error gave:
[http://ubuntuforums.org/showthread.php?t=256210]("http://ubuntuforums.org/showthread.php?t=256210")
User reinstalled epiphany and that fixed it (user first removed epiphany along with the conf files).
Second error line did not bring up anything usable.

Did you upgrade recently? Did it all go smoothly?

no upgrade recently!

i just used it a ton over the weekend and have a bagillion bookmarks i need to keep...

if I uninstall i will loose those right?

robi

---

### Post by bapoumba on 2007-04-15
in **~/.gnome2/epiphany/** you should have these two files: **bookmarks.rdf **and **ephy-bookmarks.xml**. Although I have never tested it myself, all bookmark infos should be there. You could back them up (I backup some files in .gnome2 on a regular basis, including these two files, but never got to restore epiphany bookmarks so far).

May be start with reinstalling epiphany without purging the conf files first.

---

### Post by beanco on 2007-04-16
when palying round with synoptic i got this

E: /var/cache/apt/archives/hermes1_1.3.3+really1.3.2-5_i386.deb: files list file for package `info' is missing final newline


what the heck does it mean?

robi

---

### Post by beanco on 2007-04-16
> **bapoumba said:**
> in **~/.gnome2/epiphany/** you should have these two files: **bookmarks.rdf **and **ephy-bookmarks.xml**. Although I have never tested it myself, all bookmark infos should be there. You could back them up (I backup some files in .gnome2 on a regular basis, including these two files, but never got to restore epiphany bookmarks so far).

May be start with reinstalling epiphany without purging the conf files first.

thanks for the advice but i am not sure how to do it...

could you wlk me thorugh the steps?

thanks

robi

---

### Post by beanco on 2007-04-16
so it downed on me that I could use mc to make copies of those fiels.. i did so

then i tried 

sudo apt-get remove epiphany-browser

and got this


(Reading database ... dpkg: error processing epiphany-browser (--remove):
 files list file for package `info' is missing final newline
Errors were encountered while processing:
 epiphany-browser
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)



The line *info* is missing final newline is a reoccuring problem. Now if I coudl figure out wha tit means, maybe i could get to the bottom of this.

robi

---

### Post by bapoumba on 2007-04-16
In run this error in both google and the forums:
> files list file for package `info' is missing final newline

The easiest fix looks in post #9 of the following thread:
[http://ubuntuforums.org/showthread.php?t=12737]("http://ubuntuforums.org/showthread.php?t=12737")

---

### Post by beanco on 2007-04-16
I found that thread myself as well but I was not able to understand it...

i will have to learn more computer stuff to grasp these bits o finfo and help.. it is just over my head.

robi

---

### Post by bapoumba on 2007-04-16
1- are you using non-official repositories in your sources.list?
Please post the output to:
```
cat /etc/apt/sources.list
```

2- how long have you been using epiphany, did you install it recently, or some time ago ?
I'm asking because there is a backup file of the /var/lib/dpkg/status that you could restore, but it might be corrupt too.

3- Here are some details that may help you. please read and post any comments or questions you have.

> **hordur said:**
> 
1. Edit the file /var/lib/dpkg/status , look for the listing for the broken package, remove the info for that package.

Here is where my own /var/lib/dpkg/status gives info about epiphany-browser (I'm running feisty, so your might have different version numbers):
```
Package: epiphany-browser
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 13280
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Version: 2.18.1-0ubuntu1
Provides: www-browser
```
There is more to it, I did not paste it (all the dependencies).
According to the post, you have to remove all the infos regarding every package giving you trouble.

This file is in the root file system. You need to be root to edit it.
First save it, just in case:
```
sudo cp /var/lib/dpkg/status  /var/lib/dpkg/status_bak.070416
```

Then edit the file (I like to use nano, a small text editor):
```
sudo nano /var/lib/dpkg/status
```
delete all the infos about epiphany-browser
CTRL-O will save the file (same name, hit enter), CTRL-X to exit nano.

Then run these commands (with **sudo** in front of all of them):
> **hordur said:**
> 
2. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
3. mkdir /var/lib/dpkg/info
4.1 apt-get update
4.2 apt-get -f install
5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
6. rm -f /var/lib/dpkg/info
7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info

If command 4 is giving you errors, stop and please paste them in here.

4- do not worry, you'll make it ;)

---

### Post by beanco on 2007-05-09
HI,

So Thanks for the help...  

> > **bapoumba said:**
> 1- are you using non-official repositories in your sources.list?
Please post the output to:
```
cat /etc/apt/sources.list
```


this is what I got

# deb file:/cdrom dapper main restricted
#
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) dapper main universe restricted
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END
 #ubuntu edgy
deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

[QUOTE]2- how long have you been using epiphany, did you install it recently, or some time ago ?
I'm asking because there is a backup file of the /var/lib/dpkg/status that you could restore, but it might be corrupt too.

A couple of months. I installed and started using Ubuntu around Xmas... epiphanyin Late Jan or Feb sg like that...



As to the info you provide in steps 3 and 4.. .well thanks, i will get to it later today I hope

robi

ps. edited to add.. 
itried to check

> /var/lib/dpkg/status

and got this

robi@robi:~$ /var/lib/dpkg/status
bash: /var/lib/dpkg/status: Permission denied


and this

root@robi:~# /var/lib/dpkg/status
-su: /var/lib/dpkg/status: Permission denied

---

### Post by bapoumba on 2007-05-09
1- you have to edit the files with nano (see my previous post)

2- you have edgy repos in your sources.list. Remove them, it is not a good idea to mix repos from several releases (or distributions). Is the OOo repos for dapper ?

That might be your problem here, start with your sources.list first.

---

### Post by beanco on 2007-05-09
> **bapoumba said:**
> 1- you have to edit the files with nano (see my previous post)

2- you have edgy repos in your sources.list. Remove them, it is not a good idea to mix repos from several releases (or distributions). Is the OOo repos for dapper ?

That might be your problem here, start with your sources.list first.


Being a neophyte deleting things is rather daunting to me.

1 . so do I simply open nanao, if I have it, if not what about another txt editor? , open the files, delete the lines in question, save the file?

2.  not sure about the OOo.. .how do I find out and if it is, what do I do?

Robi

---

### Post by bapoumba on 2007-05-09
OK, lets start with your sources.list. I checked the OOo repo, its for breezy. So lets remove the OOo repo and the edgy ones.

First, save the file, just in case:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
```

Then edit the file with nano, a small text editor that works from a terminal:
```
sudo nano /etc/apt/sources.list
```

[COLOR="Green"]Add a #[/COLOR] in front of the three following lines (in green). That way, the line will be ignored, but not completely deleted (its called "commenting a line", ie set it as a "comment" that will be ignored):

```

# deb file:/cdrom dapper main restricted
#
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) dapper main universe restricted
[COLOR="Green"]# [/COLOR]deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END
 #ubuntu edgy
[COLOR="Green"]# [/COLOR]deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
[COLOR="Green"]# [/COLOR]deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
```

Save the file with CTRL-O (same name, hit enter), the exit nano with CTRL-X.
run:
```
sudo aptitude update
```
and paste the output in here.

Thanks.

---

### Post by beanco on 2007-05-16
Ok, i will try that when I get to my home computer.


had other things to deal with until now. sorry for not getting back to you earlier.

thanks

robi

---

