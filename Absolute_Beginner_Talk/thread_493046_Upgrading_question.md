---
title: "Upgrading question?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by meniscus on 2007-07-05
Im upgrading from dapper to edgy from yere method here 

[http://ubuntuforums.org/showthread.php?t=227052](http://ubuntuforums.org/showthread.php?t=227052)

Im using part B alternative method

Everything seemed to go ok when i typed
```

sudo aptitude update 
```

But when i typed 
```

sudo aptitude dist-upgrade
```

I got the following prompt at the end



```

Leave the following dependencies unresolved:
nautilus recommends fam
Score is -1381

Accept this solution? [Y/n/q/?]


```

Which should i pick Y n or q?

---

### Post by kuja on 2007-07-05
This is the one thing I hate about aptitude. These dialogs are usually useless IMO. 

If you pick "no" it will give you another option, then another, then another ... 

Try saying yes, then afterwards, run "sudo aptitude install nautilus"

---

### Post by meniscus on 2007-07-05
Hi, yes went through all that.. and restarted the machine an version is still dapper one.

I started the process again and when i type 

sudo aptitude update


this time it gives

```
E: Malformed line 20 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 20 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
stewart@shickey:~$ sudo aptitude update
E: Malformed line 20 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 20 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.


```




Her is my souces list if it is any help

```
#deb cdrom:[Ubuntu 5.10 _edgyBadger_ - Release i386 (20051012)]/ edgymain restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src http://archive.ubuntu.com/ubuntu edgymain restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.# deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted

# deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgyuniverse main restricted multiverse
[COLOR="Red"]deb-src http://archive.ubuntu.com/ubuntu edgyuniverse
[/COLOR]
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe


```



I tried commenting out line 20 (in red) and it only gives 2 errors with s```
udo aptitade update
```

But when i try the dist upgrade and restart my version is still dapper!

Any clues as to what ive done wrong?

---

### Post by meniscus on 2007-07-05
Sorry got it! It was an error in the sources list! 
Thanks

---

