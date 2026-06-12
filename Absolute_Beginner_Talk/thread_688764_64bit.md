---
title: "64bit"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by pedrom169 on 2008-02-05
i have installed 64bit ubuntu (7.10) onto my computer
i originally had the 32 bit version for gusty.
when i had it i used medibuntu.
but i doesnt work for me on the 64bit version
getting the error

```
wget: option requires an argument -- O
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.

```

i want all the codecs and stuff onto this pc
plus, i have heard flash or java is a ache getting on 64bit but can be done. any guides on here about this?

Cheers
Peter

---

### Post by Daveski on 2008-02-05
There is a 64 bit forum here [http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

---

### Post by JoshuaRL on 2008-02-05
Try this thread man:
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

And this one is really helpful for a lot of problems with 64 bit:
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

But Daveski is technically right, this should be in the 64bit forum.

---

### Post by crjackson on 2008-02-05
Go to your menu - Applications>Accessories>Terminal and click!

Next cut and past the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w64codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

The last line will install all the codecs and things needed to play encrypted DVD's.  If you don't want all that, then just edit the rest of the stuff out.

---

