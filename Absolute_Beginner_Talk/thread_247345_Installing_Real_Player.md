---
title: "Installing Real Player"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by kq6up on 2006-08-30
When I try to install real player, I get the following gripe:

'realplayer' is not available in any software channel

I have attached my sources.list for your perusal.  Thanks

Chris Maness

## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by croak77 on 2006-08-30
```
sudo apt-get install libstdc++5
wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb
sudo dpkg -i realplayer_10.0.7-0.0_i386.deb
```

---

### Post by kq6up on 2006-08-30
Thanks, now I can listen to a Prairie Home Companion :p

---

### Post by PPAAUULL on 2006-08-30
You also could just use Automatix and that installs it for you.

---

### Post by whitegorilla on 2006-08-30
> **croak77 said:**
> ```
sudo apt-get install libstdc++5
wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb
sudo dpkg -i realplayer_10.0.7-0.0_i386.deb
```

Thank you, I had struggled previously to get real player working, but this code worked perfectly.

:mrgreen:

---

