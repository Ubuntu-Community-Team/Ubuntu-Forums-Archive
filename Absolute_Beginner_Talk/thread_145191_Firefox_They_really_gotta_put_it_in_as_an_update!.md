---
title: "Firefox: They really gotta put it in as an update!"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by Justin Holt on 2006-03-15
I know...I have asked this question way too much.  But the post in the wiki just doesn't work for me for some reason.  I have the file downloaded to my desktop, i don't have any bookmarks, themes, or extensions to back up, and i follow the code lines and i still get errors.  why?  if anyone can help, please don't refer me back to the wiki, it is just not working :-k

---

### Post by rfruth on 2006-03-15
Ya talking about 1.0.7 vs 1.5x ?  If so 1.0.7 works for me, (Dapper comes with 1.5)  I have 1.5 on a G3 iMac & don't see much difference (1.5 update works better ...)  Waiting for Dapper may be your best bet.

---

### Post by Justin Holt on 2006-03-15
so seeing as dapper will come with 1.5, when is dapper supposed to come out, or where do i go to get a copy of the "beta" of dapper?

---

### Post by Brunellus on 2006-03-15
[QUOTE=Justin Holt]so seeing as dapper will come with 1.5, when is dapper supposed to come out, or where do i go to get a copy of the "beta" of dapper?[/QUOTE]
you can simply edit all references to breezy in /etc/apt/sources.list to "dapper"

then

sudo apt-get update 

sudo apt-get dist-upgrade

WARNING:  dapper is not yet final.  I'm dist-upgrading now but with some trepidation yet.

---

### Post by Justin Holt on 2006-03-15
if it is really that easy to change it to dapper, is it as easy as change a line of text...please tell considering i am having a hell of a time with this

---

### Post by zubrug on 2006-03-15
[QUOTE=Justin Holt]so seeing as dapper will come with 1.5, when is dapper supposed to come out, or where do i go to get a copy of the "beta" of dapper?[/QUOTE]
I have found firefox 1.5 too buggy, especially in Dapper, here is my source list.

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

sudo gedit /etc/apt/sources.list           
Make a  backup of your source list first.

---

### Post by darkmaze on 2006-03-15
dapper should be out in june & we're still in alpha

---

### Post by Justin Holt on 2006-03-15
so...will it being in alpha give me this message in terminal

Code: 0 upgraded, 0 newly installed, 0 to remove and 163 not upgraded.
 
This shows up after i do a apt-get dist-upgrade:-k

---

### Post by towsonu2003 on 2006-03-15
Honestly, I couldn't understand why a user who can't install fx 1.5 from the wiki is given the advice to dist-upgrade to the unstable??? Dapper is unstable, may become unsuable at time, and not ready for production (everyday use included). People who test it (ie use it now) are those who can deal with glitches, bugs, X failures and so on. A user who can't install fx from the wiki is either not ready to test dapper, or have something wrong / different with his/her system. In both cases, don't we first need to know how to fix this (this = either user is newbie to ubuntu /or/ has something wrong/different in his system). 

I know the OP doesn't want this, but the only way ***I*** can help is to this, sorry :)

0. Restore sources.list to breezy
0,5. make sure firefox 1.0.7 is currently installed in your breezy (check synaptic)
0,6. check that you didn't break anything while that dist-upgrade
0,7. do not open firefox from now on during these below steps
1. move .mozilla/firefox to somewhere else (mv .mozilla/firefox .mozilla/firefox.backup)
2. go back to wiki, start from the first step, continue until you get an error. 
3. paste all your steps in detail with outputs and the error here. 

We should be able to figure out what's going wrong... thanks.

---

### Post by aysiu on 2006-03-15
And if copying and pasting commands is too difficult, you can always use Automatix.

---

### Post by Justin Holt on 2006-03-16
now that i am getting somewhere...it would be nice to be able to be root or the "owner"...does any one know really quick how to get me that?
thanks in advanced:confused:

---

### Post by aysiu on 2006-03-16
Read this entire page:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

It explains why you're not root/owner and why you shouldn't be and that there's a better way (the default).

If you read the *entire* page, it also explains how you can set up a root account and use it.

If you're open-minded enough, here are some tips on how to use *sudo* properly and efficiently:

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Justin Holt on 2006-03-16
the only problem is that to network my machines i have to edit a .conf that is lock and to install firefox 1.5, i have to access to /opt/firefox, and the get to the /firefox, i have to create a folder which i don't have the permissions to do....what do i do?

---

### Post by Brunellus on 2006-03-16
I believe it is also possible to isntall firefox entirely inside one's /home directory and run it from there with normal user privileges.

---

### Post by NeghVar on 2006-03-16
> the only problem is that to network my machines i have to edit a .conf that is lock and to install firefox 1.5, i have to access to /opt/firefox, and the get to the /firefox, i have to create a folder which i don't have the permissions to do....what do i do?

Sudo should be able to do it no problem, the first time I tried to do the upgrade a while ago I nuked it somehow, I still have no clue, but the second time I tried it worked perfectly. Just go to the wiki again once you have everything set back to Breezy and then everytime it gives you a command line operation, copy it and go to your terminal right click with your mouse and click paste.

---

