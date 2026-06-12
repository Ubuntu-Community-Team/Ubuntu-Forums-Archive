---
title: "error message at end of installation"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by nmcvicar on 2007-07-28
I just installed 7.04 (dual boot with WinXP). At the end of the installation I got the following 2 error messages:

1)
Error Removing Casper
files list for package 'perl-modules' is missing final newline
OK

2) 
Error while removing packages
E:sub-process/usr/bin/dpkg returned as an error code(1)
OK

I just continued on to complete the installation. The OS seems to be running well EXCEPT that the updates won't install. 

Any tips would be much appreciated.
Neil

---

### Post by forestpixie on 2007-07-28
When you say the updates won't install - what does it actually say - or does it just fail without an error message.

go to terminal (Application>accessories>terminal)  and try 

sudo apt-get update 

and post that here

---

### Post by nmcvicar on 2007-07-28
Thank you Forestpixie,

Here is the output:

Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Translation-en_CA
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Translation-en_CA
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 3B in 0s (4B/s)  
Reading package lists... Done


Neil

---

### Post by nmcvicar on 2007-07-28
FOrestpixie you asked:
When you say the updates won't install - what does it actually say - or does it just fail without an error message.

The message was as follows:

The following packages are in a broken state:
(several blank lines - no packages listed)
This may be due to ..... (long explanation)

Thank you,
Neil

---

### Post by forestpixie on 2007-07-28
can you not post the long explanation - it might help

also try this in terminal

dpkg -C

it might need sudo - not sure

---

### Post by nmcvicar on 2007-07-28
hmmm .... the error message is different now. Or more likely, I got the messages mixed up. Sorry.

Anyway, I got the following error message when I tried to install updates -it is correct this time :-)

E: /var/cache/apt/archives/python2.5_2.5.1-0ubuntu1_i386.deb: files list file for package `perl-modules' is missing final newline

Thanks again.

---

### Post by forestpixie on 2007-07-28
I'm not to sure about that one - if no-one else answers the thread with an idea try a new thread - with perl-modules in the title. 

You could try reinstalling perl-modules - I'm not completely sure of the syntax but man suggests
```

sudo apt-get --reinstall perl-modules
```

see if that gets a different error - or even makes it good - if that works try
```

sudo apt-get update
```

---

### Post by forestpixie on 2007-07-28
Ok dug about a bit and found these

[http://ubuntuforums.org/showthread.php?t=494321](http://ubuntuforums.org/showthread.php?t=494321)

[http://ubuntuforums.org/showthread.php?t=497690](http://ubuntuforums.org/showthread.php?t=497690)

[http://ubuntuforums.org/showpost.php?p=1635843&postcount=9](http://ubuntuforums.org/showpost.php?p=1635843&postcount=9)

[https://answers.launchpad.net/ubuntu/+question/2591](https://answers.launchpad.net/ubuntu/+question/2591)

Have a look at them - if you ok with them have a go I guess

or we could try together - be a new one for me so it's up to you :D

---

### Post by nmcvicar on 2007-07-28
THank you forestpixie,

I can't look at it today but hopefully I will get a chance tomorrow (SUnday). I'll post my results.

Neil

---

### Post by nmcvicar on 2007-07-30
Thanks Forestpixie. Unfortunately I had no luck with your suggestions.

I'm going to relate what happens when I try to install the updates. 

1) Update Manager reports 116 updates for my system.

2) When I click "install updates" (with all 116 of them checked) the following error message pops up:

E: /var/cache/apt/archives/python2.5_2.5.1-0ubuntu1_i386.deb: files list file for package `perl-modules' is missing final newline

THanks in advance for any info and advice.

Neil McVicar

---

### Post by forestpixie on 2007-07-30
this is the same issue as you've got in the other thread you posted in - read on from RomeReactor again.

Hope that will help you.

---

