---
title: "Problem playing DVD's"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by jaytek13 on 2008-01-23
So, I installed ubuntu restricted extras, went through the process of installing libdvdcss2 from medubuntu or whatever, and am still having a bit of a problem. Totem/xine simply will not play them, stating that the dvd is encrypted and maybe I'm trying to play it w/o libdvdcss2 (which I'm not). VLC will play it but only if I select the option to not bring up menus and only play the dvd.

Anyways, is there a way to get past this so I can bring up my menus, too?

---

### Post by John.Michael.Kane on 2008-01-23
> **jaytek13 said:**
> So, I installed ubuntu restricted extras, went through the process of installing libdvdcss2 from medubuntu or whatever, and am still having a bit of a problem. Totem/xine simply will not play them, stating that the dvd is encrypted and maybe I'm trying to play it w/o libdvdcss2 (which I'm not). VLC will play it but only if I select the option to not bring up menus and only play the dvd.

Anyways, is there a way to get past this so I can bring up my menus, too?

You might want to make sure libdvdnav is installed.

Here is the command I used when testing for dvd playback, it might be of some use.
```
sudo aptitude install totem-xine libxine1-ffmpeg libavifile-0.7c2 gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly libdvdcss2 libdvdnav4
```

---

### Post by jaytek13 on 2008-01-23
Well, a simply copy/paste revealed a few of the programs you have installed I did not... so I installed them, and now both totem/xine and menus w/ vlc are working.


So, thanks! That's good enough for me.


And just for informations sake, you're installation line resulted in :

The following packages are unused and will be REMOVED:
  dbus-x11 kde-icons-oxygen kdebase-runtime-data 
  kdebase-runtime-data-common kdebase-workspace-data kdelibs5-data 
  kdepimlibs-data libcapseo0 libcaptury0 libclucene0 libexiv2-0 libgpgme11 
  libkonq5-templates libmysqlclient15off libopenexr2c2a libphonon4 libpq5 
  libpth20 libqimageblitz4 libqt4-core libqt4-gui libqt4-qt3support 
  libqt4-sql libraptor1 librasqal0 librdf0 libsoprano4 libsqlite0 
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 mysql-common 

The following packages have been automatically kept back:
  libavcodec1d libavformat1d libavutil1d libpostproc1d 

The following NEW packages will be installed:
  libavifile-0.7c2


So I don't have any idea what was wrong and am not even going to think about it.

---

