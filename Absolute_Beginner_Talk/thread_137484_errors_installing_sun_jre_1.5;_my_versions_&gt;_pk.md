---
title: "errors installing sun jre 1.5; my versions &gt; pkg;   ++rant"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by jal on 2006-02-28
I am trying to install a java SDK onto 
Linux acknak 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
(that the hoary hedghog?)

Certain messages within the forum prompted me to do the following:

add the following entries to [FONT="Courier New"]/etc/apt/sources.list
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
[/FONT]
then
[FONT="Courier New"]
sudo apt-get update
sudo apt-get install sun-j2re1.5
[/FONT]
resulting in Ye Error Message:
[FONT="Courier New"]
sdk1.5: Depends: libasound2 (> 1.0.9) but 1.0.8-1 is to be installed
                Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu13 is to be 
installed
[/FONT]

I seem to be -gt required dependencies but, but, 

tell me it's an easy fix anyone, please? I give up.

<rant>
I am depressed. Day 4 of my first ever Linux install. I've still got to set up Eclipse and get smb to my old NTFS partitions. I am so so so tired of grubbing through to forums to find answers to arcane questions (er, but thanks for posting guy 'n gals).

I just wish that just once, only once, something would work the first time.

KPalm duplicates all the entries on my PDA. Three times now. Sigh. When it doesn't abend.
Even more depressing, I'm suspecting that Kubuntu is one of the better distros. It did find all the hardware, and I didn't expect it to support the clie PDA, but it does. There is just no way my dear mother could have done this.
</rant>

---

### Post by newuser111 on 2006-02-28
the problem is that you are trying to install breezy (5.10) packages from a breezy repo when you have hoary (5.04)

so either upgrade to breezy, or install java from the sun website

after you download the bin file, you can use fakeroot jpkg javafile.bin to create a deb file

sudo apt-get install java-package

i dont know where you can get deb files compiled for hoary

---

### Post by jal on 2006-02-28
Thank you newuser111.

Anyone know offhand if there's a 'hoary' (5.04) repo containing a jre or sdk for java 1.5 or 4?

Or, a prepared deb file... I'm afraid the phrase 
"fakeroot jpkg javafile.bin to create a deb file"
went over my head. 

Meantime, I'm downloading the bin from sun.

er, said lightly, "update to breezy". Is it really that easy? I was going to wait for the duck.

---

### Post by jal on 2006-03-01
now have Java SDK installed.
Yay! Thanks newuser111.


Here's more information on fakeroot and java-package

[http://www.debian-administration.org/articles/142](http://www.debian-administration.org/articles/142)

I was able to get fakeroot, but
```
sudo apt-get install java-package
```
didn't work (not found), but 

[http://pdo.debian.net/stable/misc/java-package](http://pdo.debian.net/stable/misc/java-package)
supplied a deb which installed with dpkg.

then create the JDK deb using tools as described by newuser111.

---

### Post by daredevil on 2006-03-01
Try automatix

---

