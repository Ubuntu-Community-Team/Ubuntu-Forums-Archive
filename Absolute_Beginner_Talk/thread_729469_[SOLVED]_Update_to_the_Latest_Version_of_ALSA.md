---
title: "[SOLVED] Update to the Latest Version of ALSA"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by mebu99 on 2008-03-19
Hello,
    I am trying to update to the Latest Version of ALSA.  I am doing this to try fix the sound on my Dell Latitude D630.  I am working to follow the directions this web-site.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

After doing the command:

```
sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`
```

I am prompted for the 7.10 CD.  I insert the CD in the CD-ROM however.  The CD is never read.

I can see the CD on the machine, and it is mounted under under CD-RW/DVD-RW and I can read the Ubuntu 7.10 CD.

I also see a CD-ROM1;however, when I attempt to mount CD-ROM1, I receive an error.

**Unable to mount the selected volume**
mount: special device /dev/sdb1 does not exist.  

Any way I can get the CD-ROM1 out of my system and be able to read from my true CD-ROM drive?

---

### Post by wormser on 2008-03-19
Are you connected to the internet?  These programs can be installed from the repositories.  It sounds like you need to enable the repositories and remove the CD as a source.

System> Administration> Software Sources.  Enable Main, Universe and Multiverse.  Unselect the CD-ROM/DVD.  Then run the install command again.

---

### Post by Suparious on 2008-03-19
The GUI way would be to remove the cdrom from the synaptic package manager ("System"->"Administration"->"Synaptic"->"Settings"->"Installable from CD-ROM").

Otherwise open '/etc/apt/sources.list' and comment-out (with a #) the line that reads "deb cdrom:[Ubuntu 7.10 _..." like this:

```
  
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main r$
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
...

```

then update apt:

```
sudo apt-get update
```

---

### Post by mebu99 on 2008-03-20
Thanks wormser.  That fixed me up.  Now to figure out why I don't have sound, but I will work on that off-line.

---

