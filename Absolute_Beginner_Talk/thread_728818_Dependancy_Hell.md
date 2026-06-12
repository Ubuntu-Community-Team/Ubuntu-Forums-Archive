---
title: "Dependancy Hell"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Zubatron on 2008-03-19
I am in dependancy hell. Though I've been using Linux only for about a week or so I've been trying to install Wine or Virtual Box so I can install some of my windows games. I am using Ubuntu 6.06.

No matter how hard I try to install Wine it says I need libxalan110. So I install libxalan110 and it says I need libxerces27 and so I download libxerces27 and it says I need libc6 and I couldn't download it.

And virtual box did something similar. Argh, it's very frustrating and seems to be no end in sight. All I want to do is install one simple windows game and it's turning more into a complete frustration more than anything.

---

### Post by tangibleorange on 2008-03-19
Where did you download wine from? Did you get it from the official ubuntu repos? If so, Syanptic should automatically install any dependencies...

---

### Post by Barrucadu on 2008-03-19
Try installing things with apt-get, it downloads and configures all dependancies automatically.

**sudo apt-get install *packagename***

---

### Post by Zubatron on 2008-03-19
I downloaded wine from the winehq website. Is there a link to the offical ubuntu repos?

---

### Post by Wobedraggled on 2008-03-19
Upgrade to 7.10 or wait a few weeks and upgrade to Hardy.

---

### Post by Oldsoldier2003 on 2008-03-19
> **Zubatron said:**
> I am in dependancy hell. Though I've been using Linux only for about a week or so I've been trying to install Wine or Virtual Box so I can install some of my windows games. I am using Ubuntu 6.06.

No matter how hard I try to install Wine it says I need libxalan110. So I install libxalan110 and it says I need libxerces27 and so I download libxerces27 and it says I need libc6 and I couldn't download it.

And virtual box did something similar. Argh, it's very frustrating and seems to be no end in sight. All I want to do is install one simple windows game and it's turning more into a complete frustration more than anything.

6.06 uses an older version of wine, you need to use the version from the repo in order to not run into dependency problems. if you need to install a newer app on the LTS releases of Ubuntu its better to compile it from source than it is to download the deb from an outside source.

---

### Post by tangibleorange on 2008-03-19
> **Zubatron said:**
> I downloaded wine from the winehq website. Is there a link to the offical ubuntu repos?

Just type:

```
sudo apt-get install wine
```

This will install wine from the official Ubuntu repositories - it should gather all the dependencies for you.

---

### Post by Zubatron on 2008-03-19
So i tried to just install wine through the terminal and here is what I got

matt@matt-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up liblog4j1.2-java-doc (1.2.12-1ubuntu2) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
cannot create dhelp file '/usr/share/doc/liblog4j1.2-java-doc/docs/.dhelp': No such file or directory
dpkg: error processing liblog4j1.2-java-doc (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 liblog4j1.2-java-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
matt@matt-laptop:~$

---

### Post by rudihawk on 2008-03-19
Maybe you should try compile it from source?

---

### Post by Zubatron on 2008-03-19
Sorry for sounding like a complete and utter imbecile and n00b but how would I go about that?

---

### Post by tangibleorange on 2008-03-19
It looks like you have a broken package on you system. Try thiis command:

```
sudo apt-get clean
```

---

### Post by Zubatron on 2008-03-19
When I tried that command nothing happened

---

### Post by undertakingyou on 2008-03-19
also you might want to try a ```
sudo aptitude update
sudo aptitude upgrade
``` aptitude does a good job of fixing stuff that brakes partway through install or is having dependency issues.

---

### Post by Zubatron on 2008-03-19
and this is what i got when i tried those

matt@matt-laptop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Fetched 5B in 1s (4B/s)
Reading package lists... Done
matt@matt-laptop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  libatm1 patch
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/165kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Media Change: Please insert the disc labeled 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)' in the drive '/cdrom/' and press enter

aptitude: download_signal_log.cc:67: virtual bool download_signal_log::MediaChange(std::string, std::string): Assertion `rval != -1' failed.
Aborted

---

### Post by Oldsoldier2003 on 2008-03-19
> **tangibleorange said:**
> It looks like you have a broken package on you system. Try thiis command:

```
sudo apt-get clean
```

all that command does is clear the apt archives. it doesn't fix broken packages, it frees up some disk space and makes the user re download packages

---

### Post by Zubatron on 2008-03-19
So, I'm contemplating on either installing 7.10 or waiting for the 8.04... Will 7.10 make it easier to install wine?

---

### Post by rudihawk on 2008-03-19
WINE should install with the package manager without a hitch in 7.10...

8.04 wont be due for another month i think.

---

### Post by Oldsoldier2003 on 2008-03-19
> **Zubatron said:**
> and this is what i got when i tried those

matt@matt-laptop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Fetched 5B in 1s (4B/s)
Reading package lists... Done
matt@matt-laptop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  libatm1 patch
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/165kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Media Change: Please insert the disc labeled 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)' in the drive '/cdrom/' and press enter

aptitude: download_signal_log.cc:67: virtual bool download_signal_log::MediaChange(std::string, std::string): Assertion `rval != -1' failed.
Aborted

now it looks like we have a problem. you said you installed 6.06 but apt-get wants the gutsy CD. instead of the dapper cd. This leads me to believe that you have managed somehow to mix your dependencies between versions.... which will lead to BIG problems. 

I suggest backing up your personal data then deciding:
whether to install Gutsy (ubuntu 7.10)
or whether to reinstall Dapper (6.06)
I would not recommend Hardy  because its still a development release. 

The odds are against a successful upgrade because you still need to dist upgrade to 7.04 before you caniupgrade to 7.10

---

### Post by undertakingyou on 2008-03-19
> **Oldsoldier2003 said:**
> now it looks like we have a problem. you said you installed 6.06 but apt-get wants the gutsy CD. instead of the dapper cd. This leads me to believe that you have managed somehow to mix your dependencies between versions.... which will lead to BIG problems. 

I suggest backing up your personal data then deciding:
whether to install Gutsy (ubuntu 7.10)
or whether to reinstall Dapper (6.06)
I would not recommend Hardy  because its still a development release. 

The odds are against a successful upgrade because you still need to dist upgrade to 7.04 before you caniupgrade to 7.10

At the very least I would browse the /etc/apt/sources.list file and removing all lines that say Gutsy or are looking for a CD.

---

### Post by Zubatron on 2008-03-19
well that will make it easy as I hardly have any personal data on Ubuntu its all stored on another partition. Well I'm gonna upgrade to 7.10 and see how that goes.

---

### Post by undertakingyou on 2008-03-19
> **Zubatron said:**
> well that will make it easy as I hardly have any personal data on Ubuntu its all stored on another partition. Well I'm gonna upgrade to 7.10 and see how that goes.

I think that you will be very happy with that choice, and maybe wonder why you didn't do it earlier :)  You'll have to post back how it went.

---

### Post by Oldsoldier2003 on 2008-03-19
> **Zubatron said:**
> well that will make it easy as I hardly have any personal data on Ubuntu its all stored on another partition. Well I'm gonna upgrade to 7.10 and see how that goes.

7.10 is a good choice, when hardy is released there will be a direct upgrade path.

---

### Post by Zubatron on 2008-03-19
Ok I installed 7.10 now but a few questions, where is my parititioned drive? The drive that Ubuntu is on has 50gb and im missing my 19gb backup drive when I go to computer? HELP!

---

### Post by Oldsoldier2003 on 2008-03-19
> **Zubatron said:**
> Ok I installed 7.10 now but a few questions, where is my parititioned drive? The drive that Ubuntu is on has 50gb and im missing my 19gb backup drive when I go to computer? HELP!

```
sudo fdisk -l
```
will show you a list of your drives and partitions (thats a lowercase L)

---

### Post by Zubatron on 2008-03-19
ok it shows my backup drive there but how do i get it to show up?

---

### Post by Zubatron on 2008-03-19
bump

---

### Post by Oldsoldier2003 on 2008-03-19
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) is a good resource to help you understand mounting drives and using fstab to make them persistent

---

