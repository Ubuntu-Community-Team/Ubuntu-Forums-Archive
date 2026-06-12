---
title: "Problem with APT"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Theros123 on 2008-01-25
Hey all!

This is a stupid question, yet I'm always having trouble with it! Whenever I need to run a function like: > Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Gutsy (7.10):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

in the terminal.. I can never get them to work.  It just gives me a 404 not found error???  What the heck am I doing wrong?

Thanks

---

### Post by taurus on 2008-01-25
Which command did you run and can you post the complete error message?

---

### Post by Theros123 on 2008-01-25
Okay, I'm trying to run this command:

sudo wget [http://wine.budgetdedicated.com/apt/...t.d/gutsy.list](http://wine.budgetdedicated.com/apt/...t.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

However, it spits out: 

> eric@laptop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gusty.list](http://wine.budgetdedicated.com/apt/sources.list.d/gusty.list) -O /etc/apt/sources.list.d/winehq.list
--12:57:37--  [http://wine.budgetdedicated.com/apt/sources.list.d/gusty.list](http://wine.budgetdedicated.com/apt/sources.list.d/gusty.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184, 88.159.193.22
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:57:37 ERROR 404: Not Found.



---

### Post by Theros123 on 2008-01-25
Sorry..but this seems simple?

---

### Post by EXCiD3 on 2008-01-25
Are you sure you ran this command EXACTLY?

```
*sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list*
```

Something has to be wrong with the command you wrote. When i clicked your link it did not take me to the gutsy.list file on the wine site. However **this** links does: [I][http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
[/I] 
You can always do it this way and skip that command and add the following two lines to your sources.list or create the winehq.list file yourself in /etc/apt/sources.list.d/

```
deb http://wine.budgetdedicated.com/apt gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"
deb-src http://wine.budgetdedicated.com/apt gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"
```

---

