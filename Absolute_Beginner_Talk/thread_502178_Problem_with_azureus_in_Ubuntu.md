---
title: "Problem with azureus in Ubuntu"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-16
Hello, i have a problem i am hoping can get fixed.  Everytime i either try manually opening Azureus or opening it through a .torrent file, the azur. splash screen comes up, the program starts normally, then as soon as the program loads, it closes the app.  Its as if i cliked the "X" as soon as the splash screen finishes loading. Does this sound like an issue for azureus or Ubuntu? How should i go about troubleshooting this if it is not a problem with Ubuntu?

---

### Post by dpar on 2007-07-16
What errors do you get when you start it with Terminal?

---

### Post by ITdrummer on 2007-07-16
havent tried starting it in terminal....ill try that

Has anyone else experienced this problem?

---

### Post by m4oz on 2007-07-17
I have the same problem. After writing in to the terminal the command I have such a result.



a57af000-a5915000 r-xp 00000000 08:02 3638611    /usr/share/icons/Human/icon-theme.cache
a5915000-a591c000 r-xp 00000000 08:02 3245506    /usr/lib/libfam.so.0.0.0
a591c000-a591d000 rwxp 00006000 08:02 3245506    /usr/lib/libfam.so.0.0.0
a591d000-a5923000 r-xp 00000000 08:02 20037659   /lib/libacl.so.1.1.0
a5923000-a5924000 rwxp 00005000 08:02 20037659   /lib/libacl.so.1.1.0
a592c000-a5935000 r-xp 00000000 08:02 3688727    /usr/share/locale-langpack/pl/LC_MESSAGES/totem.mo
a5a37000-a5af7000 r-xp 00000000 08:02 3245371    /usr/lib/libasound.so.2.0.0
a5af7000-a5afc000 rwxp 000bf000 08:02 3245371    /usr/lib/libasound.so.2.0.0
a5afc000-a5b00000 r-xp 00000000 08:02 3245292    /usr/lib/libORBitCosNaming-2.so.0.1.0
a5b00000-a5b01000 rwxp 00003000 08:02 3245292    /usr/lib/libORBitCosNaming-2.so.0.1.0
a5b01000-a5b37000 r-xp 00000000 08:02 20037750   /lib/libsepol.so.1
a5b37000-a5b38000 rwxp 00035000 08:02 20037750   /lib/libsepol.so.1
a5b42000-a5b91000 r-xp 00000000 08:02 3245547    /usr/lib/libgcrypt.so.11.2.2
a5b91000-a5b93000 rwxp 0004e000 08:02 3245547    /usr/lib/libgcrypt.so.11.2.2
a5b93000-a5ba7000 r-xp 00000000 08:02 3246003    /usr/lib/libtasn1.so.3.0.6
a5ba7000-a5ba8000 rwxp 00013000 08:02 3246003    /usr/lib/libtasn1.so.3.0.6
a5ba8000-a5bc6000 r-xp 00000000 08:02 3245784    /usr/lib/libjpeg.so.62.0.0
a5bc6000-a5bc7000 rwxp 0001d000 08:02 3245784    /usr/lib/libjpeg.so.62.0.0
a5bc7000-a5bd3000 r-xp 00000000 08:02 3245619    /usr/lib/libgnome-keyring.so.0.0.1
a5bd3000-a5bd4000 rwxp 0000b000 08:02 3245619    /usr/lib/libgnome-keyring.so.0.0.1
a5bd4000-a5be8000 r-xp 00000000 08:02 3245369    /usr/lib/libart_lgpl_2.so.2.3.17
a5be8000-a5be9000 rwxp 00013000 08:02 3245369    /usr/lib/libart_lgpl_2.so.2.3.17
a5be9000-a5c12000 r-xp 00000000 08:02 3245629    /usr/lib/libgnomecanvas-2.so.0.1400.0
a5c12000-a5c13000 rwxp 00029000 08:02 3245629    /usr/lib/libgnomecanvas-2.so.0.1400.0
a5c13000-a5c6e000 r-xp 00000000 08:02 3245406    /usr/lib/libbonoboui-2.so.0.0.0
a5c6e000-a5c71000 rwxp 0005a000 08:02 3245406    /usr/lib/libbonoboui-2.so.0.0.0
a5c71000-a5c78000 r-xp 00000000 08:02 20037739   /lib/libpopt.so.0.0.0
a5c78000-a5c79000 rwxp 00006000 08:02 20037739   /lib/libpopt.so.0.0.0
a5c79000-a5c99000 r-xp 00000000 08:02 3245383    /usr/lib/libaudiofile.so.0.0.2
a5c99000-a5c9b000 rwxp 00020000 08:02 3245383    /usr/lib/libaudiofile.so.0.0.2
a5c9b000-a5ca4000 r-xp 00000000 08:02 3245493    /usr/lib/libesd.so.0.2.36
a5ca4000-a5ca5000 rwxp 00009000 08:02 3245493    /usr/lib/libesd.so.0.2.36
a5ca5000-a5cb8000 r-xp 00000000 08:02 3245404    /usr/lib/libbonobo-activation.so.4.0.0
a5cb8000-a5cba000 rwxp 00013000 08:02 3245404    /usr/lib/libbonobo-activation.so.4.0.0
a5cba000-a5d0c000 r-xp 00000000 08:02 3245402    /usr/lib/libbonobo-2.so.0.0.0
a5d0c000-a5d16000 rwxp 00051000 08:02 3245402    /usr/lib/libbonobo-2.so.0.0.0
a5d16000-a5d2a000 r-xp 00000000 08:02 20037749   /lib/libselinux.so.1
a5d2a000-a5d2c000 rwxp 00013000 08:02 20037749   /lib/libselinux.so.1
a5d2c000-a5d3a000 r-xp 00000000 08:02 3245385    /usr/lib/libavahi-client.so.3.2.2
a5d3a000-a5d3b000 rwxp 0000e000 08:02 3245385    /usr/lib/libavahi-client.so.3.2.2
a5d3b000-a5d45000 r-xp 00000000 08:02 3245387    /usr/lib/libavahi-common.so.3.4.3
a5d45000-a5d46000 rwxp 00009000 08:02 3245387    /usr/lib/libavahi-common.so.3.4.3
a5d46000-a5db0000 r-xp 00000000 08:02 3245655    /usr/lib/libgnutls.so.13.0.9
a5db0000-a5db6000 rwxp 0006a000 08:02 3245655    /usr/lib/libgnutls.so.13.0.9
a5db6000-a5de7000 r-xp 00000000 08:02 3245444    /usr/lib/libdbus-1.so.3.2.0
a5de7000-a5de8000 rwxp 00031000 08:02 3245444    /usr/lib/libdbus-1.so.3.2.0
a5de8000-a5e02000 r-xp 00000000 08:02 3245446    /usr/lib/libdbus-glib-1.so.2.1.0
a5e02000-a5e03000 rwxp 0001a000 08:02 3245446    /usr/lib/libdbus-glib-1.so.2.1.0
a5e03000-a5f1a000 r-xp 00000000 08:02 3246055    /usr/lib/libxml2.so.2.6.27
a5f1a000-a5f20000 rwxp 00116000 08:02 3246055    /usr/lib/libxml2.so.2.6.27
a5f20000-a5f69000 r-xp 00000000 08:02 3245288    /usr/lib/libORBit-2.so.0.1.0
a5f69000-a5f73000 rwxp 00048000 08:02 3245288    /usr/lib/libORBit-2.so.0.1.0
a5f73000-a5fa2000 r-xp 00000000 08:02 3245545    /usr/lib/libgconf-2.so.4.1.2
a5fa2000-a5fa5000 rwxp 0002e000 08:02 3245545    /usr/lib/libgconf-2.so.4.1.2
a5fa5000-a602f000 r-xp 00000000 08:02 3245645    /usr/lib/libgnomeui-2.so.0.1788.4
a602f000-a6033000 rwxp 00089000 08:02 3245645    /usr/lib/libgnomeui-2.so.0.1788.4
a6033000-a6047000 r-xp 00000000 08:02 3245615    /usr/lib/libgnome-2.so.0.1800.0
a6047000-a6048000 rwxp 00014000 08:02 3245615    /usr/lib/libgnome-2.so.0.1800.0
a6048000-a609e000 r-xp 00000000 08:02 3245647    /usr/lib/libgnomevfs-2.so.0.1800.1
a609e000-a60a1000 rwxp 00055000 08:02 3245647    /usr/lib/libgnomevfs-2.so.0.1800.1
a60a1000-a60a4000 r-xp 00000000 08:02 20037663   /lib/libattr.so.1.1.0
a60a4000-a60a5000 rwxp 00002000 08:02 20037663   /lib/libattr.so.1.1.0
a60a5000-a60b1000 r-xp 00000000 08:02 3309935    /usr/lib/gnome-vfs-2.0/modules/libfile.so
a60b1000-a60b2000 rwxp 0000b000 08:02 3309935    /usr/lib/gnome-vfs-2.0/modules/libfile.so
a6133000-a61d0000 r-xp 00000000 08:02 3999199    /usr/lib/j2se/1.4/jre/lib/i386/libfontmanager.so
a61d0000-a61e2000 rwxp 0009d000 08:02 3999199    /usr/lib/j2se/1.4/jre/lib/i386/libfontmanager.so
a61e6000-a61fb000 r-xp 00000000 08:02 3245278    /usr/lib/libICE.so.6.3.0
a61fb000-a61fd000 rwxp 00014000 08:02 3245278    /usr/lib/libICE.so.6.3.0
a61fe000-a6206000 r-xp 00000000 08:02 3245296    /usr/lib/libSM.so.6.0.0
a6206000-a6207000 rwxp 00007000 08:02 3245296    /usr/lib/libSM.so.6.0.0
a6207000-a6254000 r-xp 00000000 08:02 3245347    /usr/lib/libXt.so.6.0.0
a6254000-a6258000 rwxp 0004c000 08:02 3245347    /usr/lib/libXt.so.6.0.0
a6258000-a625f000 r-xp 00000000 08:02 3245337    /usr/lib/libXp.so.6.2.0
a625f000-a6260000 rwxp 00006000 08:02 3245337    /usr/lib/libXp.so.6.2.0
a6260000-a6452000 r-xp 00000000 08:02 3999183    /usr/lib/j2se/1.4/jre/lib/i386/libXm.so.3
a6452000-a646c000 rwxp 001f1000 08:02 3999183    /usr/lib/j2se/1.4/jre/lib/i386/libXm.so.3
a646d000-a64d3000 r-xp 00000000 08:02 3999180    /usr/lib/j2se/1.4/jre/lib/i386/libmlib_image.so
a64d3000-a64d4000 rwxp 00066000 08:02 3999180    /usr/lib/j2se/1.4/jre/lib/i386/libmlib_image.so
a64d4000-a65b5000 r-xp 00000000 08:02 3999191    /usr/lib/j2se/1.4/jre/lib/i386/libawt.so
a65b5000-a65be000 rwxp 000e0000 08:02 3999191    /usr/lib/j2se/1.4/jre/lib/i386/libawt.so
a6f75000-a6f84000 r-xp 00000000 08:02 20071761   /lib/tls/i686/cmov/libresolv-2.5.so
a6f84000-a6f86000 rwxp 0000f000 08:02 20071761   /lib/tls/i686/cmov/libresolv-2.5.so
a6f88000-a6f8c000 r-xp 00000000 08:02 20071748   /lib/tls/i686/cmov/libnss_dns-2.5.so
a6f8c000-a6f8e000 rwxp 00003000 08:02 20071748   /lib/tls/i686/cmov/libnss_dns-2.5.so
a6f8e000-a6f90000 r-xp 00000000 08:02 20037721   /lib/libnss_mdns4_minimal.so.2
a6f90000-a6f91000 rwxp 00001000 08:02 20037721   /lib/libnss_mdns4_minimal.so.2
a6f91000-a6f92000 r-xs 00000000 08:02 3999149    /usr/lib/j2se/1.4/jre/lib/security/local_policy.jar
a6f92000-a6f93000 r-xs 00000000 08:02 3999150    /usr/lib/j2se/1.4/jre/lib/security/US_export_policy.jar
a6f93000-a6f96000 r-xp 00000000 08:02 3245659    /usr/lib/libgpg-error.so.0.3.0
a6f96000-a6f97000 rwxp 00002000 08:02 3245659    /usr/lib/libgpg-error.so.0.3.0
a6f97000-a6f99000 r-xp 00000000 08:02 20071767   /lib/tls/i686/cmov/libutil-2.5.so
a6f99000-a6f9b000 rwxp 00001000 08:02 20071767   /lib/tls/i686/cmov/libutil-2.5.so
a6f9b000-a6f9d000 r-xp 00000000 08:02 3245391    /usr/lib/libavahi-glib.so.1.0.1
a6f9d000-a6f9e000 rwxp 00001000 08:02 3245391    /usr/lib/libavahi-glib.so.1.0.1
a6f9e000-a6fa1000 r-xp 00000000 08:02 3703194    /usr/lib/jni/libswt-gnome-gtk-3236.so
a6fa1000-a6fa2000 rwxp 00002000 08:02 3703194    /usr/lib/jni/libswt-gnome-gtk-3236.so
a73aa000-a73ac000 r-xp 00000000 08:02 3408887    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
a73ac000-a73ad000 rwxp 00001000 08:02 3408887    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
a73ad000-a742a000 r-xp 00000000 08:02 3506326    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
a742a000-a7430000 r-xs 00000000 08:02 15056988   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
a7430000-a7431000 r-xs 00000000 08:02 15057532   /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
a7431000-a7434000 r-xs 00000000 08:02 15057531   /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
a7434000-a7435000 r-xs 00000000 08:02 15057530   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
a7435000-a7436000 r-xs 00000000 08:02 15057529   /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
a7436000-a743a000 r-xs 00000000 08:02 15056985   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
a743a000-a743b000 r-xs 00000000 08:02 15057527   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
a743b000-a743d000 r-xs 00000000 08:02 15057526   /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
a743d000-a743f000 r-xs 00000000 08:02 15057525   /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
a743f000-a7440000 r-xs 00000000 08:02 15057524   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
a7440000-a7442000 r-xs 00000000 08:02 15057523   /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
a7442000-a7448000 r-xs 00000000 08:02 15057522   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
a7448000-a744a000 r-xs 00000000 08:02 15057521   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
a744a000-a744c000 r-xs 00000000 08:02 15057520   /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
a744c000-a7454000 r-xs 00000000 08:02 15057519   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
a7454000-a745a000 r-xs 00000000 08:02 15057518   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
a745a000-a745b000 r-xs 00000000 08:02 15057517   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
a745b000-a745d000 r-xs 00000000 08:02 15057516   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
a745d000-a7463000 r-xs 00000000 08:02 15057515   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
a7463000-a7466000 r-xs 00000000 08:02 15057514   /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
a7466000-a746a000 r-xs 00000000 08:02 15056970   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
a746a000-a7471000 r-xs 00000000 08:02 15057330   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
a7471000-a7472000 r-xs 00000000 08:02 15057558   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
a7472000-a7473000 r-xs 00000000 08:02 15057557   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
a7473000-a7474000 r-xs 00000000 08:02 15057556   /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
a7474000-a7475000 r-xs 00000000 08:02 15057555   /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
a7475000-a7476000 r-xs 00000000 08:02 15057554   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
a7476000-a7479000 r-xs 00000000 08:02 15057553   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
a7479000-a747e000 r-xs 00000000 08:02 15057552   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
a747e000-a7480000 r-xs 00000000 08:02 15057551   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
a7480000-a7481000 r-xs 00000000 08:02 15057550   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
a7481000-a7483000 r-xs 00000000 08:02 15057549   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
a7483000-a7488000 r-xs 00000000 08:02 15057547   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
a7488000-a748c000 r-xs 00000000 08:02 15057546   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
a748c000-a748e000 r-xs 00000000 08:02 15057545   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
a748e000-a7491000 r-xs 00000000 08:02 15057544   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
a7491000-a7493000 r-xs 00000000 08:02 15057542   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
a7493000-a7497000 r-xs 00000000 08:02 15057541   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
a7497000-a74c3000 r-xs 00000000 08:02 3703275    /usr/share/azureus/plugins/azplugins/azplugins_2.1.1.jar
a74c3000-a790e000 r-xp 00000000 08:02 3642214    /usr/share/icons/hicolor/icon-theme.cache
a790e000-a8b34000 r-xp 00000000 08:02 3722261    /usr/share/icons/crystalsvg/icon-theme.cache
a8b34000-a91dd000 r-xp 00000000 08:02 3642212    /usr/share/icons/gnome/icon-theme.cache
a91dd000-a9434000 r-xp 00000000 08:02 3641354    /usr/share/icons/Tango/icon-theme.cache
a9434000-a94d5000 r-xp 00000000 08:02 3640157    /usr/share/icons/Tangerine/icon-theme.cache
a94d5000-a963b000 r-xp 00000000 08:02 3638611    /usr/share/icons/Human/icon-theme.cache
a963b000-a9640000 r-xp 00000000 08:02 3688702    /usr/share/locale-langpack/pl/LC_MESSAGES/glib20.mo
a9640000-a96a0000 rwxs 00000000 00:08 13336616   /SYSV00000000 (deleted)
a96a0000-a9700000 rwxs 00000000 00:08 13271078   /SYSV00000000 (deleted)
a9801000-a9807000 r-xs 00000000 08:02 15057540   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
a9807000-a9808000 r-xs 00000000 08:02 15057539   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
a9808000-a9810000 r-xs 00000000 08:02 15057538   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
a9810000-a9812000 r-xs 00000000 08:02 15057537   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
a9812000-a9815000 r-xs 00000000 08:02 15057536   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
a9815000-a9817000 r-xs 00000000 08:02 15057000   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
a9817000-a981e000 r-xs 00000000 08:02 15057326   /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
a981e000-a9831000 r-xs 00000000 08:02 3703278    /usr/share/azureus/plugins/bdcc/bdcc_2.2.2.jar
a9831000-a983e000 r-xp 00000000 08:02 3703246    /usr/lib/jni/libglibjni-0.4.so
a983e000-a983f000 rwxp 0000c000 08:02 3703246    /usr/lib/jni/libglibjni-0.4.so
a983f000-a98f2000 r-xp 00000000 08:02 3703224    /usr/lib/jni/libgtkjni-2.10.so
a98f2000-a98f5000 rwxp 000b3000 08:02 3703224    /usr/lib/jni/libgtkjni-2.10.so
a9976000-a9988000 r-xp 00000000 08:02 3309992    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
a9988000-a9989000 rwxp 00011000 08:02 3309992    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
a9989000-a99c1000 r-xp 00000000 08:02 3703197    /usr/lib/jni/libswt-gtk-3236.so
a99c1000-a99c3000 rwxp 00037000 08:02 3703197    /usr/lib/jni/libswt-gtk-3236.so
a99c4000-a99e6000 r-xp 00000000 08:02 3688690    /usr/share/locale-langpack/pl/LC_MESSAGES/gtk20-properties.mo
a99e6000-a99f6000 r-xp 00000000 08:02 3688781    /usr/share/locale-langpack/pl/LC_MESSAGES/gtk20.mo
a99f6000-a9acd000 r-xp 00000000 08:02 3835112    /usr/lib/locale/pl_PL.utf8/LC_COLLATE
a9acd000-a9aeb000 r-xp 00000000 08:02 3245502    /usr/lib/libexpat.so.1.0.0
a9aeb000-a9aed000 rwxp 0001d000 08:02 3245502    /usr/lib/libexpat.so.1.0.0
a9aed000-a9b0f000 r-xp 00000000 08:02 3245485    /usr/lib/libpng12.so.0.15.0
a9b0f000-a9b10000 rwxp 00021000 08:02 3245485    /usr/lib/libpng12.so.0.15.0
a9b10000-a9b14000 r-xp 00000000 08:02 3245317    /usr/lib/libXdmcp.so.6.0.0
a9b14000-a9b15000 rwxp 00003000 08:02 3245317    /usr/lib/libXdmcp.so.6.0.0
a9b15000-a9b17000 r-xp 00000000 08:02 3245306    /usr/lib/libXau.so.6.0.0
a9b17000-a9b18000 rwxp 00001000 08:02 3245306    /usr/lib/libXau.so.6.0.0
a9b18000-a9b2b000 r-xp 00000000 08:02 3246061    /usr/lib/libz.so.1.2.3
a9b2b000-a9b2c000 rwxp 00012000 08:02 3246061    /usr/lib/libz.so.1.2.3
a9b2c000-a9b94000 r-xp 00000000 08:02 3244783    /usr/lib/libfreetype.so.6.3.10
a9b94000-a9b97000 rwxp 00068000 08:02 3244783    /usr/lib/libfreetype.so.6.3.10
a9b97000-a9bc1000 r-xp 00000000 08:02 3245894    /usr/lib/libpangoft2-1.0.so.0.1600.2
a9bc1000-a9bc2000 rwxp 0002a000 08:02 3245894    /usr/lib/libpangoft2-1.0.so.0.1600.2
a9bc2000-a9bca000 r-xp 00000000 08:02 3245313    /usr/lib/libXcursor.so.1.0.2
a9bca000-a9bcb000 rwxp 00007000 08:02 3245313    /usr/lib/libXcursor.so.1.0.2
a9bcb000-a9bd0000 r-xp 00000000 08:02 3245341    /usr/lib/libXrandr.so.2.1.0
a9bd0000-a9bd1000 rwxp 00005000 08:02 3245341    /usr/lib/libXrandr.so.2.1.0
a9bd1000-a9bd8000 r-xp 00000000 08:02 3245329    /usr/lib/libXi.so.6.0.0
a9bd8000-a9bd9000 rwxp 00006000 08:02 3245329    /usr/lib/libXi.so.6.0.0
a9bd9000-a9bdb000 r-xp 00000000 08:02 3245331    /usr/lib/libXinerama.so.1.0.0
a9bdb000-a9bdc000 rwxp 00001000 08:02 3245331    /usr/lib/libXinerama.so.1.0.0
a9bdc000-a9be3000 r-xp 00000000 08:02 3245343    /usr/lib/libXrender.so.1.3.0
a9be3000-a9be4000 rwxp 00006000 08:02 3245343    /usr/lib/libXrender.so.1.3.0
a9be4000-a9c07000 r-xp 00000000 08:02 3245508    /usr/lib/libfontconfig.so.1.2.0
a9c07000-a9c0f000 rwxp 00023000 08:02 3245508    /usr/lib/libfontconfig.so.1.2.0
a9c0f000-a9c1c000 r-xp 00000000 08:02 3245321    /usr/lib/libXext.so.6.4.0
a9c1c000-a9c1d000 rwxp 0000d000 08:02 3245321    /usr/lib/libXext.so.6.4.0
a9c1d000-a9c24000 r-xp 00000000 08:02 20071763   /lib/tls/i686/cmov/librt-2.5.so
a9c24000-a9c26000 rwxp 00006000 08:02 20071763   /lib/tls/i686/cmov/librt-2.5.so
a9c26000-a9c94000 r-xp 00000000 08:02 3245410    /usr/lib/libcairo.so.2.11.1
a9c94000-a9c96000 rwxp 0006d000 08:02 3245410    /usr/lib/libcairo.so.2.11.1
a9c96000-a9d2a000 r-xp 00000000 08:02 3245603    /usr/lib/libglib-2.0.so.0.1200.11
a9d2a000-a9d2b000 rwxp 00093000 08:02 3245603    /usr/lib/libglib-2.0.so.0.1200.11
a9d2b000-a9d2d000 r-xp 00000000 08:02 3245613    /usr/lib/libgmodule-2.0.so.0.1200.11
a9d2d000-a9d2e000 rwxp 00002000 08:02 3245613    /usr/lib/libgmodule-2.0.so.0.1200.11
a9d2e000-a9d67000 r-xp 00000000 08:02 3245657    /usr/lib/libgobject-2.0.so.0.1200.11
a9d67000-a9d68000 rwxp 00039000 08:02 3245657    /usr/lib/libgobject-2.0.so.0.1200.11
a9d68000-a9d81000 r-xp 00000000 08:02 3245377    /usr/lib/libatk-1.0.so.0.1809.1
a9d81000-a9d83000 rwxp 00018000 08:02 3245377    /usr/lib/libatk-1.0.so.0.1809.1
a9d83000-a9d87000 r-xp 00000000 08:02 3245323    /usr/lib/libXfixes.so.3.1.0
a9d87000-a9d88000 rwxp 00003000 08:02 3245323    /usr/lib/libXfixes.so.3.1.0
a9d88000-a9e75000 r-xp 00000000 08:02 3245300    /usr/lib/libX11.so.6.2.0
a9e75000-a9e79000 rwxp 000ed000 08:02 3245300    /usr/lib/libX11.so.6.2.0
a9e79000-a9eb5000 r-xp 00000000 08:02 3245890    /usr/lib/libpango-1.0.so.0.1600.2
a9eb5000-a9eb7000 rwxp 0003b000 08:02 3245890    /usr/lib/libpango-1.0.so.0.1600.2
a9eb7000-a9ebe000 r-xp 00000000 08:02 3245892    /usr/lib/libpangocairo-1.0.so.0.1600.2
a9ebe000-a9ebf000 rwxp 00007000 08:02 3245892    /usr/lib/libpangocairo-1.0.so.0.1600.2
a9ebf000-a9f42000 r-xp 00000000 08:02 3245565    /usr/lib/libgdk-x11-2.0.so.0.1000.11
a9f42000-a9f45000 rwxp 00083000 08:02 3245565    /usr/lib/libgdk-x11-2.0.so.0.1000.11
a9f45000-a9f5b000 r-xp 00000000 08:02 3245567    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
a9f5b000-a9f5c000 rwxp 00015000 08:02 3245567    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
a9f5c000-a9f60000 r-xp 00000000 08:02 3245349    /usr/lib/libXtst.so.6.1.0
a9f60000-a9f61000 rwxp 00003000 08:02 3245349    /usr/lib/libXtst.so.6.1.0
a9f61000-a9f65000 r-xp 00000000 08:02 3245711    /usr/lib/libgthread-2.0.so.0.1200.11
a9f65000-a9f66000 rwxp 00003000 08:02 3245711    /usr/lib/libgthread-2.0.so.0.1200.11
a9f66000-aa2b7000 r-xp 00000000 08:02 3245714    /usr/lib/libgtk-x11-2.0.so.0.1000.11
aa2b7000-aa2bd000 rwxp 00351000 08:02 3245714    /usr/lib/libgtk-x11-2.0.so.0.1000.11
aa2be000-aa2bf000 r-xs 00000000 08:02 15057548   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
aa2bf000-aa2c0000 r-xs 00000000 08:02 15057543   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
aa2c0000-aa2c3000 r-xp 00000000 08:02 3688694    /usr/share/locale-langpack/pl/LC_MESSAGES/atk10.mo
aa2c3000-aa2c6000 rwxs 00000000 00:08 13303847   /SYSV00000000 (deleted)
aa2c6000-aa2c7000 r-xp 00000000 08:02 3277553    /usr/lib/gconv/ISO8859-1.so
aa2c7000-aa2c9000 rwxp 00000000 08:02 3277553    /usr/lib/gconv/ISO8859-1.so
aa2c9000-aa2ca000 r-xp 00000000 08:02 3310753    /usr/lib/locale/pl_PL.utf8/LC_NUMERIC
aa2ca000-aa2cb000 r-xp 00000000 08:02 3835111    /usr/lib/locale/pl_PL.utf8/LC_TIME
aa2cb000-aa2cc000 r-xp 00000000 08:02 3835113    /usr/lib/locale/pl_PL.utf8/LC_MONETARY
aa2cc000-aa2cd000 r-xp 00000000 08:02 3835115    /usr/lib/locale/pl_PL.utf8/LC_MESSAGES/SYS_LC_MESSAGES
aa2cd000-aa2ce000 r-xp 00000000 08:02 3310919    /usr/lib/locale/pl_PL.utf8/LC_PAPER
aa2ce000-aa2cf000 r-xp 00000000 08:02 3310818    /usr/lib/locale/pl_PL.utf8/LC_NAME
aa2cf000-aa327000 r-xp 00000000 08:02 3703198    /usr/lib/jni/libswt-pi-gtk-3236.so
aa327000-aa329000 rwxp 00058000 08:02 3703198    /usr/lib/jni/libswt-pi-gtk-3236.so
aa6b0000-aa6b6000 r-xp 00000000 08:02 3999171    /usr/lib/j2se/1.4/jre/lib/i386/libnio.so
aa6b6000-aa6b7000 rwxp 00006000 08:02 3999171    /usr/lib/j2se/1.4/jre/lib/i386/libnio.so
aa7b9000-aa859000 r-xs 00000000 08:02 3440908    /usr/share/java/gtk2.10.jar
aa859000-aa861000 r-xs 00000000 08:02 3440907    /usr/share/java/cairo1.0.jar
aa861000-aa867000 r-xs 00000000 08:02 3440906    /usr/share/java/glib0.4.jar
aa867000-aa9fa000 r-xs 00000000 08:02 3703208    /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar
aa9fa000-aaa2e000 r-xs 00000000 08:02 3440903    /usr/share/java/log4j-1.2.13.jar
aaa2e000-aab23000 r-xs 00000000 08:02 3440897    /usr/share/java/bcprov.jar
aac25000-aac34000 r-xp 00000000 08:02 3999190    /usr/lib/j2se/1.4/jre/lib/i386/libnet.so
aac34000-aac35000 rwxp 0000e000 08:02 3999190    /usr/lib/j2se/1.4/jre/lib/i386/libnet.so
aac5b000-ab388000 r-xs 00000000 08:02 3440909    /usr/share/java/Azureus2.jar
ab388000-ab3a4000 r-xs 00000000 08:02 3999153    /usr/lib/j2se/1.4/jre/lib/ext/sunjce_provider.jar
ab3a4000-ab460000 r-xs 00000000 08:02 3999155    /usr/lib/j2se/1.4/jre/lib/ext/localedata.jar
ab460000-ab46e000 r-xs 00000000 08:02 3999154    /usr/lib/j2se/1.4/jre/lib/ext/ldapsec.jar
ab672000-ab6ad000 r-xp 00000000 08:02 3310913    /usr/lib/locale/pl_PL.utf8/LC_CTYPE
b38b0000-b38b1000 r-xp 00000000 08:02 3835116    /usr/lib/locale/pl_PL.utf8/LC_ADDRESS
b5959000-b5ef9000 r-xs 00000000 08:02 3934535    /usr/lib/j2se/1.4/jre/lib/charsets.jar
b5ef9000-b5f0a000 r-xs 00000000 08:02 3934533    /usr/lib/j2se/1.4/jre/lib/jce.jar
b5f0a000-b5fe7000 r-xs 00000000 08:02 3934531    /usr/lib/j2se/1.4/jre/lib/jsse.jar
b5fe7000-b5ffd000 r-xs 00000000 08:02 3934537    /usr/lib/j2se/1.4/jre/lib/sunrsasign.jar
b6047000-b79f3000 r-xs 00000000 08:02 3934538    /usr/lib/j2se/1.4/jre/lib/rt.jar
b79f3000-b7a04000 r-xp 00000000 08:02 3999187    /usr/lib/j2se/1.4/jre/lib/i386/libzip.so
b7a04000-b7a06000 rwxp 00011000 08:02 3999187    /usr/lib/j2se/1.4/jre/lib/i386/libzip.so
b7a06000-b7a25000 r-xp 00000000 08:02 3999174    /usr/lib/j2se/1.4/jre/lib/i386/libjava.so
b7a25000-b7a26000 rwxp 0001f000 08:02 3999174    /usr/lib/j2se/1.4/jre/lib/i386/libjava.so
b7a26000-b7a37000 r-xp 00000000 08:02 3999179    /usr/lib/j2se/1.4/jre/lib/i386/libverify.so
b7a37000-b7a38000 rwxp 00011000 08:02 3999179    /usr/lib/j2se/1.4/jre/lib/i386/libverify.so
b7a38000-b7a41000 r-xp 00000000 08:02 20071750   /lib/tls/i686/cmov/libnss_files-2.5.so
b7a41000-b7a43000 rwxp 00008000 08:02 20071750   /lib/tls/i686/cmov/libnss_files-2.5.so
b7a43000-b7a4b000 r-xp 00000000 08:02 20071754   /lib/tls/i686/cmov/libnss_nis-2.5.so
b7a4b000-b7a4d000 rwxp 00007000 08:02 20071754   /lib/tls/i686/cmov/libnss_nis-2.5.so
b7a4d000-b7a54000 r-xp 00000000 08:02 20071746   /lib/tls/i686/cmov/libnss_compat-2.5.so
b7a54000-b7a56000 rwxp 00006000 08:02 20071746   /lib/tls/i686/cmov/libnss_compat-2.5.so
b7a56000-b7a57000 r-xp 00000000 08:02 3835117    /usr/lib/locale/pl_PL.utf8/LC_TELEPHONE
b7a57000-b7a58000 r-xp 00000000 08:02 3310915    /usr/lib/locale/pl_PL.utf8/LC_MEASUREMENT
b7a58000-b7a60000 r-xs 00000000 08:02 3440901    /usr/share/java/commons-cli-1.0.jar
b7a60000-b7a67000 r-xs 00000000 08:02 3277606    /usr/lib/gconv/gconv-modules.cache
b7a67000-b7a8c000 r-xp 00000000 08:02 20071741   /lib/tls/i686/cmov/libm-2.5.so
b7a8c000-b7a8e000 rwxp 00024000 08:02 20071741   /lib/tls/i686/cmov/libm-2.5.so
b7a8e000-b7aa1000 r-xp 00000000 08:02 20071744   /lib/tls/i686/cmov/libnsl-2.5.so
b7aa1000-b7aa3000 rwxp 00012000 08:02 20071744   /lib/tls/i686/cmov/libnsl-2.5.so
b7aa5000-b7d66000 r-xp 00000000 08:02 4014082    /usr/lib/j2se/1.4/jre/lib/i386/client/libjvm.so
b7d66000-b7d81000 rwxp 002c0000 08:02 4014082    /usr/lib/j2se/1.4/jre/lib/i386/client/libjvm.so
b7d99000-b7ed4000 r-xp 00000000 08:02 20071733   /lib/tls/i686/cmov/libc-2.5.so
b7ed4000-b7ed5000 r-xp 0013b000 08:02 20071733   /lib/tls/i686/cmov/libc-2.5.so
b7ed5000-b7ed7000 rwxp 0013c000 08:02 20071733   /lib/tls/i686/cmov/libc-2.5.so
b7edb000-b7edd000 r-xp 00000000 08:02 20071739   /lib/tls/i686/cmov/libdl-2.5.so
b7edd000-b7edf000 rwxp 00001000 08:02 20071739   /lib/tls/i686/cmov/libdl-2.5.so
b7edf000-b7ef2000 r-xp 00000000 08:02 20071759   /lib/tls/i686/cmov/libpthread-2.5.so
b7ef2000-b7ef4000 rwxp 00013000 08:02 20071759   /lib/tls/i686/cmov/libpthread-2.5.so
b7ef6000-b7ef7000 r-xp 00000000 08:02 3835118    /usr/lib/locale/pl_PL.utf8/LC_IDENTIFICATION
b7ef7000-b7efa000 r-xs 00000000 08:02 3999152    /usr/lib/j2se/1.4/jre/lib/ext/dnsns.jar
b7efa000-b7efe000 rwxs 00000000 08:02 11173951   /tmp/hsperfdata_paul/7418
b7efe000-b7f06000 r-xp 00000000 08:02 4014085    /usr/lib/j2se/1.4/jre/lib/i386/native_threads/libhpi.so
b7f06000-b7f07000 rwxp 00007000 08:02 4014085    /usr/lib/j2se/1.4/jre/lib/i386/native_threads/libhpi.so
b7f09000-b7f22000 r-xp 00000000 08:02 20037653   /lib/ld-2.5.so
b7f22000-b7f24000 rwxp 00019000 08:02 20037653   /lib/ld-2.5.so
bfa09000-bfa1f000 rwxp bfa09000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

Heap at VM Abort:
Heap
 def new generation   total 832K, used 358K [0xab8b0000, 0xab990000, 0xabd90000)
  eden space 768K,  38% used [0xab8b0000, 0xab8f9ca0, 0xab970000)
  from space 64K,  99% used [0xab980000, 0xab98fef0, 0xab990000)
  to   space 64K,   0% used [0xab970000, 0xab970000, 0xab980000)
 tenured generation   total 9856K, used 7785K [0xabd90000, 0xac730000, 0xaf8b0000)
   the space 9856K,  78% used [0xabd90000, 0xac52a518, 0xac52a600, 0xac730000)
 compacting perm gen  total 13312K, used 13219K [0xaf8b0000, 0xb05b0000, 0xb38b0000)
   the space 13312K,  99% used [0xaf8b0000, 0xb0598cc8, 0xb0598e00, 0xb05b0000)

Local Time = Tue Jul 17 13:40:27 2007
Elapsed Time = 6
#
# The exception above was detected in native code outside the VM
#
# Java VM: Java HotSpot(TM) Client VM (Blackdown-1.4.2-02 mixed mode)
#
# An error report file has been saved as hs_err_pid7418.log.
# Please refer to the file for further information.
#
Aborted (core dumped)
paul@abbalah-doon:~$

---

### Post by Nussbaum on 2007-07-17
I have this sometimes with azureus. I mostly can fix it by going to the  '/home/<username>/.azureus/logs'-directory and delete everything there. Then go to the 'save' directory and delete everything there too. Then start azureus manually, so not by double clicking a torrent file.

---

### Post by rickycodie on 2007-07-17
i have tried azureus before and had a core dump issue too. it's problem that's well documented--but has yet to be solved. at least i haven't found anything. try ktorrent.

---

### Post by m4oz on 2007-07-17
Even worse is with the Ktorent it doesn't work no matter which file I lounch

---

### Post by m4oz on 2007-07-17
What is the command for delete? Im new in town. :-D

---

### Post by techno-mole on 2007-07-17
have you tried runnnig it from you home directory ? download the latest version and try it that way.
ive also had this problem, i used to copy over a file from the azureus folder to the java folder in the file system, this would usually sort it out, but it would update properly, and i got bored of having to keep moving files about to keep it running, then i tried running it from my home directory and ive never had a problem since.
if i remember this right i had to copy - Azureus2.jar into the java folder, which can be found in - usr/share/java.
but like i said running it from my home directory solved this.
cheers

---

### Post by ITdrummer on 2007-07-17
Are there any decent, solid, dependable torrent programs available?  Ktorrent sounds nice but i use Gnome, not KDE.  I dont need anything fancy, just something to download the torrent file.

---

### Post by m4oz on 2007-07-17
where is it ?because  dont know where this azureus is instald? I have the latest  version

---

### Post by fastpakr on 2007-07-17
> **ITdrummer said:**
> Are there any decent, solid, dependable torrent programs available?  Ktorrent sounds nice but i use Gnome, not KDE.  I dont need anything fancy, just something to download the torrent file.

KTorrent works great in Gnome.

---

### Post by m4oz on 2007-07-17
where is it ?I dont know where this azureus is instald? I have the latest  version

---

### Post by fastpakr on 2007-07-17
You have the latest version from Sourceforge?  If so, I haven't had any problems like you're seeing.  I did have quite a few issues with the one from the repos, however.

---

### Post by rickycodie on 2007-07-17
the delete command is

sudo apt-get remove filename

or 

sudo apt-get autoremove filename

to remove all associated files or

sudo apt-get remove (or autoremove) --purge filename

to delete after removal

---

### Post by ITdrummer on 2007-07-17
> **fastpakr said:**
> KTorrent works great in Gnome.

Ok, i just thought that programs that started with the letter K  ran exclusively on KDE.  NOOB MISTAKE!!  HA HA

thanks

---

### Post by jvc26 on 2007-07-17
The issue you may be having with Azureus could well be caused by java6 if thats what you're using. There was a problem when I used to use Azureus and upgraded to Java6 where it would core dump all the time.
Il

---

### Post by m4oz on 2007-07-17
unfortunately the older one from synaptec, give me a link to latest if you can

---

### Post by m4oz on 2007-07-17
I have j2re1.4

---

### Post by fastpakr on 2007-07-17
Under Azureus2 [here](http://sourceforge.net/project/showfiles.php?group_id=84122).

---

### Post by misfitpierce on 2007-07-17
I had this once.. I uninstalled java and azureues and reinstalled through Automatix just to see if that would work and have had no further problems... If you seek another program try Transmission avail for linux and mac. Great lightweight and nice program.

---

### Post by m4oz on 2007-07-17
I dont know how to instal this file. I only used .deb or from repozytory.

---

### Post by misfitpierce on 2007-07-17
What file if your referring to transmission that I suggested it can be found at [http://getdeb.net](http://getdeb.net) for a pre-config'd ubuntu copy.

---

### Post by m4oz on 2007-07-17
fastpakr could You tel my now how to instal this azureus from Your link? Pleas

---

### Post by m4oz on 2007-07-17
where is usually azureus installd?

---

### Post by tankmcp on 2007-07-17
Thanks Nussbaum!  Your solution worked.
Now if we only understood why deleting logs would cause a program to quit crashing?!

---

### Post by IDmeNa on 2007-07-19
Yeah that worked out well; although..... Why would Azureus abort due to some logs?! :S
Anyway, thanks!

---

### Post by m4oz on 2007-07-23
To fix this problem erite in terminal:

sudo update-alternatives --config java

---

### Post by lamnk on 2007-09-25
> **Nussbaum said:**
> I have this sometimes with azureus. I mostly can fix it by going to the  '/home/<username>/.azureus/logs'-directory and delete everything there. Then go to the 'save' directory and delete everything there too. Then start azureus manually, so not by double clicking a torrent file.
Thank you man, it does work.

---

### Post by gedzilla on 2007-10-28
> **Nussbaum said:**
> I have this sometimes with azureus. I mostly can fix it by going to the  '/home/<username>/.azureus/logs'-directory and delete everything there. Then go to the 'save' directory and delete everything there too. Then start azureus manually, so not by double clicking a torrent file.

Been having this problem myself after a dodgy shutdown a couple of days after upgrading to 7.10, but this fix worked beautifully! I'd tried uninstalling and installing - but this was much simpler, cheers!

---

