---
title: "Public keys"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-16
how do i add public keys??

i sudo apt-get update

and i have some keys missing.

i added before in command line but i forgot.

how do u do it??:D

---

### Post by gilgongo on 2007-06-16
Unless you are using some non-standard respositories, I think you can just run apt-get update again and it'll get them won't it?

---

### Post by starcraft.man on 2007-06-16
> **skymera said:**
> how do i add public keys??

i sudo apt-get update

and i have some keys missing.

i added before in command line but i forgot.

how do u do it??:D

Which repos did you add specifically? What site from? They usually list the gpg key and command at the site. Please provide link and I'll give ya the command to do it.

---

### Post by skymera on 2007-06-16
i think i have quite a few.
i run sudo apt-get update

i habve some duplicates aswell. SORRY FOR LONG POST

```
 W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://www.virtualbox.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: GPG error: http://apt.mepis.org mepis Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D3F985C51A77B3E9
W: GPG error: http://apt.mepis.org mepis Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D3F985C51A77B3E9
W: GPG error: http://www.imbrandon.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6CFB8719887D9FD2
W: GPG error: ftp://ftp.gwdg.de  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F64E067D0845D62
W: Duplicate sources.list entry http://ubuntu.beryl-project.org feisty/main Packages (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com feisty-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com feisty-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com feisty-security/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com feisty-security/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com feisty-security/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com feisty-security/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com feisty-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_feisty-commercial_main_binary-i386_Packages)
W: Duplicate sources.list entry http://wine.budgetdedicated.com feisty/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://www.getautomatix.com feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead. 
```

Here is my sources list:

  ```
  # Treviño&#8217;s Ubuntu Feisty Fawn Sources list
    # http://3v1n0.tuxfamily.org/blog/?page_id=13
    #
    # Repository List based on standard feisty with many extra packages
    #
    # If you get errors about missing keys, lookup the key in this file
    # and run these commands (replace KEY with the key number):
    #
    #  gpg --keyserver subkeys.pgp.net --recv KEY
    #  gpg --export --armor KEY | sudo apt-key add -
    #
    # If you have a gpg key URL use (replace URL with the key address):
    #
    #  wget URL --quiet -O - | sudo apt-key add -
    #
    # If you have a gpg key file use (replace FILE with the key file):
    #
    #  sudo apt-key add FILE
    #
    # In the repository list page there&#8217;s also a script that can do this
    # work automatically, this is suggested only if you know what you&#8217;re doing


deb http://ubuntu.beryl-project.org feisty main


    # Ubuntu supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-proposed restricted main multiverse universe #Added by software-properties

    # Ubuntu community supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-security universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-proposed universe multiverse

    # Ubuntu backports project (GPG key: 437D05B5)
deb http://mi.mirror.garr.it/ubuntu feisty-backports main restricted universe multiverse
deb-src http://mi.mirror.garr.it/ubuntu feisty-backports main restricted universe multiverse

    # CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
    # RealPlayer10, Opera, VmWare Server and more to come.)
deb http://archive.canonical.com/ubuntu feisty-commercial main

    # UbuntuStudio Repository (GPG key: B6A4EB33)
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb-src http://archive.ubuntustudio.org/ubuntustudio feisty main

    ## kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
# deb http://kubuntu.org/packages/kde-latest feisty main
# deb-src http://kubuntu.org/packages/kde-latest feisty main

    ## kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
# deb http://kubuntu.org/packages/koffice-latest feisty main
# deb-src http://kubuntu.org/packages/koffice-latest feisty main

    ## kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest feisty main
deb-src http://kubuntu.org/packages/amarok-latest feisty main

    # kubuntu.org packages for KDE4 alpha-1 (GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde4-3.90.1 feisty main
deb-src http://kubuntu.org/packages/kde4-3.90.1 feisty main

    # Bleeding edge wine packages
deb http://wine.budgetdedicated.com/apt feisty main
deb-src http://wine.budgetdedicated.com/apt feisty main

    # Seveas&#8217; packages (GPG key: 1135D466)
    # GPG key-file: http://mirror.ubuntulinux.nl/1135D466.gpg
deb http://mirror.ubuntulinux.nl feisty-seveas all
deb-src http://mirror.ubuntulinux.nl feisty-seveas all

    # The Opera browser (packages) (GPG key: 6A423791)
deb http://deb.opera.com/opera etch non-free

    ## Google picasa packages (GPG key: 7FAC5991 - missing)
deb http://dl.google.com/linux/deb/ stable non-free

    # Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu - ex Penguin Liberation Front)
    # GPG key-file: http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

    # The repository from Kubuntu Germany
    # GPG key-file: http://archive.czessi.net/ubuntu/kczessi.gpg
deb http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview

    # Achim&#8217;s Unofficial &#8216;feisty&#8217; Kubuntu packages
    # GPG key-file: http://www.mpe.mpg.de/~ach/ach-gpg.asc
deb http://www.mpe.mpg.de/~ach/kubuntu/feisty ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/feisty ./

    # Ubuntu feisty University Klagenfurt packages
    # GPG key-file: http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub
    # $ sudo apt-key add uniklu-debuild.pub
    #   uniklu:         backports and new packages
    #   uniklu-intern:  not freely redistributable (jvm), or modified packages
    #   uniklu-testing: packages not ready for general use
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu-intern
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu-testing
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu-intern
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu-testing

    # MEPIS improvements, overrides and updates (distro based on kubuntu)
deb http://apt.mepis.org/mepis32-6.5/ mepis main
deb http://apt.mepis.org/simply32-6.0/ mepis main

    # Ekiga and Debian pkg-voip
deb http://pkg-voip.buildserver.net/ubuntu feisty main

    # MythTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
deb http://home.eng.iastate.edu/~superm1 feisty all
deb-src http://home.eng.iastate.edu/~superm1 feisty all

    # Official Beryl Ubuntu Packages (GPG key: 1609B551)
    # GPG key-file: http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main

    # Ubuntu repository for Screenlets (GPG key: F854AFD7)
    # GPG key-file: http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb-src http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

    # Subpixel Font rendering packages (GPG key: 937215FF)
    # Improved fonts on LCDs - WARNING: May violate some patents
    # GPG key-file: http://www.telemail.fi/mlind/ubuntu/937215FF.gpg
deb http://www.telemail.fi/mlind/ubuntu feisty fonts main
deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts main

    ## Others mlind experimental misc Packages (GPG key: 937215FF)
    ## GPG key-file: http://www.telemail.fi/mlind/ubuntu/937215FF.gpg
deb http://www.telemail.fi/mlind/ubuntu feisty experimental
deb-src http://www.telemail.fi/mlind/ubuntu feisty experimental

    # Skype packages
deb http://download.skype.com/linux/repos/debian/ stable non-free

    # Geole&#8217;s Ubuntu Repository
    # GPG key-file: http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg
deb http://ubuntu.geole.info/ feisty universe multiverse
deb-src http://ubuntu.geole.info/ feisty universe multiverse
deb http://ubuntu.geole.info/ feisty-backports main universe multiverse restricted
deb-src http://ubuntu.geole.info/ feisty-backports main universe multiverse restricted

    # Linux2Go Ubuntu Packages (GPG key: E8BDA4E3)
deb http://www.linux2go.dk/ubuntu feisty main
deb-src http://www.linux2go.dk/ubuntu feisty main

    # Asher256&#8217;s Repository
deb http://asher256-repository.tuxfamily.org edgy main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

    # Tvfreeplayer Packages (GPG key: )
    # GPG key-file: http://www.tvfreeplayer.com/linux/falcon/tvfreeplayer.gpg
deb http://www.tvfreeplayer.com/linux/falcon feisty all
deb-src http://www.tvfreeplayer.com/linux/falcon feisty all

    # gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb http://snapshots.ekiga.net/ubuntu/ feisty main
deb-src http://snapshots.ekiga.net/ubuntu/ feisty main

    ## lprod packages: many audio/video apps: avidemux, cinelerra&#8230;
deb http://lprod.org/deb/feisty/ ./
deb-src http://lprod.org/deb/feisty/ ./

    # Cinelerra Feisty packages
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./

    ## Spring Packages (RTS game)
deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /
deb-src ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /

    # Cafuego&#8217;s feisty Stuff: Broadcom firmware, google-earth, secondlife (GPG key: 969F3F57)&#8230;
deb http://au.ubuntu.cafuego.net feisty-cafuego all
deb-src http://au.ubuntu.cafuego.net feisty-cafuego all

    # Debuntu Ubuntu feisty packages
    # GPG Key: http://repository.debuntu.org/GPG-Key-chantra.txt
deb http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse

    ## BMPx feisty Repository
    ## GPG key-file: http://files.beep-media-player.org/packages/bmp-packages.pubkey
deb http://files.beep-media-player.org/packages/ubuntu feisty main testing
deb-src http://files.beep-media-player.org/packages/ubuntu feisty main testing

    # Morgoth Repository (GPG key: 7E2E4741)
    # Provides Monkey&#8217;s Audio, xmms pugins, vlc plugins, gqview, audacius, audacity&#8230;
    # GPG key-file: http://morgoth.free.fr/files/morgoth-signkey.gpg.asc
deb http://morgoth.free.fr/ubuntu feisty-backports main
deb-src http://morgoth.free.fr/ubuntu feisty-backports main

    ## ATi & nVidia drivers Ubuntu packages
    ## GPG key: http://albertomilone.com/drivers/tseliot.asc
deb http://www.albertomilone.com/drivers/feisty/latest/32bit binary/

    # Automatix repository (GPG key: E23C5FC3)
deb http://www.getautomatix.com/apt feisty main

    # edevelop - e17 (Enlightenment DR 17)
    # GPG key: http://lut1n.ifrance.com/repo_key.asc
deb http://edevelop.org/pkg-e/ubuntu feisty e17
deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
deb http://e17.dunnewind.net/ubuntu feisty e17
deb-src http://e17.dunnewind.net/ubuntu feisty e17

    # Musicbrainz Repository
    # GPG key-file: http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key
deb http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu feisty musicbrainz
deb-src http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu feisty musicbrainz

    ## Imbrandons software repository (GPG key: 887D9FD2)
    ## GPG key-file: http://www.imbrandon.com/packages/887D9FD2.gpg
deb http://www.imbrandon.com/packages feisty all
deb-src http://www.imbrandon.com/packages feisty all

    ## Candyz&#8217;s Ubuntu Packages
    ## GPG key-file: http://cle.linux.org.tw/candyz/Ubuntu/candyz.key
deb http://cle.linux.org.tw/candyz/Ubuntu/feisty i386/

    # The Ubuntu NLP Repository (GPG key: 8ABD1965)
    # GPG key-file: http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg
deb http://cl.naist.jp/~eric-n/ubuntu-nlp feisty all
deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp feisty all

    # Ubuntu System Administrator packages (GPG key: 2F306651)
    # GPG key-file: http://ubuntu.moshen.de/2F306651.gpg
deb http://ubuntu.moshen.de feisty multimedia misc
deb-src http://ubuntu.moshen.de feisty multimedia misc

    ## Michael Biebl Tracker Repository (GPG key: BD058554)
    ## GPG Key-file: http://www.teco.edu/~biebl/biebl.asc
deb http://debs.michaelbiebl.de/ feisty main
deb-src http://debs.michaelbiebl.de/ feisty main

    # The Consciousness Repository (GPG key: DD385D79)
    # GPG key-file: http://debs.peadrop.com/DD385D79.gpg
deb http://debs.peadrop.com feisty all
deb-src http://debs.peadrop.com feisty all

    ## Tolero Ubuntu Repository
deb http://ubuntu.tolero.org/ feisty main
deb-src http://ubuntu.tolero.org/ feisty main

    # IVTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
    # GPG key-file: http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg
deb http://dl.ivtvdriver.org/ubuntu feisty all
deb-src http://dl.ivtvdriver.org/ubuntu feisty all

    # syzygy42 repository: avant-window-navigator, exaile, closure&#8230; (GPG key: 8434D43A)
    # GPG key-file: http://download.tuxfamily.org/syzygy42/8434D43A.gpg
deb http://download.tuxfamily.org/syzygy42/ feisty all
deb-src http://download.tuxfamily.org/syzygy42/ feisty all

    ## Firefox 3.0 alpha builds for feisty (unstable)
deb http://gnomefreak.youmortals.com/mozilla-testing feisty main
deb-src http://gnomefreak.youmortals.com/mozilla-testing feisty main

    ## Swiftfox (enhanced Firefox for linux) packages
deb http://getswiftfox.com/builds/debian unstable non-free

    # Sonnes repository (aMule AdunanZa, Audacious)
deb http://adurepo.altervista.org/ubuntu feisty all
deb-src http://adurepo.altervista.org/ubuntu feisty all

    # FoLKeN &#8216;Repozytorium&#8217; (GPG key: 6FB65A0F)
deb http://deb.svx.pl/ feisty main universe bleeding
deb-src http://deb.svx.pl/ feisty main universe bleeding

    # Le dépomaniak repository (GPG key: 1D59E694)
    # GPG key-file: http://ubuntu.davromaniak.eu/1D59E694.gpg
deb http://ubuntu.davromaniak.eu feisty-depomaniak all
deb-src http://ubuntu.davromaniak.eu feisty-depomaniak all

    # Mez&#8217;s Repository (GPG key: 6AAAA569)
    # GPG key-file: http://apt.sourceguru.net/6AAAA569.gpg
deb http://apt.sourceguru.net feisty all
deb-src http://apt.sourceguru.net feisty all

    # Ryan Kavanagh&#8217;s packages (GPG key: 02544D0E)
    # GPG key-file: http://packages.ryanak.ca/02544D0E.gpg
deb http://packages.ryanak.ca ryan-feisty all
deb-src http://packages.ryanak.ca ryan-feisty all

    # OpenedHand Debian/Ubuntu Packages
deb http://debian.o-hand.com feisty/
deb-src http://debian.o-hand.com feisty/

    # OpenSync svn ubuntu repository (GPG key: B029CB84)
deb http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main
deb-src http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main

    # Iuculano&#8217;s debian packages (GPG key: AE3BE9AA)
    # GPG key-file: http://ubuntu.iuculano.it/AE3BE9AA.gpg
deb http://ubuntu.iuculano.it feisty amsn thunderbird #ck-kernel #all
deb-src http://ubuntu.iuculano.it feisty amsn thunderbird #ck-kernel #all

    # Treviño&#8217;s Ubuntu Feisty Fawn Repository (GPG key: 81836EBF - DD800CD9)
    # Many "random" bleeding edge software: aMule, aMSN, Mercury, flash&#8230;
    # Further informations and complete packages list: http://3v1n0.tuxfamily.org
deb http://download.tuxfamily.org/3v1deb feisty 3v1n0
deb-src http://download.tuxfamily.org/3v1deb feisty 3v1n0

    # Treviño&#8217;s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
    # Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
    # built using latest available (working) sources from git/svn/cvs&#8230;
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

    ## Treviño&#8217;s Ubuntu Suspend2 patched kernels Repository (GPG key: 81836EBF - DD800CD9)
    ## Ubuntu kernels patched with Suspend2 plus other related tools www.suspend2.net
    ## Warning: they will replace standard ubuntu kernel related packages
deb http://download.tuxfamily.org/3v1deb feisty suspend2
deb-src http://download.tuxfamily.org/3v1deb feisty suspend2

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://packages.dfreer.org feisty main

deb http://www.virtualbox.org/debian feisty non-free 
```

---

### Post by skymera on 2007-06-16
no one knows?

---

### Post by kane77 on 2007-06-16
> **skymera said:**
> no one knows?

did you read what it says in comments?
```
 # If you get errors about missing keys, lookup the key in this file
    # and run these commands (replace KEY with the key number):
    #
    #  gpg --keyserver subkeys.pgp.net --recv KEY
    #  gpg --export --armor KEY | sudo apt-key add -
    #
    # If you have a gpg key URL use (replace URL with the key address):
    #
    #  wget URL --quiet -O - | sudo apt-key add -
    #
    # If you have a gpg key file use (replace FILE with the key file):
    #
    #  sudo apt-key add FILE

```

---

### Post by skymera on 2007-06-16
ermmmm. doh

---

### Post by egui on 2007-06-23
are there any places we could get a key url or file instead of having to install all the keys by hand? or a way to generate a key file using the info from the errors? thanks! :p

---

### Post by MorphWVUtuba on 2007-06-26
Howdy folks.  I've got something that you may find useful.

I've unfortunately had some hardware problems and had to switch hard drives around a lot in the last couple months.  It gets really tedious to re-certify all my apt repositories one by one, over and over again.  Even if I copy/paste and then use the command history function (the 'up' arrow key) it was getting to be a pain.

SO.  A couple Google searches on bash scripting and I've come up with this.  All I have to do is get these two files from a network share or a USB key, and two commands later I've got all my sources restored and certified.

You start with your sources.list, and here's mine:

```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu/ feisty universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://mirror2.ubuntulinux.nl/ feisty-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

# Kubuntu.org bleeding edge KDE
# GPG key: DD4D5088
deb http://kubuntu.org/packages/kde-356 edgy main

# Kubuntu.org bleeding edge amaroK
# GPG key: DD4D5088
deb http://kubuntu.org/packages/amarok-145 edgy main

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free

# Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu feisty-commercial main

# Debuntu.org Repository
deb http://repository.debuntu.org/ feisty multiverse

## System76 Driver Repository
deb http://planet76.com/repositories/ ./

# UbuntuStudio Repository (GPG key: B6A4EB33)
deb http://archive.ubuntustudio.org/ubuntustudio feisty main

#AUTOMATIX
deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START
deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

```

Feel free to use this sources.list on your machine.  Back yours up first!

```
# sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

Next use sudo to create a file using gedit or your text editor of choice.  I gave it a rather simple name, "sourcescript."  Again, this is free(dom) software, you can use whatever you want!

```
# sudo gedit /home/dew/sourcescript 
```

For the above source.list file, paste the following code into the file:

```

#!/bin/bash
# This script will add public keys for extra repositories in sources file.
# Check if the script is being run as root exit if it is not.
if [ "$UID" -ne "0" ]
then
  echo "[ERROR] This script must be run as root"
  exit 1
fi
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 437d05b5
gpg --export --armor 437d05b5 | sudo apt-key add -
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 1135d466
gpg --export --armor 1135d466 | sudo apt-key add -
gpg --keyserver hkp://subkeys.pgp.net --recv-keys dd4d5088
gpg --export --armor dd4d5088 | sudo apt-key add -
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
wget http://repository.debuntu.org/GPG-Key-chantra.txt -O- | sudo apt-key add - 
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add -
wget http://www.getautomatix.com/keys/automatix2.key
gpg --import automatix2.key
gpg --export --armor E23C5FC3 | sudo apt-key add -
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
exit 0

```

Note:  This script can be easily modified to suit whatever sources you may have.  just add another "gpg --keyserver..." and "gpg --export..." line into your script file with the appropriate hex key, or remove the lines for repositories you don't use.

Next, change the permissions so the file is executable.

```
# sudo chmod +x /home/dew/sourcescript 
```

Last step!  Run it!

```
# sudo /home/dew/sourcescript 
```

Bam!  If you got it right, there should be no more error messages when you run apt-get update.

HTH :D

Achieve MAXIMUM Rock!

---

### Post by skymera on 2007-06-27
wow thats a nice tool.
thanks

---

### Post by MorphWVUtuba on 2007-06-27
You're quite welcome.

I've got another little tip you can add to this file if you wish.  Add the following line right above the "exit" line:

```
# sudo apt-get update
```

This will make this script automatically update after it adds the keys.

---

