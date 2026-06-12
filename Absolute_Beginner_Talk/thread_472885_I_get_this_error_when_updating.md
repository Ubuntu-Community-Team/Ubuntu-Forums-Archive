---
title: "I get this error when updating"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-06-13
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



What does it mean? How do I fix it? Thanks

---

### Post by Inxsible on 2007-06-13
Did you try doing what it says?
 
Go to the Terminal and run the command:
```
dpkg --configure -a
```

---

### Post by DeuceII on 2007-06-13
> **ajskhan said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



What does it mean? How do I fix it? Thanks

I had the same problem about 1 week ago.

Type the follwing in a Terminal and then press CTRL-ALT_BACKSPACE
***sudo dpkg --configure -a***
(you will need to enter your password at this point)

hth

DeuceII

---

### Post by ajskhan on 2007-06-13
> **DeuceII said:**
> I had the same problem about 1 week ago.

Type the follwing in a Terminal and then press CTRL-ALT_BACKSPACE
***sudo dpkg --configure -a***
(you will need to enter your password at this point)

hth

DeuceII


Thanks something is happening

I got this:
~$ sudo dpkg --configure -a
Setting up libfreetype6 (2.2.1-5ubuntu1.1) ...

Setting up libexif12 (0.6.13-5ubuntu0.1) ...

Setting up capplets-data (2.18.1-0ubuntu2.1) ...

Setting up vim-common (7.0-164+1ubuntu7.1) ...

Setting up libmagic1 (4.19-1ubuntu2.1) ...

Setting up libgimp2.0 (2.2.13-1ubuntu4.1) ...

Setting up file (4.19-1ubuntu2.1) ...
Setting up python2.5 (2.5.1-0ubuntu1) ...

Setting up gimp-data (2.2.13-1ubuntu4.1) ...
dpkg: error processing metacity-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up app-install-data-commercial (7.1) ...
Caching application data...
Got non-package menu entry kiso.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry brasero.desktop
Got non-package menu entry kmyfirewall.desktop
Generating mime/codec maps...

Setting up libnspr4 (1.firefox2.0.0.4+1-0ubuntu1) ...

Setting up libnss3 (1.firefox2.0.0.4+1-0ubuntu1) ...

Setting up libpng12-0 (1.2.15~beta5-1ubuntu1) ...

Setting up vim-tiny (7.0-164+1ubuntu7.1) ...

Setting up gimp (2.2.13-1ubuntu4.1) ...

Setting up python (2.5.1-0ubuntu3) ...

Setting up update-manager-core (0.59.20) ...

Setting up python-problem-report (0.76.1) ...

Setting up gimp-python (2.2.13-1ubuntu4.1) ...

Setting up firefox (2.0.0.4+1-0ubuntu1) ...
Please restart any running Firefoxes, or you will experience problems.
Warning: something created compreg.dat!
Your system was affected by this bug: [https://launchpad.net/bugs/30791](https://launchpad.net/bugs/30791)
compreg.dat has now been removed again, which should fix the symptoms.

Setting up python-apport (0.76.1) ...

Setting up firefox-gnome-support (2.0.0.4+1-0ubuntu1) ...

Setting up apport (0.76.1) ...
 * Starting automatic crash report generation: apport                [ OK ] 

Setting up apport-gtk (0.76.1) ...
Errors were encountered while processing:
 metacity-common



Did it work?

---

### Post by Inxsible on 2007-06-13
Does the error re-occur when you try to do updates?
 
try ```
sudo aptitude update
```

---

### Post by ajskhan on 2007-06-13
Nevermind, fixed :)

---

### Post by grathinam on 2007-06-14
am still having the same problem unable to update, tried what was posted , it just reboots my machine but does not fix anything.

Find below the error below

----------------------

[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/Release.gpg:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/Release.gpg:) Could not resolve 'mi.mirror.garr.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/main/i18n/Translation-en_US.bz2:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/main/i18n/Translation-en_US.bz2:) Could not resolve 'mi.mirror.garr.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'mi.mirror.garr.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_US.bz2:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_US.bz2:) Could not resolve 'mi.mirror.garr.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'mi.mirror.garr.us'
[http://ubuntu.iuculano.us/dists/feisty/Release.gpg:](http://ubuntu.iuculano.us/dists/feisty/Release.gpg:) Could not resolve 'ubuntu.iuculano.us'
[http://ubuntu.iuculano.us/dists/feisty/amsn/i18n/Translation-en_US.bz2:](http://ubuntu.iuculano.us/dists/feisty/amsn/i18n/Translation-en_US.bz2:) Could not resolve 'ubuntu.iuculano.us'
[http://ubuntu.iuculano.us/dists/feisty/thunderbird/i18n/Translation-en_US.bz2:](http://ubuntu.iuculano.us/dists/feisty/thunderbird/i18n/Translation-en_US.bz2:) Could not resolve 'ubuntu.iuculano.us'
[http://files.beep-media-player.org/packages/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://files.beep-media-player.org/packages/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://kubuntu.org/packages/koffice-latest/dists/feisty/main/binary-i386/Packages.gz:](http://kubuntu.org/packages/koffice-latest/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://kubuntu.org/packages/koffice-latest/dists/feisty/main/source/Sources.gz:](http://kubuntu.org/packages/koffice-latest/dists/feisty/main/source/Sources.gz:) 404 Not Found
[http://files.beep-media-player.org/packages/ubuntu/dists/feisty/testing/binary-i386/Packages.gz:](http://files.beep-media-player.org/packages/ubuntu/dists/feisty/testing/binary-i386/Packages.gz:) 404 Not Found
[http://kubuntu.org/packages/amarok-latest/dists/feisty/main/binary-i386/Packages.gz:](http://kubuntu.org/packages/amarok-latest/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://kubuntu.org/packages/amarok-latest/dists/feisty/main/source/Sources.gz:](http://kubuntu.org/packages/amarok-latest/dists/feisty/main/source/Sources.gz:) 404 Not Found
[http://files.beep-media-player.org/packages/ubuntu/dists/feisty/main/source/Sources.gz:](http://files.beep-media-player.org/packages/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found
[http://files.beep-media-player.org/packages/ubuntu/dists/feisty/testing/source/Sources.gz:](http://files.beep-media-player.org/packages/ubuntu/dists/feisty/testing/source/Sources.gz:) 404 Not Found
[http://lprod.org/deb/feisty/./Packages.gz:](http://lprod.org/deb/feisty/./Packages.gz:) 404 Not Found
[http://lprod.org/deb/feisty/./Sources.gz:](http://lprod.org/deb/feisty/./Sources.gz:) 404 Not Found
[http://cle.linux.org.tw/candyz/Ubuntu/feisty/i386/Packages.gz:](http://cle.linux.org.tw/candyz/Ubuntu/feisty/i386/Packages.gz:) 404 Not Found
[http://ubuntu.tolero.org/dists/feisty/main/binary-i386/Packages.gz:](http://ubuntu.tolero.org/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.tolero.org/dists/feisty/main/source/Sources.gz:](http://ubuntu.tolero.org/dists/feisty/main/source/Sources.gz:) 404 Not Found
[http://www.albertomilone.com/drivers/feisty/latest/32bit/binary/Packages.gz:](http://www.albertomilone.com/drivers/feisty/latest/32bit/binary/Packages.gz:) 404 Not Found
[http://debs.michaelbiebl.de/dists/feisty/main/binary-i386/Packages.gz:](http://debs.michaelbiebl.de/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://debs.michaelbiebl.de/dists/feisty/main/source/Sources.gz:](http://debs.michaelbiebl.de/dists/feisty/main/source/Sources.gz:) 404 Not Found
[http://ubuntu.iuculano.us/dists/feisty/amsn/binary-i386/Packages.gz:](http://ubuntu.iuculano.us/dists/feisty/amsn/binary-i386/Packages.gz:) Could not resolve 'ubuntu.iuculano.us'
[http://ubuntu.iuculano.us/dists/feisty/thunderbird/binary-i386/Packages.gz:](http://ubuntu.iuculano.us/dists/feisty/thunderbird/binary-i386/Packages.gz:) Could not resolve 'ubuntu.iuculano.us'
[http://ubuntu.iuculano.us/dists/feisty/amsn/source/Sources.gz:](http://ubuntu.iuculano.us/dists/feisty/amsn/source/Sources.gz:) Could not resolve 'ubuntu.iuculano.us'
[http://ubuntu.iuculano.us/dists/feisty/thunderbird/source/Sources.gz:](http://ubuntu.iuculano.us/dists/feisty/thunderbird/source/Sources.gz:) Could not resolve 'ubuntu.iuculano.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz:) Could not resolve 'mi.mirror.garr.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz:) Could not resolve 'mi.mirror.garr.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz:) Could not resolve 'mi.mirror.garr.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz:) Could not resolve 'mi.mirror.garr.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/main/source/Sources.gz:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/main/source/Sources.gz:) Could not resolve 'mi.mirror.garr.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/restricted/source/Sources.gz:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/restricted/source/Sources.gz:) Could not resolve 'mi.mirror.garr.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/universe/source/Sources.gz:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/universe/source/Sources.gz:) Could not resolve 'mi.mirror.garr.us'
[http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz:](http://mi.mirror.garr.us/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz:) Could not resolve 'mi.mirror.garr.us'

----------------------------

Thanks in advance

---

### Post by 3rdsun on 2007-06-14
> **ajskhan said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I had this same error. I just typed in what the error message said and hit enter(when I hit ctrl-alt-bck it just log out). It seams it was an error with VMbox. it asked me if i wanted to configure VMbox. I hit yes and everything was ok

---

### Post by grathinam on 2007-06-14
am not getting you, it is not  advising me to do anything

---

### Post by Inxsible on 2007-06-14
> **grathinam said:**
> am not getting you, it is not  advising me to do anything

What did you try ? Does it give you any errors when you try the above posted commands ?

---

### Post by grathinam on 2007-06-14
am getting the below list of errors, which I have posted here, unable to do any update using update manager or from the command line

Thanks

W: GPG error: [http://snapshots.ekiga.net](http://snapshots.ekiga.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A5E3A5A52ABFCB1
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 576856718434D43A
W: GPG error: [http://ubuntu.geole.info](http://ubuntu.geole.info) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BC40ED2499419355
W: GPG error: [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 580E2519969F3F57
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: GPG error: [http://www.imbrandon.com](http://www.imbrandon.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6CFB8719887D9FD2
W: GPG error: [http://www.linux2go.dk](http://www.linux2go.dk) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A278DF5EE8BDA4E3
W: GPG error: [http://ubuntu.geole.info](http://ubuntu.geole.info) feisty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BC40ED2499419355
W: GPG error: [http://ftp.musicbrainz.org](http://ftp.musicbrainz.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3A39A02A92132F7B
W: GPG error: [http://edevelop.org](http://edevelop.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 223020C2A7C6F0DF
W: GPG error: [http://debs.peadrop.com](http://debs.peadrop.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 02D40794DD385D79
W: GPG error: [http://www.tvfreeplayer.com](http://www.tvfreeplayer.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9CFD7AEA3C6489CB
W: GPG error: [http://home.eng.iastate.edu](http://home.eng.iastate.edu) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4C8BC4C880DF6D58
W: GPG error: [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 223020C2A7C6F0DF
W: GPG error: [http://cl.naist.jp](http://cl.naist.jp) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B8F0E6C98ABD1965
W: GPG error: [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651
W: GPG error: [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) feisty-depomaniak Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8BB73F9E1D59E694
W: GPG error: [http://deb.svx.pl](http://deb.svx.pl) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C12ADDB16FB65A0F
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: GPG error: [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8CC68B397E2E4741
W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: GPG error: [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A361B38AB6A4EB33
W: GPG error: [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4C8BC4C880DF6D58
W: GPG error: [http://kubuntu.org](http://kubuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://kubuntu.org](http://kubuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: GPG error: [http://www.in.fh-merseburg.de](http://www.in.fh-merseburg.de) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB210090B029CB84
W: GPG error: [http://archive.czessi.net](http://archive.czessi.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A714EB87D1B1F415
W: GPG error: [http://www.telemail.fi](http://www.telemail.fi) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: GPG error: [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A5E3A5A52ABFCB1
W: GPG error: [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 80E5E56B02544D0E
W: GPG error: [http://mirror.randumb.org](http://mirror.randumb.org) feisty-darkmagez Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB5D6B0AA3012FB3
W: GPG error: [http://repository.debuntu.org](http://repository.debuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29
W: GPG error: [http://apt.sourceguru.net](http://apt.sourceguru.net) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2404ED3A6AAAA569
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://apt.mepis.org](http://apt.mepis.org) mepis Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D3F985C51A77B3E9
W: GPG error: [http://apt.mepis.org](http://apt.mepis.org) mepis Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D3F985C51A77B3E9
W: GPG error: [ftp://ftp.gwdg.de](ftp://ftp.gwdg.de)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F64E067D0845D62
W: GPG error: [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 84F27CD6A2BF7BCB
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://www.in.fh-merseburg.de](http://www.in.fh-merseburg.de) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB210090B029CB84

---

### Post by ajskhan on 2007-06-15
I am a very noob, but is your internet connected?

---

### Post by grathinam on 2007-06-15
Yeap, am connected. No issues there

Thanks

---

### Post by facundocorradini on 2007-07-02
well.... you have added several apt sources to your system... was that really necesary?? ... where do you get that list???....

I recomend you to stay with the original sources.list from ubuntu, since it is a list of really safe and stable software... (and thay all have their key)


Answering your question, wath you have to do is add the public keys from every of the repositories that you have added to that list. 

But anyway, i strongely recomend you to get the original sources.list......

(sorry bout the english, i'm from argentina..)

---

### Post by Seisen on 2007-07-02
If you open up every one ot those repo's that said missing key it should have directions somewhere to add the GPG key.

---

### Post by grathinam on 2007-07-02
where can I get the required sources list. Thanks in advance

---

### Post by Seisen on 2007-07-02
```
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

---

