---
title: "How do I update in Kubuntu?"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-08-29
I'm a Kubuntu newbie,

and [www.ubuntuguide.org](www.ubuntuguide.org) doesn't help...

---

### Post by c0rderr0y on 2005-08-29
do a

sudo apt-get update
sudo apt-get upgrade

---

### Post by manicka on 2005-08-29
Or use synaptic

---

### Post by invalid on 2005-08-29
You would be better off doing

sudo apt-get update
sudo apt-get dist-upgrade

This is better for newbies, and people who do not quite grasp the idea of dependencies - and are not able to determine if it is safe to do certain things.
This will calculate all the things you need in a "smart upgrade" mindset.

Cheers,
Cb.

---

### Post by Muhammad on 2005-08-29
Those are the first things I tried...

My question really is: How do I add extra repositries in Kubuntu?

---

### Post by invalid on 2005-08-29
You will need to edit your sources.list

you can do this with the command

sudo nano /etc/apt/sources.list

Cheers,
Cb

---

### Post by Muhammad on 2005-08-29
You mean I should replace my currect source.lst with this:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by invalid on 2005-08-29
You can replace it with whatever repos you like :)

But yes, this is the correct list for official ubuntu packages and updates.

Cheers,
Cb

---

### Post by Muhammad on 2005-08-29
It's still not working

```
muhammad@ubuntu:~$ sudo apt-get update
Password:
Reading package lists... Done
muhammad@ubuntu:~$
```

](*,)

---

### Post by poofyhairguy on 2005-08-29
[QUOTE=Muhammad]It's still not working

```
muhammad@ubuntu:~$ sudo apt-get update
Password:
Reading package lists... Done
muhammad@ubuntu:~$
```

](*,)[/QUOTE]

That WAS correct. Now type this:

> sudo apt-get dist-upgrade

---

### Post by Muhammad on 2005-08-30
Actually I forgot to save source.list after I edited it XD

Gedit > Nano nuff said.

Thanks y'all. :)

---

