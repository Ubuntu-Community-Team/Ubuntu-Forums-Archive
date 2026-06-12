---
title: "C compiling"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by epq on 2006-08-26
I have just recently installed Ubuntu, but have been programming in C on Linux for some years in college (a maths, not a computers course).
I thought C came naturally on Linux but I just wrote a basic programme and on trying to compile it, gcc -o test test.c, was informed that the gcc command is not contained in bash.
I search the forums and found a suggestion to run the following command:

sudo apt-get install build-essential

However, I the following message came up:

Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

Does anyone have any suggestions?
Thanks

---

### Post by Crosbie on 2006-08-26
Weird.  Try it via Synaptic if you can?  Can you find the build-essential package?

---

### Post by cstudent on 2006-08-26
Do you have all the repositories enabled?

Look under System menu > Administration > Software Properties.

Make sure universe and multiverse repos are enabled. Then try again.

---

### Post by epq on 2006-08-26
I have all channels in the repositories open but when i search for build-essential all it comes up with is a package called sbuild

---

### Post by cstudent on 2006-08-26
Probably obvious question, but, did you update your sources.list before checking again?

If so then post a copy of your sources list here so we can see if there is not a problem there.


If you're not sure how to post it. Type in at a terminal window:
```

gedit /etc/apt/sources.list

```

Select all the text, copy and then paste it in a new post.

---

### Post by Buffalo Soldier on 2006-08-26
1. Just to be sure, what's the content of your **/etc/apt/sources.list** file?

2. Did you remember to```
sudo apt-get update
```first before```
sudo apt-get install build-essential
```?

---

### Post by taurus on 2006-08-26
Build-essential is also on the CD!!!

---

### Post by epq on 2006-08-26
Here is my sources list:

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


I also tried 'sudo apt-get update' before 'sudo apt-get install build-essential' and it made no difference

---

### Post by cstudent on 2006-08-26
This is a copy from my sources.list. It contains only the officially supported Ubuntu repos. Download it to your /home/youruser directory and try the following.

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak20060826

```
```

sudo cp /home/yourusername/sources.list /etc/apt/sources.list

```
```

sudo apt-get update

```
```

sudo apt-get install build-essential

```

---

### Post by cstudent on 2006-08-26
Sorry, forgot to attach the file. :rolleyes:

You'll have to rename it to sources.list.

---

### Post by epq on 2006-08-26
That's great.
Thanks a million, it's working now.

---

### Post by cstudent on 2006-08-26
My pleasure. :)

---

