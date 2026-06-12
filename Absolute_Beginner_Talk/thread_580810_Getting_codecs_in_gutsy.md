---
title: "Getting codecs in gutsy"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by LittleLORDevil on 2007-10-19
I just installed gutsy and it was the best experience I have had installing Ubuntu but how do I install the codecs for multimedia?

---

### Post by bionnaki on 2007-10-19
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by doncristobal on 2007-10-20
A. > **bionnaki said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This does not seem to apply to my Ubuntu version: Xubuntu 7.10/Gutsy Gibbon. 

B. 
This also did not work: file:///usr/share/xubuntu-docs/codecs.html
> To install extra codecs for xine and some other restricted items, issue the following command on the terminal:
    *      sudo apt-get install libxine-extracodecs libxine1-ffmpeg libxine1-plugins ffmpeg lame faad sox mjpegtools gxineplugin flashplugin-nonfree

It produces:
> gxineplugin flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine1-ffmpeg
E: Package libxine-extracodecs has no installation candidate


It seems the packages to which the desktop guide and the www help page refer are not correct for gutsy gibbon/7.10. 

Who can help? Thanks!

---

### Post by forestpixie on 2007-10-20
take libxine-extracodecs out and it should work - it's been replaced by one ofthe others


```
sudo apt-get install libxine1-ffmpeg libxine1-plugins ffmpeg lame faad sox mjpegtools gxineplugin flashplugin-nonfree
```

---

### Post by daywalker00 on 2007-10-20
```
vinson@vinson-desktop:~$ sudo apt-get install libxine1-ffmpeg libxine1-plugins ffmpeg lame faad sox mjpegtools gxineplugin flashplugin-nonfree
[sudo] password for vinson:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxine1-ffmpeg

```

---

### Post by Maestro23 on 2007-10-20
> **daywalker00 said:**
> ```
vinson@vinson-desktop:~$ sudo apt-get install libxine1-ffmpeg libxine1-plugins ffmpeg lame faad sox mjpegtools gxineplugin flashplugin-nonfree
[sudo] password for vinson:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxine1-ffmpeg

```

Make sure your universe and multiverse repos are enabled.  System>>Admin>>Software Sources

---

### Post by avik on 2007-10-20
> **Maestro23 said:**
> Make sure your universe and multiverse repos are enabled.  System>>Admin>>Software Sources

LittleLORDevil is using Xubuntu, so I believe that won't work.  I'm not sure of the graphical way under XFCE, but you can do it manually.  In a terminal, enter:

```
sudo nano /etc/apt/sources.list
```

Uncomment (get rid of the # at the beginning of) the lines that contain universe and multiverse.  Press Control-X to save and exit.

Now do:

```
sudo apt-get update
```

Now try the above methods.

---

### Post by doncristobal on 2007-10-21
Thanks, **Maestro23,** this works! 

**avik and LitteLORDevil**, in xfce you can change the apt sources like this: Applications menu - System - Software sources. 
You can access the same sources dialog box from the menu Settings - Repositories in Synaptic.

---

