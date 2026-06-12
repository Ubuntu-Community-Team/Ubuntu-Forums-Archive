---
title: "repository isues"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by joel1a on 2007-04-01
Just upgraded to 6.10 but I went to in stall libmtp2  I got this:



E: Malformed line 2 in source list /etc/apt/sources.list.d/dapper-multiverse.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

How do I fix this?  I'm sure it was something that I did but I don't know what.

Joel

---

### Post by taurus on 2007-04-01
Edit /etc/apt/sources.list.d/dapper-multiverse.list

```
gksudo gedit /etc/apt/sources.list.d/dapper-multiverse.list
```
and place a # in front of the second line.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

But since you upgraded from Dapper to Edgy, why do you still have repos for Dapper in there?

---

### Post by joel1a on 2007-04-01
"But since you upgraded from Dapper to Edgy, why do you still have repos for Dapper in there?"

I don't know...  I was wondering the same thing should I go into the repositories (god help me) and take them out?

By the way, it worked.  :)

---

### Post by taurus on 2007-04-01
If you are running Edgy right now, you should only use Edgy repos so try to replace dapper with edgy then.

---

### Post by ubunter1 on 2007-04-03
mine is a malformed line 2 how can i edit this?-
 E: Malformed line 2 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by Maestro23 on 2007-04-03
.

---

### Post by taurus on 2007-04-03
> **ubunter1 said:**
> mine is a malformed line 2 how can i edit this?-
 E: Malformed line 2 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by ubunter1 on 2007-04-03
thanks for the help,here it is- 


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe restricted multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) ubuntu 6.06-plf free non-free.
# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) ubuntu6.06lts-plf free non-free.


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe multiverse restricted

robert@robert-desktop:~$

---

### Post by taurus on 2007-04-03
> **ubunter1 said:**
> thanks for the help,here it is- 


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe restricted multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) ubuntu 6.06-plf free non-free.
# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) ubuntu6.06lts-plf free non-free.


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe multiverse restricted

robert@robert-desktop:~$

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of these lines.

```
#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy
```
Save it.  Then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ubunter1 on 2007-04-03
ok i did that but when i terminal-update,i get this
E: Malformed line 35 in source list /etc/apt/sources.list (dist parse)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Malformed line 35 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

---

### Post by taurus on 2007-04-03
Can you post your /etc/apt/sources.list again?

```
cat /etc/apt/sources.list
```

---

### Post by ubunter1 on 2007-04-03
robert@robert-desktop:~$ cat /etc/apt/sources.list

#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe restricted multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) ubuntu 6.06-plf free non-free.
# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) ubuntu6.06lts-plf free non-free.


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe multiverse restricted

robert@robert-desktop:~$ 

thanks:)

---

### Post by taurus on 2007-04-03
Well, you forgot to add the # in front of these two lines (near the bottom of /etc/apt/sources.list).

```

#deb http://archive.ubuntu.com/ubuntu/ edgy

#deb http://archive.ubuntu.com/ubuntu/ edgy

```

---

### Post by ubunter1 on 2007-04-03
i just noticed that these 2 dont have the number symbol i added and saved earlier- deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy
should i do that?oops will do now.

---

### Post by ubunter1 on 2007-04-03
its now updating,hopefully this will work.thanks alot for the help.

---

### Post by Fenrir22 on 2007-04-07
Hi, 
I think I messed up pretty badly with my repo.. It has now completely "disappeared". So first is there a way to restore it to default? 
Then the reason i messed up with it is that made a vain attempt at installing ntfs-3g by following this thread: [http://ubuntuforums.org/showthread.php?t=217009&highlight=FAT32](http://ubuntuforums.org/showthread.php?t=217009&highlight=FAT32)

When I updated it gave me E: malformed line 33...  and whe I tried to fix that it just kept getting worse until I got an empty source.list...

please help

---

### Post by zvacet on 2007-04-07
I don´t know wich version do you use and for that reason here is main page.You will find what are you looking for in** add extra repositories **
[http://easylinux.info/wiki/Main_Page]("http://easylinux.info/wiki/Main_Page")

---

### Post by Fenrir22 on 2007-04-07
Thanks it's all resolved now.

---

