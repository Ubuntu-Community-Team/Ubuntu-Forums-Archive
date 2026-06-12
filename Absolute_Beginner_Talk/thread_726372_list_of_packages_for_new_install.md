---
title: "list of packages for new install"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Jimmy Carter on 2008-03-16
After reinstall my Linux Distribution about a dozen times. I couldn't really find a good spot with a straight list of packages that are rediculously well used. So i set out to look for those packages that I needed to download every time I wanted to reinstall. This is what I came up with from about 7 or 8 sights worth of package hunting. These commands will install compiz, a huge number of audio and video codecs (a few of questionable legality), and some heavily used programs that someone new to ubuntu may want. Also I give the recommendation of install Envy first. 




1) Install Ubuntu
2) Google Envy, install and run to configure NVIDIA drivers
3) Broadcomm restricted drivers

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get install compizconfig-settings-manager

sudo mkdir mkdir -p /usr/lib/X11/fonts/Type1 sudo apt-get install msttcorefonts

sudo apt-get install powertop msttcorefonts w32codecs acroread acroread-plugins mozilla-acroread flashplugin-nonfree sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts ntfs-config mplayer mozilla-mplayer mplayer-fonts mplayer-skins gtkpod wine scilab dvdisaster qpxtool gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gl gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-dbg gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad-multiverse-dbg gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-good gstreamer0.10-plugins-good-dbg gstreamer0.10-plugins-good-doc gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg gstreamer0.10-plugins-ugly-doc gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.10-schroedinger gstreamer0.10-sdl gstreamer0.10-tools libdvdcss2 gsfonts-x11 non-free-codecs aircrack aircrack-ng airsnort alac-decoder apt-build bcc bin86 blast cpp-4.2 devscripts ffmpeg fftw3 gkrellm gkrellm-alltraxclock gkrellm-bfm gkrellm-hdplop gkrellm-i8k gkrellm-ibam gkrellm-leds gkrellm-mailwatch gkrellm-mldonkey gkrellm-radio gkrellm-reminder gkrellm-snmp gkrellm-volume gkrellm-x86info gkrellmapcupsd gkrellmd gkrellmitime gkrellmms gkrellmoon gkrellmss gkrellmwho2 gkrellmwireless gkrellongrun gkrellshoot gkrelltop gkrelltopd gkrellweather gkrellxmms2 gmail-notify i8kutils ibam libappconfig-perl libapt-pkg-perl libglib1.2 libgtk1.2 libgtk1.2-common libimlib2 libmikmod2 libswscale1d libxmmsclient-glib1 libxmmsclient2 gstreamer-tools gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gl gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-dbg gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad-multiverse-dbg gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-good-dbg gstreamer0.10-plugins-good-doc gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.10-schroedinger gstreamer0.10-sdl libcdaudio1 libfaad2-0 libfreebob0 libjack0 libmjpegtools0c2a libmms0 libopenspc0 libquicktime1 libschroedinger-0.1-0 libsidplay1 libsoundtouch1c2 ubuntu-restricted-extras gstreamer0.10-ffmpeg flashplugin-nonfree bcm43xx-fwcutter dkms gawk mpeg2dec a52dec vorbis-tools id3v2 mpg321 mpg123 libswfdec0.3 libflac++6 ffmpeg cdda2wav toolame libmp4v2-0 totem-mozilla libmjpegtools0c2a tagtool easytag id3tool lame lame-extras nautilus-script-audio-convert mozilla-helix-player helix-player libmad0 libjpeg-progs libmpcdec3 libquicktime1 flac faac faad sox toolame a52dec ffmpeg2theora libmpeg2-4 uudeview flac libmpeg3-1 mpeg3-utils mpegdemux ttf-larabie-straight ttf-larabie-deco mplayer-fonts xfonts-terminus-dos xfonts-terminus xfonts-terminus-oblique xfonts-mona tv-fonts ttf-tuffy ttf-sjfonts ttf-sil-padauk ttf-sil-ezra ttf-paktype ttf-georgewilliams ttf-fifthhorseman-dkg-handwriting ttf-farsiweb ttf-essays1743 fonty ttf-opensymbol ttf-nafees ttf-mgopen ttf-gentium ttf-freefont ttf-dustin ttf-devanagari-fonts ttf-dejavu-extra ttf-dejavu-core ttf-dejavu ttf-bpg-georgian-fonts ttf-bitstream-vera ttf-alee gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gl gstreamer0.10-gnonlin gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-farsight gstreamer0.10-plugins-ugly gstreamer0.10-sdl gstreamer0.10-plugins-bad-multiverse gstreamer0.10-schroedinger gstreamer0.10-plugins-ugly-multiverse totem-gstreamer gstreamer-dbus-media-service gstreamer-tools gsfonts gsfonts-x11 flashplugin-nonfree equivs ttf-sazanami-gothic ttf-sazanami-mincho

---

### Post by durand on 2008-03-16
Very useful, thanks :)

---

### Post by sailor2001 on 2008-03-16
you could have "aptoncd" and put all your programs on disk

---

### Post by ruibernardo on 2008-03-16
Hi Jimmy,

to get a list of all the packages that you have actually installed and to install the same list of the packages on another Ubuntu install, take a look at this:  [What do dpkg --get-selections and dpkg --set-selections do?]("http://ubuntuforums.org/showthread.php?t=169062") 

There is a tool that makes a Boot DVD with your actual setup. Remastersys will make your system boot from a DVD and also install it back! So, once you got a good setup, use remastersys and the next time you have to re-install, most of the job will be done! Take a look: [http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/). Installing the virtual package "[ubuntu-restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats")" will install most of the codecs, plugins, java, flash, etc.

You really should check why and what problem is causing all these re-installs.

---

### Post by Jimmy Carter on 2008-03-16
What I wanted to do was give beginners a decent list of useful packages so they don't have to search for them. Like Java, Flash, and the codec packages.

---

