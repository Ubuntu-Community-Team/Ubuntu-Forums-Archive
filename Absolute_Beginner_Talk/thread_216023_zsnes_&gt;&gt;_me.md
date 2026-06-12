---
title: "zsnes &gt;&gt; me"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by struess on 2006-07-14
i'm to this point with installing zsnes:  ](*,)  i spent all day reading through the forums and on google trying to install zsnes, and just can't seem to.  i changed my repositories to the ones suggested on [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources), enabled multiverse, even tried installing via the .tar.gz off sourceforge.  no dice.  the message i keep getting is:

johnk@struess:~$ sudo apt-get install zsnes
Reading package lists... Done
Building dependency tree... Done
Package zsnes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zsnes has no installation candidate

...and when i search synaptic for "zsnes", the only result is the package visualboyadvance.  this leads me to believe my system isn't checking the right repository (or, heaven forbid, zsnes is no longer available), but i've enabled all of them.  ><  

couple of conspicuous notes, dunno how relevant they are:  [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) seems to no longer be available, and compiling the program (using ./configure, make, etc..) failed, too.  from what i understand, zsnes is the only way to go as far as ubuntu is concerned emulator-wise, and not having an emulator would make me a very sad panda.  copy of my sources.list is below.  thanks for any help you can give!

> 
johnk@struess:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free



---

### Post by scxtt on 2006-07-14
it's in multiverse, i can see it in synaptic ...```
:> cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.canonical.com/ubuntu dapper-commercial main
```

---

### Post by junamuno on 2006-07-14
Did you try looking for it in Synaptic???

---

### Post by struess on 2006-07-14
still no luck, scxtt, even with your sources loaded.  would it matter that i'm running amd64?  i actually used it in the dark days of XP, so i'm sure it works with my processor, but possibly it doesn't work with this version of ubuntu... can anyone (hopefully not) verify that?

---

### Post by scxtt on 2006-07-14
have you refreshed ("Reload") synaptic before searching again? -- someone else had a problem getting things to show up after using my sources.list -- they had to "Reload" multiple times ... it's there, i checked :)

---

### Post by struess on 2006-07-14
haha yeah, i saw that post and clicked reload, what was it, 10 times?  no luck, unfortantely :P

---

### Post by scxtt on 2006-07-14
try a **sudo apt-get update** maybe? -- don't know if that's more effective ...

---

### Post by struess on 2006-07-14
yeah, updated and upgraded, backflipped and even tried cursing.  

i haven't rebooted though..   o.O  back in a flash

---

### Post by smokeysaysno on 2006-07-14
I used Asher256's repository to get ZSNES.
You can find the repos along with easy instructions at this url [http://asher256-repository.tuxfamily.org/english.php]("http://asher256-repository.tuxfamily.org/english.php")
There is also a decent Game Boy Advance emulator there and a sweet music converter too.  Gnormalize is a bit of a pain to configure but it works great.  After you add this repos and refresh, you shold be able to download ZSNES no problem. :-D

---

### Post by struess on 2006-07-14
the plot thickens... and this is gonna be a large-ish post.
couldn't seem to download from Asher256's repos, for some reason, but the webpage clearly states that zsnes is RIGHT THERE.  oh so close.

here's my sources.list
> 
 #
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

##Asher256's repository
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french



here's the result of **sudo apt-get update**:
> johnk@struess:~$ sudo apt-get update
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper Release.gpg
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper Release
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/main Packages
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/restricted Packages
Err cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper Release.gpg
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu Release.gpg
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/main Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/dupdate Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/french Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/main Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/dupdate Packages
Ign [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/french Packages
Err [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/main Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Err [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/dupdate Packages
  404 Not Found
Err [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper/french Packages
  404 Not Found
Err [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/main Packages
  404 Not Found
Err [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/dupdate Packages
  404 Not Found
Err [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu/french Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 5B in 1s (4B/s)
Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/dapper/main/binary-amd64/Packages.gz](http://asher256-repository.tuxfamily.org/dists/dapper/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/dapper/dupdate/binary-amd64/Packages.gz](http://asher256-repository.tuxfamily.org/dists/dapper/dupdate/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/dapper/french/binary-amd64/Packages.gz](http://asher256-repository.tuxfamily.org/dists/dapper/french/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/ubuntu/main/binary-amd64/Packages.gz](http://asher256-repository.tuxfamily.org/dists/ubuntu/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/ubuntu/dupdate/binary-amd64/Packages.gz](http://asher256-repository.tuxfamily.org/dists/ubuntu/dupdate/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/ubuntu/french/binary-amd64/Packages.gz](http://asher256-repository.tuxfamily.org/dists/ubuntu/french/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


i tried a direct **sudo apt-get install zsnes**, but received a similarly unenthusiastic message:

> Reading package lists... Done
Building dependency tree... Done
Package zsnes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zsnes has no installation candidate

that's a good repository site, though.. thanks :)  i'll keep that one on hand.  is there something i neglected to do to the sources.list file?

---

### Post by struess on 2006-07-14
also, the ace up my sleeve from my windows days -- i.e. restarting -- didn't do any good either.

---

### Post by echo $USER on 2006-07-14
Take your pick...

[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fcontrib%2Fz%2Fzsnes%2Fzsnes_1.400-1_i386.deb&md5sum=73d4c0205e5d50d4c8652c48c5a94b7c&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fcontrib%2Fz%2Fzsnes%2Fzsnes_1.400-1_i386.deb&md5sum=73d4c0205e5d50d4c8652c48c5a94b7c&arch=i386&type=main)

Then install the dpkg.  If it complains about dependencies, consult this..

[http://packages.debian.org/stable/otherosfs/zsnes](http://packages.debian.org/stable/otherosfs/zsnes)

---

### Post by struess on 2006-07-14
thanks for that, echo.. was also unaware of that site's packages.

however, we run into this little creature again:

> 
dpkg: error processing zsnes_1.400-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 zsnes_1.400-1_i386.deb


searched on that site for another package.. but it didn't appear that an amd64 verion is available.

---

### Post by echo $USER on 2006-07-14
oh sorry, i didn't realize.  i am still running 32 bit, cant help you with 64; I don't have any expeience with 64 yet.

Oh but i think there is a snes emulator for windows that runs perfectly in wine.  maybe give that a shot if you can't get it to run natively.  here it is

[http://prdownloads.sourceforge.net/zsnes/zsnesw142.zip](http://prdownloads.sourceforge.net/zsnes/zsnesw142.zip)

and its made by znes.

---

### Post by struess on 2006-07-14
new development:  rolled my sources.list back to scxtt's, updated, opened up synaptic and reloaded... and did a search for zsnes.  this time, nothing came up, not even the visualboyadvance package.  

sneaking packages right out from under me.

---

### Post by struess on 2006-07-15
problem solved.

seems it *was* the 64-bit architecture i was having trouble with.  after failing to *dpkg -i --force-architecture* the .deb file above, i found boyofdestiny's how-to on setting up a 32-bit chroot environment (here: [http://ubuntuforums.org/showthread.php?t=157412&highlight=chroot](http://ubuntuforums.org/showthread.php?t=157412&highlight=chroot)).    the above .deb file worked liked a charm once that was set up.

thanks for the help, guys.

note:  for anyone else with the sources.list problem, i ended up just rebuilding my repos from the omniscient [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic).

---

