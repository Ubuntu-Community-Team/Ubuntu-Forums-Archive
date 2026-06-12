---
title: "How to backup dvds and cds"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by paogeorge13 on 2006-10-16
Hi my friends! :) 
Besides I've been using ubuntu for over 6 months this is my first post here in ubuntuforums. I have a problem that I can't solve. I'd like to make a backup of a dvd and of a cd but I can't. I need a programm like clone cd or clone dvd or dvd shrink, but I can't find it anywhere. I am using Ubuntu Dapper Drake 6.06. I'd appreciate any help.
Thanks in advance. ;)

---

### Post by deeptingler on 2006-10-16
have a look in the repositories for k9copy and DeVeDe - they are the programs that I use - DeVeDe is good for getting video files onto DVD disc

---

### Post by xyz on 2006-10-16
For more infos:
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)
K9copy and dvdrip, etc... can also be found via Synaptic.

---

### Post by paogeorge13 on 2006-10-16
I tried the first one k9copy. I tried to follow [these]("http://www.ubuntuforums.org/showpost.php?p=1098581&postcount=12")
but....
paogeorge13@paogeorge-desktop:~$ tar xvfz k9copy-1.0.4-2.tar.gz
tar: k9copy-1.0.4-2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
paogeorge13@paogeorge-desktop:~$

I've downloaded the programm.



Is this programm for cd backup too?

---

### Post by paogeorge13 on 2006-10-16
In DVD Decrypter says that no devices detected! I only downloaded the programm and run it with wine. Please help :( 

This is the terminal
paogeorge13@paogeorge-desktop:~$ sudo apt-get update
Password:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://theli.free.fr](http://theli.free.fr) dapper Release.gpg
Get:3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://theli.free.fr](http://theli.free.fr) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 62B in 2s (29B/s)
Reading package lists... Done
paogeorge13@paogeorge-desktop:~$  sudo apt-get install wine winesetuptk
Reading package lists... Done
Building dependency tree... Done
wine is already the newest version.
Package winesetuptk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  wine
E: Package winesetuptk has no installation candidate

Thanks for your help.

---

### Post by paogeorge13 on 2006-10-16
Does anyone know a programm to make backup of DVDs AND CDs? If yes could he give me instructions step by step because I don't know anything in Linux. Thxs in advance.

---

### Post by xyz on 2006-10-16
Well nothing is really "easy" at first no matter what you do...so here are step-by-step instruction to "K9Copy is a small utility which allows the user to copy DVDs in Linux." 
I don't know how really NEW to Linux you are, so report back if you don't get the steps...or learn a bit about Linux first! Just a thought!

Ooops! Forgot to link to it:
[https://help.ubuntu.com/community/K9Copy](https://help.ubuntu.com/community/K9Copy)

---

### Post by paogeorge13 on 2006-10-16
Thank you very much! It's easy. Is this programm and for cd backups? If not do you know any other programm for cd backups. 

I don't know anything about Linux. 
Thx again. :D

---

### Post by xyz on 2006-10-16
*Several ways to do it* but the simple way can be:
Go to  Applications > Sound & Video and there you should see "Sound Juicer CD Extractor" and "Serpentine Audio CD Creator".

If not, you can download them in System > Administration > Synaptic and Search for them.

If I understood correctly what you meant by "easy", this should do the trick.

---

### Post by paogeorge13 on 2006-10-16
Ok....
This is for a music cd backup. And if it is a program? or a game? how I could do a backup? Thanks.

---

### Post by xyz on 2006-10-16
Don't know a thing about games!
But do you mean to create a **data CD backup,** I assume?

---

### Post by xyz on 2006-10-16
To back up/burn data and what not, I use "k3b"...again you can choose another:

Either go System > Administration > Synaptic Pacakge Manager > Search : k3b

OR in a terminal, type this:

```
sudo aptitude install k3b
```

K3b will then show in Application > Sound & Video > k3b

You'll need multiverse/universe repositories. Ask if you don't know.
Good luck.

---

### Post by paogeorge13 on 2006-10-16
Yes I have K3b. I have a game and it has many gazes. I want to make a backup of it. The game is original and I gave a lot of money to buy it. That's all. Thanks for your answers.

---

### Post by xyz on 2006-10-17
As I said, I'm no gamer but would backing up a game be the same as backing up data?

And another question: even if the game was legally bought, wouldn't the manufacturer have somehow made it very difficult for anyone to copy/backup the game ....that would mean it could be sold?

Thanks for reading.

---

### Post by paogeorge13 on 2006-10-17
When I had windows I had a program called Clone CD. With this programm I could copy EVERYTHING. Now I am trying to find a programm like that. Thxs for your answer. ;)

---

### Post by xyz on 2006-10-18
Well I found this...they say it *may* work:
[http://linuxreviews.org/howtos/cdrecording/#toc16](http://linuxreviews.org/howtos/cdrecording/#toc16)

and:
[http://translate.google.com/translate?hl=en&sl=de&u=http://schimana.net/2005/08/10/clonecd-unter-linux/](http://translate.google.com/translate?hl=en&sl=de&u=http://schimana.net/2005/08/10/clonecd-unter-linux/)

a Google-translated from German page. I didn't quite get it...maybe you can make better sense of it.
Let me know.

---

### Post by paogeorge13 on 2006-10-18
Thx for your help. I'll try to do that. :)

---

### Post by xyz on 2006-10-19
I'm not 'tops' on copying CDs but wouldn't this do it?

> Functionalities

* NeroLINUX is able to burn the following formats
* Data CDs/DVDs (ISO9660, UDF and UDF/ISO9660 Bridge)
* Bootable CDs/DVDs using the El-Torito standard
* Audio CDs (CD TEXT Infos can be added)
* Mix Mode CDs
* Enhanced CDs (CD EXTRA)
* CD and DVD Images (ISO, NRG and Cue Sheets)
* Ability to burn Multisession CD/DVD
* Double Layer DVDs
*** Copy CD or DVD as under Windows**
* Image Recorder is available
* Digital Audio Extraction for audio tracks

[NeroLinux]("http://www.gnomefiles.org/app.php/NeroLin")

---

### Post by mking213 on 2006-10-19
mkisofs --help

---

### Post by scrook on 2006-10-19
I don't know if this will work for game CD roms which have copy protection that you'd need to crack but for plain jane audio CDs or data CDs if you are using the gnome desktop you can right click on the icon of the cd you want to copy on the desktop and hit 'copy disc'.

---

