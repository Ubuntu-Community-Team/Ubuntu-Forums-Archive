---
title: "Easyubuntu please help"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-13
when i try installing things with easyubuntu i get this message

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_P
ackages)



Then this 


Could not apply changes!
Fix broken packages first

What should i do?

---

### Post by Zaffe on 2006-09-13
cat /etc/apt/source.list

Post what u get

---

### Post by haxer on 2006-09-13
oem@haxer:~$ cat /etc/apt/source.list
cat: /etc/apt/source.list: No such file or directory


but when i go to the directory it is a source.list file :S

---

### Post by Zaffe on 2006-09-13
my mistake, cat /etc/apt/sources.list

---

### Post by haxer on 2006-09-13
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiversedeb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

#
# #deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main



omg long list hope youll find the problem :)

---

### Post by jordanmthomas on 2006-09-13
```

gksudo gedit /etc/apt/sources.list

```
You should probably delete the first line of this file as it is malformed appears to be a duplicate of the next to last line.

My solution would probably be this:
*line 1*:  Insert a return before the second appearance of the word deb
*next to last line*:  put a # at the start of it

---

### Post by haxer on 2006-09-13
I dont understand not to good at english either but i think i did right but now i got this message the same message but it seems to be alrigh becouse i can make options in easyubuntu so i think i installed everything i wanted :) thx :P

---

