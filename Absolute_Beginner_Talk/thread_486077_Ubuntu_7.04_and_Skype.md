---
title: "Ubuntu 7.04 and Skype"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-06-27
When I first installed Ubuntu I installed 6.10  and installed Skype.  At that time it worked.  I updated to 7.04, messed up, and the only thing I could figure out to do was to just reload, so I downloaded the 7.04 LiveCD and installed from it.  Obviously I had to reinstall Skype.  Now when I try to use Skype it says Call Failed: Problem with Audio Playback.  I have a cheap laptop and use the Via 8237 ALSA setting to make my sound work.  I have a XACT XVP640 usb phone for Skype if that helps.

Can anyone tell me what I am doing wrong?

---

### Post by anewguy on 2007-06-27
I got this to work.  On my laptop, I had to go into Skype options and change the Sound Devices to USB Phone (plughw:Phone,0).  Don't know if this would help anyone else or not.

---

### Post by ajeetraj on 2007-06-28
for me skype doesn't run at all. I used the .deb file to install it and i can see it installed in the applications tab but it doesn't run when i run it from the terminal i get this and then nothing happens: 

deepu@easter-sunday:~$ skype
*** glibc detected *** skype: free(): invalid pointer: 0x08a3b740 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73e57cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb73e8e30]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb719ad11]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb7177a5d]
/usr/lib/libstdc++.so.6(_ZNSsD1Ev+0x57)[0xb717a5e7]
/usr/lib/libscim-1.0.so.8[0xb6c2c08b]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xb6c2cf77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xb6c27f05]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xb6ccecf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xb6cd0ace]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xb6cc9cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7c06f67]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7c06b34]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xb6e62c9b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xb6e62e4f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xb6e630be]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7c06b58]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb7959965]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb7959c6b]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7ada0e5]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb7aa13e6]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb7a9bcb0]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb7a9ef69]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7393ebc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 08:06 460297     /usr/bin/skype
08988000-08a45000 rw-p 08988000 00:00 0          [heap]
b6a00000-b6a21000 rw-p b6a00000 00:00 0 
b6a21000-b6b00000 ---p b6a21000 00:00 0 
b6bc4000-b6c98000 r-xp 00000000 08:06 459438     /usr/lib/libscim-1.0.so.8.1.0
b6c98000-b6ca6000 rw-p 000d4000 08:06 459438     /usr/lib/libscim-1.0.so.8.1.0
b6cbb000-b6cd9000 r-xp 00000000 08:06 130682     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6cd9000-b6cda000 rw-p 0001e000 08:06 130682     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6cda000-b6cfe000 r-xp 00000000 08:06 588400     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6cfe000-b6cff000 rw-p 00024000 08:06 588400     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6cff000-b6d7c000 r--p 00000000 08:06 2595342    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6d7c000-b6da6000 r-xp 00000000 08:06 458706     /usr/lib/liblcms.so.1.0.15
b6da6000-b6da7000 rw-p 00029000 08:06 458706     /usr/lib/liblcms.so.1.0.15
b6da7000-b6daa000 rw-p b6da7000 00:00 0 
b6daa000-b6e15000 r-xp 00000000 08:06 458737     /usr/lib/libmng.so.1.1.0.9
b6e15000-b6e18000 rw-p 0006a000 08:06 458737     /usr/lib/libmng.so.1.1.0.9
b6e21000-b6e2c000 r-xp 00000000 08:06 588404     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6e2c000-b6e2d000 rw-p 0000a000 08:06 588404     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6e2d000-b6e57000 r-xp 00000000 08:06 459785     /usr/lib/libkdefx.so.4.2.0
b6e57000-b6e58000 rw-p 0002a000 08:06 459785     /usr/lib/libkdefx.so.4.2.0
b6e58000-b6e5c000 r-xp 00000000 08:06 588395     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6e5c000-b6e5d000 rw-p 00003000 08:06 588395     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6e5d000-b6e66000 r-xp 00000000 08:06 588393     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6e66000-b6e67000 rw-p 00009000 08:06 588393     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6e67000-b6e6c000 r-xp 00000000 08:06 588392     /usr/lib/qt3/plugins/imageformats/libqmng.so
b6e6c000-b6e6d000 rw-p 00004000 08:06 588392     /usr/lib/qt3/plugins/imageformats/libqmng.so
b6e6d000-b6e95000 r-xp 00000000 08:06 752699     /usr/lib/kde3/plugins/styles/polyester.so
b6e95000-b6e96000 rw-p 00028000 08:06 752699     /usr/lib/kde3/plugins/styles/polyester.so
b6e96000-b6e97000 ---p b6e96000 00:00 0 
b6e97000-b6f17000 rw-p b6e97000 00:00 0 
b6f17000-b6f1d000 r--s 00000000 08:06 1616717    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6f1d000-b6f1e000 r--s 00000000 08:06 1616714    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b6f1e000-b6f21000 r--s 00000000 08:06 1616713    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b6f21000-b6f22000 r--s 00000000 08:06 1616712    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b6f22000-b6f23000 r--s 00000000 08:06 1616711    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b6f23000-b6f27000 r--s 00000000 08:06 1615768    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6f27000-b6f28000 r--s 00000000 08:06 1615766    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6f28000-b6f2a000 r--s 00000000 08:06 1615765    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b6f2a000-b6f2c000 r--s 00000000 08:06 1615764    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b6f2c000-b6f2d000 r--s 00000000 08:06 1615763    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b6f2d000-b6f2f000 r--s 00000000 08:06 1615762    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b6f2f000-b6f35000 r--s 00000000 08:06 1615736    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6f35000-b6f37000 r--s 00000000 08:06 1615761    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6f37000-b6f39000 r--s 00000000 08:06 1615760    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b6f39000-b6f41000 r--s 00000000 08:06 1615735    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6f41000-b6f47000 r--s 00000000 08:06 1615737    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6f47000-b6f48000 r--s 00000000 08:06 1615755    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6f48000-b6f4a000 r--s 00000000 08:06 1615759    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6f4a000-b6f50000 r--s 00000000 08:06 1615758    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6f50000-b6f53000 r--s 00000000 08:06 1615757    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b6f53000-b6f57000 r--s 00000000 08:06 1616755    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6f57000-b6f5e000 r--s 00000000 08:06 1617242    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6f5e000-b6f5f000 r--s 00000000 08:06 1616735    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b6f5f000-b6f60000 r--s 00000000 08:06 1616742    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b6f60000-b6f61000 r--s 00000000 08:06 1616741    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b6f61000-b6f62000 r--s 00000000 08:06 1616740    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b6f62000-b6f63000 r--s 00000000 08:06 1616739    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b6f63000-b6f66000 r--s 00000000 08:06 1616753    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b6f66000-b6f6b000 r--s 00000000 08:06 1615756    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b6f6b000-b6f6d000 r--s 00000000 08:06 1616737    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b6f6d000-b6f6e000 r--s 00000000 08:06 1616736    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b6f6e000-b6f70000 r--s 00000000 08:06 1616757    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b6f70000-b6f71000 r--s 00000000 08:06 1616733    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b6f71000-b6f76000 r--s 00000000 08:06 1616751    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b6f76000-b6f7a000 r--s 00000000 08:06 1616734    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b6f7a000-b6f7c000 r--s 00000000 08:06 1615740    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b6f7c000-b6f7f000 r--s 00000000 08:06 1615741    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b6f7f000-b6f80000 r--s 00000000 08:06 1616732    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b6f80000-b6f82000 r--s 00000000 08:06 1616731    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b6f82000-b6f86000 r--s 00000000 08:06 1616744    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b6f86000-b6f8c000 r--s 00000000 08:06 1615739    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b6f8c000-b6f8d000 r--s 00000000 08:06 1615738    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b6f8d000-b6f95000 r--s 00000000 08:06 1616730    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b6f95000-b6f97000 r--s 00000000 08:06 1616748    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6f97000-b6f9a000 r--s 00000000 08:06 1616729    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6f9a000-b6f9c000 r--s 00000000 08:06 1616728    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6f9c000-b6fa3000 r--s 00000000 08:06 1617241    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6fa3000-b6fde000 r--p 00000000 08:06 506264     /usr/lib/locale/en_US.utf8/LC_CTYPE
b6fde000-b70b5000 r--p 00000000 08:06 507425     /usr/lib/locale/en_US.utf8/LC_COLLATE
b70b5000-b70b8000 rw-p b70b5000 00:00 0 
b70b8000-b70bc000 r-xp 00000000 08:06 457739     /usr/lib/libXfixes.so.3.1.0
b70bc000-b70bd000 rw-p 00003000 08:06 457739     /usr/lib/libXfixes.so.3.1.0
b70bd000-b70db000 r-xp 00000000 08:06 457138     /usr/lib/libexpat.so.1.0.0
b70db000-b70dd000 rw-p 0001d000 08:06 457138     /usr/lib/libexpat.so.1.0.0
b70dd000-b70e1000 r-xp 00000000 08:06 457708     /usr/lib/libXdmcp.so.6.0.0
b70e1000-b70e2000 rw-p 00003000 08:06 457708     /usr/lib/libXdmcp.so.6.0.0
b70e2000-b70e4000 r-xp 00000000 08:06 457087     /usr/lib/libXau.so.6.0.0
b70e4000-b70e5000 rw-p 00001000 08:06 457087     /usr/lib/libXau.so.6.0.0
b70e5000-b70e6000 rw-p b70e5000 00:00 0 
b70e6000-b71c5000 r-xp 00000000 08:06 457674     /usr/lib/libstdc++.so.6.0.8
b71c5000-b71c8000 r--p 000de000 08:06 457674     /usr/lib/libstdc++.so.6.0.8
b71c8000-b71ca000 rw-p 000e1000 08:06 457674     /usr/lib/libstdc++.so.6.0.8
b71ca000-b71d0000 rw-p b71ca000 00:00 0 
b71d0000-b71e5000 r-xp 00000000 08:06 2480840    /usr/lib/libICE.so.6.3.0
b71e5000-b71e7000 rw-p 00014000 08:06 2480840    /usr/lib/libICE.so.6.3.0
b71e7000-b71e8000 rw-p b71e7000 00:00 0 
b71e8000-b71f0000 r-xp 00000000 08:06 2480842    /usr/lib/libSM.so.6.0.0
b71f0000-b71f1000 rw-p 00007000 08:06 2480842    /usr/lib/libSM.so.6.0.0
b71f1000-b7259000 r-xp 00000000 08:06 2480950    /usr/lib/libfreetype.so.6.3.10
b7259000-b725c000 rw-p 00068000 08:06 2480950    /usr/lib/libfreetype.so.6.3.10
b725c000-b726d000 r-xp 00000000 08:06 457791     /usr/lib/libXft.so.2.1.2
b726d000-b726e000 rw-p 00010000 08:06 457791     /usr/lib/libXft.so.2.1.2
b726e000-b7270000 r-xp 00000000 08:06 458237     /usr/lib/libXinerama.so.1.0.0
b7270000-b7271000 rw-p 00001000 08:06 458237     /usr/lib/libXinerama.so.1.0.0
b7271000-b7272000 rw-p b7271000 00:00 0 
b7272000-b727a000 r-xp 00000000 08:06 457773     /usr/lib/libXcursor.so.1.0.2
b727a000-b727b000 rw-p 00007000 08:06 457773     /usr/lib/libXcursor.so.1.0.2
b727b000-b7280000 r-xp 00000000 08:06 2480838    /usr/lib/libXrandr.so.2.1.0
b7280000-b7281000 rw-p 00005000 08:06 2480838    /usr/lib/libXrandr.so.2.1.0
b7281000-b7288000 r-xp 00000000 08:06 2480836    /usr/lib/libXrender.so.1.3.0
b7288000-b7289000 rw-p 00006000 08:06 2480836    /usr/lib/libXrender.so.1.3.0
b7289000-b7290000 r-xp 00000000 08:06 457840     /usr/lib/libXi.so.6.0.0
b7290000-b7291000 rw-p 00006000 08:06 457840     /usr/lib/libXi.so.6.0.0
b7291000-b72a4000 r-xp 00000000 08:06 2480813    /usr/lib/libz.so.1.2.3
b72a4000-b72a5000 rw-p 00012000 08:06 2480813    /usr/lib/libz.so.1.2.3
b72a5000-b72c7000 r-xp 00000000 08:06 2480954    /usr/lib/libpng12.so.0.15.0
b72c7000-b72c8000 rw-p 00021000 08:06 2480954    /usr/lib/libpng12.so.0.15.0
b72c8000-b72c9000 rw-p b72c8000 00:00 0 
b72c9000-b72e7000 r-xp 00000000 08:06 458690     /usr/lib/libjpeg.so.62.0.0
b72e7000-b72e8000 rw-p 0001d000 08:06 458690     /usr/lib/libjpeg.so.62.0.0
b72e8000-b7335000 r-xp 00000000 08:06 2480844    /usr/lib/libXt.so.6.0.0
b7335000-b7339000 rw-p 0004c000 08:06 2480844    /usr/lib/libXt.so.6.0.0
b7339000-b734e000 r-xp 00000000 08:06 2480846    /usr/lib/libaudio.so.2.4
b734e000-b734f000 rw-p 00015000 08:06 2480846    /usr/lib/libaudio.so.2.4
b734f000-b7372000 r-xp 00000000 08:06 457121     /usr/lib/libfontconfig.so.1.2.0
b7372000-b737a000 rw-p 00023000 08:06 457121     /usr/lib/libfontconfig.so.1.2.0
b737a000-b737c000 r-xp 00000000 08:06 1681076    /lib/tls/i686/cmov/libdl-2.5.so
b737c000-b737e000 rw-p 00001000 08:06 1681076    /lib/tls/i686/cmov/libdl-2.5.so
b737e000-b74b9000 r-xp 00000000 08:06 1681073    /lib/tls/i686/cmov/libc-2.5.so
b74b9000-b74ba000 r--p 0013b000 08:06 1681073    /lib/tls/i686/cmov/libc-2.5.so
b74ba000-b74bc000 rw-p 0013c000 08:06 1681073    /lib/tls/i686/cmov/libc-2.5.so
b74bc000-b74c0000 rw-p b74bc000 00:00 0 
b74c0000-b74cb000 r-xp 00000000 08:06 1289295    /lib/libgcc_s.so.1
b74cb000-b74cc000 rw-p 0000a000 08:06 1289295    /lib/libgcc_s.so.1
b74cc000-b74f1000 r-xp 00000000 08:06 1681077    /lib/tls/i686/cmov/libm-2.5.so
b74f1000-b74f3000 rw-p 00024000 08:06 1681077    /lib/tls/i686/cmov/libm-2.5.so
b74f3000-b75a3000 r-xp 00000000 08:06 460059     /usr/lib/libstdc++.so.5.0.7
b75a3000-b75a8000 rw-p 000af000 08:06 460059     /usr/lib/libstdc++.so.5.0.7
b75a8000-b75ad000 rw-p b75a8000 00:00 0 
b75ad000-b75c0000 r-xp 00000000 08:06 1681087    /lib/tls/i686/cmov/libpthread-2.5.so
b75c0000-b75c2000 rw-p 00013000 08:06 1681087    /lib/tls/i686/cmov/libpthread-2.5.so
b75c2000-b75c4000 rw-p b75c2000 00:00 0 
b75c4000-b76b1000 r-xp 00000000 08:06 2480832    /usr/lib/libX11.so.6.2.0
b76b1000-b76b5000 rw-p 000ed000 08:06 2480832    /usr/lib/libX11.so.6.2.0
b76b5000-b76c2000 r-xp 00000000 08:06 2480834    /usr/lib/libXext.so.6.4.0
b76c2000-b76c3000 rw-p 0000d000 08:06 2480834    /usr/lib/libXext.so.6.4.0
b76c3000-b7e89000 r-xp 00000000 08:06 457229     /usr/lib/libqt-mt.so.3.3.7
b7e89000-b7ecf000 rw-p 007c5000 08:06 457229     /usr/lib/libqt-mt.so.3.3.7
b7ecf000-b7ed4000 rw-p b7ecf000 00:00 0 
b7ed4000-b7f94000 r-xp 00000000 08:06 2480801    /usr/lib/libasound.so.2.0.0
b7f94000-b7f99000 rw-p 000bf000 08:06 2480801    /usr/lib/libasound.so.2.0.0
b7f99000-b7fa0000 r-xp 00000000 08:06 1681089    /lib/tls/i686/cmov/librt-2.5.so
b7fa0000-b7fa2000 rw-p 00006000 08:06 1681089    /lib/tls/i686/cmov/librt-2.5.so
b7fa3000-b7fa5000 r-xp 00000000 08:06 459443     /usr/lib/libscim-x11utils-1.0.so.8.1.0
b7fa5000-b7fa6000 rw-p 00001000 08:06 459443     /usr/lib/libscim-x11utils-1.0.so.8.1.0
b7fa6000-b7fa7000 r--p 00000000 08:06 507431     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7fa7000-b7fa8000 r--p 00000000 08:06 506382     /usr/lib/locale/en_US.utf8/LC_TIME
b7fa8000-b7fa9000 r--p 00000000 08:06 506383     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7fa9000-b7faa000 r--p 00000000 08:06 522324     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7faa000-b7fab000 r--p 00000000 08:06 507542     /usr/lib/locale/en_US.utf8/LC_PAPER
b7fab000-b7fac000 r--p 00000000 08:06 506384     /usr/lib/locale/en_US.utf8/LC_NAME
b7fac000-b7fad000 r--p 00000000 08:06 506385     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fad000-b7fae000 r--p 00000000 08:06 506386     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fae000-b7faf000 r--p 00000000 08:06 506387     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7faf000-b7fb6000 r--s 00000000 08:06 473401     /usr/lib/gconv/gconv-modules.cache
b7fb6000-b7fb7000 r--p 00000000 08:06 506388     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fb7000-b7fb9000 rw-p b7fb7000 00:00 0 
b7fb9000-b7fd2000 r-xp 00000000 08:06 3150073    /lib/ld-2.5.so
b7fd2000-b7fd4000 rw-p 00019000 08:06 3150073    /lib/ld-2.5.so
bfe82000-bfe97000 rw-p bfe82000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
_____________________________________________________________________________

can someone please help me here. what am i doing wrong?

best,

---

### Post by expatCM on 2007-06-28
On another issue I was told that "invalid pointer" means that there is a problem with the specific application package working with the operating system.   Is it possible that you could try installing skype from a different source (such as Automatix for example) since it works well for me but I did not install from the .deb.

I assume that you are installing ver 1.3 since I have found a few challenges with the 1.4 beta.

---

### Post by anewguy on 2007-06-28
All I know is that I went to skype.com, went to downloads, the clicked on the "for linux", then click on the 7.04 fiesty fawn link and downloaded 1.4.  Since I am just new to all of this, I'll ask a dumb question and then leave it to others who have the knowledge to actually help you.;)  You did download the Linux version for the version of Ubuntu you are running, right?  (Sorry, but I had to ask!;))

---

### Post by expatCM on 2007-06-28
You may want to consider installing the 1.3 release since 1.4 is still beta.

I installed 1.3 from Synaptic (system / administration / synaptic package manager  and search for skype)  where on my system at least it is shown as the 1.3 version to be installed.

---

### Post by ajeetraj on 2007-06-28
Thanks a lot guys...its working now! I used synaptic and reinstalled skype and its working like a charm :) do you know if there is a video support for skype yet?

thanks for the quick replies :)

---

### Post by Shin_Gouki2501 on 2007-06-28
i think there is no video supprt :/
and it will take surly some time till this changes.. :(

---

### Post by expatCM on 2007-06-28
Sadly video is apparently not on the near horizon.  

The Linux version of Skype is quite different from the Windows offering and to offer video represents a major rewrite ........   Do not hold your breath but I am sure it will arrive someday ......  but not soon.

---

### Post by hello_syria on 2007-06-28
delete skype and rest your computer and install skype maybe it work:-&

---

### Post by Aleksandersen on 2007-07-08
Delete Me

---

### Post by Aleksandersen on 2007-07-08
**This post could be related to an Ubuntu bug filed at**: Corrected markup. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Video suppor for Skype on Linux is in development!! \\:D/  You can see the first fruits of it's [implementation in Skype 1.4b](http://opensource-notebook.com/2007/06/skype-linux-video/).

---

