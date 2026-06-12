---
title: "wget is not known"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by meteora184 on 2006-11-25
i can't install anything: this is what i get when i try it. 

i enter: sudo apt-get install *

E: Type 'wget' is not known on line 36 in source list /etc/apt/sources.list
E: The list of sources could not be read.

that happens whenever i try and install anything, and it obviously is a big drawback.

---

### Post by taurus on 2006-11-25
What exactly are you trying to install because "sudo apt-get install *" is not going to work?  You need to replace the * with a name of a package!!!

---

### Post by Arisna on 2006-11-25
Post the contents of /etc/apt/sources.list .  It sounds like something incorrect was added to it.  Press Alt+F2 and enter the following:

```
gedit /etc/apt/sources.list
```

Select all, copy, and paste in a message here.

---

### Post by meteora184 on 2006-11-25
well of course, i tryed to install alot of things, such as wmmx, and stuff.

and heres my sources.list


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9c7c | sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2
 echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main" | sudo tee -a /etc/apt/sources.list
exit
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by bodhi.zazen on 2006-11-25
> **meteora184 said:**
> i can't install anything: this is what i get when i try it. 

i enter: sudo apt-get install *

E: Type 'wget' is not known on line 36 in source list /etc/apt/sources.list
E: The list of sources could not be read.

that happens whenever i try and install anything, and it obviously is a big drawback.

You have a bad line in /etc/apt/source.lst, one starting with wget ?

Post /etc/apt/source.lst

(that is a small "L" and not the number 1)

---

### Post by Arisna on 2006-11-25
```
wget http://www.getautomatix.com/apt/key.gpg.asc
 gpg --import key.gpg.asc
 gpg --export --armor 521A9c7c | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install automatix2
 echo "deb http://www.getautomatix.com/apt dapper main" | sudo tee -a /etc/apt/sources.list
 exit
```

These lines were meant to be executed in a terminal, not added to /etc/apt/sources.list.  Remove them from the file.  Also remove the last line you posted.  Execute those commands in a terminal (one of them will add back that last line, which is ok).

Terminal can be accessed through Applications > Accessories > Terminal .

---

### Post by bodhi.zazen on 2006-11-25
Remove this entire section:> wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9c7c | sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2
echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main" | sudo tee -a /etc/apt/sources.list
exit

You can leave this line:

> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by meteora184 on 2006-11-25
h;ow would i make it not read-only?

---

### Post by Arisna on 2006-11-25
Do Alt-F2 again, but this time enter:

```
gksudo gedit /etc/apt/sources.list
```

This will allow you to edit it with administrative privileges.

---

### Post by taurus on 2006-11-25
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

