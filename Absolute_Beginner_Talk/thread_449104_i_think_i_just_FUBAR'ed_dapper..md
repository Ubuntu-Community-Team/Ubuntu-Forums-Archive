---
title: "i think i just FUBAR'ed dapper."
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Halonut1 on 2007-05-19
Ok, so i was loading the packets to upgrade dapper to 6.10. well my friend turned off my computer. and now update manager and add/remove wont work. i get this message from add/remove

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

i think somehow my repositories are half dapper and half feisty. anyone know how i could restore them or reload ubuntu without formatting my entire HD? i have alot of stuff i cant get rid of. if there is just some way to restore dapper with the Disc or something that would be really good.

---

### Post by taurus on 2007-05-19
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and remove all the entries.  Then, paste these new ones in for your Dapper.

```

deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main 

```
Save it and then run

```
sudo aptitde update
sudo aptitude upgrade
```

p.s.  Dapper is 6.06, Edgy is 6.10, and Feisty is 7.04.

---

### Post by Halonut1 on 2007-05-19
ok now i get this message from Software updates

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/dists/dapper/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/dists/dapper/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

---

### Post by taurus on 2007-05-19
Is your network still working?  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by Halonut1 on 2007-05-19
Yes i am still on ubuntu.


kenny@laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

    # wxPython APT repository at wxcommunity.com
deb [http://wxpython.wxcommunity.com/apt/ubuntu/dapper](http://wxpython.wxcommunity.com/apt/ubuntu/dapper) /
deb-src [http://wxpython.wxcommunity.com/apt/ubuntu/dapper](http://wxpython.wxcommunity.com/apt/ubuntu/dapper) /

---

### Post by H.E. Pennypacker on 2007-05-19
taurus asked you to remove EVERYTHING from your sources list, and replace it with the list he/she provided.  You didn't do this, because you left the cd-rom in there.  

Please remove EVERYTHING as he/she said, and replace the list with his/her list.

That's why you're getting that error.

---

### Post by taurus on 2007-05-19
You said that your /etc/apt/sources.list was all messed up.  Where did you get this /etc/apt/sources.list anyway?  I personally would comment out by placing a # in front of the first lines for the CDROM and those extra repos at the end regarding Automatix & wxPython.

It is not a good idea to include 3rd party repos in your /etc/apt/sources.list when you try to upgrade from one release to the next.  That is sure one way to screw up your machine.

---

### Post by Halonut1 on 2007-05-19
Ok, i did it again with the CD out, still did the same Software Update
and i got it from entering cat /etc/apt/sources.list like you said. should i open it again and put the # infront of them?

If i can even get this to work again i probably wont switch from dapper from a *looooong* time.

---

### Post by Halonut1 on 2007-05-19
heres my Sources.list file.

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

    # wxPython APT repository at wxcommunity.com
deb [http://wxpython.wxcommunity.com/apt/ubuntu/dapper](http://wxpython.wxcommunity.com/apt/ubuntu/dapper) /
deb-src [http://wxpython.wxcommunity.com/apt/ubuntu/dapper](http://wxpython.wxcommunity.com/apt/ubuntu/dapper) /



and i honestly dont know how the hell python got on there.

---

### Post by Halonut1 on 2007-05-19
Ok, i #'ed out the python and CD rom lines, it seemed to have work, is it possible to just cut them lines out all together?

---

### Post by H.E. Pennypacker on 2007-05-20
> **Halonut1 said:**
> Ok, i #'ed out the python and CD rom lines, it seemed to have work, is it possible to just cut them lines out all together?

Sure, theoretically, you could remove ALL lines, and still be fine, but you shouldn't do that.  You could, being practical, remove only lines that were not originally there.  That includes the CD-rom, and anything related to Python.

You likely used software that changed things.

---

### Post by Halonut1 on 2007-05-20
> **H.E. Pennypacker said:**
> Sure, theoretically, you could remove ALL lines, and still be fine, but you shouldn't do that.  You could, being practical, remove only lines that were not originally there.  That includes the CD-rom, and anything related to Python.

You likely used software that changed things.

 that was what i ment. eh i got it working, best not to F($k with it right?

---

### Post by H.E. Pennypacker on 2007-05-21
> **Halonut1 said:**
> that was what i ment. eh i got it working, best not to F($k with it right?

If something is in a working state, don't mess it up.

---

