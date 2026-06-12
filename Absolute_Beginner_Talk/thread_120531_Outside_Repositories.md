---
title: "Outside Repositories"
date: 2006-01-22
forum: Absolute Beginner Talk
---

### Post by Edward The Bonobo on 2006-01-22
Can anyone tell me a (relatively) safe outside repository where I can grab gtkpod v0.99, plus dependencies?  I tried what I thought was the Debian unstable rep, but got all sorts of error messages about Public Keys.

Because I'm a newbie...can you also tell me exactly what I need to type into sources.list and/or Synaptic?

Thanks.


(Yes, I believe it's in Dapper...but I'm in Breezy)

While we're at it...I've upgraded to Breezy, but my sources.list still only refers to Hoary.  Can someone C&P what my file contents should look like?

---

### Post by juantxorena on 2006-01-22
This is the content of my /etc/apt/sources.list:
```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/
``` 
It has all breezy repos, plus breezy backports and wine backports.

However, you don't need to use outside repos in order to install gtkpod 0.99. You can install "checkinstall" (via apt-get, aptitude or synpatic). Then you can compile gtkpod 0.99 from sources, but doing "sudo checkinstall" instead of "sudo make install". Then checkinstall will make a deb package and install it, so you can uninstall it as any application installed via apt-get.

You can follow the part of [this]("http://www.ubuntuforums.org/showthread.php?t=114946") guide called "Installing gtkpod".

---

### Post by matthew on 2006-01-22
[quote=Edward The Bonobo]Can anyone tell me a (relatively) safe outside repository where I can grab gtkpod v0.99, plus dependencies? I tried what I thought was the Debian unstable rep, but got all sorts of error messages about Public Keys.[/quote]If you can't find it in the official repositories you can look here: [http://www.apt-get.org/](http://www.apt-get.org/) Bear in mind that if you use these repos you could have system breakage--USE AT OUR OWN RISK!!

---

