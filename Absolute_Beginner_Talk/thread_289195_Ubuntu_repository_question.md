---
title: "Ubuntu repository question"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by paul6 on 2006-10-30
Do the Dapper repositories keep getting upgraded with new versions? Or do I have to upgrade to Edgy for further updates?

---

### Post by raqball on 2006-10-30
Dapper is LTS and will be supported for 3 years :)

You will not get update to edgy but you will get security updates! :)

---

### Post by paul6 on 2006-10-30
So if I want Firefox 2.0 through apt-get, for example, I'll have to upgrade to Edgy, right? Will the Dapper repository be stuck with version 1.5.0.7 forever?

---

### Post by raqball on 2006-10-30
No you can inatall ff2 by itself if you want.

Check out this link :)

[http://www.ubuntuforums.org/showthread.php?t=283965&highlight=firefox+2+on+dapper](http://www.ubuntuforums.org/showthread.php?t=283965&highlight=firefox+2+on+dapper)

---

### Post by PriceChild on 2006-10-30
You don't have to go to edgy to get firefox 2.

You could build it yourself, or follow instructions on the forum. Just do a quick search for "howto latest firefox" and i'm sure you'll be on your way.

EDIT or use the link above that someone found you.

---

### Post by Sef on 2006-10-30
> Dapper is LTS and will be supported for 3 years

The desktop is supported for 3 years; the server is supported for 5 years.

---

### Post by Roobert on 2006-11-01
I just did a fresh 'sudo apt-get update', and I get errors for every single default Dapper repository. This is a fresh install of Dapper as well. Can someone verify that the Dapper repos are updating properly?

~ Roobert.

---

### Post by dbott67 on 2006-11-01
Can you post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by dbott67 on 2006-11-01
There is also a sources.list generatot here:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

This can be used to generate a new sources.list in the event that yours gets messedd up.  The other consideration is that there are local mirrors for many countries/regions that can be utilized if you're having problems with your own.  For example, you can change the 'ca' to 'us' in your sources.list to access the US mirrors (or whatever country you want).

-Dave

---

### Post by Roobert on 2006-11-01
> **dbott67 said:**
> Can you post the output of:
```
cat /etc/apt/sources.list
```

Sure thing!

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

I haven't added any third-party repo sites; this is the plain Jane version that ships from the official Ubuntu Dapper install CD from ShipIt.

~ Roobert.

---

### Post by bluenova on 2006-11-01
You have backports in the source list so you will still get updates to software.

p.s. source list looks fine, perhaps you are using a router?

---

### Post by Roobert on 2006-11-01
> **dbott67 said:**
> There is also a sources.list generatot here:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

This can be used to generate a new sources.list in the event that yours gets messedd up.  The other consideration is that there are local mirrors for many countries/regions that can be utilized if you're having problems with your own.  For example, you can change the 'ca' to 'us' in your sources.list to access the US mirrors (or whatever country you want).

-Dave

Thanks, Dave. I had originally tried the Canada sites, but got http errors on all of them; consequently, I switched to the plain old "archive.ubuntu.com sites instead with the same error. I'll try the U.S. ones, but I'd like some other Dapper user to confirm this problem just to make sure it's reproducable.

~ Roobert.

---

### Post by Roobert on 2006-11-01
> **bluenova said:**
> You have backports in the source list so you will still get updates to software.

p.s. source list looks fine, perhaps you are using a router?

I've never had a problem updating packages from Breezy, or Dapper before. I don't know why this isn't working. Maybe the authentication keys have changed? I notice that the default ones on the installation CD are 2 years old now.

---

### Post by Bartender on 2006-11-01
u.s. servers very unresponsive this morning and yesterday.  Tried at a afriend's house on his DSL modem and again at my own house a few minutes ago on dial-up.  Don't know what's going on.

---

### Post by Roobert on 2006-11-01
> **Bartender said:**
> u.s. servers very unresponsive this morning and yesterday.  Tried at a afriend's house on his DSL modem and again at my own house a few minutes ago on dial-up.  Don't know what's going on.

*Thank you* for the feedback. It's not just the U.S. repos, it's the same for Canada and the generic "archive.ubuntu.com" sites as well. Here's the output of "sudo apt-get update" for those who are curious:

```
$ sudo apt-get update
Err http://archive.ubuntu.com dapper Release.gpg
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://security.ubuntu.com dapper-security Release.gpg
  The HTTP server sent an invalid reply header
Ign http://security.ubuntu.com dapper-security Release
Err http://archive.ubuntu.com dapper-updates Release.gpg
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports Release.gpg
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Ign http://archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper-backports Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://security.ubuntu.com dapper-security/multiverse Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com dapper-security/multiverse Sources
Ign http://archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/main Packages
  The HTTP server sent an invalid reply header
Err http://security.ubuntu.com dapper-security/restricted Packages
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/main Sources
  The HTTP server sent an invalid reply header
Err http://security.ubuntu.com dapper-security/restricted Sources
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper/multiverse Packages
Ign http://archive.ubuntu.com dapper/universe Sources
Err http://security.ubuntu.com dapper-security/universe Packages
  The HTTP server sent an invalid reply header
Err http://security.ubuntu.com dapper-security/multiverse Packages
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper/multiverse Sources
Err http://security.ubuntu.com dapper-security/universe Sources
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper-updates/main Packages
Err http://security.ubuntu.com dapper-security/multiverse Sources
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://archive.ubuntu.com dapper-updates/main Sources
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/main Packages
Ign http://archive.ubuntu.com dapper-backports/restricted Packages
Ign http://archive.ubuntu.com dapper-backports/universe Packages
Ign http://archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://archive.ubuntu.com dapper-backports/main Sources
Ign http://archive.ubuntu.com dapper-backports/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/universe Sources
Ign http://archive.ubuntu.com dapper-backports/multiverse Sources
Err http://archive.ubuntu.com dapper/main Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper/main Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper/universe Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/multiverse Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper/universe Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/multiverse Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/main Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports/restricted Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/universe Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/main Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports/restricted Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/universe Sources
  Connection failed [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg The HTTP server sent an invalid reply header [IP: 85.133.25 .23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg The HTTP server sent an invalid reply header [IP: 1 95.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg The HTTP server sent an invalid reply header [IP:  85.133.25.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg The HTTP server sent an invalid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz The HTTP server sent an invalid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz The HTTP server sent an in valid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz The HTTP server sent an invalid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz The HTTP server sent an invalid reply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz The HTTP server sent an invalid reply head er [IP: 85.133.25.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz The HTTP server sent an inva lid reply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz The HTTP server sent an invalid repl y header [IP: 195.248.90.54 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz The HTTP server sent an in valid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz The HTTP server sent an invalid re ply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz The HTTP server sent an invalid reply header [IP : 85.133.25.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz The HTTP server sent an invalid reply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz The HTTP server sent an invalid reply head er [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz The HTTP server sent an invalid repl y header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz The HTTP server sent an invalid reply header  [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz The HTTP server sent an invalid reply head er [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz The HTTP server sent an invalid re ply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz The HTTP server sent an inva lid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz The HTTP server sent an invalid reply he ader [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz The HTTP server sent an invalid re ply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz The HTTP server sent an in valid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz The HTTP server sent an inva lid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz The HTTP server sent an in valid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz Connection failed [IP: 85.133.25.2 3 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Could we get a comment from Ubuntu staff whether they're aware of any problems?

---

### Post by PriceChild on 2006-11-01
EDIT Just realised the firewall of the network i'm on blocks ping requests so ignore anything you may have seen here that isn't here now...

I haven't seen your error before Roobert... scary stuff.

I think the majority is all to do with not being able to retrieve the Release.gpg files to start with... but not quite sure why you can't have them to begin with.

---

### Post by Roobert on 2006-11-01
EDIT:
Oh....so...does this mean that my problem could still be unconfirmed?

---

### Post by dbott67 on 2006-11-01
I just SSH'd into my home computer & got this:
```
dbott@thedrake:~$ sudo apt-get update
Password:
Get:1 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release
Hit http://www.getautomatix.com dapper/main Packages
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Get:4 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:5 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:6 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/restricted Sources
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/universe Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 6B in 1s (4B/s)
Reading package lists... Done
dbott@thedrake:~$
```

My sources.list:
```
dbott@thedrake:~$ cat /etc/apt/sources.list
## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
# deb http://archive.ubuntu.com/ubuntu dapper-backports main
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

# deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# deb http://archive.ubuntu.com/ubuntu dapper-backports universe
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

# deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb http://www.getautomatix.com/apt dapper main

## created by automatixrepo3

# deb http://www.beerorkid.com/compiz dapper main aiglx
# deb http://media.blutkind.org/xgl/ dapper main aiglx
```

-Dave

---

### Post by Bartender on 2006-11-01
Hi, Dave and thanks for some data.  If a person's running Dapper would it be worth a try to just copy/paste your sources.list?  I'm not up-to-speed on this stuff.  My guess is I'd want to save my current sources.list anyplace convenient - desktop, home folder, whatever - then wipe the sources.list clean, paste yours in (minus your login on top of course), save it, and see what happens?  Do you have to reboot?
If someone living on the Pacific side of the U.S. wipes all references to u.s. servers and plugs in yours, how far away am I actually going for data?  My dial-up connection is already pathetically slow!

---

### Post by Roobert on 2006-11-01
Oh, man. That's not good - that means the problem is on my end. I have no problems with internet connectivity; how else can I test my connection to the repository sites?

](*,)

---

### Post by Roobert on 2006-11-01
I just tried Dave's sources.list with the same errors. So it must be my firewall at work causing these problems. But I never had a problem before updating through Synpatic. It could be where this is a fresh Dapper install my configuration is not set up properly. Can anyone suggest how to troubleshoot this?

---

### Post by dbott67 on 2006-11-01
> **Bartender said:**
> Hi, Dave and thanks for some data.  If a person's running Dapper would it be worth a try to just copy/paste your sources.list?  I'm not up-to-speed on this stuff.  My guess is I'd want to save my current sources.list anyplace convenient - desktop, home folder, whatever - then wipe the sources.list clean, paste yours in (minus your login on top of course), save it, and see what happens?  Do you have to reboot?
If someone living on the Pacific side of the U.S. wipes all references to u.s. servers and plugs in yours, how far away am I actually going for data?  My dial-up connection is already pathetically slow!

Yes... it's fine to use someone else's sources.list file.  The only caveat is to make sure that the other sources.list file does not have any non-standard repos (like mine).  I've got the Automatix repos in there (**deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main**) plus some commented out repos for Beryl & XGL at the bottom.  You would want to remove or comment out the last few lines:
```
 [COLOR="Red"]**--- delete everything from here down or put a '#' in front of each line that does not have one ---**[/COLOR]

##############################
### Automatix Repositories ###
##############################

deb http://www.getautomatix.com/apt dapper main

## created by automatixrepo3

# deb http://www.beerorkid.com/compiz dapper main aiglx
# deb http://media.blutkind.org/xgl/ dapper main aiglx
```

And, yes, backing up your original is always a good practice:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

No re-boot required, just a **sudo apt-get update** and you're good to go.  If things go awry, just type the following 2 commands:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.daves-crappy-list  [COLOR="Red"]<--- moves current list[/COLOR] 
```
```
sudo mv /etc/apt/sources.list.bak /etc/apt/sources.list  [COLOR="Red"]<--- restores original[/COLOR]
```

-Dave

---

### Post by ajackson on 2006-11-01
Try browsing using firefox (or whatever) to [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
if it doesn't load up then the firewall is blocking access to that site. If it is your employers firewall you need to have a word with one of the techies/admin people to see if they can verify it and possibly unblock it.

---

### Post by dbott67 on 2006-11-01
A couple of questions (just taking a few guesses here):

1. Did it work before from this location?

2. Does your employer use a proxy server?  For Windows, open Internet Explorer, click TOOLS > OPTIONS > click on CONNECTIONS TAB > click LAN SETTINGS button.  If there is a Proxy server set, make note of the ADDRESS & PORT.  You would need to enter these same settings in Synaptic.  Open Synaptic, click on SETTINGS > PREFERENCES and then click on the NETWORK tab.  Enter the same settings from above.

-Dave

---

### Post by bluenova on 2006-11-01
If you're using a hardware firewall/router then:

remove your router from your /etc/resolv.conf
usually it's:
nameserver 192.168.0.1 (or the x.x.x.1 of your IP address)

hopefully your 2nd nameserver line is from your ISP.. leave that alone..
save and close your /etc/resolve.conf

and retry apt-get update.

---

### Post by dbott67 on 2006-11-01
I've also tried updating on one of my Ubuntu servers here at work and all is well (using the 'ca' repos).

**_Dapper [COLOR="Red"]sources.list[/COLOR] file for Canada_**
```

# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## GAdminTools from Backports
# deb http://www.backports.org/debian/ sarge-backports main contrib non-free
```

Perhaps a re-boot is in order?

Let us know what happens.

---

### Post by Roobert on 2006-11-01
> **ajackson said:**
> Try browsing using firefox (or whatever) to [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
if it doesn't load up then the firewall is blocking access to that site. If it is your employers firewall you need to have a word with one of the techies/admin people to see if they can verify it and possibly unblock it.

I can connect to archive.ubuntu.com through Firefox. So that is at least fine.

---

### Post by dbott67 on 2006-11-01
One other thing to try.  Perhaps it's related to IPv6.  I've been doing a little searching about folks having issues with Synaptic and IPv6 seems to rear it's ugly head every once-in-a-while.

**_To Disable IPv6:_**

Create fie named **bad_list** in **/etc/modprobe.d** containing this line **alias net-pf-10 off**:
```
gksudo gedit /etc/modprobe.d/bad_list
```
```
alias net-pf-10 off
```

Reboot.

To 'undo' this hack, **sudo rm /etc/modprobe.d/bad_list**.

Read [this thread]("http://www.ubuntuforums.org/showthread.php?p=477326#post477326") for some enlightening discussions about disabling IPv6 (pros & cons).

-Dave

---

### Post by Roobert on 2006-11-01
> **dbott67 said:**
> A couple of questions (just taking a few guesses here):

1. Did it work before from this location?

2. Does your employer use a proxy server?  For Windows, open Internet Explorer, click TOOLS > OPTIONS > click on CONNECTIONS TAB > click LAN SETTINGS button.  If there is a Proxy server set, make note of the ADDRESS & PORT.  You would need to enter these same settings in Synaptic.  Open Synaptic, click on SETTINGS > PREFERENCES and then click on the NETWORK tab.  Enter the same settings from above.

-Dave

Answers:

1. Yes, it worked from this machine before. I had at one point in time, Breezy, Dapper, and until yesterday, Edgy (let's not go there) installed. Never any connectivity problems with Synaptic.

2. *Nothing* is in Internet Explorer  TOOLS > OPTIONS > CONNECTIONS TAB > LAN SETTINGS; no address or port; all fields are blank.

Here's what's really weird - I rebooted as you said, and was able to connect with about 80% of the standard repository sites. I installed a few packages, like the xubuntu desktop, xfce and friends. After another reboot, I was completely locked out from the repositories again! ](*,)

---

### Post by Roobert on 2006-11-01
> **dbott67 said:**
> One other thing to try.  Perhaps it's related to IPv6.  I've been doing a little searching about folks having issues with Synaptic and IPv6 seems to rear it's ugly head every once-in-a-while.

**_To Disable IPv6:_**

Create fie named **bad_list** in **/etc/modprobe.d** containing this line **alias net-pf-10 off**:
```
gksudo gedit /etc/modprobe.d/bad_list
```
```
alias net-pf-10 off
```

Reboot.

To 'undo' this hack, **sudo rm /etc/modprobe.d/bad_list**.

Read [this thread]("http://www.ubuntuforums.org/showthread.php?p=477326#post477326") for some enlightening discussions about disabling IPv6 (pros & cons).

-Dave

Thanks for the patience and ideas. I copied your above code into /etc/modprobe.d/bad_list, but it doesn't seem to have had any effect. I'm still locked out of the repos.

---

### Post by dbott67 on 2006-11-01
This is weird.  

1. A few of those threads made reference to the problem happening after the installation of a particular package (one I noticed was Gimp).

2. Another thread indicates an issue with the firewall: [http://www.ubuntuforums.org/showthread.php?t=233116&highlight=apt+problems](http://www.ubuntuforums.org/showthread.php?t=233116&highlight=apt+problems).  Do you know what type of firewall you run at work?  Are the the sys admin or do you have access to the firewall (or will a large double-double from Tim Hortons get him to help you)?

3. It could also be an issue with name resolution.  Can you post the output of the following:
```
/etc/resolv.conf
```
```
ifconfig
```
```
route
```

If your work uses a DSL/Cable NAT router (such as D-Link, Linksys or Netgear) you could try changing the DNS servers from your ISP to the ones at OpenDNS ([http://www.opendns.com/)](http://www.opendns.com/)).

-Dave

---

### Post by dbott67 on 2006-11-01
Just a few more pieces of info to help determine if it's a DNS issue.

What is the output of **ping archive.ubuntu.com**?
```
dbott@thedrake:/etc$ ping archive.ubuntu.com
PING archive.ubuntu.com (**85.133.25.54**) 56(84) bytes of data.
64 bytes from 85.133.25.54: icmp_seq=1 ttl=52 time=115 ms
64 bytes from 85.133.25.54: icmp_seq=3 ttl=52 time=115 ms
64 bytes from 85.133.25.54: icmp_seq=5 ttl=52 time=114 ms
64 bytes from 85.133.25.54: icmp_seq=6 ttl=52 time=115 ms
```

If the IP address is different for you, it could be DNS (or that Ubuntu has load-balanced servers...)

---

### Post by Roobert on 2006-11-01
> **dbott67 said:**
> This is weird.  

1. A few of those threads made reference to the problem happening after the installation of a particular package (one I noticed was Gimp).

2. Another thread indicates an issue with the firewall: [http://www.ubuntuforums.org/showthread.php?t=233116&highlight=apt+problems](http://www.ubuntuforums.org/showthread.php?t=233116&highlight=apt+problems).  Do you know what type of firewall you run at work?  Are the the sys admin or do you have access to the firewall (or will a large double-double from Tim Hortons get him to help you)?

3. It could also be an issue with name resolution.  Can you post the output of the following:
```
/etc/resolv.conf
```
```
ifconfig
```
```
route
```

Alright, here goes:

```
$ more /etc/resolv.conf
search gsca.nrcan.gc.ca
nameserver 192.55.224.20
nameserver 192.55.224.12
```
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:1B:C1:8F
          inet addr:192.55.227.152  Bcast:192.55.239.255  Mask:255.255.240.0
          inet6 addr: fe80::211:43ff:fe1b:c18f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3691935 (3.5 MiB)  TX bytes:549336 (536.4 KiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
```

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.55.224.0    *               255.255.240.0   U     0      0        0 eth0
default         ott-gw.gsca.NRC 0.0.0.0         UG    0      0        0 eth0
```

Thanks!

---

### Post by dbott67 on 2006-11-01
A little more investigation turns up that Ubuntu has 2 'archive' servers: 85.133.25.**54** & 85.133.25.**23**.

From one of your earlier posts, it appears as though you're using .23, whereas I am using .54

```
dbott@thedrake:/$ nslookup archive.ubuntu.com 192.168.1.1
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   archive.ubuntu.com
Address: 85.133.25.23
Name:   archive.ubuntu.com
Address: 85.133.25.54
```

```
archive.ubuntu.com.	A	IN	600	85.133.25.54
archive.ubuntu.com.	A	IN	600	85.133.25.23
ubuntu.com.	NS	IN	10800	ns1.blackcatnetworks.co.uk.
ubuntu.com.	NS	IN	10800	ns.ubuntu.com.
ubuntu.com.	NS	IN	10800	ns0.blackcatnetworks.co.uk.
ns.ubuntu.com.	A	IN	600	82.211.81.173
ns0.blackcatnetworks.co.uk.	A	IN	86400	193.201.200.34
ns1.blackcatnetworks.co.uk.	A	IN	86400	69.55.225.40
```

I don't know if this has anything to do with the price of tea in China, but perhaps one of the servers is down.  You could edit your '/etc/hosts' file and create an entry in the file:
```
83.133.255.54  archive.ubuntu.com
```

After a few days, just remark it out:
```
#83.133.255.54  archive.ubuntu.com
```

---

### Post by dbott67 on 2006-11-01
Okay... now for a bit of "trial & error".  You may want to print this out so that you can 'undo' the changes later.

1. Backup the /etc/resolv.conf file.
```
sudo cp /etc/resolv.conf /etc/resolv.conf.bak
```

2. Edit the /etc/resolv.conf file.
```
gksudo gedit /etc/resolv.conf
```

3. Remark out (#) any existing lines and then add the following new OpenDNS servers:
```
**#** search gsca.nrcan.gc.ca
**#** nameserver 192.55.224.20
**#** nameserver 192.55.224.12

nameserver 208.67.222.222
nameserver 208.67.220.220
```

Save file.

4. Try running **sudo apt-get update** again.

5. If that fails, try creating a static entry in your hosts file as per my post above (#34):
```
gksudo gedit /etc/hosts
```
Add the following line:
```
83.133.255.54  archive.ubuntu.com
```
Save & exit.

6. Try running **sudo apt-get update** again.

-Dave

---

### Post by dbott67 on 2006-11-01
If all that fails, I may have the answer --- and it may just be your corporate firewall that is blocking certain types of **http** content, as noted in the post below (the filter was blocking the bz2 files).

[http://ubuntuforums.org/showpost.php?p=424495&postcount=10](http://ubuntuforums.org/showpost.php?p=424495&postcount=10)

The fix might be just replacing the **http://** with **ftp://** in your sources.list file.  Assuming the firewall does not block certain files via FTP, you may be able to circumvent the problem.

```
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb ftp://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src ftp://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb ftp://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src ftp://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb ftp://ca.archive.ubuntu.com/ubuntu/ dapper universe
deb-src ftp://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb ftp://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src ftp://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb ftp://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src ftp://security.ubuntu.com/ubuntu dapper-security main restricted
deb ftp://security.ubuntu.com/ubuntu dapper-security universe
deb-src ftp://security.ubuntu.com/ubuntu dapper-security universe

```

To verify if HTTP/FTP filtering is enabled on your network, try the following:

**_HTTP Filtering:_**

Using Firefox, browse to [http://archive.ubuntu.com/](http://archive.ubuntu.com/) and try to open the following files:
1. [http://archive.ubuntu.com/ubuntu/dists/dapper/](http://archive.ubuntu.com/ubuntu/dists/dapper/) and click on Release.gpg
2. [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/) and click on Packages.bz2

If the files are blocked, then this is the problem.

_**FTP Filtering:**_

Using your favourite FTP client, try the following:
1. [ftp://archive.ubuntu.com/ubuntu/dists/dapper/](ftp://archive.ubuntu.com/ubuntu/dists/dapper/) and download Release.gpg
2. [ftp://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/](ftp://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/) and download Packages.bz2

-Dave

---

### Post by Roobert on 2006-11-01
> **dbott67 said:**
> A little more investigation turns up that Ubuntu has 2 'archive' servers: 85.133.25.**54** & 85.133.25.**23**.

From one of your earlier posts, it appears as though you're using .23, whereas I am using .54

I don't know if this has anything to do with the price of tea in China, but perhaps one of the servers is down.  You could edit your '/etc/hosts' file and create an entry in the file:
```
83.133.255.54  archive.ubuntu.com
```

After a few days, just remark it out:
```
#83.133.255.54  archive.ubuntu.com
```

Done and done. Still no go. I tried pinging archive.ubuntu.com as well, and it justs hangs there forever.

---

### Post by Roobert on 2006-11-01
[QUOTE=dbott67;1699840]Okay... now for a bit of "trial & error".  You may want to print this out so that you can 'undo' the changes later.

1. Backup the /etc/resolv.conf file.
```
sudo cp /etc/resolv.conf /etc/resolv.conf.bak
```

2. Edit the /etc/resolv.conf file.
```
gksudo gedit /etc/resolv.conf
```

<snip>

Man, you are just full of great ideas. Unfortunately, I tried the above ones as well to no avail. Your idea of changing the http sources to ftp sources in /etc/sources.list kind of worked, in that I could ping about 75% of the sites succesfully, but apt-get would time out on the rest. Maybe I'll try switching my host ID back to '23' from '54' to see if that's any faster...

---

### Post by Roobert on 2006-11-02
> **dbott67 said:**
> Just a few more pieces of info to help determine if it's a DNS issue.

What is the output of **ping archive.ubuntu.com**?
```
dbott@thedrake:/etc$ ping archive.ubuntu.com
PING archive.ubuntu.com (**85.133.25.54**) 56(84) bytes of data.
64 bytes from 85.133.25.54: icmp_seq=1 ttl=52 time=115 ms
64 bytes from 85.133.25.54: icmp_seq=3 ttl=52 time=115 ms
64 bytes from 85.133.25.54: icmp_seq=5 ttl=52 time=114 ms
64 bytes from 85.133.25.54: icmp_seq=6 ttl=52 time=115 ms
```

If the IP address is different for you, it could be DNS (or that Ubuntu has load-balanced servers...)

I can never successfully ping us/ca/archive.ubuntu.com - I basically have to Ctrl-C out because it justs hangs there forever.

---

### Post by dbott67 on 2006-11-02
> **Roobert said:**
> I can never successfully ping us/ca/archive.ubuntu.com - I basically have to Ctrl-C out because it justs hangs there forever.

Your corporate firewall may block pings (not unheard of).  Can you ping other sites?  Try pinging the following:

**1. Ping a known responding server by FQDN**
```
dbott@thedrake:~$ ping www.google.com
PING www.l.google.com (72.14.205.99) 56(84) bytes of data.
64 bytes from qb-in-f99.google.com (72.14.205.99): icmp_seq=1 ttl=248 time=26.1 ms
64 bytes from qb-in-f99.google.com (72.14.205.99): icmp_seq=2 ttl=248 time=25.7 ms
64 bytes from qb-in-f99.google.com (72.14.205.99): icmp_seq=3 ttl=248 time=25.5 ms
64 bytes from qb-in-f99.google.com (72.14.205.99): icmp_seq=4 ttl=248 time=24.6 ms

```

**2. Ping same site by IP**
```
dbott@thedrake:~$ ping 72.14.205.99
PING 72.14.205.99 (72.14.205.99) 56(84) bytes of data.
64 bytes from 72.14.205.99: icmp_seq=1 ttl=248 time=26.1 ms
64 bytes from 72.14.205.99: icmp_seq=2 ttl=248 time=26.0 ms
64 bytes from 72.14.205.99: icmp_seq=3 ttl=248 time=24.5 ms
64 bytes from 72.14.205.99: icmp_seq=4 ttl=248 time=24.7 ms

```

**3. Ping Ubuntu archives by IP (we already know it doesn't respond to FQDN**
```
dbott@thedrake:~$ ping 85.133.25.54
PING 85.133.25.54 (85.133.25.54) 56(84) bytes of data.
64 bytes from 85.133.25.54: icmp_seq=1 ttl=52 time=115 ms
64 bytes from 85.133.25.54: icmp_seq=2 ttl=52 time=114 ms
64 bytes from 85.133.25.54: icmp_seq=3 ttl=52 time=116 ms

```

Post any relevant output/errors here.

Thanks,
Dave

---

### Post by Roobert on 2006-11-02
Dave,

I tried this link, thread #10: 
[http://www.ubuntuforums.org/showthread.php?t=266590&highlight=can%27t+ping+repositories]("http://www.ubuntuforums.org/showthread.php?t=266590&highlight=can%27t+ping+repositories")

and I can now access the repositories!

Basically, it involves removing the line ```
Acquire::http::Proxy "false";
``` from /etc/apt/apt.conf. Really weird. **BUT** - I *still* can't successfully ping any of the sites you listed, despite being able to apt-get the repositories. What do you make of that?

---

### Post by dbott67 on 2006-11-02
That is very strange... I have that line in my /etc/apt/apt.conf file on both computers and don't have any problems.  

As a test, I configured my laptop to use my squid proxy server to see if the file would change and guess what --- it didn't.  The apt.conf file still reads:
```
dbott@dapper:/$ cat /etc/apt/apt.conf
Acquire::http::Proxy "false";
```

Next, I tried connecting to the repos using Synaptic.  The squid server verifies that all Synaptic traffic was running through it and I had Network Proxy, Firefox Prefs, and Synaptic Prefs set to use my proxy:
```
root@thedrake:/$tail -n 20 -f /var/log/squid/store.log
[COLOR="Red"]<--- here's the Synaptic traffic --->[/COLOR]
1162482979.701 RELEASE -1 FFFFFFFF 867DF915D5335DBE3EFBA72BCF544506  206 1162482979 1149102130        -1 text/plain 1/1 GET http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg
1162482979.825 RELEASE -1 FFFFFFFF 1F2DF2B172BFC106729005C912345363  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release
1162482979.853 RELEASE -1 FFFFFFFF 45CFD52275A73266F27909255353602F  304 1162482979        -1        -1 unknown -1/0 GET http://archive.ubuntu.com/ubuntu/dists/dapper/Release
1162482979.876 RELEASE -1 FFFFFFFF 365E35FEFF392E0895AA004A07294998  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.bz2
1162482979.919 RELEASE -1 FFFFFFFF 1FA06E22A1FC4C8CC3EC5EBF9A8304E6  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.bz2
1162482979.961 RELEASE -1 FFFFFFFF 24307B46B908E35887A530A11F133EBD  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.bz2
1162482980.008 RELEASE -1 FFFFFFFF DA67C571DB852F13AEE4C565C41D0E4A  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.bz2
1162482980.051 RELEASE -1 FFFFFFFF 78CE2564F4654D3009C5E4113DD068CA  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.bz2
1162482980.096 RELEASE -1 FFFFFFFF 39ED0CC46E5B7A7215E2BAC77DC04F04  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.bz2
1162482980.120 RELEASE -1 FFFFFFFF 3921C05EE4D7562FCB6DBF6E09ACA379  304 1162482980        -1        -1 unknown -1/0 GET http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2
1162482980.139 RELEASE -1 FFFFFFFF 1A5EE9BF32D428C4C1EFAB9106A683BD  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.bz2
1162482980.185 RELEASE -1 FFFFFFFF 090EE42BEFECF78ACC7B6CBBE80A5086  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2
1162482980.235 RELEASE -1 FFFFFFFF C87244A02AE949C6ACF22B2EBEF8D13F  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.bz2
1162482980.278 RELEASE -1 FFFFFFFF 9680BD6D1108C5ACD533379ED42BA71C  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2
1162482980.323 RELEASE -1 FFFFFFFF 2AA27863E0743C4115D9CF00E9330C35  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2
1162482980.366 RELEASE -1 FFFFFFFF A76950062AE35AC22311B98F3331C23C  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2
1162482980.410 RELEASE -1 FFFFFFFF 543EDCB2368432C632130CFCD58B88C8  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.bz2
1162482980.458 RELEASE -1 FFFFFFFF 3E9D522DFDDA7CC67316B42863C2C492  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.bz2
1162482980.500 RELEASE -1 FFFFFFFF 508B9664D68F3E50B622F3E79202A86F  304 1162482982        -1        -1 unknown -1/0 GET http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.bz2
[COLOR="Red"]<--- here's some web traffic to CNN.com--->[/COLOR]
1162482895.688 SWAPOUT 00 0000015B F1EB414FFE30788C87B1019E3F885DC5  200 1162482895 1147435542        -1 image/gif 8130/8130 GET http://i.a.cnn.net/cnn/.element/img/1.5/main/icons/pipeline_ico_wht.gif
1162482895.710 SWAPOUT 00 0000015C 44474A2D3E14CAE6E83AA362099F4E53  200 1162482895 1141920510        -1 image/gif 76/76 GET http://i.a.cnn.net/cnn/.element/img/1.5/ceiling/hdr_line_edge.gif
1162482895.740 SWAPOUT 00 0000015D D058323F454BEF06E285F94D441459A2  200 1162482895 1141854681        -1 image/gif 292/292 GET http://i.a.cnn.net/cnn/.element/img/1.5/main/hdr_bg_2.gif
1162482895.769 RELEASE -1 FFFFFFFF 304B8282F811E40FB9162EBD30BE0730  200 1162482895 1162569295 1162482895 image/gif 43/43 GET http://cnn.122.2o7.net/b/ss/cnnglobal/1/H.1-Pdv-2/s72216101585678?
1162482895.775 SWAPOUT 00 0000015E D1DFF4ADD33122227803AA215E5E9421  200 1162482895 1141070266        -1 image/gif 188/188 GET http://i.a.cnn.net/cnn/.element/img/1.5/ceiling/hdr_show_separator.gif
1162482895.803 SWAPOUT 00 0000015F F66975B16115E032FE6D063CBEF43211  200 1162482895 1153162789        -1 image/gif 453/453 GET http://i.a.cnn.net/cnn/.element/img/1.5/ceiling/nav.rt.end.bg.sprite.gif
1162482895.820 SWAPOUT 00 00000160 BDCEE0812EE01C9288C7318315F9B4E7  200 1162482895 1141757410        -1 image/gif 50/50 GET http://i.a.cnn.net/cnn/.element/img/1.5/main/vertical.dot.gif
1162482895.833 SWAPOUT 00 00000161 1F974D4F144C066B1E3B1F5FC54FF7E7  200 1162482895 1142958645        -1 image/gif 109/109 GET http://i.a.cnn.net/cnn/.element/img/1.5/main/t1_bg_bottom.gif

```

I read through those other threads & I can't see how the problem came about & why it doesn't affect me.

Anyhow, I'm glad it's working for you now.

-Dave

---

### Post by dbott67 on 2006-11-02
> **Roobert said:**
> ... I *still* can't successfully ping any of the sites you listed, despite being able to apt-get the repositories. What do you make of that?

I think that your firewall is set to drop/block ICMP ping requests.  Try this:

Install **traceroute**. 

Side note: I think the built-in grahical "Network Tools" version of traceroute uses 'tracepath' (or ping -R) to record the route and it never seems to work for me.  Traceroute (from the repos) does the trick:
```
sudo apt-get install traceroute
```
Then do a traceroute to archive.ubuntu.com:
```
dbott@thedrake:/$ traceroute archive.ubuntu.com
traceroute: Warning: archive.ubuntu.com has multiple addresses; using 85.133.25.54
traceroute to archive.ubuntu.com (85.133.25.54), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  55.205 ms  0.502 ms  0.648 ms
 2  www.xxx.yyy.execulink.net (209.183.xxx.yyy)  14.407 ms  11.819 ms  12.272 ms
 3  i.core1.ip.execulink.net (209.183.xxx.zzz)  14.665 ms  12.594 ms  13.521 ms
 4  67.29.145.41 (67.29.145.41)  23.173 ms  14.492 ms  24.172 ms
 5  so-8-0.hsa1.Detroit1.Level3.net (166.90.248.1)  33.726 ms  22.319 ms  24.113 ms
 6  so-4-3-0.mp1.Detroit1.Level3.net (4.68.115.1)  40.117 ms  24.111 ms  23.371 ms
 7  ae-0-0.bbr1.NewYork1.Level3.net (64.159.1.41)  55.701 ms  48.991 ms  49.774 ms
 8  as-0-0.bbr2.London2.Level3.net (4.68.128.110)  114.971 ms ae-1-0.bbr1.London2.Level3.net (212.187.128.46)  119.086 ms as-0-0.bbr2.London2.Level3.net (4.68.128.110)  113.378 ms
 9  ae-0-51.gar1.London2.Level3.net (4.68.117.11)  114.404 ms ae-0-55.gar1.London2.Level3.net (4.68.117.139)  115.569 ms 4.68.117.43 (4.68.117.43)  115.118 ms
10  195.50.91.142 (195.50.91.142)  115.399 ms 195.50.91.146 (195.50.91.146)  118.422 ms 195.50.91.150 (195.50.91.150)  116.645 ms
11  vlan102.core-l-1.lon2.mnet.net.uk (62.140.218.201)  120.045 ms  117.371 ms  118.385 ms
12  85.133.32.130 (85.133.32.130)  119.217 ms  120.294 ms  119.860 ms
13  85.133.25.54 (85.133.25.54)  122.544 ms  121.542 ms  116.724 ms

```

Here's tracepath:
```
dbott@thedrake:/$ tracepath archive.ubuntu.com
 1:  thedrake.bott.ca (192.168.1.106)                       0.255ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                            asymm  2   0.800ms
 2:  no reply
 3:  no reply
 4:  no reply
 5:  no reply
 6:  no reply
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply

[6]+  Stopped                 tracepath archive.ubuntu.com
```

See? It sucks!!! :)

---

### Post by Roobert on 2006-11-02
Yeah, all I get with traceroute is 

1 * * *
2 * * *
3 * * *
....

etc., etc., with nothing printed. Frick!

---

### Post by dbott67 on 2006-11-02
Definitely looks like your firewall is dropping them. Damn Canadian Government! :)

-Dave

---

### Post by Roobert on 2006-11-02
Well, thanks for your help regardless; you've certainly went out of your way for me. Much appreciated!

~ Eric.

---

### Post by la3875 on 2006-11-04
OK more noob questions regarding the same issue. I'm using Kubuntu desktop and can get to the /etc/apt/apt.conf folder but it wont let me edit or remove the file. What step am I missing? 

I also happen to have the same Netgear router and have performed all the previous trace operations and get similar errors. It seems to me removing the line from /etc/apt/apt.conf is my last resort.

Thanks!

---

### Post by la3875 on 2006-11-04
In desperation and since I am still sipping my first cup of Ubuntu, I did the following to access and remove the line from /etc/apt/apt.conf and updates are now working again!!!

code: gksudo gedit /etc/apt/apt.conf 

Thanks for your detailed and patient posts.

---

### Post by konungursvia on 2007-03-04
> **Roobert said:**
> I just did a fresh 'sudo apt-get update', and I get errors for every single default Dapper repository. This is a fresh install of Dapper as well. Can someone verify that the Dapper repos are updating properly?

~ Roobert.

Me too, and I think it's because my internet connection is a slower broadband ultralite. I think the servers are ignoring clients with slower download times, can any one confirm this?

---

