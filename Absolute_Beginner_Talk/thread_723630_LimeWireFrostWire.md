---
title: "LimeWire/FrostWire"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by HebrewTheHammer on 2008-03-13
OK

LIMEWIRE

I have downloaded the limewire package for linux from the limewire website. i inatalled it by clicking "install package" at the upper right of the window that pops up when i click on the icon of the package that i downloaded from the limewire website. 

When i run limewire using terminal and typing in "limwire" I get this

******************************************************************
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
Java exec found in  /usr/lib/jvm/java-gcj/bin/
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com) 
Java exec found in  /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin/
Suitable java version found  [/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin/java = 1.5.0_13]
Configuring environment...
Loading LimeWire:
/usr/share/themes/Glossy/gtk-2.0/gtkrc:35: error: lexical error or unexpected token, expected valid token
*******************************************************************

LimeWire pops up and loads to 19% and asks me to configure. 
I tell it im using broad band
I tell it i will not use it for illegal reasons.
then an error thats says.

*******************************************************************
Your save folder is not valid. It may have been deleted, you may not have permission to write to it, or there may be another problem. please choose another folder.
*******************************************************************

yeah then i no longer know what to do. you would think it would insall the folder that it knows its supposed to be saving to.??????

OK

FROSTWIRE

I downloaded frostwire package for linux from the frostwire website. I installed it the same way i did lime wire. nothing happens when i try to open it. so i run it in terminal and it tells me

*************************************************************
chris@chris-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
chris@chris-desktop:~$ 
**************************************************************

How do i do that.

---

### Post by taurus on 2008-03-13
You need to install Sun java first before you can run either limewire or frostwire.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```
Make sure the output of the last command shows the latest version, not the gij or whatever.

p.s.  Stick with frostwire.

---

### Post by HebrewTheHammer on 2008-03-13
E: Couldn't find package sun-java6-bin
chris@chris-desktop:~$ java -version



this is what i get

so i hit enter wit "java -version" on the line and i get this 

java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


then what do i do

---

### Post by PmDematagoda on 2008-03-13
Please post the results of:-
```
cat /etc/apt/sources.list
```
and
```
sudo update-alternatives --config java
```

---

### Post by HebrewTheHammer on 2008-03-14
cat /etc/apt/sources.list

gets me

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted web
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted web
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

##Universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse web
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse #Added by software-properties

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted web
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free






**********************************************************************************

sudo update-alternatives --config java

gets me

[sudo] password for chris:

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.1
          3    /usr/bin/cacao
          4    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        5    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 





should i type a number in.

---

### Post by billgoldberg on 2008-03-14
search for "sun" in synaptic package manager and install the java jre 6 program there

And you should use frostwire, it's better and more linux friendly.

---

### Post by HebrewTheHammer on 2008-03-15
> **billgoldberg said:**
> search for "sun" in synaptic package manager and install the java jre 6 program there

And you should use frostwire, it's better and more linux friendly.





its not there. 5 is but is already installed.



oh and if i try(this has nothing to do with jre) but i cant use the java web launcher. it says i dont have the right computer type.

---

### Post by HebrewTheHammer on 2008-03-17
Alright if any of you have the same problem on frostwire do this


sudo update-alternatives --config java


that'll ge you this


[sudo] password for chris:

typre your password in and something to this effect will come up. choose wichever one looks the best.  i chose 4

There are 5 alternatives which provide `java'.

Selection Alternative
-----------------------------------------------
1 /usr/bin/gij-4.2
2 /usr/bin/gij-4.1
3 /usr/bin/cacao
4 /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+ 5 /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:



frost wire should then start.
*
*
*
*
*
*
limewire says when i try to start it now(for some reason limewire starts now that my java default is different.who knows)

Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_13]
Configuring environment...
Loading LimeWire:
/usr/share/themes/Glossy/gtk-2.0/gtkrc:35: error: lexical error or unexpected token, expected valid token


i dont know what that means.

---

