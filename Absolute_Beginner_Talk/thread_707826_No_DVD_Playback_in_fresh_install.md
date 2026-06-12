---
title: "No DVD Playback in fresh install"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by OZFive on 2008-02-25
SO hi there folks,

I just got a brand spanking new laptop!  YAY!  I did not even let Vista boot up onit, I just got the CD in there and went to town.  

Everythin is great, I am loving it.  Here is a glitch that I knew was coming but I knew that this place was here to help me out.  So...

I want to play a DVD. I downloaded the packages that were sggestd for DVD play and put a DVD in. The DVD mounted on the desktop and it woud still not play.  Damn.  Wel I rigt clicked the icon and selected Eject to remove the DVD and proceeded to get VLC.  I put a new DVD in and the Disc never showed up on my desktop.  Grrrrr.   So now that I have VLC I cannot play the disc as it is not mounting.  At least that is what I think is happening.

Totem give me a eror message about Hal

and VLC gives me the message about being unable to open dvdsimple

Help please!

Nevermind, after a restart the DVD was back and it works fine in Totem, VLC was pixelated for some reason.... But overall.  YAY!

---

### Post by julian67 on 2008-02-26
Can you confirm that you installed the DVD packages and VLC using apt or Synaptic? It occurs to me that if you compiled from source or used .debs from a different source that maybe you have packages that are built without hal support or with some problem with hal support. 

HAL is a Hardware Abstraction Layer. This allows applications to locate, recognise and use  the hardware that is connected or that you connect to your system, so (typically) when you plug in your thumb drive or load a CD or DVD it's recognised and the appropriate application or action is launched. 

You can check that HAL is running and seeing your devices by opening a terminal and using the command ```
lshal
```

I'm also wondering about your install CD.  If it's a CD you burned yourself then it's important to make sure the md5sum of your .iso file matches the md5sum as stated by Ubuntu (and which can be obtained from any Ubuntu download mirror). It's also important to burn the CD onto high quality CD to avoid errors. You should then check the integrity of your Ubuntu install CD before installing (this is one of the options when booting from CD).

---

### Post by jan quark on 2008-02-26
try this
```

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
```

sudo /usr/share/doc/libdvdread3/install-css.sh
```

and now open with gxine

---

### Post by sayakb on 2008-02-26
@OP
VLC is pixelated since you might have selected the X11 output mode. Select the OpenGL or default output mode for smoother pictures. 

To change display mode: Open VLC and goto Settings -> Preferences (Check the advanced options checkbox) -> Video -> Output Modules

---

### Post by OZFive on 2008-02-26
thansk all for the help, I did install the xine componet to Totem and that works just great, and changing the output to Open GL in VLC worked fine too.  This place is great.

---

### Post by pedro_orange on 2008-02-27
The easiest method for enabling all multimedia for use on your PC is simply to install:

```
sudo apt-get install ubuntu-restricted-extras
```

This package includes: 

flashplugin-nonfree [i386]
*Adobe Flash Player plugin installer *

gstreamer0.10-ffmpeg 
*FFmpeg plugin for GStreamer *

gstreamer0.10-plugins-bad 
*GStreamer plugins from the "bad" set *

gstreamer0.10-plugins-bad-multiverse 
*GStreamer plugins from the "bad" set (Multiverse Variant) *

gstreamer0.10-plugins-ugly 
*GStreamer plugins from the "ugly" set* 

gstreamer0.10-plugins-ugly-multiverse 
*GStreamer plugins from the "ugly" set (Multiverse Variant) *

libdvdread3 
*library for reading DVDs *

liblame0 
*LAME Ain't an MP3 Encoder *

msttcorefonts 
*Installer for Microsoft TrueType core fonts *

sun-java6-jre [amd64]
*Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files) *

sun-java6-plugin [i386]
*The Java(TM) Plug-in, Java SE 6 *

unrar 
*Unarchiver for .rar files (non-free version)*

---

