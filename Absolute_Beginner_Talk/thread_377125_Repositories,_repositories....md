---
title: "Repositories, repositories..."
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by dosmode on 2007-03-05
I am thinking about adding new repositories to my sources list and there seem to be many out there... Mine currently looks like this: 
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://bz.archive.ubuntu.com/ubuntu/](http://bz.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bz.archive.ubuntu.com/ubuntu/](http://bz.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://bz.archive.ubuntu.com/ubuntu/](http://bz.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

I found these repositories here: [http://3v1n0.tuxfamily.org/blog/informatica/linux/lista-repository-sourceslist-per-ubuntu-kubuntu-dapper-archivio/](http://3v1n0.tuxfamily.org/blog/informatica/linux/lista-repository-sourceslist-per-ubuntu-kubuntu-dapper-archivio/)

    > # Treviño&#8217;s Ubuntu Dapper Sources list
    # [http://italy.copybase.ch/blog/?page_id=13](http://italy.copybase.ch/blog/?page_id=13)
    #
    # Based on source-o-matic ([http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)) list
    # Added extra repository
    #
    # If you get errors about missing keys, lookup the key in this file
    # and run these commands (replace KEY with the key number)
    #
    # gpg &#8211;keyserver subkeys.pgp.net &#8211;recv KEY
    # gpg &#8211;export &#8211;armor KEY | sudo apt-key add -

    # Ubuntu supported packages (packages, GPG key: 437D05B5)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

    # Ubuntu community supported packages (packages, GPG key: 437D05B5)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

    # Ubuntu backports project (packages, GPG key: 437D05B5)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
     
    # CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
    # RealPlayer10, Opera and more to come.)
    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

    # Seveas&#8217; packages (packages, GPG key: 1135D466)
    deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all
    deb-src [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas all

    ## Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
    #deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
    #deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

    # kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
    deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main
    deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main
    deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

    # kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
    deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main
    deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main

    # kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
    deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main
    deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

    # Bleeding edge wine packages (packages)
    deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
    deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

    # The Opera browser (packages)
    deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

    # Penguin Liberation Front (packages)
    deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
    deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

    ## archive.kubuntu.de / archive.czessi.net
    # The repository from Kubuntu Germany
    # wget [http://archive.czessi.net/ubuntu/kczessi.gpg](http://archive.czessi.net/ubuntu/kczessi.gpg)
    # sudo apt-key add kczessi.gpg
    deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) dapper main restricted universe multiverse preview
    deb-src [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) dapper main restricted universe multiverse preview

    # E-Yagi Consulting Community Repository (GPG: 4B6E7209)
    deb [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) dapper main restricted universe multiverse
    deb-src [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) dapper main restricted universe multiverse

    # Dev not-public (Breezy Packages)
    deb [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free
    deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free

    # Achim&#8217;s Unofficial &#8216;dapper&#8217; Kubuntu packages
    deb [http://www.mpe.mpg.de/~ach/kubuntu/dapper](http://www.mpe.mpg.de/~ach/kubuntu/dapper) ./
    deb-src [http://www.mpe.mpg.de/~ach/kubuntu/dapper](http://www.mpe.mpg.de/~ach/kubuntu/dapper) ./

    # Ubuntu Taiwan ubuntu extra repository
    deb [http://apt.ubuntu.org.tw](http://apt.ubuntu.org.tw) ubtw/
    deb [http://apt.ubuntu.org.tw](http://apt.ubuntu.org.tw) ubtw-testing/

    # Ubuntu dapper University Klagenfurt packages
    # $ wget [http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub](http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub)
    # $ sudo apt-key add uniklu-debuild.pub
    # uniklu: backports and new packages
    # uniklu-desktop: packages for uniklu desktop
    # uniklu-intern: not freely redistributable (jvm), or modified packages
    # uniklu-nfsv4: nfsv4 kernel and packages
    # uniklu-vserver: vserver kernel
    # uniklu-testing: packages not ready for general use !
    deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu
    deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-desktop
    deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-intern
    deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-nfsv4
    deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-vserver
    deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-testing
    deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu
    deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-desktop
    deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-intern
    deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-nfsv4
    deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-vserver
    deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-testing

    # VoIP Ubuntu packages (Asterisk, ekiga, kphone&#8230;)
    deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) dapper main

    # VLC nightlies
    deb [http://nightlies.videolan.org/build/dapper-i386](http://nightlies.videolan.org/build/dapper-i386) /

    # # MaXeR (KDE Apps)
    # # deb [http://repos.knio.it/](http://repos.knio.it/) sarge main contrib non-free
    # # deb-src [http://repos.knio.it/](http://repos.knio.it/) sarge main contrib non-free
    # deb [http://repos.knio.it/](http://repos.knio.it/) breezy main contrib non-free
    # deb-src [http://repos.knio.it/](http://repos.knio.it/) breezy main contrib non-free

    # Quinn&#8217;s Compiz Packages - [http://xgl.compiz.info/](http://xgl.compiz.info/)
    deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
    deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
    deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
     
    ## Subpixel Font rendering packages
    #deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper fonts
    #deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper fonts

    # Skype packages
    deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

    # Easycam packages
    deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

    # Audacious
    deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious
    deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious

    # Listen
    deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

    # Geole&#8217;s Ubuntu Repository
    # wget [http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg](http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg)
    # sudo apt-key add geole-apt-key.gpg
    deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) dapper universe multiverse

    # Samba
    deb [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) dapper main
    deb-src [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) dapper main

    # GCompris, Televidilo, Kdocker,&#8230;
    deb [http://thomas.enix.org/pub/debian/packages/](http://thomas.enix.org/pub/debian/packages/) dapper main

    # Asher256&#8217;s Repository
    deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) breezy main dupdate french
    deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

    # Gauvain Repository
    deb [http://gauvain.tuxfamily.org/repos](http://gauvain.tuxfamily.org/repos) dapper contrib
    deb-src [http://gauvain.tuxfamily.org/repos](http://gauvain.tuxfamily.org/repos) dapper contrib

    # Tvfreeplayer Packages
    deb [http://www.tvfreeplayer.com/linux/ubuntu/dapper/](http://www.tvfreeplayer.com/linux/ubuntu/dapper/) unstable main

    # gnomemeeting - ekiga (GPG key: 52ABFCB1)
    deb [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) dapper main
    deb-src [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) dapper main
    #deb [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) dapper main
    #deb-src [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) dapper main

    # seb128 repository (gaim - rhythmbox)
    deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
    deb-src [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

    # lprod packages: many audio/video apps: avidemux, cinelerra&#8230;
    deb [http://lprod.org/deb/dapper/](http://lprod.org/deb/dapper/) ./
    deb-src [http://lprod.org/deb/dapper/](http://lprod.org/deb/dapper/) ./

    # Mjpegtools and Cinelerra packages (choose your arch)
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
    #deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./
    #deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./
    deb-src [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
    #deb-src [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./
    #deb-src [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./

    # LiVes dapper package
    deb [http://people.ubuntubrasil.org/~rclbelem/lives/dapper/](http://people.ubuntubrasil.org/~rclbelem/lives/dapper/) ./binary/

    # A little too quiet
    deb [http://apt.alittletooquiet.net/staging](http://apt.alittletooquiet.net/staging) dapper main

    # MythTV packages
    deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
    deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main

    ## SimplyMepis packages (distro based on k-ubuntu) but different kernel
    # deb [http://apt.mepis.org/6.0/](http://apt.mepis.org/6.0/) mepis main

    # Cafuego&#8217;s Dapper Stuff: Broadcom kernel firmwares, google-earth, beagle&#8230; (GPG key: 969F3F57)
    deb [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) dapper-cafuego all bcm43xx
    deb-src [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) dapper-cafuego all bcm43xx

    ## Ubuntu Dapper Sw-Suspend2 repository - warning: new patched kernel
    # deb [http://dagobah.ucc.asn.au/ubuntu-suspend2](http://dagobah.ucc.asn.au/ubuntu-suspend2) dapper/

    # Debuntu Ubuntu dapper packages
    # GPG Key-flie: wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt)
    deb [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse
    deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse

    # BMPx Dapper Repository
    # GPG key-file: [http://files.beep-media-player.org/packages/bmp-packages.pubkey](http://files.beep-media-player.org/packages/bmp-packages.pubkey)
    deb [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) dapper main universe
    deb [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/) dapper/
    deb-src [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) dapper main universe

    # Morgoth Repository (Monkey&#8217;s Audio, xmms pugins, vlc plugins, gqview, audacity&#8230;)
    # GPG key: [http://morgoth.free.fr/ubports/dlsignkey.php](http://morgoth.free.fr/ubports/dlsignkey.php) (7E2E4741)
    deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) dapper-backports main
    deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) dapper-backports main

    # ATi & nVidia drivers Ubuntu packages
    deb [http://www.albertomilone.com/drivers/dapper/legacy/32bit](http://www.albertomilone.com/drivers/dapper/legacy/32bit) binary/

    # Givre&#8217;s repository (ntfs-3g & fuse 2.5.3) - NTFS writing support
    deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main
    deb-src [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main

    # debian.wgdd.de Ubuntu Repository (GPG key: E394D996)
    deb [http://debian.wgdd.de/ubuntu](http://debian.wgdd.de/ubuntu) dapper universe
    deb-src [http://debian.wgdd.de/ubuntu](http://debian.wgdd.de/ubuntu) dapper universe

    # Automatix
    # wget [http://www.beerorkid.com/automatix/apt/key.gpg.asc](http://www.beerorkid.com/automatix/apt/key.gpg.asc)
    deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

    # Jahshaka
    deb [http://repo.jahshaka.org/ubuntu/dapper](http://repo.jahshaka.org/ubuntu/dapper) binary-i386/

    # SoS: SeerOfSouls
    # wget [http://seerofsouls.com/keys/hawkwind.asc](http://seerofsouls.com/keys/hawkwind.asc)
    deb [http://SeerOfSouls.com/](http://SeerOfSouls.com/) dapper e17 contrib
    deb-src [http://SeerOfSouls.com/](http://SeerOfSouls.com/) dapper contrib #e17

    # Spring
    deb [ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/](ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/) /
    deb-src [ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/](ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/) /

    ## aMule adunanza (fastweb) repository
    #deb [http://amule-adunanza.marleylandia.com/ubuntu/adu3.11b](http://amule-adunanza.marleylandia.com/ubuntu/adu3.11b) dapper/

    # Picard
    deb [http://users.musicbrainz.org/~luks/ubuntu](http://users.musicbrainz.org/~luks/ubuntu) dapper main

    # Treviño&#8217;s Ubuntu Dapper Repository (GPG key: 81836EBF)
    # Many &#8220;random&#8221; software: aMule, amsn, gnash, google-earth, stellarium, moto4lin&#8230;
    # Further informations: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)
    deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0

Comments, suggestions anyone...  

I am not too sure about the code of ethics on posts such as these that seem abnormally lengthy and I am open to being educated on this... thanks...

---

### Post by r4ik on 2007-03-05
Impressive list i would not want to have it.
Anything special you want ?

---

### Post by PriceChild on 2007-03-05
Please be extremely aware at the dangers you face in adding 3rd party repositories.

There is an example on this forum where a repository maintainer got annoyed at his repo being listed on a certain page, and with users being encouraged to add it despite them not specifically knowing what it did. He got annoyed because **untrusted maintainers could upload VERY dangerous packages. **He promptly confirmed this by uploading packages to his repositories which broke sudo... and gave a little "warning" on the desktop to teach people not to use 3rd party repositories they can't trust.

Having a HUGE sources.list does not make you big or clever.

Here is my list:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://ubuntu.beryl-project.org feisty main
```The final line on that list is a repository that I maintain... 'nuf said ;)

---

### Post by dosmode on 2007-03-05
Thanks Pricechild... that seem like just the list I needed.. :guitar: 

r4ik, I did not need any particular software... just that I am dipping my feet in the waters of Ubuntu and thought that it seems not to be a minor detail to have a "proper" one.... at the moment I am installing software as I am going along on an as needed basis...
At the moment I am looking at the list as given by "Thirteen things to do after you install Ubuntu" and using from there as I need....
Thanks all...

---

### Post by r4ik on 2007-03-05
Okidoki

---

### Post by FXWGBill on 2007-03-14
yeah.. I was gonna say.  I had a look at that list a while back and did a little research.  Some on the list are private repositories and most of the folks were not asked if it was ok to include them...  In fact, one individual got really upset with them and forced a set of desktop wallpapers etc on folks for about three days that had a skull and cross bones on it and stated that it was very dangerous to use rogue repository lists....  Countless people got VERY upset with the man, but as I said, he wasn't asked if it was ok that he be in that list...  carefullllllll

My List:

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

#### Main ####
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
########
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

#### Proposed Multiverse ####
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed main restricted universe multiverse


## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

######################################
#### Unofficial/Unsupported Repos ####
######################################

## Listen
##deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) feisty listen

## Automatix repo
##deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

## Official Skype Repository
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

##Google Picasa for Linux repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

##deb [http://albertomilone.com/drivers/edgy/nonlegacy/32bit](http://albertomilone.com/drivers/edgy/nonlegacy/32bit) binary/


#### Multimedia Codecs ####
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

---

### Post by maniacmusician on 2007-03-14
> **dosmode said:**
> Thanks Pricechild... that seem like just the list I needed.. :guitar: 

r4ik, I did not need any particular software... just that I am dipping my feet in the waters of Ubuntu and thought that it seems not to be a minor detail to have a "proper" one.... at the moment I am installing software as I am going along on an as needed basis...
At the moment I am looking at the list as given by "Thirteen things to do after you install Ubuntu" and using from there as I need....
Thanks all...
you probably shouldn't use that list.

Pricey is on Feisty Fawn. You are on Edgy Eft. The list you have right now is perfectly fine.

You should only add more repos when you need something that isn't in the default repos.

---

### Post by PriceChild on 2007-03-14
Whoops should have mentioned that maniac...

---

