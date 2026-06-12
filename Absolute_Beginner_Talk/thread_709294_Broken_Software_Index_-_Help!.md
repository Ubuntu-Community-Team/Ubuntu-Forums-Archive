---
title: "Broken Software Index - Help!"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by matolo on 2008-02-27
Yesterday I attempted to install Citadel mailserver, and wouldn't you know it there was a power outage right smack dab in the middle of the install.  I brought things back up, and noticed that the update manager has popped up in the upper right side of my screen.  So, I clicked on it, and it ran for a second, then it told me the software index is broken, and to run sudo apt-get install -f to fix.

So, I ran it and here's what I got:

$ sudo apt-get install -f
[sudo] password for matolo:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  knetwalk kpat kpdf ksokoban kolf blinken kscreensaver-xsavers krdc krec korn
  krfb kscd kppp kshisen kmoon kmahjongg klaptopdaemon ksig ksim libkscan1
  kwifimanager kcharselect kjumpingcube kdeartwork-style kdeartwork-misc
  kcoloredit artsbuilder kdessh kanagram knode kmrml katomic libcvsservice0
  kleopatra ksvg kdegames-card-data kscreensaver kruler exim4-config ktux
  klettres texlive-base kgoldrunner kbackgammon kpoker dirmngr
  kdepim-kfile-plugins libkiten1 texlive-fonts-recommended kgeography
  ksnapshot kpackage liblockdev1 kooka kenolaba kblackbox atlantikdesigner
  konsolekalendar klatin kfloppy kdegraphics-kfile-plugins kstars ttf-dustin
  trigger-data ksame kbruch kdepim-kio-plugins libkdegames1 kcalc
  texlive-common libmimelib1c2a keduca kdeedu-data
  kdemultimedia-kappfinder-data kontact kdeadmin-kfile-plugins
  kdeartwork-theme-icon kweather kmplot kalzium ksirc librss1 klinkstatus
  klickety kpovmodeler kmouth noatun-plugins kworldclock kalzium-data
  kdewebdev texlive-base-bin kdegames kicker-applets amor kdict ktouch
  kgeography-data ktnef khexedit kedit kbounce kvoctrain korganizer kdetoys
  kdenetwork-kfile-plugins kimagemapeditor atlantik kbstate tidy
libtidy-0.99-0 ri-li-data arts ark kwordquiz kcron kview ktron ttf-sjfonts
  kdenetwork libtiff-tools kdeartwork-emoticons dcoprss ksysv kwin4
  kdewallpapers libksieve0 kuser klettres-data kdeaddons kreversi kdf libksba8
  kspaceduel kig gnupg-agent kpf juk noatun kdnssd klines
  kdemultimedia-kfile-plugins fifteenapplet kdemultimedia kfaxview kstars-data
  edict lskat kaddressbook-plugins kgamma kviewshell kfilereplace kommander
  networkstatus kdeutils kdegraphics kaboodle khangman libkpimexchange1
  kmailcvt libindex0 kanjidic knetworkconf kdeartwork-theme-window ksmiletris
  konq-plugins libarts1-audiofile kxsldbg quanta kbattleship libpoppler-qt2
  kiconedit kdeadmin kpilot kasteroids kfouleggs libkdeedu3 libkgantt0
  kwalletmanager knewsticker kopete exim4-base ksnake kiten eyesapplet kdat
  indi kmail kdeedu kdelirc kpercentage superkaramba kjots kfax ksirtet
  libjpeg-progs kmines kdvi kget pinentry-qt texlive-doc-base kgpg konquest
  kate-plugins tex-common kolourpaint gnujump-data libboost-python1.34.1 gpgsm
  gnupg2 kmousetool kdeaddons-kfile-plugins libarts1-xine kmag
  kdepim-kresources kdepim-wizards kmilo ktuberling kturtle kaudiocreator
  ktimer quanta-data kmid kteatime kverbos kmix kdeartwork kodo
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsieve2-1
The following NEW packages will be installed:
  libsieve2-1
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0B/77.8kB of archives.
After unpacking 270kB of additional disk space will be used.
Do you want to continue [Y/n]? YES
(Reading database ... 199794 files and directories currently installed.)
Unpacking libsieve2-1 (from .../libsieve2-1_2.2.3-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsieve2-1_2.2.3-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libsieve.so.1', which is also in package libmailutils1
Errors were encountered while processing:
 /var/cache/apt/archives/libsieve2-1_2.2.3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
$

So, now I am stuck and I cannot install or remove any software.

Anyone have any idea how to resolve this?  Any input would be much appreciated.

Thanks!

MATOLO

---

### Post by SOULRiDER on 2008-02-27
The first thing you should do is run
```
sudo aptitude update
sudo aptitude dist-upgrade
```
That should do some package fixing. Lets see how it goes after that.

---

### Post by matolo on 2008-02-27
> **SOULRiDER said:**
> The first thing you should do is run
```
sudo aptitude update
sudo aptitude dist-upgrade
```
That should do some package fixing. Lets see how it goes after that.

Thanks SOULRiDER, I ran both commands, and received no errors.  But when I try to update, I get the same error.

---

### Post by xeth_delta on 2008-02-27
Try cleaning the apt cache
```
sudo apt-get clean
```

---

### Post by matolo on 2008-02-27
> **xeth_delta said:**
> Try cleaning the apt cache
```
sudo apt-get clean
```

Again, no errors, but no positive results either after running the suggested command.  Software Index remains broken....

---

### Post by oedha on 2008-02-27
what if :==> sudo dpkg --configure -a
then :==> sudo apt-get update

---

### Post by glennric on 2008-02-27
You are trying to install conflicting packages.  If all of these packages are in the default Ubuntu repositories, then this is a bug and you should report it.  If however you have added other sources, then you can try to report it to whoever is responsible for those sources.

The problem is that the packages libsieve2-1 and libmailutils1 have the same file in them.

---

### Post by asmoore82 on 2008-02-27
this is a sticky situation, but you could also try these:
```
sudo apt-cache check
sudo dpkg-reconfigure -a
```

---

### Post by ellalan on 2008-02-28
Hi
I am stuck as well, could any of you please help me.
I was trying to download limewire and halfway through it stoped and I closed it.
when I tried the synaptic package I got the Error:dpkg was interrupted, you must manually run 'dpkg--configure a'. I did that, when I went to remove the broken package another error is popping up  E:sun-java6-bin: Package in a very bad incinsistent state-you should
after that I am unable to read anything.
Could some one tell me what to do. Thank you.

---

### Post by matolo on 2008-02-28
> **oedha said:**
> what if :==> sudo dpkg --configure -a
then :==> sudo apt-get update

Well, I tried that, oedha, but at the end I got more errors:

$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of citadel-server:
 citadel-server depends on libsieve2-1; however:
  Package libsieve2-1 is not installed.
dpkg: error processing citadel-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of citadel-mta:
 citadel-mta depends on citadel-server; however:
  Package citadel-server is not configured yet.
dpkg: error processing citadel-mta (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsieve2-dev:
 libsieve2-dev depends on libsieve2-1 (= 2.2.3-1); however:
  Package libsieve2-1 is not installed.
dpkg: error processing libsieve2-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of citadel-suite:
 citadel-suite depends on citadel-server; however:
  Package citadel-server is not configured yet.
 citadel-suite depends on citadel-mta; however:
  Package citadel-mta is not configured yet.
dpkg: error processing citadel-suite (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 citadel-server
 citadel-mta
 libsieve2-dev
 citadel-suite
$

---

### Post by matolo on 2008-02-28
> **asmoore82 said:**
> this is a sticky situation, but you could also try these:
```
sudo apt-cache check
sudo dpkg-reconfigure -a
```

Hi asmoore.

Neither the check variable for apt-cache nor the -reconfigure variable for dpkg are available for me.

---

### Post by matolo on 2008-02-28
> **glennric said:**
> You are trying to install conflicting packages.  If all of these packages are in the default Ubuntu repositories, then this is a bug and you should report it.  If however you have added other sources, then you can try to report it to whoever is responsible for those sources.

The problem is that the packages libsieve2-1 and libmailutils1 have the same file in them.

Hmm, yes, the documentation to installing Citadel requires adding a repository to /etc/apt/sources.list (if I recall, it was something like, something like "deb [http://debian.citadel.org/ubuntu/](http://debian.citadel.org/ubuntu/) gutsy main")

I'll definitely report the bug...in the meantime though, it seems my only recourse is to wipe and reinstall.  Meh...

Thanks though, glennric, for the info!

---

