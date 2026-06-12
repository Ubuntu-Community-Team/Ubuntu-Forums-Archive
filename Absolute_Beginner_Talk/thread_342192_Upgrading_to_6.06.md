---
title: "Upgrading to 6.06"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by T4tav on 2007-01-19
Hi , Ive just installed Ubuntu 5.10 on my pc !
It works great , But I want to upgrade to 6.06 LTS. How do I go about doing this ?:confused: 

Many Thanks,
Tavis Booth

2nd question below !

---

### Post by taurus on 2007-01-19
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and replace the word **breezy** with **dapper** in there.  Save it and then run

```
sudo apt-get update
sudo apt-get dist-upgrade
```
Once it's done, reboot and you should be running Dapper now.

---

### Post by T4tav on 2007-01-19
Thx , Nice welcome to the community too ,Rearly quick reply :D 

2nd Problem , How do you get AOL to work on linux , or is it not possible ?

Also , Ive got a problem Upgrading , I get this message in the terminal 

```
tavis@ubuntu:~$ gksudo gedit /etc/apt/sources.list

(gedit:12802): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

then the sources list opens , but its empty !

---

### Post by taurus on 2007-01-19
What's the output of this command?

```
cat /etc/apt/sources.list
```

---

### Post by T4tav on 2007-01-20
> **taurus said:**
> What's the output of this command?

```
cat /etc/apt/sources.list
```

I get this :
```
tavis@ubuntu:~$ cat /etc/apt/sources.list
#deb file:///cdrom/ breezy main restricted

deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://wine.budgetdedicated.com/apt breezy main
tavis@ubuntu:~$

```

---

### Post by Sef on 2007-01-20
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe


Any line with breezy in it (like above) should be changed to dapper (like below.)

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe


---

### Post by T4tav on 2007-01-20
How can i change the code in terminal ?
and 
How can I save it ?

](*,)

---

### Post by Sef on 2007-01-20
To get to the source list:

Open the terminal (Applications > Accessories > Terminal)

```
gksudo gedit /etc/apt/sources.list
```

> How can I save it ?

then you can change breezy to dapper, just like you in a word processor: easy way to change - Under Search > Find and Replace.  Then File > Save.

---

### Post by T4tav on 2007-01-20
I get this message :
```
tavis@ubuntu:~$ gksudo gedit /etc/apt/sources.list

(gksudo:14861): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
(gedit:14864): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

tavis@ubuntu:~$


```

Then a gedit windows opens with nothing in it :confused:

---

### Post by insane_alien on 2007-01-20
just do 'sudo gedit /etc/apt/sources.list' it'll do the same thing and you shouldn't get those errors.

---

### Post by 3rdalbum on 2007-01-20
This is a known bug in Breezy (well, it's known to me!)

You can instead use the "nano" text editor:

```
sudo nano /etc/apt/sources.list
```

When you've changed "breezy" to "dapper", you can save your changes and exit Nano by pressing:
Control-X, then Y, then Enter.

Now run these commands in the terminal:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

You'll notice some changes happening to your desktop as the upgrade happens - don't worry, this is normal. After it's all finished, reboot and you'll be running Ubuntu 6.06!

---

### Post by T4tav on 2007-01-20
Something went wrong during the upgradeso i started again 
Now iget this message :
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
tavis@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
tavis@ubuntu:~$

```

Fixed now , Hopefully :D

---

### Post by taurus on 2007-01-20
```
sudo dpkg --configure -a
```

---

