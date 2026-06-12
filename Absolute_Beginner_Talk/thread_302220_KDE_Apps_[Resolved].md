---
title: "KDE Apps [Resolved]"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-18
I wanted to have multiple sessins and be able to use KDA.  I accidentally installed the full version instead of the base.  How can I still have KDE but not all the extra apps that came with the full version.

---

### Post by slimdog360 on 2006-11-18
I dont think thats possible but maybe Im wrong. Maybe if you installed via aptitude you could get rid of kde and reinstall kde-core. Or otherwise use the guide on the psychocats webpage to get rid of it (or select parts of it).

---

### Post by LLRNR on 2006-11-18
Hmm I don't know how exactly you installed KDE, but surely slimdog360 is right, you could try Aysiu's handbook on [moving from Kubuntu to kde-core](http://www.psychocats.net/ubuntu/kde-core). See what fits you best.

Good luck!

LLRNR

---

### Post by aysiu on 2006-11-18
That *moving to kde-core* tutorial is for people who have *kubuntu* installed, not *kde*.

Try pasting this command into [the terminal](http://psychocats.net/ubuntu/terminal) instead: ```
sudo apt-get remove amor arts artsbuilder atlantik atlantikdesigner autoconf automake1.9 autotools-dev blinken cervisia comerr-dev cvs dcoprss dirmngr docbook-defguide edict eyesapplet fifteenapplet flac gawk gettext-kde gnupg-agent gnupg2 gpgsm hspell juk kaboodle kaddressbook-plugins kalarm kalzium kalzium-data kanagram kandy kanjidic kappfinder karm kasteroids kate kate-plugins katomic kaudiocreator kbackgammon kbattleship kblackbox kbounce kbruch kbstate kcalc kcharselect kcoloredit kcron kdat kde kde-amusements kde-core kde-icons-mono kdeaccessibility kdeaddons kdeaddons-kfile-plugins kdeadmin kdeadmin-kfile-plugins kdeartwork kdeartwork-emoticons kdeartwork-misc kdeartwork-style kdeartwork-theme-icon kdeartwork-theme-window kdebase kdeedu kdeedu-data kdegames kdegames-card-data kdegraphics kdegraphics-kfile-plugins kdelibs kdelibs4-dev kdelirc kdemultimedia kdemultimedia-dev kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdenetwork kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim kdepim-kfile-plugins kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesdk-scripts kdessh kdetoys kdeutils kdewallpapers kdewebdev kdf kdict kdm kdnssd kdvi kedit keduca kenolaba kfax kfaxview kfilereplace kfloppy kfouleggs kgamma kget kghostview kgoldrunner kgpg khangman khelpcenter khexedit kicker-applets kiconedit kig kimagemapeditor kitchensync kiten kjots kjumpingcube klaptopdaemon klatin kleopatra klettres klettres-data klickety klines klinkstatus kmag kmahjongg kmail kmailcvt kmenuedit kmid kmilo kmines kmix kmoon kmousetool kmouth kmplot kmrml knetwalk knetworkconf knewsticker knewsticker-scripts knode knotes kodo kolf kommander kompare konqueror-nsplugins konquest konsolekalendar kontact kooka kopete korganizer korn kpackage kpager kpat kpdf kpercentage kpersonalizer kpf kpilot kpoker kpovmodeler kppp krdc krec kregexpeditor kreversi krfb kruler ksame ksayit kscd kscreensaver kscreensaver-xsavers kshisen ksig ksim ksirc ksirtet ksmiletris ksmserver ksnake ksnapshot ksokoban kspaceduel ksplash kstars kstars-data ksvg ksync ksysguard ksysguardd ksysv ktalkd kteatime ktimer ktip ktnef ktouch ktron kttsd ktuberling kturtle ktux kuser kverbos kview kviewshell kvoctrain kwalletmanager kweather kwifimanager kwin4 kwordquiz kworldclock kxsldbg libacl1-dev libart-2.0-dev libarts1-audiofile libarts1-dev libarts1-mpeglib libarts1-xine libartsc0-dev libasound2-dev libaspell-dev libattr1-dev libaudio-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-compat-libdnssd1 libavahi-qt3-dev libbeecrypt6 libboost-python1.33.1 libbz2-dev libc6-dev libconvert-binhex-perl libcupsys2-dev libcvsservice0 libdb4.3++c2 libdbus-1-dev libesd0-dev libexpat1-dev libfinance-quote-perl libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libgmp3c2 libgnutls-dev libgpg-error-dev libhtml-tableextract-perl libice-dev libidn11-dev libindex0 libio-socket-ssl-perl libio-stringy-perl libjasper-1.701-dev libjasper-runtime libjpeg62-dev libkadm55 libkdeedu3 libkdegames1 libkgantt0 libkiten1 libkmime2 libkpimexchange1 libkpimidentities1 libkrb5-dev libksba8 libkscan1 libksieve0 liblcms1-dev liblockdev1 liblua50-dev liblualib50-dev liblzo-dev libmailtools-perl libmal1 libmime-perl libmimelib1c2a libmng-dev libnet-ssleay-perl libnews-nntpclient-perl libogg-dev libopencdk8-dev libopenexr-dev libpcre3-dev libpcrecpp0 libpng12-dev libpoppler1-qt libpopt-dev libpth20 libqt3-compat-headers libqt3-headers libqt3-mt-dev librpm4 librss1 libsasl2-dev libsm-dev libssl-dev libt1-5 libtasn1-3-dev libtidy-0.99-0 libtiff-tools libtiff4-dev libtiffxx0c2 libtimedate-perl libtunepimp-bin libtunepimp3 libvorbis-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxine-extracodecs libxine1 libxinerama-dev libxml2-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxslt1-dev libxt-dev lilo-config linux-libc-dev lisa lskat lua50 m4 mesa-common-dev mpeglib networkstatus noatun noatun-plugins ocrad perl-tk php-doc phpdoc pinentry-curses pinentry-qt poster postfix procmail psutils qca-tls qt3-dev-tools quanta quanta-data rpm secpolicy superkaramba talk tetex-base tetex-bin tetex-doc tex-common tidy ttf-dustin ttf-sjfonts x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev ytalk zlib1g-dev
```

---

### Post by LLRNR on 2006-11-18
Whoops... mea culpa :oops: I'm sorry.

---

### Post by gentlemanmasher on 2006-11-18
> **aysiu said:**
> That *moving to kde-core* tutorial is for people who have *kubuntu* installed, not *kde*.

Try pasting this command into [the terminal](http://psychocats.net/ubuntu/terminal) instead: ```
sudo apt-get remove amor arts artsbuilder atlantik atlantikdesigner autoconf automake1.9 autotools-dev blinken cervisia comerr-dev cvs dcoprss dirmngr docbook-defguide edict eyesapplet fifteenapplet flac gawk gettext-kde gnupg-agent gnupg2 gpgsm hspell juk kaboodle kaddressbook-plugins kalarm kalzium kalzium-data kanagram kandy kanjidic kappfinder karm kasteroids kate kate-plugins katomic kaudiocreator kbackgammon kbattleship kblackbox kbounce kbruch kbstate kcalc kcharselect kcoloredit kcron kdat kde kde-amusements kde-core kde-icons-mono kdeaccessibility kdeaddons kdeaddons-kfile-plugins kdeadmin kdeadmin-kfile-plugins kdeartwork kdeartwork-emoticons kdeartwork-misc kdeartwork-style kdeartwork-theme-icon kdeartwork-theme-window kdebase kdeedu kdeedu-data kdegames kdegames-card-data kdegraphics kdegraphics-kfile-plugins kdelibs kdelibs4-dev kdelirc kdemultimedia kdemultimedia-dev kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdenetwork kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim kdepim-kfile-plugins kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesdk-scripts kdessh kdetoys kdeutils kdewallpapers kdewebdev kdf kdict kdm kdnssd kdvi kedit keduca kenolaba kfax kfaxview kfilereplace kfloppy kfouleggs kgamma kget kghostview kgoldrunner kgpg khangman khelpcenter khexedit kicker-applets kiconedit kig kimagemapeditor kitchensync kiten kjots kjumpingcube klaptopdaemon klatin kleopatra klettres klettres-data klickety klines klinkstatus kmag kmahjongg kmail kmailcvt kmenuedit kmid kmilo kmines kmix kmoon kmousetool kmouth kmplot kmrml knetwalk knetworkconf knewsticker knewsticker-scripts knode knotes kodo kolf kommander kompare konqueror-nsplugins konquest konsolekalendar kontact kooka kopete korganizer korn kpackage kpager kpat kpdf kpercentage kpersonalizer kpf kpilot kpoker kpovmodeler kppp krdc krec kregexpeditor kreversi krfb kruler ksame ksayit kscd kscreensaver kscreensaver-xsavers kshisen ksig ksim ksirc ksirtet ksmiletris ksmserver ksnake ksnapshot ksokoban kspaceduel ksplash kstars kstars-data ksvg ksync ksysguard ksysguardd ksysv ktalkd kteatime ktimer ktip ktnef ktouch ktron kttsd ktuberling kturtle ktux kuser kverbos kview kviewshell kvoctrain kwalletmanager kweather kwifimanager kwin4 kwordquiz kworldclock kxsldbg libacl1-dev libart-2.0-dev libarts1-audiofile libarts1-dev libarts1-mpeglib libarts1-xine libartsc0-dev libasound2-dev libaspell-dev libattr1-dev libaudio-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-compat-libdnssd1 libavahi-qt3-dev libbeecrypt6 libboost-python1.33.1 libbz2-dev libc6-dev libconvert-binhex-perl libcupsys2-dev libcvsservice0 libdb4.3++c2 libdbus-1-dev libesd0-dev libexpat1-dev libfinance-quote-perl libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libgmp3c2 libgnutls-dev libgpg-error-dev libhtml-tableextract-perl libice-dev libidn11-dev libindex0 libio-socket-ssl-perl libio-stringy-perl libjasper-1.701-dev libjasper-runtime libjpeg62-dev libkadm55 libkdeedu3 libkdegames1 libkgantt0 libkiten1 libkmime2 libkpimexchange1 libkpimidentities1 libkrb5-dev libksba8 libkscan1 libksieve0 liblcms1-dev liblockdev1 liblua50-dev liblualib50-dev liblzo-dev libmailtools-perl libmal1 libmime-perl libmimelib1c2a libmng-dev libnet-ssleay-perl libnews-nntpclient-perl libogg-dev libopencdk8-dev libopenexr-dev libpcre3-dev libpcrecpp0 libpng12-dev libpoppler1-qt libpopt-dev libpth20 libqt3-compat-headers libqt3-headers libqt3-mt-dev librpm4 librss1 libsasl2-dev libsm-dev libssl-dev libt1-5 libtasn1-3-dev libtidy-0.99-0 libtiff-tools libtiff4-dev libtiffxx0c2 libtimedate-perl libtunepimp-bin libtunepimp3 libvorbis-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxine-extracodecs libxine1 libxinerama-dev libxml2-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxslt1-dev libxt-dev lilo-config linux-libc-dev lisa lskat lua50 m4 mesa-common-dev mpeglib networkstatus noatun noatun-plugins ocrad perl-tk php-doc phpdoc pinentry-curses pinentry-qt poster postfix procmail psutils qca-tls qt3-dev-tools quanta quanta-data rpm secpolicy superkaramba talk tetex-base tetex-bin tetex-doc tex-common tidy ttf-dustin ttf-sjfonts x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev ytalk zlib1g-dev
```

For some reason my login screen is one from KDE theme manager?  Not sure how it happened.  Will posting this command take anything away from the theme mananger?  I had trouble ending sessions when it wasn't run by KDE not sure why.

---

### Post by aysiu on 2006-11-18
> **LLRNR said:**
> Whoops... mea culpa :oops: I'm sorry.
No problem. I happen to like a lot that tutorial you linked to. Just doesn't apply to this particular situation.

---

### Post by wilberfan on 2006-11-18
So many acronyms!!!  How is KDE different from Kubuntu?  Does kubunutu USE KDE?   What IS KDE??

---

### Post by aysiu on 2006-11-18
> **wilberfan said:**
> So many acronyms!!!  How is KDE different from Kubuntu?  Does kubunutu USE KDE?   What IS KDE??
KDE stands for K Desktop Environment. I don't think the *K* itself stands for anything. It offers a full... environment for you to point-and-click in. It controls the way windows and panels look and behave. It controls your desktop wallpaper and your screensaver. It gives you tools to customize your system.

There are several different metapackages (pointers to a collection of real packages) in Ubuntu that all install KDE with different bundles of software.

**In order from small to large**
*kdebase* is the most minimal, installing only the K Desktop Environment and very few extra tools or applications.

*kde-core* is fairly minimal but gives you at least some productivity tools.

*kubuntu-desktop* gives you a minimal but full working environment--this is Ubuntu's default KDE setup.

*kde* is pretty much all the KDE-related applications and tools.

I would advise [using *kde-core* instead of *kubuntu-desktop*](http://www.psychocats.net/ubuntu/kde-core). It's faster and leaner. You will undoubtedly have to install a few more applications on top of it, but that's pretty easy to do.

---

### Post by LLRNR on 2006-11-18
You can take a look [here](http://en.wikipedia.org/wiki/Desktop_environment) for other desktop environments.

---

### Post by wilberfan on 2006-11-18
> **aysiu said:**
> I would advise [using *kde-core* instead of *kubuntu-desktop*](http://www.psychocats.net/ubuntu/kde-core). It's faster and leaner. You will undoubtedly have to install a few more applications on top of it, but that's pretty easy to do.

What applications, for example, would be necessary to install in the leaner version?  I'm curious which ones you're thinking of...    

There's a fairly simple way to remove the full kubuntu-desktop and go with just the core, yes?   Or is there just some packages that can get removed from the full desktop version?

I DO like the idea of having a leaner system in place and just adding what I need!

---

### Post by aysiu on 2006-11-18
> **wilberfan said:**
> What applications, for example, would be necessary to install in the leaner version?  I'm curious which ones you're thinking of...     Well, that all depends on your needs. For example, some people like to install Amarok (that doesn't come standard on *kde-core*), but maybe you prefer XMMS or JuK or... don't listen to music at all.

> 
There's a fairly simple way to remove the full kubuntu-desktop and go with just the core, yes?   Or is there just some packages that can get removed from the full desktop version? Yes, I linked to it in my last post.

> 
I DO like the idea of having a leaner system in place and just adding what I need! So do a lot of us. Read [this thread](http://ubuntuforums.org/showthread.php?t=277090) for more details.

---

### Post by wilberfan on 2006-11-18
Is the core version still faster in Edgy?   Or was it just a Dapper issue?

---

### Post by aysiu on 2006-11-18
> **wilberfan said:**
> Is the core version still faster in Edgy?   Or was it just a Dapper issue?
I don't know. Since I gave up *kubuntu-desktop* in Dapper, I haven't looked back. So I haven't done any benchmarks in Edgy yet.

---

### Post by gentlemanmasher on 2006-11-18
By the way the comman you gave me worked perfectly.  How do I set my posts as resolved.

---

