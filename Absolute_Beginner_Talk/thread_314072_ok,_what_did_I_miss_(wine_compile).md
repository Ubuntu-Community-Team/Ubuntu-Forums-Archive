---
title: "ok, what did I miss (wine compile)"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by pizzutz on 2006-12-07
ok, still new here, trying to recompile wine to fix a mouse bug in my favorite game(Dark age of camelot).  I'm missing something.

I did a wget of the latest wine files

I uncompressed them in a new directory..

I did a patch to fix a mouse bug that exists with the current wine version and that particular game.

did ./configure

did make depend && make

did sudo make install

now wine camelot #which worked before I did the patch gives me this error

[INDENT]pizzutz@mike-desktop:~/.wine/drive_c/Darkness$ wine camelot
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
[email]pizzutz@mike-desktop:~/.wine[/email]/drive_c/Darkness$ err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
[/INDENT]

Something got lost in the compile, and this is the first time I've tried compiling under any linux.  I'm sure I'm missing something easy, and the error is practally screaming at me what it is, but I don't know.  Please help; getting this game to run right is the only thing stopping me from completely reformating my ntfs drives and ditching M$ forever.  :)

---

### Post by pay on 2006-12-07
Try compilling it like this (I can not promise that it will work). Add deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main to your /etc/apt/sources.list and then```
sudo apt-get update
sudo apt-get build-dep wine
sudo apt-get source wine
```then patch the downloaded source (as root user)```
cd
sudo apt-get --build source wine
sudo dpkg -i wine*
```

---

### Post by pizzutz on 2006-12-07
I'm using dapper atm, and I do have the budgetdedicated repo loaded for dapper.


(sources,list)
```

deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://wine.budgetdedicated.com/apt dapper main
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ dapper main main-all
deb http://www.albertomilone.com/drivers/dapper/legacy/32bit binary/
```

I get an error on 
```

pizzutz@mike-desktop:~$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for wine
pizzutz@mike-desktop:~$
```

---

### Post by pay on 2006-12-07
You have the binary repo. This is the source repo```
deb-src http://wine.budgetdedicated.com/apt edgy
```It doesn't matter that it's edgy because your compilling it anyway.

---

