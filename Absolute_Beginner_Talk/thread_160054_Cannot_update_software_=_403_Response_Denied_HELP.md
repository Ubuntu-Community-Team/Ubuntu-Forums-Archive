---
title: "Cannot update software = 403 Response Denied HELP"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by hepkat63 on 2006-04-14
Hi,
I have only just installed Ubuntu 5.10 Breezy.   I am now trying to update the packages and software.  I have tried the gui update manager and all i receive is '403 response denied".  I searched through this forum and found a few things to try.  I tried using apt-get upgrade and apt-get update (both as root) and still cannot get anywhere.  I have tried changing the source list to an Australia one  - still come up with errors.  Can anyone give me a quick fix for what should be something very elementary to do.  Here is my screen dump:

root@ubuntu:/home/srolfe# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
The following packages will be upgraded:
  acpi-support base-config bogofilter bogofilter-bdb bogofilter-common cpio dhcp3-client dhcp3-common evince
  fetchmail gksu gnupg gtk2-engines-pixbuf info iptables irssi-text language-pack-en language-pack-gnome-en
  language-selector libc6 libc6-i686 libcairo2 libcurl3 libgda2-3 libgda2-common libgksu1.2-0 libgl1-mesa
  libgl1-mesa-dri libglu1-mesa libgnome2-canvas-perl libgnutls11 libgphoto2-2 libgphoto2-port0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libkpathsea3 libmagick6 libmysqlclient14 libnautilus-extension1 libnspr4 libnss3
  libperl5.8 libpoppler0c2 libpoppler0c2-glib libpq4 libssl0.9.7 libtasn1-2 libtotem-plparser0 libvte-common
  libvte4 linux-386 linux-restricted-modules-common locales login nautilus nautilus-data openssh-client passwd
  perl perl-base perl-modules pmount python-apt python-gnome2-extras python2.4-apt python2.4-gnome2-extras
  ssh-askpass-gnome sudo tar totem totem-gstreamer ubuntu-docs unzip wget xkeyboard-config
76 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 60.3MB of archives.
After unpacking 16.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libc6 2.3.5-1ubuntu12.5.10.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main login 1:4.0.3-37ubuntu8
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libc6-i686 2.3.5-1ubuntu12.5.10.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main language-pack-en 20060126
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main perl-modules 5.8.7-5ubuntu1.2
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main language-pack-gnome-en 20060126
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main xkeyboard-config 0.6-5breezy1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main perl 5.8.7-5ubuntu1.2
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main dhcp3-client 3.0.2-1ubuntu7
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main dhcp3-common 3.0.2-1ubuntu7
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main locales 2.3.5-1ubuntu12.5.10.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libperl5.8 5.8.7-5ubuntu1.2
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main iptables 1.3.1-2ubuntu1.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main acpi-support 0.46ubuntu1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main perl-base 5.8.7-5ubuntu1.2
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libnautilus-extension1 2.12.1-0ubuntu1.2
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main evince 0.4.0-0ubuntu4.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libgksu1.2-0 1.3.1-1ubuntu7
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main tar 1.15.1-2ubuntu0.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main gksu 1.3.0-1ubuntu11
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main python2.4-apt 0.6.16.2breezy1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libmagick6 6:6.2.3.4-1ubuntu1.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main language-selector 0.1.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libgnome2-canvas-perl 1.002-1ubuntu0.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libgphoto2-port0 2.1.6-1ubuntu6.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main passwd 1:4.0.3-37ubuntu8
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libgphoto2-2 2.1.6-1ubuntu6.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libnspr4 2:1.7.12-1ubuntu1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main base-config 2.67ubuntu20
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libnss3 2:1.7.12-1ubuntu1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libpq4 8.0.3-15ubuntu2
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libtotem-plparser0 1.2.0-0ubuntu3.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libvte4 1:0.11.15-0ubuntu3
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libvte-common 1:0.11.15-0ubuntu3
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main nautilus-data 2.12.1-0ubuntu1.2
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main nautilus 2.12.1-0ubuntu1.2
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main pmount 0.9.5-0ubuntu6
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main python-apt 0.6.16.2breezy1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main python2.4-gnome2-extras 2.12.0-0ubuntu1.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main python-gnome2-extras 2.12.0-0ubuntu1.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main totem 1.2.0-0ubuntu3.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main totem-gstreamer 1.2.0-0ubuntu3.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main ubuntu-docs 5.10-6.3
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main cpio 2.5-1.2ubuntu1.1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libgl1-mesa-dri 6.3.2-0ubuntu6breezy1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libglu1-mesa 6.3.2-0ubuntu6breezy1
  403 Response denied
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main libgl1-mesa 6.3.2-0ubuntu6breezy1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main gnupg 1.4.1-1ubuntu1.2
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libtasn1-2 0.2.10-4ubuntu0.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libgnutls11 1.0.16-13.1ubuntu1.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libssl0.9.7 0.9.7g-1ubuntu1.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main sudo 1.6.8p9-2ubuntu2.3
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main info 4.7-2.2ubuntu2.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main openssh-client 1:4.1p1-7ubuntu4.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main wget 1.10-2ubuntu0.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main bogofilter-common 0.95.2-1ubuntu1.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main bogofilter-bdb 0.95.2-1ubuntu1.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main bogofilter 0.95.2-1ubuntu1.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libcairo2 1.0.2-0ubuntu1.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libgtk2.0-common 2.8.6-0ubuntu2.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libgtk2.0-bin 2.8.6-0ubuntu2.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libgtk2.0-0 2.8.6-0ubuntu2.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libkpathsea3 2.0.2-30ubuntu3.5
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libpoppler0c2-glib 0.4.2-0ubuntu6.7
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libpoppler0c2 0.4.2-0ubuntu6.7
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main fetchmail 6.2.5-13ubuntu3.2
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main gtk2-engines-pixbuf 2.8.6-0ubuntu2.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main irssi-text 0.8.9+0.8.10rc5-0ubuntu4.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libcurl3 7.14.0-2ubuntu1.2
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libgda2-common 1.2.1-2ubuntu3.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libgda2-3 1.2.1-2ubuntu3.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libmysqlclient14 4.1.12-1ubuntu3.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted linux-386 2.6.12.16.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted linux-restricted-modules-common 2.6.12.4-11.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main ssh-askpass-gnome 1:4.1p1-7ubuntu4.1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main unzip 5.52-3ubuntu2.2
  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.0.3-37ubuntu8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.0.3-37ubuntu8_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.7-5ubuntu1.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.7-5ubuntu1.2_all.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.5-1ubuntu12.5.10.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.5-1ubuntu12.5.10.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.5-1ubuntu12.5.10.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.5-1ubuntu12.5.10.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.7-5ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.7-5ubuntu1.2_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.7-5ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.7-5ubuntu1.2_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.7-5ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.7-5ubuntu1.2_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.15.1-2ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.15.1-2ubuntu0.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_20060126_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_20060126_all.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_20060126_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_20060126_all.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick6_6.2.3.4-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick6_6.2.3.4-1ubuntu1.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/x/xkeyboard-config/xkeyboard-config_0.6-5breezy1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/x/xkeyboard-config/xkeyboard-config_0.6-5breezy1_all.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/shadow/passwd_4.0.3-37ubuntu8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/shadow/passwd_4.0.3-37ubuntu8_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/base-config/base-config_2.67ubuntu20_all.deb](http://security.ubuntu.com/ubuntu/pool/main/b/base-config/base-config_2.67ubuntu20_all.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cpio/cpio_2.5-1.2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cpio/cpio_2.5-1.2ubuntu1.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-client_3.0.2-1ubuntu7_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-client_3.0.2-1ubuntu7_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.0.2-1ubuntu7_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.0.2-1ubuntu7_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg_1.4.1-1ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg_1.4.1-1ubuntu1.2_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libt/libtasn1-2/libtasn1-2_0.2.10-4ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libt/libtasn1-2/libtasn1-2_0.2.10-4ubuntu0.1_i386.deb) 403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnutls11/libgnutls11_1.0.16-13.1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnutls11/libgnutls11_1.0.16-13.1ubuntu1.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.7_0.9.7g-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.7_0.9.7g-1ubuntu1.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/locales_2.3.5-1ubuntu12.5.10.1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/locales_2.3.5-1ubuntu12.5.10.1_all.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.8p9-2ubuntu2.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.8p9-2ubuntu2.3_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texinfo/info_4.7-2.2ubuntu2.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/i/iptables/iptables_1.3.1-2ubuntu1.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/i/iptables/iptables_1.3.1-2ubuntu1.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.1p1-7ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.1p1-7ubuntu4.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.10-2ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.10-2ubuntu0.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/a/acpi-support/acpi-support_0.46ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/a/acpi-support/acpi-support_0.46ubuntu1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-common_0.95.2-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-common_0.95.2-1ubuntu1.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-bdb_0.95.2-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-bdb_0.95.2-1ubuntu1.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter_0.95.2-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter_0.95.2-1ubuntu1.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.0.2-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.0.2-0ubuntu1.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.6-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.6-0ubuntu2.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea3_2.0.2-30ubuntu3.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea3_2.0.2-30ubuntu3.5_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.12.1-0ubuntu1.2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.12.1-0ubuntu1.2_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler0c2-glib_0.4.2-0ubuntu6.7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler0c2-glib_0.4.2-0ubuntu6.7_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler0c2_0.4.2-0ubuntu6.7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler0c2_0.4.2-0ubuntu6.7_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_0.4.0-0ubuntu4.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_0.4.0-0ubuntu4.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/fetchmail/fetchmail_6.2.5-13ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/fetchmail/fetchmail_6.2.5-13ubuntu3.2_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgksu1.2/libgksu1.2-0_1.3.1-1ubuntu7_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgksu1.2/libgksu1.2-0_1.3.1-1ubuntu7_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gksu/gksu_1.3.0-1ubuntu11_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gksu/gksu_1.3.0-1ubuntu11_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.8.6-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.8.6-0ubuntu2.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/irssi-text/irssi-text_0.8.9+0.8.10rc5-0ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/irssi-text/irssi-text_0.8.9+0.8.10rc5-0ubuntu4.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python2.4-apt_0.6.16.2breezy1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python2.4-apt_0.6.16.2breezy1_i386.deb) 403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector_0.1.1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector_0.1.1_all.deb) 403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.14.0-2ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.14.0-2ubuntu1.2_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libg/libgda2/libgda2-common_1.2.1-2ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libg/libgda2/libgda2-common_1.2.1-2ubuntu3.1_i386.deb) 403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libg/libgda2/libgda2-3_1.2.1-2ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libg/libgda2/libgda2-3_1.2.1-2ubuntu3.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgnome2-canvas-perl/libgnome2-canvas-perl_1.002-1ubuntu0.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgnome2-canvas-perl/libgnome2-canvas-perl_1.002-1ubuntu0.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.1.6-1ubuntu6.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.1.6-1ubuntu6.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.1.6-1ubuntu6.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.1.6-1ubuntu6.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-4.1/libmysqlclient14_4.1.12-1ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-4.1/libmysqlclient14_4.1.12-1ubuntu3.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mozilla/libnspr4_1.7.12-1ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mozilla/libnspr4_1.7.12-1ubuntu1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mozilla/libnss3_1.7.12-1ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mozilla/libnss3_1.7.12-1ubuntu1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.0/libpq4_8.0.3-15ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.0/libpq4_8.0.3-15ubuntu2_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser0_1.2.0-0ubuntu3.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser0_1.2.0-0ubuntu3.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte4_0.11.15-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte4_0.11.15-0ubuntu3_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.11.15-0ubuntu3_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.11.15-0ubuntu3_all.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-386_2.6.12.16.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-386_2.6.12.16.1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.12/linux-restricted-modules-common_2.6.12.4-11.1_all.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.12/linux-restricted-modules-common_2.6.12.4-11.1_all.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.12.1-0ubuntu1.2_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.12.1-0ubuntu1.2_all.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.12.1-0ubuntu1.2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.12.1-0ubuntu1.2_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.5-0ubuntu6_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.5-0ubuntu6_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.6.16.2breezy1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.6.16.2breezy1_all.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gnome-python-extras/python2.4-gnome2-extras_2.12.0-0ubuntu1.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gnome-python-extras/python2.4-gnome2-extras_2.12.0-0ubuntu1.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gnome-python-extras/python-gnome2-extras_2.12.0-0ubuntu1.1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gnome-python-extras/python-gnome2-extras_2.12.0-0ubuntu1.1_all.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.1p1-7ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.1p1-7ubuntu4.1_i386.deb) 403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_1.2.0-0ubuntu3.1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_1.2.0-0ubuntu3.1_all.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_1.2.0-0ubuntu3.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_1.2.0-0ubuntu3.1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_5.10-6.3_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_5.10-6.3_all.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-3ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-3ubuntu2.2_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_6.3.2-0ubuntu6breezy1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_6.3.2-0ubuntu6breezy1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglu1-mesa_6.3.2-0ubuntu6breezy1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglu1-mesa_6.3.2-0ubuntu6breezy1_i386.deb)  403 Response denied
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb)  403 Response denied

---

### Post by stozball on 2006-04-19
Do you use a proxy server to connect to the internet?

---

