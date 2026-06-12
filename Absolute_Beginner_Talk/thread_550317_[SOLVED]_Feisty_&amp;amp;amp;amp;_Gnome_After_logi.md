---
title: "[SOLVED] Feisty &amp;amp;amp;amp; Gnome: After login - instant forced logout"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by OliverN on 2007-09-13
SO

I've been messing a bit with themes lately (mostly login- and splash screens), and now if I run gnome like normal I'm automatically logged out again as soon as I log in.
I usually get to the point in which I see my wallpaper and my wireless network prompts me for password, but then - login screen again.

Can anybody help? I figure I might need to post some outputs of sorts so just tell me which :)
Gnome runs ''fine'' in safe mode, only my window manager doesn't load properly.

EDIT;

my x-session

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "oliver"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Profeten:/tmp/.ICE-unix/8310
Initializing gnome-mount extension
/usr/local/bin/start_beryl.sh: Error: beryl-manager not launched. Xgl not running?
unclutter: usage:
	-display <display>
	-idle <seconds>		time between polls to detect idleness.
	-keystroke		wait for keystroke before idling.
	-jitter <pixels>	pixels mouse can twitch without moving
	-grab			use grabpointer method not createwindow
	-reset			reset the timer whenever cursor becomes
					visible even if it hasn't moved
 	-root	       		apply to cursor on root window too
	-onescreen		apply only to given screen of display
 	-visible       		ignore visibility events
 	-noevents      		don't send pseudo events
	-regex			name or class below is a regular expression
	-not names...		don't apply to windows whose wm-name begins.
				(must be last argument)
	-notname names...	same as -not names...
	-notclass classes...    don't apply to windows whose wm-class begins.
				(must be last argument, cannot be used with
				-not or -notname)
*** glibc detected *** x-session-manager: malloc(): memory corruption: 0x0825fa08 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7626ef3]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb762860e]
/usr/lib/libSM.so.6(_SmsProcessMessage+0xd1c)[0xb7eba5fc]
/usr/lib/libICE.so.6(IceProcessMessages+0x311)[0xb7eaeef1]
/usr/lib/libgnomeui-2.so.0[0xb7f01605]
/usr/lib/libglib-2.0.so.0[0xb776040d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7736df2]
/usr/lib/libglib-2.0.so.0[0xb7739dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb773a179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c6f044]
x-session-manager(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75d4ebc]
x-session-manager[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:11 6275524    /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:11 6275524    /usr/bin/gnome-session
08069000-0829a000 rw-p 08069000 00:00 0          [heap]
b3b00000-b3b21000 rw-p b3b00000 00:00 0 
b3b21000-b3c00000 ---p b3b21000 00:00 0 
b3ca3000-b3cae000 r-xp 00000000 08:11 6651968    /lib/libgcc_s.so.1
b3cae000-b3caf000 rw-p 0000a000 08:11 6651968    /lib/libgcc_s.so.1
b3cc1000-b3d21000 rw-s 00000000 00:08 2195460    /SYSV00000000 (deleted)
b3d21000-b3d22000 ---p b3d21000 00:00 0 
b3d22000-b4522000 rw-p b3d22000 00:00 0 
b4522000-b459f000 r--p 00000000 08:11 6537348    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b459f000-b45a1000 r-xp 00000000 08:11 6373933    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b45a1000-b45a2000 rw-p 00001000 08:11 6373933    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b45a2000-b45a5000 r--s 00000000 08:11 5456824    /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b45a5000-b45ab000 r--s 00000000 08:11 5456632    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b45ab000-b45ac000 r--s 00000000 08:11 5456821    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b45ac000-b45af000 r--s 00000000 08:11 5456816    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b45af000-b45b0000 r--s 00000000 08:11 5456815    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b45b0000-b45b1000 r--s 00000000 08:11 5456812    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b45b1000-b45b5000 r--s 00000000 08:11 5455961    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b45b5000-b45b6000 r--s 00000000 08:11 5456810    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b45b6000-b45b8000 r--s 00000000 08:11 5456809    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b45b8000-b45ba000 r--s 00000000 08:11 5456807    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b45ba000-b45bb000 r--s 00000000 08:11 5456806    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b45bb000-b45bd000 r--s 00000000 08:11 5456805    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b45bd000-b45c3000 r--s 00000000 08:11 5456800    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b45c3000-b45c5000 r--s 00000000 08:11 5456791    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b45c5000-b45c7000 r--s 00000000 08:11 5456776    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b45c7000-b45cf000 r--s 00000000 08:11 5456774    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b45cf000-b45d5000 r--s 00000000 08:11 5456773    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b45d5000-b45d6000 r--s 00000000 08:11 5456772    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b45d6000-b45ed000 r--s 00000000 08:11 5456229    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b45ed000-b45ef000 r--s 00000000 08:11 5456771    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b45ef000-b45f5000 r--s 00000000 08:11 5456765    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b45f5000-b45f8000 r--s 00000000 08:11 5456764    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b45f8000-b45fc000 r--s 00000000 08:11 5455946    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b45fc000-b4603000 r--s 00000000 08:11 5456476    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b4603000-b4604000 r--s 00000000 08:11 5456852    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b4604000-b4605000 r--s 00000000 08:11 5456851    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b4605000-b4606000 r--s 00000000 08:11 5456850    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b4606000-b4607000 r--s 00000000 08:11 5456849    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b4607000-b4608000 r--s 00000000 08:11 5456368    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4608000-b460b000 r--s 00000000 08:11 5456847    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b460b000-b4610000 r--s 00000000 08:11 5456365    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b4610000-b4612000 r--s 00000000 08:11 5456845    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b4612000-b4613000 r--s 00000000 08:11 5456844    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b4613000-b4615000 r--s 00000000 08:11 5456843    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b4615000-b4616000 r--s 00000000 08:11 5456842    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b4616000-b461b000 r--s 00000000 08:11 5456841    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b461b000-b461f000 r--s 00000000 08:11 5456840    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b461f000-b4621000 r--s 00000000 08:11 5456839    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b4621000-b4624000 r--s 00000000 08:11 5456838    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b4624000-b4625000 r--s 00000000 08:11 5456837    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b4625000-b4628000 r--s 00000000 08:11 5456836    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b4628000-b462c000 r--s 00000000 08:11 5456362    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b462c000-b4632000 r--s 00000000 08:11 5456834    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b4632000-b463a000 r--s 00000000 08:11 5456832    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b463a000-b463c000 r--s 00000000 08:11 5456360    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b463c000-b463f000 r--s 00000000 08:11 5456830    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b463f000-b4646000 r--s 00000000 08:11 5456472    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b4646000-b48fd000 r--p 00000000 08:11 6705629    /usr/share/icons/hicolor/icon-theme.cache
b48fd000-b617f000 r--p 00000000 08:11 6883026    /usr/share/icons/crystalsvg/icon-theme.cache
b617f000-b6828000 r--p 00000000 08:11 6705472    /usr/share/icons/gnome/icon-theme.cache
b6828000-b6a7f000 r--p 00000000 08:11 6705414    /usr/share/icons/Tango/icon-theme.cache
b6a7f000-b6b20000 r--p 00000000 08:11 6704450    /usr/share/icons/Tangerine/icon-theme.cache
b6b20000-b6c86000 r--p 00000000 08:11 6702904    /usr/share/icons/Human/icon-theme.cache
b6c86000-b6c98000 r-xp 00000000 08:11 6340977    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6c98000-b6c99000 rw-p 00011000 08:11 6340977    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6c99000-b6cf9000 rw-s 00000000 00:08 2162691    /SYSV00000000 (deleted)
b6cf9000-b6d61000 rw-p b6cf9000 00:00 0 
b6d61000-b6d65000 r-xp 00000000 08:11 6340997    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6d65000-b6d66000 rw-p 00003000 08:11 6340997    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6d66000-b6d6d000 r-xp 00000000 08:11 6276546    /usr/lib/libfam.so.0.0.0
b6d6d000-b6d6e000 rw-p 00006000 08:11 6276546    /usr/lib/libfam.so.0.0.0
b6d6e000-b6d74000 r-xp 00000000 08:11 6651931    /lib/libacl.so.1.1.0
b6d74000-b6d75000 rw-p 00005000 08:11 6651931    /lib/libacl.so.1.1.0
b6d75000-b6d78000 r-xp 00000000 08:11 6651935    /lib/libattr.so.1.1.0
b6d78000-b6d79000 rw-p 00002000 08:11 6651935    /lib/libattr.so.1.1.0
b6d7b000-b6d7d000 r--s 00000000 08:11 5456358    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6d7d000-b6d82000 r--p 00000000 08:11 6621043    /usr/share/locale-langpack/da/LC_MESSAGES/glib20.mo
b6d82000-b6d89000 r--p 00000000 08:11 6621051    /usr/share/locale-langpack/da/LC_MESSAGES/gnome-vfs-2.0.mo
b6d89000-b6d8b000 r--p 00000000 08:11 6621004    /usr/share/locale-langpack/da/LC_MESSAGES/gnome-desktop-2.0.mo
b6d8b000-b6d97000 r-xp 00000000 08:11 6340920    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6d97000-b6d98000 rw-p 0000b000 08:11 6340920    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6d98000-b6d9f000 r--p 00000000 08:11 6621044    /usr/share/locale-langpack/da/LC_MESSAGES/libgnome-2.0.mo
b6d9f000-b6da2000 r--p 00000000 08:11 6621021    /usr/share/locale-langpack/da/LC_MESSAGES/gnome-session-2.0.mo
b6da2000-b6db1000 r--p 00000000 08:11 6620999    /usr/share/locale-langpack/da/LC_MESSAGES/GConf2.mo
b6db1000-b6db2000 r-xp 00000000 08:11 6308593    /usr/lib/gconv/ISO8859-1.so
b6db2000-b6db4000 rw-p 00000000 08:11 6308593    /usr/lib/gconv/ISO8859-1.so
b6db4000-b6dce000 r--p 00000000 08:11 6621031    /usr/share/locale-langpack/da/LC_MESSAGES/gtk20-properties.mo
b6dce000-b6dd8000 r--p 00000000 08:11 6621030    /usr/share/locale-langpack/da/LC_MESSAGES/gtk20.mo
b6dd8000-b6e13000 r--p 00000000 08:11 6424895    /usr/lib/locale/da_DK.utf8/LC_CTYPE
b6e13000-b6eeb000 r--p 00000000 08:11 6424897    /usr/lib/locale/da_DK.utf8/LC_COLLATE
b6eeb000-b6ef4000 r-xp 00000000 08:11 6685971    /lib/tls/i686/cmov/libnss_files-2.5.so
b6ef4000-b6ef6000 rw-p 00008000 08:11 6685971    /lib/tls/i686/cmov/libnss_files-2.5.so
b6ef6000-b6efe000 r-xp 00000000 08:11 6685975    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6efe000-b6f00000 rw-p 00007000 08:11 6685975    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f00000-b6f07000 r-xp 00000000 08:11 6685967    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f07000-b6f09000 rw-p 00006000 08:11 6685967    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f09000-b6f0c000 rw-p b6f09000 00:00 0 
b6f0c000-b6f42000 r-xp 00000000 08:11 6652022    /lib/libsepol.so.1
b6f42000-b6f43000 rw-p 00035000 08:11 6652022    /lib/libsepol.so.1
b6f43000-b6f4d000 rw-p b6f43000 00:00 0 
b6f4d000-b6f50000 r-xp 00000000 08:11 6276699    /usr/lib/libgpg-error.so.0.3.0
b6f50000-b6f51000 rw-p 00002000 08:11 6276699    /usr/lib/libgpg-error.so.0.3.0
b6f51000-b6fa0000 r-xp 00000000 08:11 6276587    /usr/lib/libgcrypt.so.11.2.2
b6fa0000-b6fa2000 rw-p 0004e000 08:11 6276587    /usr/lib/libgcrypt.so.11.2.2
b6fa2000-b6fa3000 rw-p b6fa2000 00:00 0 
b6fa3000-b6fb7000 r-xp 00000000 08:11 6277043    /usr/lib/libtasn1.so.3.0.6
b6fb7000-b6fb8000 rw-p 00013000 08:11 6277043    /usr/lib/libtasn1.so.3.0.6
b6fb8000-b6fba000 r-xp 00000000 08:11 6685988    /lib/tls/i686/cmov/libutil-2.5.so
b6fba000-b6fbc000 rw-p 00001000 08:11 6685988    /lib/tls/i686/cmov/libutil-2.5.so
b6fbc000-b6fd0000 r-xp 00000000 08:11 6652021    /lib/libselinux.so.1
b6fd0000-b6fd2000 rw-p 00013000 08:11 6652021    /lib/libselinux.so.1
b6fd2000-b6fe1000 r-xp 00000000 08:11 6685982    /lib/tls/i686/cmov/libresolv-2.5.so
b6fe1000-b6fe3000 rw-p 0000f000 08:11 6685982    /lib/tls/i686/cmov/libresolv-2.5.so
b6fe3000-b6fe5000 rw-p b6fe3000 00:00 0 
b6fe5000-b6ff3000 r-xp 00000000 08:11 6276425    /usr/lib/libavahi-client.so.3.2.2
b6ff3000-b6ff4000 rw-p 0000e000 08:11 6276425    /usr/lib/libavahi-client.so.3.2.2
b6ff4000-b6ff5000 rw-p b6ff4000 00:00 0 
b6ff5000-b6fff000 r-xp 00000000 08:11 6276427    /usr/lib/libavahi-common.so.3.4.3
b6fff000-b7000000 rw-p 00009000 08:11 6276427    /usr/lib/libavahi-common.so.3.4.3
b7000000-b7002000 r-xp 00000000 08:11 6276431    /usr/lib/libavahi-glib.so.1.0.1
b7002000-b7003000 rw-p 00001000 08:11 6276431    /usr/lib/libavahi-glib.so.1.0.1
b7003000-b706d000 r-xp 00000000 08:11 6276695    /usr/lib/libgnutls.so.13.0.9
b706d000-b7073000 rw-p 0006a000 08:11 6276695    /usr/lib/libgnutls.so.13.0.9
b7073000-b7095000 r-xp 00000000 08:11 6276514    /usr/lib/libpng12.so.0.15.0
b7095000-b7096000 rw-p 00021000 08:11 6276514    /usr/lib/libpng12.so.0.15.0
b7096000-b70b4000 r-xp 00000000 08:11 6276542    /usr/lib/libexpat.so.1.0.0
b70b4000-b70b6000 rw-p 0001d000 08:11 6276542    /usr/lib/libexpat.so.1.0.0
b70b6000-b70b7000 rw-p b70b6000 00:00 0 
b70b7000-b711f000 r-xp 00000000 08:11 6276512    /usr/lib/libfreetype.so.6.3.10
b711f000-b7122000 rw-p 00068000 08:11 6276512    /usr/lib/libfreetype.so.6.3.10
b7122000-b7135000 r-xp 00000000 08:11 6277101    /usr/lib/libz.so.1.2.3
b7135000-b7136000 rw-p 00012000 08:11 6277101    /usr/lib/libz.so.1.2.3
b7136000-b7149000 r-xp 00000000 08:11 6685965    /lib/tls/i686/cmov/libnsl-2.5.so
b7149000-b714b000 rw-p 00012000 08:11 6685965    /lib/tls/i686/cmov/libnsl-2.5.so
b714b000-b714d000 rw-p b714b000 00:00 0 
b714d000-b7151000 r-xp 00000000 08:11 6276332    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7151000-b7152000 rw-p 00003000 08:11 6276332    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7152000-b7153000 rw-p b7152000 00:00 0 
b7153000-b7157000 r-xp 00000000 08:11 6276357    /usr/lib/libXdmcp.so.6.0.0
b7157000-b7158000 rw-p 00003000 08:11 6276357    /usr/lib/libXdmcp.so.6.0.0
b7158000-b7176000 r-xp 00000000 08:11 6276824    /usr/lib/libjpeg.so.62.0.0
b7176000-b7177000 rw-p 0001d000 08:11 6276824    /usr/lib/libjpeg.so.62.0.0
b7177000-b717f000 r-xp 00000000 08:11 6277033    /usr/lib/libstartup-notification-1.so.0.0.0
b717f000-b7180000 rw-p 00007000 08:11 6277033    /usr/lib/libstartup-notification-1.so.0.0.0
b7180000-b7181000 rw-p b7180000 00:00 0 
b7181000-b7188000 r-xp 00000000 08:11 6685984    /lib/tls/i686/cmov/librt-2.5.so
b7188000-b718a000 rw-p 00006000 08:11 6685984    /lib/tls/i686/cmov/librt-2.5.so
b718a000-b718e000 r-xp 00000000 08:11 6276751    /usr/lib/libgthread-2.0.so.0.1200.11
b718e000-b718f000 rw-p 00003000 08:11 6276751    /usr/lib/libgthread-2.0.so.0.1200.11
b718f000-b7191000 r-xp 00000000 08:11 6685960    /lib/tls/i686/cmov/libdl-2.5.so
b7191000-b7193000 rw-p 00001000 08:11 6685960    /lib/tls/i686/cmov/libdl-2.5.so
b7193000-b7195000 r-xp 00000000 08:11 6276653    /usr/lib/libgmodule-2.0.so.0.1200.11
b7195000-b7196000 rw-p 00002000 08:11 6276653    /usr/lib/libgmodule-2.0.so.0.1200.11
b7196000-b71ec000 r-xp 00000000 08:11 6276687    /usr/lib/libgnomevfs-2.so.0.1800.1
b71ec000-b71ef000 rw-p 00055000 08:11 6276687    /usr/lib/libgnomevfs-2.so.0.1800.1
b71ef000-b725d000 r-xp 00000000 08:11 6276450    /usr/lib/libcairo.so.2.11.1
b725d000-b725f000 rw-p 0006d000 08:11 6276450    /usr/lib/libcairo.so.2.11.1
b725f000-b7260000 rw-p b725f000 00:00 0 
b7260000-b7264000 r-xp 00000000 08:11 6276363    /usr/lib/libXfixes.so.3.1.0
b7264000-b7265000 rw-p 00003000 08:11 6276363    /usr/lib/libXfixes.so.3.1.0
b7265000-b726d000 r-xp 00000000 08:11 6276353    /usr/lib/libXcursor.so.1.0.2
b726d000-b726e000 rw-p 00007000 08:11 6276353    /usr/lib/libXcursor.so.1.0.2
b726e000-b7275000 r-xp 00000000 08:11 6276369    /usr/lib/libXi.so.6.0.0
b7275000-b7276000 rw-p 00006000 08:11 6276369    /usr/lib/libXi.so.6.0.0
b7276000-b7278000 r-xp 00000000 08:11 6276371    /usr/lib/libXinerama.so.1.0.0
b7278000-b7279000 rw-p 00001000 08:11 6276371    /usr/lib/libXinerama.so.1.0.0
b7279000-b7280000 r-xp 00000000 08:11 6276383    /usr/lib/libXrender.so.1.3.0
b7280000-b7281000 rw-p 00006000 08:11 6276383    /usr/lib/libXrender.so.1.3.0
b7281000-b728e000 r-xp 00000000 08:11 6276361    /usr/lib/libXext.so.6.4.0
b728e000-b728f000 rw-p 0000d000 08:11 6276361    /usr/lib/libXext.so.6.4.0
b728f000-b7290000 rw-p b728f000 00:00 0 
b7290000-b72b3000 r-xp 00000000 08:11 6276548    /usr/lib/libfontconfig.so.1.2.0
b72b3000-b72bb000 rw-p 00023000 08:11 6276548    /usr/lib/libfontconfig.so.1.2.0
b72bb000-b72c2000 r-xp 00000000 08:11 6276932    /usr/lib/libpangocairo-1.0.so.0.1600.2
b72c2000-b72c3000 rw-p 00007000 08:11 6276932    /usr/lib/libpangocairo-1.0.so.0.1600.2
b72c3000-b72ed000 r-xp 00000000 08:11 6276934    /usr/lib/libpangoft2-1.0.so.0.1600.2
b72ed000-b72ee000 rw-p 0002a000 08:11 6276934    /usr/lib/libpangoft2-1.0.so.0.1600.2
b72ee000-b7302000 r-xp 00000000 08:11 6276409    /usr/lib/libart_lgpl_2.so.2.3.17
b7302000-b7303000 rw-p 00013000 08:11 6276409    /usr/lib/libart_lgpl_2.so.2.3.17
b7303000-b730a000 r-xp 00000000 08:11 6652011    /lib/libpopt.so.0.0.0
b730a000-b730b000 rw-p 00006000 08:11 6652011    /lib/libpopt.so.0.0.0
b730b000-b7334000 r-xp 00000000 08:11 6276669    /usr/lib/libgnomecanvas-2.so.0.1400.0
b7334000-b7335000 rw-p 00029000 08:11 6276669    /usr/lib/libgnomecanvas-2.so.0.1400.0
b7335000-b7336000 rw-p b7335000 00:00 0 
b7336000-b7391000 r-xp 00000000 08:11 6276446    /usr/lib/libbonoboui-2.so.0.0.0
b7391000-b7394000 rw-p 0005a000 08:11 6276446    /usr/lib/libbonoboui-2.so.0.0.0
b7394000-b74ab000 r-xp 00000000 08:11 6277095    /usr/lib/libxml2.so.2.6.27
b74ab000-b74b1000 rw-p 00116000 08:11 6277095    /usr/lib/libxml2.so.2.6.27
b74b1000-b7571000 r-xp 00000000 08:11 6276411    /usr/lib/libasound.so.2.0.0
b7571000-b7576000 rw-p 000bf000 08:11 6276411    /usr/lib/libasound.so.2.0.0
b7576000-b759b000 r-xp 00000000 08:11 6685962    /lib/tls/i686/cmov/libm-2.5.so
b759b000-b759d000 rw-p 00024000 08:11 6685962    /lib/tls/i686/cmov/libm-2.5.so
b759d000-b75bd000 r-xp 00000000 08:11 6276423    /usr/lib/libaudiofile.so.0.0.2
b75bd000-b75bf000 rw-p 00020000 08:11 6276423    /usr/lib/libaudiofile.so.0.0.2
b75bf000-b76fa000 r-xp 00000000 08:11 6685954    /lib/tls/i686/cmov/libc-2.5.so
b76fa000-b76fb000 r--p 0013b000 08:11 6685954    /lib/tls/i686/cmov/libc-2.5.so
b76fb000-b76fd000 rw-p 0013c000 08:11 6685954    /lib/tls/i686/cmov/libc-2.5.so
b76fd000-b7701000 rw-p b76fd000 00:00 0 
b7701000-b7708000 r-xp 00000000 08:11 6652217    /lib/libwrap.so.0.7.6
b7708000-b7709000 rw-p 00007000 08:11 6652217    /lib/libwrap.so.0.7.6
b7709000-b779d000 r-xp 00000000 08:11 6276643    /usr/lib/libglib-2.0.so.0.1200.11
b779d000-b779e000 rw-p 00093000 08:11 6276643    /usr/lib/libglib-2.0.so.0.1200.11
b779e000-b77aa000 r-xp 00000000 08:11 6276659    /usr/lib/libgnome-keyring.so.0.0.1
b77aa000-b77ab000 rw-p 0000b000 08:11 6276659    /usr/lib/libgnome-keyring.so.0.0.1
b77ab000-b77e4000 r-xp 00000000 08:11 6276697    /usr/lib/libgobject-2.0.so.0.1200.11
b77e4000-b77e5000 rw-p 00039000 08:11 6276697    /usr/lib/libgobject-2.0.so.0.1200.11
b77e5000-b7817000 r-xp 00000000 08:11 6275561    /usr/lib/libdbus-1.so.3.2.0
b7817000-b7818000 rw-p 00031000 08:11 6275561    /usr/lib/libdbus-1.so.3.2.0
b7818000-b7832000 r-xp 00000000 08:11 6276486    /usr/lib/libdbus-glib-1.so.2.1.0
b7832000-b7833000 rw-p 0001a000 08:11 6276486    /usr/lib/libdbus-glib-1.so.2.1.0
b7833000-b7834000 rw-p b7833000 00:00 0 
b7834000-b7847000 r-xp 00000000 08:11 6685980    /lib/tls/i686/cmov/libpthread-2.5.so
b7847000-b7849000 rw-p 00013000 08:11 6685980    /lib/tls/i686/cmov/libpthread-2.5.so
b7849000-b784b000 rw-p b7849000 00:00 0 
b784b000-b7894000 r-xp 00000000 08:11 6276328    /usr/lib/libORBit-2.so.0.1.0
b7894000-b789e000 rw-p 00048000 08:11 6276328    /usr/lib/libORBit-2.so.0.1.0
b789e000-b78cd000 r-xp 00000000 08:11 6276585    /usr/lib/libgconf-2.so.4.1.2
b78cd000-b78d0000 rw-p 0002e000 08:11 6276585    /usr/lib/libgconf-2.so.4.1.2
b78d0000-b78e3000 r-xp 00000000 08:11 6276444    /usr/lib/libbonobo-activation.so.4.0.0
b78e3000-b78e5000 rw-p 00013000 08:11 6276444    /usr/lib/libbonobo-activation.so.4.0.0
b78e5000-b7937000 r-xp 00000000 08:11 6276442    /usr/lib/libbonobo-2.so.0.0.0
b7937000-b7941000 rw-p 00051000 08:11 6276442    /usr/lib/libbonobo-2.so.0.0.0
b7941000-b7942000 rw-p b7941000 00:00 0 
b7942000-b7a2f000 r-xp 00000000 08:11 6276340    /usr/lib/libX11.so.6.2.0
b7a2f000-b7a33000 rw-p 000ed000 08:11 6276340    /usr/lib/libX11.so.6.2.0
b7a33000-b7a6f000 r-xp 00000000 08:11 6276930    /usr/lib/libpango-1.0.so.0.1600.2
b7a6f000-b7a71000 rw-p 0003b000 08:11 6276930    /usr/lib/libpango-1.0.so.0.1600.2
b7a71000-b7a76000 r-xp 00000000 08:11 6276381    /usr/lib/libXrandr.so.2.1.0
b7a76000-b7a77000 rw-p 00005000 08:11 6276381    /usr/lib/libXrandr.so.2.1.0
b7a77000-b7a8d000 r-xp 00000000 08:11 6276607    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a8d000-b7a8e000 rw-p 00015000 08:11 6276607    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a8e000-b7aa7000 r-xp 00000000 08:11 6276417    /usr/lib/libatk-1.0.so.0.1809.1
b7aa7000-b7aa9000 rw-p 00018000 08:11 6276417    /usr/lib/libatk-1.0.so.0.1809.1
b7aa9000-b7b2c000 r-xp 00000000 08:11 6276605    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b2c000-b7b2f000 rw-p 00083000 08:11 6276605    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b2f000-b7b30000 rw-p b7b2f000 00:00 0 
b7b30000-b7e81000 r-xp 00000000 08:11 6276754    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e81000-b7e87000 rw-p 00351000 08:11 6276754    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e87000-b7e88000 rw-p b7e87000 00:00 0 
b7e88000-b7e9c000 r-xp 00000000 08:11 6276655    /usr/lib/libgnome-2.so.0.1800.0
b7e9c000-b7e9d000 rw-p 00014000 08:11 6276655    /usr/lib/libgnome-2.so.0.1800.0
b7e9d000-b7eb2000 r-xp 00000000 08:11 6276318    /usr/lib/libICE.so.6.3.0
b7eb2000-b7eb4000 rw-p 00014000 08:11 6276318    /usr/lib/libICE.so.6.3.0
b7eb4000-b7eb5000 rw-p b7eb4000 00:00 0 
b7eb5000-b7ebd000 r-xp 00000000 08:11 6276336    /usr/lib/libSM.so.6.0.0
b7ebd000-b7ebe000 rw-p 00007000 08:11 6276336    /usr/lib/libSM.so.6.0.0
b7ebe000-b7f48000 r-xp 00000000 08:11 6276685    /usr/lib/libgnomeui-2.so.0.1788.4
b7f48000-b7f4c000 rw-p 00089000 08:11 6276685    /usr/lib/libgnomeui-2.so.0.1788.4
b7f4c000-b7f60000 r-xp 00000000 08:11 6276657    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f60000-b7f61000 rw-p 00014000 08:11 6276657    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f61000-b7f62000 rw-p b7f61000 00:00 0 
b7f62000-b7f6b000 r-xp 00000000 08:11 6276533    /usr/lib/libesd.so.0.2.36
b7f6b000-b7f6c000 rw-p 00009000 08:11 6276533    /usr/lib/libesd.so.0.2.36
b7f6c000-b7f6e000 r-xp 00000000 08:11 6276346    /usr/lib/libXau.so.6.0.0
b7f6e000-b7f6f000 rw-p 00001000 08:11 6276346    /usr/lib/libXau.so.6.0.0
b7f6f000-b7f70000 r--s 00000000 08:11 5456833    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7f70000-b7f71000 r--p 00000000 08:11 6341796    /usr/lib/locale/da_DK.utf8/LC_NUMERIC
b7f71000-b7f72000 r--p 00000000 08:11 6424896    /usr/lib/locale/da_DK.utf8/LC_TIME
b7f72000-b7f73000 r--p 00000000 08:11 6424898    /usr/lib/locale/da_DK.utf8/LC_MONETARY
b7f73000-b7f74000 r--p 00000000 08:11 6440608    /usr/lib/locale/da_DK.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f74000-b7f75000 r--p 00000000 08:11 6342248    /usr/lib/locale/da_DK.utf8/LC_PAPER
b7f75000-b7f76000 r--p 00000000 08:11 6342246    /usr/lib/locale/da_DK.utf8/LC_NAME
b7f76000-b7f77000 r--p 00000000 08:11 6341833    /usr/lib/locale/da_DK.utf8/LC_ADDRESS
b7f77000-b7f78000 r--p 00000000 08:11 6341842    /usr/lib/locale/da_DK.utf8/LC_TELEPHONE
b7f78000-b7f79000 r--p 00000000 08:11 6342244    /usr/lib/locale/da_DK.utf8/LC_MEASUREMENT
b7f79000-b7f80000 r--s 00000000 08:11 6308646    /usr/lib/gconv/gconv-modules.cache
b7f80000-b7f81000 r--p 00000000 08:11 6424899    /usr/lib/locale/da_DK.utf8/LC_IDENTIFICATION
b7f81000-b7f83000 rw-p b7f81000 00:00 0 
b7f83000-b7f9c000 r-xp 00000000 08:11 6651925    /lib/ld-2.5.so
b7f9c000-b7f9e000 rw-p 00019000 08:11 6651925    /lib/ld-2.5.so
bff1e000-bff33000 rw-p bff1e000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
** Message: failed to load session from /home/oliver/.nautilus/saved-session-8LBJYT
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in Xorg.conf or XFree86.conf to use GSynaptics
Starting gdesklets-daemon...

Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
(gnome-power-manager:8383): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:8382): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:8386): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```

---

### Post by ntetreau on 2007-09-13
My first guess is that it is beryl that's causing X to crash.  At gdm, login to a failsafe terminal, then start session manager

```
gnome-session-properties
```

find the part where Beryl is being started be default and find a way to remove/disable that entry.  Close it and try again.

---

### Post by OliverN on 2007-09-13
> **ntetreau said:**
> My first guess is that it is beryl that's causing X to crash.  At gdm, login to a failsafe terminal, then start session manager

```
gnome-session-properties
```find the part where Beryl is being started be default and find a way to remove/disable that entry.  Close it and try again.

Tried it, but no - it's not Beryl.

Also, I found out I'm able to start Beryl in failsafe mode, which launches my gnome window manager, so that's nice.

EDIT;

Found out that I can start a gnome session by attempting two logins in a row. Only, after the second login I can't close the window saying that my previous session lasted under 10 secs and so forth without busting myself back to the login screen as usual. Leaving that window open let's me stay in the current gnome session.
Beryl is really unstable, and occasionally crashes everything when I try to start it up. I don't know if Beryl's killing X though. When I log in (not in failsafe), X's chequered pattern never even appears, and I guess that means it crashes on start up.

This is my x-session error log without Beryl (and gdesklets)

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "oliver"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Profeten:/tmp/.ICE-unix/6335
Initializing gnome-mount extension
unclutter: usage:
	-display <display>
	-idle <seconds>		time between polls to detect idleness.
	-keystroke		wait for keystroke before idling.
	-jitter <pixels>	pixels mouse can twitch without moving
	-grab			use grabpointer method not createwindow
	-reset			reset the timer whenever cursor becomes
					visible even if it hasn't moved
 	-root	       		apply to cursor on root window too
	-onescreen		apply only to given screen of display
 	-visible       		ignore visibility events
 	-noevents      		don't send pseudo events
	-regex			name or class below is a regular expression
	-not names...		don't apply to windows whose wm-name begins.
				(must be last argument)
	-notname names...	same as -not names...
	-notclass classes...    don't apply to windows whose wm-class begins.
				(must be last argument, cannot be used with
				-not or -notname)
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in Xorg.conf or XFree86.conf to use GSynaptics
** Message: failed to load session from /home/oliver/.nautilus/saved-session-8LBJYT

(gnome-power-manager:6413): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection./etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "oliver"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Profeten:/tmp/.ICE-unix/6335
Initializing gnome-mount extension
unclutter: usage:
	-display <display>
	-idle <seconds>		time between polls to detect idleness.
	-keystroke		wait for keystroke before idling.
	-jitter <pixels>	pixels mouse can twitch without moving
	-grab			use grabpointer method not createwindow
	-reset			reset the timer whenever cursor becomes
					visible even if it hasn't moved
 	-root	       		apply to cursor on root window too
	-onescreen		apply only to given screen of display
 	-visible       		ignore visibility events
 	-noevents      		don't send pseudo events
	-regex			name or class below is a regular expression
	-not names...		don't apply to windows whose wm-name begins.
				(must be last argument)
	-notname names...	same as -not names...
	-notclass classes...    don't apply to windows whose wm-class begins.
				(must be last argument, cannot be used with
				-not or -notname)
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in Xorg.conf or XFree86.conf to use GSynaptics
** Message: failed to load session from /home/oliver/.nautilus/saved-session-8LBJYT

(gnome-power-manager:6413): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```

---

### Post by ntetreau on 2007-09-18
Hey, your pasted output really doesn' t look good to be but i' m not an expert.  I would try to remove beryl if I were you just to make sure that it isn' t the problem.  Anyway, let's hope someone more knowledgeable steps in.

Nic

---

### Post by tvrg on 2007-09-18
I think you have a broken saved session

try removing $HOME/.gnome2/session*

---

### Post by OliverN on 2007-09-20
> Hey, your pasted output really doesn' t look good to be but i' m not an expert. I would try to remove beryl if I were you just to make sure that it isn' t the problem. Anyway, let's hope someone more knowledgeable steps in.

Nic

Already tried that. I'm now running compiz fusion (or at least trying to), but still got the same problem. It's not always an issue, though. It seems like I only get the problem once a session has crashed for any reason at all, and I try to log in again. I'm not really sure how I break the cycle..!

> **tvrg said:**
> I think you have a broken saved session

try removing $HOME/.gnome2/session*

That sounds right! I'm a little anxious about deleting saved sessions, though. Anything I should be made aware of before doing that?

---

### Post by shae on 2007-09-20
You should not be to worried about deleting the saved session.

---

### Post by OliverN on 2007-09-20
> **shae said:**
> You should not be to worried about deleting the saved session.

alright, I deleted the file, and that seemed to do it! Thank you, friendly people :) I hope this will be the last of it.

---

