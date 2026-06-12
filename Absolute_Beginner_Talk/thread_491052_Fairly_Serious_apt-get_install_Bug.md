---
title: "Fairly Serious apt-get install Bug"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-07-03
when I sudo apt-get install   "anything", terminal throws this after entering the password:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by ruza on 2007-07-03
You have some program like synaptic runing? Read the error massage :D

---

### Post by PaulFr on 2007-07-03
If you can verify that no other package manager like Synaptic is running, perhaps your last installation was interrupted abruptly. In that case, a lock file will be left behind. So you will need to remove that lock file by ```
sudo rm /var/lib/dpkg/lock
```

---

### Post by johntkucz on 2007-07-04
> **PaulFr said:**
> If you can verify that no other package manager like Synaptic is running, perhaps your last installation was interrupted abruptly. In that case, a lock file will be left behind. So you will need to remove that lock file by ```
sudo rm /var/lib/dpkg/lock
```

hey paul, I think you're on to it. you're right, something wasn't removed:

kooz@kooz-laptop:~$ sudo apt-get install amule
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  amule-common libcrypto++5.2c2a libwxbase2.8-0 libwxgtk2.8-0 sun-java5-bin
  sun-java5-jre
Suggested packages:
  amule-utils-gui sun-java5-plugin ia32-sun-java5-plugin sun-java5-fonts
  ttf-sazanami-gothic ttf-sazanami-mincho
Recommended packages:
  amule-utils gsfonts-x11
The following NEW packages will be installed:
  amule amule-common libcrypto++5.2c2a libwxbase2.8-0 libwxgtk2.8-0
The following packages will be upgraded:
  sun-java5-bin sun-java5-jre
2 upgraded, 5 newly installed, 0 to remove and 8 not upgraded.
2 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
kooz@kooz-laptop:~$ 



I think it was sun-java5-bin, but it still doesn't work after I give your command a shot.

---

### Post by johntkucz on 2007-07-04
When I use the update manager, I get this:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

When I list the contents of that directory, I get this:

app-install-data_0.3.31_all.deb
app-install-data-commercial_7.1_all.deb
apport_0.76.1_all.deb
apport-gtk_0.76.1_all.deb
artsbuilder_4%3a3.5.6-0ubuntu4_i386.deb
atlas3-base_3.6.0-20.6_i386.deb
beryl_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb
beryl-core_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb
beryl-manager_0.2.1-0ubuntu1_i386.deb
beryl-plugins_0.2.1-0ubuntu2_i386.deb
beryl-plugins-data_0.2.1-0ubuntu2_all.deb
beryl-settings_0.2.1-0ubuntu1_all.deb
beryl-settings-bindings_0.2.1-0ubuntu1_i386.deb
build-essential_11.3_i386.deb
capplets-data_1%3a2.18.1-0ubuntu2.1_all.deb
dpkg-dev_1.13.24ubuntu6_all.deb
emerald_0.2.1-0ubuntu1_i386.deb
emerald-themes_0.2.1-0ubuntu1_all.deb
evolution-data-server_1.10.1-0ubuntu1.1_i386.deb
evolution-data-server-common_1.10.1-0ubuntu1.1_all.deb
fftw3_3.1.2-1build1_i386.deb
file_4.19-1ubuntu2.1_i386.deb
firefox_2.0.0.4+1-0ubuntu1_i386.deb
firefox-gnome-support_2.0.0.4+1-0ubuntu1_i386.deb
fl-cow_0.6-1_i386.deb
g++-4.1_4.1.2-0ubuntu4_i386.deb
g++_4%3a4.1.2-1ubuntu1_i386.deb
gcc-3.4-base_3.4.6-5ubuntu1_i386.deb
gdeskcal_0.57.1-2ubuntu1_all.deb
gdesklets_0.35.3-4ubuntu2_i386.deb
gdesklets-data_0.35.6-1_all.deb
gettext_0.16.1-1ubuntu2_i386.deb
gftp-common_2.0.18-16ubuntu2_i386.deb
gftp-gtk_2.0.18-16ubuntu2_i386.deb
gimp_2.2.13-1ubuntu4.1_i386.deb
gimp-data_2.2.13-1ubuntu4.1_all.deb
gimp-python_2.2.13-1ubuntu4.1_i386.deb
gnome-app-install_0.3.31_all.deb
gnome-btdownload_0.0.28-1~feisty1_all.deb
gnome-control-center_1%3a2.18.1-0ubuntu2.1_i386.deb
gnome-panel_1%3a2.18.1-0ubuntu3.1_i386.deb
gnome-panel-data_1%3a2.18.1-0ubuntu3.1_all.deb
gstreamer0.10-ffmpeg_0.10.2-0ubuntu4_i386.deb
gstreamer0.10-plugins-bad_0.10.4-1ubuntu1_i386.deb
gstreamer0.10-plugins-bad-multiverse_0.10.4-3_i386.deb
gstreamer0.10-plugins-ugly_0.10.5-0ubuntu2_i386.deb
hal_0.5.9-1ubuntu2~feisty1_i386.deb
hal-device-manager_0.5.9-1ubuntu2~feisty1_all.deb
hal-info_20070402-1ubuntu1~feisty1_all.deb
hwdb-client-common_0.6.10.1_all.deb
hwdb-client-gnome_0.6.10.1_all.deb
java-common_0.25ubuntu2_all.deb
kdeedu-data_4%3a3.5.6-0ubuntu1_all.deb
kdelibs4c2a_4%3a3.5.6-0ubuntu14_i386.deb
kdelibs-data_4%3a3.5.6-0ubuntu14_all.deb
ktron_4%3a3.5.6-0ubuntu2_i386.deb
kturtle_4%3a3.5.6-0ubuntu1_i386.deb
language-pack-en_1%3a7.04+20070601_all.deb
language-pack-gnome-en_1%3a7.04+20070601_all.deb
liba52-0.7.4_0.7.4-7_i386.deb
libarts1c2a_1.5.6-0ubuntu1_i386.deb
libartsc0_1.5.6-0ubuntu1_i386.deb
libavahi-qt3-1_0.6.17-0ubuntu3_i386.deb
libberyldecoration0_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb
libberylsettings0_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb
libc6-dev_2.5-0ubuntu14_i386.deb
libcamel1.2-10_1.10.1-0ubuntu1.1_i386.deb
libcdaudio1_0.99.12p2-2_i386.deb
libdvdread3_0.9.7-2ubuntu1_i386.deb
libebook1.2-9_1.10.1-0ubuntu1.1_i386.deb
libecal1.2-7_1.10.1-0ubuntu1.1_i386.deb
libedata-book1.2-2_1.10.1-0ubuntu1.1_i386.deb
libedata-cal1.2-6_1.10.1-0ubuntu1.1_i386.deb
libedataserver1.2-9_1.10.1-0ubuntu1.1_i386.deb
libedataserverui1.2-8_1.10.1-0ubuntu1.1_i386.deb
libegroupwise1.2-13_1.10.1-0ubuntu1.1_i386.deb
libemeraldengine0_0.2.1-0ubuntu1_i386.deb
libexchange-storage1.2-3_1.10.1-0ubuntu1.1_i386.deb
libexif12_0.6.13-5ubuntu0.1_i386.deb
libfaac0_1.24clean-0ubuntu4_i386.deb
libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3_i386.deb
libfreebob0_1.0.0-3_i386.deb
libfreetype6_2.2.1-5ubuntu1.1_i386.deb
libg2c0_1%3a3.4.6-5ubuntu1_i386.deb
libgfortran1_4.1.2-0ubuntu4_i386.deb
libgimp2.0_2.2.13-1ubuntu4.1_i386.deb
libglib1.2_1.2.10-17build1_i386.deb
libgnome-window-settings1_1%3a2.18.1-0ubuntu2.1_i386.deb
libgsm1_1.0.10-13_i386.deb
libgtk1.2_1.2.10-18_i386.deb
libgtk1.2-common_1.2.10-18_all.deb
libhal1_0.5.9-1ubuntu2~feisty1_i386.deb
libhal-storage1_0.5.9-1ubuntu2~feisty1_i386.deb
libhdf5-serial-1.6.5-0_1.6.5-3_i386.deb
libid3tag0_0.15.1b-8_i386.deb
libjack0.100.0-0_0.102.20-1_i386.deb
libkdegames1_4%3a3.5.6-0ubuntu2_i386.deb
libltdl3_1.5.22-4_i386.deb
liblua50_5.0.3-2build1_i386.deb
liblualib50_5.0.3-2build1_i386.deb
libmad0_0.15.1b-2.1_i386.deb
libmagic1_4.19-1ubuntu2.1_i386.deb
libmetacity0_1%3a2.18.2-0ubuntu1.1_i386.deb
libmikmod2_3.1.11-a-6ubuntu3_i386.deb
libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu3_i386.deb
libmms0_0.3-2ubuntu1_i386.deb
libmodplug0c2_1%3a0.7-5.2build1_i386.deb
libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3_i386.deb
libmpcdec3_1.2.2-1_i386.deb
libmpeg2-4_0.4.1-1_i386.deb
libncurses5-dev_5.5-5ubuntu2_i386.deb
libnspr4_2%3a1.firefox2.0.0.4+1-0ubuntu1_i386.deb
libnss3_2%3a1.firefox2.0.0.4+1-0ubuntu1_i386.deb
libopenexr2c2a_1.2.2-4.3ubuntu1_i386.deb
libpanel-applet2-0_1%3a2.18.1-0ubuntu3.1_i386.deb
libpcre3_6.7-1ubuntu2_i386.deb
libpng12-0_1.2.15~beta5-1ubuntu1_i386.deb
libpulse0_0.9.5-5ubuntu4.1_i386.deb
libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu5_i386.deb
libquicktime0_2%3a0.9.7-1ubuntu2_i386.deb
libsamplerate0_0.1.2-2_i386.deb
libsidplay1_1.36.59-4_i386.deb
libslab0_1%3a2.18.1-0ubuntu2.1_i386.deb
libsmbclient_3.0.24-2ubuntu1.2_i386.deb
libsoundtouch1c2_1.3.0-2.1_i386.deb
libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb
libswfdec0.3_0.3.6-2.1_i386.deb
libwavpack1_4.40.0-1_i386.deb
libxine1_1.1.4-2ubuntu3_i386.deb
libxine1-ffmpeg_1.1.4-2ubuntu3_i386.deb
libxvidcore4_2%3a1.1.2-0.1ubuntu1.1_i386.deb
libxvmc1_2%3a1.0.2-0ubuntu2_i386.deb
linux-generic_2.6.20.16.28.1_i386.deb
linux-headers-2.6.20-16_2.6.20-16.29_i386.deb
linux-headers-2.6.20-16-generic_2.6.20-16.29_i386.deb
linux-headers-generic_2.6.20.16.28.1_i386.deb
linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
linux-image-generic_2.6.20.16.28.1_i386.deb
linux-libc-dev_2.6.20-16.29_i386.deb
linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.28_i386.deb
linux-restricted-modules-common_2.6.20.5-16.28_all.deb
linux-restricted-modules-generic_2.6.20.16.28.1_i386.deb
lock
menu-xdg_0.2.3_all.deb
metacity_1%3a2.18.2-0ubuntu1.1_i386.deb
metacity-common_1%3a2.18.2-0ubuntu1.1_all.deb
mozilla-thunderbird_1.5.0.12-0ubuntu0.7.04_i386.deb
noatun_4%3a3.5.6-0ubuntu4_i386.deb
octave_1%3a2.1.73-13_all.deb
octave2.1_1%3a2.1.73-13_i386.deb
odbcinst1debian1_2.2.11-13_i386.deb
partial
pulseaudio_0.9.5-5ubuntu4.1_i386.deb
python2.4_2.4.4-2ubuntu7_i386.deb
python2.4-minimal_2.4.4-2ubuntu7_i386.deb
python_2.5.1-0ubuntu3_all.deb
python2.5_2.5.1-0ubuntu1_i386.deb
python2.5-minimal_2.5.1-0ubuntu1_i386.deb
python-apport_0.76.1_all.deb
python-cups_1.9.19-0ubuntu1_i386.deb
python-gdbm_2.5.1-0ubuntu1_i386.deb
python-minimal_2.5.1-0ubuntu3_all.deb
python-problem-report_0.76.1_all.deb
rdesktop_1.5.0-1ubuntu1_i386.deb
samba-common_3.0.24-2ubuntu1.2_i386.deb
screem_0.16.1-4ubuntu1_i386.deb
smbclient_3.0.24-2ubuntu1.2_i386.deb
system-config-printer_0.7.62-0ubuntu1_all.deb
texinfo_4.8.dfsg.1-4build1_i386.deb
tzdata_2007e-0ubuntu0.7.04_all.deb
unattended-upgrades_0.23ubuntu3_all.deb
unixodbc_2.2.11-13_i386.deb
update-manager_1%3a0.59.20_all.deb
update-manager-core_1%3a0.59.20_i386.deb
vim_1%3a7.0-164+1ubuntu7.1_i386.deb
vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb
vim-runtime_1%3a7.0-164+1ubuntu7.1_all.deb
vim-tiny_1%3a7.0-164+1ubuntu7.1_i386.deb
wine_0.9.33-0ubuntu1_i386.deb
wine_0.9.39~winehq0~ubuntu~7.04-1_i386.deb
wine-dev_0.9.33-0ubuntu1_i386.deb
wine-dev_0.9.39~winehq0~ubuntu~7.04-1_i386.deb
xaos_3.2-3ubuntu2_i386.deb
xchat-gnome_1%3a0.16-0ubuntu3_i386.deb
xchat-gnome-common_1%3a0.16-0ubuntu3_all.deb
xmms_1%3a1.2.10+20061201-1ubuntu3_i386.deb
xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-16.28_i386.deb
xscreensaver-data_4.24-5ubuntu2.1_i386.deb
xscreensaver-gl_4.24-5ubuntu2.1_i386.deb
app-install-data_0.3.31_all.deb
app-install-data-commercial_7.1_all.deb
apport_0.76.1_all.deb
apport-gtk_0.76.1_all.deb
artsbuilder_4%3a3.5.6-0ubuntu4_i386.deb
atlas3-base_3.6.0-20.6_i386.deb
beryl_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb
beryl-core_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb
beryl-manager_0.2.1-0ubuntu1_i386.deb
beryl-plugins_0.2.1-0ubuntu2_i386.deb
beryl-plugins-data_0.2.1-0ubuntu2_all.deb
beryl-settings_0.2.1-0ubuntu1_all.deb
beryl-settings-bindings_0.2.1-0ubuntu1_i386.deb
build-essential_11.3_i386.deb
capplets-data_1%3a2.18.1-0ubuntu2.1_all.deb
dpkg-dev_1.13.24ubuntu6_all.deb
emerald_0.2.1-0ubuntu1_i386.deb
emerald-themes_0.2.1-0ubuntu1_all.deb
evolution-data-server_1.10.1-0ubuntu1.1_i386.deb
evolution-data-server-common_1.10.1-0ubuntu1.1_all.deb
fftw3_3.1.2-1build1_i386.deb
file_4.19-1ubuntu2.1_i386.deb
firefox_2.0.0.4+1-0ubuntu1_i386.deb
firefox-gnome-support_2.0.0.4+1-0ubuntu1_i386.deb
fl-cow_0.6-1_i386.deb
g++-4.1_4.1.2-0ubuntu4_i386.deb
g++_4%3a4.1.2-1ubuntu1_i386.deb
gcc-3.4-base_3.4.6-5ubuntu1_i386.deb
gdeskcal_0.57.1-2ubuntu1_all.deb
gdesklets_0.35.3-4ubuntu2_i386.deb
gdesklets-data_0.35.6-1_all.deb
gettext_0.16.1-1ubuntu2_i386.deb
gftp-common_2.0.18-16ubuntu2_i386.deb
gftp-gtk_2.0.18-16ubuntu2_i386.deb
gimp_2.2.13-1ubuntu4.1_i386.deb
gimp-data_2.2.13-1ubuntu4.1_all.deb
gimp-python_2.2.13-1ubuntu4.1_i386.deb
gnome-app-install_0.3.31_all.deb
gnome-btdownload_0.0.28-1~feisty1_all.deb
gnome-control-center_1%3a2.18.1-0ubuntu2.1_i386.deb
gnome-panel_1%3a2.18.1-0ubuntu3.1_i386.deb
gnome-panel-data_1%3a2.18.1-0ubuntu3.1_all.deb
gstreamer0.10-ffmpeg_0.10.2-0ubuntu4_i386.deb
gstreamer0.10-plugins-bad_0.10.4-1ubuntu1_i386.deb
gstreamer0.10-plugins-bad-multiverse_0.10.4-3_i386.deb
gstreamer0.10-plugins-ugly_0.10.5-0ubuntu2_i386.deb
hal_0.5.9-1ubuntu2~feisty1_i386.deb
hal-device-manager_0.5.9-1ubuntu2~feisty1_all.deb
hal-info_20070402-1ubuntu1~feisty1_all.deb
hwdb-client-common_0.6.10.1_all.deb
hwdb-client-gnome_0.6.10.1_all.deb
java-common_0.25ubuntu2_all.deb
kdeedu-data_4%3a3.5.6-0ubuntu1_all.deb
kdelibs4c2a_4%3a3.5.6-0ubuntu14_i386.deb
kdelibs-data_4%3a3.5.6-0ubuntu14_all.deb
ktron_4%3a3.5.6-0ubuntu2_i386.deb
kturtle_4%3a3.5.6-0ubuntu1_i386.deb
language-pack-en_1%3a7.04+20070601_all.deb
language-pack-gnome-en_1%3a7.04+20070601_all.deb
liba52-0.7.4_0.7.4-7_i386.deb
libarts1c2a_1.5.6-0ubuntu1_i386.deb
libartsc0_1.5.6-0ubuntu1_i386.deb
libavahi-qt3-1_0.6.17-0ubuntu3_i386.deb
libberyldecoration0_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb
libberylsettings0_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb
libc6-dev_2.5-0ubuntu14_i386.deb
libcamel1.2-10_1.10.1-0ubuntu1.1_i386.deb
libcdaudio1_0.99.12p2-2_i386.deb
libdvdread3_0.9.7-2ubuntu1_i386.deb
libebook1.2-9_1.10.1-0ubuntu1.1_i386.deb
libecal1.2-7_1.10.1-0ubuntu1.1_i386.deb
libedata-book1.2-2_1.10.1-0ubuntu1.1_i386.deb
libedata-cal1.2-6_1.10.1-0ubuntu1.1_i386.deb
libedataserver1.2-9_1.10.1-0ubuntu1.1_i386.deb
libedataserverui1.2-8_1.10.1-0ubuntu1.1_i386.deb
libegroupwise1.2-13_1.10.1-0ubuntu1.1_i386.deb
libemeraldengine0_0.2.1-0ubuntu1_i386.deb
libexchange-storage1.2-3_1.10.1-0ubuntu1.1_i386.deb
libexif12_0.6.13-5ubuntu0.1_i386.deb
libfaac0_1.24clean-0ubuntu4_i386.deb
libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3_i386.deb
libfreebob0_1.0.0-3_i386.deb
libfreetype6_2.2.1-5ubuntu1.1_i386.deb
libg2c0_1%3a3.4.6-5ubuntu1_i386.deb
libgfortran1_4.1.2-0ubuntu4_i386.deb
libgimp2.0_2.2.13-1ubuntu4.1_i386.deb
libglib1.2_1.2.10-17build1_i386.deb
libgnome-window-settings1_1%3a2.18.1-0ubuntu2.1_i386.deb
libgsm1_1.0.10-13_i386.deb
libgtk1.2_1.2.10-18_i386.deb
libgtk1.2-common_1.2.10-18_all.deb
libhal1_0.5.9-1ubuntu2~feisty1_i386.deb
libhal-storage1_0.5.9-1ubuntu2~feisty1_i386.deb
libhdf5-serial-1.6.5-0_1.6.5-3_i386.deb
libid3tag0_0.15.1b-8_i386.deb
libjack0.100.0-0_0.102.20-1_i386.deb
libkdegames1_4%3a3.5.6-0ubuntu2_i386.deb
libltdl3_1.5.22-4_i386.deb
liblua50_5.0.3-2build1_i386.deb
liblualib50_5.0.3-2build1_i386.deb
libmad0_0.15.1b-2.1_i386.deb
libmagic1_4.19-1ubuntu2.1_i386.deb
libmetacity0_1%3a2.18.2-0ubuntu1.1_i386.deb
libmikmod2_3.1.11-a-6ubuntu3_i386.deb
libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu3_i386.deb
libmms0_0.3-2ubuntu1_i386.deb
libmodplug0c2_1%3a0.7-5.2build1_i386.deb
libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3_i386.deb
libmpcdec3_1.2.2-1_i386.deb
libmpeg2-4_0.4.1-1_i386.deb
libncurses5-dev_5.5-5ubuntu2_i386.deb
libnspr4_2%3a1.firefox2.0.0.4+1-0ubuntu1_i386.deb
libnss3_2%3a1.firefox2.0.0.4+1-0ubuntu1_i386.deb
libopenexr2c2a_1.2.2-4.3ubuntu1_i386.deb
libpanel-applet2-0_1%3a2.18.1-0ubuntu3.1_i386.deb
libpcre3_6.7-1ubuntu2_i386.deb
libpng12-0_1.2.15~beta5-1ubuntu1_i386.deb
libpulse0_0.9.5-5ubuntu4.1_i386.deb
libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu5_i386.deb
libquicktime0_2%3a0.9.7-1ubuntu2_i386.deb
libsamplerate0_0.1.2-2_i386.deb
libsidplay1_1.36.59-4_i386.deb
libslab0_1%3a2.18.1-0ubuntu2.1_i386.deb
libsmbclient_3.0.24-2ubuntu1.2_i386.deb
libsoundtouch1c2_1.3.0-2.1_i386.deb
libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb
libswfdec0.3_0.3.6-2.1_i386.deb
libwavpack1_4.40.0-1_i386.deb
libxine1_1.1.4-2ubuntu3_i386.deb
libxine1-ffmpeg_1.1.4-2ubuntu3_i386.deb
libxvidcore4_2%3a1.1.2-0.1ubuntu1.1_i386.deb
libxvmc1_2%3a1.0.2-0ubuntu2_i386.deb
linux-generic_2.6.20.16.28.1_i386.deb
linux-headers-2.6.20-16_2.6.20-16.29_i386.deb
linux-headers-2.6.20-16-generic_2.6.20-16.29_i386.deb
linux-headers-generic_2.6.20.16.28.1_i386.deb
linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
linux-image-generic_2.6.20.16.28.1_i386.deb
linux-libc-dev_2.6.20-16.29_i386.deb
linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.28_i386.deb
linux-restricted-modules-common_2.6.20.5-16.28_all.deb
linux-restricted-modules-generic_2.6.20.16.28.1_i386.deb
lock
menu-xdg_0.2.3_all.deb
metacity_1%3a2.18.2-0ubuntu1.1_i386.deb
metacity-common_1%3a2.18.2-0ubuntu1.1_all.deb
mozilla-thunderbird_1.5.0.12-0ubuntu0.7.04_i386.deb
noatun_4%3a3.5.6-0ubuntu4_i386.deb
octave_1%3a2.1.73-13_all.deb
octave2.1_1%3a2.1.73-13_i386.deb
odbcinst1debian1_2.2.11-13_i386.deb
partial
pulseaudio_0.9.5-5ubuntu4.1_i386.deb
python2.4_2.4.4-2ubuntu7_i386.deb
python2.4-minimal_2.4.4-2ubuntu7_i386.deb
python_2.5.1-0ubuntu3_all.deb
python2.5_2.5.1-0ubuntu1_i386.deb
python2.5-minimal_2.5.1-0ubuntu1_i386.deb
python-apport_0.76.1_all.deb
python-cups_1.9.19-0ubuntu1_i386.deb
python-gdbm_2.5.1-0ubuntu1_i386.deb
python-minimal_2.5.1-0ubuntu3_all.deb
python-problem-report_0.76.1_all.deb
rdesktop_1.5.0-1ubuntu1_i386.deb
samba-common_3.0.24-2ubuntu1.2_i386.deb
screem_0.16.1-4ubuntu1_i386.deb
smbclient_3.0.24-2ubuntu1.2_i386.deb
system-config-printer_0.7.62-0ubuntu1_all.deb
texinfo_4.8.dfsg.1-4build1_i386.deb
tzdata_2007e-0ubuntu0.7.04_all.deb
unattended-upgrades_0.23ubuntu3_all.deb
unixodbc_2.2.11-13_i386.deb
update-manager_1%3a0.59.20_all.deb
update-manager-core_1%3a0.59.20_i386.deb
vim_1%3a7.0-164+1ubuntu7.1_i386.deb
vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb
vim-runtime_1%3a7.0-164+1ubuntu7.1_all.deb
vim-tiny_1%3a7.0-164+1ubuntu7.1_i386.deb
wine_0.9.33-0ubuntu1_i386.deb
wine_0.9.39~winehq0~ubuntu~7.04-1_i386.deb
wine-dev_0.9.33-0ubuntu1_i386.deb
wine-dev_0.9.39~winehq0~ubuntu~7.04-1_i386.deb
xaos_3.2-3ubuntu2_i386.deb
xchat-gnome_1%3a0.16-0ubuntu3_i386.deb
xchat-gnome-common_1%3a0.16-0ubuntu3_all.deb
xmms_1%3a1.2.10+20061201-1ubuntu3_i386.deb
xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-16.28_i386.deb
xscreensaver-data_4.24-5ubuntu2.1_i386.deb
xscreensaver-gl_4.24-5ubuntu2.1_i386.deb

---

### Post by christhemonkey on 2007-07-04
As you can see from that list, the file "lock" is still there.


IF you are 100% sure there is no onther process running (update-manager synaptic apt aptitude anyothers) then remove that file like this:
```
sudo rm /var/cache/apt/archives/lock 
```


You may also need to perform an update once removed:
```
sudo apt-get update 
```

---

### Post by johntkucz on 2007-07-04
thanks christ monkey,

should I delete my entire /var/cache/apt/archives file?  It seems to be causing a lot of problems? What would that do?  How do you know what's innocuous to delete and what's not?

How did you learn about what that cache file does?  How do you know the significance of most of these system files?  Is there some general read-up on that ?

---

### Post by johntkucz on 2007-07-04
I removed the lock file and did sudo apt-get update, but then it threw the same error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by christhemonkey on 2007-07-04
Try executing this command:
```
sudo fuser -km /var/cache/apt/archives/lock 
```

This should kill any process accessing that file, then run:
```
sudo apt-get update 
```

EDIT: Performing that first command killed my pc.... So maybe just try doing this:
```
sudo fuser /var/cache/apt/archives/lock 
```

---

### Post by PaulFr on 2007-07-04
So there are two lock files (/var/cache/apt/archives/lock and /var/lib/dpkg/lock) that are tripping you up - it seems very likely that there is a process that is trying to update your packages.

We need to find what that process is - as indicated above, please run:```
sudo fuser -amuv /var/cache/apt/archives/lock /var/lib/dpkg/lock
``` and see if any process is indicated. If so, we need to first see why that process has this file locked and let it run to completion, or kill it. Please post your output.

If on the other hand, there is no process indicated, then ```
sudo rm /var/cache/apt/archives/lock /var/lib/dpkg/lock
``` should remove both the files. Then please run ```
sudo apt-get check
sudo dpkg -C
``` to verify the state of the package databases. If no problems are indicated, then you can install your package.

Idea: Is the system notification area near the date showing you that you have updates ? Maybe this is the process that is holding the lock. In that case, please click on the icon and install all the updates before you begin to install your own packages.

---

### Post by PaulFr on 2007-07-06
My mistake - I asked you to use ```
sudo fuser -amuv /var/cache/apt/archives/lock /var/lib/dpkg/lock
```. You should instead use ```
sudo fuser -auv /var/cache/apt/archives/lock /var/lib/dpkg/lock
``` to see the processes. Using the **-m** flag means any process writing to the same file system will be output, i.e. not what you want.

---

