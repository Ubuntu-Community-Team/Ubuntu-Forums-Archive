---
title: "Major Failure of my software management system"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by harerama on 2006-09-09
When I run Applications>Add/Remove Applications.
Pop up messages appears and it says
-----
Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.
-----
Basically I have no idea what to do.
How can I check the file permissions and corectness?
Can anyone help?

Thanks

---

### Post by Tomosaur on 2006-09-09
Open up a terminal, and type:
```

ls -l /etc/apt/sources.list

```

Paste what it says here please.

---

### Post by harerama on 2006-09-09
-rw-r--r-- 1 root root 2207 2006-09-10 07:23 /etc/apt/sources.list

this is what it says

---

### Post by Tomosaur on 2006-09-09
Looks fine to me then.
Just try running 'sudo apt-get update'

---

### Post by harerama on 2006-09-09
Oh Thanks then it says,

E: Malformed line 32 in source list /etc/apt/sources.list (dist)

Any Idea what I can do?

---

### Post by Tomosaur on 2006-09-09
Try pasting your /etc/apt/sources.list file up here, looks like you've messed  something up in there.

---

### Post by harerama on 2006-09-09
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
--------------------------------------------------------------------------
Here. I did mess up some.....
Thanks.

---

### Post by jordanmthomas on 2006-09-09
Starting at deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) you haven't told apt where to go after that.
Whatever told you to add those repositories may have been wrong

```
gksu gedit /etc/apt/sources.list
```
and add "dapper main" (without quotes) to the last 5 lines and sudo apt-get update should work.

---

### Post by harerama on 2006-09-09
deb [http://archive.ubuntu.com/ubuntudappermain](http://archive.ubuntu.com/ubuntudappermain)
deb-src [http://archive.ubuntu.com/ubuntudappermain](http://archive.ubuntu.com/ubuntudappermain)
deb [http://packages.freecontrib.org/ubuntu/plfdappermain](http://packages.freecontrib.org/ubuntu/plfdappermain)
deb-src [http://packages.freecontrib.org/ubuntu/plfdappermain](http://packages.freecontrib.org/ubuntu/plfdappermain)
deb [http://archive.canonical.com/ubuntudappermain](http://archive.canonical.com/ubuntudappermain)

Ok Like this? Probably not.

---

### Post by jordanmthomas on 2006-09-09
you need a space before dapper in each one.  Sorry I didn't tell you that.

Also, if this doesn't work you can temporarily remove those last 5 by putting a # at the start of each line.

---

### Post by harerama on 2006-09-09
Thank you so much.
It seems OK.
How knowledgble you guys are! =D> 

Thank you.

---

### Post by jordanmthomas on 2006-09-09
I definitely wouldn't consider myself knowledgable, but thanks.

---

