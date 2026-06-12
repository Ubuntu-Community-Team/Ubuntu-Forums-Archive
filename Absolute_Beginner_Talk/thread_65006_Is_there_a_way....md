---
title: "Is there a way..."
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by America's Reject on 2005-09-12
Can I get my music files from my Windows partition and play them in my Linux OS?

---

### Post by bored2k on 2005-09-12
Yes. You have to mount your Windows partition and install codecs first.

1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
3. [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

If you need help mounting your partition, just give us a shout.

---

### Post by aysiu on 2005-09-12
Yes.

---

### Post by America's Reject on 2005-09-12
[QUOTE=bored2k]Yes. You have to mount your Windows partition and install codecs first.

1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
3. [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

If you need help mounting your partition, just give us a shout.[/QUOTE]
 I could use help with the mounting.  Umm also.  I installed a bunch of codecs form the Ubuntu all in one thing.  SHould that have it all?

Thanks.  How can I get to you about mounting?  And can it be perminataly mounted?

---

### Post by aysiu on 2005-09-12
The Ubuntu Guide has all the answers:

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by America's Reject on 2005-09-12
[QUOTE=bored2k]Yes. You have to mount your Windows partition and install codecs first.

1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
3. [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

If you need help mounting your partition, just give us a shout.[/QUOTE]
 uhhh, hwod o I know if it is this, e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)

---

### Post by bored2k on 2005-09-12
[QUOTE=America's Reject]uhhh, hwod o I know if it is this, e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)[/QUOTE]
 Terminal mode (Applications -> System Tools -> Terminal)
1. sudo fdisk -l

There you will your partition table, just paste the drive you want to mount here or what fdisk said.

---

### Post by America's Reject on 2005-09-12
[QUOTE=bored2k]Terminal mode (Applications -> System Tools -> Terminal)
1. sudo fdisk -l

There you will your partition table, just paste the drive you want to mount here or what fdisk said.[/QUOTE]
 mmmk, It is mounted and I can access it.  What program should I use to play them like iTunes, and how do I put them in my library and install the program.  SOrry for all the trouble =S lol

---

### Post by bored2k on 2005-09-12
[QUOTE=America's Reject]mmmk, It is mounted and I can access it.  What program should I use to play them like iTunes, and how do I put them in my library and install the program.  SOrry for all the trouble =S lol[/QUOTE]
 There are many applications. If you dont want to install any, you Rhythmbox aka Music Player already installed wich acts pretty much like iTunes. In your applications > sound menu you can access it.

---

### Post by America's Reject on 2005-09-12
[QUOTE=bored2k]There are many applications. If you dont want to install any, you Rhythmbox aka Music Player already installed wich acts pretty much like iTunes. In your applications > sound menu you can access it.[/QUOTE]
 I get "This file is not an adio stream"

---

### Post by America's Reject on 2005-09-12
[QUOTE=America's Reject]I get "This file is not an adio stream"[/QUOTE]
 I thought, is it even possible to play ACC and MP3 on linux?  If so could this be the reason?  And if I can what do I need to do.

Another thing, how can I change the w to a capital?

---

### Post by invisage01 on 2005-09-12
once again.. refer to the guide.. refer to the guide .. make sure you have your extra repositries added (near the start of the guide).. once you have done that add the codecs that it says to add... or search synaptec for something like "codec" and see if you can see the ones you want there..

Ubuntu does not ship with Proprietary (im not sure on the spelling!  :grin: ) codecs, hence why you have to add the extra repositries and the fact that it doesnt ship with MP3 codecs..

the guide has it all.. :)

Iain.

---

### Post by America's Reject on 2005-09-12
[QUOTE=invisage01]once again.. refer to the guide.. refer to the guide .. make sure you have your extra repositries added (near the start of the guide).. once you have done that add the codecs that it says to add... or search synaptec for something like "codec" and see if you can see the ones you want there..

Ubuntu does not ship with Proprietary (im not sure on the spelling!  :grin: ) codecs, hence why you have to add the extra repositries and the fact that it doesnt ship with MP3 codecs..

the guide has it all.. :)

Iain.[/QUOTE]
 Do I add all of them?

Also I try and add them but the file is in another language!

---

### Post by aysiu on 2005-09-12
[QUOTE=America's Reject]Do I add all of them?[/quote] Yes. In fact, just go ahead and replace all of your existing sources with the ones in the guide.

> 
Also I try and add them but the file is in another language! What file is in another language? /etc/apt/sources.list? Is English not your first language?

---

### Post by America's Reject on 2005-09-12
[QUOTE=aysiu]Yes. In fact, just go ahead and replace all of your existing sources with the ones in the guide.

 What file is in another language? /etc/apt/sources.list? Is English not your first language?[/QUOTE]
 English is my language but the file is not =(

---

### Post by America's Reject on 2005-09-12
[QUOTE=America's Reject]English is my language but the file is not =([/QUOTE]
 example
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

# Dépôts normaux
deb http://fr.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu hoary main restricted

# Universe et Multiverse
```

an error?
- using device default
- using device default
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave

---

### Post by aysiu on 2005-09-12
Whoa. Did you get a French version of Ubuntu? Or did you select "French" for the language option when you installed it? Regardless, the Ubuntu Guide repositories are all in English, so just copy and paste those over your current French sources (the entire thing--just overwrite it completely) and type this into the terminal ```
sudo apt-get update
```

---

### Post by America's Reject on 2005-09-12
[QUOTE=aysiu]Whoa. Did you get a French version of Ubuntu? Or did you select "French" for the language option when you installed it? Regardless, the Ubuntu Guide repositories are all in English, so just copy and paste those over your current French sources (the entire thing--just overwrite it completely) and type this into the terminal ```
sudo apt-get update
```[/QUOTE]
 Doe snot look like it even matches...

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

# Dépôts normaux
deb http://fr.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu hoary main restricted

# Universe et Multiverse
deb http://fr.archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu hoary universe multiverse

# Mises à jour
deb http://fr.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu hoary-updates main restricted

# Mises à jour de sécurité
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security universe multiverse

# Extra
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

# Backports officiels
#deb http://fr.archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

# Backports non-officiels
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

# KDE 3.4.2
#deb http://kubuntu.org/hoary-kde342 hoary-updates main

# PHP5
#deb http://people.debian.org/~dexter php5 hoary

# suPHP (sources)
#deb-src http://manu.home-dn.net/debian/suphp-preview sid main

# Wine
#deb http://wine.sourceforge.net/apt/ hoary/
```

---

### Post by bored2k on 2005-09-12
[QUOTE=America's Reject]Doe snot look like it even matches...

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

# Dépôts normaux
deb http://fr.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu hoary main restricted

# Universe et Multiverse
deb http://fr.archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu hoary universe multiverse

# Mises à jour
deb http://fr.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu hoary-updates main restricted

# Mises à jour de sécurité
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security universe multiverse

# Extra
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

# Backports officiels
#deb http://fr.archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

# Backports non-officiels
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

# KDE 3.4.2
#deb http://kubuntu.org/hoary-kde342 hoary-updates main

# PHP5
#deb http://people.debian.org/~dexter php5 hoary

# suPHP (sources)
#deb-src http://manu.home-dn.net/debian/suphp-preview sid main

# Wine
#deb http://wine.sourceforge.net/apt/ hoary/
```[/QUOTE]
 Those look the right ones. It smells to me like you got those sources from the french ubuntu forums.

---

### Post by America's Reject on 2005-09-12
huh, thats in my system
I am so lost right now.

---

### Post by bored2k on 2005-09-12
[QUOTE=America's Reject]huh, thats in my system
I am so lost right now.[/QUOTE]
 1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
Just replace all those for these ones.

---

### Post by America's Reject on 2005-09-12
[QUOTE=bored2k]1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
Just replace all those for these ones.[/QUOTE]
 what about the KDE and PHP5?

---

### Post by aysiu on 2005-09-12
[QUOTE=America's Reject]what about the KDE and PHP5?[/QUOTE] Yeah, replace everything. Just put a fresh list of the extra repositories in.

---

### Post by America's Reject on 2005-09-13
[QUOTE=aysiu]Yeah, replace everything. Just put a fresh list of the extra repositories in.[/QUOTE]
 problems

```
owner@Shane:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
owner@Shane:~$ sudo gedit /etc/apt/sources.list
- using device default
- using device default
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
owner@Shane:~$ sudo apt-get update
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release.gpg
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary ReleaseIgn cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Hit http://security.ubuntu.com hoary-security Release
Hit http://us.archive.ubuntu.com hoary Release
Get:4 http://archive.ubuntu.com hoary Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://us.archive.ubuntu.com hoary-updates Release
Hit http://archive.ubuntu.com hoary Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Fetched 4B in 1s (4B/s)
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
owner@Shane:~$ sudo apt-get install libmotif3
Reading package lists... Done
Building dependency tree... Done
libmotif3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

---

### Post by aysiu on 2005-09-13
Can you post the exact and full contents of your /etc/apt/sources.list?

---

### Post by America's Reject on 2005-09-13
[QUOTE=aysiu]Can you post the exact and full contents of your /etc/apt/sources.list?[/QUOTE]
 deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by aysiu on 2005-09-13
It looks good, but can you comment out this line?

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
```

To "comment out" the line, just put two number signs in front of it:

```
## deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
```

Then, *sudo apt-get update*. See if that makes a difference.

---

### Post by America's Reject on 2005-09-13
[QUOTE=aysiu]It looks good, but can you comment out this line?

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
```

To "comment out" the line, just put two number signs in front of it:

```
## deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
```

Then, *sudo apt-get update*. See if that makes a difference.[/QUOTE]
 Ok, didn't get any errors

---

### Post by aysiu on 2005-09-13
I'm speculating, but I think maybe the CD-ROM source was somehow in conflict with the other sources. I don't know.

---

### Post by America's Reject on 2005-09-13
[QUOTE=aysiu]I'm speculating, but I think maybe the CD-ROM source was somehow in conflict with the other sources. I don't know.[/QUOTE]
 Does this mean there is something wrong, still? =S lol

Also, how do I play m4p files?  I don't think the codecs worked.

---

### Post by aysiu on 2005-09-13
[QUOTE=America's Reject]
Also, how do I play m4p files?  I don't think the codecs worked.[/QUOTE] [http://www.ubuntuforums.org/showthread.php?t=36632&page=2&pp=10](http://www.ubuntuforums.org/showthread.php?t=36632&page=2&pp=10)
[http://ubuntuforums.org/showthread.php?t=33420](http://ubuntuforums.org/showthread.php?t=33420)
[http://ubuntuforums.org/showthread.php?t=33688](http://ubuntuforums.org/showthread.php?t=33688)

---

### Post by Galoot on 2005-09-18
[QUOTE=America's Reject]English is my language but the file is not =([/QUOTE]
[Blame keyes](http://ubuntuforums.org/showthread.php?t=64629). :)

I just noticed the same thing with my sources.list, and was tearing my hair out for a 1/2 hour trying to figure out why.

---

