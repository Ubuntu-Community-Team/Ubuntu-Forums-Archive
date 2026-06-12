---
title: "[SOLVED] problem in installing new softwares"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by srikrishnan on 2007-12-14
Hi,

Just now I have installed Ubuntu 7.10 64bit version as my second OS in my AMD 64 bit processor system successfully.

Also I have configured my Internet connection also successfully. When I open Browser, I am able to browse all the pages.

But When I try to install any software through ADD/REMOVE programs. I have encountered the following dialog box. But I am not able to find such a button in that interface

"The list of applications is not availabe
Click on 'Reload' to load it. To reload the list you need a working internet connection. "

But I am not encountered such a problem earlier in Ubuntu 7.04. Please help me to solve this problem.

Regards,
Srikrishnan

---

### Post by simon_is_learning on 2007-12-14
If it's a repositorie error you can go to 

System -> Administration -> Synaptic package manager.

---

### Post by srikrishnan on 2007-12-14
Hi,

Thanks for your reply,

I have tried that in synaptic package manager.

Eventhough I am not able install any software.

Regards,
Srikrishnan

---

### Post by hyper_ch on 2007-12-14
open a terminal and run the following command and post the output here:

```

sudo apt-get update

```

---

### Post by srikrishnan on 2007-12-15
Hi,

I have pasted below, the result as per you mentioned in your mail.

srikrishnan@srikrishnan-desktop:~$ sudo apt-get update
[sudo] password for srikrishnan:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_IN
Reading package lists... Done
srikrishnan@srikrishnan-desktop:~$ 

Please give me your valuable suggestions.

Regards,
Srikrishnan

---

### Post by PmDematagoda on 2007-12-15
I think your sources.list file is borked, post the result of:-

```
cat /etc/apt/sources.list
```

---

### Post by trimethoxy on 2007-12-15
> **hyper_ch said:**
> open a terminal and run the following command and post the output here:

```

sudo apt-get update

```


Sorry for the piggyback, but I, too, am new to ubuntu and am having the same problem. My output was the following:

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Fetched 2B in 0s (3B/s)  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by PmDematagoda on 2007-12-15
Concerning your problem, do:-

```
sudo rm /var/lib/dpkg/lock
```

Then do:-

```
sudo apt-get update
```

---

### Post by srikrishnan on 2007-12-15
please see the below result:

srikrishnan@srikrishnan-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
srikrishnan@srikrishnan-desktop:~$ sudo rm /var/lib/dpkg/lock
srikrishnan@srikrishnan-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_IN
Reading package lists... Done
srikrishnan@srikrishnan-desktop:~$

---

### Post by PmDematagoda on 2007-12-15
Ok, edit the sources.list file, open it for editing using:-

```
gksudo gedit /etc/apt/sources.list
```

Then uncomment the repository addresses by removing the # in front of them so that such lines as these:-

```
#deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
#deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

```
look like this:-
```
deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

```

After you edit the file do:-
```

sudo apt-get update
```

That should fix your problem.

---

### Post by srikrishnan on 2007-12-15
Hi,

Now Add/Remove programs works fine.

Thanks for your great and immediate help

Regards,
Srikrishnan

---

### Post by PmDematagoda on 2007-12-15
Glad I was able to help:).

Wish you a Happy Holiday Season:lolflag:.

I seem to be giving a lot of holiday greetings today:).

---

### Post by trimethoxy on 2007-12-15
> **PmDematagoda said:**
> Concerning your problem, do:-

```
sudo rm /var/lib/dpkg/lock
```

Then do:-

```
sudo apt-get update
```

looks like it worked, thanks.  however, i can't install anything now because i am using the 64-bit ubuntu :(

---

### Post by PmDematagoda on 2007-12-15
Could you please elaborate on what you said about the problem that you cannot install anything?

---

### Post by trimethoxy on 2007-12-15
> **PmDematagoda said:**
> Could you please elaborate on what you said about the problem that you cannot install anything?

Whenever I try to add an application via add/remove application, it says "**** cannot be installed on your computer type(amd64).  Either the application requires special hardware features or the vendor decided to not support your computer type."

---

### Post by srikrishnan on 2007-12-15
Hi,

I have successfully installed some of my favourite softwares.

But still I am not able to configure my language as additional to English.

keyboard icon appears at the top right of the taskbar.

But when i click it will not work.

how can I solve this problem and use to type in my own language.

Thanks in Advance,
Srikrishnan

---

### Post by Ub1476 on 2007-12-15
System>Preferences/Administration>Keyboard/Lanuage tools, should fix any wrong keyboard setups and language.

---

### Post by trimethoxy on 2007-12-15
> **trimethoxy said:**
> Whenever I try to add an application via add/remove application, it says "**** cannot be installed on your computer type(amd64).  Either the application requires special hardware features or the vendor decided to not support your computer type."

Nevermind, it seems to have worked itself out.  Thanks for your help.

---

### Post by PmDematagoda on 2007-12-15
Glad I could help you out with your Ubuntu problems:).

---

### Post by srikrishnan on 2007-12-16
Eventhough I enabled "Tamil" language in "Language Support" tool.

Icon in the top right of the taskbar for selecting keyboard drivers not working.

Can anybody helpme in this.

Regards,
Srikrishnan

---

