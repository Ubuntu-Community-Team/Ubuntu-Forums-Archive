---
title: "Synaptic reload error"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by sarum on 2006-10-16
Hello
I received this 'Warning' after doing a reload in Synaptic. I'd appreciate any comments as to how to solve it (and what a pubkey is)


W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718



After clicking OK(or similar), I got this as well

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)

Any help will be much appreciated; thanks ..............Sarum

---

### Post by dmizer on 2006-10-16
post the contents of /etc/apt/sources.list please :)

---

### Post by sarum on 2006-10-17
Thanks for your reply. Sorry, I'm too much of a newbie to know how to do as you ask. I did try this:-
joe@Joes-pc:~$ cd /etc/apt/sources
bash: cd: /etc/apt/sources: No such file or directory
joe@Joes-pc:~$ ls /etc/apt/sources
ls: /etc/apt/sources: No such file or directory
joe@Joes-pc:~$
Can you explain further please. Thanks in advance Sarum

---

### Post by Kateikyoushi on 2006-10-17
Use this command to list it.

```
cat /etc/apt/sources/list
```

---

### Post by sarum on 2006-10-17
Sorry again; this is what I got:-
joe@Joes-pc:~$ cat /etc/apt/sources/list
cat: /etc/apt/sources/list: No such file or directory
joe@Joes-pc:~$ cd
joe@Joes-pc:~$ sudo cat /etc/apt/sources/list
Password:
cat: /etc/apt/sources/list: No such file or directory
joe@Joes-pc:~$
This is really frustrating. Thanks for your help.Sarum

---

### Post by Kateikyoushi on 2006-10-17
Sorry. I made a typo. >.<

```
cat /etc/apt/sources.list
```

---

### Post by sarum on 2006-10-17
> **Kateikyoushi said:**
> Sorry. I made a typo. >.<

```
cat /etc/apt/sources.list
```

Bingo, and thankyou so much; I was begining to think.........not sure what.
So this:-
joe@Joes-pc:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
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
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# deb cdrom:[APC World]/ dapper main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
I hope this gives some idea of what's wrong.Thankyou again Sarum

---

### Post by sarum on 2006-10-19
Yes, well no replies yet, and no complaints about that either. So I think a re-install-start again would be a good idea. Thanks for your replies and help .....Sarum

---

### Post by Kateikyoushi on 2006-10-19
Sorry I did not notice your post.
This should solve your key issues.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

Remove the duplicated lines from your sources.list would solve the other half.

```
gksudo gedit /etc/apt/sources.list
```

Tere are two lines at the end which you should remove.

---

### Post by sarum on 2006-10-20
Thankyou for your help, I shall do as you suggest this evening. If all goes well I shall not trouble you again; so if you don't hear from me; please accept my thanks now!.........Sarum.

---

