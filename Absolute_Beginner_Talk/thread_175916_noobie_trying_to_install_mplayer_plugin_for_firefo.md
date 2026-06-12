---
title: "noobie trying to install mplayer plugin for firefox"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by keheikev on 2006-05-14
:KS Please dont laugh too loudly. Ive got the files downloaded from http//:mplayer-plugin.sourceforge.net called mplayer-plugin.tar.gz and then a couple other tar balls which purport to be skins and essential codecs. I uziped the folder to the desktop but I am lost on what to do next. Is this a source code or do I just configure it to install with synaptic.
TIA
Keheikev
Good morning from the Golden State of California...
I am using Ubuntu 5.10 Breezy.



I am trying to install a simple streaming plugin for firefox. But now I 
> have a bunch o files to install its the mplayer plugin for mozilla how 
> do  I do it?
> keheikev
> should I use apt get instead?
What I want to install is this...can some one talk me down off this high building so I can get back to my computer and do what I need to do? My eyes are rolling right now.
[http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/) this is the website to install the plugin for firefox. what to do next.

---

### Post by aysiu on 2006-05-14
Yes, use *apt-get* instead.

I would recommend reading these two links:

[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by keheikev on 2006-05-14
I read [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) but I already installed it with synaptic after adding multiverse. It still doesnt play. I have a amd 2100 so I installed mplayer k6 after reading from the wiki how to install the program. It uninstalled the mplayer plugin that I had just installed as the K6 one was the one recommended for my processor. I typedthe configuration edits from the wiki
[https://wiki.ubuntu.com/MplayerInstallHowto](https://wiki.ubuntu.com/MplayerInstallHowto)
Configuration

Configuring mplayer and gmplayer is not obvious to the casual observer. The configurations options given below are mostly taken from Ubuntu 6.04, and should work on most computers. To use this configuration, first open your mplayer configuration file:

gedit ~/.mplayer/config

Then cut and paste the following block into the file:

# Specify default video driver (see -vo help for a list).
vo=xv,sdl,x11

# Specify default audio driver (see -ao help for a list).
ao=alsa,oss,sdl,esd,arts

# Drop frames to preserve audio/video sync.
framedrop = yes

# get a default OSD font from fontconfig
fontconfig = yes
font = "Sans"
subfont-text-scale = 3
but it would not allow me to save the gedit file to home it gives the error
Could not save the file "/home/kevin/.mplayer/config"


also had a bunch of stuff in the terminal window after the first try of the above not sure where it came from but it didnt come up on the next try of doing the config edit.
I peaked at the terminal window and there was some stuff there after the gedit window command
I/O warning : failed to load external entity "/home/kevin/.gnome2/yelp-bookmarks.xbel"

(gnome-help:14036): Gtk-CRITICAL **: gtk_stock_lookup: assertion `stock_id != NULL' failed
Unmatched element: citerefentry
Unmatched element: refentrytitle
Unmatched element: citerefentry
Unmatched element: refentrytitle
embed_open_uri_cb uri=file://///usr/share/gnome/help/gedit/C/gedit.xml#gedit-usage
 Sorry this is so long 
TIA
Keheikev:KS 
good morning

---

### Post by catlett on 2006-05-14
[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) Follow this link and read the thread. If you install the script it pertains to it will make your life easy. You won't learn anything but you will have firefox with all it's plug ins.

P.S. I keep forgetting alot of people have dapper now. If you have dapper nevermind it only works with breezy.

---

### Post by keheikev on 2006-05-14
[QUOTE=catlett][http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) Follow this link and read the thread. If you install the script it pertains to it will make your life easy. You won't learn anything but you will have firefox with all it's plug ins.

P.S. I keep forgetting alot of people have dapper now. If you have dapper nevermind it only works with breezy.[/QUOTE]
edit ~/.mplayer/config

Then cut and paste the following block into the file:

# Specify default video driver (see -vo help for a list).
vo=xv,sdl,x11

# Specify default audio driver (see -ao help for a list).
ao=alsa,oss,sdl,esd,arts

# Drop frames to preserve audio/video sync.
framedrop = yes

# get a default OSD font from fontconfig
fontconfig = yes
font = "Sans"
subfont-text-scale = 3
but it would not allow me to save the gedit file to home it gives the error
Could not save the file "/home/kevin/.mplayer/config"
I tried gksudo gedit ~/.mplayer.config but it still would not allow me to save the configuration changes. I am sure I have a root password set but there was some errors that came up on terminal about not recognizing the 
(gedit:18216): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
:confused:

---

### Post by keheikev on 2006-05-16
These are the exact directions from the Ubuntu wiki  at [https://wiki.ubuntu.com/MplayerInstallHowto](https://wiki.ubuntu.com/MplayerInstallHowto)
edit ~/.mplayer/config

Then cut and paste the following block into the file:

# Specify default video driver (see -vo help for a list).
vo=xv,sdl,x11

# Specify default audio driver (see -ao help for a list).
ao=alsa,oss,sdl,esd,arts

# Drop frames to preserve audio/video sync.
framedrop = yes

# get a default OSD font from fontconfig
fontconfig = yes
font = "Sans"
subfont-text-scale = 3
but it would not allow me to save the gedit file to home it gives the error
Could not save the file "/home/kevin/.mplayer/config"
I tried sudo gedit but it kept telling me there is no file mplayer in my home dir. So should I just enter the above in a folder I create in home/kevin or do I need all the stuff from confg in the etc file.  I am wondering why synaptic did not create a folder in home/kevin/.mplayer 
I tested gedit and it will save files so I dont think that gedit is the problem usually mplayer isnt so hard to install is it? I want to learn a few things and avoid the automatix script way as I think it will help me to navigate with terminal.
Keheikev
:KS from the golden state.

---

### Post by dmizer on 2006-05-16
check to see if there is actually a file at ~/.mplayer called config

if not, i found mine at /etc/mplayer ... try there (note, mine was called mplayer.conf).  no it's not usually this difficult, but things change before the documentation can be updated sometimes.

if you open up the config file and there is no text in it ... you haven't found the right one yet.

if you look at the text in the config file in etc, it states that:
if there is a ~/.mplayer/config ... then it will override whatever is written at /etc/mplayer/mplayer.conf
if there is nothing at ~/.mplayer/config, it will use the /etc/mplayer/mplayer.conf

it is also necessary to delete all the text that you find in the file before adding the given configuration.

also, make note of what audio module you use, and in this line:
```
# Specify default audio driver (see -ao help for a list).
ao=alsa,oss,sdl,esd,arts
```
delete all but the module you use to drive your audio. so for example, if your audio module is alsa (most are) it should read "ao=alsa".

edit to add ... i just got my mplayer to work no problem by pasting the given text to /etc/mplayer/mplayer.conf.  it was actually much easier to accomplish on this machine where i don't have firefox 1.5 installed.  was just a matter of finding the mplayer configure file.

---

