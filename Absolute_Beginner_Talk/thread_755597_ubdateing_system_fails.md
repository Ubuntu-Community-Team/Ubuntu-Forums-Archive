---
title: "ubdateing system fails"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by DrScum on 2008-04-15
I have installed Xubuntu 7.10 and am trying to update the system using "add remove"

I am told that the list of packages is outdated and when I select ot reload files are downloaded initially but the system freezes at some point. When I select cancel I get the following error message:
W: GPG error: [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy Release: The following signatures were invalid: NODATA 2

This happens with the default settings of the repositories as well as with altered settings and after choosing other download servers.

I get similar results when using the synaptic package manager.

Help would be appreciated!

---

### Post by Duckyspetrie on 2008-04-15
Make sure that, at the very least, you have the 'main' and 'universe' repositories enabled. You said you had the default repositories enabled; in 7.10 they didn't enable by default on my system but in 8.04 they did, so just check if you haven't. Refresh it in Add/Remove and see what happens.

---

### Post by Pasty-Flawss on 2008-04-15
very similiar to my problem.. check the recent topics and look for mine called help app error or something.. theres lots of solutions in there but sadly none have worked for me :(.. if i figure something out you'll be the first to know

---

### Post by chrisdugdale on 2008-04-15
When I had this problem I gave up and reinstalled! :(

---

### Post by DrScum on 2008-04-15
That's what I did too! But after the reinstall same picture. I need a solution for this since my original plan was to install Xubuntu at every Machine in our institution (School) with processors between 500MHz and 1Ghz. I am using Xubuntu at home and the updating part works just fine. Moreover, I installed the system at home from the very same CD I used for this system showing the problem.

---

### Post by nickpaton on 2008-04-15
I'm a bit confused as to which of your many posts about this problem you want us to reply to!
It may help if you only post your problem once, so we don't repeat suggestions made by other people :)

Please could you post the output to:

```
 cat /etc/apt/sources.list
```

Also please could you post the result of

```
sudo apt-get update
```

---

### Post by DrScum on 2008-04-15
Thanks for your suggestion, nickpaton. 
Experience in this forum teaches me that you don't get any help if you don't get it within the first few hours after posting. So what else can one do that try to find someone in another section?

---

### Post by nickpaton on 2008-04-15
Fair comment M8! :lolflag:

Any chance of posting the two outputs?

---

### Post by nickpaton on 2008-04-15
Just found this in another post which could be a bug.

To get round it, try

```
sudo apt-get update -o Acquire::http::No-Cache=True
```

---

### Post by DrScum on 2008-04-15
I'm at home now, without access to the culprit. Posting won't be possible before 24h. Thanks for your interest though.

---

### Post by nickpaton on 2008-04-15
I've been searching the forums for the GPG error which indicates a key is missing.
 
Have a look at this post which talks about the bug and a permanent solution which should work for Xubu:

[http://ubuntuforums.org/showthread.php?t=589767]("http://ubuntuforums.org/showthread.php?t=589767")

Possibly if you could post your sources list we can have a look and see if there's a missing key somewhere.

I'll look out for your reply when you're at your PC.

Good luck - Xubuntu is OK isn't it - I use it on low spec laptops.

Nick

---

### Post by DrScum on 2008-04-15
Thanks for the reply, I'll work on the key hint and will try posting the error messages tomorrow.

Yes, Xubuntu is great, I use it at home on an old Dell Latitude Laptop (500mHz, 256Mb RAM) and  I am very happy with it.

---

### Post by DrScum on 2008-04-16
Here the two outputs for nickpaton
The cat /etc/apt/sources.list output
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

The sudo apt-get update output
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Get:2 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/main Translation-en_US             
Get:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/universe Translation-en_US         
Get:4 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/restricted Translation-en_US       
Get:5 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy Release                               
99% [2 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:6 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/main Packages 
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/main Translation-en_US
Get:7 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/universe Packages                   
Get:8 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/restricted Packages                   
Get:9 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/multiverse Packages                   
Get:10 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Get:11 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Get:12 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Get:13 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
99% [3 Translation-en_US bzip2 0]

---

### Post by Jonniefive79 on 2008-04-16
Duckyspetrie already covered this a while back, but it worked for me.

I had the same exact issue after re installing 7.10.  I was solved by ticking the universe, multiverse and all other update options that applied to me in Synaptic-->Settings-->repositories [I think]

Here's the thread I found it in
[http://ubuntuforums.org/showthread.php?t=754797&highlight=universe](http://ubuntuforums.org/showthread.php?t=754797&highlight=universe)

---

### Post by Jonniefive79 on 2008-04-16
I take it all back... now I am stuck too :-?

I got all the initial updates 200+ then had to reboot, now I'm stuck again
This is what I am getting, look familiar?

~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse main universe restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by nickpaton on 2008-04-16
Looking at the cat list, you can see that all the repo's have been #'ed out which means they will not be downloaded, since  there is something which is causing them not to be verified.

You both have gutsy but DrS is i386 and Johnney 64bit.

First thing both of you back up your existing repository sources list:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

That's the command for Ubuntu, I think cp will be recognised  in Xubu.

Open your sources list:

Xubuntu:

```
gksudo mousepad /etc/apt/sources.list
```

and remove the current contents and replace it with:

```

# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```


Save and close the file.

Run

```
sudo apt-get update
```

I've found in Xubuntu quite often that it does not always complete and you end up with biz2 something or other at about 95% or so.

I've just closed at that point and it always seems to be OK. I think it's due to not all the repos being available from the selected server.
What you need to do is change to another server - I'm find I have to change around and currently the main UK site seems to work (this morning!) but have to go to main worldwide server, and sometimes the USA.

For 64bit Ubuntu

To open sources list:

```
gksudo gedit /etc/apt/sources.list
```

and copy the above repo list, but change the title part to:

```

# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Releaseamd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
```

(The title makes no difference to the operation of the sources list but just keeps things correct.)

and again save and close and update

```
sudo apt-get update
```

More information on repositories can be seen [here]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories")

Good luck

---

### Post by Jonniefive79 on 2008-04-16
I was able to fix the part of the problem for a short while by installing two of the synaptic packages: "unattended-upgrades" and "update-apt".  This got me to the point where I could atleast install the "ia32-libs" that I needed to install FAH SMP client.

Still can't get updates, I tried what you suggested, I may not have done it correctly though.  I'm very new to any sort of Linux and operating from a terminal.  Heres what I got...

Thanks for the help!

jonniefive79@jonniefive-desktop:~$ gksudo gedit /etc/apt/sources.list
jonniefive79@jonniefive-desktop:~$ sudu apt-get update
bash: sudu: command not found
jonniefive79@jonniefive-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Releaseamd64 (20071016) gutsy Release.gpg
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Releaseamd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Releaseamd64 (20071016) gutsy/restricted Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Releaseamd64 (20071016) gutsy Release
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Releaseamd64 (20071016) gutsy/main Packages
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Releaseamd64 (20071016) gutsy/restricted Packages
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Releaseamd64 (20071016) gutsy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Releaseamd64 (20071016) gutsy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US          
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Fetched 3B in 10s (0B/s) 
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Releaseamd64 (20071016)]/dists/gutsy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Releaseamd64 (20071016)]/dists/gutsy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by nickpaton on 2008-04-17
My bad Jonnie - there was a typo error (now corrected).

Can you open your sources list and remove the bit you inserted at the top and repaste the corrected version above.

I'd missed out a '#' against CD rom:....... and so update was trying to find a file called CD rom!

Otherwise it looks good to me.

Do you play music or DVD,s on your PC?  If so  you will need to add the medibuntu repo to your sources list

Via a Terminal carry out the following:

Install the key

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


Add medibuntu to the sources list

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Note medibuntu will not appear on the sources list but runs when ever updates are requested.

More details on medibuntu and how it works [here]("https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29")

---

### Post by DrScum on 2008-04-21
nickpaton, thanks for your effort. I did what you posted above, updating the sources list with the code you posted. This is what I get when tryint to run the update:
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
DrScum@B-211-05:~$

When trying to run "add remove" I still get the message that the list of packages is not up to date and when I select "update" the program freezes (its frozen right now and I don't know how to force quit it).

Regarding your comment "it looks good": my main concern is not to have the system updated but to have the open office components OOocalc, OOobase and OOomath installed.

---

### Post by nickpaton on 2008-04-21
Sorry for the delay getting back to you - away for the weekend.

That error message can be because Synaptic is open as well as the Add/Remove window.
Also the update server could be down, which as I've said before is not uncommon.

<EDIT> Also have a look at[ this post]("http://ubuntuforums.org/showthread.php?t=760461#5") <EDIT>

In general I would suggest using Synaptic rather than Add/ Remove which is not always as reliable.

To add the Oo packages you want, within Synaptic use search option to find open office calc and select the package and so on for the rest you want.  
Then click the Add button to install all of them.  
Using Synaptic guarantees that any dependencies are also automatically installed.

---

### Post by DrScum on 2008-04-22
I was trying to use the synaptic manager but couldn't find the OOo packages. Via Synaptic I find only a bunch of language packs and help files bur neither calc nor base nor math. But then, the list wasn't up to date and I still fail to uptdate it even when the synaptic package manager is the only program open. The error message regarding the lock remains.

I'll keep trying.

---

### Post by DrScum on 2008-04-22
I was successful in getting rid of the lock file error message by renaming the file /var/lib/apt/lists/lock (need to be root to do this).

Then using the terminal command sudo apt-get -update leaves me with a freezing download at

Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:8 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                      
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                   
Get:10 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages              
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                     
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                     
98% [4 Translation-en_US bzip2 0] 

To me it seems as if this 4 Translation-en_US bzip2 0 file is the culprit. If I kill the download using ctrl c, I think the list of available packages does not get updated ant that seems to be my problem. Is there a way to skip this crappy file during download or is there a way of letting the list file appear updated?
Alternatively: does anyone have a better solution?

Here my goals in a nutshell: I want to install the complete OpenOffice suite (including the calc, the base, the draw and the math modules) and I want to be able to install software from the repositories in the future.

I chose Xubuntu since I have had good experiences with it on machines with Pentium III processors and 125mB RAM whereas the regular Ubuntu I find too slow on machines with relatively low processor and RAM power.

---

### Post by nickpaton on 2008-04-22
OK - to install Open Office, Oo base, Oo calc, Oo maths - 

Two ways (close Add/Remove.. package if open) -

**_1. Using Synaptic_**

search for openoffice.org-base, openoffice.org-calc, openoffice.org-math
Right click and select install packages and Apply to install.

**_2. Using Terminal_**

Close Synaptic and Add/ Remove..

Open a Terminal and run:

```
sudo apt-get install openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-math
```

Re the errors at 98%, this has been the norm for me in Xubuntu and I think is due to some of the repos being down.  The way I've sorted it is to change the location where I get them from - i.e. change from the USA to somewhere else.

In general I've simply updated when the update logo appears, and tend not to sudo apt-get update.

---

### Post by DrScum on 2008-04-23
I did use the Synaptic package manager and was searching for the open office programs, but they didn't turn up.

I usually do as you do only update when there is an alert, but in this case I need specifically some programs that aren't installed by default. 

Thanks again for your help. I hope I get this sorted out now.

---

### Post by nickpaton on 2008-04-23
Have you managed to install the Oo packages using the Terminal as I suggested?

What happens if you try to install the programs using the terminal - just copy and paste the command in my last post into a Terminal!

Unfortunately I don't have a working Xubuntu PC to look at so I can't check within Synaptic to see if they are listed, but I'm fairly sure that I did load all of Oo using the Synaptic method on an Xubu PC a couple of weeks ago.

What happens if you type 'openoffice.org-math' (no '  ') into Synaptic Search, for instance - is it listed?  What happens if you type 'openoffice.org' - again is anything listed in Synaptic?

Other than this I don't know what to suggest.  Maybe you could download the latest verion Oo from [here]("http://openoffice.bouncer.osuosl.org/?&product=OpenOffice.org&os=linuxintelwjre&lang=en-US&version=2.4.0")

Install help is available from [here]("http://download.openoffice.org/common/instructions.html#linux")

I've even done a forum search on missing Oo packages and can't find anything.

---

### Post by DrScum on 2008-04-24
openoffice.org-base doesn't yield any result when using in the search option of the synaptic package manager. Neither do the other strings you use in your post above.

When entering the terminal command you are posting above I'm left with the following:

DrScum@B-211-05:~$ sudo apt-get install openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-math
[sudo] password for DrScum:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ttf-opensymbol openoffice.org-writer openoffice.org-core
  openoffice.org-common
E: Package openoffice.org has no installation candidate
DrScum@B-211-05:~$ 

The message could be interpreted to the effect that the packages are installed, however, I can't find the applications anywhere in the system.

I know, that you're doing your best, but on my end this is becoming a nightmare! And I won't be able to convince anybody that Xubuntu is the way to go.

---

### Post by nickpaton on 2008-04-24
It looks like Oo isn't even installed!

What version of Xubuntu did you download?

As I said before I very recently had to install Oo for someone on their Xubu Thinkpad and had no probs at all.  But I am now wondering if I had to download and install it straight off the Oo site.
I use Xubu Gutsy Alternative i386 regardless of the machine it's going onto.

What is the spec of the box you're loading it onto?

Just to compare notes I've found Xubu to be perfect for older or less powerful boxes.  I'm quite careful in what wireless cards I use, so that they'll be automatically detected during installation and so find everything is quite painless, just leaving the multimedia extras to sort out.

I can totally understand your frustration at this "so-simple" problem!  I'll see if I can put a laptop together tomorrow and load Xubu on and see what is available Oo-wise.

Other than that, maybe you simply need to download the package from the site and get it installed that way - not great but it'll solve your immediate problem and let you live a proper life again!!

---

### Post by DrScum on 2008-04-25
As posted at the beginning of this adventure I am using Xubuntu alternate CD i386 just as you say and just as you say, an install from the very same CD works flawless on an old Dell Latitude. There I installed OOo using the "add remove" option. 

Thus it might have something to do with the network architecutre. I'll research in that direction and, as Plan B, I'll try Xubuntu 8.04 next week.
For this week from the workplace over and out!

---

### Post by DrScum on 2008-04-28
Meanwhile installed Xubuntu 8.04, initially had the same problems described above. Using "software sources" after testing for the best server and selcting it as well as unchecking the multiverse repositories I was able to update the list of apps and to install the OpenOffice suite.

---

### Post by nickpaton on 2008-04-28
That sounds good!

I tend not to use the search for best server since too often it selects one that turns out is dead!  I just stick to UK (being from there!) and within UK the various mirrors; the main Ubu / xubu server; USA mirrors - only because once I got a 100% download from somewhere in that country.

Are you now fully working regarding that problem?  If so you may want to mark the thread as SOLVED.

---

### Post by DrScum on 2008-04-29
I thought I did mark the thread as solved by editing the first post. Is there another way?

---

### Post by nickpaton on 2008-04-29
If the thread is not totally solved then don't mark as solved!

There is a problem with the mark as solved function which will probably be solved in due course

See [this]("http://ubuntuforums.org/showthread.php?t=766298") post.

How to do it [here]("http://ubuntuforums.org/showthread.php?t=771417").

Great talking to you and see you around.

Nick

---

