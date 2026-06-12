---
title: "Install Flash In Konqueror"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by nirpius on 2008-01-01
Is there any easy way to do this?

I've spent all day trying to follow guides online and they are all just confusing me.

I followed the link KOnqueror gave me and I was presented with 3 files, one was tar.gz - I tried to extract this and got nowhere. ONe was an rpm so I installed alien but then couldn't find it anywhere so I didn't know how to run that one either. THelast was called a .yum which sounds very tasty and nice but I have no idea what it means.

Does anyone know how this is meant to be done? I did on Firefox really easily...

---

### Post by por100pre1 on 2008-01-01
Be sure that the firefox plugin is detected:

```
kate ~/.kde/share/apps/nsplugins/cache
```

look the opened file for something like this:

```
[/home/YOURUSERNAME/.mozilla/plugins/flashplugin-alternative.so]
application/x-shockwave-flash:swf:Shockwave Flash
application/futuresplash:spl:FutureSplash Player
```

if it is NOT present be sure to add it, replacing YOURUSERNAME with your actual user name and save.

Be sure to verify that flashplugin-alternative.so is present in /home/YOURUSERNAME/.mozilla/plugins/ .

---

### Post by nirpius on 2008-01-01
My home folder doesn't have that folder you mentioned. I get home/MYUSERNAME/.mozilla/ then all I have in there is one folder called firefox with no plugin folder in any of it's subfolders

---

### Post by nirpius on 2008-01-01
> **por100pre1 said:**
> Be sure that the firefox plugin is detected:

```
kate ~/.kde/share/apps/nsplugins/cache
```

I entered that and got

```

[/usr/lib/firefox/plugins/libvlcplugin.so]
audio/mpeg:mp2,mp3,mpga,mpega:MPEG audio
audio/x-mpeg:mp2,mp3,mpga,mpega:MPEG audio
video/mpeg:mpg,mpeg,mpe:MPEG video
video/x-mpeg:mpg,mpeg,mpe:MPEG video
video/mpeg-system:mpg,mpeg,mpe,vob:MPEG video
video/x-mpeg-system:mpg,mpeg,mpe,vob:MPEG video
video/mpeg4:mp4,mpg4:MPEG-4 video
audio/mpeg4:mp4,mpg4:MPEG-4 audio
application/mpeg4-iod:mp4,mpg4:MPEG-4 video
application/mpeg4-muxcodetable:mp4,mpg4:MPEG-4 video
video/x-msvideo:avi:AVI video
video/quicktime:mov,qt:QuickTime video
application/x-ogg:ogg:Ogg stream
application/ogg:ogg:Ogg stream
application/x-vlc-plugin:vlc:VLC plugin
video/x-ms-asf-plugin:asf,asx:Windows Media Video
video/x-ms-asf:asf,asx:Windows Media Video
application/x-mplayer2::Windows Media
video/x-ms-wmv:wmv:Windows Media
application/x-google-vlc-plugin::Google VLC plugin
audio/wav:wav:WAV audio
audio/x-wav:wav:WAV audio
audio/3gpp:3gp,3gpp:3GPP audio
video/3gpp:3gp,3gpp:3GPP video
audio/3gpp2:3g2,3gpp2:3GPP2 audio
video/3gpp2:3g2,3gpp2:3GPP2 video
[/usr/lib/firefox/plugins/mplayerplug-in-dvx.so]
video/divx:divx:DivX Media Format
video/vnd.divx:divx:DivX Media Format
[/usr/lib/firefox/plugins/mplayerplug-in-qt.so]
video/quicktime:mov:Quicktime
video/x-quicktime:mov:Quicktime
image/x-quicktime:mov:Quicktime
video/quicktime:mp4:Quicktime
video/quicktime:sdp:Quicktime - Session Description Protocol
application/x-quicktimeplayer:mov:Quicktime
application/smil:smil:SMIL
[/usr/lib/firefox/plugins/mplayerplug-in-rm.so]
audio/x-pn-realaudio:ram,rm:RealAudio
application/vnd.rn-realmedia:rm:RealMedia
application/vnd.rn-realaudio:ra,ram:RealAudio
video/vnd.rn-realvideo:rv:RealVideo
audio/x-realaudio:ra:RealAudio
audio/x-pn-realaudio-plugin:rpm:RealAudio
application/smil:smil:SMIL
[/usr/lib/firefox/plugins/mplayerplug-in-wmp.so]
application/asx:*:Media Files
video/x-ms-asf-plugin:*:Media Files
video/x-msvideo:avi,*:AVI
video/msvideo:avi,*:AVI
application/x-mplayer2:*:Media Files
application/x-ms-wmv:wmv,*:Microsoft WMV video
video/x-ms-asf:asf,asx,*:Media Files
video/x-ms-wm:wm,*:Media Files
video/x-ms-wmv:wmv,*:Microsoft WMV video
audio/x-ms-wmv:wmv,*:Windows Media
video/x-ms-wmp:wmp,*:Windows Media
video/x-ms-wvx:wvx,*:Windows Media
audio/x-ms-wax:wax,*:Windows Media
audio/x-ms-wma:wma,*:Windows Media
application/x-drm-v2:asx,*:Windows Media
audio/wav:wav,*:Microsoft wave file
audio/x-wav:wav,*:Microsoft wave file
[/usr/lib/firefox/plugins/mplayerplug-in.so]
video/mpeg:mpg,mpeg:MPEG
audio/mpeg:mpg,mpeg:MPEG
video/x-mpeg:mpg,mpeg:MPEG
video/x-mpeg2:mpv2,mp2ve:MPEG2
audio/x-mpeg:mpg,mpeg:MPEG
audio/mpeg2:mp2:MPEG audio
audio/x-mpeg2:mp2:MPEG audio
video/mp4:mp4:MPEG 4 Video
video/3gpp:mp4,3gp:MPEG 4 Video
application/x-ogg:ogg:Ogg Vorbis Media
audio/ogg:ogg:Ogg Vorbis Audio
audio/x-ogg:ogg:Ogg Vorbis Audio
application/ogg:ogg:Ogg Vorbis / Ogg Theora
audio/flac:flac:FLAC Audio
audio/x-flac:flac:FLAC Audio
video/fli:fli,flc:FLI animation
video/x-fli:fli,flc:FLI animation
video/x-flv:flv:Flash Video
video/vnd.vivo:viv,vivo:VivoActive
application/x-nsv-vp3-mp3:nsv:Nullsoft Streaming Video
audio/x-mod:mod:Soundtracker
audio/basic:au,snd:Basic Audio File
audio/x-basic:au,snd:Basic Audio File
[/usr/lib/mozilla/plugins/libflash-mozplugin.so]
application/x-shockwave-flash:swf:Flash Plugin
application/futuresplash:spl:Future Splash

```

---

### Post by por100pre1 on 2008-01-01
> **nirpius said:**
> My home folder doesn't have that folder you mentioned. I get home/MYUSERNAME/.mozilla/ then all I have in there is one folder called firefox with no plugin folder in any of it's subfolders

Check if it is present in /usr/lib/mozilla/plugins/ . Verify that flashplugin-nonfree is already installed in Adept.

---

### Post by nirpius on 2008-01-01
I have installed flashplugin-nonfree but I can't find any flash plugin in that folder either, I've got VLC, TOTEM, JAVA (even though Java doesn't work) but no flash

---

### Post by nirpius on 2008-01-01
I just rebooted and now instead of having nothing on youtube, I get a grey box which is better than nothing I suppose. Same thing happens on other flash websites too. Also, whenever I open a page with flash I get a crash message saying that nspluginviewer has broken. I googled it and apparently it's unworkable - maybe I should just bite the bullet and use Firefox?

---

### Post by por100pre1 on 2008-01-01
> **nirpius said:**
> I just rebooted and now instead of having nothing on youtube, I get a grey box which is better than nothing I suppose. Same thing happens on other flash websites too. Also, whenever I open a page with flash I get a crash message saying that nspluginviewer has broken. I googled it and apparently it's unworkable - maybe I should just bite the bullet and use Firefox?

The previous mentioned plugins are actually symbolic links to /etc/alternatives/mozilla-flashplugin . It seems you have another issue with Flash. Are you using 64bit Ubuntu? :-k

---

### Post by nirpius on 2008-01-01
I am using the i386 version, not 64 bit. I had a look at /etc/alternatives and I didn't have mozilla-flashplugin. Is this my problem?

---

### Post by erythrocyte on 2008-05-01
Hi there fellas :) . I have Kubuntu 8.04 LTS which comes with KDE 3.5.9 . On my Konqueror 3.5.9, flash behaviour is erratic. Sometimes I can see flash videos and animations and at other times all I get is a grey box with sound but no picture.

I did a little searching and came across this:

[http://docs.kde.org/stable/en/kdebase-runtime/faq/webbrowser.html#id2558174]("http://docs.kde.org/stable/en/kdebase-runtime/faq/webbrowser.html#id2558174")

You think this could be the problem?

Any help would be greatly appreciated. Thanks!

Here are the contents of my xorg.conf :-

```

#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
            Modes       "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

---

