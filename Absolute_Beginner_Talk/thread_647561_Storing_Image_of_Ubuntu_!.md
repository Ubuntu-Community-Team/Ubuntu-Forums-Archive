---
title: "Storing Image of Ubuntu !"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by neon100 on 2007-12-22
**_QUESTION 1_**

I just installed ubuntu and installed a lot of properiety softwares and other things. 

THE PROBLEM:
I want to know a method to avoid the installation of softwares again

SOME EXPLANATION:
I asked on another forum that could i archive all these updates so that i can install them whenever i reinstall them. ONE fellow said that i can store the /var/cache/apt/archives/   folder and install all these files with following commands

cd /var/cache/apt/archives
sudo dpkg -i *.deb

but cant i make an image of my hard-drive or something like that and just do some magical tweak with whatever the later version of Ubuntu comes out and i get all my softwares in that Ubuntu.

[B][U]
QUESTION 2[/U][/B]

HOW CAN i create the hard drive image of already install ubuntu on my PC so as to paste that image on my friend's PC to get the exactly same ubuntu on his PC. 

(please dont suggest upgrading because there is a high risk of creating a mess !)

---

### Post by neon100 on 2007-12-22
will somebody please answer?

---

### Post by ubukool on 2007-12-22
As far as question one is concerned, I'm not really clear on what you are trying to do.  Are you trying to upgrade to a later release of Ubuntu?  If so, then you can upgrade rather than doing a clean install, but doing an upgrade can often lead to more problems.  I have found that the best solution is to have a separate /home partition and then to reinstall all the software (you can make a list).  I don't know if you can install all the software from an archive, sorry.

In answer to question two, the best thing to do is to use partimage to make a copy of your Ubuntu partition and then restore this partition image on your friend's PC.  He will have to use the live CD to install Ubuntu and then you can restore your version.  However, if you have an older version of Ubuntu and he wants the latest release, again, it's better to do a clean install and then install all the proprietary software again.

Here are instructions for using Partimage:

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by fatality_uk on 2007-12-22
Firstly, please be paitent. Solutions on forums are often like buses, you wait for one then three come along.

You have a couple of options. A fellow member posted a script to make a backup of your system. Its here in this thread [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

Secondly, I read your posts in the cafe and a good place to start is a site like [http://linuxappfinder.com/]("http://linuxappfinder.com/")

[http://linuxappfinder.com/alternatives?search_text=ghost]("http://linuxappfinder.com/alternatives?search_text=ghost")

Will give you the equivelant of Norton Ghost which i expect you are looking for

---

### Post by foppeh on 2007-12-22
[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

I made a backup, but didn put it back. So I cannot give a review. It sounds like a neat idea though.

---

