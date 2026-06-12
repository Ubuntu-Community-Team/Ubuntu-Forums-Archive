---
title: "ubuntustudio-audio: dependency problems"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by AKD on 2008-01-04
I installed Ubuntu 7.10 about a week ago on an external hard drive I had and then updated it to Ubuntu Studio using this:
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```
and I started getting many errors. Here are a few that I remember:
```
No volume control GStreamer plugins and/or devices found.
```
and
```
E: timidity: subprocess post-installation script returned error exit status 1
E: ubuntustudio-audio: dependency problems - leaving unconfigured
```

I only noticed the issue with the sound after I updated to Ubuntu Studio but I think there was a problem right after I installed it. I tried reinstalling "ubuntustudio-audio" and made sure that everything was updated but got the ladder error, I'm posting because I just have a feeling I need to reinstall Ubuntu or download the Ubuntu Studio ISO and install from that. I would like to avoid reinstallation but if it must be done it must.

If you need anymore information please tell me. I'll post it as soon as I can. Thanks.

---

### Post by AKD on 2008-01-04
I'm not one to bump my own thread but I would like to know if reinstallation is the way to go or if there is a fix so I can get back to enjoying Ubuntu.

---

### Post by perlluver on 2008-01-04
You can try sudo apt-get -f install, see if that helps out.

Also look to make sure all the packages for ubuntustudio are installed in synaptic, if you can get in there.

---

### Post by AKD on 2008-01-04
I ran what you said and ended up getting this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up timidity (2.13.2-15ubuntu1) ...
 * Starting timidity                                                             * Starting TiMidity++ ALSA midi emulation...                                   ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
                                                                         [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by perlluver on 2008-01-04
Have you run timidity --configure?

---

### Post by perlluver on 2008-01-04
Also be sure all of these are installed:
>     * ardour - Digital audio workstation (graphical gtk2 interface) (This is Ardour 2)
    * ardour-i686 - Digital audio workstation (graphical gtk2 interface) [i686] (This is Ardour 2)
    * ubuntustudio-desktop - Makes up our base desktop install.
    * ubuntustudio-audio - Ubuntu Studio audio package
    * ubuntustudio-audio-plugins - Ubuntu Studio audio plugins package
    * ubuntustudio-graphics - Ubuntu Studio graphics package
    * ubuntustudio-video - Ubuntu Studio video package
    * ubuntustudio-artwork - UbuntuStudio themes and artwork
    * ubuntustudio-gdm-theme - Ubuntu Studio GDM theme
    * ubuntustudio-icon-theme - UbuntuStudio Icon theme
    * ubuntustudio-look - Ubuntustudio look (metapackage)
    * ubuntustudio-session-splashes - Ubuntu Studio Session splashes
    * ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
    * ubuntustudio-screensaver - Ubuntu Studio's floating logo screensaver
    * ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
    * ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
    * usplash-theme-ubuntustudio - Usplash theme for Ubuntustudio
    * wired - Audio creation free software for Linux


---

### Post by AKD on 2008-01-04
> **perlluver said:**
> Have you run timidity --configure?

I have not done much beyond what I have already said. I was getting help from a friend of mine but do to a time difference, me USA, him Australia, I couldn't always get a hold of him when needed.

---

### Post by perlluver on 2008-01-04
Maybe this thread will help you out a little more [How To Install Ubuntustudio]("http://ubuntuforums.org/showthread.php?p=4073372#post4073372")

---

### Post by AKD on 2008-01-04
> **perlluver said:**
> Also be sure all of these are installed:

Yes, I have all of those installed.

---

### Post by AKD on 2008-01-04
> **perlluver said:**
> Maybe this thread will help you out a little more [How To Install Ubuntustudio]("http://ubuntuforums.org/showthread.php?p=4073372#post4073372")

I'll check it out but the way things are going I'm starting to think I should just reinstall and see what happens. I didn't really do much so it won't be a huge lose, just a hassle.

---

### Post by perlluver on 2008-01-04
> **AKD said:**
> I'll check it out but the way things are going I'm starting to think I should just reinstall and see what happens. I didn't really do much so it won't be a huge lose, just a hassle.

Try that thread, maybe your friend could help you too.  At worst back up and do a fresh install.

---

### Post by AKD on 2008-01-04
> **perlluver said:**
> Try that thread, maybe your friend could help you too.  At worst back up and do a fresh install.

I'll be using that thread but as for my friend he is kind of stumped. The last message I got from him on the issue he said:
> I have never come across "ubuntustudio-audio", but a dependency problem could mean that something has been removed. You may also want to check your "sources" and see if any of your repositories are unchecked (that you used earlier).
I did just that and everything seemed to be fine. He also told me to do sudo apt-get upgrade and sudo apt-get update which I did but no good. I was surprised it stumped him, who has Linux running on pretty much everything in is house from his iPhone to his toaster.

---

### Post by mpgarate on 2008-05-04
I had this problem too, with none of these solutions working. It worked, however, after I closed rhythmbox, so I assume it had to do with the sound card being busy.

---

