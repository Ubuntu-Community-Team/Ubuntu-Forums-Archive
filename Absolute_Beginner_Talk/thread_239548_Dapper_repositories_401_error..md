---
title: "Dapper repositories 401 error."
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by davyBoy on 2006-08-19
Hi, I recently installed Dapper on a new system and cannot get the repositories.  I've checked and all my repositories are dapper ones, not hoary ones like I've seen elsewhere in the forum.  I can connect to the net fine with Firefox, but cannot update any software.  Any ideas?

dB

---

### Post by TFX360 on 2006-08-19
Could you paste the contents of:

```
sudo less /etc/apt/sources.list
```


Kind regards,


TFX

---

### Post by TFX360 on 2006-08-19
By the way, do you use a proxy? If so you should add it to

```
/etc/environment
```

or more appropriate in this case

```
etc/apt/apt.conf
```

Lemme know,


Kind regards,


TFX

---

### Post by davyBoy on 2006-08-19
ooh...would using a proxy do that?  Right now I'm connected ubuntu-->cat5-->OSX-->Router-->cable modem.  I could take it downstairs temporarily and plug it in to software update, though I'd like to get it going on its own upstairs.

dB

---

### Post by davyBoy on 2006-08-19
and here's my etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.



dB

---

