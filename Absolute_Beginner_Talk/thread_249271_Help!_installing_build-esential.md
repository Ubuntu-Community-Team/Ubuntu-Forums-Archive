---
title: "Help! installing build-esential"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Chris85r on 2006-09-02
I am a newbie to linux, and i am trying to install build-essential.  This is what i get:

christopher@christopher-laptop:~$ sudo apt-get update
Password:
Reading package lists... Done
christopher@christopher-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essential



PLEASE HELPME

---

### Post by taurus on 2006-09-02
What does your /etc/apt/sources.list look like then???

```
more /etc/apt/sources.list
```

---

### Post by jineesh on 2006-09-02
hi
  hope u have root paswd. follow this path 
  system->administarion->update manager
  it will update u r system.
  then
  sudo apt-get install build-essential
  will install all files
  all the best
                 jin

---

### Post by Chris85r on 2006-09-02
christopher@christopher-laptop:~$ more /ect/apt/sources.list
/ect/apt/sources.list: No such file or directory

---

### Post by taurus on 2006-09-02
> **Chris85r said:**
> christopher@christopher-laptop:~$ more /ect/apt/sources.list
/ect/apt/sources.list: No such file or directory
Check your typing!!!  It's **/etc/apt/sources.list**, NOT /ect/apt/sources.list...

---

### Post by Chris85r on 2006-09-02
Sorry about that.

christopher@christopher-laptop:~$ more /etc/apt/sources.list

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ
erse multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted
universe multiverse

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by taurus on 2006-09-02
No wonder you can't install anything!!!  You don't have any repo set to open in your /etc/apt/sources.list.  So, you need to remove the # in front of all the lines with deb...

```
gksudo gedit /etc/apt/sources.list
```
Save it and run

```

sudo aptitude update
sudo aptitude install build-essential

```

---

### Post by Chris85r on 2006-09-02
Thanks Alot you are a lifesaver

---

### Post by taurus on 2006-09-02
You're welcome.  Now, you can install whatever else you want with aptitude...

---

### Post by Chris85r on 2006-09-02
Alright one more question.. sorry to bug you i have 2 systems one running ubuntu and one kubuntu,(I am trying to see if I like KDE or GNOME better) do you know i would do that same thing in kubuntu. i tryed it and i didnt work..Thankx

---

### Post by taurus on 2006-09-02
What did you try and didn't work!!!  Perhaps you need to open a terminal and use nano instead!

```
sudo nano /etc/apt/sources.list
```
Then, <Ctrl>x to save it, holding down <Ctrl> while pressing x...

---

### Post by Chris85r on 2006-09-02
I got it using nano.  Thank you so much.

---

### Post by taurus on 2006-09-02
Remember, gedit is a GUI editor for Gnome while nano is a text editor and it, nano, should work on whatever window manager you are running.  Quite handy to know...

---

