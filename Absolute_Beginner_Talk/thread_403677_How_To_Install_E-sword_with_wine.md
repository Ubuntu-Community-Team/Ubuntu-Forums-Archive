---
title: "How To Install E-sword with wine"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by david_kt on 2007-04-07
[B]This "how to" is outdated. For up to date "how to" please follow below link:

[http://http://ubuntuforums.org/showthread.php?t=404042]("http://http://ubuntuforums.org/showthread.php?t=404042")
 [/B]

=================================================================================

You could download the program and other addons here:

[http://www.e-sword.net/downloads.html]("http://www.e-sword.net/downloads.html")

Create "bottle" for Esword:
```
wineprefixcreate --prefix .wine_Esword
```

Download riched20, riched32, and oleaut32.dll to your ~/.wine_Esword /drive_c/windows/system32 from here:

[http://www.dll-files.com]("http://www.dll-files.com")

Or you could go to direct link below:
Riched20:
[http://www.dll-files.com/dllindex/dll-files.shtml?riched20]("http://www.dll-files.com/dllindex/dll-files.shtml?riched20")

Riched32:
[http://www.dll-files.com/dllindex/dll-files.shtml?riched32]("http://www.dll-files.com/dllindex/dll-files.shtml?riched32")

oleaut32:
[http://www.dll-files.com/dllindex/dll-files.shtml?oleaut32]("http://www.dll-files.com/dllindex/dll-files.shtml?oleaut32")


Download msls31.dll to your ~/.wine_Esword/drive_c/windows/system32 from here:

[http://www.dlldump.com/]("http://www.dlldump.com/")

Or from direct link here:

[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/msls31.dll]("http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/msls31.dll")


Install the program:

```
env WINEPREFIX=~/.wine_Esword wine setup785.exe
```

In winecfg set riched20.dll and oleaut32.dll to native for e-sword.exe

```
env WINEPREFIX=~/.wine_Esword winecfg
```

Type: 

```
env WINEPREFIX=~/.wine_Esword wine e-sword.exe
```

 in the installation directory to run e-Sword. 

To install addons, run in terminal:

```
 env WINEPREFIX=~/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine bbe.exe
```

The above example is to install bbe.exe. You could install other addons using above overrides, just replace bbe.exe.

DK

---

### Post by userundefine on 2007-04-07
What's wrong with the esword available natively for Linux?

```

Package: gnomesword
Priority: optional
Section: universe/gnome
Installed-Size: 3028
Maintainer: Daniel Glassey <wdg@debian.org>
Architecture: i386
Version: 2.1.7-2
Provides: sword-frontend
Depends: sword-text, sword-comm, sword-dict, libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.13.0), libbonoboui2-0 (>=
 2.5.4), libc6 (>= 2.4-1), libcairo2 (>= 1.0.2-2), libcomerr2 (>= 1.33-3), libcurl3-gnutls (>= 7.15.0-1), libfontconfig1 (>= 2.3.0), libgcc
1 (>= 1:4.1.0), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.10.0), libgnome-keyring0 (>= 0.4.3), libgnome2-0 (>=
2.8.0), libgnomecanvas2-0 (>= 2.11.1), libgnomeprint2.2-0 (>= 2.12.1), libgnomeprintui2.2-0 (>= 2.12.1), libgnomeui-0 (>= 2.13.0), libgnome
vfs2-0 (>= 2.13.92-0ubuntu4), libgnutls12 (>= 1.2.5), libgtk2.0-0 (>= 2.8.0), libgtkhtml3.8-15 (>= 3.10.1), libice6, libidn11 (>= 0.5.18),
libkrb53 (>= 1.4.2), liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.12.2), libpopt0 (>= 1.10), libsm6, libstdc++6 (>= 4.1.0), libsword5c2a (>
= 1.5.8-7), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.24), libxrandr2, libxrender1, zli
b1g (>= 1:1.2.1)
Filename: pool/universe/g/gnomesword/gnomesword_2.1.7-2_i386.deb
Size: 1902126
MD5sum: 19e54b1c33ab951a759032e027f6f088
SHA1: 2d44591e18794e801b4d38c089dae791c17cc493
SHA256: 02e0e98ed9480c9620bf56331ec7ef81e45087756c0aae28b8645afbd1efbe0f
Description: Bible study with GNOME
 A bible study program for GNOME using the SWORD library.
 Features:
  Search Bible and Commentary
  Search Personal notes
  Add personal notes to verses
  Bookmarks
  Parallel Page - Display up to five versions
  StudyPad for keeping notes
  Spellcheck for StudyPad and Personal notes (uses gnome-spell)
  Uses modules from the SWORD Project
  Support for Sword Bible, Commentary, Lexicon and General Book modules
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

And there's also Bibletime built on QT:

```

Package: bibletime
Priority: optional
Section: universe/kde
Installed-Size: 2676
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Daniel Glassey <wdg@debian.org>
Architecture: i386
Version: 1.6-0ubuntu1
Provides: sword-frontend
Depends: kdelibs4c2a (>= 4:3.5.3-1), libacl1 (>= 2.2.11-1), libart-2.0-2 (>= 2.3.16), libattr1 (>= 2.4.4-1), libaudio2, libc6 (>= 2.4-1), l
ibclucene0 (>= 0.9.16-1), libcomerr2 (>= 1.33-3), libcurl3-gnutls (>= 7.15.4-1), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.2), libgcc1
(>= 1:4.1.1-12), libgcrypt11 (>= 1.2.2), libgnutls13 (>= 1.4.0-0), libgpg-error0 (>= 1.2), libice6, libidn11 (>= 0.5.18), libjpeg62, libkrb
53 (>= 1.4.2), libpcre3 (>= 4.5), libpng12-0 (>= 1.2.8rel), libqt3-mt (>= 3:3.3.6), libsm6, libstdc++6 (>= 4.1.1-12), libsword6 (>= 1.5.9-0
ubuntu3), libtasn1-3 (>= 0.3.4), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxft2 (>> 2.1.1), libxi6, libxinerama1, libxrandr2, libxrend
er1, libxt6, zlib1g (>= 1:1.2.1)
Recommends: sword-text, sword-dict, sword-comm
Filename: pool/universe/b/bibletime/bibletime_1.6-0ubuntu1_i386.deb
Size: 1114632
MD5sum: 2a264a474756f420479a958b09a24232
SHA1: f8cc84015fe42449a31a40f049bd0c490ed378f3
SHA256: a9a9bcbf5947b2e1bbb28b2c66c3a485c7fb1d58cd8364a777e0302b78044ea0
Description: A bible study tool for KDE
 BibleTime is a free and easy to use bible study tool for UNIX systems.
 It requires a working KDE environment and the SWORD library.
 BibleTime provides easy handling of digitized texts (Bibles, commentaries
 and lexicons) and powerful features to work with these texts (search in
 texts, write own notes, save, print etc.).
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by david_kt on 2007-04-07
> **userundefine said:**
> What's wrong with the esword available natively for Linux?


I have never tried others, but I heard that E-sword is much more complete. It has many bibles in many languages (including chinese, japanese,  vietnamese, greek), dictionary, explanation, devotion, map (graphic), sermon preparation tools, and many other functions.

Basically, it has all you need for bible study. Is the linux bible as good as E-sword? I doubt so. E-sword is one of the best e bible, comparable (or even better) than the commercial one. So, we should bring it to linux user as well. 

Last time I saw people need to install addons manually, but I have tried to install it automatically using dll overrides (without any error).

But I have not tried all functions as actually I am using it on windows xp. Please let me know if some function is not working. For example in wine, to view graphic, you need to print preview first, closed print preview, and then click fit all.

DK

---

### Post by AndyCooll on 2007-04-07
This would probably be better in the [ Ubuntu Christian Edition forum]("http://ubuntuforums.org/forumdisplay.php?f=168")

Another link for e-Sword in that forum is here: [ e-Sword! You asked for it! You got it!]("http://ubuntuforums.org/showthread.php?t=372359")

:cool:

---

### Post by userundefine on 2007-04-07
That screenshot you put up looks basically exactly like Bibletime.

But, it's not a program I use.  The guys in the Christian edition forum could give you a much fuller opinion than I could.

---

### Post by david_kt on 2007-04-08
> **userundefine said:**
> That screenshot you put up looks basically exactly like Bibletime.

But, it's not a program I use.  The guys in the Christian edition forum could give you a much fuller opinion than I could.

I saw they are struggling to install E-sword, and Jeremy even make an installer for linux. But I find it very easy to run this program using normal wine. As suggested, I have posted also in Ubuntu Christian ( I am not sure whether or it considered double post). The reason I post here is to help people that want to use normal ubuntu (not Ubuntu CE) but wanted to run E-sword badly as it is considered one of the best bible.

I tried gnomesword, but it is much inferior (imo) compared to E-sword, or I just do not know yet how to install other feature in gnomesword?

DK

---

### Post by userundefine on 2007-04-08
I don't disagree about gnomesword.  When I played with it, it seemed limited.  I preferred BibleTime by far.  Downloading features like bibles and commentaries is quite easy with it.

---

### Post by david_kt on 2007-04-09
> **userundefine said:**
> I don't disagree about gnomesword.  When I played with it, it seemed limited.  I preferred BibleTime by far.  Downloading features like bibles and commentaries is quite easy with it.

How is bibletime compared to E-sword? Is bible time able to run in gnome? I could inform by now that E-sword should run perfectly using the setup I tried, not even neccesary to have windows box either to copy dll (available for download) or to copy module (could install module without error in linux).

DK

---

### Post by AndyCooll on 2007-04-09
> **david_kt said:**
> How is bibletime compared to E-sword? Is bible time able to run in gnome? I could inform by now that E-sword should run perfectly using the setup I tried, not even neccesary to have windows box either to copy dll (available for download) or to copy module (could install module without error in linux).

DK

Yes Bibletime can run on the GNOME desktop, just about any KDE based app can. Just install Bibletime through Synaptic and the necessary KDE libraries required to run it will also  be installed. It may run a little slower than it would if it were on its native KDE desktop but it will be fine.

:cool:

---

