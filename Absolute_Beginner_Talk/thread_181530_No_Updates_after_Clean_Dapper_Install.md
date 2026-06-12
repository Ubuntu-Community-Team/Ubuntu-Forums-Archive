---
title: "No Updates after Clean Dapper Install"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by greggfathead on 2006-05-24
Hey there - I did a clean install of Dapper (no LiveCD here, I wanted to run clean on a spare laptop to see how the new OS was) on Friday, and so far - there have been no updates yet.  Meanwhile, a friend of mine who is also running Dapper said that he is getting about thirty updates a day.  Thi sseems odd to me, adn I'm wondering if I need to tweak my settings to be sure I am getting all the updates I should be.

Is there something I should run in the Terminal to be sure I am getting all the necessary updates?

Thank you for your help!

---

### Post by jeremy on 2006-05-24
Post a copy of your /etc/apt/sources.list
Maybe there's something wrong there.

---

### Post by greggfathead on 2006-05-24
Okkie dokie - here you go...

...

# 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060504)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060504)]/ dapper main restricted

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

...

Thank you!

---

### Post by popkid on 2006-05-24
Sure I read in another post that the US mirrors are broken at the moment, so I think you will need to change all those repository addresses to the standard ones...

ie... drop the "us." from the front of each address so you have something like below....

[SIZE="1"]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse[/SIZE]

you will also need to remove the # from the beginning of these lines, looks like the mirrors were broken at the time you installed and the installer commented them out of the repository list

And since you have an alpha release... go away and make several cups of coffee while the downloads come!

Hope this works for you,

pK

---

### Post by confused57 on 2006-05-24
Looks like you need to enable the extra repositories, by uncommenting any of the entries in your sources.list that looks like a URL(Take out the # in front of them).  You can also do this from Synaptic Package Manager:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications)

These instructions are for Breezy, but are pretty much the same in Dapper.
Then run Update Manager or do it from terminal(update, then upgrade).   

I imagine that was what Jeremy was looking for, if you want to wait until he replies again.

---

### Post by greggfathead on 2006-05-24
Thank you so much for the help!  For some reason I could not edit that sources.list file, so I did have to go thru the package manager and re-activate basically everything since the mirrors were down during my install.  And yes, that was a good thing to do right before lunch, what with the 314 initial updates that needed to be downloaded and installed.  :)

Thank you so much for the assistance, it's much appreciated!  Now, if I could only get my WiFi card activated, but I'm gonna hammer away at that for a bit myself before I ask for help again, I don't want to wear out my welcome.  ;)

---

