---
title: "Repositories enabled, but still getting &quot;Error code 1&quot;"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-07-15
After fresh install of 7.04 a couple of weeks ago, I am now having trouble finding packages that I can install. I keep getting the "Error Code 1" message. I have enabled all the repositories as instructed on the "Install anything in Ubuntu" page,  did the sudo update and sudo upgrade thing, and still there are certain repos that can't be accessed because of the error code 1. After the sudo upgrade I get the message
 "99% [11 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources [1523kB]            
99% [12 Sources gzip 0]                                               759kB/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                        
  Sub-process gzip returned an error code (1)
Fetched 12B in 44s (0B/s) "
Anyone have any ideas as to what is going on here ?? I read some other posts on this matter, but no solutions have been forthcoming so far. Any help will be realllly appreciated. I also used gksudo to uncomment the lines in /ect/apt/sources.list, still with no effect. Here is my sources list --
"# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main universe restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main universe restricted multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main universe restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main universe restricted multiverse #Added by software-properties

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main universe restricted multiverse #Added by software-properties

## BERYL PROJECT
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

#AUTOMATIX REPOS END

---

### Post by AlexenderReez on 2007-07-15
sometimes that situation will happen,it is repositories error....for me i will reload it again...or just upgrade softwares that available then wait couple of hours to check it back....

---

### Post by jerrynewt on 2007-07-15
Thanks for the quick reply. Been at this thing for two weeks now and no change. I reload three or four times a night with the same error messages. Any ideas??

---

### Post by forestpixie on 2007-07-15
have you tried commenting out 1 line at a time to see which is causing problems?

have you tried removing "#Added by software-properties" from the lines it appears on?

Just a thought

---

