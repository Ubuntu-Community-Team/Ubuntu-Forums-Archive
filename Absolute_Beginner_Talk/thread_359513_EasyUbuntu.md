---
title: "EasyUbuntu"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-12
i tried to install easyUbuntu via the deb file downloaded from their site and thsi is what i got:

```

shoaibi@saber-rider:~$ wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
Password:
gpg: no valid OpenPGP data found.

```
and then when i try to install the required packages i get:
```

apt-get  -o=dir::etc=/usr/lib/easyubuntu/conf -o=dir::etc::sourcelist=sources.list update
apt-get  -o=dir::etc=/usr/lib/easyubuntu/conf -o=dir::etc::sourcelist=sources.list --yes --allow-unauthenticated  install gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg libxine-extracodecs libxine-main1 faad sox lame ffmpeg mjpegtools vorbis-tools libxvidcore4 gstreamer0.10-pitfdll w32codecs libdvdcss2 timidity timidity-interfaces-extra freepats flashplugin-nonfree sun-java5-bin sun-java5-plugin kaffeine-mozilla rar unace msttcorefonts gsfonts-x11 xfonts-intl-european
update-flashplugin
cp /usr/lib/easyubuntu/conf/easyubuntu.list /etc/apt/sources.list.d/easyubuntu.list
fc-cache -f -v
Executing: 
apt-get  -o=dir::etc=/usr/lib/easyubuntu/conf -o=dir::etc::sourcelist=sources.list update
error: 
error: 
error: 
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
error: 
error: 
error: 
E: Unable to lock the list directory
Executing: 
apt-get  -o=dir::etc=/usr/lib/easyubuntu/conf -o=dir::etc::sourcelist=sources.list --yes --allow-unauthenticated  install gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg libxine-extracodecs libxine-main1 faad sox lame ffmpeg mjpegtools vorbis-tools libxvidcore4 gstreamer0.10-pitfdll w32codecs libdvdcss2 timidity timidity-interfaces-extra freepats flashplugin-nonfree sun-java5-bin sun-java5-plugin kaffeine-mozilla rar unace msttcorefonts gsfonts-x11 xfonts-intl-european
Reading package lists...
Building dependency tree...

Reading state information...

gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
libxine-extracodecs is already the newest version.
sox is already the newest version.
The following extra packages will be installed:
  cabextract java-common libcurl3-gnutls libfaac0 libfaad2-0 libjack0.100.0-0
  liblame0 libltdl3 libmjpegtools0c2a libmms0 libmp4v2-0 libquicktime0
  libsidplay1 libswfdec0.3 libwavpack0 odbcinst1debian1 sun-java5-jre unixodbc
Suggested packages:
  iceweasel konqueror-nsplugins ttf-xfree86-nonfree xfs equivs sidplay-base
  xsidplay toolame mpeg2dec a52dec unrar sun-java5-fonts ttf-sazanami-gothic
  ttf-sazanami-mincho pmidi libmyodbc odbc-postgresql libct1 mplayer
  xfonts-biznet-iso-8859-2-base xfonts-biznet-iso-8859-2-75dpi
  xfonts-biznet-iso-8859-2-100dpi emacs-intl-fonts
Recommended packages:
  jackd
The following NEW packages will be installed:
  cabextract faad ffmpeg flashplugin-nonfree freepats gsfonts-x11
  gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse java-common kaffeine-mozilla lame
  libcurl3-gnutls libdvdcss2 libfaac0 libfaad2-0 libjack0.100.0-0 liblame0
  libltdl3 libmjpegtools0c2a libmms0 libmp4v2-0 libquicktime0 libsidplay1
  libswfdec0.3 libwavpack0 libxine-main1 libxvidcore4 mjpegtools msttcorefonts
  odbcinst1debian1 rar sun-java5-bin sun-java5-jre sun-java5-plugin timidity
  timidity-interfaces-extra unace unixodbc vorbis-tools w32codecs
  xfonts-intl-european
0 upgraded, 45 newly installed, 0 to remove and 0 not upgraded.
Need to get 80.1MB of archives.
After unpacking 172MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  java-common libltdl3 odbcinst1debian1 unixodbc sun-java5-bin sun-java5-jre
  cabextract libfaad2-0 faad ffmpeg flashplugin-nonfree freepats gsfonts-x11
  gstreamer0.10-ffmpeg gstreamer0.10-pitfdll libmms0 libswfdec0.3 libwavpack0
  gstreamer0.10-plugins-bad libmp4v2-0 libfaac0 libxvidcore4
  gstreamer0.10-plugins-bad-multiverse libsidplay1 gstreamer0.10-plugins-ugly
  liblame0 gstreamer0.10-plugins-ugly-multiverse kaffeine-mozilla lame
  libcurl3-gnutls libdvdcss2 libjack0.100.0-0 libquicktime0 libmjpegtools0c2a
  libxine-main1 mjpegtools msttcorefonts rar sun-java5-plugin timidity
  timidity-interfaces-extra unace vorbis-tools w32codecs xfonts-intl-european
Authentication warning overridden.
Err http://archive.ubuntu.com edgy/main java-common 0.25ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://security.ubuntu.com edgy-security/universe libxine-main1 1.1.2+repacked1-0ubuntu3.2
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (101 Network is unreachable)
Err http://archive.ubuntu.com edgy/main libltdl3 1.5.22-4
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://medibuntu.sos-sts.com edgy/free libdvdcss2 1.2.9-2medibuntu2
  Could not connect to medibuntu.sos-sts.com:80 (88.191.35.32). - connect (101 Network is unreachable) [IP: 88.191.35.32 80]
Err http://medibuntu.sos-sts.com edgy/non-free w32codecs 20061022-0medibuntu1
  Could not connect to medibuntu.sos-sts.com:80 (88.191.35.32). - connect (101 Network is unreachable) [IP: 88.191.35.32 80]
Err http://archive.ubuntu.com edgy/main odbcinst1debian1 2.2.11-13
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/main unixodbc 2.2.11-13
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse sun-java5-bin 1.5.0-08-0ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse sun-java5-jre 1.5.0-08-0ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe cabextract 1.1-1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse libfaad2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse faad 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe ffmpeg 3:0.cvs20060823-3.1ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy-backports/multiverse flashplugin-nonfree 9.0.31.0.1ubuntu1~edgy1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe freepats 20060219-1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/main gsfonts-x11 0.20build1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe gstreamer0.10-ffmpeg 0.10.1-2ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe gstreamer0.10-pitfdll 0.9.1.1+cvs20060515-1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe libmms0 0.2-7
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe libswfdec0.3 0.3.6-2ubuntu2
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe libwavpack0 4.32-2ubuntu2
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe gstreamer0.10-plugins-bad 0.10.3+cvs20060918-0ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse libmp4v2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse libfaac0 1.24clean-0ubuntu4
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse libxvidcore4 2:1.1.0-final-0.1ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse gstreamer0.10-plugins-bad-multiverse 0.10.3+cvs20060918-1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe libsidplay1 1.36.59-4
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe gstreamer0.10-plugins-ugly 0.10.4-0ubuntu3
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse liblame0 3.96.1-2
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.4-2
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe kaffeine-mozilla 0.4.3.1.dfsg-0.1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse lame 3.96.1-2
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy-proposed/main libcurl3-gnutls 7.15.4-1ubuntu2.1~proposed1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe libjack0.100.0-0 0.101.1-1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/main libquicktime0 1:0.9.7-0.6ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse libmjpegtools0c2a 1:1.8.0-0.2ubuntu2
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse mjpegtools 1:1.8.0-0.2ubuntu2
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse msttcorefonts 1.2ubuntu3
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy-backports/multiverse rar 1:3.6.0-0ubuntu1~edgy1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/multiverse sun-java5-plugin 1.5.0-08-0ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe timidity 2.13.2-7.1ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe timidity-interfaces-extra 2.13.2-7.1ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe unace 1.2b-3
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/main vorbis-tools 1.1.1-5
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy/universe xfonts-intl-european 1.2.1-6ubuntu1
  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
error: 
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.25ubuntu1_all.deb  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
error: 
error: 
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libltdl3_1.5.22-4_i386.deb  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
error: 
error: 
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-13_i386.deb  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
error: 
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-13_i386.deb  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
error: 
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java5/sun-java5-bin_1.5.0-08-0ubuntu1_i386.deb  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
error: 
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java5/sun-java5-jre_1.5.0-08-0ubuntu1_all.deb  Could not connect to archive.ubuntu.com:80 (195.248.90.35). - connect (101 Network is unreachable) [IP: 195.248.90.35 80]
Executing: 
cp /usr/lib/easyubuntu/conf/easyubuntu.list /etc/apt/sources.list.d/easyubuntu.list
Executing: 
fc-cache -f -v
EasyUbuntu is finished. You may copy this log for debugging purposes.
fc-cache: "/usr/share/fonts": 
caching, 0 fonts, 3 dirs
fc-cache: "/usr/share/fonts/X11": 
caching, 0 fonts, 6 dirs
fc-cache: "/usr/share/fonts/X11/100dpi": 
caching, 358 fonts, 0 dirs
fc-cache: "/usr/share/fonts/X11/75dpi": 
caching, 358 fonts, 0 dirs
fc-cache: "/usr/share/fonts/X11/Type1": 
caching, 8 fonts, 0 dirs
fc-cache: "/usr/share/fonts/X11/encodings": 
caching, 0 fonts, 1 dirs
fc-cache: "/usr/share/fonts/X11/encodings/large": 
caching, 0 fonts, 0 dirs
fc-cache: "/usr/share/fonts/X11/misc": 
caching, 55 fonts, 0 dirs
fc-cache: "/usr/share/fonts/X11/util": 
caching, 0 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype": 
caching, 0 fonts, 22 dirs
fc-cache: "/usr/share/fonts/truetype/arphic": 
caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/baekmuk": 
caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/freefont": 
caching, 12 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/kochi": 
caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/openoffice": 
caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/thai": 
caching, 23 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-arabeyes": 
caching, 39 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-bengali-fonts": 
caching, 7 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-bitstream-vera": 
caching, 10 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-dejavu": 
caching, 21 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-devanagari-fonts": 
caching, 5 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-gentium": 
caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-gujarati-fonts": 
caching, 5 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-kannada-fonts": 
caching, 8 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-lao": 
caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-malayalam-fonts": 
caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-mgopen": 
caching, 16 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-oriya-fonts": 
caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-punjabi-fonts": 
caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-tamil-fonts": 
caching, 9 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-telugu-fonts": 
caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/latex-xft-fonts": 
caching, 7 fonts, 0 dirs
fc-cache: "/usr/share/fonts/type1": 
caching, 0 fonts, 1 dirs
fc-cache: "/usr/share/fonts/type1/gsfonts": 
caching, 35 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts": 
skipping, no such directory
fc-cache: "/usr/local/share/fonts": 
caching, 0 fonts, 0 dirs
fc-cache: "/root/.fonts": 
skipping, no such directory
fc-cache: "/var/lib/defoma/fontconfig.d": 
caching, 0 fonts, 26 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/A": 
caching, 8 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/B": 
caching, 11 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/C": 
caching, 6 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/D": 
caching, 23 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/E": 
caching, 1 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/F": 
caching, 13 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/G": 
caching, 12 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/H": 
caching, 4 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/J": 
caching, 2 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/K": 
caching, 6 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/L": 
caching, 6 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/M": 
caching, 19 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/N": 
caching, 23 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/O": 
caching, 2 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/P": 
caching, 5 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/R": 
caching, 3 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/S": 
caching, 7 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/T": 
caching, 10 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/U": 
caching, 13 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/V": 
caching, 1 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/a": 
caching, 1 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/j": 
caching, 1 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/m": 
caching, 6 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/u": 
caching, 1 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/c": 
caching, 4 fonts, 0 dirs
fc-cache: "/var/lib/defoma/fontconfig.d/w": 
caching, 1 fonts, 0 dirs
fc-cache: succeeded

```
The problem is that it somewhere gave the "101 Network is unreachable error" and "E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)", do i have to worry about this???

PS:
I don't have Firefox, i uninstalled it, i have Flock installed....

---

### Post by jpeddicord on 2007-02-12
EasyUbuntu isn't very actively developed anymore (well, it might be, but there has been no recent releases), so I suggest Automatix if you want an easy installer:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

It is very much like EasyUbuntu, but it is more compatible with newer releases and has more options available.

Jacob

---

### Post by nickburns on 2007-02-12
It is much easier to research what you want and do it yourself than with easy ubuntu.  What features are you looking for?

---

### Post by paker on 2007-02-12
> **jacobmp92 said:**
> EasyUbuntu isn't very actively developed anymore (well, it might be, but there has been no recent releases), so I suggest Automatix if you want an easy installer:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

It is very much like EasyUbuntu, but it is more compatible with newer releases and has more options available.

Jacob
Do I have to remove EasyUbuntu before installing Automatix? Potential software conflict if EasyUbuntu not removed first?

---

### Post by jpeddicord on 2007-02-13
Yes, it is probably a good idea to remove it. If it doesn't work, then why keep it? ;)

---

