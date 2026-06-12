---
title: "DVD Ripping software?"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-12-01
Hi guys,


Do any any of ye know any easy to use software packages for ripping dvds?

---

### Post by Mr Green on 2006-12-01
Not that I have any clue at all but I think a lot of people are running DVDShrink under WINE to do this.

---

### Post by AndyCooll on 2006-12-01
dvd-rip

I think it's in the repositaries.

:cool:

---

### Post by meniscus on 2006-12-01
> How to install DVD Ripper (dvd::rip)

    * Read #General Notes
    * Read #How to add extra repositories
    * Read #How to install Multimedia Codecs
    * Read #How to install DVD playback capability
    * Read #How to install Multimedia Player (Totem) with Plug-in for Mozilla Firefox
    * Read #How to install RAR Archiver (rar) 

```
sudo apt-get install dvdrip vcdimager cdrdao subtitleripper
sudo ln -fs /usr/bin/rar /usr/bin/rar-2.80
gksudo gedit /usr/share/applications/dvdrip.desktop
```

    * Insert the following lines into the new file 

```
[Desktop Entry]
Name=dvd::rip 
Comment=dvd::rip
Exec=dvdrip
Icon=/usr/share/perl5/Video/DVDRip/icon.xpm
Terminal=false
Type=Application
Categories=Application;AudioVideo;

```
    * Save the edited file
    * Applications -> Sound & Video -> dvd::rip 

Thanks!
I got the above here [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_Ripper_.28dvd::rip29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_Ripper_.28dvd::rip29)




When  i put 

```
gksudo gedit /usr/share/applications/dvdrip.desktop
```


It opened the blank file alright but wouldnt let me save it after i pasted the settings in.

I went 

```
sudo gedit /usr/share/applications/dvdrip.desktop

```



and it let me save the same settings!

will it work? 
Whats the difference between ```
sudo gedit
``` and ```
gksudo gedit
```

---

### Post by Oki on 2006-12-01
I have not yet ripped any dvd in Linux, but I have noticed the following tips;

A good guide: [http://ubuntuforums.org/archive/index.php/t-7057.html](http://ubuntuforums.org/archive/index.php/t-7057.html)

Shows how to install DVD Shrink 3.2 and DVD Decrypter in Ubuntu 
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

Program to convert AVI to DVD format:
KmediaFactory: [http://susku.pyhaselka.fi/damu/software/kmediafactory/index.html](http://susku.pyhaselka.fi/damu/software/kmediafactory/index.html)

How to make ISO file from a dvd;
[http://ubuntuforums.org/archive/index.php/t-6509.html](http://ubuntuforums.org/archive/index.php/t-6509.html)

Other programs:
acidrip: [http://untrepid.com/acidrip/](http://untrepid.com/acidrip/)
k9copy: [http://k9copy.sourceforge.net/](http://k9copy.sourceforge.net/)
dvd::rip: [http://www.exit1.org/dvdrip](http://www.exit1.org/dvdrip)
I think most people like dvd::rip best. 

Have fun:-)

---

### Post by echo $USER on 2006-12-01
[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

xDVDShrink native gnu/linux app... build from Source... nothing better... no wine needed.  You can run it from bash or gui.

---

### Post by meniscus on 2006-12-05
Thanks very much lads

---

### Post by deep.tinker77 on 2006-12-05
Or you can just install Automatix2 and let it get and install everything you need for you. Good luck.

---

### Post by 3rdalbum on 2006-12-05
I recommend Acidrip - it seems to work better than anything else I've tried, and although it has a lot of confusing options, there are good tooltips and little features that help you.

Dvd:rip can optionally rip *just* the audio from a DVD - which makes it invaluable for creating audio CDs from concert DVDs.

---

### Post by meniscus on 2006-12-05
When i installed acidrip it suggested that "[COLOR="Red"]libdvdcss[/COLOR]"
and "[COLOR="Red"]w32codecs[/COLOR]" be installed.

I tried sudo apt-get install on both and this is the error i got. Why is this?


```
Setting up acidrip (0.14-0.0ubuntu1) ...
meniscus@meniscot:~$ sudo apt-get install libdvdcss
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss has no installation candidate
meniscus@meniscot:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

```

---

### Post by nandasunu on 2006-12-05
> **meniscus said:**
> When i installed acidrip it suggested that "[COLOR="Red"]libdvdcss[/COLOR]"
and "[COLOR="Red"]w32codecs[/COLOR]" be installed.

I tried sudo apt-get install on both and this is the error i got. Why is this?


make sure you have all the restricted repos (universe & multiverse) enabled in synaptic: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by RMorris78 on 2006-12-05
i think the new one is libdvdcss2

try

sudo apt-get cache libdvdcss

---

### Post by Bloch on 2006-12-05
That's because these software items are restricted by copyright, and it may be illegal to use them in some couintruies.

As the warning suggests, you need to "enable these repositories." Open Suystem>Administration>Software Properties and mgo down the list to make sure that universe and multiverse for bunay files are ticked. (Don't bother ticking source or backports)

Then try the commands again

---

### Post by Jagot on 2006-12-05
w32codecs is not in the Ubuntu repositories.  To install:

```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

For libdvdcss, you will need to install the libdvdread3 package, which is available in the repos:

```
sudo aptitude update && sudo aptitude install libdvdread3
```

And then enter this command:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by meniscus on 2006-12-07
> And then enter this command:



```
sudo /usr/share/doc/libdvdread3/install-css.sh

```



thanks>Everything seemed alright for the first command bu the second 1 returned an error?
```
meniscus@meniscot:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
sudo: /usr/share/doc/libdvdread3/install-css.sh: command not found
```

---

### Post by ubunlilluz on 2006-12-07
but does dvdrip allow only to rip? I think that it converts to avi too.

---

