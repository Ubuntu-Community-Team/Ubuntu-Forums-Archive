---
title: "how to : download additional packages and then install them"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by m.h.shams on 2006-04-21
dear friends,

im new in ubuntu, after downloading an Installer CD from ubuntu site,
i installed it on my pc, but now i need some package for media, and dialup connection and ....., 

but i have a problem, i can't connect internet via ubuntu, i can't configure my modem to connect internet.

is there any way to download this package with windows or other OS, and 
then install them on my ubuntu ?

please help me, 

thanx all
shams

---

### Post by KLineD on 2006-04-21
Yes, just save the deb packages you download to any media you can access under ubuntu (CDROM, DVD or another hard disk partition, etc) and then in ubuntu:

1.- Open a terminal
2.- Navigate to where your packages are
3.- sudo dpkg -i nameofthepackage.deb

And that's it. I think that in Dapper there's a gui for installing those downloaded packages but I can't verify because I'm at work.

Good Luck!

---

### Post by brentoboy on 2006-04-21
I'm going to warn you here...this option really sucks.

Ubuntu normally protects you from details by automatically downloading dependancy packages.  If you download a package, it isnt like a windows installer where all the extra support files are in there, instead, each package just knows which packages it needs to work, and it downloads them for you without any hassel.  Unless you download the deb file yourself.

What you will end up with is what turned me off of redhat based distros years ago.  rpm hell.  (or deb hell in our case)   when you try to install a deb, it might complain "you need this other package" before it will install.  that other package might also complain "you need some completely different package" and so on.

good luck with that, but I would keep with the packages on the CD unless you really want a specific application.  BTW, there are a lot of packages on the CD that dont get installed, so you do have some wiggle room.

---

