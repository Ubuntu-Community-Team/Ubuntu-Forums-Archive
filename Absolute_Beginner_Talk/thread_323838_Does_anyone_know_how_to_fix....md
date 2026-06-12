---
title: "Does anyone know how to fix..."
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by samlathan on 2006-12-22
This error messege: E: Type 'dep' is not known on line 35 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I can hardly open or install anything. I know it's something messed up in my repositories, but I'm not sure what.
Any help?

---

### Post by taurus on 2006-12-22
Maybe you miss config your /etc/apt/sources.list, especially line 35!  Why don't you post your /etc/apt/sources.list here then!

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by croppyboy on 2006-12-22
There is probably a mispelling in your sources.list. Open your sources.list file and look for dep (should probably be "deb") on line 35 . . .

```
sudo gedit /etc/apt/sources.list
```

Correct it and save the changes . . .

It might also be helpful to post the contents of your sources.list file if this doesn't work.

---

### Post by samlathan on 2006-12-22
Here it is:


deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
dep [http://www.nicotine-plus.org/debian](http://www.nicotine-plus.org/debian) branch main

---

### Post by taurus on 2006-12-22
Here's your problem.  

```
dep http://www.nicotine-plus.org/debian branch main
```
It should be **deb**, not **dep**...

So, you need to edit your /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by croppyboy on 2006-12-22
The last line

> dep [http://www.nicotine-plus.org/debian](http://www.nicotine-plus.org/debian) branch main

should be

> [COLOR="Red"]deb[/COLOR] [http://www.nicotine-plus.org/debian](http://www.nicotine-plus.org/debian) branch main

Open a terminal and edit your sources.list (as explained above).

---

### Post by samlathan on 2006-12-22
Oh jeez, completely missed that. Thanks a lot guys.

---

