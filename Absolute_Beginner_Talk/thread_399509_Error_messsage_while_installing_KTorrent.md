---
title: "Error messsage while installing KTorrent"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by reddust on 2007-04-02
Hiya all.

I am still new with Ubuntu, I am currently trying to give Ktorrent a try. While running apt-get command. I encountered the following error. 

mngkl@smngkl-desktop:~$ sudo apt-get install ktorrent
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ktorrent: Depends: kdelibs4c2a (>= 4:3.5.2) but it is not going to be installed
            Depends: libpcre3 (>= 4.5) but it is not going to be installed
            Depends: libqt3-mt (>= 3:3.3.6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

It said, I can get apt-get -f to install the application. What are the consequence if I do that? Can I actually resolve the dependency problem?

Kind regards,

---

### Post by JNowka on 2007-04-02
I personally would advise you to install ktorrent through synaptic package manager.  This will usually install it for you.  I would also suggest making sure you enable all of the repositories in the /etc/apt/sources.list file.  Here is an example for an edgy eft system. 

> 
## Ubuntu Security Repositories
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 

## Ubuntu Archives Repositories
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse 


In order to edit your sources.list file you will type 
> gksu gedit /etc/apt/sources.list 
at the command line.  I hope this helps.

If you still are having problems, come back to the forums.

---

### Post by zvacet on 2007-04-02
```
sudo apt-get install kdelibs4c2a
```
Do the same with two other dependencies.In the future to avoid this kind of situation install with aptitude

```
sudo aptitude install package_name
```

With aptitude you will download program and al dependencies

---

### Post by reddust on 2007-04-04
Guys thank you all. It worked fine.

---

