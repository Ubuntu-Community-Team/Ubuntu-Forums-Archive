---
title: "Media Freezes Ubuntu"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by lithiumbloom on 2008-01-17
I recently switched from Windows to Ubuntu, and have had some minor issues.

Most I have sorted out, however just recently any media I attempt to play freezes Ubuntu.  It never used to do this.  I can't think of anything I've recently changed that may have brought this situation into effect.

Songbird opens, but when I go to click on a song, the window fades to grey and never loads.  Same for gtkpod, Totem movie player.  DVDs freeze, basically any media.  I've installed the package for restricted file types (m4a, mp3, etc.)  Why all of the sudden seemingly randomly?

Any help would be greatly appreciated.

---

### Post by lithiumbloom on 2008-01-17
/bump

---

### Post by lithiumbloom on 2008-01-17
/bump

---

### Post by lithiumbloom on 2008-01-17
Also, firefox does the same upon trying to play Youtube videos.  FTW please help. >_<;;

---

### Post by lithiumbloom on 2008-01-17
. . .):

/bmp

---

### Post by lithiumbloom on 2008-01-18
Anyone??

---

### Post by zipperback on 2008-01-18
What version of Ubuntu are you using?

Does the application crash or does the entire system lock up?

Does your system play CD's ok?

Where did you install the codecs from? Are you installing from the Ubuntu repositories?

How did you install them?

Please also post the output from the following.

```

cat /etc/apt/sources.list

```

The above command will display your respository source list.

- zipperback
:popcorn:

---

### Post by lithiumbloom on 2008-01-20
Running Gutsy.

App. Crashes, (fades grey and freezes)

Plays CDs fine.

Codecs from the synaptic installer -> unrestrict media package thing.

Results from cat /etc/apt/sources.list:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by lithiumbloom on 2008-01-20
.bump

---

### Post by lithiumbloom on 2008-01-20
well does anyone know ANYTHING, PLEASE because I have certain things I need to do for a class, and school is tomorrow, so.  Any help would be GREATLY appreciated.

---

### Post by lithiumbloom on 2008-01-20
/bmp  T_T;

---

### Post by mgmiller on 2008-01-20
If you have desktop effects turned on, try turning them off.
System > Preferences > Appearance and select the Visual effects tab and then click on "None".

---

### Post by lithiumbloom on 2008-01-22
This does nothing.

---

### Post by lithiumbloom on 2008-01-22
. . .  /bump.

---

### Post by lithiumbloom on 2008-01-22
/BUMP

CAN ANYONE Help me pleassseee.

---

### Post by lithiumbloom on 2008-01-22
.

---

### Post by crjackson on 2008-01-22
> **lithiumbloom said:**
> I recently switched from Windows to Ubuntu, and have had some minor issues.

Most I have sorted out, however just recently any media I attempt to play freezes Ubuntu.  It never used to do this.  I can't think of anything I've recently changed that may have brought this situation into effect.

Songbird opens, but when I go to click on a song, the window fades to grey and never loads.  Same for gtkpod, Totem movie player.  DVDs freeze, basically any media.  I've installed the package for restricted file types (m4a, mp3, etc.)  Why all of the sudden seemingly randomly?

Any help would be greatly appreciated.

Couple of things here.  You shouldn't bumb more than once in a 24 hour period.  You are risking a forum infraction.  It actually sounds to me like you should try reinstalling your codecs.

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and past the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

Flash go here - [http://ubuntuforums.org/showthread.php?t=648356]("http://ubuntuforums.org/showthread.php?t=648356")

Hope this helps...

---

### Post by Liam-Gorham on 2008-01-22
I have had the same problem when i first installed my ubuntu 7.10 the codecs are important make sure you have them all there are about a total of 3-4 of them. Use the add/remove app to find'em. Make sure you set the settings to show all unsupported as well they will still install and work fine.

---

### Post by Liam-Gorham on 2008-01-22
There are 6 search GStreamer make sure you install them all.

---

### Post by lithiumbloom on 2008-01-22
I've installed all 6 of the available GStreamer codecs.

I'm sorry for continuous bumping but like I said I've had this problem for a long time and I need to do things with the media for school. >_<

---

### Post by mgmiller on 2008-01-23
Have you installed the ubuntu-restricted-extras package?
It's a metapackage that keeps all that stuff as well as flash and java up to date.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by bwtranch on 2008-01-23
I would backup important files and try a fresh install. For all I know, it could be a hardware problem. Instead of all that bumping, you could have posted some output.

---

