---
title: "Problem checking for updates, server update?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by webjames on 2006-11-28
Hi, i've been using Ubuntu 6.10 (Edgy) for a little while now, i've just gone and clicked on the update manager (System > Administration) and i get an error.
if everyone getting the same error at the moment?

enter the following into the terminal to get an update list, the error should be at the end.

```
sudo apt-get update
```

my error is:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

if you'd do this and reply telling me if you get an error, i heard when ubuntu is updating the lists it does this?

Cheers guys,

James

---

### Post by webjames on 2006-11-28
nobody? i have attached a screen shot of my error and here is my sources.list file:

> 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted universe main multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted universe main multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted universe main multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END


NOTE: i have installed automatix2

thanks for any help or posts,

regards,
James

---

### Post by ginkhao on 2006-11-28
I have exactly the same error as you, and I don't have automatix installed, so I'd like to know too.

---

### Post by nickburns on 2006-11-28
Does

sudo apt-get update

work?

---

### Post by ginkhao on 2006-11-28
webjames,

I have found something that resolves the problem for me, it appears to be due to the fact that my ISP uses a transparent proxy.  Try running this command:

apt-get update -o Acquire::http::No-Cache=True
(from here: [https://launchpad.net/distros/ubuntu/+source/apt/+bug/33505](https://launchpad.net/distros/ubuntu/+source/apt/+bug/33505))

Running that command gave me an error-free update and eliminated the authentication problem I was having with a security update.

---

### Post by ityro on 2007-05-20
Thank You ginkhao,

Had same problem for several days. Your solution worked for me, thanks for the post.

---

