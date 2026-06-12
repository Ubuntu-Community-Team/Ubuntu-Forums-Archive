---
title: "Problems with Unofficial Ubuntu 5.04 Starter Guide (PowerPC)"
date: 2005-06-18
forum: Apple PPC Users
---

### Post by harryc on 2005-06-18
I just ran through the "Unofficial Ubuntu 5.04 Starter Guide (PowerPC)" 
[http://powerpc.ubuntuguide.org/#mplayer](http://powerpc.ubuntuguide.org/#mplayer)
and I encountered two problems. First, while installing mplayer-powerpc I get this error;

```
harryc@ubuntu:~$ sudo apt-get install mplayer-powerpc
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
  mplayer-powerpc: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
                   Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
E: Broken packages

```

Mind you, I did an extensive forum search and the only thing I can find is that I need to comment out the marillat repos. The problem is I never had them in the original etc/apt/sources.list, nor in the new sources.list that the guide had me update to.

Sources.list recommended by the guide;

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release powerpc (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

# Contains libdvdcss2, mplayer, etc... for powerpc
deb http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/ mplayer/

```

The second problem is that I am missing a key.

```
harryc@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:3 http://archive.ubuntu.com hoary-updates Release.gpg [189B]
Get:4 http://honk.physik.uni-konstanz.de mplayer/ Release.gpg [307B]
Hit http://security.ubuntu.com hoary-security Release
Hit http://archive.ubuntu.com hoary Release
Hit http://honk.physik.uni-konstanz.de mplayer/ Release
Hit http://archive.ubuntu.com hoary-updates Release
Hit http://security.ubuntu.com hoary-security/main Packages
Ign http://honk.physik.uni-konstanz.de mplayer/ Release
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://archive.ubuntu.com hoary/main Packages
Ign http://honk.physik.uni-konstanz.de mplayer/ Packages
Hit http://archive.ubuntu.com hoary/restricted Packages
Hit http://archive.ubuntu.com hoary/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://honk.physik.uni-konstanz.de mplayer/ Packages
Hit http://archive.ubuntu.com hoary/restricted Sources
Hit http://archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/universe Sources
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://archive.ubuntu.com hoary-updates/main Packages
Hit http://archive.ubuntu.com hoary-updates/restricted Packages
Hit http://archive.ubuntu.com hoary-updates/main Sources
Hit http://archive.ubuntu.com hoary-updates/restricted Sources
Fetched 310B in 0s (321B/s)
Reading package lists... Done
W: GPG error: http://honk.physik.uni-konstanz.de mplayer/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6F55E43F840A7FF6
W: You may want to run apt-get update to correct these problems

```

Any ideas? This was a new install yesterday. All I did was let 'Ubuntu Update Manager" install updates against the original sources.list, which I still have (backed up)

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release powerpc (20050407)]/ hoary main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

```

---

### Post by jonatin on 2005-06-18
Take the trailing backslash off the http:// site in the repository list

for example...
```
deb http://us.archive.ubuntu.com/ubuntu hoary .. ..
```

---

### Post by harryc on 2005-06-18
Thanks for the reply. There is no trailing backslash in the sources.list recommended by the guide.

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release powerpc (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

# Contains libdvdcss2, mplayer, etc... for powerpc
deb http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/ mplayer/
```

Did you mean in this line?

```
deb http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/ mplayer/
```

---

### Post by jonatin on 2005-06-19
[QUOTE=harryc]Thanks for the reply. There is no trailing backslash in the sources.list recommended by the guide.

Did you mean in this line?

```
deb http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/ mplayer/
```[/QUOTE]

Note that the apt-get update indicates its ignoring the mplayer repositories?  (The **Ign** rather than Hit) I'd suspect you need libraries from that repository to fufill the dependencies. And mplayer/ likely isn't working for a repo name.

And it couldn't hurt making sure you haven't left a trailing slash on the ubuntu archive URL either, unless your posted sources.list was wrong.

[QUOTE=harryc]
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release powerpc (20050407)]/ hoary main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
**deb [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") hoary universe main restricted**
# deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary universe

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe [/QUOTE]

HTH

---

### Post by harryc on 2005-06-20
Ok, the previous problem was fixed by commenting out the last line of the sources.list from the guide - 
deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/

The next issue is that I can't find the executable for mplayer..how do you run it? Do I need mplayer-G4? Normally I'd find an icon in the 'applications', 'sound and video' section, but it is not there. The console command 'mplayer' does nothing. The console command 'mplayer-powerpc' does nothing.  Also Limewire does not work after following the guide line for line, although Azureus does, so it's probably not a java problem. Anyone else seeing these problems?

```
harryc@ubuntu:~$ locate mplayer
/etc/mplayer
/etc/mplayer/mplayer.conf
/etc/mplayerplug-in.types
/etc/mplayerplug-in.conf
/var/lib/dpkg/info/mplayer-powerpc.postinst
/var/lib/dpkg/info/mplayer-powerpc.list
/var/lib/dpkg/info/mplayer-powerpc.preinst
/var/lib/dpkg/info/mplayer-powerpc.postrm
/var/lib/dpkg/info/mplayer-powerpc.md5sums
/var/lib/dpkg/info/mplayer-fonts.config
/var/lib/dpkg/info/mplayer-fonts.list
/var/lib/dpkg/info/mplayer-fonts.templates
/var/lib/dpkg/info/mplayer-fonts.postinst
/var/lib/dpkg/info/mplayer-fonts.postrm
/var/lib/dpkg/info/mplayer-fonts.md5sums
/var/lib/dpkg/info/mozilla-mplayer.md5sums
/var/lib/dpkg/info/mozilla-mplayer.list
/var/lib/dpkg/info/mozilla-mplayer.conffiles
/usr/share/doc/mplayer-powerpc
/usr/share/doc/mplayer-powerpc/changelog.Debian.gz
/usr/share/doc/mplayer-powerpc/README.Debian
/usr/share/doc/mplayer-powerpc/copyright
/usr/share/doc/mplayer-powerpc/examples
/usr/share/doc/mplayer-powerpc/examples/codecs.conf.gz
/usr/share/doc/mplayer-powerpc/examples/mencvcd.gz
/usr/share/doc/mplayer-powerpc/changelog.gz
/usr/share/doc/mplayer-fonts
/usr/share/doc/mplayer-fonts/changelog.Debian.gz
/usr/share/doc/mplayer-fonts/copyright
/usr/share/doc/mozilla-mplayer
/usr/share/doc/mozilla-mplayer/copyright
/usr/share/doc/mozilla-mplayer/README
/usr/share/doc/mozilla-mplayer/TODO
/usr/share/doc/mozilla-mplayer/changelog.Debian.gz
/usr/share/doc/mozilla-mplayer/changelog.gz
/usr/share/icons/hicolor/32x32/apps/mplayer.png
/usr/share/icons/hicolor/48x48/apps/mplayer.png
/usr/share/vim/vim63/syntax/mplayerconf.vim
/usr/share/mplayer
/usr/share/mplayer/Skin
/usr/share/mplayer/Skin/default
/usr/share/mplayer/Skin/default/main-silver.png
/usr/share/mplayer/Skin/default/about.png
/usr/share/mplayer/Skin/default/bareqb.png
/usr/share/mplayer/Skin/default/barexit.png
/usr/share/mplayer/Skin/default/barffwd.png
/usr/share/mplayer/Skin/default/barfwd.png
/usr/share/mplayer/Skin/default/barmute.png
/usr/share/mplayer/Skin/default/barplay.png
/usr/share/mplayer/Skin/default/barrev.png
/usr/share/mplayer/Skin/default/barrevv.png
/usr/share/mplayer/Skin/default/barstop.png
/usr/share/mplayer/Skin/default/barzoom.png
/usr/share/mplayer/Skin/default/eqb.png
/usr/share/mplayer/Skin/default/exit.png
/usr/share/mplayer/Skin/default/font-pl.png
/usr/share/mplayer/Skin/default/forward.png
/usr/share/mplayer/Skin/default/load.png
/usr/share/mplayer/Skin/default/minimize.png
/usr/share/mplayer/Skin/default/main.png
/usr/share/mplayer/Skin/default/menu.png
/usr/share/mplayer/Skin/default/menus.png
/usr/share/mplayer/Skin/default/playlist.png
/usr/share/mplayer/Skin/default/mute.png
/usr/share/mplayer/Skin/default/next.png
/usr/share/mplayer/Skin/default/play.png
/usr/share/mplayer/Skin/default/playbar.png
/usr/share/mplayer/Skin/default/preferences2.png
/usr/share/mplayer/Skin/default/pos.png
/usr/share/mplayer/Skin/default/progres-long2c.png
/usr/share/mplayer/Skin/default/prefs.png
/usr/share/mplayer/Skin/default/prev.png
/usr/share/mplayer/Skin/default/symbols.fnt
/usr/share/mplayer/Skin/default/skin
/usr/share/mplayer/Skin/default/progres-long2d.png
/usr/share/mplayer/Skin/default/rev.png
/usr/share/mplayer/Skin/default/skinb.png
/usr/share/mplayer/Skin/default/stop.png
/usr/share/mplayer/Skin/default/subblue.png
/usr/share/mplayer/Skin/default/subload.png
/usr/share/mplayer/Skin/default/symbols2.png
/usr/share/mplayer/Skin/default/zoom-3.png
/usr/share/mplayer/Skin/default/font.fnt
/usr/share/mplayer/Skin/default/symbolsg.fnt
/usr/share/mplayer/font
/usr/share/mplayer/font/font.desc
/usr/share/mplayer/font/iso-8859-1
/usr/share/mplayer/font/iso-8859-1/README-arial-iso-8859-1
/usr/share/mplayer/font/iso-8859-1/arial-18
/usr/share/mplayer/font/iso-8859-1/arial-18/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-1/arial-18/font.desc
/usr/share/mplayer/font/iso-8859-1/arial-18/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-1/arial-18/iso-8859-1-a.raw
/usr/share/mplayer/font/iso-8859-1/arial-18/iso-8859-1-b.raw
/usr/share/mplayer/font/iso-8859-1/arial-28
/usr/share/mplayer/font/iso-8859-1/arial-28/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-1/arial-28/font.desc
/usr/share/mplayer/font/iso-8859-1/arial-28/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-1/arial-28/iso-8859-1-a.raw
/usr/share/mplayer/font/iso-8859-1/arial-28/iso-8859-1-b.raw
/usr/share/mplayer/font/iso-8859-1/arial-24
/usr/share/mplayer/font/iso-8859-1/arial-24/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-1/arial-24/font.desc
/usr/share/mplayer/font/iso-8859-1/arial-24/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-1/arial-24/iso-8859-1-a.raw
/usr/share/mplayer/font/iso-8859-1/arial-24/iso-8859-1-b.raw
/usr/share/mplayer/font/iso-8859-1/arial-14
/usr/share/mplayer/font/iso-8859-1/arial-14/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-1/arial-14/font.desc
/usr/share/mplayer/font/iso-8859-1/arial-14/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-1/arial-14/iso-8859-1-a.raw
/usr/share/mplayer/font/iso-8859-1/arial-14/iso-8859-1-b.raw
/usr/share/mplayer/font/iso-8859-2
/usr/share/mplayer/font/iso-8859-2/README-arial-iso-8859-2
/usr/share/mplayer/font/iso-8859-2/arial-14
/usr/share/mplayer/font/iso-8859-2/arial-14/iso-8859-2-a.raw
/usr/share/mplayer/font/iso-8859-2/arial-14/iso-8859-2-b.raw
/usr/share/mplayer/font/iso-8859-2/arial-14/font.desc
/usr/share/mplayer/font/iso-8859-2/arial-14/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-2/arial-14/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-2/arial-28
/usr/share/mplayer/font/iso-8859-2/arial-28/iso-8859-2-a.raw
/usr/share/mplayer/font/iso-8859-2/arial-28/iso-8859-2-b.raw
/usr/share/mplayer/font/iso-8859-2/arial-28/font.desc
/usr/share/mplayer/font/iso-8859-2/arial-28/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-2/arial-28/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-2/arial-18
/usr/share/mplayer/font/iso-8859-2/arial-18/iso-8859-2-a.raw
/usr/share/mplayer/font/iso-8859-2/arial-18/iso-8859-2-b.raw
/usr/share/mplayer/font/iso-8859-2/arial-18/font.desc
/usr/share/mplayer/font/iso-8859-2/arial-18/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-2/arial-18/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-2/arial-24
/usr/share/mplayer/font/iso-8859-2/arial-24/iso-8859-2-a.raw
/usr/share/mplayer/font/iso-8859-2/arial-24/iso-8859-2-b.raw
/usr/share/mplayer/font/iso-8859-2/arial-24/font.desc
/usr/share/mplayer/font/iso-8859-2/arial-24/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-2/arial-24/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-7
/usr/share/mplayer/font/iso-8859-7/arial-14
/usr/share/mplayer/font/iso-8859-7/arial-14/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-7/arial-14/font.desc
/usr/share/mplayer/font/iso-8859-7/arial-14/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-7/arial-14/iso-8859-7-a.raw
/usr/share/mplayer/font/iso-8859-7/arial-14/iso-8859-7-b.raw
/usr/share/mplayer/font/iso-8859-7/arial-18
/usr/share/mplayer/font/iso-8859-7/arial-18/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-7/arial-18/font.desc
/usr/share/mplayer/font/iso-8859-7/arial-18/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-7/arial-18/iso-8859-7-a.raw
/usr/share/mplayer/font/iso-8859-7/arial-18/iso-8859-7-b.raw
/usr/share/mplayer/font/iso-8859-7/arial-24
/usr/share/mplayer/font/iso-8859-7/arial-24/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-7/arial-24/font.desc
/usr/share/mplayer/font/iso-8859-7/arial-24/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-7/arial-24/iso-8859-7-a.raw
/usr/share/mplayer/font/iso-8859-7/arial-24/iso-8859-7-b.raw
/usr/share/mplayer/font/iso-8859-7/arial-28
/usr/share/mplayer/font/iso-8859-7/arial-28/osd-mplayer-a.raw
/usr/share/mplayer/font/iso-8859-7/arial-28/font.desc
/usr/share/mplayer/font/iso-8859-7/arial-28/osd-mplayer-b.raw
/usr/share/mplayer/font/iso-8859-7/arial-28/iso-8859-7-a.raw
/usr/share/mplayer/font/iso-8859-7/arial-28/iso-8859-7-b.raw
/usr/share/mplayer/font/iso-8859-7/README-arial-iso-8859-7
/usr/share/mplayer/font/cp1250
/usr/share/mplayer/font/cp1250/README-arial-cp1250
/usr/share/mplayer/font/cp1250/arial-14
/usr/share/mplayer/font/cp1250/arial-14/cp1250-a.raw
/usr/share/mplayer/font/cp1250/arial-14/font.desc
/usr/share/mplayer/font/cp1250/arial-14/osd-mplayer-a.raw
/usr/share/mplayer/font/cp1250/arial-14/cp1250-b.raw
/usr/share/mplayer/font/cp1250/arial-14/osd-mplayer-b.raw
/usr/share/mplayer/font/cp1250/arial-18
/usr/share/mplayer/font/cp1250/arial-18/cp1250-a.raw
/usr/share/mplayer/font/cp1250/arial-18/font.desc
/usr/share/mplayer/font/cp1250/arial-18/osd-mplayer-a.raw
/usr/share/mplayer/font/cp1250/arial-18/cp1250-b.raw
/usr/share/mplayer/font/cp1250/arial-18/osd-mplayer-b.raw
/usr/share/mplayer/font/cp1250/arial-24
/usr/share/mplayer/font/cp1250/arial-24/cp1250-a.raw
/usr/share/mplayer/font/cp1250/arial-24/font.desc
/usr/share/mplayer/font/cp1250/arial-24/osd-mplayer-a.raw
/usr/share/mplayer/font/cp1250/arial-24/cp1250-b.raw
/usr/share/mplayer/font/cp1250/arial-24/osd-mplayer-b.raw
/usr/share/mplayer/font/cp1250/arial-28
/usr/share/mplayer/font/cp1250/arial-28/cp1250-a.raw
/usr/share/mplayer/font/cp1250/arial-28/font.desc
/usr/share/mplayer/font/cp1250/arial-28/osd-mplayer-a.raw
/usr/share/mplayer/font/cp1250/arial-28/cp1250-b.raw
/usr/share/mplayer/font/cp1250/arial-28/osd-mplayer-b.raw
/usr/share/mplayer/font/cp1251
/usr/share/mplayer/font/cp1251/arial-14
/usr/share/mplayer/font/cp1251/arial-14/windows-1251-b.raw
/usr/share/mplayer/font/cp1251/arial-14/font.desc
/usr/share/mplayer/font/cp1251/arial-14/windows-1251-a.raw
/usr/share/mplayer/font/cp1251/arial-14/osd-mplayer-b.raw
/usr/share/mplayer/font/cp1251/arial-14/osd-mplayer-a.raw
/usr/share/mplayer/font/cp1251/arial-18
/usr/share/mplayer/font/cp1251/arial-18/windows-1251-b.raw
/usr/share/mplayer/font/cp1251/arial-18/font.desc
/usr/share/mplayer/font/cp1251/arial-18/windows-1251-a.raw
/usr/share/mplayer/font/cp1251/arial-18/osd-mplayer-b.raw
/usr/share/mplayer/font/cp1251/arial-18/osd-mplayer-a.raw
/usr/share/mplayer/font/cp1251/arial-24
/usr/share/mplayer/font/cp1251/arial-24/windows-1251-b.raw
/usr/share/mplayer/font/cp1251/arial-24/font.desc
/usr/share/mplayer/font/cp1251/arial-24/windows-1251-a.raw
/usr/share/mplayer/font/cp1251/arial-24/osd-mplayer-b.raw
/usr/share/mplayer/font/cp1251/arial-24/osd-mplayer-a.raw
/usr/share/mplayer/font/cp1251/arial-28
/usr/share/mplayer/font/cp1251/arial-28/windows-1251-b.raw
/usr/share/mplayer/font/cp1251/arial-28/font.desc
/usr/share/mplayer/font/cp1251/arial-28/windows-1251-a.raw
/usr/share/mplayer/font/cp1251/arial-28/osd-mplayer-b.raw
/usr/share/mplayer/font/cp1251/arial-28/osd-mplayer-a.raw
/usr/share/mplayer/font/cp1251/README
/usr/share/mplayer/font/cp1251/README.bg
/usr/lib/menu/mplayer-powerpc
/usr/lib/mime/packages/mplayer-powerpc
/usr/lib/mozilla/plugins/mplayerplug-in.so
/usr/lib/mozilla/components/mplayerplug-in.xpt
/usr/lib/mozilla-firefox/plugins/mplayerplug-in.so

```

---

### Post by virgule on 2005-06-20
My experiment: ** alien-ing ** a fellow mplayer binary

1- sudo alien mplayer-1.0-0.14.pre6a.0.yd4.fr.ppc.rpm
 (downloaded from <http://ayo.freshrpms.net/yellowdog/4.0/ppc/RPMS.freshrpms/>
2- sudo dpkg -i mplayer_1.0-1.14_powerpc.deb
dpkg: error processing mplayer_1.0-1.14_powerpc.deb (--install):
 trying to overwrite `/usr/share/mplayer/Skin/default/about.png', which is also in package mplayer-powerpc
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 mplayer_1.0-1.14_powerpc.deb
3- sudo apt-get remove mplayer
<ok>
4- sudo dpkg -i mplayer_1.0-1.14_powerpc.deb
<ok>
5- mplayer testfile.wmv
mplayer: error while loading shared libraries: libxvidcore.so.4: cannot open shared object file: No such file or directory

#note to self: hmmm yeah.. At least I have a 'mplayer' executabe! This can actually work!

6- cp /usr/bin/mplayer ~/
7- sudo dpkg -r mplayer
8- sudo apt-get install mplayer-powerpc
9- sudo cp ~/mplayer /usr/bin/
10- mplayer testfile.wmv
mplayer: error while loading shared libraries: libxvidcore.so.4: cannot open shared object file: No such file or directory
11- ::go cry at the corner::

Thoughs??  I guess its somewhere in those lib* packages but there is sooo much Im not sure which one to take I dont wanna blow my system.

BTW: vlc does work for the most part. Only WMV3 files does not output visuals.. only audio... I'd say the real question is: Why no binary in mplayer-powerpc!?!?!?!?!

---

### Post by harryc on 2005-06-20
[QUOTE=virgule]My experiment: ** alien-ing **  I'd say the real question is: Why no binary in mplayer-powerpc!?!?!?!?![/QUOTE]An excellent question. Another good question would be; Does anyone who reads this forum have mplayer working on Ubuntu PPC?

---

### Post by mgalvin on 2005-06-22
I do have mplayer working on my ppc box here. I will take a look at this problem when I get home and have access to my ppc box that I use to test this stuff.

Thanks for reporting the problem.

Matt

---

### Post by harryc on 2005-06-22
Thanks Matt, I appreciate it.

---

### Post by pvz on 2005-06-22
There is a known problem with mplayer on ppc for Hoary, have a look at those threads for more information:
[http://ubuntuforums.org/showthread.php?t=39553&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=39553&highlight=mplayer)
[http://ubuntuforums.org/showthread.php?t=38564&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=38564&highlight=mplayer)

Your options are installing mplayer from source or from the
 [http://honk.physik.uni-konstanz.de/...nux-ppc/debian/](http://honk.physik.uni-konstanz.de/...nux-ppc/debian/) repository, which might cause dependency conflicts, or use vlc as a mediaplayer. I have mplayer installed from source on my iBook G4 and it works well, but I mostly use vlc.

---

### Post by mgalvin on 2005-06-23
Ok so it seems that due to some updated packages there are in deed dep problems now, sadly on libc6 :-/ and others. I think I may just make my own mplayer package when I have time, for now I would say use vlc if it works for you. I should have a better working solution soon(a day or two)... argh, not enough hours in a day :-/

---

### Post by harryc on 2005-06-24
[QUOTE=mgalvin]Ok so it seems that due to some updated packages there are in deed dep problems now, sadly on libc6 :-/ and others. I think I may just make my own mplayer package when I have time, for now I would say use vlc if it works for you. I should have a better working solution soon(a day or two)... argh, not enough hours in a day :-/[/QUOTE]Matt, if there is anything we can do to help or test, please PM. I'm glad that you also see the problem, Sorry for the extra work ;/

---

### Post by harryc on 2005-07-13
Was this ever resolved? Does a working Mplayer package for Ubuntu Hoary PPC exist?

---

