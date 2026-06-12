---
title: "Skype does not work after Cjk input set up"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by rockymaxsource on 2007-03-27
Hey,

Before, my skype works on my Ubuntu installation. But after I did ```
sudo apt-get install scim-qtimm
im-switch -z en_GB -s scim
```  I can not start skype anymore. ```
$ skype &
```gives me the following error:

```
[2] 5870
lover@lover-laptop:~$ *** glibc detected *** skype: free(): invalid pointer: 0x08a6ce68 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73cc8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb73cca44]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb718bfc1]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb7168d3d]
/usr/lib/libscim-1.0.so.8[0xb6d4f633]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xb6d508c7]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xb6d4b0c5]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xb6deacf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xb6decace]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xb6de5cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7b8301f]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7b82bec]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xb6f0d85b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xb6f0da0f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xb6f0dc7e]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7b82c10]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb78d5a8d]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb78d5d93]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7a5619d]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb7a1d49e]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb7a17d68]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb7a1b021]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb737b8cc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 03:01 4986008    /usr/bin/skype
08988000-08a86000 rw-p 08988000 00:00 0          [heap]
b6b00000-b6b21000 rw-p b6b00000 00:00 0 
b6b21000-b6c00000 ---p b6b21000 00:00 0 
b6cb6000-b6cc1000 r-xp 00000000 03:01 5046978    /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6cc1000-b6cc2000 rw-p 0000a000 03:01 5046978    /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6cc2000-b6ce6000 r-xp 00000000 03:01 5046977    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6ce6000-b6ce7000 rw-p 00024000 03:01 5046977    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6ce7000-b6dbc000 r-xp 00000000 03:01 4982876    /usr/lib/libscim-1.0.so.8.1.0
b6dbc000-b6dca000 rw-p 000d5000 03:01 4982876    /usr/lib/libscim-1.0.so.8.1.0
b6dca000-b6dcc000 r-xp 00000000 03:01 4982880    /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6dcc000-b6dcd000 rw-p 00001000 03:01 4982880    /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6dd7000-b6df5000 r-xp 00000000 03:01 5046554    /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6df5000-b6df6000 rw-p 0001e000 03:01 5046554    /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6df6000-b6dfa000 r-xp 00000000 03:01 5046976    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6dfa000-b6dfb000 rw-p 00003000 03:01 5046976    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6dfb000-b6e6c000 r--p 00000000 03:01 5243036    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6e6c000-b6e96000 r-xp 00000000 03:01 4982726    /usr/lib/liblcms.so.1.0.15
b6e96000-b6e97000 rw-p 00029000 03:01 4982726    /usr/lib/liblcms.so.1.0.15
b6e97000-b6e9a000 rw-p b6e97000 00:00 0 
b6e9a000-b6f05000 r-xp 00000000 03:01 4982757    /usr/lib/libmng.so.1.1.0.9
b6f05000-b6f08000 rw-p 0006a000 03:01 4982757    /usr/lib/libmng.so.1.1.0.9
b6f08000-b6f11000 r-xp 00000000 03:01 5046975    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6f11000-b6f12000 rw-p 00008000 03:01 5046975    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6f12000-b6f17000 r-xp 00000000 03:01 5046973    /usr/lib/qt3/plugins/imageformats/libqmng.so
b6f17000-b6f18000 rw-p 00004000 03:01 5046973    /usr/lib/qt3/plugins/imageformats/libqmng.so
b6f18000-b6f19000 ---p b6f18000 00:00 0 
b6f19000-b6f99000 rw-p b6f19000 00:00 0 
b6f99000-b6f9a000 r-xp 00000000 03:01 4983120    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b6f9a000-b6f9b000 rw-p 00000000 03:01 4983120    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b6f9b000-b6fce000 r--p 00000000 03:01 5047528    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6fce000-b6fcf000 r--p 00000000 03:01 5047533    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b6fcf000-b6fd0000 r--p 00000000 03:01 5047536    /usr/lib/locale/en_US.utf8/LC_TIME
b6fd0000-b70a7000 r--p 00000000 03:01 5047527    /usr/lib/locale/en_US.utf8/LC_COLLATE
b70a7000-b70a8000 r--p 00000000 03:01 5047531    /usr/lib/locale/en_US.utf8/LC_MONETARY
b70a8000-b70a9000 r--p 00000000 03:01 5047537    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b70a9000-b70aa000 r--p 00000000 03:01 5047534    /usr/lib/locale/en_US.utf8/LC_PAPER
b70aa000-b70ab000 r--p 00000000 03:01 5047532    /usr/lib/locale/en_US.utf8/LC_NAME
b70ab000-b70ac000 r--p 00000000 03:01 5047526    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b70ac000-b70af000 rw-p b70ac000 00:00 0 
b70af000-b70b3000 r-xp 00000000 03:01 4982249    /usr/lib/libXfixes.so.3.1.0
b70b3000-b70b4000 rw-p 00003000 03:01 4982249    /usr/lib/libXfixes.so.3.1.0
b70b4000-b70d0000 r-xp 00000000 03:01 4982428    /usr/lib/libexpat.so.1.0.0
b70d0000-b70d2000 rw-p 0001c000 03:01 4982428    /usr/lib/libexpat.so.1.0.0
b70d2000-b70d6000 r-xp 00000000 03:01 4982243    /usr/lib/libXdmcp.so.6.0.0
b70d6000-b70d7000 rw-p 00003000 03:01 4982243    /usr/lib/libXdmcp.so.6.0.0
b70d7000-b70d9000 r-xp 00000000 03:01 4982234    /usr/lib/libXau.so.6.0.0
b70d9000-b70da000 rw-p 00001000 03:01 4982234    /usr/lib/libXau.so.6.0.0
b70da000-b70db000 rw-p b70da000 00:00 0 
b70db000-b71af000 r-xp 00000000 03:01 4982917    /usr/lib/libstdc++.so.6.0.8
b71af000-b71b2000 r--p 000d4000 03:01 4982917    /usr/lib/libstdc++.so.6.0.8
b71b2000-b71b4000 rw-p 000d7000 03:01 4982917    /usr/lib/libstdc++.so.6.0.8
b71b4000-b71ba000 rw-p b71b4000 00:00 0 
b71ba000-b71cf000 r-xp 00000000 03:01 4982206    /usr/lib/libICE.so.6.3.0
b71cf000-b71d0000 rw-p 00014000 03:01 4982206    /usr/lib/libICE.so.6.3.0
b71d0000-b71d2000 rw-p b71d0000 00:00 0 
b71d2000-b71da000 r-xp 00000000 03:01 4982224    /usr/lib/libSM.so.6.0.0
b71da000-b71db000 rw-p 00007000 03:01 4982224    /usr/lib/libSM.so.6.0.0
b71db000-b7242000 r-xp 00000000 03:01 4982444    /usr/lib/libfreetype.so.6.3.10
b7242000-b7245000 rw-p 00067000 03:01 4982444    /usr/lib/libfreetype.so.6.3.10
b7245000-b7256000 r-xp 00000000 03:01 4982253    /usr/lib/libXft.so.2.1.2
b7256000-b7257000 rw-p 00010000 03:01 4982253    /usr/lib/libXft.so.2.1.2
b7257000-b7259000 r-xp 00000000 03:01 4982257    /usr/lib/libXinerama.so.1.0.0
b7259000-b725a000 rw-p 00001000 03:01 4982257    /usr/lib/libXinerama.so.1.0.0
b725a000-b725b000 rw-p b725a000 00:00 0 
b725b000-b7263000 r-xp 00000000 03:01 4982239    /usr/lib/libXcursor.so.1.0.2
b7263000-b7264000 rw-p 00007000 03:01 4982239    /usr/lib/libXcursor.so.1.0.2
b7264000-b7266000 r-xp 00000000 03:01 4982267    /usr/lib/libXrandr.so.2.0.0
b7266000-b7267000 rw-p 00002000 03:01 4982267    /usr/lib/libXrandr.so.2.0.0
b7267000-b726e000 r-xp 00000000 03:01 4982269    /usr/lib/libXrender.so.1.3.0
b726e000-b726f000 rw-p 00006000 03:01 4982269    /usr/lib/libXrender.so.1.3.0
b726f000-b7276000 r-xp 00000000 03:01 4982255    /usr/lib/libXi.so.6.0.0
b7276000-b7277000 rw-p 00006000 03:01 4982255    /usr/lib/libXi.so.6.0.0
b7277000-b728a000 r-xp 00000000 03:01 4982974    /usr/lib/libz.so.1.2.3
b728a000-b728b000 rw-p 00012000 03:01 4982974    /usr/lib/libz.so.1.2.3
b728b000-b72ae000 r-xp 00000000 03:01 4981470    /usr/lib/libpng12.so.0.1.2.8
b72ae000-b72af000 rw-p 00023000 03:01 4981470    /usr/lib/libpng12.so.0.1.2.8
b72af000-b72b0000 rw-p b72af000 00:00 0 
b72b0000-b72ce000 r-xp 00000000 03:01 4982710    /usr/lib/libjpeg.so.62.0.0
b72ce000-b72cf000 rw-p 0001d000 03:01 4982710    /usr/lib/libjpeg.so.62.0.0
b72cf000-b7319000 r-xp 00000000 03:01 4982273    /usr/lib/libXt.so.6.0.0
b7319000-b731d000 rw-p 00049000 03:01 4982273    /usr/lib/libXt.so.6.0.0
b731d000-b7332000 r-xp 00000000 03:01 4982310    /usr/lib/libaudio.so.2.4
b7332000-b7333000 rw-p 00014000 03:01 4982310    /usr/lib/libaudio.so.2.4
b7333000-b735c000 r-xp 00000000 03:01 4982434    /usr/lib/libfontconfig.so.1.0.4
b735c000-b7361000 rw-p 00028000 03:01 4982434    /usr/lib/libfontconfig.so.1.0.4
b7361000-b7362000 rw-p b7361000 00:00 0 
b7362000-b7364000 r-xp 00000000 03:01 2523197    /lib/tls/i686/cmov/libdl-2.4.so
b7364000-b7366000 rw-p 00001000 03:01 2523197    /lib/tls/i686/cmov/libdl-2.4.so
b7366000-b7493000 r-xp 00000000 03:01 2523178    /lib/tls/i686/cmov/libc-2.4.so
b7493000-b7495000 r--p 0012c000 03:01 2523178    /lib/tls/i686/cmov/libc-2.4.so
b7495000-b7497000 rw-p 0012e000 03:01 2523178    /lib/tls/i686/cmov/libc-2.4.so
b7497000-b749b000 rw-p b7497000 00:00 0 
b749b000-b74a5000 r-xp 00000000 03:01 2523203    /lib/libgcc_s.so.1
b74a5000-b74a6000 rw-p 00009000 03:01 2523203    /lib/libgcc_s.so.1
b74a6000-b74ca000 r-xp 00000000 03:01 2523209    /lib/tls/i686/cmov/libm-2.4.so
b74ca000-b74cc000 rw-p 00023000 03:01 2523209    /lib/tls/i686/cmov/libm-2.4.so
b74cc000-b757c000 r-xp 00000000 03:01 4982915    /usr/lib/libstdc++.so.5.0.7
b757c000-b7581000 rw-p 000af000 03:01 4982915    /usr/lib/libstdc++.so.5.0.7
b7581000-b7586000 rw-p b7581000 00:00 0 
b7586000-b7595000 r-xp 00000000 03:01 2523242    /lib/tls/i686/cmov/libpthread-2.4.so
b7595000-b7597000 rw-p 0000f000 03:01 2523242    /lib/tls/i686/cmov/libpthread-2.4.so
b7597000-b7599000 rw-p b7597000 00:00 0 
b7599000-b765f000 r-xp 00000000 03:01 4982228    /usr/lib/libX11.so.6.2.0
b765f000-b7662000 rw-p 000c5000 03:01 4982228    /usr/lib/libX11.so.6.2.0
b7662000-b766e000 r-xp 00000000 03:01 4982247    /usr/lib/libXext.so.6.4.0
b766e000-b766f000 rw-p 0000c000 03:01 4982247    /usr/lib/libXext.so.6.4.0
b766f000-b7670000 rw-p b766f000 00:00 0 
b7670000-b7e05000 r-xp 00000000 03:01 4983390    /usr/lib/libqt-mt.so.3.3.6
b7e05000-b7e4c000 rw-p 00794000 03:01 4983390    /usr/lib/libqt-mt.so.3.3.6
b7e4c000-b7e4f000 rw-p b7e4c000 00:00 0 
b7e4f000-b7f02000 r-xp 00000000 03:01 4982297    /usr/lib/libasound.so.2.0.0
b7f02000-b7f07000 rw-p 000b2000 03:01 4982297    /usr/lib/libasound.so.2.0.0
b7f07000-b7f0e000 r-xp 00000000 03:01 2523248    /lib/tls/i686/cmov/librt-2.4.so
b7f0e000-b7f10000 rw-p 00006000 03:01 2523248    /lib/tls/i686/cmov/librt-2.4.so
b7f10000-b7f11000 r--p 00000000 03:01 5047535    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f11000-b7f12000 r--p 00000000 03:01 5047530    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f12000-b7f19000 r--s 00000000 03:01 4980863    /usr/lib/gconv/gconv-modules.cache
b7f19000-b7f1a000 r--p 00000000 03:01 5047529    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f1a000-b7f1c000 rw-p b7f1a000 00:00 0 
b7f1c000-b7f35000 r-xp 00000000 03:01 2523140    /lib/ld-2.4.so
b7f35000-b7f37000 rw-p 00018000 03:01 2523140    /lib/ld-2.4.so
bfc0d000-bfc23000 rw-p bfc0d000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]



```

Can any of you help me please?

Thanks in advance!

Rocky

---

### Post by Big Ben on 2007-03-27
Skype and SCIM don't play well together.

Start skype using this command:
```
XMODIFIERS=@im=none QT_IM_MODULE=xim skype
```
and it should start normally, but you won't be able to use cjk within Skype itself.

More info here:
[https://help.ubuntu.com/community/Skype#head-3c0465dd246054db937a707d410b55aa94e19c93](https://help.ubuntu.com/community/Skype#head-3c0465dd246054db937a707d410b55aa94e19c93)

and there's a script you can use for this on this thread:
[http://www.ubuntuforums.org/showthread.php?t=304764](http://www.ubuntuforums.org/showthread.php?t=304764)

---

