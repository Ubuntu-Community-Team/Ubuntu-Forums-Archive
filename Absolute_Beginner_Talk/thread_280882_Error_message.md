---
title: "Error message"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2006-10-20
Hello Everybody,

On trying to use Easy Ubuntu, I get the following error message:

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

It then also says:

Could not apply changes!
Fix broken packages first.

Looking through my newly bought and read Official Ubuntu Book, on page 197 it gives details on how to fix broken packages. I tried it and it doesn't work. Running Easy Ubuntu again produces the same error messages. All this on a fresh install of Ubuntu.

How do I get round these problems?

Thanks in advance!

Chris

---

### Post by chuckyp on 2006-10-20
Easyubuntu and automatix are not officially supported here.  You would have to go to their respective web pages asking about help.

---

### Post by unisol on 2006-10-20
try sudo apt-get update first, if it still gives you problems try automatix.you could also try this;gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x12B83718 ;  gpg --export -a 0x12B83718 | sudo apt-key add -

---

### Post by PriceChild on 2006-10-20
Could you post exactly how you're trying to fix the broken packages, and the error returned please.
> **chuckyp said:**
> Easyubuntu and automatix are not officially supported here.  You would have to go to their respective web pages asking about help.Still no reason why we shouldn't help.

---

### Post by Charlie Chick on 2006-10-20
Hi, I used:

sudo apt-get update
and
sudo apt-get -f install
which the Official Ubuntu Guidebook says updates and fixes your package manager (page 197). The error messages quoted in my original post comes from trying to run Easy Ubuntu.

Thanks

---

### Post by PriceChild on 2006-10-20
> **Charlie Chick said:**
> sudo apt-get -f installCould you post the output of this please

And also
```
cat /etc/apt/sources.list
```

---

### Post by Charlie Chick on 2006-10-20
The output of sudo apt-get -f install is:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
The output of cat/etc/apt/sources.list is:
eb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ erse multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Thanks.

---

### Post by Bachstelze on 2006-10-20
It is a standard sources.list. I suggest you install your stuff manually instead of usine EasyUbuntu.

---

### Post by Charlie Chick on 2006-10-20
So does that mean that there is nothing wrong with my brand new Ubuntu installation? Perhaps the problem lies with Easy Ubuntu? The error message suggested that it was a problem with Ubuntu itself. For newbies to Ubuntu like myself, the attraction of Easy Ubuntu is that it claims to install all the things you need in one,easy sweep. 

Thanks

---

### Post by Bachstelze on 2006-10-20
Nope, actually the problem was very simple. You just forgot to add the GPG key used to authenticate some packages. The instructions to add it are [here](http://packages.freecontrib.org/plf/).

But the suggestion to do it all manually stands. There won't be EasyUbuntu for everything, so the sooner you learn how to install stuff *via* apt, the better ;)

---

### Post by Charlie Chick on 2006-10-20
Thanks. I presume that whilst the cursor is still flashing, it's doing something? It hasn't returned to the standard text that I get when I open the terminal.

---

