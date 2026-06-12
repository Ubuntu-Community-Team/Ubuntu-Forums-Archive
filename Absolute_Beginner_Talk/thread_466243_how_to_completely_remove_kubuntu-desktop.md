---
title: "how to completely remove kubuntu-desktop?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by tschuliaen on 2007-06-06
Hello there

I'm using Ubuntu however I wanted to try out Kubuntu. So I made

```
sudo apt-get install kubuntu-desktop
```

Now I had a look at it, liked it as well but made my decision for GNOME. Therefore I'd like to remove KDE again including all the KDE-programs kubuntu-desktop installed.
So I typed in:

```
sudo apt-get remove --purge kubuntu-desktop
```

Unfortunately all the KDE-programs are still here and I've got no ideal how to get rid of them...

What do i have to do?

Cheers

---

### Post by meng on 2007-06-06
You could try
sudo apt-get autoremove

---

### Post by Inxsible on 2007-06-06
Do you know what KDE programs you have installed ?
 
That way you can list all of them in the same command and remove them all together

---

### Post by steeleyuk on 2007-06-06
> **Inxsible said:**
> Do you know what KDE programs you have installed ?
 
That way you can list all of them in the same command and remove them all together

It will have installed all the programs that come with kubuntu-desktop, so tracking them all down might be difficult.

---

### Post by tschuliaen on 2007-06-06
sudo apt-get remove doesn't change anything

I don't know which programs are installed. They came together with kubuntu-desktop (Including the kubuntu splash screen and stuff)

---

### Post by meng on 2007-06-06
it's autoremove (not remove)
but if it doesn't work (and I wasn't sure it would), try this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by tschuliaen on 2007-06-06
sorry of course I meant  sudo apt-get autoremove

but the page did it well, however it deinstalled a bit too much but a well its quickly reinstalled!

thanks

---

### Post by strabes on 2007-06-06
The reason that it's leaving stuff on your system is you used apt-get instead of aptitude to install kubuntu-desktop. Autoremove will not remove those leftover packages because to the system, they are not orphaned or unneeded/unwanted. I don't know if this will work but you could try running ```
sudo aptitude reinstall -f kubuntu-desktop
sudo aptitude remove kubuntu-desktop
```

---

### Post by zeeR on 2007-06-16
I had the same problem as you, and to completely remove kubuntu (in my case it was xubuntu, but it works the same), I went to the Synaptic's "Historic", and copied the list of packages installed at the time I installed "xubuntu-desktop" (synaptic sorts it out for you). Then I looked for every one on Synaptic (it's quicker than you think, a lot of them have dependencies and remove several at a time), and erased the entries on the list as I marked them for removal. This removed them all, and you'll be exactly as you were before installing the kubuntu-desktop!

EDIT: I found [_[COLOR="DarkRed"]this[/COLOR]_]("http://http://www.psychocats.net/ubuntu/puregnome").

To remove all those packages, run this on your terminal (it's doing the same as I did up there, but they have all the packages sorted out for you):

```

sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools && sudo apt-get install ubuntu-desktop
```

---

### Post by Happy_Man on 2007-06-16
I must say this, as a Kubuntu user, was there anything you didn't like about Kubuntu? Or was it just personal preference?

---

### Post by SimonPhoto on 2007-06-17
I recently did the same thing.  I am using pure Gnome, and installed KDE to test out Quanta for web development.  KDE, for me, was much slower that gnome.  I missed the clean interface very much as well.  

I have no doubt KDE is feature-rich, but I neither need nor want many of those features.  I'm still fairly new, and there seemed to be 5 different ways to do anything in KDE.  Gnome is more intuitive, to me.

Personal preference I suppose.

---

### Post by jmimick on 2007-08-02
btw, that will hose many other programs unrelated to KDE :confused::(
But - yes the KDE UI is far inferior and I just wanted it off my system, so I'm content to rebuild things (eg apache, mysql, php, wireshark, etc)

---

