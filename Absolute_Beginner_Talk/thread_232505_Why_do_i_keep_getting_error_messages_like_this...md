---
title: "Why do i keep getting error messages like this..??"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-08-08
```
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)

```

```
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

```


Almost everytime i try to run the **Add Programs** application...

And then sometimes ( or most of the time ) i can't install things because of these errors , Also some things **are still** "Blanked out" in the add programs manager...

I also get this message **"sometimes"** when i:

```
sudo apt-get update
```


Any idea's why...????

---

### Post by em3raldxiii on 2006-08-08
It looks like your repositories list is broken.  I am not a Linux guru, so I could be wrong.  Let me see if I can find a link for you to use (or you can search for links regarding repositories)

PS.  Why are you still using Breezy?  You might consider upgrading to Dapper (6.06 LTS).

---

### Post by skale on 2006-08-08
Here's my sources.list, if you want:
> # Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main



---

### Post by Zimmer on 2006-08-08
Simple answer is that apt cannot locate that particular repository mentioned in your sources file either because:
Your internet is not connected.
The server it is located on is unavailable.
or it is a location that does not exist......

Check out the forum for a link to a good sources file (not a Dapper one, you appear to be using Breezy..)
 etc/apt/sources.list   is the file you want

EDIT:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Ubuntu_Repositories_and_sources.list](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Ubuntu_Repositories_and_sources.list)

---

### Post by em3raldxiii on 2006-08-08
I think that the best process for you, though, is to do a complete upgrade.  Follow this link for the officially supported method of upgrading to the latest verison of Ubuntu:

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

Once that is complete, I highly recommend adding more components to your sources list.  You can do this either with Synaptic, or much more quickly by editing your sources.list directly.  I'll see if I can find a good thread on that subject.

---

### Post by em3raldxiii on 2006-08-08
Excellent page regarding sources.list (FOR DAPPER):

[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by jason.b.c on 2006-08-08
> **em3raldxiii said:**
> I think that the best process for you, though, is to do a complete upgrade.  Follow this link for the officially supported method of upgrading to the latest verison of Ubuntu:

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)


[QUOTE=em3raldxiii]PS. Why are you still using Breezy? You might consider upgrading to Dapper (6.06 LTS).[/QUOTE]

For what reason would i want to do that..???

I had dapper installed before and i couldn't stand it.!  It was completely unusable to me..It wouldn't stop putting my computer into suspend/hibernation....Here's the thread i started...
[http://www.ubuntuforums.org/showthread.php?t=207014]("http://www.ubuntuforums.org/showthread.php?t=207014")

[QUOTE=skale]Here's my sources.list, if you want:[/QUOTE]

Isn't that a dapper list..???   I'm running breezy , Where can i find one for that..??

---

### Post by jason.b.c on 2006-08-08
> **skale said:**
> Here's my sources.list, if you want:

How do i add that to my breezy system..??  , I mean , what are the terminal commands that i type..???

---

### Post by msak007 on 2006-08-08
Some people don't want the latest and greatest, or can't use the newest updates so the answer shouldn't always be "upgrade". 

Anyway, not sure if this list is still accurate but I use UbuntuGuide.org to get my sources.list. [Here's]("http://ubuntuguide.org/wiki/Breezy#How_to_add_extra_repositories") their list for Breezy. Try copying / pasting it into your sources.list and doing an update. If you're not sure how to update sources.list, do the following:

1. Open a terminal

2. Type 
```
cd /etc/apt/
``` 
3. Type
```
sudo cp sources.list sources.list_backup
``` to back up your original file before making any changes to it.

4. Finally, type
```
gksudo gedit sources.list
``` That should open gedit and you'll see your apt-get sources list. It could be some of the repos in your list are no longer up or supported, but I wouldn't know as I'm not sure how much longer after a new version is out repos are updated or maintained. Dapper is LTS, so I know that there'll be support there after Edgy is released but I'm not sure of the support for Breezy. Hope this helps!

---

### Post by jason.b.c on 2006-08-08
I get an error like this:

```
jason@Hp-Vectra-VL:~$ cd /etc/apt/
jason@Hp-Vectra-VL:/etc/apt$ gksudo gedit sources.list

(gedit:20249): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

I can paste the list and save it though.! , Do i still have a problem...???

---

### Post by jason.b.c on 2006-08-08
And after i:

```
sudo apt-get update
```

> jason@Hp-Vectra-VL:~$ cd /etc/apt/
jason@Hp-Vectra-VL:/etc/apt$ gksudo gedit sources.list

(gedit:20249): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
jason@Hp-Vectra-VL:/etc/apt$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) breezy Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) breezy Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [1223kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [3028kB]
99% [6 Sources gzip 0]                                              18.5kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Sub-process gzip returned an error code (1)
99% [7 Packages gzip 0]                                             18.5kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 7B in 7s (1B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
jason@Hp-Vectra-VL:/etc/apt$


---

### Post by msak007 on 2006-08-08
You can sometimes get an error like that when launching a graphical app using gksudo - it's normal. As far as updating your list, I'm not entirely sure it's been updated as that's not the same list I linked you to (I still see references to the Automatix repo in there). Once you open up your apt sources.list, highlight everything, delete it, copy / paste the list I linked you to, then save the file. Also try the following before you try updating again:

```
sudo apt-get autoclean
sudo apt-get clean
```

Finally, try to apt-get update again.

---

### Post by jason.b.c on 2006-08-09
[QUOTE=msak007]As far as updating your list, I'm not entirely sure it's been updated as that's not the same list I linked you to (I still see references to the Automatix repo in there). Once you open up your apt sources.list, highlight everything, delete it, copy / paste the list I linked you to, then save the file. Also try the following before you try updating again:
[/QUOTE]

Well i went and got it again and went through the whole source.list-delete-replace-update thing again...!

Is it correct now...???    I dunno , For some reason it still looks funny to me..!   And it still states that error stuff down at the bottom..

> jason@Hp-Vectra-VL:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
jason@Hp-Vectra-VL:~$ sudo gedit /etc/apt/sources.list

jason@Hp-Vectra-VL:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [46.9kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Get:5 [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages [550B]
Get:6 [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages [2343B]
Get:7 [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources [321B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:10 [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources [479B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release [30.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources [5185B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources [14B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources [10.2kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources [701B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [3028kB]
99% [17 Packages gzip 0] [15 Release 11369/30.9kB 36%]               4334B/s 4s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [1223kB]
99% [18 Sources gzip 0] [15 Release 20129/30.9kB 65%]                4334B/s 2s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Sub-process gzip returned an error code (1)
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages [585kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources [232kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages [39.7kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources [18.8kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages [767kB]
90% [27 Packages gzip 0]                                          3648B/s 2m40s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
  Sub-process gzip returned an error code (1)
Fetched 807kB in 12m37s (1066B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
jason@Hp-Vectra-VL:~$


So do i still have problems..???

---

### Post by jason.b.c on 2006-08-09
*Bump*

---

### Post by msak007 on 2006-08-09
Well if your list is up to date and you're still having problems, then it's most likely a problem with the server or your communication with certain servers. One suggestion I've seen in several threads for this specific problem is to try chaning the "http" in front of your sources to "ftp", then trying to update again. Also, I've never used it but it might be worth a shot to check out the [sources.list generator]("http://www.ubuntulinux.nl/source-o-matic") to see if you can generate an up-to-date sources.list and trying that one.

EDIT: Just out of curiosity, what happens if you click the links in your post for one of the servers / files you're having problems with (particularly Sources.gz)? I was able to get to the site using my browser, download the file, and open it. See if you can do the same.

---

### Post by davebgimp on 2006-08-09
Duplicate post...sorry. See below.

---

### Post by davebgimp on 2006-08-09
Here's a source list generator that will output a breezy list for you. 

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Once you have the list saved to your desktop, named sources.list, Open a terminal and type:

**sudo cp /etc/apt/sources.list /ect/apt/sources.list_backup**

then

**sudo mv /home/userfolder/Desktop/sources.list /etc/apt/sources.list**

Lastly, run

**sudo apt-get update**

---

