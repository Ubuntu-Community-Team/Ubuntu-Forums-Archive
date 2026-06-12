---
title: "Installing to Dual Boot Problem"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by bigngamer92 on 2008-02-01
Okay I have a Dell WXPWS269 with an Intel Dual Core Proccesor and 504 MB of RAM.  I got a CD of 7.04 from a book on Ubuntu Desktop Edition.  I tested its integrity and came up with no errors.  I entered the LiveCD version and loaded up the installation.

When going through the Partition section I gave 26 GB to Windows and 11 GB to Ubuntu and 700 MB to the swap (The book told me to use manual).  When I hit the next button the computer stopped working and after 10 min of waiting had yet to reach the 1% marker.  I fiddled around trying to make it wake up and eventually just exited the installation.

I retried the installation but this time when I got to step 4 it gave me an error message saying "Partman failed exit code 10. Extra info can be found at /var/log/syslog" . After hitting try again twice I decided to go back through and had the same issue.

So now I'm here.  Anybody know how to fix this?

---

### Post by jan quark on 2008-02-01
> Extra info can be found at /var/log/syslog

you don't have the extra info mentioned ?

if the installation process keeps freezing download the newest version of ubuntu 
namely gutsy gibbon 7.10 in the alternate version 

can be found here
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

it is a text based installation but easy and stable

---

### Post by bigngamer92 on 2008-02-01
I tried to search for the information in the file manager but the cd drive just started moaning and I closed it out.

I know that 7.10 is more stable and up to date but wouldn't it save me time to just use Feisty and then upgrade to 7.10 once its done installing?

---

### Post by jan quark on 2008-02-01
IMHO it does save time if you download the gutsy alternate cd

upgrades are again linked with risks that something is going not to work
a fresh install is always better than an upgrade

---

### Post by bigngamer92 on 2008-02-01
Downloading in progress...

So when I go through the install process do I just choose the / partition that I created my first time through?  Also is their any significant differences between Gutsy and Feisty installation (I am using a book so it would be nice to know where to go from here.

---

### Post by jan quark on 2008-02-01
the installation process should be the same

and here is a good guide for installing via the alternate cd

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

there are many pictures explaining the installation step by step

ask for more info :)

---

### Post by slikwill on 2008-02-01
I tried the DVD from the book and had similar results.  I have ordered 7.04 and 7.10 by mail and they work perfectly.  I haven't found the book to be worth the price.  I have a Dell Inspiron  1000 dual-boot with ubuntu Fiesty and Ubuntu Gutsy.  Absolutely beautiful.

---

### Post by bigngamer92 on 2008-02-01
Ugh I was supposed to get the ALternate one! Hour long download and I grab the wrong one.  Is the alternate one more stable?  Please tell me I don't need to redo the entire download process again! What is the benifit of the alternate CD?

---

### Post by wasing on 2008-02-01
yeah i had the same problem with installing the Ubuntu alternate it kept taking me to the wrong download so eventually just gave up and used Kubuntu. the text based installer is by far i believe the best way to install Ubuntu and its derivatives its really easy. when you get through it to the end it will tell you to overwrite the master boot record with the grub boot loader. anyway to find the Ubuntu alternate (if the link is not fixed yet)  use bit torrent or a 3rd part mirror.

---

### Post by bigngamer92 on 2008-02-01
Okay now I get it...

The alternative CD is more bug proof but less pretty than its graphical counterpart.
Is there anything special I should do because of there already being a partition change?  I know that my windows partition was shrunk but I don't know how well it did on creating the new partitions.

---

### Post by randy78 on 2008-02-01
I looked up your model number and couldn't find anything relevant, but I will suggest that if it is a laptop (or desktop) that will be storing any type of sensitive information, you should choose the encrypted lvm option, because it will keep your data safe and secure if it ever gets stolen.

---

