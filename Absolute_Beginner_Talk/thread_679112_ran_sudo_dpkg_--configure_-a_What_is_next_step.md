---
title: "ran sudo dpkg --configure -a What is next step?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by chick penguin on 2008-01-26
When I tried to update I got the message:
"Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first."

I check the on line postings regarding this problem and ran this command in the terminal:
sudo dpkg --configure -a

after that I got this in the terminal window:
Setting up libpq4 (8.1.11-0ubuntu0.6.06.1) ...

Setting up libxml2 (2.6.24.dfsg-1ubuntu1.1) ...

Setting up libcairo2 (1.0.4-0ubuntu1.2) ...

Setting up konsole (3.5.2-0ubuntu27.3) ...

Setting up kdebase-data (3.5.2-0ubuntu27.3) ...

Setting up libopal-2.2.0 (2.2.1-1ubuntu1.1) ...

Setting up kdebase-bin (3.5.2-0ubuntu27.3) ...

Setting up libpt-1.10.0 (1.10.0-1ubuntu1.1) ...

Setting up kpager (3.5.2-0ubuntu27.3) ...

Setting up libkonq4 (3.5.2-0ubuntu27.3) ...

Setting up kpersonalizer (3.5.2-0ubuntu27.3) ...

Setting up kate (3.5.2-0ubuntu27.3) ...

Setting up ksysguardd (3.5.2-0ubuntu27.3) ...
Setting up libsnmp-base (5.2.1.2-4ubuntu2.2) ...
Setting up linux-restricted-modules-common (2.6.15.12-51.1) ...

Setting up libgd2-noxpm (2.0.33-2ubuntu5.3) ...
Setting up locales (2.3.18.8) ...
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
Current default timezone: 'America/Vancouver'.
Local time is now:      Sat Jan 26 13:36:09 PST 2008.
Universal Time is now:  Sat Jan 26 21:36:09 UTC 2008.
Run 'tzconfig' if you wish to change it.

Setting up libsmbclient (3.0.22-1ubuntu3.6) ...
Setting up kmenuedit (3.5.2-0ubuntu27.3) ...

Setting up mysql-common (5.0.22-0ubuntu6.06.6) ...
Setting up ksmserver (3.5.2-0ubuntu27.3) ...

Setting up kappfinder (3.5.2-0ubuntu27.3) ...

Setting up libxml2-utils (2.6.24.dfsg-1ubuntu1.1) ...
Setting up libpt-plugins-v4l (1.10.0-1ubuntu1.1) ...
Setting up python2.4-libxml2 (2.6.24.dfsg-1ubuntu1.1) ...

Setting up kdeprint (3.5.2-0ubuntu27.3) ...

Setting up samba-common (3.0.22-1ubuntu3.6) ...

Setting up smbclient (3.0.22-1ubuntu3.6) ...
Setting up ksplash (3.5.2-0ubuntu27.3) ...

Setting up kfind (3.5.2-0ubuntu27.3) ...

Setting up opera (9.25-20071214.6dapper1) ...

Setting up kdesktop (3.5.2-0ubuntu27.3) ...

Setting up khelpcenter (3.5.2-0ubuntu27.3) ...

Setting up ksysguard (3.5.2-0ubuntu27.3) ...

Setting up kwin (3.5.2-0ubuntu27.3) ...

Setting up kdebase-kio-plugins (3.5.2-0ubuntu27.3) ...

Setting up konqueror-nsplugins (3.5.2-0ubuntu27.3) ...

Setting up python-libxml2 (2.6.24.dfsg-1ubuntu1.1) ...
Setting up ktip (3.5.2-0ubuntu27.3) ...

Setting up libcupsys2 (1.2.2-0ubuntu0.6.06.6) ...

Setting up openssh-client (4.2p1-7ubuntu3.2) ...

Setting up kicker (3.5.2-0ubuntu27.3) ...

Setting up libpt-plugins-v4l2 (1.10.0-1ubuntu1.1) ...
Setting up klipper (3.5.2-0ubuntu27.3) ...

Setting up libpt-plugins-alsa (1.10.0-1ubuntu1.1) ...
Setting up libcupsimage2 (1.2.2-0ubuntu0.6.06.6) ...

Setting up kdepasswd (3.5.2-0ubuntu27.3) ...

Setting up libmysqlclient15off (5.0.22-0ubuntu6.06.6) ...

Setting up libsnmp9 (5.2.1.2-4ubuntu2.2) ...

Setting up ssh-askpass-gnome (4.2p1-7ubuntu3.2) ...

Setting up cupsys-client (1.2.2-0ubuntu0.6.06.6) ...

Setting up kcontrol (3.5.2-0ubuntu27.3) ...

Setting up cupsys (1.2.2-0ubuntu0.6.06.6) ...
 * Starting Common Unix Printing System: cupsd                           [ ok ]

Setting up konqueror (3.5.2-0ubuntu27.3) ...

Setting up cupsys-bsd (1.2.2-0ubuntu0.6.06.6) ...

Setting up kdebase (3.5.2-0ubuntu27.3) ...

xxxxx@xxxxxxx-desktop:~$

Now, my user name and blinking cursor are waiting for a command
 what do I do?

Thank you for your assistance.
I appreciate all the postings and help given to others.

---

### Post by taurus on 2008-01-26
You can try

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by RebounD11 on 2008-01-26
Turn off Synaptic, Add/Remove or any other tool (like the update manager - only if it's doing sth at the moment). then it's safe to do what taurus said, without getting the error you got before.

---

### Post by chick penguin on 2008-01-26
> **taurus said:**
> You can try

```
sudo apt-get update
sudo apt-get upgrade
```

thanks,
I did that and got this reply:
what do I do now?

Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-security Release.gpg [191B]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:9 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:12 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release [5999B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Fetched 6200B in 5s (1178B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by chick penguin on 2008-01-26
almost finished...

I ran the 
sudo apt-get update
sudo apt-get upgrade commands

these are the last four lines in the out put:
what do I do now,
thank you.

Setting up libxfont1 (1.0.0-0ubuntu3.4) ...
Setting up linux-386 (2.6.15.51) ...
Setting up update-manager (0.42.2ubuntu22.2) ...

Setting up xserver-xorg-core (1.0.2-0ubuntu10.10) ...
xxxxxx@xxxxx-desktop:~$

---

### Post by taurus on 2008-01-26
> **chick penguin said:**
> almost finished...

I ran the 
sudo apt-get update
sudo apt-get upgrade commands

these are the last four lines in the out put:
what do I do now,
thank you.

Setting up libxfont1 (1.0.0-0ubuntu3.4) ...
Setting up linux-386 (2.6.15.51) ...
Setting up update-manager (0.42.2ubuntu22.2) ...

Setting up xserver-xorg-core (1.0.2-0ubuntu10.10) ...
xxxxxx@xxxxx-desktop:~$
Nothing else you can do except start using your machine and enjoying it.  What else do you expect to do?

---

### Post by chick penguin on 2008-01-26
> **taurus said:**
> Nothing else you can do except start using your machine and enjoying it.  What else do you expect to do?

I think I got the idea of this now,
what has works, with thanks,
is
on that last message I posted
I repeated the commands until the orange up date icon greyed out
I assumed that mean that I had all the updates and upgrades.

Success had arrived
then,
the orange update came on
I click and proceeded to update the lastest packages on the kernel
it is now in the final stages of being up to date.

I would like to thank you Taurus and RebounD11 for you help
Very much appreciated. I cannot see where I click the thank you button
or the RESOLVED buttton but it is Done Successfully.

Update is complete. I can close off.
merci beaucoup.

---

