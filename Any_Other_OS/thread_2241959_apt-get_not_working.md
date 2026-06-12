---
title: "apt-get not working"
date: 2014-08-29
forum: Any Other OS
---

### Post by alex130 on 2014-08-29
I recently tried to install gnome-tweak-manager and I got errors and can't run some apt-get commands. Here is a copy of my terminal.



```
root@kali:/etc/apt# apt-get install gnome-tweak-tool 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  aptdaemon gir1.2-clutter-gst-1.0 gir1.2-folks-0.6 gir1.2-gee-1.0 gir1.2-gst-plugins-base-0.10 grilo-plugins-0.1 libcamel-1.2-33
  libclutter-gst-1.0-0 libclutter-imcontext-0.1-0 libclutter-imcontext-0.1-bin libcluttergesture-0.0.2-0 libcolord1 libdconf0 libebackend-1.2-2
  libecal-1.2-11 libedata-cal-1.2-15 libedataserver-1.2-16 libgdata13 libgee2 libgrilo-0.1-0 libgupnp-av-1.0-2 libmx-1.0-2 libmx-bin libmx-common
  librest-extras-0.7-0 librhythmbox-core6 libsocialweb-client2 libsocialweb-common libsocialweb-service libsocialweb0 libtelepathy-farstream2
  libxatracker1 nautilus-sendto python-aptdaemon python-defer python-gnupginterface python-mako python-packagekit python-software-properties
  python3-apt python3-aptdaemon python3-defer python3-pkg-resources python3.2 python3.2-minimal unattended-upgrades
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  accountsservice aptdaemon at-spi2-core bluez cheese-common colord colord-data cups-bsd cups-client cups-common dconf-cli dconf-editor
  dconf-gsettings-backend dconf-service dconf-tools dh-python dmsetup empathy empathy-common eog evolution-data-server evolution-data-server-common
  folks-common fontconfig-config gcc-4.9-base gdm3 gedit gedit-common geoclue-2.0 gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gdm3 gir1.2-glib-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0
  gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-2.0 gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-ibus-1.0 gir1.2-mutter-3.0
  gir1.2-nmgtk-1.0 gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-rb-3.0 gir1.2-secret-1 gir1.2-soup-2.4 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gjs glib-networking glib-networking-common glib-networking-services gnome-bluetooth gnome-contacts gnome-control-center
  gnome-control-center-data gnome-desktop3-data gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-symbolic gnome-menus
  gnome-online-accounts gnome-packagekit gnome-packagekit-data gnome-packagekit-session gnome-panel gnome-panel-data gnome-screensaver
  gnome-session gnome-session-bin gnome-session-common gnome-session-fallback gnome-session-flashback gnome-settings-daemon gnome-shell
  gnome-shell-common gnome-shell-extensions gnome-sushi gnome-themes-standard gnome-themes-standard-data gsettings-desktop-schemas
  gstreamer1.0-clutter gstreamer1.0-nice gstreamer1.0-plugins-bad gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-pulseaudio
  gstreamer1.0-x gtk2-engines-pixbuf gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-libs i965-va-driver ifupdown init-system-helpers
  initscripts libaccountsservice0 libapt-inst1.5 libapt-pkg4.12 libarchive13 libass5 libatk1.0-0 libatk1.0-data libatk1.0-dev libatspi2.0-0
  libaudit-common libaudit1 libavcodec55 libavformat55 libavutil53 libc-dev-bin libc6 libc6-dev libc6-i386 libcairo-gobject2
  libcairo-script-interpreter2 libcairo2 libcairo2-dev libcamel-1.2-49 libcaribou-common libcaribou0 libchamplain-0.12-0 libcheese-gtk23 libcheese7
  libchromaprint0 libclutter-1.0-0 libclutter-gst-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libclutter-imcontext-0.1-0
  libclutter-imcontext-0.1-bin libcluttergesture-0.0.2-0 libcogl-pango20 libcogl-path20 libcogl20 libcolord-gtk1 libcolord2 libcolorhug2 libcrack2
  libcups2 libcupsfilters1 libcupsimage2 libdb5.3 libdbus-glib-1-2 libdconf1 libdevmapper1.02.1 libdrm-dev libdrm-intel1 libdrm-nouveau2
  libdrm-radeon1 libdrm2 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20 libedata-cal-1.2-23
  libedataserver-1.2-18 libegl1-mesa libegl1-mesa-dev libegl1-mesa-drivers libelfg0 libepoxy0 libevdev2 libfarstream-0.2-2 libffi6 libflac8
  libfluidsynth1 libfolks-eds25 libfolks-telepathy25 libfolks25 libfontconfig1 libfontconfig1-dev libgail-3-0 libgail-common libgail18 libgbm1
  libgck-1-0 libgcr-3-1 libgcr-base-3-1 libgcr-ui-3-1 libgcrypt11 libgcrypt20 libgd3 libgdata19 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common
  libgdk-pixbuf2.0-dev libgdm1 libgee-0.8-2 libgeocode-glib0 libgirepository-1.0-1 libgjs0e libgl1-mesa-dev libgl1-mesa-glx libglapi-mesa
  libglib2.0-0 libglib2.0-bin libglib2.0-dev libgmp10 libgnome-bluetooth13 libgnome-desktop-3-10 libgnomekbd-common libgnomekbd8 libgnutls-deb0-28
  libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-1 libgphoto2-6 libgphoto2-port10 libgraphite2-3 libgrilo-0.2-1 libgssapi-krb5-2
  libgstreamer-plugins-bad1.0-0 libgstreamer-plugins-base1.0-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-dev libgtkglext1 libgtksourceview-3.0-1 libgtksourceview-3.0-common libgweather-3-6 libgweather-common libharfbuzz-dev
  libharfbuzz-gobject0 libharfbuzz-icu0 libharfbuzz0b libhogweed2 libibus-1.0-5 libical1 libicu52 libimobiledevice4 libinput0
  libjavascriptcoregtk-3.0-0 libkeyutils1 libkrb5-3 libkrb5support0 liblcms2-2 libllvm3.4 libmbim-glib0 libmission-control-plugins0
  libmjpegutils-2.1-0 libmm-glib0 libmotif-common libmozjs-24-0 libmpdec2 libmpeg2encpp-2.1-0 libmpg123-0 libmplex2-2.1-0 libmrm4 libmtp-runtime
  libmtp9 libmutter0d libmx-1.0-2 libmx-common libndp0 libnettle4 libnl-3-200 libnl-genl-3-200 libnl-route-3-200 libnm-glib4 libnm-gtk-common
  libnm-gtk0 libnm-util2 libopencv-calib3d2.4 libopencv-contrib2.4 libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4 libopencv-ml2.4 libopencv-objdetect2.4 libopencv-video2.4 libopenjpeg5
  libopenvg1-mesa libopus0 liborc-0.4-0 libp11-kit0 libpackagekit-glib2-16 libpam-systemd libpango-1.0-0 libpango1.0-0 libpango1.0-dev
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpangox-1.0-0 libpangoxft-1.0-0 libpcre3 libpcre3-dev libpcrecpp0 libpixman-1-0 libpixman-1-dev libplist2
  libpoppler46 libproxy1 libpwquality-common libpwquality1 libpython-stdlib libpython2.7 libpython2.7-minimal libpython2.7-stdlib libpython3-stdlib
  libpython3.4-minimal libpython3.4-stdlib libqmi-glib1 libqmi-proxy librhythmbox-core8 librsvg2-2 librsvg2-common librtmp1 libsbc1 libsecret-1-0
  libsecret-common libsoundtouch0 libsoup2.4-1 libsoup2.4-dev libsrtp0 libstdc++6 libswscale2 libsystemd-daemon0 libsystemd-id128-0
  libsystemd-journal0 libsystemd-login0 libtasn1-6 libtbb2 libtelepathy-farstream3 libtelepathy-glib0 libtelepathy-logger3 libtiff5 libtirpc1
  libtotem-plparser18 libtracker-sparql-1.0-0 libudev1 libudisks2-0 libuil4 libupower-glib2 libusbmuxd2 libva1 libvdpau1 libvpx1 libwacom-common
  libwacom2 libwayland-client0 libwayland-cursor0 libwayland-dev libwayland-egl1-mesa libwayland-server0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwebp5 libx11-6 libx11-dev libx11-xcb-dev libx11-xcb1 libx264-142 libxatracker2 libxcb-dri2-0 libxcb-dri2-0-dev libxcb-dri3-0 libxcb-dri3-dev
  libxcb-glx0 libxcb-glx0-dev libxcb-icccm4 libxcb-image0 libxcb-present-dev libxcb-present0 libxcb-randr0 libxcb-randr0-dev libxcb-shape0
  libxcb-shape0-dev libxcb-sync-dev libxcb-sync1 libxcb-xf86dri0 libxcb-xfixes0 libxcb-xfixes0-dev libxcb1 libxcb1-dev libxi-dev libxi6
  libxkbcommon0 libxm4 libxml2 libxml2-dev libxshmfence-dev libxshmfence1 libxxf86vm-dev libxxf86vm1 libzeitgeist-2.0-0 locales lvm2
  mesa-common-dev modemmanager mutter-common nautilus nautilus-data nautilus-open-terminal nautilus-sendto network-manager network-manager-gnome
  nfs-common packagekit packagekit-backend-aptcc packagekit-tools policykit-1 ppp python python-aptdaemon python-gi python-gi-cairo python-minimal
  python2.7 python2.7-minimal python3 python3-apt python3-aptdaemon python3-cairo python3-dbus python3-defer python3-gi python3-gi-cairo
  python3-mako python3-markupsafe python3-minimal python3-packagekit python3-pkg-resources python3.4 python3.4-minimal rhythmbox rhythmbox-data
  rhythmbox-plugins startpar systemd systemd-sysv sysvinit-utils telepathy-mission-control-5 udisks2 upower usbmuxd va-driver-all vdpau-va-driver
  x11proto-dri2-dev x11proto-gl-dev x11proto-xf86vidmode-dev xpdf xserver-common xserver-xephyr xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-modesetting xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb
  xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xvfb
Suggested packages:
  cups xpp telepathy-idle evolution evolution-data-server-dbg gedit-plugins gstreamer1.0-libav frei0r-plugins rdnssd lrzip glibc-doc libcairo2-doc
  libchromaprint-tools python-acoustid libgles2-mesa libgles2 rng-tools libgd-tools libglib2.0-doc gnutls-bin gphoto2 gtkam grilo-plugins-0.2
  krb5-doc krb5-user gstreamer-codec-install gnome-codec-install gstreamer1.0-tools libgtk2.0-doc libusbmuxd-tools liblcms2-utils opus-tools
  libpango1.0-doc librsvg2-bin libsoup2.4-doc srtp-utils nvidia-vdpau-driver vdpau-driver libxcb-doc thin-provisioning-tools xdg-user-dirs
  avahi-autoipd network-manager-openconnect-gnome network-manager-openvpn-gnome network-manager-vpnc-gnome network-manager-pptp-gnome open-iscsi
  watchdog packagekit-backend-smart python-doc python2.7-doc python3-doc python3-tk python3-venv python3-apt-dbg python-apt-doc python-dbus-doc
  python3-dbus-dbg python3-beaker python-mako-doc python3-setuptools python3.4-venv python3.4-doc rhythmbox-plugin-cdrecorder systemd-ui bootlogd
  sash xfsprogs reiserfsprogs exfat-utils btrfs-tools mdadm xfonts-100dpi xfonts-75dpi xfonts-scalable gpointing-device-settings touchfreeze xinput
Recommended packages:
  lintian rygel rygel-tracker system-config-printer libnss-myhostname realmd cracklib-runtime gstreamer1.0-plugins-ugly xserver-xorg-video-qxl
The following packages will be REMOVED:
  intel-linux-graphics-installer libaudit0 libcheese-gtk21 libcheese3 libcogl-pango0 libcogl9 libebook-1.2-13 libedata-book-1.2-13
  libedataserverui-3.0-1 libgjs0b libgnome-desktop-3-2 libgoa-1.0-0 libgtksourceview-3.0-0 libmutter0 libpackagekit-glib2-14 locales-all
  nautilus-sendto-empathy xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-chips xserver-xorg-video-i128
  xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-sis xserver-xorg-video-tseng
  xserver-xorg-video-voodoo
The following NEW packages will be installed:
  colord-data dconf-cli dconf-editor dh-python gcc-4.9-base geoclue-2.0 gir1.2-clutter-gst-2.0 gir1.2-gdm3 gir1.2-gnomedesktop-3.0
  gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-ibus-1.0 gir1.2-nmgtk-1.0 gir1.2-notify-0.7 gir1.2-secret-1 gnome-packagekit-session
  gnome-session-flashback gnome-tweak-tool gstreamer1.0-clutter gstreamer1.0-nice gstreamer1.0-plugins-bad gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf i965-va-driver init-system-helpers libarchive13 libass5
  libaudit-common libaudit1 libavcodec55 libavformat55 libavutil53 libcamel-1.2-49 libcheese-gtk23 libcheese7 libchromaprint0 libclutter-gst-2.0-0
  libcogl-pango20 libcogl-path20 libcogl20 libcolord-gtk1 libcolord2 libcolorhug2 libcrack2 libcupsfilters1 libdb5.3 libdconf1 libdrm-dev
  libdrm-nouveau2 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20 libedata-cal-1.2-23
  libedataserver-1.2-18 libegl1-mesa libegl1-mesa-dev libegl1-mesa-drivers libelfg0 libepoxy0 libevdev2 libfarstream-0.2-2 libffi6 libfluidsynth1
  libgbm1 libgcr-base-3-1 libgcr-ui-3-1 libgcrypt20 libgd3 libgdata19 libgdm1 libgee-0.8-2 libgjs0e libgl1-mesa-dev libgnome-bluetooth13
  libgnome-desktop-3-10 libgnomekbd8 libgnutls-deb0-28 libgoa-1.0-0b libgoa-backend-1.0-1 libgphoto2-6 libgphoto2-port10 libgraphite2-3
  libgrilo-0.2-1 libgstreamer-plugins-bad1.0-0 libgstreamer-plugins-base1.0-0 libgstreamer1.0-0 libgtkglext1 libgtksourceview-3.0-1 libgweather-3-6
  libharfbuzz-dev libharfbuzz-gobject0 libharfbuzz-icu0 libharfbuzz0b libhogweed2 libibus-1.0-5 libical1 libicu52 libimobiledevice4 libinput0
  libllvm3.4 libmbim-glib0 libmjpegutils-2.1-0 libmm-glib0 libmotif-common libmozjs-24-0 libmpdec2 libmpeg2encpp-2.1-0 libmpg123-0 libmplex2-2.1-0
  libmrm4 libmutter0d libndp0 libopencv-calib3d2.4 libopencv-contrib2.4 libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4 libopencv-ml2.4 libopencv-objdetect2.4 libopencv-video2.4 libopenjpeg5
  libopenvg1-mesa libpackagekit-glib2-16 libpam-systemd libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangox-1.0-0 libpangoxft-1.0-0
  libplist2 libpoppler46 libproxy1 libpwquality-common libpwquality1 libpython-stdlib libpython2.7-minimal libpython2.7-stdlib libpython3-stdlib
  libpython3.4-minimal libpython3.4-stdlib libqmi-glib1 libqmi-proxy librhythmbox-core8 librtmp1 libsbc1 libsecret-1-0 libsecret-common libsrtp0
  libsystemd-id128-0 libsystemd-journal0 libtasn1-6 libtbb2 libtelepathy-farstream3 libtelepathy-logger3 libtiff5 libtotem-plparser18
  libtracker-sparql-1.0-0 libudev1 libudisks2-0 libuil4 libupower-glib2 libusbmuxd2 libvdpau1 libwayland-client0 libwayland-cursor0 libwayland-dev
  libwayland-egl1-mesa libwayland-server0 libwebp5 libx11-xcb-dev libx264-142 libxatracker2 libxcb-dri2-0-dev libxcb-dri3-0 libxcb-dri3-dev
  libxcb-glx0-dev libxcb-icccm4 libxcb-image0 libxcb-present-dev libxcb-present0 libxcb-randr0-dev libxcb-shape0-dev libxcb-sync-dev libxcb-sync1
  libxcb-xf86dri0 libxcb-xfixes0-dev libxkbcommon0 libxm4 libxshmfence-dev libxshmfence1 libxxf86vm-dev libzeitgeist-2.0-0 mesa-common-dev
  python3-apt python3-aptdaemon python3-cairo python3-dbus python3-defer python3-gi python3-gi-cairo python3-mako python3-markupsafe
  python3-packagekit python3-pkg-resources python3.4 python3.4-minimal startpar systemd systemd-sysv udisks2 va-driver-all vdpau-va-driver
  x11proto-dri2-dev x11proto-gl-dev x11proto-xf86vidmode-dev xserver-xorg-video-modesetting
The following packages will be upgraded:
  accountsservice aptdaemon at-spi2-core bluez cheese-common colord cups-bsd cups-client cups-common dconf-gsettings-backend dconf-service
  dconf-tools dmsetup empathy empathy-common eog evolution-data-server evolution-data-server-common folks-common fontconfig-config gdm3 gedit
  gedit-common gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-freedesktop
  gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-2.0 gir1.2-gtk-3.0
  gir1.2-gtksource-3.0 gir1.2-mutter-3.0 gir1.2-pango-1.0 gir1.2-rb-3.0 gir1.2-soup-2.4 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gjs
  glib-networking glib-networking-common glib-networking-services gnome-bluetooth gnome-contacts gnome-control-center gnome-control-center-data
  gnome-desktop3-data gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-symbolic gnome-menus gnome-online-accounts gnome-packagekit
  gnome-packagekit-data gnome-panel gnome-panel-data gnome-screensaver gnome-session gnome-session-bin gnome-session-common gnome-session-fallback
  gnome-settings-daemon gnome-shell gnome-shell-common gnome-shell-extensions gnome-sushi gnome-themes-standard gnome-themes-standard-data
  gsettings-desktop-schemas gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-libs ifupdown initscripts libaccountsservice0 libapt-inst1.5
  libapt-pkg4.12 libatk1.0-0 libatk1.0-data libatk1.0-dev libatspi2.0-0 libc-dev-bin libc6 libc6-dev libc6-i386 libcairo-gobject2
  libcairo-script-interpreter2 libcairo2 libcairo2-dev libcaribou-common libcaribou0 libchamplain-0.12-0 libclutter-1.0-0 libclutter-gst-1.0-0
  libclutter-gtk-1.0-0 libclutter-imcontext-0.1-0 libclutter-imcontext-0.1-bin libcluttergesture-0.0.2-0 libcups2 libcupsimage2 libdbus-glib-1-2
  libdevmapper1.02.1 libdrm-intel1 libdrm-radeon1 libdrm2 libflac8 libfolks-eds25 libfolks-telepathy25 libfolks25 libfontconfig1 libfontconfig1-dev
  libgail-3-0 libgail-common libgail18 libgck-1-0 libgcr-3-1 libgcrypt11 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdk-pixbuf2.0-dev
  libgeocode-glib0 libgirepository-1.0-1 libgl1-mesa-glx libglapi-mesa libglib2.0-0 libglib2.0-bin libglib2.0-dev libgmp10 libgnomekbd-common
  libgoa-1.0-common libgssapi-krb5-2 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-dev libgtksourceview-3.0-common
  libgweather-common libjavascriptcoregtk-3.0-0 libkeyutils1 libkrb5-3 libkrb5support0 liblcms2-2 libmission-control-plugins0 libmtp-runtime
  libmtp9 libmx-1.0-2 libmx-common libnettle4 libnl-3-200 libnl-genl-3-200 libnl-route-3-200 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2
  libopus0 liborc-0.4-0 libp11-kit0 libpango1.0-0 libpango1.0-dev libpcre3 libpcre3-dev libpcrecpp0 libpixman-1-0 libpixman-1-dev libpython2.7
  librsvg2-2 librsvg2-common libsoundtouch0 libsoup2.4-1 libsoup2.4-dev libstdc++6 libswscale2 libsystemd-daemon0 libsystemd-login0
  libtelepathy-glib0 libtirpc1 libva1 libvpx1 libwacom-common libwacom2 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libx11-6 libx11-dev libx11-xcb1
  libxcb-dri2-0 libxcb-glx0 libxcb-randr0 libxcb-shape0 libxcb-xfixes0 libxcb1 libxcb1-dev libxi-dev libxi6 libxml2 libxml2-dev libxxf86vm1 locales
  lvm2 modemmanager mutter-common nautilus nautilus-data nautilus-open-terminal nautilus-sendto network-manager network-manager-gnome nfs-common
  packagekit packagekit-backend-aptcc packagekit-tools policykit-1 ppp python python-aptdaemon python-gi python-gi-cairo python-minimal python2.7
  python2.7-minimal python3 python3-minimal rhythmbox rhythmbox-data rhythmbox-plugins sysvinit-utils telepathy-mission-control-5 upower usbmuxd
  xpdf xserver-common xserver-xephyr xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa
  xserver-xorg-video-vmware xvfb
271 upgraded, 224 newly installed, 27 to remove and 1540 not upgraded.
Need to get 238 MB of archives.
After this operation, 151 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-common all 2:1.16.0-1 [1,741 kB]
Get:2 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-all amd64 1:7.7+7 [36.7 kB]    
Get:3 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-vmware amd64 1:13.0.2-3+b1 [102 kB]        
Get:4 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-vesa amd64 1:2.3.3-1+b3 [29.9 kB]        
Get:5 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-trident amd64 1:1.3.6-2+b2 [66.7 kB]      
Get:6 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-sisusb amd64 1:0.9.6-2+b2 [47.4 kB]          
Get:7 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-siliconmotion amd64 1:1.7.7-2+b2 [83.0 kB]  
Get:8 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xvfb amd64 2:1.16.0-1 [2,468 kB]                   
Get:9 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-savage amd64 1:2.3.7-2+b2 [90.6 kB]
Get:10 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-radeon amd64 1:7.4.0-2 [415 kB]
Get:11 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-r128 amd64 6.9.2-1+b2 [178 kB]     
Get:12 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-neomagic amd64 1:1.2.8-1+b2 [41.1 kB]
Get:13 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-mga amd64 1:1.6.3-2+b1 [98.7 kB]  
Get:14 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-mach64 amd64 6.9.4-1+b3 [197 kB]
Get:15 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-intel amd64 2:2.21.15-2+b2 [1,330 kB]
Get:16 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-cirrus amd64 1:1.5.2-2+b1 [40.6 kB]                                              
Get:17 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-ati amd64 1:7.4.0-2 [301 kB]                                                     
Get:18 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-input-wacom amd64 0.23.0+20131011-1+b2 [85.6 kB]                                       
Get:19 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-core amd64 2:1.16.0-1 [3,048 kB]                                                       
Get:20 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-tdfx amd64 1:1.4.5-1+b2 [42.2 kB]                                                
Get:21 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-openchrome amd64 1:0.3.3-1+b2 [200 kB]                                           
Get:22 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-nouveau amd64 1:1.0.10-1+b2 [299 kB]                                             
Get:23 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-fbdev amd64 1:0.4.4-1+b2 [23.2 kB]                                               
Get:24 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-input-vmmouse amd64 1:13.0.0-1+b3 [28.1 kB]                                            
Get:25 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-input-synaptics amd64 1.8.0-1 [208 kB]                                                 
Get:26 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-input-mouse amd64 1:1.9.0-1+b3 [66.2 kB]                                               
Get:27 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-input-evdev amd64 1:2.8.2-1+b2 [110 kB]                                                
Get:28 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xephyr amd64 2:1.16.0-1 [2,632 kB]                                                          
Get:29 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-screensaver amd64 3.6.1-1+b1 [234 kB]                                                         
Get:30 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-shell-extensions all 3.12.2-1 [130 kB]                                                        
Get:31 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-shell-common all 3.12.2-3 [627 kB]                                                            
Get:32 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-freedesktop amd64 1.40.0-2 [20.2 kB]                                                         
Get:33 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-shell amd64 3.12.2-3 [609 kB]                                                                 
Get:34 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-menus amd64 3.13.3-1 [135 kB]                                                                 
Get:35 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-panel amd64 3.8.0-3+b2 [581 kB]                                                               
Get:36 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-glib-2.0 amd64 1.40.0-2 [138 kB]                                                             
Get:37 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-control-center-data all 1:3.12.1-4 [3,949 kB]                                                 
Get:38 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gdm3 amd64 3.12.2-2.1 [609 kB]                                                                      
Get:39 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-control-center amd64 1:3.12.1-4 [3,231 kB]                                                    
Get:40 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-settings-daemon amd64 3.12.2-1 [1,212 kB]                                                     
Get:41 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main at-spi2-core amd64 2.12.0-2 [45.6 kB]                                                               
Get:42 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libaudit-common all 1:2.3.7-1 [13.0 kB]                                                             
Get:43 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgssapi-krb5-2 amd64 1.12.1+dfsg-7 [147 kB]                                                       
Get:44 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libkrb5support0 amd64 1.12.1+dfsg-7 [57.2 kB]                                                       
Get:45 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main nfs-common amd64 1:1.2.8-9 [206 kB]                                                                 
Get:46 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main startpar amd64 0.59-3 [21.8 kB]                                                                     
Get:47 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main sysvinit-utils amd64 2.88dsf-53.2kali2 [83.0 kB]                                                    
Get:48 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main ifupdown amd64 0.7.48.1 [66.0 kB]                                                                   
Get:49 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main initscripts amd64 2.88dsf-53.2kali2 [86.1 kB]                                                       
Get:50 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libkeyutils1 amd64 1.5.9-5 [11.7 kB]                                                                
Get:51 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libkrb5-3 amd64 1.12.1+dfsg-7 [298 kB]                                                              
Get:52 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libc6-dev amd64 2.19-9 [1,997 kB]                                                                   
Get:53 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libtirpc1 amd64 0.2.4-2.1 [77.8 kB]                                                                 
Get:54 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main locales all 2.19-9 [3,921 kB]                                                                       
Get:55 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libc-dev-bin amd64 2.19-9 [238 kB]                                                                  
Get:56 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libudev1 amd64 208-8 [50.5 kB]                                                                      
Get:57 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main dmsetup amd64 2:1.02.88-1 [68.3 kB]                                                                 
Get:58 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libaudit1 amd64 1:2.3.7-1 [43.4 kB]                                                                 
Get:59 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libglapi-mesa amd64 10.2.5-1 [53.4 kB]                                                              
Get:60 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb1-dev amd64 1.10-3 [81.8 kB]                                                                  
Get:61 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb1 amd64 1.10-3 [42.6 kB]                                                                      
Get:62 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libx11-xcb1 amd64 2:1.6.2-3 [163 kB]                                                                
Get:63 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-sync1 amd64 1.10-3 [13.8 kB]                                                                 
Get:64 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libdrm-radeon1 amd64 2.4.56-1 [30.8 kB]                                                             
Get:65 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libdrm-intel1 amd64 2.4.56-1 [63.4 kB]                                                              
Get:66 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xserver-xorg-video-modesetting amd64 0.9.0-1+b1 [31.7 kB]                                           
Get:67 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gcc-4.9-base amd64 4.9.1-4 [157 kB]                                                                 
Get:68 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libllvm3.4 amd64 1:3.4.2-8 [6,722 kB]                                                               
Get:69 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libc6 amd64 2.19-9 [4,821 kB]                                                                       
Get:70 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxi6 amd64 2:1.7.4-1 [79.0 kB]                                                                    
Get:71 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libwayland-server0 amd64 1.5.0-1 [27.6 kB]                                                          
Get:72 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-shape0 amd64 1.10-3 [11.2 kB]                                                                
Get:73 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libepoxy0 amd64 1.2-1 [166 kB]                                                                      
Get:74 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-icccm4 amd64 0.4.1-1 [27.0 kB]                                                               
Get:75 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-xf86dri0 amd64 1.10-3 [12.0 kB]                                                              
Get:76 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main glib-networking-common all 2.40.1-2 [51.2 kB]                                                       
Get:77 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libnettle4 amd64 2.7.1-3 [175 kB]                                                                   
Get:78 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libp11-kit0 amd64 0.20.3-2 [153 kB]                                                                 
Get:79 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libtasn1-6 amd64 4.0-2 [47.9 kB]                                                                    
Get:80 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgnutls-deb0-28 amd64 3.2.16-1 [970 kB]                                                           
Get:81 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpython2.7 amd64 2.7.8-5 [1,054 kB]                                                               
Get:82 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python2.7 amd64 2.7.8-5 [244 kB]                                                                    
Get:83 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python2.7-minimal amd64 2.7.8-5 [1,375 kB]                                                          
Get:84 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpython2.7-minimal amd64 2.7.8-5 [348 kB]                                                         
Get:85 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpython2.7-stdlib amd64 2.7.8-5 [1,881 kB]                                                        
Get:86 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libc6-i386 amd64 2.19-9 [2,386 kB]                                                                  
Get:87 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python amd64 2.7.8-1 [151 kB]                                                                       
Get:88 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python-minimal amd64 2.7.8-1 [39.7 kB]                                                              
Get:89 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libelfg0 amd64 0.8.13-5 [51.6 kB]                                                                   
Get:90 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libglib2.0-bin amd64 2.40.0-4 [1,360 kB]                                                            
Get:91 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libdevmapper1.02.1 amd64 2:1.02.88-1 [143 kB]                                                       
Get:92 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgcrypt11 amd64 1.5.4-2 [256 kB]                                                                  
Get:93 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libdrm2 amd64 2.4.56-1 [29.4 kB]                                                                    
Get:94 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgl1-mesa-glx amd64 10.2.5-1 [151 kB]                                                             
Get:95 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libx11-dev amd64 2:1.6.2-3 [800 kB]                                                                 
Get:96 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpcre3-dev amd64 1:8.35-3 [468 kB]                                                                
Get:97 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libx11-6 amd64 2:1.6.2-3 [729 kB]                                                                   
Get:98 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main liblcms2-2 amd64 2.6-3 [140 kB]                                                                     
Get:99 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopenjpeg5 amd64 1.5.2-2 [109 kB]                                                                 
Get:100 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libtiff5 amd64 4.0.3-9 [211 kB]                                                                    
Get:101 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpoppler46 amd64 0.26.4-1 [1,210 kB]                                                             
Get:102 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-dri2-0 amd64 1.10-3 [12.4 kB]                                                               
Get:103 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-dri3-0 amd64 1.10-3 [10.7 kB]                                                               
Get:104 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-glx0 amd64 1.10-3 [25.9 kB]                                                                 
Get:105 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-present0 amd64 1.10-3 [10.8 kB]                                                             
Get:106 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxshmfence1 amd64 1.1-2 [6,452 B]                                                                
Get:107 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxxf86vm1 amd64 1:1.1.3-1 [19.1 kB]                                                              
Get:108 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpixman-1-dev amd64 0.32.6-2 [523 kB]                                                            
Get:109 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmotif-common all 2.3.4-5 [27.4 kB]                                                              
Get:110 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxm4 amd64 2.3.4-5 [988 kB]                                                                      
Get:111 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpixman-1-0 amd64 0.32.6-2 [506 kB]                                                              
Get:112 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgraphite2-3 amd64 1.2.4-3 [57.4 kB]                                                             
Get:113 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpango1.0-dev amd64 1.36.6-1 [464 kB]                                                            
Get:114 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpango1.0-0 amd64 1.36.6-1 [181 kB]                                                              
Get:115 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpangoft2-1.0-0 amd64 1.36.6-1 [211 kB]                                                          
Get:116 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libdrm-nouveau2 amd64 2.4.56-1 [21.3 kB]                                                           
Get:117 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpangoxft-1.0-0 amd64 1.36.6-1 [193 kB]                                                          
Get:118 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libffi6 amd64 3.1-2 [19.8 kB]                                                                      
Get:119 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libstdc++6 amd64 4.9.1-4 [273 kB]                                                                  
Get:120 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libharfbuzz-icu0 amd64 0.9.35-1 [360 kB]                                                           
Get:121 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libharfbuzz-dev amd64 0.9.35-1 [384 kB]                                                            
Get:122 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxatracker2 amd64 10.2.5-1 [210 kB]                                                              
Get:123 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxi-dev amd64 2:1.7.4-1 [237 kB]                                                                 
Get:124 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpango-1.0-0 amd64 1.36.6-1 [288 kB]                                                             
Get:125 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libevdev2 amd64 1.2.2+dfsg-1 [27.0 kB]                                                             
Get:126 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libwayland-client0 amd64 1.5.0-1 [22.6 kB]                                                         
Get:127 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgbm1 amd64 10.2.5-1 [138 kB]                                                                    
Get:128 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxml2-dev amd64 2.9.1+dfsg1-4 [689 kB]                                                           
Get:129 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-xfixes0 amd64 1.10-3 [14.2 kB]                                                              
Get:130 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libegl1-mesa amd64 10.2.5-1 [87.9 kB]                                                              
Get:131 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali/main libxcb-image0 amd64 0.3.9-1 [22.3 kB]                                                                  
Get:132 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libproxy1 amd64 0.4.11-4 [52.7 kB]                                                                 
Get:133 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main glib-networking amd64 2.40.1-2 [50.1 kB]                                                           
Get:134 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main glib-networking-services amd64 2.40.1-2 [16.2 kB]                                                  
Get:135 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgmp10 amd64 2:6.0.0+dfsg-6 [253 kB]                                                             
Get:136 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgdk-pixbuf2.0-0 amd64 2.30.7-1 [163 kB]                                                         
Get:137 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gtk-2.0 amd64 2.24.24-1 [693 kB]                                                            
Get:138 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libhogweed2 amd64 2.7.1-3 [125 kB]                                                                 
Get:139 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgirepository-1.0-1 amd64 1.40.0-2 [91.8 kB]                                                     
Get:140 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libatk1.0-dev amd64 2.12.0-1 [124 kB]                                                              
Get:141 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-atk-1.0 amd64 2.12.0-1 [65.6 kB]                                                            
Get:142 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libdb5.3 amd64 5.3.28-6 [679 kB]                                                                   
Get:143 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgtk2.0-dev amd64 2.24.24-1 [3,112 kB]                                                           
Get:144 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpython-stdlib amd64 2.7.8-1 [19.2 kB]                                                           
Get:145 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libglib2.0-dev amd64 2.40.0-4 [2,662 kB]                                                           
Get:146 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgtk2.0-bin amd64 2.24.24-1 [531 kB]                                                             
Get:147 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcupsfilters1 amd64 1.0.58-1 [104 kB]                                                            
Get:148 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpcre3 amd64 1:8.35-3 [336 kB]                                                                   
Get:149 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcupsimage2 amd64 1.7.5-1 [115 kB]                                                               
Get:150 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main cups-bsd amd64 1.7.5-1 [35.3 kB]                                                                   
Get:151 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpcrecpp0 amd64 1:8.35-3 [142 kB]                                                                
Get:152 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libatk1.0-0 amd64 2.12.0-1 [91.0 kB]                                                               
Get:153 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgtk2.0-0 amd64 2.24.24-1 [2,280 kB]                                                             
Get:154 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libatk1.0-data all 2.12.0-1 [179 kB]                                                               
Get:155 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main xpdf amd64 3.03-17+b1 [155 kB]                                                                     
Get:156 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libfontconfig1-dev amd64 2.11.0-6 [894 kB]                                                         
Get:157 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libfontconfig1 amd64 2.11.0-6 [328 kB]                                                             
Get:158 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main fontconfig-config all 2.11.0-6 [273 kB]                                                            
Get:159 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libharfbuzz0b amd64 0.9.35-1 [485 kB]                                                              
Get:160 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpangocairo-1.0-0 amd64 1.36.6-1 [198 kB]                                                        
Get:161 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-pango-1.0 amd64 1.36.6-1 [198 kB]                                                           
Get:162 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-themes-standard amd64 3.12.0-1 [266 kB]                                                      
Get:163 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libicu52 amd64 52.1-5 [6,774 kB]                                                                   
Get:164 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgtk-3-0 amd64 3.12.2-3 [2,119 kB]                                                               
Get:165 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgail-3-0 amd64 3.12.2-3 [65.9 kB]                                                               
Get:166 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main dconf-service amd64 0.20.0-2 [41.0 kB]                                                             
Get:167 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcolord2 amd64 1.2.1-1 [226 kB]                                                                  
Get:168 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-soup-2.4 amd64 2.46.0-2 [73.6 kB]                                                           
Get:169 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libsoup2.4-1 amd64 2.46.0-2 [253 kB]                                                               
Get:170 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libatspi2.0-0 amd64 2.12.0-2 [56.2 kB]                                                             
Get:171 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpython3.4-minimal amd64 3.4.1-10 [490 kB]                                                       
Get:172 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmpdec2 amd64 2.4.0-6 [82.0 kB]                                                                  
Get:173 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpython3.4-stdlib amd64 3.4.1-10 [2,081 kB]                                                      
Get:174 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libharfbuzz-gobject0 amd64 0.9.35-1 [365 kB]                                                       
Get:175 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main dh-python all 1.20140511-1 [52.8 kB]                                                               
Get:176 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpangox-1.0-0 amd64 0.0.2-4 [41.4 kB]                                                            
Get:177 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgck-1-0 amd64 3.12.2-1 [87.9 kB]                                                                
Get:178 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxml2 amd64 2.9.1+dfsg1-4 [797 kB]                                                               
Get:179 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgcr-3-1 amd64 3.12.2-1 [16.7 kB]                                                                
Get:180 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgcr-ui-3-1 amd64 3.12.2-1 [154 kB]                                                              
Get:181 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libsecret-common all 0.18-1 [19.9 kB]                                                              
Get:182 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main init-system-helpers all 1.21 [13.9 kB]                                                             
Get:183 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main ppp amd64 2.4.6-2 [331 kB]                                                                         
Get:184 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main network-manager amd64 0.9.10.0-1.1 [1,431 kB]                                                      
Get:185 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main librsvg2-common amd64 2.40.3-1 [170 kB]                                                            
Get:186 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgdk-pixbuf2.0-dev amd64 2.30.7-1 [51.0 kB]                                                      
Get:187 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgdk-pixbuf2.0-common all 2.30.7-1 [293 kB]                                                      
Get:188 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main librsvg2-2 amd64 2.40.3-1 [247 kB]                                                                 
Get:189 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmm-glib0 amd64 1.2.0-1 [164 kB]                                                                 
Get:190 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gdkpixbuf-2.0 amd64 2.30.7-1 [15.8 kB]                                                      
Get:191 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgail-common amd64 2.24.24-1 [633 kB]                                                            
Get:192 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libndp0 amd64 1.4-1 [10.3 kB]                                                                      
Get:193 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libnl-3-200 amd64 3.2.24-2 [56.0 kB]                                                               
Get:194 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libnm-util2 amd64 0.9.10.0-1.1 [363 kB]                                                            
Get:195 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libnm-glib4 amd64 0.9.10.0-1.1 [316 kB]                                                            
Get:196 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgail18 amd64 2.24.24-1 [536 kB]                                                                 
Get:197 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libsystemd-login0 amd64 208-8 [42.1 kB]                                                            
Get:198 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main lvm2 amd64 2.02.109-1 [696 kB]                                                                     
Get:199 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main cups-common all 1.7.5-1 [272 kB]                                                                   
Get:200 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main cups-client amd64 1.7.5-1 [296 kB]                                                                 
Get:201 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libsystemd-journal0 amd64 208-8 [69.3 kB]                                                          
Get:202 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main systemd amd64 208-8 [1,332 kB]                                                                     
Get:203 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcups2 amd64 1.7.5-1 [282 kB]                                                                    
Get:204 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgtk-3-bin amd64 3.12.2-3 [92.5 kB]                                                              
Get:205 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgtk-3-common all 3.12.2-3 [3,011 kB]                                                            
Get:206 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libnm-gtk0 amd64 0.9.10.0-2 [120 kB]                                                               
Get:207 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-icon-theme-symbolic all 3.12.0-1 [145 kB]                                                    
Get:208 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-icon-theme-extras all 3.12.0-1 [850 kB]                                                      
Get:209 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-icon-theme all 3.12.0-1 [9,898 kB]                                                           
Get:210 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-themes-standard-data all 3.12.0-1 [3,655 kB]                                                 
Get:211 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libwayland-cursor0 amd64 1.5.0-1 [12.2 kB]                                                         
Get:212 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxkbcommon0 amd64 0.4.1-2 [113 kB]                                                               
Get:213 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libaccountsservice0 amd64 0.6.37-3 [75.6 kB]                                                       
Get:214 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libdconf1 amd64 0.20.0-2 [34.8 kB]                                                                 
Get:215 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgcrypt20 amd64 1.6.1-3 [388 kB]                                                                 
Get:216 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main dconf-gsettings-backend amd64 0.20.0-2 [33.5 kB]                                                   
Get:217 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libsoup2.4-dev amd64 2.46.0-2 [356 kB]                                                             
Get:218 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main nautilus-open-terminal amd64 0.20-1 [70.5 kB]                                                      
Get:219 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgrilo-0.2-1 amd64 0.2.10-1 [221 kB]                                                             
Get:220 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3.4-minimal amd64 3.4.1-10 [1,644 kB]                                                        
Get:221 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libplist2 amd64 1.11-3 [26.4 kB]                                                                   
Get:222 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libusbmuxd2 amd64 1.0.9-1 [14.6 kB]                                                                
Get:223 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libimobiledevice4 amd64 1.1.6+dfsg-3.1 [56.5 kB]                                                   
Get:224 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libwebp5 amd64 0.4.0-4.1 [181 kB]                                                                  
Get:225 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libwebkitgtk-3.0-common all 2.4.4-2 [449 kB]                                                       
Get:226 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libjavascriptcoregtk-3.0-0 amd64 2.4.4-2 [1,965 kB]                                                
Get:227 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3 amd64 3.4.1-1 [20.9 kB]                                                                    
Get:228 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3-minimal amd64 3.4.1-1 [34.2 kB]                                                            
Get:229 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3.4 amd64 3.4.1-10 [201 kB]                                                                  
Get:230 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpython3-stdlib amd64 3.4.1-1 [17.9 kB]                                                          
Get:231 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcamel-1.2-49 amd64 3.12.2-1 [473 kB]                                                            
Get:232 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgcr-base-3-1 amd64 3.12.2-1 [197 kB]                                                            
Get:233 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libsecret-1-0 amd64 0.18-1 [94.0 kB]                                                               
Get:234 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmtp9 amd64 1.1.6-51-g1a2669c~ds0-3 [178 kB]                                                     
Get:235 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main librhythmbox-core8 amd64 3.0.3-1+b1 [834 kB]                                                       
Get:236 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libdbus-glib-1-2 amd64 0.102-1 [201 kB]                                                            
Get:237 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libnl-route-3-200 amd64 3.2.24-2 [121 kB]                                                          
Get:238 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libnl-genl-3-200 amd64 3.2.24-2 [20.1 kB]                                                          
Get:239 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libsystemd-daemon0 amd64 208-8 [25.9 kB]                                                           
Get:240 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main systemd-sysv amd64 208-8 [26.2 kB]                                                                 
Get:241 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main rhythmbox-plugins amd64 3.0.3-1+b1 [710 kB]                                                        
Get:242 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpam-systemd amd64 208-8 [40.5 kB]                                                               
Get:243 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main policykit-1 amd64 0.105-6.1 [58.5 kB]                                                              
Get:244 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main nautilus-sendto amd64 3.8.1-1+b1 [86.4 kB]                                                         
Get:245 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main nautilus amd64 3.12.2-1 [3,018 kB]                                                                 
Get:246 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gvfs-backends amd64 1.20.2-1 [503 kB]                                                              
Get:247 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-contacts amd64 3.12.0-1+b2 [436 kB]                                                          
Get:248 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main eog amd64 3.12.2-1 [3,318 kB]                                                                      
Get:249 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main aptdaemon all 1.1.1-3 [362 kB]                                                                     
Get:250 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-bluetooth amd64 3.12.0-5 [979 kB]                                                            
Get:251 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libglib2.0-0 amd64 2.40.0-4 [2,422 kB]                                                             
Get:252 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main network-manager-gnome amd64 0.9.10.0-2 [983 kB]                                                    
Get:253 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gvfs-libs amd64 1.20.2-1 [309 kB]                                                                  
Get:254 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gvfs-daemons amd64 1.20.2-1 [328 kB]                                                               
Get:255 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main empathy amd64 3.12.4-2 [1,543 kB]                                                                  
Get:256 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libnm-gtk-common all 0.9.10.0-2 [58.9 kB]                                                          
Get:257 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main accountsservice amd64 0.6.37-3 [71.2 kB]                                                           
Get:258 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libarchive13 amd64 3.1.2-9 [269 kB]                                                                
Get:259 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libtotem-plparser18 amd64 3.10.2-3 [190 kB]                                                        
Get:260 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgstreamer1.0-0 amd64 1.4.0-1 [1,652 kB]                                                         
Get:261 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-online-accounts amd64 3.12.4-1 [311 kB]                                                      
Get:262 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgoa-1.0-common all 3.12.4-1 [275 kB]                                                            
Get:263 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgoa-backend-1.0-1 amd64 3.12.4-1 [210 kB]                                                       
Get:264 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libebook-contacts-1.2-0 amd64 3.12.2-1 [161 kB]                                                    
Get:265 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgee-0.8-2 amd64 0.14.0-1 [220 kB]                                                               
Get:266 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libzeitgeist-2.0-0 amd64 0.9.14-2.2 [119 kB]                                                       
Get:267 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main folks-common all 0.9.8-1 [429 kB]                                                                  
Get:268 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main liborc-0.4-0 amd64 1:0.4.21-1 [141 kB]                                                             
Get:269 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libfolks25 amd64 0.9.8-1 [485 kB]                                                                  
Get:270 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgstreamer-plugins-base1.0-0 amd64 1.4.0-1 [1,293 kB]                                            
Get:271 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmx-common all 1.4.7-1 [89.7 kB]                                                                 
Get:272 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmx-1.0-2 amd64 1.4.7-1+b1 [216 kB]                                                              
Get:273 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-mutter-3.0 amd64 3.12.2-2 [248 kB]                                                          
Get:274 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libclutter-imcontext-0.1-0 amd64 0.1.4-3+b2 [14.0 kB]                                              
Get:275 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-sushi amd64 3.12.0-2 [67.4 kB]                                                               
Get:276 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libclutter-gst-1.0-0 amd64 1.6.0-2+b2 [41.7 kB]                                                    
Get:277 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-cogl-1.0 amd64 1.18.2-1 [56.7 kB]                                                           
Get:278 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcogl20 amd64 1.18.2-1 [264 kB]                                                                  
Get:279 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcogl-pango20 amd64 1.18.2-1 [39.4 kB]                                                           
Get:280 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libass5 amd64 0.10.2-3 [59.9 kB]                                                                   
Get:281 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libavutil53 amd64 6:10.4-1 [119 kB]                                                                
Get:282 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopus0 amd64 1.1-1 [155 kB]                                                                      
Get:283 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main usbmuxd amd64 1.0.8-5 [31.7 kB]                                                                    
Get:284 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libchromaprint0 amd64 1.1-1+b1 [34.5 kB]                                                           
Get:285 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libwebkitgtk-3.0-0 amd64 2.4.4-2 [6,783 kB]                                                        
Get:286 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libfluidsynth1 amd64 1.1.6-2 [227 kB]                                                              
Get:287 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgstreamer-plugins-bad1.0-0 amd64 1.4.0-1 [1,312 kB]                                             
Get:288 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmpeg2encpp-2.1-0 amd64 1:2.1.0+debian-2.1 [76.1 kB]                                             
Get:289 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmpg123-0 amd64 1.20.1-1 [132 kB]                                                                
Get:290 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libavformat55 amd64 6:10.4-1 [560 kB]                                                              
Get:291 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libswscale2 amd64 6:10.4-1 [133 kB]                                                                
Get:292 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopencv-features2d2.4 amd64 2.4.9+dfsg-1 [233 kB]                                                
Get:293 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopencv-ml2.4 amd64 2.4.9+dfsg-1 [196 kB]                                                        
Get:294 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopencv-legacy2.4 amd64 2.4.9+dfsg-1 [418 kB]                                                    
Get:295 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libsoundtouch0 amd64 1.8.0-1 [41.4 kB]                                                             
Get:296 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gstreamer1.0-plugins-bad amd64 1.4.0-1 [2,342 kB]                                                  
Get:297 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gstreamer1.0-nice amd64 0.1.7-1 [22.6 kB]                                                          
Get:298 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libfarstream-0.2-2 amd64 0.2.3-3 [376 kB]                                                          
Get:299 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main telepathy-mission-control-5 amd64 1:5.16.2-1 [306 kB]                                              
Get:300 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main geoclue-2.0 amd64 2.1.8-1 [57.6 kB]                                                                
Get:301 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgoa-1.0-0b amd64 3.12.4-1 [63.7 kB]                                                             
Get:302 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgd3 amd64 2.1.0-4 [146 kB]                                                                      
Get:303 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libudisks2-0 amd64 2.1.3-3 [95.9 kB]                                                               
Get:304 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gstreamer1.0-x amd64 1.4.0-1 [827 kB]                                                              
Get:305 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gstreamer-1.0 amd64 1.4.0-1 [883 kB]                                                        
Get:306 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gst-plugins-base-1.0 amd64 1.4.0-1 [817 kB]                                                 
Get:307 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gtk-3.0 amd64 3.12.2-3 [222 kB]                                                             
Get:308 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-secret-1 amd64 0.18-1 [9,894 B]                                                             
Get:309 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libapt-inst1.5 amd64 1.0.6 [166 kB]                                                                
Get:310 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali/main python3-defer all 1.0.6-2 [11.2 kB]                                                                    
Get:311 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3-dbus amd64 1.2.0-2+b3 [189 kB]                                                             
Get:312 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3-gi amd64 3.12.1-1+b1 [438 kB]                                                              
Get:313 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3-aptdaemon all 1.1.1-3 [137 kB]                                                             
Get:314 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3-mako all 1.0.0-1 [59.6 kB]                                                                 
Get:315 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gdesktopenums-3.0 amd64 3.12.2-1 [10.1 kB]                                                  
Get:316 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libupower-glib2 amd64 0.99.0-3 [46.1 kB]                                                           
Get:317 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main mutter-common all 3.12.2-2 [775 kB]                                                                
Get:318 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmtp-runtime amd64 1.1.6-51-g1a2669c~ds0-3 [45.6 kB]                                             
Get:319 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmutter0d amd64 3.12.2-2 [543 kB]                                                                
Get:320 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python-aptdaemon all 1.1.1-3 [136 kB]                                                              
Get:321 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python-gi-cairo amd64 3.12.1-1+b1 [290 kB]                                                         
Get:322 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gjs amd64 1.40.1-2 [14.7 kB]                                                                       
Get:323 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgjs0e amd64 1.40.1-2 [155 kB]                                                                   
Get:324 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python-gi amd64 3.12.1-1+b1 [475 kB]                                                               
Get:325 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3-cairo amd64 1.10.0+dfsg-4+b1 [29.0 kB]                                                     
Get:326 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3-gi-cairo amd64 3.12.1-1+b1 [291 kB]                                                        
Get:327 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-clutter-gst-2.0 amd64 2.0.12-1 [11.4 kB]                                                    
Get:328 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gvfs-bin amd64 1.20.2-1 [252 kB]                                                                   
Get:329 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gstreamer1.0-clutter amd64 2.0.12-1 [27.5 kB]                                                      
Get:330 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcheese-gtk23 amd64 3.12.2-1 [256 kB]                                                            
Get:331 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgnome-bluetooth13 amd64 3.12.0-5 [304 kB]                                                       
Get:332 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libwacom2 amd64 0.8-1 [15.9 kB]                                                                    
Get:333 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gvfs-common all 1.20.2-1 [704 kB]                                                                  
Get:334 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main colord amd64 1.2.1-1 [296 kB]                                                                      
Get:335 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main bluez amd64 5.21-3 [695 kB]                                                                        
Get:336 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libical1 amd64 1.0-1 [183 kB]                                                                      
Get:337 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gvfs amd64 1.20.2-1 [308 kB]                                                                       
Get:338 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libedata-cal-1.2-23 amd64 3.12.2-1 [179 kB]                                                        
Get:339 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgweather-common all 3.12.2-1 [2,598 kB]                                                         
Get:340 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main rhythmbox amd64 3.0.3-1+b1 [460 kB]                                                                
Get:341 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main rhythmbox-data all 3.0.3-1 [4,284 kB]                                                              
Get:342 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main evolution-data-server-common all 3.12.2-1 [1,164 kB]                                               
Get:343 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-panel-data all 3.8.0-3 [1,330 kB]                                                            
Get:344 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gsettings-desktop-schemas all 3.12.2-1 [376 kB]                                                    
Get:345 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcairo-gobject2 amd64 1.12.16-2 [539 kB]                                                         
Get:346 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcairo-script-interpreter2 amd64 1.12.16-2 [575 kB]                                              
Get:347 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libdrm-dev amd64 2.4.56-1 [178 kB]                                                                 
Get:348 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-randr0 amd64 1.10-3 [20.1 kB]                                                               
Get:349 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-shape0-dev amd64 1.10-3 [12.7 kB]                                                           
Get:350 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-xfixes0-dev amd64 1.10-3 [17.4 kB]                                                          
Get:351 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-sync-dev amd64 1.10-3 [16.1 kB]                                                             
Get:352 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main x11proto-gl-dev all 1.4.17-1 [28.0 kB]                                                             
Get:353 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libegl1-mesa-dev amd64 10.2.5-1 [49.4 kB]                                                          
Get:354 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcairo2 amd64 1.12.16-2 [987 kB]                                                                 
Get:355 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libfolks-eds25 amd64 0.9.8-1 [371 kB]                                                              
Get:356 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main evolution-data-server amd64 3.12.2-1 [538 kB]                                                      
Get:357 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgnomekbd-common all 3.6.0-1 [78.7 kB]                                                           
Get:358 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgnomekbd8 amd64 3.6.0-1 [46.6 kB]                                                               
Get:359 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-session all 3.12.1-3 [153 kB]                                                                
Get:360 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-session-fallback all 3.8.0-3 [227 kB]                                                        
Get:361 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libtelepathy-glib0 amd64 0.24.0-1 [765 kB]                                                         
Get:362 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-session-bin amd64 3.12.1-3 [223 kB]                                                          
Get:363 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgdm1 amd64 3.12.2-2.1 [88.6 kB]                                                                 
Get:364 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-caribou-1.0 amd64 0.4.13-1 [12.3 kB]                                                        
Get:365 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcaribou0 amd64 0.4.13-1 [45.3 kB]                                                               
Get:366 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gnomedesktop-3.0 amd64 3.12.2-2 [150 kB]                                                    
Get:367 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-ibus-1.0 amd64 1.5.8-2 [257 kB]                                                             
Get:368 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-nmgtk-1.0 amd64 0.9.10.0-2 [60.5 kB]                                                        
Get:369 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-telepathylogger-0.2 amd64 0.8.0-3 [79.4 kB]                                                 
Get:370 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpackagekit-glib2-16 amd64 0.8.17-4 [112 kB]                                                     
Get:371 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libsystemd-id128-0 amd64 208-8 [30.2 kB]                                                           
Get:372 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libebackend-1.2-7 amd64 3.12.2-1 [232 kB]                                                          
Get:373 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main dconf-tools all 0.20.0-2 [16.3 kB]                                                                 
Get:374 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main dconf-editor amd64 0.20.0-2 [170 kB]                                                               
Get:375 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3-packagekit all 0.8.17-4 [27.5 kB]                                                          
Get:376 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libedata-book-1.2-20 amd64 3.12.2-1 [228 kB]                                                       
Get:377 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-packagekit amd64 3.12.2-1 [396 kB]                                                           
Get:378 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-packagekit-session amd64 3.12.2-1 [340 kB]                                                   
Get:379 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libebook-1.2-14 amd64 3.12.2-1 [168 kB]                                                            
Get:380 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libfolks-telepathy25 amd64 0.9.8-1 [372 kB]                                                        
Get:381 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main i965-va-driver amd64 1.3.2-1 [214 kB]                                                              
Get:382 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmbim-glib0 amd64 1.8.0-1 [51.5 kB]                                                              
Get:383 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmrm4 amd64 2.3.4-5 [75.3 kB]                                                                    
Get:384 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libwayland-egl1-mesa amd64 10.2.5-1 [38.8 kB]                                                      
Get:385 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libqmi-glib1 amd64 1.10.2-1 [335 kB]                                                               
Get:386 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libuil4 amd64 2.3.4-5 [146 kB]                                                                     
Get:387 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcluttergesture-0.0.2-0 amd64 0.0.2.1-7+b2 [22.3 kB]                                             
Get:388 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libvdpau1 amd64 0.7-2 [31.9 kB]                                                                    
Get:389 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gtk2-engines-pixbuf amd64 2.24.24-1 [540 kB]                                                       
Get:390 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libclutter-imcontext-0.1-bin amd64 0.1.4-3+b2 [7,688 B]                                            
Get:391 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libclutter-gtk-1.0-0 amd64 1.5.2-2 [26.1 kB]                                                       
Get:392 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-coglpango-1.0 amd64 1.18.2-1 [29.4 kB]                                                      
Get:393 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main modemmanager amd64 1.2.0-1 [531 kB]                                                                
Get:394 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libchamplain-0.12-0 amd64 0.12.8-1 [221 kB]                                                        
Get:395 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-clutter-1.0 amd64 1.18.4-1 [233 kB]                                                         
Get:396 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libclutter-1.0-0 amd64 1.18.4-1 [568 kB]                                                           
Get:397 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcogl-path20 amd64 1.18.2-1 [55.7 kB]                                                            
Get:398 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gstreamer1.0-plugins-base amd64 1.4.0-1 [1,278 kB]                                                 
Get:399 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libflac8 amd64 1.3.0-2 [86.6 kB]                                                                   
Get:400 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libvpx1 amd64 1.3.0-2.1 [596 kB]                                                                   
Get:401 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gstreamer1.0-plugins-good amd64 1.4.0-1 [2,354 kB]                                                 
Get:402 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libva1 amd64 1.3.1-3 [42.7 kB]                                                                     
Get:403 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libx264-142 amd64 2:0.142.2431+gita5831aa-1 [586 kB]                                               
Get:404 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libavcodec55 amd64 6:10.4-1 [2,844 kB]                                                             
Get:405 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmjpegutils-2.1-0 amd64 1:2.1.0+debian-2.1 [27.0 kB]                                             
Get:406 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmplex2-2.1-0 amd64 1:2.1.0+debian-2.1 [49.0 kB]                                                 
Get:407 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libtbb2 amd64 4.2~20140122-1.1 [119 kB]                                                            
Get:408 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopencv-core2.4 amd64 2.4.9+dfsg-1 [709 kB]                                                      
Get:409 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopencv-flann2.4 amd64 2.4.9+dfsg-1 [124 kB]                                                     
Get:410 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main librtmp1 amd64 2.4+20131018.git79459a2-4 [59.4 kB]                                                 
Get:411 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgtkglext1 amd64 1.2.0-3.2 [89.1 kB]                                                             
Get:412 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopencv-imgproc2.4 amd64 2.4.9+dfsg-1 [647 kB]                                                   
Get:413 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopencv-highgui2.4 amd64 2.4.9+dfsg-1 [114 kB]                                                   
Get:414 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopencv-calib3d2.4 amd64 2.4.9+dfsg-1 [228 kB]                                                   
Get:415 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopencv-objdetect2.4 amd64 2.4.9+dfsg-1 [206 kB]                                                 
Get:416 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopencv-video2.4 amd64 2.4.9+dfsg-1 [126 kB]                                                     
Get:417 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopencv-contrib2.4 amd64 2.4.9+dfsg-1 [311 kB]                                                   
Get:418 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libsbc1 amd64 1.2-3 [32.0 kB]                                                                      
Get:419 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libsrtp0 amd64 1.4.5~20130609~dfsg-1 [72.9 kB]                                                     
Get:420 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgeocode-glib0 amd64 3.12.2-1 [64.9 kB]                                                          
Get:421 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmission-control-plugins0 amd64 1:5.16.2-1 [165 kB]                                              
Get:422 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libtelepathy-farstream3 amd64 0.6.1-1 [189 kB]                                                     
Get:423 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libtelepathy-logger3 amd64 0.8.0-3 [140 kB]                                                        
Get:424 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main empathy-common all 3.12.4-2 [3,926 kB]                                                             
Get:425 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gstreamer1.0-pulseaudio amd64 1.4.0-1 [957 kB]                                                     
Get:426 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgphoto2-port10 amd64 2.5.4-1 [145 kB]                                                           
Get:427 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgphoto2-6 amd64 2.5.4-1 [817 kB]                                                                
Get:428 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main udisks2 amd64 2.1.3-3 [262 kB]                                                                     
Get:429 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-rb-3.0 amd64 3.0.3-1+b1 [444 kB]                                                            
Get:430 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libapt-pkg4.12 amd64 1.0.6 [767 kB]                                                                
Get:431 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3-apt amd64 0.9.3.8 [166 kB]                                                                 
Get:432 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3-pkg-resources all 5.5.1-1 [34.2 kB]                                                        
Get:433 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main python3-markupsafe amd64 0.23-1+b1 [16.4 kB]                                                       
Get:434 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libmozjs-24-0 amd64 24.2.0-2 [1,663 kB]                                                            
Get:435 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gtksource-3.0 amd64 3.12.2-1 [30.6 kB]                                                      
Get:436 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gedit amd64 3.12.1-1+b1 [413 kB]                                                                   
Get:437 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gedit-common all 3.12.1-1 [1,552 kB]                                                               
Get:438 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgtksourceview-3.0-common all 3.12.2-1 [606 kB]                                                  
Get:439 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgtksourceview-3.0-1 amd64 3.12.2-1 [180 kB]                                                     
Get:440 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libinput0 amd64 0.2.0-2 [23.4 kB]                                                                  
Get:441 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libclutter-gst-2.0-0 amd64 2.0.12-1 [37.2 kB]                                                      
Get:442 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main cheese-common all 3.12.2-1 [1,253 kB]                                                              
Get:443 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcheese7 amd64 3.12.2-1 [262 kB]                                                                 
Get:444 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcolord-gtk1 amd64 0.1.25-1.1+b1 [17.2 kB]                                                       
Get:445 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libibus-1.0-5 amd64 1.5.8-2 [305 kB]                                                               
Get:446 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcrack2 amd64 2.9.1-1+b2 [53.4 kB]                                                               
Get:447 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpwquality-common all 1.2.3-1 [5,454 B]                                                          
Get:448 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libpwquality1 amd64 1.2.3-1 [11.7 kB]                                                              
Get:449 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libwacom-common all 0.8-1 [19.6 kB]                                                                
Get:450 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcolorhug2 amd64 1.2.1-1 [153 kB]                                                                
Get:451 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main colord-data all 1.2.1-1 [1,213 kB]                                                                 
Get:452 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgdata19 amd64 0.15.2-1 [427 kB]                                                                 
Get:453 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgweather-3-6 amd64 3.12.2-1 [64.4 kB]                                                           
Get:454 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libedataserver-1.2-18 amd64 3.12.2-1 [306 kB]                                                      
Get:455 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libecal-1.2-16 amd64 3.12.2-1 [211 kB]                                                             
Get:456 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-desktop3-data all 3.12.2-2 [520 kB]                                                          
Get:457 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgnome-desktop-3-10 amd64 3.12.2-2 [233 kB]                                                      
Get:458 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libtracker-sparql-1.0-0 amd64 1.0.2-1+b1 [589 kB]                                                  
Get:459 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main nautilus-data all 3.12.2-1 [4,178 kB]                                                              
Get:460 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcairo2-dev amd64 1.12.16-2 [1,131 kB]                                                           
Get:461 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main mesa-common-dev amd64 10.2.5-1 [301 kB]                                                            
Get:462 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libx11-xcb-dev amd64 2:1.6.2-3 [165 kB]                                                            
Get:463 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-dri3-dev amd64 1.10-3 [11.4 kB]                                                             
Get:464 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-randr0-dev amd64 1.10-3 [26.1 kB]                                                           
Get:465 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-present-dev amd64 1.10-3 [12.5 kB]                                                          
Get:466 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxshmfence-dev amd64 1.1-2 [5,854 B]                                                             
Get:467 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-dri2-0-dev amd64 1.10-3 [14.5 kB]                                                           
Get:468 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxcb-glx0-dev amd64 1.10-3 [36.4 kB]                                                             
Get:469 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali/main x11proto-xf86vidmode-dev all 2.3.1-2 [6,114 B]                                                         
Get:470 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libxxf86vm-dev amd64 1:1.1.3-1 [23.5 kB]                                                           
Get:471 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main x11proto-dri2-dev all 2.8-2 [18.2 kB]                                                              
Get:472 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libgl1-mesa-dev amd64 10.2.5-1 [37.4 kB]                                                           
Get:473 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libopenvg1-mesa amd64 10.2.5-1 [44.0 kB]                                                           
Get:474 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libegl1-mesa-drivers amd64 10.2.5-1 [2,463 kB]                                                     
Get:475 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libwayland-dev amd64 1.5.0-1 [107 kB]                                                              
Get:476 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-session-common all 3.12.1-3 [269 kB]                                                         
Get:477 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-session-flashback all 3.8.0-3 [232 kB]                                                       
Get:478 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main upower amd64 0.99.0-3 [89.4 kB]                                                                    
Get:479 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gdm3 amd64 3.12.2-2.1 [54.1 kB]                                                             
Get:480 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-atspi-2.0 amd64 2.12.0-2 [16.6 kB]                                                          
Get:481 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libcaribou-common all 0.4.13-1 [10.1 kB]                                                           
Get:482 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gcr-3 amd64 3.12.2-1 [28.7 kB]                                                              
Get:483 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gck-1 amd64 3.12.2-1 [24.2 kB]                                                              
Get:484 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-gnomebluetooth-1.0 amd64 3.12.0-5 [240 kB]                                                  
Get:485 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-upowerglib-1.0 amd64 0.99.0-3 [15.9 kB]                                                     
Get:486 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main dconf-cli amd64 0.20.0-2 [36.9 kB]                                                                 
Get:487 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main packagekit-tools amd64 0.8.17-4 [51.0 kB]                                                          
Get:488 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main packagekit-backend-aptcc amd64 0.8.17-4 [114 kB]                                                   
Get:489 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main packagekit amd64 0.8.17-4 [460 kB]                                                                 
Get:490 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-packagekit-data all 3.12.2-1 [4,044 kB]                                                      
Get:491 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main vdpau-va-driver amd64 0.7.4-3 [43.2 kB]                                                            
Get:492 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gir1.2-notify-0.7 amd64 0.7.6-2 [19.8 kB]                                                          
Get:493 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main gnome-tweak-tool all 3.12.0-2 [139 kB]                                                             
Get:494 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main libqmi-proxy amd64 1.10.2-1 [7,180 B]                                                              
Get:495 [http://http.kali.org/kali/](http://http.kali.org/kali/) kali-dev/main va-driver-all amd64 1.3.1-3 [8,654 B]                                                              
Fetched 238 MB in 3min 13s (1,230 kB/s)                                                                                                             
Reading changelogs... Done
apt-listchanges: Mailing root: apt-listchanges: news for kali
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 335471 files and directories currently installed.)
Removing intel-linux-graphics-installer ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
(Reading database ... 335458 files and directories currently installed.)
Preparing to replace xserver-common 2:1.12.4-6+deb7u2 (using .../xserver-common_2%3a1.16.0-1_all.deb) ...
Unpacking replacement xserver-common ...
Preparing to replace xvfb 2:1.12.4-6+deb7u2 (using .../xvfb_2%3a1.16.0-1_amd64.deb) ...
Unpacking replacement xvfb ...
Preparing to replace xserver-xorg-video-all 1:7.7+3~deb7u1 (using .../xserver-xorg-video-all_1%3a7.7+7_amd64.deb) ...
Unpacking replacement xserver-xorg-video-all ...
Processing triggers for man-db ...
(Reading database ... 335459 files and directories currently installed.)
Removing xserver-xorg-video-voodoo ...
Processing triggers for man-db ...
(Reading database ... 335451 files and directories currently installed.)
Preparing to replace xserver-xorg-video-vmware 1:12.0.2-1+kali1 (using .../xserver-xorg-video-vmware_1%3a13.0.2-3+b1_amd64.deb) ...
Unpacking replacement xserver-xorg-video-vmware ...
Preparing to replace xserver-xorg-video-vesa 1:2.3.1-1+b1 (using .../xserver-xorg-video-vesa_1%3a2.3.3-1+b3_amd64.deb) ...
Unpacking replacement xserver-xorg-video-vesa ...
Processing triggers for man-db ...
(Reading database ... 335453 files and directories currently installed.)
Removing xserver-xorg-video-tseng ...
Processing triggers for man-db ...
(Reading database ... 335445 files and directories currently installed.)
Preparing to replace xserver-xorg-video-trident 1:1.3.5-1 (using .../xserver-xorg-video-trident_1%3a1.3.6-2+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-trident ...
Preparing to replace xserver-xorg-video-tdfx 1:1.4.4-1 (using .../xserver-xorg-video-tdfx_1%3a1.4.5-1+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-tdfx ...
Preparing to replace xserver-xorg-video-sisusb 1:0.9.4-3 (using .../xserver-xorg-video-sisusb_1%3a0.9.6-2+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-sisusb ...
Processing triggers for man-db ...
(Reading database ... 335448 files and directories currently installed.)
Removing xserver-xorg-video-sis ...
Processing triggers for man-db ...
(Reading database ... 335440 files and directories currently installed.)
Preparing to replace xserver-xorg-video-siliconmotion 1:1.7.6-1 (using .../xserver-xorg-video-siliconmotion_1%3a1.7.7-2+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-siliconmotion ...
Preparing to replace xserver-xorg-video-savage 1:2.3.4-1 (using .../xserver-xorg-video-savage_1%3a2.3.7-2+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-savage ...
Processing triggers for man-db ...
(Reading database ... 335442 files and directories currently installed.)
Removing xserver-xorg-video-s3virge ...
Removing xserver-xorg-video-s3 ...
Removing xserver-xorg-video-rendition ...
Processing triggers for man-db ...
(Reading database ... 335418 files and directories currently installed.)
Preparing to replace xserver-xorg-video-radeon 1:6.14.4-8 (using .../xserver-xorg-video-radeon_1%3a7.4.0-2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-radeon ...
Preparing to replace xserver-xorg-video-r128 6.8.2-1 (using .../xserver-xorg-video-r128_6.9.2-1+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-r128 ...
Preparing to replace xserver-xorg-video-openchrome 1:0.2.906-2+deb7u1 (using .../xserver-xorg-video-openchrome_1%3a0.3.3-1+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-openchrome ...
Preparing to replace xserver-xorg-video-nouveau 1:1.0.1-5 (using .../xserver-xorg-video-nouveau_1%3a1.0.10-1+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-nouveau ...
Preparing to replace xserver-xorg-video-neomagic 1:1.2.6-1 (using .../xserver-xorg-video-neomagic_1%3a1.2.8-1+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-neomagic ...
Preparing to replace xserver-xorg-video-mga 1:1.5.0-3 (using .../xserver-xorg-video-mga_1%3a1.6.3-2+b1_amd64.deb) ...
Unpacking replacement xserver-xorg-video-mga ...
Preparing to replace xserver-xorg-video-mach64 6.9.1-2 (using .../xserver-xorg-video-mach64_6.9.4-1+b3_amd64.deb) ...
Unpacking replacement xserver-xorg-video-mach64 ...
Preparing to replace xserver-xorg-video-intel 2:2.19.0-6 (using .../xserver-xorg-video-intel_2%3a2.21.15-2+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
Processing triggers for man-db ...
(Reading database ... 335422 files and directories currently installed.)
Removing xserver-xorg-video-i128 ...
Processing triggers for man-db ...
(Reading database ... 335414 files and directories currently installed.)
Preparing to replace xserver-xorg-video-fbdev 1:0.4.2-4+b3 (using .../xserver-xorg-video-fbdev_1%3a0.4.4-1+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-fbdev ...
Preparing to replace xserver-xorg-video-cirrus 1:1.4.0-2 (using .../xserver-xorg-video-cirrus_1%3a1.5.2-2+b1_amd64.deb) ...
Unpacking replacement xserver-xorg-video-cirrus ...
Processing triggers for man-db ...
(Reading database ... 335416 files and directories currently installed.)
Removing xserver-xorg-video-chips ...
Processing triggers for man-db ...
(Reading database ... 335408 files and directories currently installed.)
Preparing to replace xserver-xorg-video-ati 1:6.14.4-8 (using .../xserver-xorg-video-ati_1%3a7.4.0-2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-ati ...
Processing triggers for man-db ...
(Reading database ... 335408 files and directories currently installed.)
Removing xserver-xorg-video-ark ...
dpkg: xserver-xorg-video-apm: dependency problems, but removing anyway as you requested:
 xserver-xorg depends on xserver-xorg-video-all | xorg-driver-video; however:
  Package xserver-xorg-video-all is not configured yet.
  Package xorg-driver-video is not installed.
  Package xserver-xorg-video-siliconmotion which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-ati which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-mach64 which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-intel which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-trident which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-mga which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-nouveau which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-neomagic which provides xorg-driver-video is not configured yet.
  Package xserver-xo
Removing xserver-xorg-video-apm ...
Processing triggers for man-db ...
(Reading database ... 335393 files and directories currently installed.)
Preparing to replace xserver-xorg-input-wacom 0.15.0+20120515-2 (using .../xserver-xorg-input-wacom_0.23.0+20131011-1+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-input-wacom ...
Preparing to replace xserver-xorg-input-vmmouse 1:12.9.0-1 (using .../xserver-xorg-input-vmmouse_1%3a13.0.0-1+b3_amd64.deb) ...
Unpacking replacement xserver-xorg-input-vmmouse ...
Preparing to replace xserver-xorg-input-synaptics 1.6.2-2 (using .../xserver-xorg-input-synaptics_1.8.0-1_amd64.deb) ...
Unpacking replacement xserver-xorg-input-synaptics ...
Preparing to replace xserver-xorg-input-mouse 1:1.7.2-3 (using .../xserver-xorg-input-mouse_1%3a1.9.0-1+b3_amd64.deb) ...
Unpacking replacement xserver-xorg-input-mouse ...
Preparing to replace xserver-xorg-input-evdev 1:2.7.0-1+b1 (using .../xserver-xorg-input-evdev_1%3a2.8.2-1+b2_amd64.deb) ...
Unpacking replacement xserver-xorg-input-evdev ...
Preparing to replace xserver-xorg-core 2:1.12.4-6+deb7u2 (using .../xserver-xorg-core_2%3a1.16.0-1_amd64.deb) ...
Unpacking replacement xserver-xorg-core ...
Preparing to replace xserver-xephyr 2:1.12.4-6+deb7u2 (using .../xserver-xephyr_2%3a1.16.0-1_amd64.deb) ...
Unpacking replacement xserver-xephyr ...
Preparing to replace gnome-screensaver 3.4.1-1kali0 (using .../gnome-screensaver_3.6.1-1+b1_amd64.deb) ...
Unpacking replacement gnome-screensaver ...
Preparing to replace gnome-shell-extensions 3.4.0-2 (using .../gnome-shell-extensions_3.12.2-1_all.deb) ...
Unpacking replacement gnome-shell-extensions ...
Preparing to replace gnome-shell-common 3.4.2-7+deb7u1 (using .../gnome-shell-common_3.12.2-3_all.deb) ...
Unpacking replacement gnome-shell-common ...
Preparing to replace gir1.2-freedesktop 1.32.1-1 (using .../gir1.2-freedesktop_1.40.0-2_amd64.deb) ...
Unpacking replacement gir1.2-freedesktop ...
Preparing to replace gir1.2-glib-2.0 1.32.1-1 (using .../gir1.2-glib-2.0_1.40.0-2_amd64.deb) ...
Unpacking replacement gir1.2-glib-2.0 ...
Preparing to replace gdm3 3.4.1-8 (using .../gdm3_3.12.2-2.1_amd64.deb) ...
Unpacking replacement gdm3 ...
Preparing to replace gnome-shell 3.4.2-7+deb7u1 (using .../gnome-shell_3.12.2-3_amd64.deb) ...
Unpacking replacement gnome-shell ...
Preparing to replace gnome-menus 3.4.2-5 (using .../gnome-menus_3.13.3-1_amd64.deb) ...
Unpacking replacement gnome-menus ...
Preparing to replace gnome-panel 3.4.2.1-4 (using .../gnome-panel_3.8.0-3+b2_amd64.deb) ...
Unpacking replacement gnome-panel ...
Preparing to replace gnome-control-center 1:3.4.3.1-2 (using .../gnome-control-center_1%3a3.12.1-4_amd64.deb) ...
Unpacking replacement gnome-control-center ...
Preparing to replace gnome-control-center-data 1:3.4.3.1-2 (using .../gnome-control-center-data_1%3a3.12.1-4_all.deb) ...
Moving obsolete conffile /etc/xdg/menus/gnomecc.menu out of the way...
Moving obsolete conffile /etc/xdg/autostart/gnome-sound-applet.desktop out of the way...
Unpacking replacement gnome-control-center-data ...
Preparing to replace gnome-settings-daemon 3.4.2+git20121218.7c1322-3+deb7u3 (using .../gnome-settings-daemon_3.12.2-1_amd64.deb) ...
Moving obsolete conffile /etc/dbus-1/system.d/org.gnome.SettingsDaemon.DateTimeMechanism.conf out of the way...
Unpacking replacement gnome-settings-daemon ...
Preparing to replace at-spi2-core 2.5.3-2 (using .../at-spi2-core_2.12.0-2_amd64.deb) ...
Unpacking replacement at-spi2-core ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
(Reading database ... 335255 files and directories currently installed.)
Removing libaudit0 ...
Selecting previously unselected package libaudit-common.
(Reading database ... 335248 files and directories currently installed.)
Unpacking libaudit-common (from .../libaudit-common_1%3a2.3.7-1_all.deb) ...
Preparing to replace libkeyutils1:amd64 1.5.5-3 (using .../libkeyutils1_1.5.9-5_amd64.deb) ...
Unpacking replacement libkeyutils1:amd64 ...
Preparing to replace libgssapi-krb5-2:amd64 1.10.1+dfsg-5+deb7u2 (using .../libgssapi-krb5-2_1.12.1+dfsg-7_amd64.deb) ...
Unpacking replacement libgssapi-krb5-2:amd64 ...
Preparing to replace libkrb5-3:amd64 1.10.1+dfsg-5+deb7u2 (using .../libkrb5-3_1.12.1+dfsg-7_amd64.deb) ...
Unpacking replacement libkrb5-3:amd64 ...
Preparing to replace libkrb5support0:amd64 1.10.1+dfsg-5+deb7u2 (using .../libkrb5support0_1.12.1+dfsg-7_amd64.deb) ...
Unpacking replacement libkrb5support0:amd64 ...
Preparing to replace nfs-common 1:1.2.6-4 (using .../nfs-common_1%3a1.2.8-9_amd64.deb) ...
Unpacking replacement nfs-common ...
Preparing to replace libtirpc1:amd64 0.2.2-5 (using .../libtirpc1_0.2.4-2.1_amd64.deb) ...
Unpacking replacement libtirpc1:amd64 ...
Preparing to replace locales 2.13-38+deb7u3 (using .../locales_2.19-9_all.deb) ...
Unpacking replacement locales ...
Processing triggers for man-db ...
dpkg: locales-all: dependency problems, but removing anyway as you requested:
 postgresql-9.1 depends on locales; however:
  Package locales is not configured yet.
  Package locales-all which provides locales is to be removed.


(Reading database ... 335298 files and directories currently installed.)
Removing locales-all ...
Generating locales (this might take a while)...
Generation complete.
(Reading database ... 329147 files and directories currently installed.)
Preparing to replace libc6:amd64 2.13-38+deb7u3 (using .../libc6_2.19-9_amd64.deb) ...
Checking for services that may need to be restarted...
Checking init scripts...
Unpacking replacement libc6:amd64 ...
Setting up libc6:amd64 (2.19-9) ...
Checking for services that may need to be restarted...
Checking init scripts...


Restarting services possibly affected by the upgrade:
  cron: restarting...done.
  atd: restarting...done.


Services restarted successfully.
(Reading database ... 329150 files and directories currently installed.)
Preparing to replace sysvinit-utils 2.88dsf-41+kali2 (using .../sysvinit-utils_2.88dsf-53.2kali2_amd64.deb) ...
Unpacking replacement sysvinit-utils ...
Selecting previously unselected package startpar.
Unpacking startpar (from .../startpar_0.59-3_amd64.deb) ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up startpar (0.59-3) ...
Installing new version of config file /etc/init/startpar-bridge.conf ...
Setting up sysvinit-utils (2.88dsf-53.2kali2) ...
(Reading database ... 329157 files and directories currently installed.)
Preparing to replace ifupdown 0.7.8 (using .../ifupdown_0.7.48.1_amd64.deb) ...
Unpacking replacement ifupdown ...
Preparing to replace initscripts 2.88dsf-41+kali2 (using .../initscripts_2.88dsf-53.2kali2_amd64.deb) ...
Removing unmodified and obsolete conffile /etc/init.d/mtab.sh ...
Unpacking replacement initscripts ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up initscripts (2.88dsf-53.2kali2) ...
Installing new version of config file /etc/init.d/bootmisc.sh ...
Installing new version of config file /etc/init.d/checkfs.sh ...
Installing new version of config file /etc/init.d/checkroot.sh ...
Installing new version of config file /etc/init.d/checkroot-bootclean.sh ...
Installing new version of config file /etc/init.d/mountall.sh ...
Installing new version of config file /etc/init.d/mountdevsubfs.sh ...
Installing new version of config file /etc/init.d/mountkernfs.sh ...
Installing new version of config file /etc/init.d/rmnologin ...
Installing new version of config file /etc/init.d/umountfs ...
Installing new version of config file /etc/network/if-up.d/mountnfs ...
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match mountkernfs.sh Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match mountkernfs.sh Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match hostname.sh Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match hostname.sh Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match mountdevsubfs.sh Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match mountdevsubfs.sh Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match checkroot.sh Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match checkroot.sh Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match checkroot-bootclean.sh Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match checkroot-bootclean.sh Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match checkfs.sh Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match checkfs.sh Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match mountall.sh Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match mountall.sh Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match mountall-bootclean.sh Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match mountall-bootclean.sh Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match mountnfs.sh Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match mountnfs.sh Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match mountnfs-bootclean.sh Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match mountnfs-bootclean.sh Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match bootmisc.sh Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match bootmisc.sh Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match urandom Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match urandom Default-Stop values (0 6)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match halt Default-Start values (none)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match halt Default-Stop values (0)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match reboot Default-Start values (none)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match reboot Default-Stop values (6)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match umountroot Default-Start values (none)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match umountroot Default-Stop values (0 6)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match umountfs Default-Start values (none)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match umountfs Default-Stop values (0 6)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match umountnfs.sh Default-Start values (none)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match umountnfs.sh Default-Stop values (0 6)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match sendsigs Default-Start values (none)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match sendsigs Default-Stop values (0 6)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match killprocs Default-Start values (1)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match killprocs Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match single Default-Start values (1)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match single Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match motd Default-Start values (1 2 3 4 5)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match motd Default-Stop values (none)
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match bootlogs Default-Start values (1 2 3 4 5)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match bootlogs Default-Stop values (none)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match rc.local Default-Stop values (none)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match rmnologin Default-Stop values (none)
(Reading database ... 329159 files and directories currently installed.)
Preparing to replace libc6-i386 2.13-38+deb7u3 (using .../libc6-i386_2.19-9_amd64.deb) ...
Unpacking replacement libc6-i386 ...
Preparing to replace libc6-dev:amd64 2.13-38+deb7u3 (using .../libc6-dev_2.19-9_amd64.deb) ...
Unpacking replacement libc6-dev:amd64 ...
Preparing to replace libc-dev-bin 2.13-38+deb7u3 (using .../libc-dev-bin_2.19-9_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Selecting previously unselected package libudev1:amd64.
Unpacking libudev1:amd64 (from .../libudev1_208-8_amd64.deb) ...
Preparing to replace dmsetup 2:1.02.74-8 (using .../dmsetup_2%3a1.02.88-1_amd64.deb) ...
Unpacking replacement dmsetup ...
Preparing to replace libdevmapper1.02.1:amd64 2:1.02.74-8 (using .../libdevmapper1.02.1_2%3a1.02.88-1_amd64.deb) ...
Unpacking replacement libdevmapper1.02.1:amd64 ...
Selecting previously unselected package libaudit1:amd64.
Unpacking libaudit1:amd64 (from .../libaudit1_1%3a2.3.7-1_amd64.deb) ...
Preparing to replace libgcrypt11:amd64 1.5.0-5+deb7u1 (using .../libgcrypt11_1.5.4-2_amd64.deb) ...
Unpacking replacement libgcrypt11:amd64 ...
Preparing to replace libdrm2:amd64 2.4.40-1~deb7u2 (using .../libdrm2_2.4.56-1_amd64.deb) ...
Unpacking replacement libdrm2:amd64 ...
Preparing to replace libgl1-mesa-glx:amd64 8.0.5-4+deb7u2 (using .../libgl1-mesa-glx_10.2.5-1_amd64.deb) ...
Unpacking replacement libgl1-mesa-glx:amd64 ...
Preparing to replace libglapi-mesa:amd64 8.0.5-4+deb7u2 (using .../libglapi-mesa_10.2.5-1_amd64.deb) ...
Unpacking replacement libglapi-mesa:amd64 ...
Preparing to replace libxcb1-dev:amd64 1.8.1-2+deb7u1 (using .../libxcb1-dev_1.10-3_amd64.deb) ...
Unpacking replacement libxcb1-dev:amd64 ...
Preparing to replace libxcb1:amd64 1.8.1-2+deb7u1 (using .../libxcb1_1.10-3_amd64.deb) ...
Unpacking replacement libxcb1:amd64 ...
Preparing to replace libx11-dev:amd64 2:1.5.0-1+deb7u1 (using .../libx11-dev_2%3a1.6.2-3_amd64.deb) ...
Unpacking replacement libx11-dev:amd64 ...
Preparing to replace libx11-6:amd64 2:1.5.0-1+deb7u1 (using .../libx11-6_2%3a1.6.2-3_amd64.deb) ...
Unpacking replacement libx11-6:amd64 ...
Preparing to replace libx11-xcb1:amd64 2:1.5.0-1+deb7u1 (using .../libx11-xcb1_2%3a1.6.2-3_amd64.deb) ...
Unpacking replacement libx11-xcb1:amd64 ...
Preparing to replace libxcb-dri2-0:amd64 1.8.1-2+deb7u1 (using .../libxcb-dri2-0_1.10-3_amd64.deb) ...
Unpacking replacement libxcb-dri2-0:amd64 ...
Selecting previously unselected package libxcb-dri3-0:amd64.
Unpacking libxcb-dri3-0:amd64 (from .../libxcb-dri3-0_1.10-3_amd64.deb) ...
Preparing to replace libxcb-glx0:amd64 1.8.1-2+deb7u1 (using .../libxcb-glx0_1.10-3_amd64.deb) ...
Unpacking replacement libxcb-glx0:amd64 ...
Selecting previously unselected package libxcb-present0:amd64.
Unpacking libxcb-present0:amd64 (from .../libxcb-present0_1.10-3_amd64.deb) ...
Selecting previously unselected package libxcb-sync1:amd64.
Unpacking libxcb-sync1:amd64 (from .../libxcb-sync1_1.10-3_amd64.deb) ...
Selecting previously unselected package libxshmfence1:amd64.
Unpacking libxshmfence1:amd64 (from .../libxshmfence1_1.1-2_amd64.deb) ...
Preparing to replace libxxf86vm1:amd64 1:1.1.2-1+deb7u1 (using .../libxxf86vm1_1%3a1.1.3-1_amd64.deb) ...
Unpacking replacement libxxf86vm1:amd64 ...
Preparing to replace libpixman-1-dev 0.26.0-4+deb7u1 (using .../libpixman-1-dev_0.32.6-2_amd64.deb) ...
Unpacking replacement libpixman-1-dev ...
Preparing to replace libpixman-1-0:amd64 0.26.0-4+deb7u1 (using .../libpixman-1-0_0.32.6-2_amd64.deb) ...
Unpacking replacement libpixman-1-0:amd64 ...
Preparing to replace libdrm-radeon1:amd64 2.4.40-1~deb7u2 (using .../libdrm-radeon1_2.4.56-1_amd64.deb) ...
Unpacking replacement libdrm-radeon1:amd64 ...
Preparing to replace libdrm-intel1:amd64 2.4.40-1~deb7u2 (using .../libdrm-intel1_2.4.56-1_amd64.deb) ...
Unpacking replacement libdrm-intel1:amd64 ...
Selecting previously unselected package xserver-xorg-video-modesetting.
Unpacking xserver-xorg-video-modesetting (from .../xserver-xorg-video-modesetting_0.9.0-1+b1_amd64.deb) ...
Selecting previously unselected package libdrm-nouveau2:amd64.
Unpacking libdrm-nouveau2:amd64 (from .../libdrm-nouveau2_2.4.56-1_amd64.deb) ...
Selecting previously unselected package libffi6:amd64.
Unpacking libffi6:amd64 (from .../libffi6_3.1-2_amd64.deb) ...
Selecting previously unselected package gcc-4.9-base:amd64.
Unpacking gcc-4.9-base:amd64 (from .../gcc-4.9-base_4.9.1-4_amd64.deb) ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up gcc-4.9-base:amd64 (4.9.1-4) ...
(Reading database ... 329237 files and directories currently installed.)
Preparing to replace libstdc++6:amd64 4.7.2-5 (using .../libstdc++6_4.9.1-4_amd64.deb) ...
Unpacking replacement libstdc++6:amd64 ...
Setting up libstdc++6:amd64 (4.9.1-4) ...
Selecting previously unselected package libllvm3.4:amd64.
(Reading database ... 329248 files and directories currently installed.)
Unpacking libllvm3.4:amd64 (from .../libllvm3.4_1%3a3.4.2-8_amd64.deb) ...
Selecting previously unselected package libxatracker2:amd64.
Unpacking libxatracker2:amd64 (from .../libxatracker2_10.2.5-1_amd64.deb) ...
Preparing to replace libxi-dev 2:1.6.1-1+deb7u1 (using .../libxi-dev_2%3a1.7.4-1_amd64.deb) ...
Unpacking replacement libxi-dev ...
Preparing to replace libxi6:amd64 2:1.6.1-1+deb7u1 (using .../libxi6_2%3a1.7.4-1_amd64.deb) ...
Unpacking replacement libxi6:amd64 ...
Selecting previously unselected package libevdev2.
Unpacking libevdev2 (from .../libevdev2_1.2.2+dfsg-1_amd64.deb) ...
Selecting previously unselected package libwayland-client0:amd64.
Unpacking libwayland-client0:amd64 (from .../libwayland-client0_1.5.0-1_amd64.deb) ...
Selecting previously unselected package libwayland-server0:amd64.
Unpacking libwayland-server0:amd64 (from .../libwayland-server0_1.5.0-1_amd64.deb) ...
Selecting previously unselected package libgbm1:amd64.
Unpacking libgbm1:amd64 (from .../libgbm1_10.2.5-1_amd64.deb) ...
Preparing to replace libxcb-shape0:amd64 1.8.1-2+deb7u1 (using .../libxcb-shape0_1.10-3_amd64.deb) ...
Unpacking replacement libxcb-shape0:amd64 ...
Preparing to replace libxcb-xfixes0:amd64 1.8.1-2+deb7u1 (using .../libxcb-xfixes0_1.10-3_amd64.deb) ...
Unpacking replacement libxcb-xfixes0:amd64 ...
Selecting previously unselected package libegl1-mesa:amd64.
Unpacking libegl1-mesa:amd64 (from .../libegl1-mesa_10.2.5-1_amd64.deb) ...
Selecting previously unselected package libepoxy0.
Unpacking libepoxy0 (from .../libepoxy0_1.2-1_amd64.deb) ...
Selecting previously unselected package libxcb-icccm4:amd64.
Unpacking libxcb-icccm4:amd64 (from .../libxcb-icccm4_0.4.1-1_amd64.deb) ...
Selecting previously unselected package libxcb-image0:amd64.
Unpacking libxcb-image0:amd64 (from .../libxcb-image0_0.3.9-1_amd64.deb) ...
Selecting previously unselected package libxcb-xf86dri0:amd64.
Unpacking libxcb-xf86dri0:amd64 (from .../libxcb-xf86dri0_1.10-3_amd64.deb) ...
Selecting previously unselected package libproxy1:amd64.
Unpacking libproxy1:amd64 (from .../libproxy1_0.4.11-4_amd64.deb) ...
Preparing to replace glib-networking:amd64 2.32.3-1 (using .../glib-networking_2.40.1-2_amd64.deb) ...
Unpacking replacement glib-networking:amd64 ...
Preparing to replace glib-networking-services 2.32.3-1 (using .../glib-networking-services_2.40.1-2_amd64.deb) ...
Unpacking replacement glib-networking-services ...
Preparing to replace glib-networking-common 2.32.3-1 (using .../glib-networking-common_2.40.1-2_all.deb) ...
Unpacking replacement glib-networking-common ...
Preparing to replace libgmp10:amd64 2:5.0.5+dfsg-2 (using .../libgmp10_2%3a6.0.0+dfsg-6_amd64.deb) ...
Unpacking replacement libgmp10:amd64 ...
Preparing to replace libnettle4:amd64 2.4-3 (using .../libnettle4_2.7.1-3_amd64.deb) ...
Unpacking replacement libnettle4:amd64 ...
Selecting previously unselected package libhogweed2:amd64.
Unpacking libhogweed2:amd64 (from .../libhogweed2_2.7.1-3_amd64.deb) ...
Preparing to replace libp11-kit0:amd64 0.12-3 (using .../libp11-kit0_0.20.3-2_amd64.deb) ...
Unpacking replacement libp11-kit0:amd64 ...
Selecting previously unselected package libtasn1-6:amd64.
Unpacking libtasn1-6:amd64 (from .../libtasn1-6_4.0-2_amd64.deb) ...
Selecting previously unselected package libgnutls-deb0-28:amd64.
Unpacking libgnutls-deb0-28:amd64 (from .../libgnutls-deb0-28_3.2.16-1_amd64.deb) ...
Preparing to replace libgirepository-1.0-1 1.32.1-1 (using .../libgirepository-1.0-1_1.40.0-2_amd64.deb) ...
Unpacking replacement libgirepository-1.0-1 ...
Preparing to replace libatk1.0-dev 2.4.0-2 (using .../libatk1.0-dev_2.12.0-1_amd64.deb) ...
Unpacking replacement libatk1.0-dev ...
Preparing to replace gir1.2-atk-1.0 2.4.0-2 (using .../gir1.2-atk-1.0_2.12.0-1_amd64.deb) ...
Unpacking replacement gir1.2-atk-1.0 ...
Preparing to replace libpython2.7 2.7.3-6+deb7u2 (using .../libpython2.7_2.7.8-5_amd64.deb) ...
Unpacking replacement libpython2.7:amd64 ...
Preparing to replace python2.7 2.7.3-6+deb7u2 (using .../python2.7_2.7.8-5_amd64.deb) ...
Unpacking replacement python2.7 ...
Preparing to replace python2.7-minimal 2.7.3-6+deb7u2 (using .../python2.7-minimal_2.7.8-5_amd64.deb) ...
Unpacking replacement python2.7-minimal ...
dpkg: warning: unable to delete old directory '/etc/python2.7': Directory not empty
Selecting previously unselected package libpython2.7-minimal:amd64.
Unpacking libpython2.7-minimal:amd64 (from .../libpython2.7-minimal_2.7.8-5_amd64.deb) ...
Selecting previously unselected package libdb5.3:amd64.
Unpacking libdb5.3:amd64 (from .../libdb5.3_5.3.28-6_amd64.deb) ...
Selecting previously unselected package libpython2.7-stdlib:amd64.
Unpacking libpython2.7-stdlib:amd64 (from .../libpython2.7-stdlib_2.7.8-5_amd64.deb) ...
Preparing to replace python 2.7.3-4+deb7u1 (using .../python_2.7.8-1_amd64.deb) ...
Unpacking replacement python ...
Preparing to replace python-minimal 2.7.3-4+deb7u1 (using .../python-minimal_2.7.8-1_amd64.deb) ...
Unpacking replacement python-minimal ...
Selecting previously unselected package libpython-stdlib:amd64.
Unpacking libpython-stdlib:amd64 (from .../libpython-stdlib_2.7.8-1_amd64.deb) ...
Selecting previously unselected package libelfg0:amd64.
Unpacking libelfg0:amd64 (from .../libelfg0_0.8.13-5_amd64.deb) ...
Preparing to replace libglib2.0-dev 2.33.12+really2.32.4-5 (using .../libglib2.0-dev_2.40.0-4_amd64.deb) ...
Unpacking replacement libglib2.0-dev ...
Preparing to replace libglib2.0-bin 2.33.12+really2.32.4-5 (using .../libglib2.0-bin_2.40.0-4_amd64.deb) ...
Unpacking replacement libglib2.0-bin ...
Preparing to replace libpcre3-dev 1:8.30-5 (using .../libpcre3-dev_1%3a8.35-3_amd64.deb) ...
Unpacking replacement libpcre3-dev:amd64 ...
Preparing to replace libpcre3:amd64 1:8.30-5 (using .../libpcre3_1%3a8.35-3_amd64.deb) ...
Unpacking replacement libpcre3:amd64 ...
Preparing to replace libpcrecpp0:amd64 1:8.30-5 (using .../libpcrecpp0_1%3a8.35-3_amd64.deb) ...
Unpacking replacement libpcrecpp0:amd64 ...
Preparing to replace libatk1.0-0:amd64 2.4.0-2 (using .../libatk1.0-0_2.12.0-1_amd64.deb) ...
Unpacking replacement libatk1.0-0:amd64 ...
Preparing to replace libatk1.0-data 2.4.0-2 (using .../libatk1.0-data_2.12.0-1_all.deb) ...
Unpacking replacement libatk1.0-data ...
Preparing to replace liblcms2-2:amd64 2.2+git20110628-2.2+deb7u1 (using .../liblcms2-2_2.6-3_amd64.deb) ...
Unpacking replacement liblcms2-2:amd64 ...
Selecting previously unselected package libopenjpeg5:amd64.
Unpacking libopenjpeg5:amd64 (from .../libopenjpeg5_1.5.2-2_amd64.deb) ...
Selecting previously unselected package libtiff5:amd64.
Unpacking libtiff5:amd64 (from .../libtiff5_4.0.3-9_amd64.deb) ...
Selecting previously unselected package libpoppler46:amd64.
Unpacking libpoppler46:amd64 (from .../libpoppler46_0.26.4-1_amd64.deb) ...
Selecting previously unselected package libmotif-common.
Unpacking libmotif-common (from .../libmotif-common_2.3.4-5_all.deb) ...
Selecting previously unselected package libxm4:amd64.
Unpacking libxm4:amd64 (from .../libxm4_2.3.4-5_amd64.deb) ...
Preparing to replace xpdf 3.03-10 (using .../xpdf_3.03-17+b1_amd64.deb) ...
Unpacking replacement xpdf ...
Preparing to replace libfontconfig1-dev 2.9.0-7.1 (using .../libfontconfig1-dev_2.11.0-6_amd64.deb) ...
Unpacking replacement libfontconfig1-dev:amd64 ...
Preparing to replace libfontconfig1:amd64 2.9.0-7.1 (using .../libfontconfig1_2.11.0-6_amd64.deb) ...
Unpacking replacement libfontconfig1:amd64 ...
Preparing to replace fontconfig-config 2.9.0-7.1 (using .../fontconfig-config_2.11.0-6_all.deb) ...
Moving obsolete conffile /etc/fonts/conf.avail/10-autohint.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/10-no-sub-pixel.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/10-sub-pixel-bgr.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/10-sub-pixel-rgb.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/10-sub-pixel-vbgr.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/10-sub-pixel-vrgb.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/10-unhinted.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/11-lcdfilter-default.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/11-lcdfilter-legacy.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/11-lcdfilter-light.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/20-fix-globaladvance.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/20-unhint-small-vera.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/25-unhint-nonlatin.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/30-metric-aliases.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/30-urw-aliases.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/40-nonlatin.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/45-latin.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/49-sansserif.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/50-user.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/51-local.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/60-latin.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/65-fonts-persian.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/65-khmer.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/65-nonlatin.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/69-unifont.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/70-force-bitmaps.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/70-no-bitmaps.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/70-yes-bitmaps.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/80-delicious.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/90-synthetic.conf out of the way...
Moving obsolete conffile /etc/fonts/fonts.dtd out of the way...
Unpacking replacement fontconfig-config ...
Selecting previously unselected package libgraphite2-3:amd64.
Unpacking libgraphite2-3:amd64 (from .../libgraphite2-3_1.2.4-3_amd64.deb) ...
Selecting previously unselected package libharfbuzz0b:amd64.
Unpacking libharfbuzz0b:amd64 (from .../libharfbuzz0b_0.9.35-1_amd64.deb) ...
Preparing to replace libpango1.0-dev 1.30.0-1 (using .../libpango1.0-dev_1.36.6-1_amd64.deb) ...
Unpacking replacement libpango1.0-dev ...
Preparing to replace libpango1.0-0:amd64 1.30.0-1 (using .../libpango1.0-0_1.36.6-1_amd64.deb) ...
Unpacking replacement libpango1.0-0:amd64 ...
Selecting previously unselected package libpangoft2-1.0-0:amd64.
Unpacking libpangoft2-1.0-0:amd64 (from .../libpangoft2-1.0-0_1.36.6-1_amd64.deb) ...
Selecting previously unselected package libpangocairo-1.0-0:amd64.
Unpacking libpangocairo-1.0-0:amd64 (from .../libpangocairo-1.0-0_1.36.6-1_amd64.deb) ...
Selecting previously unselected package libpangoxft-1.0-0:amd64.
Unpacking libpangoxft-1.0-0:amd64 (from .../libpangoxft-1.0-0_1.36.6-1_amd64.deb) ...
Preparing to replace gir1.2-pango-1.0 1.30.0-1 (using .../gir1.2-pango-1.0_1.36.6-1_amd64.deb) ...
Unpacking replacement gir1.2-pango-1.0 ...
Selecting previously unselected package libicu52:amd64.
Unpacking libicu52:amd64 (from .../libicu52_52.1-5_amd64.deb) ...
Selecting previously unselected package libharfbuzz-icu0:amd64.
Unpacking libharfbuzz-icu0:amd64 (from .../libharfbuzz-icu0_0.9.35-1_amd64.deb) ...
Selecting previously unselected package libharfbuzz-gobject0:amd64.
Unpacking libharfbuzz-gobject0:amd64 (from .../libharfbuzz-gobject0_0.9.35-1_amd64.deb) ...
Selecting previously unselected package libharfbuzz-dev.
Unpacking libharfbuzz-dev (from .../libharfbuzz-dev_0.9.35-1_amd64.deb) ...
Selecting previously unselected package libpangox-1.0-0:amd64.
Unpacking libpangox-1.0-0:amd64 (from .../libpangox-1.0-0_0.0.2-4_amd64.deb) ...
Selecting previously unselected package libpango-1.0-0:amd64.
Unpacking libpango-1.0-0:amd64 (from .../libpango-1.0-0_1.36.6-1_amd64.deb) ...
Preparing to replace libxml2-dev:amd64 2.8.0+dfsg1-7+wheezy1 (using .../libxml2-dev_2.9.1+dfsg1-4_amd64.deb) ...
Unpacking replacement libxml2-dev:amd64 ...
Preparing to replace libxml2:amd64 2.8.0+dfsg1-7+wheezy1 (using .../libxml2_2.9.1+dfsg1-4_amd64.deb) ...
Unpacking replacement libxml2:amd64 ...
Preparing to replace librsvg2-common:amd64 2.36.1-2 (using .../librsvg2-common_2.40.3-1_amd64.deb) ...
Unpacking replacement librsvg2-common:amd64 ...
Preparing to replace libgdk-pixbuf2.0-dev 2.26.1-1 (using .../libgdk-pixbuf2.0-dev_2.30.7-1_amd64.deb) ...
Unpacking replacement libgdk-pixbuf2.0-dev ...
Preparing to replace libgdk-pixbuf2.0-common 2.26.1-1 (using .../libgdk-pixbuf2.0-common_2.30.7-1_all.deb) ...
Unpacking replacement libgdk-pixbuf2.0-common ...
Preparing to replace libgdk-pixbuf2.0-0:amd64 2.26.1-1 (using .../libgdk-pixbuf2.0-0_2.30.7-1_amd64.deb) ...
Unpacking replacement libgdk-pixbuf2.0-0:amd64 ...
Preparing to replace librsvg2-2:amd64 2.36.1-2 (using .../librsvg2-2_2.40.3-1_amd64.deb) ...
Unpacking replacement librsvg2-2:amd64 ...
Preparing to replace gir1.2-gdkpixbuf-2.0 2.26.1-1 (using .../gir1.2-gdkpixbuf-2.0_2.30.7-1_amd64.deb) ...
Unpacking replacement gir1.2-gdkpixbuf-2.0 ...
Preparing to replace gir1.2-gtk-2.0 2.24.10-2 (using .../gir1.2-gtk-2.0_2.24.24-1_amd64.deb) ...
Unpacking replacement gir1.2-gtk-2.0 ...
Preparing to replace libgtk2.0-dev 2.24.10-2 (using .../libgtk2.0-dev_2.24.24-1_amd64.deb) ...
Unpacking replacement libgtk2.0-dev ...
Preparing to replace libgtk2.0-bin 2.24.10-2 (using .../libgtk2.0-bin_2.24.24-1_amd64.deb) ...
Unpacking replacement libgtk2.0-bin ...
Preparing to replace libgail-common:amd64 2.24.10-2 (using .../libgail-common_2.24.24-1_amd64.deb) ...
Unpacking replacement libgail-common:amd64 ...
Preparing to replace libgail18:amd64 2.24.10-2 (using .../libgail18_2.24.24-1_amd64.deb) ...
Unpacking replacement libgail18:amd64 ...
Selecting previously unselected package libcupsfilters1:amd64.
Unpacking libcupsfilters1:amd64 (from .../libcupsfilters1_1.0.58-1_amd64.deb) ...
Preparing to replace libcupsimage2:amd64 1.5.3-5+deb7u4 (using .../libcupsimage2_1.7.5-1_amd64.deb) ...
Unpacking replacement libcupsimage2:amd64 ...
Preparing to replace cups-common 1.5.3-5+deb7u4 (using .../cups-common_1.7.5-1_all.deb) ...
Unpacking replacement cups-common ...
Preparing to replace cups-bsd 1.5.3-5+deb7u4 (using .../cups-bsd_1.7.5-1_amd64.deb) ...
Cannot find cached rlinetd's config files for service printer, ignoring disable request
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Unpacking replacement cups-bsd ...
Preparing to replace cups-client 1.5.3-5+deb7u4 (using .../cups-client_1.7.5-1_amd64.deb) ...
Unpacking replacement cups-client ...
Preparing to replace libcups2:amd64 1.5.3-5+deb7u4 (using .../libcups2_1.7.5-1_amd64.deb) ...
Unpacking replacement libcups2:amd64 ...
Preparing to replace libgtk2.0-0:amd64 2.24.10-2 (using .../libgtk2.0-0_2.24.24-1_amd64.deb) ...
Unpacking replacement libgtk2.0-0:amd64 ...
Preparing to replace libgtk-3-bin 3.4.2-7 (using .../libgtk-3-bin_3.12.2-3_amd64.deb) ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking replacement libgtk-3-bin ...
Preparing to replace gnome-themes-standard 3.4.2-2.1 (using .../gnome-themes-standard_3.12.0-1_amd64.deb) ...
Unpacking replacement gnome-themes-standard:amd64 ...
Preparing to replace libgtk-3-0:amd64 3.4.2-7 (using .../libgtk-3-0_3.12.2-3_amd64.deb) ...
Unpacking replacement libgtk-3-0:amd64 ...
Preparing to replace libgtk-3-common 3.4.2-7 (using .../libgtk-3-common_3.12.2-3_all.deb) ...
Unpacking replacement libgtk-3-common ...
Preparing to replace libgail-3-0:amd64 3.4.2-7 (using .../libgail-3-0_3.12.2-3_amd64.deb) ...
Unpacking replacement libgail-3-0:amd64 ...
Preparing to replace gnome-themes-standard-data 3.4.2-2.1 (using .../gnome-themes-standard-data_3.12.0-1_all.deb) ...
Unpacking replacement gnome-themes-standard-data ...
Selecting previously unselected package libwayland-cursor0:amd64.
Unpacking libwayland-cursor0:amd64 (from .../libwayland-cursor0_1.5.0-1_amd64.deb) ...
Selecting previously unselected package libxkbcommon0:amd64.
Unpacking libxkbcommon0:amd64 (from .../libxkbcommon0_0.4.1-2_amd64.deb) ...
Selecting previously unselected package libdconf1:amd64.
Unpacking libdconf1:amd64 (from .../libdconf1_0.20.0-2_amd64.deb) ...
Preparing to replace dconf-gsettings-backend:amd64 0.12.1-3 (using .../dconf-gsettings-backend_0.20.0-2_amd64.deb) ...
Unpacking replacement dconf-gsettings-backend:amd64 ...
Preparing to replace dconf-service 0.12.1-3 (using .../dconf-service_0.20.0-2_amd64.deb) ...
Unpacking replacement dconf-service ...
Selecting previously unselected package libcolord2:amd64.
Unpacking libcolord2:amd64 (from .../libcolord2_1.2.1-1_amd64.deb) ...
Preparing to replace libsoup2.4-dev 2.38.1-3 (using .../libsoup2.4-dev_2.46.0-2_amd64.deb) ...
Unpacking replacement libsoup2.4-dev ...
Preparing to replace gir1.2-soup-2.4 2.38.1-3 (using .../gir1.2-soup-2.4_2.46.0-2_amd64.deb) ...
Unpacking replacement gir1.2-soup-2.4 ...
Preparing to replace libsoup2.4-1:amd64 2.38.1-3 (using .../libsoup2.4-1_2.46.0-2_amd64.deb) ...
Unpacking replacement libsoup2.4-1:amd64 ...
Preparing to replace libatspi2.0-0:amd64 2.5.3-2 (using .../libatspi2.0-0_2.12.0-2_amd64.deb) ...
Unpacking replacement libatspi2.0-0:amd64 ...
Preparing to replace nautilus-open-terminal 0.19-2+b1 (using .../nautilus-open-terminal_0.20-1_amd64.deb) ...
Unpacking replacement nautilus-open-terminal ...
Selecting previously unselected package libpython3.4-minimal:amd64.
Unpacking libpython3.4-minimal:amd64 (from .../libpython3.4-minimal_3.4.1-10_amd64.deb) ...
Selecting previously unselected package python3.4-minimal.
Unpacking python3.4-minimal (from .../python3.4-minimal_3.4.1-10_amd64.deb) ...
Preparing to replace python3 3.2.3-6 (using .../python3_3.4.1-1_amd64.deb) ...
running python pre-rtupdate hooks for python3.4...
Unpacking replacement python3 ...
Preparing to replace python3-minimal 3.2.3-6 (using .../python3-minimal_3.4.1-1_amd64.deb) ...
Unpacking replacement python3-minimal ...
Selecting previously unselected package libmpdec2:amd64.
Unpacking libmpdec2:amd64 (from .../libmpdec2_2.4.0-6_amd64.deb) ...
Selecting previously unselected package libpython3.4-stdlib:amd64.
Unpacking libpython3.4-stdlib:amd64 (from .../libpython3.4-stdlib_3.4.1-10_amd64.deb) ...
Selecting previously unselected package python3.4.
Unpacking python3.4 (from .../python3.4_3.4.1-10_amd64.deb) ...
Selecting previously unselected package libpython3-stdlib:amd64.
Unpacking libpython3-stdlib:amd64 (from .../libpython3-stdlib_3.4.1-1_amd64.deb) ...
Selecting previously unselected package dh-python.
Unpacking dh-python (from .../dh-python_1.20140511-1_all.deb) ...
Selecting previously unselected package libcamel-1.2-49.
Unpacking libcamel-1.2-49 (from .../libcamel-1.2-49_3.12.2-1_amd64.deb) ...
Preparing to replace libgck-1-0 3.4.1-3 (using .../libgck-1-0_3.12.2-1_amd64.deb) ...
Unpacking replacement libgck-1-0:amd64 ...
Preparing to replace libgcr-3-1 3.4.1-3 (using .../libgcr-3-1_3.12.2-1_amd64.deb) ...
Unpacking replacement libgcr-3-1:amd64 ...
Selecting previously unselected package libgcr-ui-3-1:amd64.
Unpacking libgcr-ui-3-1:amd64 (from .../libgcr-ui-3-1_3.12.2-1_amd64.deb) ...
Selecting previously unselected package libgcr-base-3-1:amd64.
Unpacking libgcr-base-3-1:amd64 (from .../libgcr-base-3-1_3.12.2-1_amd64.deb) ...
Selecting previously unselected package libsecret-common.
Unpacking libsecret-common (from .../libsecret-common_0.18-1_all.deb) ...
Selecting previously unselected package libsecret-1-0:amd64.
Unpacking libsecret-1-0:amd64 (from .../libsecret-1-0_0.18-1_amd64.deb) ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for mime-support ...
Processing triggers for gconf2 ...


(gdbus call:24862): GLib-GObject-CRITICAL **: /tmp/buildd/glib2.0-2.33.12+really2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()


(gdbus call:24862): GLib-GObject-CRITICAL **: /tmp/buildd/glib2.0-2.33.12+really2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()


(gdbus call:24862): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed


(gdbus call:24862): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed


(gdbus call:24862): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed


(gdbus call:24862): GLib-GObject-CRITICAL **: /tmp/buildd/glib2.0-2.33.12+really2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()


(gdbus call:24862): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed


(gdbus call:24862): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed


(gdbus call:24862): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed


(gdbus call:24862): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed


(gdbus call:24862): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
**
GLib-GIO:ERROR:/tmp/buildd/glib2.0-2.33.12+really2.32.4/./gio/gdbusconnection.c:6764:get_uninitialized_connection: assertion failed: (ret != NULL)
Aborted
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
W: Operation was interrupted before it could finish
root@kali:/etc/apt# apt-get purge gnome-t
gnome-terminal              gnome-terminal-data         gnome-themes-standard       gnome-themes-standard-data  
root@kali:/etc/apt# apt-get purge gnome-t
gnome-terminal              gnome-terminal-data         gnome-themes-standard       gnome-themes-standard-data  
root@kali:/etc/apt# apt-get purge gnome-tweak-tool 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'gnome-tweak-tool' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 at-spi2-core : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 dconf-gsettings-backend : Depends: libglib2.0-0 (>= 2.39.1) but 2.33.12+really2.32.4-5 is to be installed
 dconf-service : Depends: libglib2.0-0 (>= 2.39.1) but 2.33.12+really2.32.4-5 is to be installed
 gdm3 : Depends: libgdm1 (= 3.12.2-2.1) but it is not going to be installed
        Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
        Depends: libsystemd-id128-0 (>= 38) but it is not going to be installed
        Depends: libsystemd-journal0 (>= 38) but it is not going to be installed
        Depends: libsystemd-login0 (>= 186) but 44-11+deb7u4 is to be installed
        Depends: gir1.2-gdm3 (= 3.12.2-2.1) but it is not going to be installed
        Depends: libpam-systemd but it is not going to be installed
        Depends: gnome-session-bin (>= 3.10) but 3.4.2.1-4 is to be installed
        Depends: policykit-1 (>= 0.105-5~) but 0.105-3 is to be installed
        Depends: dconf-cli (>= 0.20) but it is not going to be installed
 gir1.2-glib-2.0 : Depends: libglib2.0-0 (>= 2.39.91) but 2.33.12+really2.32.4-5 is to be installed
 glib-networking : Depends: libglib2.0-0 (>= 2.39.4) but 2.33.12+really2.32.4-5 is to be installed
 glib-networking-services : Depends: libglib2.0-0 (>= 2.39.3) but 2.33.12+really2.32.4-5 is to be installed
 gnome-control-center : Depends: libaccountsservice0 (>= 0.6.34) but 0.6.21-8 is to be installed
                        Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
                        Depends: libclutter-1.0-0 (>= 1.11.10) but 1.10.8-2 is to be installed
                        Depends: libcolord-gtk1 (>= 0.1.24) but it is not going to be installed
                        Depends: libglib2.0-0 (>= 2.39.91) but 2.33.12+really2.32.4-5 is to be installed
                        Depends: libgnome-bluetooth13 (>= 3.12.0) but it is not going to be installed
                        Depends: libgnome-desktop-3-10 (>= 3.11.90) but it is not going to be installed
                        Depends: libgoa-1.0-0b (>= 3.7.90) but it is not going to be installed
                        Depends: libgoa-backend-1.0-1 (>= 3.10.0) but it is not going to be installed
                        Depends: libgrilo-0.2-1 (>= 0.2.2) but it is not going to be installed
                        Depends: libibus-1.0-5 (>= 1.5.2) but it is not going to be installed
                        Depends: libmm-glib0 (>= 0.7.991) but it is not going to be installed
                        Depends: libnm-glib4 (>= 0.9.7.995) but 0.9.4.0-10 is to be installed
                        Depends: libnm-gtk0 (>= 0.9.7.997) but 0.9.4.1-5 is to be installed
                        Depends: libnm-util2 (>= 0.9.10.0) but 0.9.4.0-10 is to be installed
                        Depends: libpwquality1 (>= 1.1.0) but it is not going to be installed
                        Depends: libupower-glib2 (>= 0.99.0) but it is not going to be installed
                        Depends: libwacom2 (>= 0.7) but 0.6-1 is to be installed
                        Depends: colord (>= 0.1.30) but 0.1.21-1 is to be installed
                        Depends: gnome-icon-theme (>= 3.7) but 3.4.0-2 is to be installed
                        Depends: gnome-icon-theme-symbolic (>= 3.7) but 3.4.0-2 is to be installed
                        Depends: gsettings-desktop-schemas (>= 3.9.91) but 3.4.2-3 is to be installed
                        Recommends: rygel but it is not going to be installed or
                                    rygel-tracker but it is not going to be installed
                        Recommends: system-config-printer (>= 1.4) but it is not going to be installed
                        Recommends: network-manager-gnome (>= 0.9.8) but 0.9.4.1-5 is to be installed
                        Recommends: libnss-myhostname but it is not going to be installed
                        Recommends: realmd but it is not going to be installed
 gnome-panel : Depends: libecal-1.2-16 (>= 3.5.91) but it is not going to be installed
               Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not going to be installed
               Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
               Depends: libgnome-desktop-3-10 (>= 3.11.90) but it is not going to be installed
               Depends: libgweather-3-6 (>= 3.7.91) but it is not going to be installed
               Depends: libical1 (>= 1.0) but it is not going to be installed
               Depends: gnome-panel-data (= 3.8.0-3) but 3.4.2.1-4 is to be installed
               Recommends: gnome-session-flashback but it is not going to be installed
 gnome-screensaver : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
                     Depends: libgnome-desktop-3-10 (>= 3.11.90) but it is not going to be installed
                     Depends: libgnomekbd8 (>= 3.6.0) but it is not going to be installed
 gnome-settings-daemon : Depends: libgeocode-glib0 (>= 0.99.1) but 0.99.0-1 is to be installed
                         Depends: libglib2.0-0 (>= 2.37.7) but 2.33.12+really2.32.4-5 is to be installed
                         Depends: libgnome-desktop-3-10 (>= 3.11.90) but it is not going to be installed
                         Depends: libgweather-3-6 (>= 3.10.0) but it is not going to be installed
                         Depends: libibus-1.0-5 (>= 1.5.1) but it is not going to be installed
                         Depends: libpackagekit-glib2-16 (>= 0.8.10) but it is not going to be installed
                         Depends: libupower-glib2 (>= 0.99.0) but it is not going to be installed
                         Depends: libwacom2 (>= 0.7) but 0.6-1 is to be installed
                         Depends: systemd but it is not going to be installed
                         Depends: gsettings-desktop-schemas (>= 3.10.0) but 3.4.2-3 is to be installed
 gnome-shell : Depends: gir1.2-clutter-1.0 (>= 1.17) but 1.10.8-2 is to be installed
               Depends: gir1.2-gtk-3.0 (>= 3.8) but 3.4.2-7 is to be installed
               Depends: gir1.2-mutter-3.0 (>= 3.12.0) but 3.4.1-5 is to be installed
               Depends: libclutter-1.0-0 (>= 1.15.90) but 1.10.8-2 is to be installed
               Depends: libcogl-pango20 (>= 1.17.4) but it is not going to be installed
               Depends: libcogl20 (>= 1.17.4) but it is not going to be installed
               Depends: libecal-1.2-16 (>= 3.5.91) but it is not going to be installed
               Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not going to be installed
               Depends: libgjs0-libmozjs-24-0
               Depends: libgjs0e (>= 1.40.1) but it is not going to be installed
               Depends: libglib2.0-0 (>= 2.39.90) but 2.33.12+really2.32.4-5 is to be installed
               Depends: libgstreamer1.0-0 (>= 1.0.0) but it is not going to be installed
               Depends: libical1 (>= 1.0) but it is not going to be installed
               Depends: libmozjs-24-0 but it is not going to be installed
               Depends: libmutter0d but it is not going to be installed
               Depends: libsystemd-journal0 (>= 38) but it is not going to be installed
               Depends: evolution-data-server (>= 3.7.90) but 3.4.4-3 is to be installed
               Depends: gir1.2-gdm3 (>= 3.5.90) but it is not going to be installed
               Depends: gir1.2-atspi-2.0 (>= 2.9.91) but 2.5.3-2 is to be installed
               Depends: gir1.2-caribou-1.0 (>= 0.4.8) but 0.4.4-1 is to be installed
               Depends: gir1.2-gdesktopenums-3.0 (>= 3.12) but 3.4.2-3 is to be installed
               Depends: gir1.2-gcr-3 (>= 3.7.5) but 3.4.1-3 is to be installed
               Depends: gir1.2-gnomebluetooth-1.0 (>= 3.6.0) but 3.4.2-1 is to be installed
               Depends: gir1.2-gnomedesktop-3.0 (>= 3.12.0) but it is not going to be installed
               Depends: gir1.2-ibus-1.0 (>= 1.5.2) but it is not going to be installed
               Depends: gir1.2-nmgtk-1.0 (>= 0.9.8) but it is not going to be installed
               Depends: gir1.2-telepathylogger-0.2 (>= 0.8.0) but 0.4.0-1 is to be installed
               Depends: gir1.2-upowerglib-1.0 (>= 0.99) but 0.9.17-1 is to be installed
               Depends: gjs (>= 1.39.0) but 1.32.0-5 is to be installed
               Depends: gsettings-desktop-schemas (>= 3.11) but 3.4.2-3 is to be installed
 gnome-shell-extensions : Depends: gvfs (>= 1.16.0) but 1.12.3-4 is to be installed
                          Depends: gnome-session (>= 3.8) but 3.4.2.1-4 is to be installed
                          Recommends: gnome-tweak-tool (>= 3.12) but it is not going to be installed
 gnome-themes-standard : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
                         Recommends: gtk2-engines-pixbuf but it is not going to be installed
 libatk1.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 libatspi2.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 libcamel-1.2-49 : Depends: libglib2.0-0 (>= 2.36) but 2.33.12+really2.32.4-5 is to be installed
 libcolord2 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 libdconf1 : Depends: libglib2.0-0 (>= 2.39.1) but 2.33.12+really2.32.4-5 is to be installed
 libgail-3-0 : Depends: libglib2.0-0 (>= 2.39.5) but 2.33.12+really2.32.4-5 is to be installed
 libgail-common : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 libgcr-base-3-1 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 libgdk-pixbuf2.0-0 : Depends: libglib2.0-0 (>= 2.37.6) but 2.33.12+really2.32.4-5 is to be installed
 libgdk-pixbuf2.0-dev : Depends: libglib2.0-0 (>= 2.37.6) but 2.33.12+really2.32.4-5 is to be installed
 libgirepository-1.0-1 : Depends: libglib2.0-0 (>= 2.39.0) but 2.33.12+really2.32.4-5 is to be installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.40.0-4) but 2.33.12+really2.32.4-5 is to be installed
 libglib2.0-dev : Depends: libglib2.0-0 (= 2.40.0-4) but 2.33.12+really2.32.4-5 is to be installed
 libgtk-3-0 : Depends: libglib2.0-0 (>= 2.39.90) but 2.33.12+really2.32.4-5 is to be installed
 libgtk-3-bin : Depends: libglib2.0-0 (>= 2.39.5) but 2.33.12+really2.32.4-5 is to be installed
 libgtk2.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 libpango-1.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 libpango1.0-dev : Depends: libcairo2 (>= 1.12.10) but 1.12.2-3 is to be installed
                   Depends: libglib2.0-0 (>= 2.34.0) but 2.33.12+really2.32.4-5 is to be installed
                   Depends: libcairo2-dev (>= 1.12.10) but 1.12.2-3 is to be installed
 libpangocairo-1.0-0 : Depends: libcairo2 (>= 1.12.10) but 1.12.2-3 is to be installed
                       Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 libpangoft2-1.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 libpangox-1.0-0 : Depends: libglib2.0-0 (>= 2.34.0) but 2.33.12+really2.32.4-5 is to be installed
 libpangoxft-1.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 librsvg2-2 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is to be installed
 libsecret-1-0 : Depends: libglib2.0-0 (>= 2.38.0) but 2.33.12+really2.32.4-5 is to be installed
 libsoup2.4-1 : Depends: libglib2.0-0 (>= 2.39.90) but 2.33.12+really2.32.4-5 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@kali:/etc/apt# apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 at-spi2-core : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 dconf-gsettings-backend : Depends: libglib2.0-0 (>= 2.39.1) but 2.33.12+really2.32.4-5 is installed
 dconf-service : Depends: libglib2.0-0 (>= 2.39.1) but 2.33.12+really2.32.4-5 is installed
 gdm3 : Depends: libgdm1 (= 3.12.2-2.1) but it is not installed
        Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
        Depends: libsystemd-id128-0 (>= 38) but it is not installed
        Depends: libsystemd-journal0 (>= 38) but it is not installed
        Depends: libsystemd-login0 (>= 186) but 44-11+deb7u4 is installed
        Depends: gir1.2-gdm3 (= 3.12.2-2.1) but it is not installed
        Depends: libpam-systemd but it is not installed
        Depends: gnome-session-bin (>= 3.10) but 3.4.2.1-4 is installed
        Depends: policykit-1 (>= 0.105-5~) but 0.105-3 is installed
        Depends: dconf-cli (>= 0.20) but it is not installed
 gir1.2-glib-2.0 : Depends: libglib2.0-0 (>= 2.39.91) but 2.33.12+really2.32.4-5 is installed
 glib-networking : Depends: libglib2.0-0 (>= 2.39.4) but 2.33.12+really2.32.4-5 is installed
 glib-networking-services : Depends: libglib2.0-0 (>= 2.39.3) but 2.33.12+really2.32.4-5 is installed
 gnome-control-center : Depends: libaccountsservice0 (>= 0.6.34) but 0.6.21-8 is installed
                        Depends: libcheese-gtk23 (>= 3.4.0) but it is not installed
                        Depends: libcheese7 (>= 3.0.1) but it is not installed
                        Depends: libclutter-1.0-0 (>= 1.11.10) but 1.10.8-2 is installed
                        Depends: libcolord-gtk1 (>= 0.1.24) but it is not installed
                        Depends: libglib2.0-0 (>= 2.39.91) but 2.33.12+really2.32.4-5 is installed
                        Depends: libgnome-bluetooth13 (>= 3.12.0) but it is not installed
                        Depends: libgnome-desktop-3-10 (>= 3.11.90) but it is not installed
                        Depends: libgoa-1.0-0b (>= 3.7.90) but it is not installed
                        Depends: libgoa-backend-1.0-1 (>= 3.10.0) but it is not installed
                        Depends: libgrilo-0.2-1 (>= 0.2.2) but it is not installed
                        Depends: libibus-1.0-5 (>= 1.5.2) but it is not installed
                        Depends: libmm-glib0 (>= 0.7.991) but it is not installed
                        Depends: libnm-glib4 (>= 0.9.7.995) but 0.9.4.0-10 is installed
                        Depends: libnm-gtk0 (>= 0.9.7.997) but 0.9.4.1-5 is installed
                        Depends: libnm-util2 (>= 0.9.10.0) but 0.9.4.0-10 is installed
                        Depends: libpwquality1 (>= 1.1.0) but it is not installed
                        Depends: libupower-glib2 (>= 0.99.0) but it is not installed
                        Depends: libwacom2 (>= 0.7) but 0.6-1 is installed
                        Depends: colord (>= 0.1.30) but 0.1.21-1 is installed
                        Depends: gnome-icon-theme (>= 3.7) but 3.4.0-2 is installed
                        Depends: gnome-icon-theme-symbolic (>= 3.7) but 3.4.0-2 is installed
                        Depends: gsettings-desktop-schemas (>= 3.9.91) but 3.4.2-3 is installed
                        Recommends: rygel but it is not installed or
                                    rygel-tracker but it is not installed
                        Recommends: system-config-printer (>= 1.4) but it is not installed
                        Recommends: network-manager-gnome (>= 0.9.8) but 0.9.4.1-5 is installed
                        Recommends: libnss-myhostname but it is not installed
                        Recommends: realmd but it is not installed
 gnome-panel : Depends: libecal-1.2-16 (>= 3.5.91) but it is not installed
               Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not installed
               Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
               Depends: libgnome-desktop-3-10 (>= 3.11.90) but it is not installed
               Depends: libgweather-3-6 (>= 3.7.91) but it is not installed
               Depends: libical1 (>= 1.0) but it is not installed
               Depends: gnome-panel-data (= 3.8.0-3) but 3.4.2.1-4 is installed
               Recommends: gnome-session-flashback but it is not installed
 gnome-screensaver : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
                     Depends: libgnome-desktop-3-10 (>= 3.11.90) but it is not installed
                     Depends: libgnomekbd8 (>= 3.6.0) but it is not installed
 gnome-settings-daemon : Depends: libgeocode-glib0 (>= 0.99.1) but 0.99.0-1 is installed
                         Depends: libglib2.0-0 (>= 2.37.7) but 2.33.12+really2.32.4-5 is installed
                         Depends: libgnome-desktop-3-10 (>= 3.11.90) but it is not installed
                         Depends: libgweather-3-6 (>= 3.10.0) but it is not installed
                         Depends: libibus-1.0-5 (>= 1.5.1) but it is not installed
                         Depends: libpackagekit-glib2-16 (>= 0.8.10) but it is not installed
                         Depends: libupower-glib2 (>= 0.99.0) but it is not installed
                         Depends: libwacom2 (>= 0.7) but 0.6-1 is installed
                         Depends: systemd but it is not installed
                         Depends: gsettings-desktop-schemas (>= 3.10.0) but 3.4.2-3 is installed
 gnome-shell : Depends: gir1.2-clutter-1.0 (>= 1.17) but 1.10.8-2 is installed
               Depends: gir1.2-gtk-3.0 (>= 3.8) but 3.4.2-7 is installed
               Depends: gir1.2-mutter-3.0 (>= 3.12.0) but 3.4.1-5 is installed
               Depends: libclutter-1.0-0 (>= 1.15.90) but 1.10.8-2 is installed
               Depends: libcogl-pango20 (>= 1.17.4) but it is not installed
               Depends: libcogl20 (>= 1.17.4) but it is not installed
               Depends: libecal-1.2-16 (>= 3.5.91) but it is not installed
               Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not installed
               Depends: libgjs0-libmozjs-24-0
               Depends: libgjs0e (>= 1.40.1) but it is not installed
               Depends: libglib2.0-0 (>= 2.39.90) but 2.33.12+really2.32.4-5 is installed
               Depends: libgstreamer1.0-0 (>= 1.0.0) but it is not installed
               Depends: libical1 (>= 1.0) but it is not installed
               Depends: libmozjs-24-0 but it is not installed
               Depends: libmutter0d but it is not installed
               Depends: libsystemd-journal0 (>= 38) but it is not installed
               Depends: evolution-data-server (>= 3.7.90) but 3.4.4-3 is installed
               Depends: gir1.2-gdm3 (>= 3.5.90) but it is not installed
               Depends: gir1.2-atspi-2.0 (>= 2.9.91) but 2.5.3-2 is installed
               Depends: gir1.2-caribou-1.0 (>= 0.4.8) but 0.4.4-1 is installed
               Depends: gir1.2-gdesktopenums-3.0 (>= 3.12) but 3.4.2-3 is installed
               Depends: gir1.2-gcr-3 (>= 3.7.5) but 3.4.1-3 is installed
               Depends: gir1.2-gnomebluetooth-1.0 (>= 3.6.0) but 3.4.2-1 is installed
               Depends: gir1.2-gnomedesktop-3.0 (>= 3.12.0) but it is not installed
               Depends: gir1.2-ibus-1.0 (>= 1.5.2) but it is not installed
               Depends: gir1.2-nmgtk-1.0 (>= 0.9.8) but it is not installed
               Depends: gir1.2-telepathylogger-0.2 (>= 0.8.0) but 0.4.0-1 is installed
               Depends: gir1.2-upowerglib-1.0 (>= 0.99) but 0.9.17-1 is installed
               Depends: gjs (>= 1.39.0) but 1.32.0-5 is installed
               Depends: gsettings-desktop-schemas (>= 3.11) but 3.4.2-3 is installed
 gnome-shell-extensions : Depends: gvfs (>= 1.16.0) but 1.12.3-4 is installed
                          Depends: gnome-session (>= 3.8) but 3.4.2.1-4 is installed
                          Recommends: gnome-tweak-tool (>= 3.12) but it is not installed
 gnome-themes-standard : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
                         Recommends: gtk2-engines-pixbuf but it is not installed
 libatk1.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 libatspi2.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 libcamel-1.2-49 : Depends: libglib2.0-0 (>= 2.36) but 2.33.12+really2.32.4-5 is installed
 libcolord2 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 libdconf1 : Depends: libglib2.0-0 (>= 2.39.1) but 2.33.12+really2.32.4-5 is installed
 libgail-3-0 : Depends: libglib2.0-0 (>= 2.39.5) but 2.33.12+really2.32.4-5 is installed
 libgail-common : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 libgcr-base-3-1 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 libgdk-pixbuf2.0-0 : Depends: libglib2.0-0 (>= 2.37.6) but 2.33.12+really2.32.4-5 is installed
 libgdk-pixbuf2.0-dev : Depends: libglib2.0-0 (>= 2.37.6) but 2.33.12+really2.32.4-5 is installed
 libgirepository-1.0-1 : Depends: libglib2.0-0 (>= 2.39.0) but 2.33.12+really2.32.4-5 is installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.40.0-4) but 2.33.12+really2.32.4-5 is installed
 libglib2.0-dev : Depends: libglib2.0-0 (= 2.40.0-4) but 2.33.12+really2.32.4-5 is installed
 libgtk-3-0 : Depends: libglib2.0-0 (>= 2.39.90) but 2.33.12+really2.32.4-5 is installed
 libgtk-3-bin : Depends: libglib2.0-0 (>= 2.39.5) but 2.33.12+really2.32.4-5 is installed
 libgtk2.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 libpango-1.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 libpango1.0-dev : Depends: libcairo2 (>= 1.12.10) but 1.12.2-3 is installed
                   Depends: libglib2.0-0 (>= 2.34.0) but 2.33.12+really2.32.4-5 is installed
                   Depends: libcairo2-dev (>= 1.12.10) but 1.12.2-3 is installed
 libpangocairo-1.0-0 : Depends: libcairo2 (>= 1.12.10) but 1.12.2-3 is installed
                       Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 libpangoft2-1.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 libpangox-1.0-0 : Depends: libglib2.0-0 (>= 2.34.0) but 2.33.12+really2.32.4-5 is installed
 libpangoxft-1.0-0 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 librsvg2-2 : Depends: libglib2.0-0 (>= 2.37.3) but 2.33.12+really2.32.4-5 is installed
 libsecret-1-0 : Depends: libglib2.0-0 (>= 2.38.0) but 2.33.12+really2.32.4-5 is installed
 libsoup2.4-1 : Depends: libglib2.0-0 (>= 2.39.90) but 2.33.12+really2.32.4-5 is installed
E: Unmet dependencies. Try using -f.
root@kali:/etc/apt# apt-get upgrade
```

---

### Post by deadflowr on 2014-08-29
Thread moved to [B]Other Operating Systems and Projects

[/B]&#8203;

---

