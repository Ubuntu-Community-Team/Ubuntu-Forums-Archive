---
title: "Odd Repository Problem"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Ronfar on 2006-11-02
Ok I installed these awhile ago and today I was trying to install a program and I kept getting the message "Unable to locate software package". So I was trying to figure out what the problem was and I checked my Repositories and Universal and Multiverse were gone. So I readd them and I tried to install the software again and it gives me the same message, sure enough they were gone again. I then tried to add them several times, restarting my computer, etc and they just won't save. 

Now I never have messed with them again since I added them awhile ago so what could be the problem? Could it be something to do with the Ubuntu updates or is there something else wrong? Any help is greatly apperciated thanks alot!

---

### Post by raul_ on 2006-11-02
Are they available in sources.list?

---

### Post by NeoLithium on 2006-11-02
How did you add them, through the software sources/package manager or by editing /etc/apt/sources.list manually?

---

### Post by Ronfar on 2006-11-02
I did it through the System/Admin/Software Properties. I wasn't that comfortable then with the command line. Do you think adding on the sources list will help? Also when I look at the sources list theres "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse" and other ones similiar to that, so that leads me to believe that they aren't on right? Do I need to delete any of this stuff before adding the code or just add it at the bottom?

---

### Post by raul_ on 2006-11-02
just add them. There's a clean sources.list available in the forum...i'll get it for u

---

### Post by Ronfar on 2006-11-02
Thanks I apperciate it, also I was just curious as to what caused all this in the frist place? I had another similiar problem with my screen resolution changing automatically and I had to end up reconfiguring it through the command terminal.

---

### Post by raul_ on 2006-11-02
copy and paste the following over your existing sources.list if you're using Dapper (6.06):
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free

---

### Post by NeoLithium on 2006-11-02
I've always just gone through manually editing the list; beacuse it's nice and easy, and if you mess up, just take your backup, and revert it.

---

