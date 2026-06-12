---
title: "dpkg-scanpackages issue"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by byenary on 2007-05-03
Hello im experimenting with some software made by 3th party.

I have made a repositroy on a local server to install the app wich contains about 10 deb files, this goes fine.
Now the deb files for this application also depend on a load of other debs wich can be retrieved from the standard + universer repository.
I want to add all thee debs that are being fetched from the internet to the repository, so i copied my /var/cache/apt/archives
and did a newe dpkg-scanpackages but now i get output like this, do you know how to get rid of thes version issues ?



root@Backupsrv:/var/www/eigenrelease2/ubuntu# dpkg-scanpackages eigenrelease2 /dev/null | gzip -9c > eigenrelease2/Packages.gz
 ! Package adduser (filename eigenrelease2/adduser_3.100_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/adduser_3.80ubuntu2_all.deb !
 ! Package alsa-base (filename eigenrelease2/alsa-base_1.0.13-3ubuntu1_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/alsa-base_1.0.10-4ubuntu4_all.deb !
 ! Package alsa-utils (filename eigenrelease2/alsa-utils_1.0.13-1ubuntu5_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/alsa-utils_1.0.10-1ubuntu14_i386.deb !
 ! Package apt (filename eigenrelease2/apt_0.6.46.4ubuntu10_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/apt_0.6.43.3ubuntu2_i386.deb !
 ! Package aptitude (filename eigenrelease2/aptitude_0.4.4-1ubuntu3_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/aptitude_0.4.0-5ubuntu3_i386.deb !
 ! Package apt-utils (filename eigenrelease2/apt-utils_0.6.46.4ubuntu10_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/apt-utils_0.6.43.3ubuntu2_i386.deb !
 ! Package base-files (filename eigenrelease2/base-files_4ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/base-files_3.1.9ubuntu7.1_i386.deb !
 ! Package bash (filename eigenrelease2/bash_3.2-0ubuntu7_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/bash_3.1-2ubuntu10_i386.deb !
 ! Package belocs-locales-bin (filename eigenrelease2/belocs-locales-bin_2.4-2ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/belocs-locales-bin_2.3.5-5ubuntu7_i386.deb !
 ! Package bsdutils (filename eigenrelease2/bsdutils_1%3a2.12r-17ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/bsdutils_1%3a2.12r-4ubuntu6_i386.deb !
 ! Package busybox-initramfs (filename eigenrelease2/busybox-initramfs_1%3a1.01-4ubuntu3_i386.deb) is repeat;
   ignored that one and using data from eigenrelease2/busybox-initramfs_1%3a1.1.3-3ubuntu3_i386.deb !
 ! Package bzip2 (filename eigenrelease2/bzip2_1.0.3-6build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/bzip2_1.0.3-0ubuntu2_i386.deb !
 ! Package console-tools (filename eigenrelease2/console-tools_1%3a0.2.3dbs-65ubuntu3_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/console-tools_1%3a0.2.3dbs-60ubuntu3_i386.deb !
 ! Package coreutils (filename eigenrelease2/coreutils_5.97-5.2ubuntu3_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/coreutils_5.93-5ubuntu4_i386.deb !
 ! Package cpio (filename eigenrelease2/cpio_2.6-10ubuntu0.2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/cpio_2.6-10_i386.deb !
 ! Package cpio (filename eigenrelease2/cpio_2.6-17_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/cpio_2.6-10ubuntu0.2_i386.deb !
 ! Package debconf (filename eigenrelease2/debconf_1.5.13ubuntu1_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/debconf_1.4.72ubuntu9_all.deb !
 ! Package debconf-i18n (filename eigenrelease2/debconf-i18n_1.5.13ubuntu1_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/debconf-i18n_1.4.72ubuntu9_all.deb !
 ! Package debianutils (filename eigenrelease2/debianutils_2.17.4build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/debianutils_2.15.2_i386.deb !
 ! Package dhcp3-client (filename eigenrelease2/dhcp3-client_3.0.4-12ubuntu4_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/dhcp3-client_3.0.3-6ubuntu7_i386.deb !
 ! Package dhcp3-common (filename eigenrelease2/dhcp3-common_3.0.4-12ubuntu4_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/dhcp3-common_3.0.3-6ubuntu7_i386.deb !
 ! Package diff (filename eigenrelease2/diff_2.8.1-11ubuntu4_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/diff_2.8.1-11ubuntu3_i386.deb !
 ! Package dpkg (filename eigenrelease2/dpkg_1.13.11ubuntu7_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/dpkg_1.13.11ubuntu6_i386.deb !
 ! Package dpkg (filename eigenrelease2/dpkg_1.13.24ubuntu6_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/dpkg_1.13.11ubuntu7_i386.deb !
 ! Package e2fslibs (filename eigenrelease2/e2fslibs_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/e2fslibs_1.38-2ubuntu2_i386.deb !
 ! Package e2fsprogs (filename eigenrelease2/e2fsprogs_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/e2fsprogs_1.38-2ubuntu2_i386.deb !
 ! Package eject (filename eigenrelease2/eject_2.0.13deb-18ubuntu4_i386.deb) is repeat;
   ignored that one and using data from eigenrelease2/eject_2.1.4-2.1ubuntu2_i386.deb !
 ! Package ethtool (filename eigenrelease2/ethtool_5-1build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/ethtool_3-1_i386.deb !
 ! Package findutils (filename eigenrelease2/findutils_4.2.28-2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/findutils_4.2.27-1ubuntu1_i386.deb !
 ! Package gettext-base (filename eigenrelease2/gettext-base_0.16.1-1ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/gettext-base_0.14.5-2ubuntu3_i386.deb !
 ! Package gnupg (filename eigenrelease2/gnupg_1.4.6-1ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/gnupg_1.4.2.2-1ubuntu2.2_i386.deb !
 ! Package grep (filename eigenrelease2/grep_2.5.1.ds2-6build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/grep_2.5.1.ds2-4_i386.deb !
 ! Package gzip (filename eigenrelease2/gzip_1.3.9-2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/gzip_1.3.5-12_i386.deb !
 ! Package hostname (filename eigenrelease2/hostname_2.93build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/hostname_2.91.0ubuntu1_i386.deb !
 ! Package ifupdown (filename eigenrelease2/ifupdown_0.6.8ubuntu6_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/ifupdown_0.6.7ubuntu7_i386.deb !
 ! Package initramfs-tools (filename eigenrelease2/initramfs-tools_0.85eubuntu10_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/initramfs-tools_0.40ubuntu32_all.deb !
 ! Package initscripts (filename eigenrelease2/initscripts_2.86.ds1-14.1ubuntu18_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/initscripts_2.86.ds1-6ubuntu32_i386.deb !
 ! Package iproute (filename eigenrelease2/iproute_20061002-3ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/iproute_20041019-4ubuntu5_i386.deb !
 ! Package iputils-ping (filename eigenrelease2/iputils-ping_3%3a20020927-3ubuntu1_i386.deb) is repeat;
   ignored that one and using data from eigenrelease2/iputils-ping_3%3a20020927-3.1ubuntu2_i386.deb !
 ! Package klibc-utils (filename eigenrelease2/klibc-utils_1.4.30-3ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/klibc-utils_1.1.16-1ubuntu5_i386.deb !
 ! Package klogd (filename eigenrelease2/klogd_1.4.1-20ubuntu4_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/klogd_1.4.1-17ubuntu7_i386.deb !
 ! Package less (filename eigenrelease2/less_394-4build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/less_394-1_i386.deb !
 ! Package libacl1 (filename eigenrelease2/libacl1_2.2.42-1ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libacl1_2.2.34-1ubuntu1_i386.deb !
 ! Package libasound2 (filename eigenrelease2/libasound2_1.0.13-1ubuntu5_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libasound2_1.0.10-2ubuntu4_i386.deb !
 ! Package libattr1 (filename eigenrelease2/libattr1_2.4.25-1_i386.deb) is repeat;
   ignored that one and using data from eigenrelease2/libattr1_1%3a2.4.32-1.1ubuntu1_i386.deb !
 ! Package libblkid1 (filename eigenrelease2/libblkid1_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libblkid1_1.38-2ubuntu2_i386.deb !
 ! Package libbz2-1.0 (filename eigenrelease2/libbz2-1.0_1.0.3-6build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libbz2-1.0_1.0.3-0ubuntu2_i386.deb !
 ! Package libc6 (filename eigenrelease2/libc6_2.3.6-0ubuntu20_i386.deb) is repeat;
   ignored that one and using data from eigenrelease2/libc6_2.3.6-0ubuntu20.4_i386.deb !
 ! Package libc6 (filename eigenrelease2/libc6_2.5-0ubuntu14_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libc6_2.3.6-0ubuntu20.4_i386.deb !
 ! Package libc6-i686 (filename eigenrelease2/libc6-i686_2.3.6-0ubuntu20_i386.deb) is repeat;
   ignored that one and using data from eigenrelease2/libc6-i686_2.3.6-0ubuntu20.4_i386.deb !
 ! Package libc6-i686 (filename eigenrelease2/libc6-i686_2.5-0ubuntu14_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libc6-i686_2.3.6-0ubuntu20.4_i386.deb !
 ! Package libcomerr2 (filename eigenrelease2/libcomerr2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libcomerr2_1.38-2ubuntu2_i386.deb !
 ! Package libconsole (filename eigenrelease2/libconsole_1%3a0.2.3dbs-65ubuntu3_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libconsole_1%3a0.2.3dbs-60ubuntu3_i386.deb !
 ! Package libdb4.3 (filename eigenrelease2/libdb4.3_4.3.29-6build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libdb4.3_4.3.29-5build1_i386.deb !
 ! Package libdbus-1-2 (filename eigenrelease2/libdbus-1-2_0.60-6ubuntu8_i386.deb) is repeat;
   ignored that one and using data from eigenrelease2/libdbus-1-2_0.60-6ubuntu8.1_i386.deb !
 ! Package libdevmapper1.02 (filename eigenrelease2/libdevmapper1.02_2%3a1.02.08-1ubuntu10_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libdevmapper1.02_2%3a1.02.05-1ubuntu1_i386.deb !
 ! Package libfribidi0 (filename eigenrelease2/libfribidi0_0.10.7-4build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libfribidi0_0.10.7-1_i386.deb !
 ! Package libgcc1 (filename eigenrelease2/libgcc1_1%3a4.1.2-0ubuntu4_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libgcc1_1%3a4.0.3-1ubuntu5_i386.deb !
 ! Package libgcrypt11 (filename eigenrelease2/libgcrypt11_1.2.3-2build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libgcrypt11_1.2.2-1_i386.deb !
 ! Package libgpg-error0 (filename eigenrelease2/libgpg-error0_1.4-2build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libgpg-error0_1.1-4_i386.deb !
 ! Package libiw28 (filename eigenrelease2/libiw28_28-1ubuntu3_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libiw28_27+28pre13-1ubuntu2_i386.deb !
 ! Package libklibc (filename eigenrelease2/libklibc_1.4.30-3ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libklibc_1.1.16-1ubuntu5_i386.deb !
 ! Package libldap2 (filename eigenrelease2/libldap2_2.1.30-13.3_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libldap2_2.1.30-12ubuntu3_i386.deb !
 ! Package libncurses5 (filename eigenrelease2/libncurses5_5.5-5ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libncurses5_5.5-1ubuntu3_i386.deb !
 ! Package libncursesw5 (filename eigenrelease2/libncursesw5_5.5-5ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libncursesw5_5.5-1ubuntu3_i386.deb !
 ! Package libopencdk8 (filename eigenrelease2/libopencdk8_0.5.9-2build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libopencdk8_0.5.7-2_i386.deb !
 ! Package libpam0g (filename eigenrelease2/libpam0g_0.79-4ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libpam0g_0.79-3ubuntu14_i386.deb !
 ! Package libpam-modules (filename eigenrelease2/libpam-modules_0.79-4ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libpam-modules_0.79-3ubuntu14_i386.deb !
 ! Package libpam-runtime (filename eigenrelease2/libpam-runtime_0.79-4ubuntu2_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libpam-runtime_0.79-3ubuntu14_all.deb !
 ! Package libpopt0 (filename eigenrelease2/libpopt0_1.10-3build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libpopt0_1.7-5_i386.deb !
 ! Package libreadline5 (filename eigenrelease2/libreadline5_5.2-2ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libreadline5_5.1-7build1_i386.deb !
 ! Package libsasl2-modules (filename eigenrelease2/libsasl2-modules_2.1.22.dfsg1-8ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libsasl2-modules_2.1.19.dfsg1-0.1ubuntu2_i386.deb !
 ! Package libselinux1 (filename eigenrelease2/libselinux1_1.32-3ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libselinux1_1.28-2ubuntu2_i386.deb !
 ! Package libsepol1 (filename eigenrelease2/libsepol1_1.14-2build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libsepol1_1.10-1_i386.deb !
 ! Package libsigc++-2.0-0c2a (filename eigenrelease2/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libsigc++-2.0-0c2a_2.0.16-3_i386.deb !
 ! Package libslang2 (filename eigenrelease2/libslang2_2.0.6-4build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libslang2_2.0.5-1build2_i386.deb !
 ! Package libss2 (filename eigenrelease2/libss2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libss2_1.38-2ubuntu2_i386.deb !
 ! Package libssl0.9.8 (filename eigenrelease2/libssl0.9.8_0.9.8c-4build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libssl0.9.8_0.9.8a-7build1_i386.deb !
 ! Package libstdc++6 (filename eigenrelease2/libstdc++6_4.1.2-0ubuntu4_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libstdc++6_4.0.3-1ubuntu5_i386.deb !
 ! Package libsysfs2 (filename eigenrelease2/libsysfs2_2.1.0-1build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libsysfs2_2.0.0-5build1_i386.deb !
 ! Package libtext-charwidth-perl (filename eigenrelease2/libtext-charwidth-perl_0.04-4build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libtext-charwidth-perl_0.04-3_i386.deb !
 ! Package libtext-iconv-perl (filename eigenrelease2/libtext-iconv-perl_1.4-3_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libtext-iconv-perl_1.4-2_i386.deb !
 ! Package libtext-wrapi18n-perl (filename eigenrelease2/libtext-wrapi18n-perl_0.06-5_all.deb) is repeat but newer version;   used that one and ignored data from eigenrelease2/libtext-wrapi18n-perl_0.06-4_all.deb !
 ! Package libusb-0.1-4 (filename eigenrelease2/libusb-0.1-4_2%3a0.1.12-2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libusb-0.1-4_2%3a0.1.10a-22ubuntu1_i386.deb !
 ! Package libuuid1 (filename eigenrelease2/libuuid1_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/libuuid1_1.38-2ubuntu2_i386.deb !
 ! Package linux-sound-base (filename eigenrelease2/linux-sound-base_1.0.13-3ubuntu1_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/linux-sound-base_1.0.10-4ubuntu4_all.deb !
 ! Package locales (filename eigenrelease2/locales_2.3.18_all.deb) is repeat;
   ignored that one and using data from eigenrelease2/locales_2.3.18.3_all.deb !
 ! Package locales (filename eigenrelease2/locales_2.3.23_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/locales_2.3.18.3_all.deb !
 ! Package login (filename eigenrelease2/login_1%3a4.0.18.1-6ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/login_1%3a4.0.13-7ubuntu3.2_i386.deb !
 ! Package lsb-base (filename eigenrelease2/lsb-base_3.1-22ubuntu3_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/lsb-base_3.1-5ubuntu2_all.deb !
 ! Package lsb-release (filename eigenrelease2/lsb-release_3.1-22ubuntu3_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/lsb-release_3.1-5ubuntu2_all.deb !
 ! Package lsof (filename eigenrelease2/lsof_4.77.dfsg.1-3_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/lsof_4.76.dfsg.1-1_i386.deb !
 ! Package makedev (filename eigenrelease2/makedev_2.3.1-83ubuntu2_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/makedev_2.3.1-79ubuntu1_all.deb !
 ! Package mawk (filename eigenrelease2/mawk_1.3.3-11ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/mawk_1.3.3-11ubuntu1_i386.deb !
 ! Package mii-diag (filename eigenrelease2/mii-diag_2.11-2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/mii-diag_2.11-1_i386.deb !
 ! Package module-init-tools (filename eigenrelease2/module-init-tools_3.3-pre3-1ubuntu7_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/module-init-tools_3.2.2-1ubuntu7_i386.deb !
 ! Package mount (filename eigenrelease2/mount_2.12r-17ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/mount_2.12r-4ubuntu6_i386.deb !
 ! Package ncurses-base (filename eigenrelease2/ncurses-base_5.5-5ubuntu2_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/ncurses-base_5.5-1ubuntu3_all.deb !
 ! Package ncurses-bin (filename eigenrelease2/ncurses-bin_5.5-5ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/ncurses-bin_5.5-1ubuntu3_i386.deb !
 ! Package netbase (filename eigenrelease2/netbase_4.27ubuntu2_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/netbase_4.24ubuntu3_all.deb !
 ! Package netcat (filename eigenrelease2/netcat_1.10-32_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/netcat_1.10-29_i386.deb !
 ! Package net-tools (filename eigenrelease2/net-tools_1.60-17ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/net-tools_1.60-16ubuntu2_i386.deb !
 ! Package ntpdate (filename eigenrelease2/ntpdate_1%3a4.2.2.p4+dfsg-1ubuntu3_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/ntpdate_1%3a4.2.0a+stable-8.1ubuntu6_i386.deb !
 ! Package passwd (filename eigenrelease2/passwd_1%3a4.0.18.1-6ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/passwd_1%3a4.0.13-7ubuntu3.2_i386.deb !
 ! Package pciutils (filename eigenrelease2/pciutils_1%3a2.2.4-1ubuntu1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/pciutils_1%3a2.1.11-15.3ubuntu1_i386.deb !
 ! Package pcmciautils (filename eigenrelease2/pcmciautils_014-3ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/pcmciautils_012-1ubuntu4_i386.deb !
 ! Package perl (filename eigenrelease2/perl_5.8.8-7build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/perl_5.8.7-10ubuntu1_i386.deb !
 ! Package perl-base (filename eigenrelease2/perl-base_5.8.8-7build1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/perl-base_5.8.7-10ubuntu1_i386.deb !
 ! Package perl-modules (filename eigenrelease2/perl-modules_5.8.8-7build1_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/perl-modules_5.8.7-10ubuntu1_all.deb !
 ! Package procps (filename eigenrelease2/procps_1%3a3.2.7-3ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/procps_1%3a3.2.6-2ubuntu4_i386.deb !
 ! Package python (filename eigenrelease2/python_2.5.1~rc1-0ubuntu3_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/python_2.4.2-0ubuntu3_all.deb !
 ! Package python-minimal (filename eigenrelease2/python-minimal_2.5.1~rc1-0ubuntu3_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/python-minimal_2.4.2-0ubuntu3_all.deb !
 ! Package readline-common (filename eigenrelease2/readline-common_5.2-2ubuntu1_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/readline-common_5.1-7build1_all.deb !
 ! Package sed (filename eigenrelease2/sed_4.1.5-1_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/sed_4.1.4-5_i386.deb !
 ! Package sudo (filename eigenrelease2/sudo_1.6.8p12-4ubuntu5_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/sudo_1.6.8p12-1ubuntu6_i386.deb !
 ! Package sysklogd (filename eigenrelease2/sysklogd_1.4.1-20ubuntu4_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/sysklogd_1.4.1-17ubuntu7_i386.deb !
 ! Package sysv-rc (filename eigenrelease2/sysv-rc_2.86.ds1-14.1ubuntu18_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/sysv-rc_2.86.ds1-6ubuntu32_all.deb !
 ! Package tar (filename eigenrelease2/tar_1.16-2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/tar_1.15.1-2ubuntu2_i386.deb !
 ! Package tzdata (filename eigenrelease2/tzdata_2007e-0ubuntu0.7.04_all.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/tzdata_2007b-0ubuntu1_all.deb !
 ! Package ubuntu-minimal (filename eigenrelease2/ubuntu-minimal_1.43_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/ubuntu-minimal_0.120_i386.deb !
 ! Package udev (filename eigenrelease2/udev_108-0ubuntu4_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/udev_079-0ubuntu34_i386.deb !
 ! Package usbutils (filename eigenrelease2/usbutils_0.72-7ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/usbutils_0.71+cvs20051029-4ubuntu1_i386.deb !
 ! Package util-linux (filename eigenrelease2/util-linux_2.12r-17ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/util-linux_2.12r-4ubuntu6_i386.deb !
 ! Package vim-common (filename eigenrelease2/vim-common_1%3a7.0-164+1ubuntu7_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/vim-common_1%3a6.4-006+2ubuntu6_i386.deb !
 ! Package whiptail (filename eigenrelease2/whiptail_0.52.2-8ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/whiptail_0.51.6-31ubuntu1_i386.deb !
 ! Package wireless-tools (filename eigenrelease2/wireless-tools_28-1ubuntu3_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/wireless-tools_27+28pre13-1ubuntu2_i386.deb !
 ! Package wpasupplicant (filename eigenrelease2/wpasupplicant_0.5.7-0ubuntu2_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/wpasupplicant_0.4.8-3ubuntu1.1_i386.deb !
 ! Package zlib1g (filename eigenrelease2/zlib1g_1%3a1.2.3-13ubuntu4_i386.deb) is repeat but newer version;
   used that one and ignored data from eigenrelease2/zlib1g_1%3a1.2.3-6ubuntu4_i386.deb !
 ** Packages in archive but missing from override file: **
  adduser alsa-base alsa-utils alsamixergui apport apport-gtk appres
  apt apt-file apt-utils aptitude aspell aspell-de aspell-en aspell-fr
  aspell-nl autofs base-files base-passwd bash beforelight belocs-
  locales-bin bitmap bsdutils busybox-initramfs bzip2 capplets-data
  compressor console-common console-data console-setup console-
  terminus console-tools coreutils cpio dash dbus debconf debconf-i18n
  debconf-utils debianutils defoma dhcp3-client dhcp3-common
  dictionaries-common diff discover1 discover1-data djmatic-checkdpkg
  djmatic-data djmatic-gui djmatic-gui-doc djmatic-help djmatic-
  keyring djmatic-theme-brown djmatic-theme-lounge djmatic-theme-metal
  djmatic-theme-purple djmatic-theme-woodstock djmatic-tools djmatic-
  videoconfig dmidecode dmsetup docbook-xml dosfstools dpkg dselect
  e2fslibs e2fsprogs editres eject elo-calibrate ethtool findutils
  fontconfig freeglut3 fstobdf gamin gcc-4.0-base gcc-4.1-base gconf2
  gconf2-common gdm gettext-base gimp-help-common gimp-help-de gimp-
  help-en gimp-help-fr gimp-help-nl gksu gnome-control-center gnome-
  keyring gnome-mime-data gnome-panel gnome-panel-data gnupg gpgv grep
  grepmap gstreamer0.8-alsa gstreamer0.8-mad gstreamer0.8-misc gtk2-
  engines-ubuntulooks gzip hal hicolor-icon-theme hostname iceauth ico
  ifupdown imake ingerman initramfs-tools initscripts iogerman iproute
  iputils-ping ispell jfsutils klibc-utils klogd language-pack-de
  language-pack-de-base language-pack-en language-pack-en-base
  language-pack-fr language-pack-fr-base language-pack-gnome-de
  language-pack-gnome-de-base language-pack-gnome-en language-pack-
  gnome-en-base language-pack-gnome-fr language-pack-gnome-fr-base
  language-pack-gnome-nl language-pack-gnome-nl-base language-pack-nl
  language-pack-nl-base language-support-de language-support-en
  language-support-fr language-support-nl laptop-detect less libacl1
  libapt-pkg-perl libart-2.0-2 libasound2 libaspell15 libatk1.0-0
  libatk1.0-data libatm1 libattr1 libaudio-dev libaudio2 libavahi-
  client3 libavahi-common-data libavahi-common3 libavahi-glib1
  libblkid1 libbonobo2-0 libbonobo2-common libbz2-1.0 libc6 libc6-dev
  libc6-i686 libcairo2 libcap1 libcomerr2 libconfig-file-perl
  libconsole libcroco3 libcupsys2-dev libdac2 libdb4.2 libdb4.3
  libdb4.4 libdbus-1-2 libdbus-1-3 libdbus-1-cil libdbus-1-dev
  libdbus-glib-1-2 libdbus-glib-1-dev libdbus-glib-1-doc libdbus-qt-1-
  1c2 libdbus-qt-1-dev libdevmapper1.02 libdiscover1 libdjmessage
  libdmx1 libdrm2 libevent1 libexpat1 libexpat1-dev libfltk1.1
  libfontconfig1 libfontconfig1-dev libfontenc1 libfreetype6
  libfreetype6-dev libfribidi0 libfs6 libft-perl libgamin0 libgcc1
  libgconf2-4 libgcrypt11 libgcrypt11-dev libgcryptobox libgdbm3
  libgksu1.2-1 libgksuui1.0-1 libgl1-mesa libgl1-mesa-dev libgl1-mesa-
  dri libglade2-0 libglib2.0-0 libglib2.0-data libglib2.0-dev libglu1-
  mesa libglu1-mesa-dev libgnome-keyring0 libgnome-window-settings1
  libgnomecanvas2-0 libgnomecanvas2-common libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgnutls-dev libgnutls12
  libgnutls13 libgpg-error-dev libgpg-error0 libgpmg1 libgsf-1-113
  libgsf-1-common libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0
  libgstreamer0.8-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libhal-
  storage1 libhal1 libice-dev libice6 libid3tag0 libidl0 libiw28
  libjpeg62 libjpeg62-dev libklibc liblcms1 liblcms1-dev libldap2
  liblocale-gettext-perl liblzo-dev liblzo1 libmad0 libmng-dev libmng1
  libncurses5 libncursesw5 libnewt0.51 libnewt0.52 libnfsidmap1
  libogg0 liboil0.3 libopencdk8 libopencdk8-dev liborbit2 libpam-
  foreground libpam-modules libpam-runtime libpam0g libpanel-applet2-0
  libpango1.0-0 libpango1.0-common libpci2 libpng12-0 libpng12-dev
  libpopt-dev libpopt0 libqt3-compat-headers libqt3-headers libqt3-mt
  libqt3-mt-dev libreadline5 librsvg2-2 librsvg2-common libsamplerate0
  libsasl2 libsasl2-2 libsasl2-modules libscrollkeeper0 libselinux1
  libsepol1 libshout3 libsigc++-2.0-0c2a libslab0 libslang2 libsm-dev
  libsm6 libsmbclient libsqlite3-0 libss2 libssl0.9.8 libstartup-
  notification0 libstdc++6 libsysfs2 libtasn1-2 libtasn1-3 libtasn1-3-
  dev libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl
  libtheora0 libtiff4 libttf2 libusb-0.1-4 libuuid1 libvolume-id0
  libvorbis0a libwavpack0 libwrap0 libx11-6 libx11-dev libxau-dev
  libxau6 libxaw7 libxcursor-dev libxcursor1 libxdmcp-dev libxdmcp6
  libxext-dev libxext6 libxfixes-dev libxfixes3 libxfont1 libxft-dev
  libxft2 libxi-dev libxi6 libxinerama-dev libxinerama1 libxkbfile1
  libxml2 libxmu-dev libxmu-headers libxmu6 libxmuu1 libxpm4
  libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxslt1.1
  libxss1 libxt-dev libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1
  libxxf86misc1 libxxf86vm1 linux-libc-dev linux-sound-base listres
  locales login lsb-base lsb-release lsof lvm2 makedepend makedev mawk
  mcpp mdetect memtest86+ mesa-common-dev mesa-utils mii-diag mime-
  support mktemp module-init-tools mount mozilla-browser mozilla-
  firefox-locale-de-de mozilla-firefox-locale-en-gb mozilla-firefox-
  locale-fr-fr mozilla-firefox-locale-nl-nl mozilla-psm myspell-de-at
  myspell-de-ch myspell-de-de myspell-en-gb myspell-en-us myspell-fr-
  gut ncurses-base ncurses-bin net-tools netbase netcat nfs-common
  ntpdate obconf oclock openbox openoffice.org-help-de openoffice.org-
  help-en-us openoffice.org-help-fr openoffice.org-help-nl
  openoffice.org-hyphenation-de openoffice.org-l10n-common
  openoffice.org-l10n-de openoffice.org-l10n-en-gb openoffice.org-
  l10n-en-us openoffice.org-l10n-en-za openoffice.org-l10n-fr
  openoffice.org-l10n-nl openoffice.org-thesaurus-de openoffice.org-
  thesaurus-de-ch openoffice.org-thesaurus-en-us passwd pciutils
  pcmciautils perl perl-base perl-doc perl-modules pitch pmount
  portmap procps proengine python python-apport python-minimal python-
  problem-report python2.4 python2.4-minimal python2.5 python2.5-
  minimal qt3-dev-tools rdesktop readline-common reiser4progs
  reiserfsprogs samba scrollkeeper sed sessreg sgml-base sgml-data
  shared-mime-info smbfs smproxy startup-tasks stereo strace sudo
  sysklogd system-services sysv-rc sysvinit sysvutils tar tasksel
  tasksel-data tcpd thunderbird-locale-de thunderbird-locale-en-gb
  thunderbird-locale-fr thunderbird-locale-nl ttf-bitstream-vera ttf-
  dejavu ttf-djmatic ttf-freefont tzdata ubuntu-artwork ubuntu-keyring
  ubuntu-minimal ubuntu-sounds ucf udev update-inetd update-manager
  update-manager-core upstart upstart-compat-sysv upstart-logd
  usbutils util-linux util-linux-locales viewres vim vim-common vim-
  runtime vim-tiny volumeid wamerican wbritish wdutch wfrench whiptail
  wireless-tools wngerman wogerman wpasupplicant wswiss x-ttcidfont-
  conf x11-common x11perf x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-
  render-dev x11proto-xext-dev x11proto-xinerama-dev xauth xbase-
  clients xbiff xcalc xclipboard xclock xconsole xcursorgen xditview
  xdpyinfo xdriinfo xev xeyes xf86dga xfd xfonts-base xfonts-scalable
  xfonts-utils xfontsel xfsprogs xfstt xgamma xgc xhost xinit xkb-data
  xkbutils xkeyboard-config xkill xload xloadimage xlogo xlsatoms
  xlsclients xlsfonts xmag xman xmessage xml-core xmodmap xmore
  xpmutils xprop xrandr xrdb xrefresh xresprobe xrgb xserver-xorg
  xserver-xorg-core xserver-xorg-driver-all xserver-xorg-driver-apm
  xserver-xorg-driver-ark xserver-xorg-driver-ati xserver-xorg-driver-
  chips xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix xserver-
  xorg-driver-dummy xserver-xorg-driver-fbdev xserver-xorg-driver-
  glint xserver-xorg-driver-i128 xserver-xorg-driver-i740 xserver-
  xorg-driver-i810 xserver-xorg-driver-imstt xserver-xorg-driver-mga
  xserver-xorg-driver-neomagic xserver-xorg-driver-newport xserver-
  xorg-driver-nsc xserver-xorg-driver-nv xserver-xorg-driver-rendition
  xserver-xorg-driver-s3 xserver-xorg-driver-s3virge xserver-xorg-
  driver-savage xserver-xorg-driver-siliconmotion xserver-xorg-driver-
  sis xserver-xorg-driver-sisusb xserver-xorg-driver-tdfx xserver-
  xorg-driver-tga xserver-xorg-driver-trident xserver-xorg-driver-
  tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa xserver-xorg-
  driver-vga xserver-xorg-driver-via xserver-xorg-driver-vmware
  xserver-xorg-driver-voodoo xserver-xorg-input-all xserver-xorg-
  input-elographics xserver-xorg-input-evdev xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-wacom xset xsetmode
  xsetpointer xsetroot xsm xstdcmap xterm xtrans-dev xtrap xutils
  xvidtune xvinfo xwd xwininfo xwud zenity zlib1g zlib1g-dev

 Wrote 632 entries to output Packages file.

---

### Post by rai4shu2 on 2007-05-04
Looks to me like warnings. Otherwise, your custom repo looks fine.

---

### Post by byenary on 2007-05-07
[http://ubuntuforums.org/showthread.php?t=435637](http://ubuntuforums.org/showthread.php?t=435637)

---

