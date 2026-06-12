---
title: "Segmentation fault"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Petar Marjanovic on 2007-04-30
I want to install something to listen to music. Why not Amarok?

I opened Synaptic, but it crashed(?). I opened the own software from Ubuntu to install Amarok; no way to open it without crashing. Then I wanted to install it via terminal:

```
petar@petar-desktop:~$ sudo aptitude install amarok
Segmentation fault (core dumped)%
```

What's happened?

---

### Post by taurus on 2007-04-30
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by Petar Marjanovic on 2007-04-30
Of course. (Yes, I am an Automatix-Kiddie)^^
```
deb http://de.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://de.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://de.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb http://ubuntu.beryl-project.org/ edgy main

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
#AUTOMATIX REPOS END
```

---

### Post by starcraft.man on 2007-04-30
Also, what happens when you try to install any other program? Is this systematic? Try maybe installing listen...

```
sudo aptitude install listen
```

Does that pop out the same error?

---

### Post by Skrynesaver on 2007-04-30
That is a very odd result for such a well used program, try
```
apt-get install amarok
```

---

### Post by Petar Marjanovic on 2007-04-30
It was automatix and beryl what I don't use -.- ^^

But thanks for helping.

---

### Post by taurus on 2007-04-30
You have a major problem with your /etc/apt/sources.list.  You are running Edgy but somehow you installed Automatix for Feisty!  Therefore, you need to remove all the lines that Automatix added.  Otherwise, here's your new /etc/apt/sources.list.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main 

```

Save the new list and then run

```
sudo aptitude update
sudo aptitude install amarok
```

---

### Post by starcraft.man on 2007-04-30
> **Petar Marjanovic said:**
> It was automatix and beryl what I don't use -.- ^^

But thanks for helping.

I don't follow, your problem is fixed?

Edit: Make sure to fix your sources there >.>.

---

