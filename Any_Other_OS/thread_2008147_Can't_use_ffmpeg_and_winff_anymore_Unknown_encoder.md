---
title: "Can't use ffmpeg and winff anymore: Unknown encoder 'libx264'"
date: 2012-06-22
forum: Any Other OS
---

### Post by amsterdamharu on 2012-06-22
I think this used to work, haven't used my linux mint 9 in months. Now trying to convert some video and getting that error.

tried to install libavcodec-extra-52 but get the following error:
```

me@lapt ~ $ sudo apt-get install libavcodec-extra-52
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavcodec-extra-52: Depends: libavutil-extra-49 (< 4:0.5.1-99) but 4:0.5.9-0ubuntu0.10.04.1 is to be installed
E: Broken packages

```

When trying aptitude it tells me to remove ffmpeg to fix ffmpeg, not a good solution for me:
```

me@lapt ~ $ sudo aptitude install libavcodec-extra-52 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  ffmpeg libavcodec-extra-52 libavdevice52 libavfilter1 libavformat52 
The following packages will be REMOVED:
  libavcodec52{a} 
0 packages upgraded, 1 newly installed, 1 to remove and 1 not upgraded.
Need to get 4,027kB of archives. After unpacking 172kB will be freed.
The following packages have unmet dependencies:
  libavcodec-extra-52: Depends: libopenjpeg2 but it is not installable
  libavformat52: Depends: libavcodec52 (>= 4:0.6.2-1ubuntu1.1~ppa1~lucid1) but it is not installable or
                          libavcodec-extra-52 (>= 4:0.6.2) but 4:0.5.1-1ubuntu1.3+medibuntu1 is to be installed.
  ffmpeg: Depends: libavcodec52 (>= 4:0.6.2-1ubuntu1.1~ppa1~lucid1) but it is not installable or
                   libavcodec-extra-52 (>= 4:0.6.2) but 4:0.5.1-1ubuntu1.3+medibuntu1 is to be installed.
  libavfilter1: Depends: libavcodec52 (>= 4:0.6.2-1ubuntu1.1~ppa1~lucid1) but it is not installable or
                         libavcodec-extra-52 (>= 4:0.6.2) but 4:0.5.1-1ubuntu1.3+medibuntu1 is to be installed.
  libavdevice52: Depends: libavcodec52 (>= 4:0.6.2-1ubuntu1.1~ppa1~lucid1) but it is not installable or
                          libavcodec-extra-52 (>= 4:0.6.2) but 4:0.5.1-1ubuntu1.3+medibuntu1 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
ffmpeg
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad-multiverse
libavdevice52
libavfilter1
libavformat52
libmjpegtools-1.9
libquicktime1
mjpegtools

Keep the following packages at their current version:
libavcodec-extra-52 [Not Installed]

Leave the following dependencies unresolved:
libavidemux0 recommends mjpegtools
audacity recommends libavcodec52 | libavcodec-extra-52
audacity recommends libavformat52 | libavformat-extra-52
Score is -10940

Accept this solution? [Y/n/q/?] 

```

After typing n and enter nothing happens only q enter quits.

---

### Post by Perfect Storm on 2012-06-22
Moved to Other OS/Distro Talk.

---

