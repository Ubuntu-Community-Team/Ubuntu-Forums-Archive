---
title: "g3 ibook - mkisofs problem"
date: 2006-12-07
forum: Apple PPC Users
---

### Post by sweeps63 on 2006-12-07
I'm having problems making an image of my primary partition (/) with mkisofs (had no problem making an image of my home directory).  I'm on a g3 900 ibook with a dapper server install + fluxbox, firefox, etc.  I'm in a bit over my head trying to figure this out but am pretty stubborn.  Here's a copy of my terminal both with and without Rock enabled:

First try at making a bootable copy of my harddrive.

boredom@steW:/lib/udev/devices$ cd /
boredom@steW:/$ sudo mkisofs -r -R -l -o base.iso /
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: Warning: Directory loop 
(/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c dev: 3 ino: 4026532429).
Using POWER000 for  ./rr_moved/power (power)
Using POWER001 for  ./rr_moved/power (power)
Using POWER002 for  ./rr_moved/power (power)
Using POWER003 for  ./rr_moved/power (power)
Using US_ARCHIVE_U000.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_source_Sources 
(us.archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_source_Sources)
Using US_ARCHIVE_U001.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_source_Sources 
(us.archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_source_Sources)
Using US_ARCHIVE_U002.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_source_Sources 
(us.archive.ubuntu.com_ubuntu_dists_dapper-backports_main_source_Sources)
Using US_ARCHIVE_U003.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-backports_main_source_Sources 
(us.archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-powerpc_Packages)
Using US_ARCHIVE_U004.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-powerpc_Packages 
(us.archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-powerpc_Packages)
Using US_ARCHIVE_U005.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-powerpc_Packages 
(us.archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-powerpc_Packages)
Using US_ARCHIVE_U006.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-powerpc_Packages 
(us.archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-powerpc_Packages)
Using US_ARCHIVE_U007.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-powerpc_Packages 
(us.archive.ubuntu.com_ubuntu_dists_dapper_universe_source_Sources)
Using US_ARCHIVE_U008.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_source_Sources 
(us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-powerpc_Packages)
Using US_ARCHIVE_U009.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-powerpc_Packages 
(us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_source_Sources)
Using US_ARCHIVE_U00A.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_source_Sources 
(us.archive.ubuntu.com_ubuntu_dists_dapper_main_source_Sources)
Using US_ARCHIVE_U00B.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_main_source_Sources 
(us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-powerpc_Packages)
Using US_ARCHIVE_U00C.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-powerpc_Packages 
(us.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-powerpc_Packages)
Using SECURITY_UBU000.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_source_Sources 
(security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-powerpc_Packages)
Using SECURITY_UBU001.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-powerpc_Packages 
(security.ubuntu.com_ubuntu_dists_dapper-security_restricted_source_Sources)
Using SECURITY_UBU002.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_source_Sources 
(security.ubuntu.com_ubuntu_dists_dapper-security_main_source_Sources)
Using SECURITY_UBU003.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_source_Sources 
(security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-powerpc_Packages)
Using SECURITY_UBU004.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-powerpc_Packages 
(security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-powerpc_Packages)
Using SECURITY_UBU005.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-powerpc_Packages 
(security.ubuntu.com_ubuntu_dists_dapper-security_Release)
Using US_ARCHIVE_U00D.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-powerpc_Packages 
(us.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_source_Sources)
Using US_ARCHIVE_U00E.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_source_Sources 
(us.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_source_Sources)
Using US_ARCHIVE_U00F.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_source_Sources 
(us.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-powerpc_Packages)
Using US_ARCHIVE_U00G.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-powerpc_Packages 
(us.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-powerpc_Packages)
Using US_ARCHIVE_U00H.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-powerpc_Packages 
(us.archive.ubuntu.com_ubuntu_dists_dapper-backports_Release)
Using US_ARCHIVE_U00I.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-backports_Release 
(us.archive.ubuntu.com_ubuntu_dists_dapper-updates_Release)
Using US_ARCHIVE_UBUNTU_COM_UB000.GPG;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-backports_Release.gpg 
(us.archive.ubuntu.com_ubuntu_dists_dapper-updates_Release.gpg)
Using UBUNTU_SERVE000.06_20_5FDAPPER_;1 for  
/var/lib/apt/lists/Ubuntu-Server%206.06%20%5fDapper%20Drake%5f%20-%20Release%20powerpc%20(20060531)_dists_dapper_restricted_binary-powerpc_Packages 
(Ubuntu-Server%206.06%20%5fDapper%20Drake%5f%20-%20Release%20powerpc%20(20060531)_dists_dapper_main_binary-powerpc_Packages)
Using US_ARCHIVE_UBUNTU_COM_UB001.GPG;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-updates_Release.gpg 
(us.archive.ubuntu.com_ubuntu_dists_dapper_Release.gpg)
Using UBUNTU_SERVE001.06_20_5FDAPPER_;1 for  
/var/lib/apt/lists/Ubuntu-Server%206.06%20%5fDapper%20Drake%5f%20-%20Release%20powerpc%20(20060531)_dists_dapper_main_binary-powerpc_Packages 
(Ubuntu-Server%206.06%20%5fDapper%20Drake%5f%20-%20Release%20powerpc%20(20060531)_dists_dapper_Release)
Using US_ARCHIVE_U00J.COM_UBUNTU_DIST;1 for  
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-updates_Release 
(us.archive.ubuntu.com_ubuntu_dists_dapper_Release)
Using XSERVER_XORG_DRIVER_000.MD5SUMS;1 for  
/var/lib/dpkg/info/xserver-xorg-driver-sisusb.md5sums (xserver-xorg-driver-sis.md5sums)
Using LINUX_RESTRICTED_MOD000.MD5SUMS;1 for  
/var/lib/dpkg/info/linux-restricted-modules-powerpc.md5sums 
(linux-restricted-modules-common.md5sums)
Using BITSTREAM_VERA_SANS_MONO000.TTF;1 for  
/var/lib/defoma/fontconfig.d/B/Bitstream-Vera-Sans-Mono-Bold-Oblique.ttf 
(Bitstream-Vera-Sans-Mono-Bold.ttf)
Using DEJAVU_SERIF_CONDENSED_B000.TTF;1 for  
/var/lib/defoma/fontconfig.d/D/DejaVu-Serif-Condensed-Bold.ttf 
(DejaVu-Serif-Condensed-Bold-Oblique.ttf)
Using IPT_TTL000.KO;1 for  
/lib/modules/2.6.15-23-powerpc/kernel/net/ipv4/netfilter/ipt_ttl.ko (ipt_TTL.ko)
Using IPT_TOS000.KO;1 for  
/lib/modules/2.6.15-23-powerpc/kernel/net/ipv4/netfilter/ipt_tos.ko (ipt_TOS.ko)
Using IPT_TCPMSS000.KO;1 for  
/lib/modules/2.6.15-23-powerpc/kernel/net/ipv4/netfilter/ipt_tcpmss.ko (ipt_TCPMSS.ko)
Using IPT_MARK000.KO;1 for  
/lib/modules/2.6.15-23-powerpc/kernel/net/ipv4/netfilter/ipt_mark.ko (ipt_MARK.ko)
Using IPT_ECN000.KO;1 for  
/lib/modules/2.6.15-23-powerpc/kernel/net/ipv4/netfilter/ipt_ecn.ko (ipt_ECN.ko)
Using IPT_DSCP000.KO;1 for  
/lib/modules/2.6.15-23-powerpc/kernel/net/ipv4/netfilter/ipt_dscp.ko (ipt_DSCP.ko)
Using IPT_CONNMARK000.KO;1 for  
/lib/modules/2.6.15-23-powerpc/kernel/net/ipv4/netfilter/ipt_connmark.ko (ipt_CONNMARK.ko)
Using IP6T_MARK000.KO;1 for  
/lib/modules/2.6.15-23-powerpc/kernel/net/ipv6/netfilter/ip6t_mark.ko (ip6t_MARK.ko)
Using IP6T_HL000.KO;1 for  
/lib/modules/2.6.15-23-powerpc/kernel/net/ipv6/netfilter/ip6t_hl.ko (ip6t_HL.ko)
Using LIBIP6T_MARK000.SO;1 for  /lib/iptables/libip6t_MARK.so (libip6t_mark.so)
Using LIBIP6T_HL000.SO;1 for  /lib/iptables/libip6t_HL.so (libip6t_hl.so)
Using LIBIPT_TTL000.SO;1 for  /lib/iptables/libipt_TTL.so (libipt_ttl.so)
Using LIBIPT_TOS000.SO;1 for  /lib/iptables/libipt_TOS.so (libipt_tos.so)
Using LIBIPT_TCPMSS000.SO;1 for  /lib/iptables/libipt_TCPMSS.so (libipt_tcpmss.so)
Using LIBIPT_MARK000.SO;1 for  /lib/iptables/libipt_MARK.so (libipt_mark.so)
Using LIBIPT_ECN000.SO;1 for  /lib/iptables/libipt_ECN.so (libipt_ecn.so)
Using LIBIPT_DSCP000.SO;1 for  /lib/iptables/libipt_DSCP.so (libipt_dscp.so)
Using LIBIPT_CONNMARK000.SO;1 for  /lib/iptables/libipt_CONNMARK.so (libipt_connmark.so)
Using CHANGELOG000.GZ;1 for  /usr/share/doc/yaboot/ChangeLog.gz (changelog.gz)
Using CHANGELOG000.GZ;1 for  /usr/share/doc/libfreetype6/ChangeLog.gz (changelog.gz)
Using GNOME_VFS_20_GNOME_VFS_000.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-volume.html 
(gnome-vfs-20-gnome-vfs-volume-monitor.html)
Using GNOME_VFS_20_GNOME_VFS_001.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-socket.html 
(gnome-vfs-20-gnome-vfs-socket-buffer.html)
Using GNOME_VFS_20_GNOME_VFS_002.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-result.html 
(gnome-vfs-20-gnome-vfs-resolve.html)
Using GNOME_VFS_20_GNOME_VFS_003.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-module.html 
(gnome-vfs-20-gnome-vfs-module-shared.html)
Using GNOME_VFS_20_GNOME_VFS_004.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-module-shared.html 
(gnome-vfs-20-gnome-vfs-module-callback-module-api.html)
Using GNOME_VFS_20_GNOME_VFS_005.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-module-callback-module-api.html 
(gnome-vfs-20-gnome-vfs-module-callback.html)
Using GNOME_VFS_20_GNOME_VFS_006.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-mime.html 
(gnome-vfs-20-gnome-vfs-mime-monitor.html)
Using GNOME_VFS_20_GNOME_VFS_007.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-mime-monitor.html 
(gnome-vfs-20-gnome-vfs-mime-database.html)
Using GNOME_VFS_20_GNOME_VFS_008.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-file-trunc-ops.html 
(gnome-vfs-20-gnome-vfs-file-size.html)
Using GNOME_VFS_20_GNOME_VFS_009.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-file-size.html 
(gnome-vfs-20-gnome-vfs-file-rw-ops.html)
Using GNOME_VFS_20_GNOME_VFS_00A.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-file-rw-ops.html 
(gnome-vfs-20-gnome-vfs-file-info.html)
Using GNOME_VFS_20_GNOME_VFS_00B.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-file-info.html 
(gnome-vfs-20-gnome-vfs-file-info-ops.html)
Using GNOME_VFS_20_GNOME_VFS_00C.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-file-info-ops.html 
(gnome-vfs-20-gnome-vfs-file-basic-ops.html)
Using GNOME_VFS_20_GNOME_VFS_00D.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-file-basic-ops.html 
(gnome-vfs-20-gnome-vfs-file-advanced-ops.html)
Using GNOME_VFS_20_GNOME_VFS_00E.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-directory-list-ops.html 
(gnome-vfs-20-gnome-vfs-directory-find-ops.html)
Using GNOME_VFS_20_GNOME_VFS_00F.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-directory-find-ops.html 
(gnome-vfs-20-gnome-vfs-directory-basic-ops.html)
Using GNOME_VFS_20_GNOME_VFS_00G.HTML;1 for  
/usr/share/doc/libgnomevfs2-common/html/gnome-vfs-20-gnome-vfs-mime-database.html 
(gnome-vfs-20-gnome-vfs-mime-database-deprecated.html)
Using CHANGELOG000.GZ;1 for  /usr/share/doc/discover1/ChangeLog.gz (changelog.gz)
Using ISO_8859_9_7000.GZ;1 for  /usr/share/man/man7/iso_8859_9.7.gz (iso-8859-9.7.gz)
Using ISO_8859_7_7000.GZ;1 for  /usr/share/man/man7/iso_8859_7.7.gz (iso-8859-7.7.gz)
Using ISO_8859_2_7000.GZ;1 for  /usr/share/man/man7/iso_8859_2.7.gz (iso-8859-2.7.gz)
Using ISO_8859_16_7000.GZ;1 for  /usr/share/man/man7/iso_8859_16.7.gz (iso-8859-16.7.gz)
Using ISO_8859_15_7000.GZ;1 for  /usr/share/man/man7/iso_8859_15.7.gz (iso-8859-15.7.gz)
Using ISO_8859_1_7000.GZ;1 for  /usr/share/man/man7/iso_8859_1.7.gz (iso-8859-1.7.gz)
Using ISO_8859_1_7001.GZ;1 for  /usr/share/man/man7/iso-8859-1.7.gz (iso_8859-1.7.gz)
Using ISO_8859_15_7001.GZ;1 for  /usr/share/man/man7/iso-8859-15.7.gz (iso_8859-15.7.gz)
Using ISO_8859_9_7001.GZ;1 for  /usr/share/man/man7/iso-8859-9.7.gz (iso_8859-9.7.gz)
Using ISO_8859_7_7001.GZ;1 for  /usr/share/man/man7/iso-8859-7.7.gz (iso_8859-7.7.gz)
Using ISO_8859_2_7001.GZ;1 for  /usr/share/man/man7/iso-8859-2.7.gz (iso_8859-2.7.gz)
Using ISO_8859_16_7001.GZ;1 for  /usr/share/man/man7/iso-8859-16.7.gz (iso_8859-16.7.gz)
Using TTYS_4000.GZ;1 for  /usr/share/man/man4/ttys.4.gz (ttyS.4.gz)
Using GMT_0000.;1 for  /usr/share/zoneinfo/GMT-0 (GMT+0)
Using GMT_0000.;1 for  /usr/share/zoneinfo/Etc/GMT+0 (GMT-0)
Using GMT_1000.;1 for  /usr/share/zoneinfo/Etc/GMT+1 (GMT-1)
Using GMT_2000.;1 for  /usr/share/zoneinfo/Etc/GMT+2 (GMT-2)
Using GMT_3000.;1 for  /usr/share/zoneinfo/Etc/GMT+3 (GMT-3)
Using GMT_4000.;1 for  /usr/share/zoneinfo/Etc/GMT+4 (GMT-4)
Using GMT_5000.;1 for  /usr/share/zoneinfo/Etc/GMT+5 (GMT-5)
Using GMT_6000.;1 for  /usr/share/zoneinfo/Etc/GMT+6 (GMT-6)
Using GMT_7000.;1 for  /usr/share/zoneinfo/Etc/GMT+7 (GMT-7)
Using GMT_8000.;1 for  /usr/share/zoneinfo/Etc/GMT+8 (GMT-8)
Using GMT_9000.;1 for  /usr/share/zoneinfo/Etc/GMT+9 (GMT-9)
Using GMT_10000.;1 for  /usr/share/zoneinfo/Etc/GMT+10 (GMT-10)
Using GMT_11000.;1 for  /usr/share/zoneinfo/Etc/GMT+11 (GMT-11)
Using GMT_12000.;1 for  /usr/share/zoneinfo/Etc/GMT+12 (GMT-12)
Using GMT_0000.;1 for  /usr/share/zoneinfo/posix/GMT-0 (GMT+0)
Using GMT_0000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+0 (GMT-0)
Using GMT_1000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+1 (GMT-1)
Using GMT_2000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+2 (GMT-2)
Using GMT_3000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+3 (GMT-3)
Using GMT_4000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+4 (GMT-4)
Using GMT_5000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+5 (GMT-5)
Using GMT_6000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+6 (GMT-6)
Using GMT_7000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+7 (GMT-7)
Using GMT_8000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+8 (GMT-8)
Using GMT_9000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+9 (GMT-9)
Using GMT_10000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+10 (GMT-10)
Using GMT_11000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+11 (GMT-11)
Using GMT_12000.;1 for  /usr/share/zoneinfo/posix/Etc/GMT+12 (GMT-12)
Using GMT_0000.;1 for  /usr/share/zoneinfo/right/GMT-0 (GMT+0)
Using GMT_0000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+0 (GMT-0)
Using GMT_1000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+1 (GMT-1)
Using GMT_2000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+2 (GMT-2)
Using GMT_3000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+3 (GMT-3)
Using GMT_4000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+4 (GMT-4)
Using GMT_5000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+5 (GMT-5)
Using GMT_6000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+6 (GMT-6)
Using GMT_7000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+7 (GMT-7)
Using GMT_8000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+8 (GMT-8)
Using GMT_9000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+9 (GMT-9)
Using GMT_10000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+10 (GMT-10)
Using GMT_11000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+11 (GMT-11)
Using GMT_12000.;1 for  /usr/share/zoneinfo/right/Etc/GMT+12 (GMT-12)
Using POD000 for  /usr/share/perl/5.8.7/pod (Pod)
Using MENU_CZECH_CZECH_REPUBLI000.VIM;1 for  
/usr/share/vim/vim64/lang/menu_czech_czech_republic.1252.vim 
(menu_czech_czech_republic.1250.vim)
Using MENU_ENGLISH_UNITED_KINGD000.VI;1 for  
/usr/share/vim/vim64/lang/menu_english_united_kingdom.ascii.vim 
(menu_english_united_kingdom.1252.vim)
Using LIBBONOBO_BONOBO_PROPER000.HTML;1 for  
/usr/share/gtk-doc/html/libbonobo/libbonobo-bonobo-property-bag.html 
(libbonobo-bonobo-property-bag-client.html)
Using LIBBONOBOUI_BONOBO_SELE000.HTML;1 for  
/usr/share/gtk-doc/html/libbonoboui/libbonoboui-bonobo-selector.html 
(libbonoboui-bonobo-selector-widget.html)
Using LIBBONOBOUI_BONOBO_UI_E000.HTML;1 for  
/usr/share/gtk-doc/html/libbonoboui/libbonoboui-bonobo-ui-engine.html 
(libbonoboui-bonobo-ui-engine-config.html)
Using LIBBONOBOUI_BONOBO_CONT000.HTML;1 for  
/usr/share/gtk-doc/html/libbonoboui/libbonoboui-bonobo-control.html 
(libbonoboui-bonobo-control-frame.html)
Using DESKTOP_GNOME_PERIPH000.SCHEMAS;1 for  
/usr/share/gconf/schemas/desktop_gnome_peripherals_mouse.schemas 
(desktop_gnome_peripherals_keyboard.schemas)
Using DESKTOP_GNOME_APPLIC000.SCHEMAS;1 for  
/usr/share/gconf/schemas/desktop_gnome_applications_terminal.schemas 
(desktop_gnome_applications_window_manager.schemas)
Using DESKTOP_GNOME_APPLIC001.SCHEMAS;1 for  
/usr/share/gconf/schemas/desktop_gnome_applications_window_manager.schemas 
(desktop_gnome_applications_browser.schemas)
Using DESKTOP_GNOME_APPLIC002.SCHEMAS;1 for  
/usr/share/gconf/schemas/desktop_gnome_applications_browser.schemas 
(desktop_gnome_applications_help_viewer.schemas)
Using DESKTOP_GNOME_ACCESS000.SCHEMAS;1 for  
/usr/share/gconf/schemas/desktop_gnome_accessibility_startup.schemas 
(desktop_gnome_accessibility_keyboard.schemas)
Using VND_OASIS_OPENDOCUMENT_P000.XML;1 for  
/usr/share/mime/application/vnd.oasis.opendocument.presentation.xml 
(vnd.oasis.opendocument.presentation-template.xml)
Using VND_OASIS_OPENDOCUMENT_S000.XML;1 for  
/usr/share/mime/application/vnd.oasis.opendocument.spreadsheet.xml 
(vnd.oasis.opendocument.spreadsheet-template.xml)
Using VND_OASIS_OPENDOCUMENT_T000.XML;1 for  
/usr/share/mime/application/vnd.oasis.opendocument.text-template.xml 
(vnd.oasis.opendocument.text-master.xml)
Using VND_OASIS_OPENDOCUMENT_T001.XML;1 for  
/usr/share/mime/application/vnd.oasis.opendocument.text-master.xml 
(vnd.oasis.opendocument.text.xml)
Using VND_OASIS_OPENDOCUMENT_G000.XML;1 for  
/usr/share/mime/application/vnd.oasis.opendocument.graphics.xml 
(vnd.oasis.opendocument.graphics-template.xml)
Using VND_OASIS_OPENDOCUMENT_T002.XML;1 for  
/usr/share/mime/application/vnd.oasis.opendocument.text.xml 
(vnd.oasis.opendocument.text-web.xml)
Using EXO_PREFERRED_APPLICATIO000.PNG;1 for  
/usr/share/xfce4/doc/C/images/exo-preferred-applications-webbrowser-menu.png 
(exo-preferred-applications-webbrowser-custom.png)
Using EXO_PREFERRED_APPLICATIO001.PNG;1 for  
/usr/share/xfce4/doc/C/images/exo-preferred-applications-webbrowser-custom.png 
(exo-preferred-applications-internet.png)
Using EXO_PREFERRED_APPLICATIO002.PNG;1 for  
/usr/share/xfce4/doc/C/images/exo-preferred-applications-internet.png 
(exo-preferred-applications-utilities.png)
Using EXO_PREFERRED_APPLICATIO000.PNG;1 for  
/usr/share/xfce4/doc/ja/images/exo-preferred-applications-webbrowser-menu.png 
(exo-preferred-applications-webbrowser-custom.png)
Using EXO_PREFERRED_APPLICATIO001.PNG;1 for  
/usr/share/xfce4/doc/ja/images/exo-preferred-applications-webbrowser-custom.png 
(exo-preferred-applications-internet.png)
Using EXO_PREFERRED_APPLICATIO002.PNG;1 for  
/usr/share/xfce4/doc/ja/images/exo-preferred-applications-internet.png 
(exo-preferred-applications-utilities.png)
Using SYS000 for  /usr/lib/perl/5.8.7/sys (Sys)
Using TTYS0000.;1 for  /dev/ttyS0 (ttys0)
Using TTYS1000.;1 for  /dev/ttyS1 (ttys1)
Using TTYS2000.;1 for  /dev/ttyS2 (ttys2)
Using TTYS3000.;1 for  /dev/ttyS3 (ttys3)
Using TTYS4000.;1 for  /dev/ttyS4 (ttys4)
Using TTYS5000.;1 for  /dev/ttyS5 (ttys5)
Using TTYS6000.;1 for  /dev/ttyS6 (ttys6)
Using TTYS7000.;1 for  /dev/ttyS7 (ttys7)
Using TTYS8000.;1 for  /dev/ttyS8 (ttys8)
Using TTYS9000.;1 for  /dev/ttyS9 (ttys9)
Using TTYS4000.;1 for  /dev/.static/dev/ttyS4 (ttys4)
Using TTYS3000.;1 for  /dev/.static/dev/ttyS3 (ttys3)
Using TTYS2000.;1 for  /dev/.static/dev/ttyS2 (ttys2)
Using TTYS1000.;1 for  /dev/.static/dev/ttyS1 (ttys1)
Using TTYS0000.;1 for  /dev/.static/dev/ttyS0 (ttys0)
Using ATA_TOSHIBA_MK4025GAS_X3R89000.;1 for  
/dev/disk/by-id/ata-TOSHIBA_MK4025GAS_X3R89140S (ata-TOSHIBA_MK4025GAS_X3R89140S-part1)
Using ATA_TOSHIBA_MK4025GAS_X3R89001.;1 for  
/dev/disk/by-id/ata-TOSHIBA_MK4025GAS_X3R89140S-part1 
(ata-TOSHIBA_MK4025GAS_X3R89140S-part4)
Using ATA_TOSHIBA_MK4025GAS_X3R89002.;1 for  
/dev/disk/by-id/ata-TOSHIBA_MK4025GAS_X3R89140S-part4 
(ata-TOSHIBA_MK4025GAS_X3R89140S-part3)
Using ATA_TOSHIBA_MK4025GAS_X3R89003.;1 for  
/dev/disk/by-id/ata-TOSHIBA_MK4025GAS_X3R89140S-part3 
(ata-TOSHIBA_MK4025GAS_X3R89140S-part2)
Using DEVICE_TYPE000.;1 for  
/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/device_type (device_type)
Using AUDIO_GPIO000.;1 for  
/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/audio-gpio (audio-gpio)
Using AUDIO_GPIO_ACTIVE_STATE000.;1 for  
/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/audio-gpio-active-state 
(audio-gpio-active-state)
Using BUILT_IN000.;1 for  
/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/built-in (built-in)
Using REG000.;1 for  /proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/reg 
(reg)
Using AAPL_ADDRESS000.;1 for  
/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/AAPL,address 
(AAPL,address)
Using INTERRUPTS000.;1 for  
/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/interrupts (interrupts)
Using INTERRUPT_PARENT000.;1 for  
/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/interrupt-parent 
(interrupt-parent)
Using LINUX_PHANDLE000.;1 for  
/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/linux,phandle 
(linux,phandle)
Using NAME000.;1 for  /proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/name 
(name)
mkisofs: Error: 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/device_type' and 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/device_type' have the 
same Rock Ridge name 'device_type'.
mkisofs: Error: 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/AAPL,address' and 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/AAPL,address' have the 
same Rock Ridge name 'AAPL,address'.
mkisofs: Error: 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/audio-gpio' and 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/audio-gpio' have the same 
Rock Ridge name 'audio-gpio'.
mkisofs: Error: 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/audio-gpio-active-state' 
and 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/audio-gpio-active-state' 
have the same Rock Ridge name 'audio-gpio-active-state'.
mkisofs: Error: '/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/built-in' 
and '/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/built-in' have the 
same Rock Ridge name 'built-in'.
mkisofs: Error: 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/interrupts' and 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/interrupts' have the same 
Rock Ridge name 'interrupts'.
mkisofs: Error: 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/interrupt-parent' and 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/interrupt-parent' have 
the same Rock Ridge name 'interrupt-parent'.
mkisofs: Error: 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/linux,phandle' and 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/linux,phandle' have the 
same Rock Ridge name 'linux,phandle'.
mkisofs: Error: '/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/name' and 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/name' have the same Rock 
Ridge name 'name'.
mkisofs: Error: '/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/reg' and 
'/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c/reg' have the same Rock 
Ridge name 'reg'.mkisofs: Unable to sort directory 
/proc/device-tree/pci@f2000000/mac-io@17/gpio@50/extint-gpio4@5c



2nd try without Rock. 

  1.36% done, estimate finish Thu Dec  7 14:37:58 2006
  2.73% done, estimate finish Thu Dec  7 14:38:35 2006
  4.09% done, estimate finish Thu Dec  7 14:38:23 2006
  5.45% done, estimate finish Thu Dec  7 14:40:07 2006
  6.81% done, estimate finish Thu Dec  7 14:40:40 2006
  8.18% done, estimate finish Thu Dec  7 14:40:37 2006
  9.54% done, estimate finish Thu Dec  7 14:40:25 2006
 10.90% done, estimate finish Thu Dec  7 14:40:25 2006
 12.26% done, estimate finish Thu Dec  7 14:40:25 2006
 13.63% done, estimate finish Thu Dec  7 14:40:25 2006
mkisofs: Operation not permitted. cannot open '/lib/udev/devices/core'

Permissions are ok on file.  Tried to open and permission was denied

---

