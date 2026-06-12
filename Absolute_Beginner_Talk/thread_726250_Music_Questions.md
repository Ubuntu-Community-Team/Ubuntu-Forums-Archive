---
title: "Music Questions"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by runnerdi7 on 2008-03-16
I just transfered all of my itunes music files onto my new ubuntu system, and the format is not supported.  What file converters are out there, so i can listen to the music i payed for.  Also rhythembox does not work for me, I deleted it thinking i could possibly download a different media player but none seem to let me download them from add/remove, every time i try it says they arent supported on my computer type i386 or

Cannot install 'mplayer'

This application conflicts with other installed software. To install 'mplayer' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

and im lost from there.  Also movie player wont let me play my divx files or dvds?  Any help?

---

### Post by sumguy231 on 2008-03-16
You should install the 'ubuntu-restricted-extras' package through Synaptic, because that will give you pretty much every music codec that's out there. But from the sound of it, you've broken something with your packaging system so that needs to be taken care of first. Can you post:
1.) The output of the command:
```
sudo apt-get install rhythmbox
```
2.) The contents of the file /etc/apt/sources.list ?

---

### Post by prshah on 2008-03-16
> **runnerdi7 said:**
> I just transfered all of my itunes music files onto my new ubuntu system, and the format is not supported.  What file converters are out there, so i can listen to the music i payed for.  Also rhythembox does not work for me, I deleted it thinking i could possibly download a different media player but none seem to let me download them from add/remove, every time i try it says they arent supported on my computer type i386 or

Cannot install 'mplayer'

This application conflicts with other installed software. To install 'mplayer' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

and im lost from there.  Also movie player wont let me play my divx files or dvds?  Any help?

What format are your music files in? MP3? aac? In any case, installing the restricted extras  ```
sudo apt-get install ubuntu-restricted-extras
``` will pull in support for most audio and video formats.

If you prefer, you can also do this from Synaptic, and resolve whatever conflicts you have along the way. Synaptic Package Manager can be found under System->Administration.

For "cannot be installed...(i386) message, refer [http://ubuntuforums.org/showthread.php?t=592031](http://ubuntuforums.org/showthread.php?t=592031)

> I had the same problem when using 7.10 and fixed it by clicking on the "Preferences" button in the lower left of the "Add/Remove Applications" window and enabling all the "Downloadable from the Internet" sources.

---

### Post by sumguy231 on 2008-03-16
Also, for playing DVDs, read this:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by runnerdi7 on 2008-03-16
so i threw that line into terminal and got this...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rhythmbox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rhythmbox has no installation candidate

---

### Post by Oldsoldier2003 on 2008-03-16
> **runnerdi7 said:**
> so i threw that line into terminal and got this...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rhythmbox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rhythmbox has no installation candidate

make sure you have the first four repositories enabled on the first page in System>Administration>Software Sources

then in a teminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install rhythmbox
```

---

### Post by runnerdi7 on 2008-03-16
ok so i've got rhythembox and banshee downloaded, i also took care ot the i386 deal that i was getting, downloaded the codec to get my music and divX movies to play.  Thank you so much guys, i really appreciate it.

---

### Post by Oldsoldier2003 on 2008-03-16
> **runnerdi7 said:**
> ok so i've got rhythembox and banshee downloaded, i also took care ot the i386 deal that i was getting, downloaded the codec to get my music and divX movies to play.  Thank you so much guys, i really appreciate it.

Glad to hear you got it sorted out :)

---

### Post by runnerdi7 on 2008-03-16
all right i have one more issue, movie player, wont play my dvd's.  I have the "ugly" codec set downloaded which it suggest but still nothing.  It plays divX just not dvd from my optical. Any suggestions?

---

### Post by angry_johnnie on 2008-03-17
> **runnerdi7 said:**
>  It plays divX just not dvd from my optical. Any suggestions?


Have you installed libdvdcss2 ?

---

