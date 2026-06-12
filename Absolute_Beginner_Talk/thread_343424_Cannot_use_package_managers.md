---
title: "Cannot use package managers"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by mythrilfan on 2007-01-21
Hi, new here. Have been able to solve my problems on my own in the past... but now i'm buggered. First some background like i use ubuntu edgy with gnome on an about 3-year old celeron-based laptop. Now the problem is that it does not seem to be possible for me to do anything with packages anymore... nothing works- apt in the terminal, synaptic... neither do the smaller wizards like the update manager nor add/remove. 
I get an error: ```
E: /var/cache/apt/archives/tzdata_2006p-0ubuntu6.10_all.deb: files list file for package `update-notifier' contains empty filename

```
Note that this is not the first message like this on this computer, i got some under the same circumstances which were almost identical save for the .deb file, but i seemed to fix those by copying the files from my working edgy install on another computer to this one. However, this method did not work with the current file. Also, as suggested in [http://www.informit.com/articles/article.asp?p=667418&rl=1](http://www.informit.com/articles/article.asp?p=667418&rl=1) i tried
```
sudo apt-get update
sudo apt-get -f install
```
but this didn't work either.
I have no clue how or when this problem occurred, and am now waiting for some response. :biggrin: There's always the possibility of a reinstall, but that would be windowsy and i'd hate that. Is there a way to rebuild the .debs?
Thanks in foreway, but if we get THIS file fixed, i'm afraid there'll be another quintillion like it. So the best things would be to somehow repair-install ubuntu w/o losing my programs and files, or just repairing the folder.

---

### Post by stijn_pol on 2007-01-21
Something wrong with /etc/apt/sources.list maybe?
Perhaps you can post it. Don't know for sure...

---

### Post by lamego on 2007-01-21
Just delete the file /var/cache/apt/archives/tzdata_2006p-0ubuntu6.10_all.deb

---

### Post by garyinok on 2007-01-21
Try the following link:

[http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)

I had a similar problem which the following solved.

# apt-get -f install
# dpkg --configure -a

Hope this helps.

---

### Post by mythrilfan on 2007-01-21
my sources.list is here:

> # 
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END


---

### Post by mythrilfan on 2007-01-21
> **lamego said:**
> Just delete the file /var/cache/apt/archives/tzdata_2006p-0ubuntu6.10_all.deb

i did... it *magically* reappears upon the next package manager start (when i try to upgrade something that is, or "apply" in synaptic) and gives me the same error.

---

### Post by mythrilfan on 2007-01-21
Have some new information for You. When i sudo apt-get -f install, it says this: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpcre3 python-orbit libimlib2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.

```
and so, indeed i sudo apt-get autoremove. then it tells me
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpcre3 python-orbit libimlib2
The following packages will be REMOVED:
  libimlib2 libpcre3 python-orbit
0 upgraded, 0 newly installed, 3 to remove and 29 not upgraded.
Need to get 0B of archives.
After unpacking 1208kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `xsane-common' missing, assuming package has no files currently installed.
dpkg: error processing libimlib2 (--remove):
 files list file for package `update-notifier' contains empty filename
Errors were encountered while processing:
 libimlib2
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

of course, i again tried to 
```
apt-get -f install
dpkg --configure -a
```
and i even inputted the last line FIVE times (in reference to the site's help: And then try again. It may be necessary to run the second of the above commands more than once. This is an important lesson for those adventurers who use `unstable'.):wink: . But to no avail, i still get the same message. This is all i know for now, i hope someone can figure it out by the time i wake up in the morning, it's getting late :biggrin: 
Thanks for the replies so far.

---

### Post by mythrilfan on 2007-01-25
bump

---

### Post by mythrilfan on 2007-01-27
well, bump again, if there's no hope forthcoming i'll be busy reinstalling the bloody thing tomorrow. sad. it seems amazing that i managed to screw it up so fast and so completely, there's no coming back.

---

### Post by mlissner on 2007-10-26
Hummm...I have a very similar problem, but no solution here either:
[http://ubuntuforums.org/showthread.php?t=591910](http://ubuntuforums.org/showthread.php?t=591910)

EDIT: I figured out a solution for myself at that link.

---

