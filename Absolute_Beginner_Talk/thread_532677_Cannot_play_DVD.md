---
title: "Cannot play DVD"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by aspen_dv on 2007-08-23
Following the Feisty guide, I have installed VLC, Mplayer, (with all codes) but none can't play DVD.  . Some DVD plays for a little while then VLC just automatically stops playing. Also, sometimes when I fast forward, it stops too. Some DVD's it cant even start. I don't know if it's Feisty bug or not, but I've never had this problem with previous version Edgy. 
Does anyone know if I have to set up the video codes within those program or something?
Thanks

---

### Post by daradib on 2007-08-23
To play most DVDs you'll need the libdvdcss2 package. This package is available using Medibuntu (see [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)).

If DVD playback fails, and you've never played any DVD before on your system, you may need the regionset package to initially set the drive's region (not likely your problem since you could play DVDs before).

Please specify what Feisty Guide. This one ([http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty))? Exactly what additional packages have you installed (that are not included by default in Ubuntu)?

Please tell me if this did or didn't help you.

---

### Post by aspen_dv on 2007-08-23
Yes, that's the guide I followed:

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh

    * Install xine backend for Totem (if you are using Totem): 

sudo apt-get install totem-xine

    * Finish installing modules: 

sudo apt-get install libdvdcss2

One thing I notice after running sudo /usr/share/doc/libdvdread3/install-css.sh
is that it seems like going back to previous version of libdvdcss2. But does not matter which version, i still have the issue. For additional packages, I am not sure because I installed some other packages for various software too (also from that guide). 
I could wipe out everything and reinstall Feisty from fresh, but it's PITA. Again, never have the problem when using Edgy.
Thanks for all your help.

---

### Post by daradib on 2007-08-23
Not sure if this will help you, but you could try installing the regionset package (availabe in the Ubuntu Universe Repository) and see what region the drive is set to.

You could also try the following (copied from Ubuntu Feisty Guide)

```
sudo apt-get install libdvdnav4 libdvdplay0 libdvdread3 libdvdcss2
sudo apt-get remove --purge totem totem-gstreamer
sudo apt-get install totem-xine

```

Meanwhile I'll bump you in case someone can find a better answer.

---

