---
title: "Trying to Access OS X Music and Documents Folder"
date: 2006-11-05
forum: Apple PPC Users
---

### Post by ozwald on 2006-11-05
To make a long story short, I screwed up my OS X install and I can't get into it. However, I need to get to the files in my Music and Documents folder that are on my OS X formatted hard drive (I'm working off the Live CD).

So far, using the instructions here:

[http://jclark.org/weblog/2005/05/24/ubuntumount/](http://jclark.org/weblog/2005/05/24/ubuntumount/)

I've been able to mount the hard drive, and I've gotten to where I can see the music and documents folder, but whenever I try to go into them or copy them it tells me I don't have the right permissions. Is there any possible way to rescue these?

Thanks.

---

### Post by gerghk on 2006-11-05
You need to sync your linux uid to whatever your osx account's uid was.

I think OSX defaults the uid's to start from 501

To make sure, in your OSX home directory, type 'ls -l', it will show you the owner of the Music and Documents folders.  If you didn't do anything fancy with your user groups in osx, your user name will show up as the owner user, and your owner group will be a number, which is your uid

in the case that you're actually able to boot into osx, just fire up a terminal and type 'id', it will tell you what your uid is.

So once you figure out what your uid is, modify your linux account to use the same uid by typing: 'usermod -u ###', ### being your osx uid

---

### Post by ozwald on 2006-11-05
Okay, I confirmed that my uid is 501, but evertime I try to type 'usermod -u 501', it tells me 'usermod: user 501 does not exist'.

---

### Post by gerghk on 2006-11-05
o oops my bad, it's supposed to be

usermod -u 501 YOURLINUXUSERNAME

---

### Post by jclark on 2006-11-05
Ozwald-

Let us know how this works.  If you get everything working, I'll update the instructions you linked to above, on my site.

Thanks,
Jason

---

### Post by ozwald on 2006-11-05
Okay, so I tried 'sudo usermod -u 501 ubunutu' (it wouldn't work without sudo, and ubuntu is the username on the live CD), and when I tried to cd into the Music folder, I still get permission denied.

---

