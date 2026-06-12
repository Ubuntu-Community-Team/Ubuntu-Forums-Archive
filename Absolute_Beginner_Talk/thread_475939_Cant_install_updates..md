---
title: "Cant install updates."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by sirab on 2007-06-16
I messed around and did something really stupid.

and now when i try to update it recomends a partial update and when i say ok to that i get this message

> It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

adduser
alsa-base
alsa-utils
apmd
brltty
brltty-x11
bsdmainutils
bsdutils
busybox
ca-certificates
console-terminus
coreutils
dash
defoma
dhcdbd
dhcp3-client
dhcp3-common
dmidecode
dosfstools
dpkg
dpkg-dev
dselect
eject
ekiga
fontconfig
fontconfig-config
gamin
gnome-mount
gnome-pilot
gnupg
gpgv
grub
hal
hal-device-manager
hdparm
iceweasel
iceweasel-l10n-en-gb
initramfs-tools
initscripts
iputils-arping
iputils-ping
iputils-tracepath
iso-codes
kino
klibc-utils
libapm1
libasound2
libasound2-dev
libavc1394-0
libbrlapi1
libcamel1.2-8
libdb4.2
libdb4.3
libdc1394-13
libebook1.2-5
libedataserver1.2-7
libeel2-2.14
libflac7
libfontconfig1
libfontconfig1-dev
libgail17
libgamin0
libgksu2-0
libglade2-0
libgnome-pilot2
libgnome2-canvas-perl
libgpmg1
libgtkspell0
libhal-storage1
libhal1
libid3tag0
libklibc
libkpathsea4
libkrb53
libmozjs0d
libnewt0.52
libnspr4-0d
libnss3-0d
libopal-2.2.0
libparted1.7-1
libsane
libscrollkeeper0
libsdl-image1.2
libsdl-image1.2-dev
libsdl1.2-dev
libsdl1.2debian
libsdl1.2debian-alsa
libsensors3
libsmbclient
libsnmp-base
libsnmp9
libswfdec0.3
libtiff4
libtiff4-dev
libtiffxx0c2
libusb-0.1-4
libwrap0
libxul-common
libxul0d
linux-sound-base
login
lsb-base
lsb-release
m4
man-db
modconf
module-init-tools
mount
mozilla-firefox-locale-en-gb
netbase
ntpdate
openbsd-inetd
openssh-client
p7zip-full
parted
passwd
popularity-contest
ppp
pppoeconf
samba-common
screen
scrollkeeper
smbclient
ssh-askpass-gnome
ssl-cert
sysv-rc
sysvinit-utils
tasksel
tasksel-data
tcpd
ttf-arabeyes
ttf-arphic-ukai
ttf-bengali-fonts
ttf-dejavu
ttf-devanagari-fonts
ttf-gujarati-fonts
ttf-indic-fonts
ttf-kannada-fonts
ttf-malayalam-fonts
ttf-oriya-fonts
ttf-punjabi-fonts
ttf-tamil-fonts
ttf-telugu-fonts
ucf
update-inetd
util-linux
util-linux-locales
vnc-common
whiptail
wvdial
x-ttcidfont-conf
xbitmaps
xsane
xsane-common
xserver-xorg-input-synaptics
xserver-xorg-video-savage
xvncviewer

And if I dont agree to the partial update and try a full update it tells me that another synaptics is running.

---

### Post by llamakc on 2007-06-16
Would make sense to explain what you did that was, in your words, "stupid". That can help someone walk you through the fix.

---

### Post by sirab on 2007-06-16
I don't really remember.

I messed around with some packages in synaptics trying to get vmware to work and then canceled an update.

Thats about it..

---

### Post by llamakc on 2007-06-16
Open a terminal.

Type: 

sudo killall synaptic

Next, type

ps aux | grep synaptic

and cut/paste the results here.

---

