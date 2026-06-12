---
title: "Trouble installing KDE in Ubuntu 6.06"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by raguru on 2006-09-24
Hi,

I would appreciate if someone could help me with this problem.  

I am trying to install KDE in Ubuntu 6.06 and I have tried it 3 times and it fails each time.  I am enclosing the log of what happens below.  

I would highly appreciate if someone could tell me what I am doing wrong.  Thanks in advance.

cheers,
Raghu
-------------Log below-----------------------------
rtumkur@rtumkur-desktop:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  wlassistant
The following NEW packages will be automatically installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags
  flac gtk2-engines-gtk-qt gwenview k3b kaffeine kaffeine-xine karm
  katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klaptopdaemon klipper
  kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins
  knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal
  language-selector-qt latex-xft-fonts libakode2 libarts1-akode
  libflac++5c2 libgadu3 libifp4 libimlib2 libiso9660-4 libjpeg-progs
  libk3b2 libkexif1 libkipi0 libkpimexchange1 libkscan1 liblockdev1 libmad0
  libmodplug0c2 libmpcdec3 libpoppler1-qt libpythonize0 libqt-perl
  librsync1 libsamplerate0 libskim0 libsmokeqt1 libtdb1 libtunepimp3
  libvcdinfo0 libvisual-0.4-0 libxine-extracodecs libxine-main1 libxvmc1
  ncompress ocrad openoffice.org-kde poster psutils pykdeextensions
  python-kde3 python-qt3 python2.4-dev python2.4-kde3 python2.4-qt3
  python2.4-sip4-qt3 qca-tls qobex rdiff-backup scim-qtimm skim speedcrunch
  vcdimager zoo
The following NEW packages will be installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags    flac gtk2-engines-gtk-qt 

gwenview k3b kaffeine kaffeine-xine karm
  katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep khelpcenter
  kio-apt kio-locate kipi-plugins kitchensync klaptopdaemon klipper
  kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins
  knetworkconf knode knotes 

koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop
  kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager
  kwin-style-crystal language-selector-qt latex-xft-fonts libakode2
  libarts1-akode libflac++5c2 libgadu3 libifp4 libimlib2 libiso9660-4
  libjpeg-progs libk3b2 libkexif1 libkipi0 libkpimexchange1 libkscan1
  liblockdev1 libmad0 libmodplug0c2 libmpcdec3 libpoppler1-qt libpythonize0
  libqt-perl librsync1 libsamplerate0 libskim0 libsmokeqt1 libtdb1
  libtunepimp3 libvcdinfo0 libvisual-0.4-0 libxine-extracodecs
  libxine-main1 libxvmc1 ncompress ocrad openoffice.org-kde poster psutils
  pykdeextensions python-kde3 python-qt3 python2.4-dev python2.4-kde3
  python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex rdiff-backup scim-qtimm
  skim speedcrunch vcdimager zoo
0 packages upgraded, 143 newly installed, 0 to remove and 0 not upgraded.
Need to get 124MB of archives. After unpacking 370MB will be used.
The following packages have unmet dependencies:
  wlassistant: Depends: kdelibs4 (>= 4:3.3.2-6.2) which is a virtual package.
               Depends: libiw27 (>= 27) which is a virtual package.
               Depends: libqt3c102-mt (>= 3:3.3.4) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:
Keep the following packages at their current version:
amarok [Not Installed]
amarok-xine [Not Installed]
gwenview [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
libvisual-0.4-0 [Not Installed]
wlassistant [Not Installed]
Score is 80
Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done

---

### Post by Metacarpal on 2006-09-24
Sounds like you have wlassistant (a KDE app) installed, but it's broken for want of its dependancies.  Here's what to do:

Open Synaptic (System menu > Administration > Synaptic).  Then go to Edit, Fix Broken Packages.  Once that finishes doing what it needs to do, you should be able to aptitude install kubuntu-desktop

---

### Post by raguru on 2006-09-25
Thanks a lot for your reply.  It seems like wlassistant is not installed.  When I try to select in Synaptic, the only option I get is "Mark for installation".  If I do that, it tells me to enable all repositories in the Preferences section.  And it also tells me that it depends on:
kdelibs4 (>= 4:3.3.2-6.2) which is not installable
libiw27 (>= 27) which is not installable
libqt3c102-mt (>= 3:3.3.4) which is installable

I am stuck and I have enabled everything under Repositories.  I don't know what to do.  I would appreciate your help again.  

cheers,
Raghu

---

### Post by WalmartSniperLX on 2006-09-25
I had a similar notice when installing something on my friends computer. Try reloading the software properties list. I did it just by unchecking a repo and then checking it again, then clicking close/refresh. Then it fixed it. Your case might be different, but you can try it, because it worked for me

---

### Post by raguru on 2006-09-26
Thanks for your reply.  I will try it this evening and see what it does.  I hope it works!  Thanks again.

-Raghu

---

### Post by Bachstelze on 2006-09-26
Also, you could try to add this line to your sources.list :

*deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main*

then do :

```

wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by buckethead27 on 2006-09-26
Maybe your sources.list is messed up. Check it out, back it up, and replace it from the sources list from the Live CD.

---

### Post by podunk on 2006-09-26
Did you by any chance try to install compiz with a Radeon video card? I had the exact same error and fiddled around with it for a while, and decided that it would be a lot easier  to just install Kunbutu from scratch.

Kubuntu is slightly slower it seems, but it's interface is much more windowish than Ubuntu and long time windows users will find it more familiar.

There is a very cool program that runs  great in Kubuntu that doesn't work very well in Gnome called kxdocker &#8211; check it out once you get KDE going. :-)

---

### Post by raguru on 2006-09-26
Thanks everyone for your responses.  Here is what I have tried.

I tried refreshing the softwre properties list.  That did not help unfortunately.  Still was not able to install wlassistant.

I added the source that HymnToLife suggested.  But when I tried the wget command, I get the following response:

rtumkur@rtumkur-desktop:/etc/apt$ wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
--22:58:54--  [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
           => `kubuntu-packages-jriddell-key.gpg'
Resolving people.ubuntu.com... 82.211.81.132
Connecting to people.ubuntu.com|82.211.81.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 26,430 (26K) [text/plain]
kubuntu-packages-jriddell-key.gpg: Permission denied

Cannot write to `kubuntu-packages-jriddell-key.gpg' (Permission denied).


That does not sound right.  Correct?

I still have not restored the sources list from the CD and tried it.  I ran out of time tonight.  :( 

Also, I have not done anything with the Compiz and Radeon.  I have an nVidia card.  But I will try the kxdocker once I am able to install the KDE.  

I want KDE since I want to use a password manager program called pwmanager which is only available for KDE.  

I will pursue this again tomorrow and get back to you guys.

But once again, thanks to all of you for your suggestions.

cheers,
Raghu

---

### Post by raguru on 2006-09-26
Thanks everyone for your responses.  Here is what I have tried.

I tried refreshing the softwre properties list.  That did not help unfortunately.  Still was not able to install wlassistant.

I added the source that HymnToLife suggested.  But when I tried the wget command, I get the following response:

rtumkur@rtumkur-desktop:/etc/apt$ wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
--22:58:54--  [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
           => `kubuntu-packages-jriddell-key.gpg'
Resolving people.ubuntu.com... 82.211.81.132
Connecting to people.ubuntu.com|82.211.81.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 26,430 (26K) [text/plain]
kubuntu-packages-jriddell-key.gpg: Permission denied

Cannot write to `kubuntu-packages-jriddell-key.gpg' (Permission denied).


That does not sound right.  Correct?

I still have not restored the sources list from the CD and tried it.  I ran out of time tonight.  :( 

Also, I have not done anything with the Compiz and Radeon.  I have an nVidia card.  But I will try the kxdocker once I am able to install the KDE.  

I want KDE since I want to use a password manager program called pwmanager which is only available for KDE.  

I will pursue this again tomorrow and get back to you guys.

But once again, thanks to all of you for your suggestions.

cheers,
Raghu

---

### Post by Metacarpal on 2006-09-27
Hi again Raghu,

You didn't mention trying Edit > Fix Broken Packages in Synaptic.  If you tried that, what was the result?

---

### Post by raguru on 2006-09-27
Sorry about that.  I mentioned it but I was not clear.  The only way I could highlight wlassistant was by highlighting it.  If I tried to check the box, then the only option I got was "Mark for Installation".  I tried that and that's when it said that it could install it because of other dependencies that it could not install.
This is where I had tried to reply to you:

"Thanks a lot for your reply. It seems like wlassistant is not installed. When I try to select in Synaptic, the only option I get is "Mark for installation". If I do that, it tells me to enable all repositories in the Preferences section. And it also tells me that it depends on:
kdelibs4 (>= 4:3.3.2-6.2) which is not installable
libiw27 (>= 27) which is not installable
libqt3c102-mt (>= 3:3.3.4) which is installable"

But if I just highlighted without marking and then when I say "Fix Broken Package", it just quickly came back and said at the bottom of the window in the frame "Package successfully fixed"!! :( 

So, that is where I stand.  I am going to try a few more suggestions tonight and see what happens.  

But thanks for checking back.  I appreciate it.

-Raghu

---

### Post by raguru on 2006-09-27
I had slightly better luck with what HymnToLife had said yesterday.  Here is what happened today:

rtumkur@rtumkur-desktop:~$ wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
--23:11:23--  [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
           => `kubuntu-packages-jriddell-key.gpg'
Resolving people.ubuntu.com... 82.211.81.132
Connecting to people.ubuntu.com|82.211.81.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 26,430 (26K) [text/plain]

100%[====================================>] 26,430        71.36K/s

23:11:24 (71.16 KB/s) - `kubuntu-packages-jriddell-key.gpg' saved [26430/26430]

So, that worked better today.  Next....

rtumkur@rtumkur-desktop:~$ sudo apt-key add kubuntu-packages-jriddell-key.gpg
gpg: no ultimately trusted keys found
OK
rtumkur@rtumkur-desktop:~$ sudo apt-key add kubuntu-packages-jriddell-key.gpg
OK

I had to try that 2 times, but it seemed it worked ok.

I then executed sudo apt-get update and that worked fine.  And then finally, I tried 

sudo apt-get install kubuntu-desktop

and this is what I get:

rtumkur@rtumkur-desktop:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: wlassistant but it is not going to be installed
E: Broken packages

--------------------------------------
So, is it telling me that I should file a bug report?  This is totally different from all of my previous attempts.  

Any help is appreciated.  Thanks again.

-Raghu

---

