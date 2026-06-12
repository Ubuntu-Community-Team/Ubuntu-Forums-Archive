---
title: "repository indexes"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by matchstich on 2007-05-02
not sure about this. i clicked on reload on the synaptic package manager.

i got this.



The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

then a message comes up about dual lists.

thanks

---

### Post by starcraft.man on 2007-05-02
Ok this should be a simple fix, can you please post your whole sources list, seems like you have a few bad entries. We can trim em out easy. Also, tell us which version you are using, I don't see it selected on your profile.

To get your sources list, type into a terminal:

```
gksudo gedit /etc/apt/sources.list
```

Then just copy and paste it all in here with the code tags around em (The # button on the message panel).

---

### Post by matchstich on 2007-05-02
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


i also got this

(gedit:10469): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

thanks

ps: i have ubuntu 6.06 LTS , i guess that is dapper?

---

### Post by starcraft.man on 2007-05-02
Hmmmm, everything looks fine... except maybe for the fact you have 

```
# deb http://security.ubuntu.com/ubuntu dapper-security universe
```

Commented out, pretty sure you want that included in your repos. Ok, lets try this to fix your problem...

run in your terminal this command:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

Just making a backup before modifying, if you want to restore just type that back into terminal and reverse the locations so that list_backup is first and .list is second, the first denotes original and second where to copy too. (A useful command to remember.

Then, open up your list again with

```
gksudo gedit /etc/apt/sources.list
```

Select it all and delete, replace with this list:

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Push the save button, and close the text editor. Then run these two commands one after the other.

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
```

Then try again what you were doing, should be fine.

---

### Post by matchstich on 2007-05-02
(gedit:12768): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed
-desktop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg)  -O- | sudo apt-key add -
OK
desktop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [50.9kB]
Get:8 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages [2636B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
78% [7 Release 8509/50.9kB 16%] [Waiting for headers]bzip2: (stdin) is not a bzi p2 file.
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
  Sub-process bzip2 returned an error code (2)
Get:9 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages [2636B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
84% [9 Packages bzip2 0] [7 Release 20189/50.9kB 39%] [Waiting for headers] [Wab zip2: (stdin) is not a bzip2 file.
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [4082B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [7284B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources [771B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [38.4kB]
Get:14 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources [255kB]
Get:16 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release [7232B]
Get:17 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages [3327B]
Get:18 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages [1967B]
Get:19 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Sources [1133B]
Get:20 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Sources [887B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources [975kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [138kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages [22.4kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages [1805B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [49.5kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources [3676B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources [733B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14.5kB]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [47.8kB]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [10.6kB]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [4706B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [12.4kB]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [2631B]
Fetched 1704kB in 30s (56.3kB/s)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main) /binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main) /binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/unive rse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-securit y_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.
desktop:~$


this what i got

---

### Post by starcraft.man on 2007-05-02
Hmmm, I guess the cannonical servers for dapper are down... kinda odd, I don't think it needs a GPG key so I guess you should just try again later >.>.

Unless someone else knows why the cannonical not working?

---

### Post by matchstich on 2007-05-02
ok, i will try again in the morning,
thanks

---

### Post by starcraft.man on 2007-05-02
> **matchstich said:**
> ok, i will try again in the morning,
thanks

Ok then, hope it works then. If not post here again to bump it and someone should be able to further help >.>

---

### Post by la3875 on 2007-05-03
I'm having the same problem in Dapper. I broke my previous install trying to upgrade to Edgy. I installed 6.06.1 and when it came up, the update manageer tells me there are 29 updates, but no joy. This has been over four hours tonight. Are the servers down? Is the script for the repos old? This is bumming me out because I have been a believer in this OS for many months now and am at the threshold of fully commiting to it.

Any help is appreciated!:confused:

---

### Post by LaurelLynn on 2007-05-03
I would try it with that last line commented out for the moment (put a "#" in front of it).

The software your trying to download might be available from one of the other repositories listed.

You can always add it back latter if the server becomes available.

---

### Post by matchstich on 2007-05-03
i tried again and still getting the error about canonical servers being down

and i get this

W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_main_binary-i386_Packages)

not sure how to fix it,
 thanks

---

