---
title: "Can't Upgrade to Dapper!"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by CybaCowboy on 2006-06-02
I followed the instructions on [this page]("https://wiki.ubuntu.com/DapperUpgrades"), but it's not working!


Here's what I did...

[i]cowboy@ubuntu:~$ gksudo gedit /etc/apt/sources.list

(gedit:9976): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/i]

This then opens up a blank document in gedit.


I then close this without saving and type:
[i]cowboy@ubuntu:~$ sudo apt-get update && sudo apt-get dist-upgrade
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [62.8kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [17.7kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Fetched 113kB in 15s (7353B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/i]


So as you can see, it's refusing to upgrade!

---

### Post by Patrick-Ruff on 2006-06-02
clean install really is the best way to upgrade, no software conflicts and all that bs. it would take you less time to upgrade to dapper via clean install, then to go through this. backup all your stuff and do a clean install, it'll be worth it.

---

### Post by Rackerz on 2006-06-02
You need to change your sources.list to Dappers.

Or you could just run sudo update-manager -d and see if it tells you there is 6.06 LTS to upgrade too.

---

### Post by CybaCowboy on 2006-06-02
[QUOTE=Patrick-Ruff]clean install really is the best way to upgrade, no software conflicts and all that bs. it would take you less time to upgrade to dapper via clean install, then to go through this. backup all your stuff and do a clean install, it'll be worth it.[/QUOTE]

I'm gonna do a clean install in a month or so, when I have Dapper on CD (I'll be clean installing XP too)...

I wanna do it all in one hit.


[QUOTE=Rackerz]Or you could just run sudo update-manager -d and see if it tells you there is 6.06 LTS to upgrade too.[/QUOTE]

That worked!

It didn't before (:-k ), but it did this time...


Thanks!:mrgreen:

---

### Post by Rackerz on 2006-06-02
No problem ;).

---

### Post by CybaCowboy on 2006-06-02
How big *is* Dapper?

I've been downloading it for at *least* two hours now (with a broadband internet connection I might add!) and my computer *still* says 19 hours!

---

### Post by CybaCowboy on 2006-06-02
Ten-ish hours still!


So does anyone know exactly how big Dapper is?

---

### Post by ash211 on 2006-06-02
It depends on how recently you last updated.  If I remember correctly, mine was around 500MB, though that could be off.  Does update manager tell you the download speed?  Is that about what you normally get?  (I'm not sure, because I use Kubuntu, not Ubuntu, and they're a bit different).

---

### Post by catlett on 2006-06-02
It's not very big (the install of ubuntu will always fit on one cd which limits it to 700mb) It definately is a download issue. Either your service is having issues or the Dapper servers are loaded and there isn't much bandwidth for you.

---

### Post by bobpur on 2006-06-02
I downloaded Dapper in about 2.5 hrs on DSL. It was about 698 mbs. It has something to do with about a gazillion people all trying to download at the same time and taxing the servers.
WOW! 19 hrs, 10 hrs! Download speeds ought to improve as demand decreases.

---

### Post by CybaCowboy on 2006-06-02
[QUOTE=ash211]It depends on how recently you last updated.[/QUOTE]

I updated immediately prior to downloading Dapper Drake...


[QUOTE=ash211]If I remember correctly, mine was around 500MB, though that could be off.[/QUOTE]

I have quite a lot of hardware - multiple drives, PCI cards coming out my ears, etc...

Do you think that could be contributing to such a large download?


[QUOTE=ash211]It depends on how recently you last updated.  If I remember correctly, mine was around 500MB, though that could be off.  Does update manager tell you the download speed?[/QUOTE]

Update Manager says:
*Downloading file 815 of 1185 at 8527/s*

Of course, "file xxx" obviously changes as the download progresses...

[QUOTE=ash211]Does update manager tell you the download speed?  Is that about what you normally get?[/QUOTE]

Actually, I don't *know* what my broabdband speed is!

My computer illiterate mother pays the bill, so I can only guess at what the speed is...

256k or 512k are my guesses, from experience.

---

### Post by truenemesis on 2006-06-03
I get this error. can someone help me! I wanna upgrade soo badly!


Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/dapper/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/dapper/Packages.gz)  404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/dapper/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/dapper/Sources.gz)  404 Not Found

---

### Post by ash211 on 2006-06-03
[QUOTE=truenemesis]I get this error. can someone help me! I wanna upgrade soo badly!

Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/dapper/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/dapper/Packages.gz)  404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/dapper/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/dapper/Sources.gz)  404 Not Found[/QUOTE]


The problem is that some of the servers in your /etc/apt/sources.list file aren't working correctly.  Run in the terminal ```
sudo nano /etc/apt/sources.list
```  Comment out (put a '#' sign at the beginning of the line) those koti.mbnet.fi lines.  Ctrl-O saves the file, and Ctrl-X exits nano.  If you then update normally, you'll be on your way to running Dapper!

---

### Post by ash211 on 2006-06-03
[QUOTE=CybaCowboy]I updated immediately prior to downloading Dapper Drake...[/QUOTE]

That should make the download less.

[QUOTE=CybaCowboy]I have quite a lot of hardware - multiple drives, PCI cards coming out my ears, etc...

Do you think that could be contributing to such a large download?
[/QUOTE]
Probably not, but it could be.

[QUOTE=CybaCowboy]Update Manager says:
*Downloading file 815 of 1185 at 8527/s*

Of course, "file xxx" obviously changes as the download progresses...
[/QUOTE]
The problem here is that your download speed is WAY too slow.  8000/s is about 8KB/s, which is closer to dial-up speed.  My DSL can get around 150KB/s, and cable/fiber goes even faster.  If your download hasn't finished yet, here's one way you could get it to go faster:

Change your sources list to download from a different mirror.  Stop the update first (don't worry, apt-get won't lose your download progress!)  
Run ```
sudo nano /etc/apt/sources.list
``` then look for the URLs with ubuntu.com in them.  If they don't have a two letter country code in front of them (like archive.ubuntu.com instead of us.archive.ubuntu.com) then consider putting the 'us' in front (or gb if you're in Great Britain, nz if you're in New Zealand, etc).  If you already have the us (or another country code), remove it.  Do this for all the lines, and then run ```
sudo apt-get update
``` and start updating again.  Hopefully your download speeds will be faster :D !

---

### Post by painterboy on 2006-06-03
[QUOTE=ash211]The problem is that some of the servers in your /etc/apt/sources.list file aren't working correctly.  Run in the terminal ```
sudo nano /etc/apt/sources.list
```  Comment out (put a '#' sign at the beginning of the line) those koti.mbnet.fi lines.  Ctrl-O saves the file, and Ctrl-X exits nano.  If you then update normally, you'll be on your way to running Dapper![/QUOTE]
alternatively you should be able to use synaptic and edit your repositories thru there synaptic>settings>repositories then remove the checkmark from in front of those repos.  then close synaptic

---

