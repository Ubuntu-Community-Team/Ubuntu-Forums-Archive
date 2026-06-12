---
title: "easyubuntu does nothing, no installation no message"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by deepbluegene on 2007-01-11
Hi
i recently downloaded easyubuntu but when i click on ok it does nothing. it just give me message that some things might be illegal in your country so press cancel to review and ok to install but when i press ok it does not do anything it just sit there on my desktop.

where is the problem
i am using i386 and ubuntu 6.10

please help
thanx

.............................................
problem solved but not completely. this time i let easyubuntu running and it started downloading the package i selected after around 15-20 mins.why such a delay?

---

### Post by AbeJarano on 2007-01-11
Hi,

Please follow the directions this page.
 [http://easyubuntu.freecontrib.org/get.html]("http://easyubuntu.freecontrib.org/get.html").

Good luck,
Anthony

---

### Post by mikewhatever on 2007-01-11
Downloaded and installed, or just downloaded?

```
 How to install EasyUbuntu

Open a terminal from Menu -> Accessories -> Terminal and run the following commands

wget http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz
tar -zxf easyubuntu-3.023.tar.gz
cd easyubuntu
cp packagelist-dapper.pot packagelist-edgy.pot
cp packagelist-dapper.xml packagelist-edgy.xml
sudo python easyubuntu.in

    * From the Easy Ubuntu window, check the appropriate boxes to download and install content to Ubuntu.
    * Note: Users of the previous EasyUbuntu 3.0 version may experience issues with installing Flash and Java.
    * If you would like automatic update, then follow these instructions: 

depending on which version of Ubuntu you're using:

On Ubuntu:

sudo gedit /etc/apt/sources.list

On Kubuntu:

sudo kate /etc/apt/sources.list

On Xubuntu:

gksudo mousepad /etc/apt/sources.list

In your text editor which will open, add to the bottom of your /etc/apt/sources.list file:

deb http://easyubuntu.cafuego.net main easyubuntu

From now on, EasyUbuntu should be automatically updated.


```

---

### Post by AbeJarano on 2007-01-11
Hi,

You probable got a corrupted download.  To check,please follow the directions this page to install the Medibuntu GPG key. [http://easyubuntu.freecontrib.org/get.html]("http://easyubuntu.freecontrib.org/get.html").
The following is the GPG homepage.  There are HOWTOs showing how to use keys to check your software.
[http://www.gnupg.org/]("http://www.gnupg.org/")
Good luck,
Anthony

---

### Post by AbeJarano on 2007-01-11
Hi DeepBlueGene,

You probably got a corrupted download.  To check,please follow the directions this page to install the Medibuntu GPG key. [http://easyubuntu.freecontrib.org/get.html]("here").
The following is the GPG homepage.  There are HOWTOs showing how to use keys to check your software.
[http://www.gnupg.org/]("http://www.gnupg.org/")
Good luck,
Anthony

---

### Post by AbeJarano on 2007-01-11
Hi DeepBlueGene,

You probably got a corrupted download.  To check,please follow the directions at [http://easyubuntu.freecontrib.org/get.html]("http://easyubuntu.freecontrib.org/get.html") this page to install the Medibuntu GPG key.  Then go to [http://www.gnupg.org/]("http://www.gnupg.org/") and read the HOWTOs to learn how to use keys to check your downloads.

Good luck,
Anthony

---

### Post by mikewhatever on 2007-01-11
AbeJrano, it looks like you have a corrupted right hand index finger.:-D

---

