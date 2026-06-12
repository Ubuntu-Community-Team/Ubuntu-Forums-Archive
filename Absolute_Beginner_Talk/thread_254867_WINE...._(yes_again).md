---
title: "WINE.... (yes again)"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2006-09-10
hi, i have seen many people asking about WINE problems, i am wanting to install x-fire with WINE, and i have looked at a few HOW-TO's and they are well over my head, does anyone have a n00b-pr00f HOW-TO...

any help would be very grateful..

thx in advance

---

### Post by Inhumane on 2006-09-10
I haven't installed it so I wouldn't exactly know how to install it, but I can give it a try
cd Desktop (persuming that's where the install is)
wine xfire.exe (or whatever the filename is), install it
cd .wine/drive_c/"Program Files"/Xfire/
wine Xfire.exe
There is also this plugin for Gaim: [http://www.fryx.ch/xfire/](http://www.fryx.ch/xfire/) but I haven't tried it either

---

### Post by shoot2kill on 2006-09-10
yes, let me emphesise the N00BNESS of me...

lol

the link for xgaim is baffling, and i havnt even installed wine yet, i dont know how

---

### Post by psychiccyberfreak on 2007-02-17
I know what you mean. I don't think the xfire devs are porting it ever, so we're going to have to figure this out. 
In feisty, it is VERY unstable. It's usable, but barely works. There is Gfire, which is a gaim plugin that lets you do some of the things you can o in xfire, but it's still not xfire. I will fool around with it tonight and see what I can do.

---

### Post by OldTimeTech on 2007-02-17
download automatix2 from [http://www.getautomatix.com/](http://www.getautomatix.com/) and install wine from there....it's under utilities.

---

### Post by Adramelech on 2007-02-17
install Gfire plugin for xfire is wayyyy better than trying to get xfire to work.

---

### Post by nonewmsgs on 2007-02-17
that automatrix thing looked real neat, but i got an error i have also gotten before.  does this mean it isnt installing and how serious is this or did i do something wrong?

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
william@william-desktop:~$ sudo apt-get install automatrix2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package automatrix2

---

### Post by OldTimeTech on 2007-02-17
Check this out and see if it helps....

[http://www.ubuntuforums.org/showthread.php?t=190025&page=9&highlight=turn+ipv6](http://www.ubuntuforums.org/showthread.php?t=190025&page=9&highlight=turn+ipv6)

---

### Post by nonewmsgs on 2007-02-17
oh i did it again and it worked (without any warnings or errors).  what did i do wrong the first time?

---

### Post by nonewmsgs on 2007-02-17
dpkg is running?
please close dpkg and restart automatrix

---

### Post by OldTimeTech on 2007-02-17
also make sure all your repositories are available....under System/software sources....make sure you have Universe, main,multiverse and restricted checked so that when you update all will add to your software.

Also in the above url: it's talking about dapper, if you have edgy, will have to change it to edgy when in terminal.

---

### Post by OldTimeTech on 2007-02-17
means you may have had synaptic or apt-get running and all must be shut down when trying to use automatix2

---

