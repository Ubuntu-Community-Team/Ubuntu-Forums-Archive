---
title: "root"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by brandon333 on 2007-12-21
how do i sign in as root? i keep getting errors that i cant update or install anything, well after I decided to add the kde kubuntu theme or what have you, is this the problem?

---

### Post by Dr Small on 2007-12-21
```
sudo su
```
or:
```
sudo *command*
```

Please check out this article on the wiki:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by JillSwift on 2007-12-21
Normally you never have to sign in as root. In fact, you can't without giving root a password.

Are you using the account you created on installing Kubuntu? If not, it may not be an account with "administrator" privileges.

A quick experiment would be to type:```
sudo ls
```into a terminal window (konsole in KDE) If it asks for your password and gives you a directory listing, you're an administrator. Otherwise it will tell you you can't use sudo and you need to log into your admin account.

---

### Post by brandon333 on 2007-12-21
yes but i dont know password

---

### Post by Dr Small on 2007-12-21
> **brandon333 said:**
> yes but i dont know password
Unless you have setup a password for root, then use sudo and the password will be the same as your user password.

---

### Post by brandon333 on 2007-12-21
ok i did the sudo ls and used my passsword and it gave me a list so why is the synapic magager saying no changes will be made ?

---

### Post by RomeReactor on 2007-12-21
Hi. Are you sure this isn't a package conflict problem? what is the error Synaptic gives you?

---

### Post by brandon333 on 2007-12-21
starting without admin privies!  maybe I should dump kubutu, I thought it was a theme but it looks like a whole additional os and i see its features and apps in my menus yet dont tell you how to get to the os, lol

---

### Post by brandon333 on 2007-12-21
how do i unistall kubunt and everything relatd to t, smethings is up and to be oest takigon one o is enugh for me, way way to many rograms.

---

### Post by RomeReactor on 2007-12-21
Ubuntu, Kubuntu, and Xubuntu all share the same underlying OS; what changes is the desktop environment, and with it the applications that you have at your disposal. Depending how you installed the Kubuntu desktop it can be fairly easy to remove it or a little more involved; if you installed it from the terminal using Aptitude, you can uninstall the Kubuntu desktop like this:
```
sudo aptitude remove kubuntu-desktop
```

However, if you used Apt-Get, Add/Remove or Synaptic, then the command is longer:
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon && sudo apt-get install ubuntu-desktop
```

More on that in [Aysiu's Psychocats page]("http://www.psychocats.net/ubuntu/puregnome.php").

---

### Post by brandon333 on 2007-12-21
I am trying to fix issues before i trash out kubuntu and really like how my desktop looks now cube, advanced desktop, and if i dump kubuntu I think I will loose all that.

my directory is /home/me the main user /home is for me unattainable, i can add things in add and remove the problem is the kubuntu manager adept or what have you, I will screen shot the error

---

### Post by brandon333 on 2007-12-21
screenshot, problem isnt in synaptic or add.remove only with adept

---

### Post by RomeReactor on 2007-12-21
Try launching Adept from the terminal or Konsole:
```
kdesu adept
```

---

### Post by brandon333 on 2007-12-21
command not found it says

---

### Post by RomeReactor on 2007-12-21
It seems you don't have a complete installation of KDE; try running:
```
sudo aptitude install kubuntu-desktop
```
to see if it installs additional packages; or, if you want to remove it completely, see the previous page on this thread.

Note: In your screenshot you're running Gnome, not KDE.

---

### Post by brandon333 on 2007-12-22
> **RomeReactor said:**
> It seems you don't have a complete installation of KDE; try running:
```
sudo aptitude install kubuntu-desktop
```
to see if it installs additional packages; or, if you want to remove it completely, see the previous page on this thread.

Note: In your screenshot you're running Gnome, not KDE.


I am confused on the ubuntu or kubuntu thing, I have both yet the only difference I see is it added more programs, mostly crap that give me nore more benefit, are you suppose to switch betwwen them? you say I am running gnome not kde, how do i run kde? and how do you know which is which and how do you switch between them?

---

### Post by brandon333 on 2007-12-22
after that command here is what I got in terminal:




Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done   

so it was there already right?

---

### Post by brandon333 on 2007-12-22
I tried using adept again and got errors: telling me I dont have admin privs and to run through sudo or kdesu or as root

---

### Post by RomeReactor on 2007-12-22
Log out, then at the login screen, go to "Options" or "Sessions" (I forget which) and there you can select between Gnome or KDE (Ubuntu or Kubuntu).

---

### Post by brandon333 on 2007-12-22
ok the adept manager works in kubuntu session not ubuntu, but looked around a bit and well computer runs worse, alot of things were slow, crashed, overall dont like the looks or feel, I like UBUNTU!! SO how do I get rid of KUBUNTU FOREVER, is this possible? also logged back into ubuntu session and wallpaper is gone and desktop is brown, was blue, and windows are brown were blue.

---

### Post by brandon333 on 2007-12-22
ok i unistalled and it removed kubuntu, but other programs, like kino, amarok, etc but what has me worried is this:

Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: ubuntu-sounds but it is not going to be installed
E: Broken packages

---

### Post by brandon333 on 2007-12-22
but horay got my gparted back an no more errors opening synaptic

---

