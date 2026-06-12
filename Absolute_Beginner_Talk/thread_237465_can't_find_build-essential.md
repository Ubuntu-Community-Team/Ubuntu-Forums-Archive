---
title: "can't find build-essential"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by nilzee on 2006-08-16
does any one know where 'build-essential' package is? I looked using the package manager but i can't seem to find it. :confused: please help

---

### Post by meng on 2006-08-16
That's funny, it's in the standard repositories. Are you sure you spelt it correctly?

---

### Post by mcneely.mike on 2006-08-16
i think you have to enable the multiverse repositories in synaptic

---

### Post by Dinerty on 2006-08-16
Tried

 ```
sudo apt-get install build-essential
```

---

### Post by az on 2006-08-16
No.  It id not in multiverse - multiverse is for proprietary non-free software.  Build-essential is most definitely free-libre!

If you are not on the net, when at your ubuntu desktop, insert the installer cd again.  The package manager will start and you will be able to install build-essential from the cd.

build-essential is on a repo on the cd, apart from the live session.

---

### Post by phossal on 2006-08-16
The command you're using is correct: sudo apt-get install build-essential. You're right, though, you will not find it without updating your repositories. A simple way to do this is to find an "updated" copy of the /etc/apt/sources.list file which is the text-based list of repositories. 

Do this: 
```

sudo gedit /etc/apt/sources.list

```

Delete everything.  Paste the following:
```

## BEGING COPYING
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
## END COPYING

```

Now get the build-essential package
```

sudo apt-get install build-essential

```

---

