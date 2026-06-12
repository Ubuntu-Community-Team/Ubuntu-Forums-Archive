---
title: "WVP2 codecs for playing WMVs?"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Oreo on 2006-08-01
I have a WMV that was created by MSMovieMaker. When I try to play it using Totem I get the following error message:

[INDENT]Video codec 'WVP2' is not handled. You might need to install additional plugins to be able to play some types of movies[/INDENT]

Also, many of my movies play too bright, washed out in color. VLC does better than Totem in that area for me. Why? Any fixes?

Thanks,
Oreo

---

### Post by bluespymaster on 2007-06-16
1.  Install MPlayer.
```
sudo apt-get install mplayer
```

2.  Install Win32 Codecs.
```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

reference: [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

3. At this point, MPlayer will work but not GMPlayer.  Here is the fix:

Edit ~/.mplayer/gui.conf
```
gedit ~/.mplayer/gui.conf
```
Change the driver for video_out to **xv**
```
vo_driver = "xv"
```
reference: [http://ubuntuforums.org/showthread.php?t=440638](http://ubuntuforums.org/showthread.php?t=440638)

---

### Post by grantbuntu on 2008-03-10
NB the new link is now:
```
http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.1_i386.deb
```

---

### Post by kostkon on 2008-03-10
You have to install the *w32codecs* package that **you should better** get it from the [*Medibuntu* repository]("http://medibuntu.org/"). Please follow [these instructions on how to add it to your software sources list]("https://help.ubuntu.com/community/Medibuntu").

After adding the repository, open *Synaptic*, search for *w32codecs* and install the package or open a terminal and give
```
sudo apt-get install w32codecs
```
After that, you will be able to play the video with *Totem*.

---

