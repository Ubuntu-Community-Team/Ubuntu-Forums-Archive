---
title: "Wine Question"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by K1CK1NVV1NG on 2007-12-11
I am not very far with  with my linux experience. But I have a problem that I am unable to find an answer for. I have joined two forums and done much google research but can not find the answer. Now on to my problem, my problem is, I can not get Wine to install. I used the command line sudo stuff and got all the codes and when I do it, it says The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences. So if anyone knows what to do to fix this your help would be greatly appreciated, and thanks in advance for any help.

---

### Post by Tyke91 on 2007-12-11
I believe you can install wine simply by going to the "Add/Remove" list and searching for "wine"

---

### Post by PmDematagoda on 2007-12-11
Post the result of:-
```

cat /etc/apt/sources.list
```

And also try:-

```
sudo apt-get update
```

Then try installing Wine again.

---

### Post by Rocket2DMn on 2007-12-11
Have you followed the directions from wine's website?
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)
Don't forget to run
```
sudo apt-get update
```
after following that.
If it STILL gives you the error, it's possible that wine's repository is currently down.

---

### Post by K1CK1NVV1NG on 2007-12-11
> **PmDematagoda said:**
> Post the result of:-
```

cat /etc/apt/sources.list
```

And also try:-

```
sudo apt-get update
```

Then try installing Wine again.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


As requested for the first option given.

---

### Post by PmDematagoda on 2007-12-11
Your sources.list file looks fine, do:-

```
sudo apt-get update
```

And see if that solves your problem.

---

