---
title: "Toshiba Satellite 2545CDS - NO PROPER SCREEN DISPLAY AND NO SOUND"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Enaid on 2006-09-30
Hi there,
[Posted erroneously on laptop support]
I have just installed Ubuntu 5.10 (after burning a CD from the disk image abvailable at the website) on a Toshiba Sattellite 2545CDS with a 64MB memory upgrade (96 MB RAM).

Ubuntu has been installed as the only operating system.

No problems at all when installing Ubuntu seems to have seen the video card and even my router.

Unfortunately, the only available screen resolution is the very low 640x480 (from my memory). The installation detected that this computer could display, at least, 800x600.

When I go to the preferences, the low resolution is the only resolution available.

How comeubuntu have not detected the available LCD?

There is no sound at all either.

I would certainly appreciate some help as in this way the computer has a very low usability.

Thank you very much in advance.

Enaid

---

### Post by theknave on 2006-09-30
If you're having the same problem that I was, you may have to lower the number of colours in order to get yourself more display options. Otherwise, you may have just disabled the desired resolutions. Try using the command:

```
sudo dpkg-reconfigure xserver-xorg
```

It should open a blue screen that will let you edit these options.

EDIT: First off, I've only been on Ubuntu for about a week, so don't expect much from me. As far as the sound thing goes, I had the same issue, and even my Windows partition didn't recognize that I had an onboard sound card, so I bought a new one. I've wanted surround sound for awhile anyway.

---

### Post by Enaid on 2006-10-01
> **theknave said:**
> If you're having the same problem that I was, you may have to lower the number of colours in order to get yourself more display options. Otherwise, you may have just disabled the desired resolutions. Try using the command:

```
sudo dpkg-reconfigure xserver-xorg
```

It should open a blue screen that will let you edit these options.

EDIT: First off, I've only been on Ubuntu for about a week, so don't expect much from me. As far as the sound thing goes, I had the same issue, and even my Windows partition didn't recognize that I had an onboard sound card, so I bought a new one. I've wanted surround sound for awhile anyway.


Thank you for your prompt reply. I have tried to use the code you suggested, unfortunately, being a laptop, I do not have all the details that thing asks for (LCD screen name, etc) and going for the defaults did not help. So, I am stuck there.

On the audio, I have found a posting that might be useful (especially because the poster changed audio cards and it did not manage to have any sound). If you have not, you might be interested in reading

[http://www.ubuntuforums.org/showpost.php?p=904515&postcount=7](http://www.ubuntuforums.org/showpost.php?p=904515&postcount=7)

Hope this helps. (I will continue battling with xorg.conf file.)

Best of luck for you (and me),

Enaid

---

