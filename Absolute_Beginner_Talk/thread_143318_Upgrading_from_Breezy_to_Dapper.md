---
title: "Upgrading from Breezy to Dapper?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by zexoc on 2006-03-12
Can this be done without having to unistall Breezy Badger and then installing Dapper Drake? ie. from withing Breezy Badger?

---

### Post by bjweeks on 2006-03-12
Yes.

---

### Post by Sutekh on 2006-03-12
To do this you must do a **dist-upgrade**

You should backup your sources.list then edit it so that all instances of **breezy** are replaced with **dapper**
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt-sources.list
```
If this were my current (breezy) sources list
```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu **breezy** main restricted
deb-src http://archive.ubuntu.com/ubuntu **breezy** main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu **breezy**-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu **breezy**-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu **breezy** universe
deb-src http://archive.ubuntu.com/ubuntu **breezy** universe

deb http://security.ubuntu.com/ubuntu **breezy**-security main restricted
deb-src http://security.ubuntu.com/ubuntu **breezy**-security main restricted

deb http://security.ubuntu.com/ubuntu **breezy**-security universe
deb-src http://security.ubuntu.com/ubuntu **breezy**-security universe

deb http://archive.ubuntu.com/ubuntu **breezy** multiverse
deb-src http://archive.ubuntu.com/ubuntu **breezy** multiverse

deb http://archive.ubuntu.com/ubuntu v-backports main restricted universe multiverse 
```
Then I would change all the **breezy**'s to **dapper**'s
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu **dapper** main restricted
deb-src http://archive.ubuntu.com/ubuntu **dapper** main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu **dapper**-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu **dapper**-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu **dapper** universe
deb-src http://archive.ubuntu.com/ubuntu **dapper** universe

deb http://security.ubuntu.com/ubuntu **dapper**-security main restricted
deb-src http://security.ubuntu.com/ubuntu **dapper**-security main restricted

deb http://security.ubuntu.com/ubuntu **dapper**-security universe
deb-src http://security.ubuntu.com/ubuntu **dapper**-security universe

deb http://archive.ubuntu.com/ubuntu **dapper** multiverse
deb-src http://archive.ubuntu.com/ubuntu **dapper** multiverse

deb http://archive.ubuntu.com/ubuntu **dapper**-backports main restricted universe multiverse 
```
Then write the file (Ctrl+X) exit (Ctrl+O) and then issue the command to **dist-upgrade** to dapper
```
sudo apt-get update
sudo apt-get dist-upgrade
```

It will download approximately 600MB worth of packages, and then you'll have Dapper.

---

### Post by eqisow on 2006-03-12
One note though, Dapper is still beta software. I upgraded and the kernel wouldn't even boot. I had to use recovery mode from the install CD to fix this. Once the kernel booted I found that X wouldn't start, this required for command line fixes. Everything now works great, but just be warned: if you're innexperienced with Linux/Ubuntu you may want to wait.

---

### Post by Sutekh on 2006-03-12
Absolutely, Dapper is not ready for your "production systems" as they say.  (I think they still call it alpha software too)

Wait until it's final release and then you can try the dist-upgrade.

---

### Post by zexoc on 2006-03-14
i definitely wont try to update until it comes out of beta

---

### Post by ncappel1 on 2006-03-24
I want to try the distro-upgrade, but is there a way that I can keep all the packages I downloaded and installed? When I install (and overwrite everything) from an iso I created, if I put my home directory (which I have backed up) on my computer will I still have the packages? ie gaim2.0, banshee, amarok, abiword, etc. If not, what directories should I backup?

thank you!

---

### Post by wsanders on 2006-03-24
You won't have packages still installed if you just have /home backed up. The packages are installed under /usr and other various places.

---

### Post by Nordoelum on 2006-04-03
You can use these too:
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf]("http://packages.freecontrib.org/ubuntu/plf") breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf]("http://packages.freecontrib.org/ubuntu/plf") breezy free non-free
```

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

---

### Post by meborc on 2006-04-03
just curious... why does this list contain both **breezy **and **dapper **(last two lines are breezy) ...

doesn't that brake the system? :eek:

---

### Post by Nordoelum on 2006-04-03
[quote=meborc]just curious... why does this list contain both **breezy **and **dapper **(last two lines are breezy) ...

doesn't that brake the system? :eek:[/quote]

That I haven't noticed.. I don't know...

---

### Post by meborc on 2006-04-03
oh, and for those who want to make the leap from **breezy **to **dapper**, NOW is not a good time to dist-upgrade... in dapper forums there has been a lot of complaints about system breaks... and for newbies (in the most respectful sence) it is NOT a good idea to jump... not just yet...

if you are not afraid to lose data, or to reinstall, then try dist-upgradeing... if there are any problems, file bugreports and install dapper from flight6 cd

---

