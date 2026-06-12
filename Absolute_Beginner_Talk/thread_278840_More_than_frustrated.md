---
title: "More than frustrated"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by BStyles on 2006-10-17
Yeah, I'm a noob.  But if the Linux community wants or expects Linux distros to compete with Windows/Apple, it's, at the very least, going to have to stop releasing software with package managers that don't work.  At least I can install software on my Windows boxes (usually).  For a solid week I've been simply trying to install some additional software on my shiney new Ubuntu box.  But, alas, it seems that all that great new software is locked in repositories whose indexes can't be downloaded - without exception, every single title I'm interested in seems to be located in a reposirory that's "403 Forbidden".  Yes, I've scanned the forums and tried various posted command line work arounds but nothing has worked for me.  And all I want to be able to do is simply play a DVD.  Oh, I'm sure I'm not doing something right, but I've checked and rechecked what I'm typing with what I'm reading and it just isn't happening.  Should I just go play my little DVD on one of my Windows or Apple boxes and leave Linux to the 'big boys' or can someone out there tell me how to do what I've described?  I mean really take the time to TELL me - no one line post with a link to something I've already tried.

thx

---

### Post by thephotoman on 2006-10-17
Could you do something for me?

Go into the command line and type:

gedit /etc/apt/sources.list

and copy and paste the contents of that file here.  I need to know to which servers you're connecting.

---

### Post by RudolfMDLT on 2006-10-17
BStyles, I'm not picking a fight here... I know a bit about computers, more than some less than others. If you didn't post or talk, we(the forum) could not smell that you had a problem. Please just drop a little attitude. Unfortunatly I can't help you now because I'm off to work but I'll be back later to see if I can't help you. 

In the meantime, read this:

[http://www.ubuntuforums.org/showpost.php?p=1488521&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1488521&postcount=1)

It's not gonna help your computer problems but it will atleast give you an insight into forum culture.

Best of luck!

Cheers,

Rudolf

---

### Post by Ozitraveller on 2006-10-17
> **BStyles said:**
> Yeah, I'm a noob.  But if the Linux community wants or expects Linux distros to compete with Windows/Apple, it's, at the very least, going to have to stop releasing software with package managers that don't work.  At least I can install software on my Windows boxes (usually).  For a solid week I've been simply trying to install some additional software on my shiney new Ubuntu box.  But, alas, it seems that all that great new software is locked in repositories whose indexes can't be downloaded - without exception, every single title I'm interested in seems to be located in a reposirory that's "403 Forbidden".  Yes, I've scanned the forums and tried various posted command line work arounds but nothing has worked for me.  And all I want to be able to do is simply play a DVD.  Oh, I'm sure I'm not doing something right, but I've checked and rechecked what I'm typing with what I'm reading and it just isn't happening.  Should I just go play my little DVD on one of my Windows or Apple boxes and leave Linux to the 'big boys' or can someone out there tell me how to do what I've described?  I mean really take the time to TELL me - no one line post with a link to something I've already tried.

thx


This might give you a better idea of what's happening.

How to install ANYTHING in Ubuntu!
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Hope it helps.

---

### Post by seshomaru samma on 2006-10-17
Welcome to Ubuntu forum

In fact Ubuntu's pacakage manager is very good , if there is anything tha Ubuntu does well it's most certainly installing software with ease. there could be several reasons why your package manager is not working correctly , but in order to help you we need more info:
1) can you tell us more about your machine and its specs? is it by any chance 64 bit? 
2) what version of Ubuntu did you install?
3) can you give an example of a particular software that you tried to install? how did you do it and what errors did you get? (it's best if you copy-paste the errors directly to your post)

Best of luck

---

### Post by SunnyRabbiera on 2006-10-17
worse comes to worst use synaptic, I love that program :D

---

### Post by seijuro on 2006-10-17
also include how you connect to the internet and if it is working. Also make sure to check you have the proper repositories set up in your package manager. If you don't know how to change the repos post that too and we can supply that info for you. I have dialup and my modem drops a lot and occasionally when it drops while the package manager is pulling the package list which creates all sorts of problems and simply telling it to download again will not fix it if you think this happened to you try what I did. I removed all but the universe and multiverse repos and downloaded the pkg lists again. then I added them back and told it to update and it downloaded fresh copies of the lists that borked.

---

### Post by r4ik on 2006-10-17
[QUOTE=BStyles;1626298]Yeah, I'm a noob.  But if the Linux community wants or expects Linux distros to compete with Windows/Apple, it's, at the very least, going to have to stop releasing software with package managers that don't work.  At least I can install software on my Windows boxes (usually).  For a solid week I've been simply trying to install some additional software on my shiney new Ubuntu box.  But, alas, it seems that all that great new software is locked in repositories whose indexes can't be downloaded - without exception, every single title I'm interested in seems to be located in a reposirory that's "403 Forbidden".  Yes, I've scanned the forums and tried various posted command line work arounds but nothing has worked for me.  And all I want to be able to do is simply play a DVD.  Oh, I'm sure I'm not doing something right, but I've checked and rechecked what I'm typing with what I'm reading and it just isn't happening.  Should I just go play my little DVD on one of my Windows or Apple boxes and leave Linux to the 'big boys' or can someone out there tell me how to do what I've described?  I mean really take the time to TELL me - no one line post with a link to something I've already tried.

Please try in a terminal,

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

    * Replace everything with the following lines 

    To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code) 
    e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse 

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

    * Save the edited file 

wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -
sudo apt-get update


Now you could follow this guide just copy and paste in a terminal,

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Good luck !

---

### Post by BStyles on 2006-10-17
My thanks to everyone who responded.  I will try to provide the info as requested.

1. thephotoman:

Here you go.  This, of course, is not the content of the originally installed sources.list.  I got this from a post somewhere and I believe it matches that recommended by r4ik in his response below.

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORT REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

2. RudolfMDLT:

I tend to be rather direct and abrupt in all my communications.  If you choose to consider my comments, criticism, and disappointment as "attitude", so be it.  I'm too old to worry much about stepping on toes.  I 'm not here for the "culture", I'm here for help and to learn. By the way, the anology of the Rude Fisherman hardly applies here.  I don't expect Ubuntu to be like Windows, Apple or any other OS.  But I do expect it to work. In any case, I assure you I will appreciate any help you choose to offer.  Nuff said.

3. Ozitraveller:

I'm looking at the link you sent.  I haven't seen anything yet that addresses my particular issue, but it most definately contains a lot of great information that I will be referring to.  Thank you!

4. seshomaru samma:

1) 1.6 GHz P4, 32 bit, 1 gig RAM.
2) 6.06.1
3) Xine, Adobe Reader.  The problems are not specifically with installing the software.  They are with connecting to the repositories. Whether I reload through Add/Remove Applications or Synaptic, I get the following:

[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) 403 Forbidden
[http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) 403 Forbidden
[http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]

5. SunnyRabbiera:

See #4 above.

6. seijuro:

Actually, I have the exact same issues whether at home using DSL or at work using our T1.  Both are up and working fine.  Also, I have tried the manipulations you mention with the package manager and package lists, but it didn't work for me.

7. r4ik:

Been there, done that. See #1 above.


Thanks all

- no 'tude here

---

### Post by justin whitaker on 2006-10-17
Bstyles:

There are legal reasons why Ubuntu cannot ship with every multimedia codec or proprietary application on the install disc. Many linux distros do, but that is not legally correct. Of course, they haven't been dragged into court yet....but it's not no harm no foul. Cannonical is a big target to sue, little distros like PCLinuxOS aren't worth a lawsuit. 

That said: 

Try the localize hack that r4ik suggested.

Also, try Automatix or EasyUbuntu before searching out the packages seperately.

---

### Post by TheWalt on 2006-10-17
I notice that the repositories are not the US servers, of which I have had no issue with.  Did you try using those?

---

### Post by Ozitraveller on 2006-10-18
> **BStyles said:**
> My thanks to everyone who responded.  I will try to provide the info as requested.

1. thephotoman:

Here you go.  This, of course, is not the content of the originally installed sources.list.  I got this from a post somewhere and I believe it matches that recommended by r4ik in his response below.

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORT REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

2. RudolfMDLT:

I tend to be rather direct and abrupt in all my communications.  If you choose to consider my comments, criticism, and disappointment as "attitude", so be it.  I'm too old to worry much about stepping on toes.  I 'm not here for the "culture", I'm here for help and to learn. By the way, the anology of the Rude Fisherman hardly applies here.  I don't expect Ubuntu to be like Windows, Apple or any other OS.  But I do expect it to work. In any case, I assure you I will appreciate any help you choose to offer.  Nuff said.

3. Ozitraveller:

I'm looking at the link you sent.  I haven't seen anything yet that addresses my particular issue, but it most definately contains a lot of great information that I will be referring to.  Thank you!

4. seshomaru samma:

1) 1.6 GHz P4, 32 bit, 1 gig RAM.
2) 6.06.1
3) Xine, Adobe Reader.  The problems are not specifically with installing the software.  They are with connecting to the repositories. Whether I reload through Add/Remove Applications or Synaptic, I get the following:

[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) 403 Forbidden
[http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) 403 Forbidden
[http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) 403 Forbidden [IP: 195.248.90.54 80]

5. SunnyRabbiera:

See #4 above.

6. seijuro:

Actually, I have the exact same issues whether at home using DSL or at work using our T1.  Both are up and working fine.  Also, I have tried the manipulations you mention with the package manager and package lists, but it didn't work for me.

7. r4ik:

Been there, done that. See #1 above.


Thanks all

- no 'tude here


Acrobat is in Multiverse
xine-ui is in Universe

Ubuntu packages (searchable)
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Sources.list generator 
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)


This is my sources.list file as an example:

> 
## 
## Use the following repos only if you need them. 
## To use one remove the "#" from the line that starts with "# deb". 
## 


## ---------------- cdrom

## deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

## ---------------- main restricted

## deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
## deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted


## ---------------- Updates

## Major bug fix updates produced after the final release of the
## distribution.
## deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted


## ---------------- Universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
## deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe


## ---------------- Backports

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
## deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse


## ---------------- Security

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted


## ---------------- Multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse


## ---------------- Backports Extras

## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) dapper-extras main restricted universe multiverse
  
  
## ---------------- Commercial by canonical

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
  
  
## -------------------------------------------------
##                  3rd party repos 
## -------------------------------------------------

## ---------------- Dapper PLF primary (Penguin Liberation Front)
## http 100mbit/s mirror provided thanks to OVH [http://ovh.com](http://ovh.com) 
# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free


## ---------------- plf secondary repo. Use if primary repo is offline. 
## FTP mirror from [http://free.fr](http://free.fr) (french ISP) 
## deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
## deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free


## ---------------- plf mirror. Use if primary and secundairy are offline 
## deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) dapper free non-free


## ---------------- Automatix
## deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) dapper free non-free
## deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) dapper free non-free


## deb [http://plf.acnova.com/ubuntu/plf/](http://plf.acnova.com/ubuntu/plf/) dapper free non-free
## deb-src [http://plf.acnova.com/ubuntu/plf/](http://plf.acnova.com/ubuntu/plf/) dapper free non-free


## ---------------- Cipherfunk multimedia packages (GPG key: 33BAC1B3)
## gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
## gpg --export --armor 33BAC1B3 | sudo apt-key add -
## deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
## deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main


## ---------------- Seveas' Ubuntu packages  (GPG key: 1135D466)   
## You can enter this key into the APT trusted keys database with the following command
## gpg --keyserver subkeys.pgp.net --recv 1135D466
## gpg --export --armor 1135D466 | sudo apt-key add -
## or 
## wget [http://seveas.ubuntulinux.nl/1135D466.gpg](http://seveas.ubuntulinux.nl/1135D466.gpg) -O- | sudo apt-key add -
## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) dapper-seveas all
## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) dapper-seveas freenx
           

## ---------------- Bleeding edge (official) wine repository for Dapper
## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


## ---------------- skype (official)
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free           


---

### Post by H.E. Pennypacker on 2006-10-19
BS Styles, there's something clearly wrong with the repositories you are using, because no one else is having this problem.  That's a guaruntee.  I regularly connect to Ubuntu repositories and others, and this never happens.

Either you're using the wrong repositories (if that's the case, replace the entire repositories document with a fresh one), or there's something going on between the package manager and the Internet.  It almost seems as if the package manager is blocked; doesn't have an Internet access.

---

### Post by Peepsalot on 2006-10-19
This thread has some good info I think.  I didn't really read it all, but looks like one of the causes can be firewall settings.
[http://www.ubuntuforums.org/showthread.php?t=186455&highlight=403+Forbidden](http://www.ubuntuforums.org/showthread.php?t=186455&highlight=403+Forbidden)

---

### Post by gn2 on 2006-10-19
> **justin whitaker said:**
> Bstyles:

There are legal reasons why Ubuntu cannot ship with every multimedia codec or proprietary application on the install disc. Many linux distros do, but that is not legally correct. Of course, they haven't been dragged into court yet....but it's not no harm no foul. Cannonical is a big target to sue, little distros like PCLinuxOS aren't worth a lawsuit. 


Legally it could be argued that there is no difference between having these packages on the disc and available through the OS's package management software.

Canonical is facilitating the use of the proprietary software as it is, so there's no difference how it is supplied?

And lastly, biggest isn't always best. There are quite a few reasons for choosing PCLinuxOS over Ubuntu.....
E.G. GUI Disc Mounting, Install to USB an option on the Draklive Installer

The Ubuntu forums are busy for a reason....

.

---

### Post by Ozitraveller on 2006-10-20
Oops

---

### Post by Ozitraveller on 2006-10-20
Open a web browser and browse to one of the repos in the error list on page 1.

I went to this one without any problems:
> 
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/)


It would be interesting to see whether it gives you any more information.

---

