---
title: "counter strike and linux"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by chrishere01 on 2007-09-10
how is this possible

i need help

im running wine .0.9.9


so yah

---

### Post by Maestro23 on 2007-09-10
> **chrishere01 said:**
> how is this possible

i need help

im running wine .0.9.9


so yah

Check the entries for Counterstike: [http://appdb.winehq.org/appbrowse.php?catId=16](http://appdb.winehq.org/appbrowse.php?catId=16)

---

### Post by Hellcom on 2007-09-10
Hi, you can play counter quite easily with wine, I do it myself. You said you have wine 0.9.9, which is interesting because there is no such thing yet. :P

 The latest wine release is 0.9.44.

You can get the latest wine from here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Here you can get instructions for running counter strike with wine:
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

---

### Post by Daveth on 2007-09-10
as well as

[http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)

---

### Post by chrishere01 on 2007-09-10
well hmm
is there a way to run just steam so i can get onto my cs files

---

### Post by Maestro23 on 2007-09-10
> **chrishere01 said:**
> well hmm
is there a way to run just steam so i can get onto my cs files

Section 4.1 of the link that Daveth provided you.

---

### Post by chrishere01 on 2007-09-10
> **Hellcom said:**
> Hi, you can play counter quite easily with wine, I do it myself. You said you have wine 0.9.9, which is interesting because there is no such thing yet. :P

 The latest wine release is 0.9.44.

You can get the latest wine from here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Here you can get instructions for running counter strike with wine:
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

well hmm im trying to get 1.6 and i currently have like 6.10 ubuntu

yah i cant get 7.04 unless theres a well to have the iso on a flash drive


but yah hmmm

---

### Post by chrishere01 on 2007-09-10
sooooo im in the terminal running wine
and im not sure where the steaminstall is
is there a way i can just use the current os to run this

---

### Post by chrishere01 on 2007-09-10
ubuntu@ubuntu:~$ wine msiexec /i SteamInstall.msi
fixme:msi:MsiInstallProductW L"SteamInstall.msi" (null)
err:msi:copy_package_to_temp failed to copy package to temp path L"C:\\windows\\temp\\MSI4ba.tmp"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002!

---

### Post by Daveth on 2007-09-10
where are you sourcing your SteamInstall.exe file from? You will probably have better success running the Wine command within the directory in which this .exe file sits.

Have you also checked out the section in

[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

the "install stuff" section.

---

### Post by chrishere01 on 2007-09-10
i think much of the problem is that ubuntu isnt installed on my hard drive

---

### Post by Maestro23 on 2007-09-10
> **chrishere01 said:**
> i think much of the problem is that ubuntu isnt installed on my hard drive

You running of the Live CD? Running Ubuntu off a flash drive?  That kind of info would have been helpful in your first post.

---

### Post by chrishere01 on 2007-09-10
ahaha
srry bout that

yah man im trying to partition it
and theres errors so i cant install it unless i get help...

---

### Post by dhughes on 2007-09-10
Isn't there some Linux LiveCD with games (ET, Counter-Strike) and WINE on it? I forget the name of the distribution, either it's hard to find or it's not real.

---

### Post by chrishere01 on 2007-09-10
not sure


god i hate vista
it did this to me

---

### Post by jordanmthomas on 2007-09-10
> **Hellcom said:**
> Hi, you can play counter quite easily with wine, I do it myself. You said you have wine 0.9.9, which is interesting because there is no such thing yet. :P

 The latest wine release is 0.9.44.

Just for the record, 0.9.9 is older than 0.9.44

---

### Post by chrishere01 on 2007-09-10
> **jordanmthomas said:**
> Just for the record, 0.9.9 is older than 0.9.44
oh the thing is i just did what it told me to...
thats what it got i guess

---

### Post by Daveth on 2007-09-11
well, you are not going to get anywhere with gaming whilst running the livecd- remember it loads and runs in ram, and we all know how intensive good games are. Sure, you can run a few things (I played a bit with Danger from the Deep in 64 bit live cd Sabayon recently), but if you are wanting to play CS under wine then you need to commit to an Ubuntu install.

Then follow the guides....

---

