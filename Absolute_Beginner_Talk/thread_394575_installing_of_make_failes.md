---
title: "installing of make failes"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by koukkis on 2007-03-27
when trying to install make from cdrom i get th error message;

W: failed to fetch cdrom [Ubuntu 6.06.1_Dapper drake_-Release amd64 (20060806.1)]/pool/main/m/make/make_3.80+3.81.b4-1_amd64.deb
MD5SUM mismatch

where am i doing wrong?

rgds Anders
Edit/Delete Message

---

### Post by lloyd_b on 2007-03-27
> W: failed to fetch cdrom [Ubuntu 6.06.1_Dapper drake_-Release amd64 (20060806.1)]/pool/main/m/make/make_3.80+3.81.b4-1_amd64.deb
MD5SUM mismatch

MD5SUM errors generally indicate a corrupt file.  Possibly a bad CD, or it could be an indication that your CD-ROM drive is flaky.

Lloyd B.

---

### Post by RKCole on 2007-03-27
If you aren't able to get another CD of Ubuntu at the time (and if you have an Internet connection on your Dapper system) you can go to System->Administration->Synaptic Package Manager.  In Synaptic, I'm pretty sure it's under Settings->Repositories--you can disable the CD-ROM repository there.  I had to do this at one point as I did not have a CD available and the system would not get anything from the online repositories until I deactivated the CD-ROM option in Synaptic.

I hope this helps some.

Take care.

---

### Post by the.unclean.cpp on 2007-03-27
Enter System->Administration->Software Sources->Enter Password->Disable the Cdrom with Ubuntu 6.10 'Edgy Eft'(or what distro you have)
Then go to Applications->Accesories->Terminal and type:
```
$ sudo apt-get install make
```
You will be prompted for password. Enter it and wait until make is installed.

---

### Post by zvacet on 2007-03-27
If you don´t use Edgy edit your source list
```
gksudo gedit etc/apt/sources.list
```
put # sign in front of Cdrom line

save and close

```
sudo aptitude install make
```

---

