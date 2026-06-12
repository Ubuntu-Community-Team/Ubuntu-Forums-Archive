---
title: "Problem with Installing Wine"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by pkj on 2008-03-16
HI,
Have problem with Installing Wine..

I am doing the following

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

 sudo apt-get update

sudo apt-get install wine

I am getting the following error report

sudo apt-get install wineReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.14) but 1.0.13-1ubuntu5 is to be installed
        Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
        Depends: libgphoto2-2 (>= 2.4.0) but 2.3.0-0ubuntu4 is to be installed
        Depends: libgphoto2-port0 (>= 2.4.0) but 2.3.0-0ubuntu4 is to be installed
        Depends: libxml2 (>= 2.6.29) but 2.6.27.dfsg-1ubuntu3 is to be installed
E: Broken packages


Any Help....

pkj

---

### Post by Ub1476 on 2008-03-16
Why not just do

```
sudo apt-get install wine
```

If you have broken packages do:

```
sudo apt-get -f install

sudo dpkg --confgure -a
```

---

### Post by forrestcupp on 2008-03-16
You may just need to enable the Universe and Multiverse repos.  Try going to System->Administration->Software Sources and make sure all boxes are checked in the Ubuntu Software tab.  Then:
```
sudo apt-get update
sudo apt-get install wine
```

See if that works.

---

### Post by pkj on 2008-03-16
Hi
The first command
 
sudo apt-get install wine

is what is giving the broken dependencies

the other two commands 

sudo apt-get -f install

and

sudo dpkg --configure -a

run smoothly...

does this mean that wine is now installed...

If yes.. How do i actually check that...

pkj

---

### Post by pkj on 2008-03-16
Both the tabs are already checked in the software tab

pkj

---

### Post by Ub1476 on 2008-03-16
If the broken packages has been fixed, install wine again:

```
sudo apt-get install wine
```

---

### Post by pkj on 2008-03-16
The error message remains the same

pkj

---

### Post by Ub1476 on 2008-03-16
Try:

```
sudo apt-get autoremove
```

And:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mc4man on 2008-03-16
Are you running feisty or gutsy - all of the packages listed in the unmet dependencies are feisty versions. If your on feisty then you need a feisty version of wine not gutsy

---

