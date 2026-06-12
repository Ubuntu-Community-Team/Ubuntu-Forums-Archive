---
title: "skype instalation problems"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Station on 2008-03-19
what does 

Error: Dependency is not satisfiable: libqt4-core

mean?

I have ubuntu 7.10 trying to install skype 2.0

---

### Post by wormser on 2008-03-19
It means that you need to install libqt4-core before Skype will install.  Try installing it first then install Skype.

```
sudo apt-get install libqt4-core
```

---

### Post by Station on 2008-03-20
there is no package libqt4-core

---

### Post by billgoldberg on 2008-03-20
How are you installing skype?

You should download it from the medibuntu repository, that way all dependencies should be downloaded automatically. 

[link]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")

---

### Post by Station on 2008-03-20
I tried the link and the first step leaves me with...

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O 

HTTP request sent, awaiting response... 404 Not Found

---

### Post by plucky on 2008-03-20
From this [link](https://help.ubuntu.com/community/Medibuntu)

Copy and paste into a terminal the following two lines.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

And this line will add the key and update and upgrade your repository indexes ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then to install **skype** ```
sudo apt-get install skype
```

Good Luck

---

### Post by Station on 2008-03-20
[QUOTE=plucky;4555053]From this [link](https://help.ubuntu.com/community/Medibuntu)

Copy and paste into a terminal the following two lines.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

This does not seem to work. I get
```
 HTTP request sent, awaiting response... 404 Not Found 
20:23:40 ERROR 404: Not Found
```

---

### Post by Station on 2008-03-20
> **Station said:**
> [QUOTE=plucky;4555053]From this [link](https://help.ubuntu.com/community/Medibuntu)

Copy and paste into a terminal the following two lines.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

This does not seem to work. I get
```
 HTTP request sent, awaiting response... 404 Not Found 
20:23:40 ERROR 404: Not Found
```

ah I tried it a third time and it worked. 

but now I have this problem

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libqt4-core (>= 4.3.2) but it is not installable
         Depends: libqt4-gui (>= 4.3.2) but it is not installable
         Depends: dbus-x11 (>= 1.0.0) but it is not installable
E: Broken packages

```

---

### Post by MobiusNZ on 2008-03-20
Note that you can also use the direct skype repo
```

deb http://download.skype.com/linux/repos/debian/ stable non-free

```

---

### Post by Cappy on 2008-03-21
None of that will help. Your sources.list file is incorrect or you need to
```
sudo apt-get update
```

Post your
```
gksudo gedit /etc/apt/sources.list
```
and we'll see what the problem is.

---

### Post by 3rdalbum on 2008-03-21
You need to use Software Sources (System > Administration > Software Sources) and enable all the repositories underneath the words "Downloadable from the Internet".

---

