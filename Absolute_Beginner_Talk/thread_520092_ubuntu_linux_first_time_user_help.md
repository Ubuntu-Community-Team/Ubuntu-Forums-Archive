---
title: "ubuntu linux first time user help"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by hyg71886 on 2007-08-07
I'm running the os off of the cd n im liking it already, the gui looks really good. And i already use mozilla as my web browser. I luv the fact that u have 4 work places so u can do different things in different windows. I cant seem to install any programs though, can anyone help with that?

---

### Post by Rocket2DMn on 2007-08-07
There is the almighty Installation thread on this forum, you should have a look (it's very detailed)
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)
and there is also:
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

If you have any program-specific setup questions, feel free to ask.  Welcome to Ubuntu!

---

### Post by tgm4883 on 2007-08-07
> **hyg71886 said:**
> I'm running the os off of the cd n im liking it already, the gui looks really good. And i already use mozilla as my web browser. I luv the fact that u have 4 work places so u can do different things in different windows. I cant seem to install any programs though, can anyone help with that?

Well you would install them by going to System > Administration > Synaptic Package Manager

But nothing will stay installed as your in a read only environment

---

### Post by roncrump on 2007-08-07
I think you actually need to install Ubuntu to the hard drive and then boot into that before you can start installing extra software. The live CD wouldn't have anywhere to install programs to.

Ron.

---

### Post by K.Mandla on 2007-08-07
Ron's right: You're better off installing software once you've installed the operating system to a hard drive. You can install things in the live environment, but you'll run out of space very fast, and when you shut down the computer it's all gone. :|

---

### Post by Jimcanoa on 2007-08-07
As far as I know, and I am actually quite sure about it, you can definitely install software on the LiveCD, problem is, like someone said a couple of posts above, it won't be there if you shut down the computer and boot again into the LiveCD.
In any case, installing programs is extremely easy:
Open a terminal (I assume you already know how to do this...) and enter:
```
gksudo gedit /etc/apt/sources.list
```
gedit (a text editor) will open and show you some lines... erase all of them and paste this instead:
 
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://es.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://es.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://es.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://es.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://es.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

Save it, and back in the terminal enter:
```
sudo apt-get update
```
And now you're ready to install a program, to do it simply type:
```
sudo apt-get install name_of_the_program
```

EDIT:
I just realised that downloading software  might be slower for you than for me since I'm in Spain and so are those repositories I listed above... But it should work nevertheless...

---

