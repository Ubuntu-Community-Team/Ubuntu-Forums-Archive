---
title: "I need to delete some Cd-roms"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2006-01-25
I installed a new dvd burner and took both my old cd roms out so now I only have one. synaptic will ask me to put the cd in the cd rom but it never finds it. I looked in my media folder and it is showing 3 how do i delete the old ons?

---

### Post by Jucato on 2006-01-25
Just a guess:

Maybe your system still mounts the two old cd-roms. Have you checked your /etc/fstab? try to comment out the two references to the old cd-roms if they're still there.

---

### Post by benplaut on 2006-01-25
[QUOTE=Fenyx]Just a guess:

Maybe your system still mounts the two old cd-roms. Have you checked your /etc/fstab? try to comment out the two references to the old cd-roms if they're still there.[/QUOTE]
otoh, post your /etc/fstab here, so you don't mess anything up.  Also, post your /etc/apt/sources.list  so we can get rid of the synaptic issue

Good luck! :)

---

### Post by Jucato on 2006-01-25
oh yeah. forgot to ask you to post those stuff. sorry. the synaptic problem might also be due to the cdrom repository still being enabled.

---

### Post by onesojourner on 2006-01-26
fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda7       /media/hda7     ext3    defaults        0       2
/dev/hda8       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/bigdrive  ntfs    nls=utf8,umask=0222 0       0
/dev/hda6       /media/FAT  vfat    iocharset=utf8,umask=000   0       0

---

### Post by onesojourner on 2006-01-26
source list

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051005)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

---

### Post by Jucato on 2006-01-26
do this in the sources.list

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051005)]/ breezy main restricted
```

that should solve your problem with Synaptic looking for the cdrom.

as for the fstab, I'm not really sure how to do this. Are you saying the Storage Media (media:/) recognizes the DVD-ROM and the 2 CD-ROMs? because as far as your fstab is concerned, your system is only supposed to see the 2 CD-ROMs. I'm not really sure how to do this with DVD-ROMs. Sorry I couldn't be of much further help.

---

### Post by onesojourner on 2006-01-26
I added that to the bottom of my source list but synaptic is still asking my to put the cd in the rom. its in the new rom and thats the only rom in the computer. i think synaptic is just looking for the cd in a rom that does not exist any more.

If I go to my media folder I see 3 folders for roms. I only have one. its like it still sees the 2 old ones.

---

### Post by Madpilot on 2006-01-26
I'm not sure what's up with your multiple CD drive issue, but to fix Synaptic: add a # in front of the CDROM line in your sources.list (that's the very first line, that starts with "deb cdrom:[Ubuntu 5.10 _Breezy Badger_...")

That's what Fenyx meant - you don't need to add a line at all, just comment one out.

The # means that Synaptic will read that line just a a comment - like the human-readable explanations in the other parts of sources.list

---

### Post by Jucato on 2006-01-26
oops... I should have been more precise. I meant to tell you to comment out (put #) the cdrom repository, the one on top of your sources.list so that it should look like this:

```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051005)]/ breezy main restricted
 
 
 ## Uncomment the following two lines to fetch updated software from the network
 # deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
 
 ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
 # deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
 # deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
 
 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
 # deb-src http://us.archive.ubuntu.com/ubuntu breezy universe
 
 ## Uncomment the following two lines to add software from the 'backports'
 ## repository.
 ## N.B. software from this repository may not have been tested as
 ## extensively as that contained in the main release, although it includes
 ## newer versions of some applications which may provide useful features.
 ## Also, please note that software in backports WILL NOT receive any review
 ## or updates from the Ubuntu security team.
 # deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted
 # deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted
 
 # deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 # deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
 
 # deb http://security.ubuntu.com/ubuntu breezy-security universe
 # deb-src http://security.ubuntu.com/ubuntu breezy-security universe
 deb http://wine.sourceforge.net/apt/ binary/
```

Sorry for not being clear... :(

---

### Post by az on 2006-01-26
Apt will ask you to put a cd into the drive that the /dev/cdrom symlink points to.  Gnome will create shortcuts to any device it finds in the gnome Computer location.

You need to remove one of the fstab entries (the one that no longer exists) and make sure that the cdrom symlink points to your device.  So, if you have one optical device, you should have one fstab entry about it. Gnome will figure out the rest and you should no longer have three optical drives in gnome.

---

### Post by onesojourner on 2006-01-26
well I think that fixed it. I will let you know if it didnt. thanks for the help.

---

