---
title: "[SOLVED] Videos Won't Play."
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by XxBigP123xX on 2008-03-03
None of my videos will play! I installed VLC player and MP player and all they do is open really quick and close. Help?

---

### Post by jeffus_il on 2008-03-03
Open a terminal, run vlc from the command prompt and post the output here.

---

### Post by Superkoop on 2008-03-03
Type the following in the terminal, it will install what you need to watch videos.

```
sudo apt-get install ubuntu-restricted-extras
```

For DVDs see the following link:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by XxBigP123xX on 2008-03-03
> **jeffus_il said:**
> Open a terminal, run vlc from the command prompt and post the output here.

```
paul@paul-laptop:~$ vlc player
VLC media player 0.8.6c Janus

(.:15366): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
        'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat player
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000290] main input error: no suitable access module for `player'
[00000281] main playlist: nothing to play
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85
paul@paul-laptop:~$ 

```

---

### Post by XxBigP123xX on 2008-03-03
> **Superkoop said:**
> Type the following in the terminal, it will install what you need to watch videos.

```
sudo apt-get install ubuntu-restricted-extras
```

For DVDs see the following link:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

```
paul@paul-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for paul:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  liblzo1
Use 'apt-get autoremove' to remove them.

```

---

### Post by Superkoop on 2008-03-03
OK then I recommend just following this guide since you need the w32 codecs and such: [http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html)

It will be able to explain it a bit better and in more detail.

---

### Post by XxBigP123xX on 2008-03-03
> **Superkoop said:**
> OK then I recommend just following this guide since you need the w32 codecs and such: [http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html)

It will be able to explain it a bit better and in more detail.

Did the guide, still dosent play:(

---

### Post by Superkoop on 2008-03-03
Have you restarted your computer? When I was messing with the sound earlier today I needed to do a restart to make the settings get applied. 

what file format are your videos?

---

### Post by jeffus_il on 2008-03-03
Try:
```
sudo aptitude install libdvdread3
```

---

### Post by XxBigP123xX on 2008-03-03
> **Superkoop said:**
> Have you restarted your computer? When I was messing with the sound earlier today I needed to do a restart to make the settings get applied. 

what file format are your videos?

I restarted my computer and videos work! Thanks alot to both of you.

---

### Post by Superkoop on 2008-03-03
Your welcome! 
Please mark this thread as solved now, it's at the top of this thread in thread tools. It makes the forums easier to read.

---

