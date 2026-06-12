---
title: "&quot;Can Not Authenticate&quot;"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by aaaantoine on 2007-08-02
I don't know if I broke something at some point.  On the first day, any time I ran apt-get install, the only confirmation I would receive is, "Do you want to download xxMB worth of files? [Y/n]" (paraphrased, obvously).

But since yesterday, any time I run apt-get install, I get a warning that the system CAN NOT AUTHENTICATE the package (emphasis not mine).  Meanwhile, I'm not downloading anything out of the ordinary; just what's recommended in the support threads here.

I figure if the files cannot be authenticated, there is a strong possiblity that I'll get rootkitted (or maybe I already am) if I keep downloading stuff without authentication.  Is there something I need to configure to make this stop?

Thanks in advance.

---

### Post by taurus on 2007-08-02
Did you by any chance add a repo in your /etc/apt/sources.list?  Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by aaaantoine on 2007-08-02
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

---

### Post by nigul on 2007-10-23
I am having the same problems. I just installed Gutsy fresh. I used the alternate cd so I could use full hard drive encryption. Now Automatix is giving me errors. But when I do apt-get on the same packages it works. But I get the package is not authenticated message when using apt-get. I am assuming that this is messing automatix up. I have not changed anything in the repositories. I am checking with someone that I work with if they are receiving the same thing. Will post back, in the meantime, does anyone know what is causing this? Maybe user error? :)

Just heard from him. He did 5 installations and none of them are doing this. He had one installed using the alternate CD for hard drive encryption as I did.

---

### Post by nigul on 2007-10-24
I tried it again today. This time there are not any messages about authenticate packages when using sudo apt-get. I turned off IPv6 following this guide before I tried sudo apt-get. So I'm not sure if this was causing the problem or not.

[http://ralph.n3rds.net/index.php?/archives/177-How-to-Disable-IPV6-in-Ubuntu.html](http://ralph.n3rds.net/index.php?/archives/177-How-to-Disable-IPV6-in-Ubuntu.html)

I also found out today that where I work is in the process of changing things to IPv6, so not sure if a network problem was causing the problems either, but I do not think so. They have been changing the network stuff for a week or so now.

Since no one else has posted I would try turning IPv6 off aaaantoine. If it doesn't work you can always turn it back on if you need it.

---

