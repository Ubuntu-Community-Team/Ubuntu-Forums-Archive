---
title: "I have to manual install the packages,"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by ovidiu82 on 2006-02-08
1. installed the ubuntu wit the cd inside...

2. it said take the cd out please...

i said..thank you...and took it out..

3. it rebooted and installed some more files...

during installing these files it stopped at gstreamer0.8-jpeg and said there is an error and i have to manually install the packages..

I go in the system>> administratuion>> synaptic packages and i see a lot of them..

which packages do I have to install?

I cannot see my other partitioN WHICH IS FORMATED NTFS 

please help...

---

### Post by kaamos on 2006-02-08
Hello!

open *Applications->Accessories->Terminal* and type
```
sudo apt-get install ubuntu-desktop
```
that should get you the default ubuntu packages.

For ntfs you could look here: [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by nik on 2006-02-08
I would try, in a terminal,
```

sudo apt-get update

```
then
```

sudo apt-get dist-upgrade

```
as for the ntfs partition, the kernel needs to be compiled with support for this. In general you should avoid ntfs in linux, at least write support is dodgy...

EDIT: ops, too late :) That might work too... :)

---

### Post by kaamos on 2006-02-08
The kernel has *read* support for ntfs, so you don't need to compile anything to see it or copy files. Writing to ntfs is atm bad idea.

---

### Post by ovidiu82 on 2006-02-08
sudo apt-get install ubuntu-desktop

Building dependency tree... Done
ubuntu-desktop is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python2.4-tk: Depends: blt (>= 2.4z) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

us@ubuntu:~$ apt-get -f install
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


us@ubuntu:~$ :-k

---

### Post by kaamos on 2006-02-08
The latter should be "**sudo** apt-get -f install"

---

### Post by ovidiu82 on 2006-02-08
us@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  blt
Suggested packages:
  blt-demo
The following NEW packages will be installed:
  blt
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
307 not fully installed or removed.
Need to get 0B/2050kB of archives.
After unpacking 5046kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 60509 files and directories currently installed.)
Unpacking blt (from .../blt_2.4z-3ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/blt_2.4z-3ubuntu1_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive: Success
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/blt_2.4z-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kaamos on 2006-02-08
Try
```
sudo apt-get clean && sudo apt-get install -f
```

---

### Post by ovidiu82 on 2006-02-08
us@ubuntu:~$ sudo apt-get clean && sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  blt
Suggested packages:
  blt-demo
The following NEW packages will be installed:
  blt
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
307 not fully installed or removed.
Need to get 0B/2050kB of archives.
After unpacking 5046kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/pool/main/b/blt/blt_2.4z-3ubuntu1_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by ovidiu82 on 2006-02-08
So the bootable Cd is F* up?

---

### Post by kaamos on 2006-02-08
Seems like it to me.

Lets not use the cd.
```
sudo gedit /etc/apt/sources.list
```
Comment out the line with cd-rom with a "#". This line is probably at the top of the file. Save the file and then
```
sudo apt-get update
sudo apt-get install -f
```

---

### Post by ovidiu82 on 2006-02-08
Thank a lot it worked...

the system is installed and most of it seems ok..

I still have some troubles with the amaroK it doesn't play the files, and the video player ain't working either...

---

### Post by bartbes on 2006-02-08
try to install these packages: > 
gstreamer0.8-alsa - ALSA plugin for GStreamer
gstreamer0.8-audiofile - AudioFile plugin for GStreamer
gstreamer0.8-cdparanoia - cdparanoia plugin for GStreamer
gstreamer0.8-dv - DV plugin for GStreamer
gstreamer0.8-dvd - DVD plugin for GStreamer
gstreamer0.8-esd - Enlightened Sound Daemon plugin for GStreamer
gstreamer0.8-flac - FLAC plugin for GStreamer
gstreamer0.8-gnomevfs - Gnome VFS plugin for GStreamer
gstreamer0.8-gsm - GSM plugin for GStreamer
gstreamer0.8-hermes - colorspace conversion plugin for GStreamer based on hermesgstreamer0.8-jpeg - JPEG plugin for GStreamer
gstreamer0.8-misc - Collection of various GStreamer plugins
gstreamer0.8-musepack - Musepack (MPC) audio decoder plugin for GStreamer
gstreamer0.8-oss - OSS plugin for GStreamer
gstreamer0.8-plugin-apps - Simple GStreamer applications
gstreamer0.8-sdl - SDL videosink plugin for GStreamer
gstreamer0.8-speex - Speex plugin for GStreamer
gstreamer0.8-theora - Theora plugin for GStreamer
gstreamer0.8-vorbis - Vorbis plugin for GStreamer
gstreamer0.8-x - X videosink plugin for GStreamer
libgstreamer-gconf0.8-0 - GConf support for GStreamer
libgstreamer-plugins0.8-0 - Various GStreamer libraries and library plugins
gstreamer0.8-tools - Tools for use with GStreamer
libgstreamer0.8-0 - Core GStreamer libraries, plugins, and utilities
gstreamer-editor - GStreamer Pipeline Editor and other GUI tools
gstreamer0.8-a52dec - ATSC A/52 audio decoder plugin for GStreamer
gstreamer0.8-cdio - low-level CD-ROM reading and control plugin for GStreamer
gstreamer0.8-ffmpeg - FFmpeg plugin for GStreamer
gstreamer0.8-gtk - GdkPixbuf decoder plugin for GStreamer
gstreamer0.8-mad - MAD MPEG audio decoder plugin for GStreamer
gstreamer0.8-mms - mms plugin for GStreamer
gstreamer0.8-mpeg2dec - MPEG1 and MPEG2 video decoder plugin for GStreamer
gstreamer0.8-pitfdll - DLL/QTX loader plugin for GStreamer
gstreamer0.8-plugins - All GStreamer plugins
gstreamer0.8-swfdec - SWF (Macromedia Flash) decoder plugin for GStreamer
libglib2.0-cil - CLI binding for the GLib utility library 2.0, unstable version
libgstreamer0.8-ruby - GStreamer 0.8 bindings for the Ruby language
libgtksourceview1-ruby - GTKSourceView bindings for the Ruby language
gstreamer0.8-aa - AA-lib plugin for GStreamer
gstreamer0.8-artsd - aRtsd plugin for GStreamer
gstreamer0.8-caca - Colour AsCii Art library plugin for GStreamer
gstreamer0.8-doc - GStreamer documentation
gstreamer0.8-festival - Festival speech synthesis plugin for GStreamer
gstreamer0.8-jack - JACK plugin for GStreamer
gstreamer0.8-mikmod - MikMod decoder plugin for GStreamer
gstreamer0.8-sid - C64 SID decoder plugin for GStreamer
libgstreamer-gconf0.8-dev - Development files for GConf support for GStreamer
libgstreamer-plugins0.8-dev - Development files for various GStreamer library and library plugins
libgstreamer0.8-dev - GStreamer development libraries and headers
gstreamer0.8-dirac - Dirac decoder plugin for GStreamer
gstreamer0.8-faac - AAC encodingplugin for GStreamer
gstreamer0.8-faad - AAC decoding plugin for GStreamer
gstreamer0.8-lame - LAME encoder plugin for GStreamer
gstreamer0.8-plugins-multiverse - All Multiverse GStreamer plugins
gstreamer0.8-wavpack - Wavpack decoder plugin for GStreamer
gstreamer0.8-xvid - XVID encoder plugin for GStreamer

(tried to cut out all the programs you don't need)
You actually don't need all of them, but they can be useful in later stages, you can search the repo's by the command ```
apt-cache search *<search term>*
```
You **DON'T** need sudo for this

---

### Post by kaamos on 2006-02-08
*bartbes*: Whoa what a list! :D

You must first enable universe and multiverse: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
Then install the package "gstreamer0.8-plugins-multiverse", you get most of the necessary ones from the list above with that. Use the command "gst-register-0.8" in a terminal once you have the packages you need.

For video codecs: [https://wiki.ubuntu.com/RestrictedFormats#head-fda9cc5147253891fe3047263b82d787ab025bba](https://wiki.ubuntu.com/RestrictedFormats#head-fda9cc5147253891fe3047263b82d787ab025bba)

---

### Post by ovidiu82 on 2006-02-08
Thanks a lot for your help...

I think I won'e ever be able to at least use the minimum features of this OS...

Either im dumb, either this ain't easy..

Now I formated the windows partition I had with fat 32...and i can't see it , i can't access it....Any idea why and which are the magic words?

thank you...

---

### Post by mips on 2006-02-08
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

