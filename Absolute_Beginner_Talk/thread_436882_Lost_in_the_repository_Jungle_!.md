---
title: "Lost in the repository Jungle !"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Joseaa on 2007-05-08
I was trying to make sense of adding additional Ubuntu repository list( sources.list) and now it seems like I am lost. 

What will happen, if the packages which I want to install is present in more than one repository ? ( If this question makes no sense, it just shows I am lost )

---

### Post by taurus on 2007-05-08
What package do  you have in mind and can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by PriceChild on 2007-05-08
Please only use the official ubuntu supported repositories. 3rd party ones "will" break upgrade paths.

If the same package exists in two repos, for example feisty & feisty-updates, then it will be the package with the higher version number which is installed.

---

### Post by starcraft.man on 2007-05-08
Just a note to add to Price Child, if you have more than one version in the repos it will default to the highest version, but you can downgrade manually if you find something buggy or have a specific reason (I had a minor problem with beryl, so I downgraded a few files and I"m peachy :) ).

---

### Post by houstonbofh on 2007-05-08
> **PriceChild said:**
> Please only use the official ubuntu supported repositories. 3rd party ones "will" break upgrade paths.
A little strong here.  Perhaps "3rd part ones *can* break upgrade paths. I have been using medibuntu since plf died, and the wine repos for several upgrades with less problems than nvidia-glx... :)  If you want the non-free codecs, you have to go to outside repositories.  Several things there are quite safe.  Some things may not be.

---

### Post by PriceChild on 2007-05-08
> **houstonbofh said:**
> A little strong here.  Perhaps "3rd part ones *can* break upgrade paths. I have been using medibuntu since plf died, and the wine repos for several upgrades with less problems than nvidia-glx... :)  If you want the non-free codecs, you have to go to outside repositories.  S*!*@vizi.seeveral things there are quite safe.  Some things may not be.I am wearing my Ubuntu hat when I say that :)

Don't install anything you can't trust, and you can't trust anyone but Ubuntu :P

I heard medibuntu was done by a few ubuntu devs anyway... but I don't know :)

At the end of the day, if you use unsupported software don't come crying to us :)

---

### Post by Joseaa on 2007-05-08
I've been experimenting with different versions of sources.list and following is the one which I have currently. 

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced 
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe 

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted 

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe 

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse 

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse 

deb http://archive.canonical.com/ubuntu feisty-commercial main


```

I was trying to install Opera and I believe it is available through "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main", correct me if I am wrong. ( I already have it installed in my system but the package was downloaded and installed manually, now I want to try the same using apt-get install).

$aptitude search opera -- > gave the following result

i   opera                                           - The Opera Web Browser                                    
v   opera-static           

What does this search result mean ? Opera is available ? If so, where is it available ?

In a nut shell my question is, How can I know from which repository the package is being downloaded ?

---

### Post by houstonbofh on 2007-05-09
> **PriceChild said:**
> I am wearing my Ubuntu hat when I say that :)

Don't install anything you can't trust, and you can't trust anyone but Ubuntu :P

I heard medibuntu was done by a few ubuntu devs anyway... but I don't know :)

At the end of the day, if you use unsupported software don't come crying to us :)
But that ain't true either.  Come crying anyway, and we will still do what we can.  Look how much we helped people with envy, ndiswrapper for WiFi, and no LAN to the net?  And that was asking for it!
:lolflag:
We are suckers...  We will even help trolls. :D

---

### Post by PriceChild on 2007-05-10
```
apt-cache policy package
```Will tell you the "candidate" for instillation and where its from.
> **houstonbofh said:**
> But that ain't true either.  Come crying anyway, and we will still do what we can.  Look how much we helped people with envy, ndiswrapper for WiFi, and no LAN to the net?  And that was asking for it!
:lolflag:
We are suckers...  We will even help trolls. :DIts sad isn't it :)

---

