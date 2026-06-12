---
title: "Skype refuses to start anymore"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by freshmaker on 2006-11-22
I am running Ubuntu Edgy Eft. Installed Skype which worked fine until today when it stopped even showing any sign of existence (even an error message). It is the second time skype does this to me but the first time I solved it by  reinstalling  Ubintu. I don't want to do it anymore ](*,) 
BTW this happens after I wrote this
```
im-switch -z “your locale” -s scim
``` in terminal in order to use SCIM keyboard  output (following this instruction [https://help.ubuntu.com/community/SCIM?highlight=%28SCIM%29](https://help.ubuntu.com/community/SCIM?highlight=%28SCIM%29)

Then I tried to start skype from the terminal and got this
```
*** glibc detected *** skype: double free or corruption (out): 0x08a2c688 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb74088bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7408a44]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb71c7fc1]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb71a4d3d]
/usr/lib/libscim-1.0.so.8[0xb6ea1633]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xb6ea28c7]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xb6e9d0c5]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xb6f3dcf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xb6f3face]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xb6f38cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7bbf01f]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7bbebec]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xb705c85b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xb705ca0f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xb705cc7e]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7bbec10]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb7911a8d]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb7911d93]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7a9219d]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb7a5949e]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb7a53d68]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb7a57021]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb73b78cc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 03:03 1791151    /usr/bin/skype
08988000-08a80000 rw-p 08988000 00:00 0          [heap]
b6d00000-b6d21000 rw-p b6d00000 00:00 0 
b6d21000-b6e00000 ---p b6d21000 00:00 0 
b6e08000-b6e13000 r-xp 00000000 03:03 1851929    /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6e13000-b6e14000 rw-p 0000a000 03:03 1851929    /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6e14000-b6e38000 r-xp 00000000 03:03 1851928    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6e38000-b6e39000 rw-p 00024000 03:03 1851928    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6e39000-b6f0e000 r-xp 00000000 03:03 1787996    /usr/lib/libscim-1.0.so.8.1.0
b6f0e000-b6f1c000 rw-p 000d5000 03:03 1787996    /usr/lib/libscim-1.0.so.8.1.0
b6f1c000-b6f1e000 r-xp 00000000 03:03 1788000    /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6f1e000-b6f1f000 rw-p 00001000 03:03 1788000    /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6f2a000-b6f48000 r-xp 00000000 03:03 1852374    /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6f48000-b6f49000 rw-p 0001e000 03:03 1852374    /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6f49000-b6fba000 r--p 00000000 03:03 53199      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6fba000-b6fe4000 r-xp 00000000 03:03 1787846    /usr/lib/liblcms.so.1.0.15
b6fe4000-b6fe5000 rw-p 00029000 03:03 1787846    /usr/lib/liblcms.so.1.0.15
b6fe5000-b6fe8000 rw-p b6fe5000 00:00 0 
b6fe8000-b7053000 r-xp 00000000 03:03 1787877    /usr/lib/libmng.so.1.1.0.9
b7053000-b7056000 rw-p 0006a000 03:03 1787877    /usr/lib/libmng.so.1.1.0.9
b7057000-b7060000 r-xp 00000000 03:03 1851926    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b7060000-b7061000 rw-p 00008000 03:03 1851926    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b7061000-b7066000 r-xp 00000000 03:03 1851924    /usr/lib/qt3/plugins/imageformats/libqmng.so
b7066000-b7067000 rw-p 00004000 03:03 1851924    /usr/lib/qt3/plugins/imageformats/libqmng.so
b7067000-b7068000 ---p b7067000 00:00 0 
b7068000-b70eb000 rw-p b7068000 00:00 0 
b70eb000-b70ef000 r-xp 00000000 03:03 1787369    /usr/lib/libXfixes.so.3.1.0
b70ef000-b70f0000 rw-p 00003000 03:03 1787369    /usr/lib/libXfixes.so.3.1.0
b70f0000-b710c000 r-xp 00000000 03:03 1787548    /usr/lib/libexpat.so.1.0.0
b710c000-b710e000 rw-p 0001c000 03:03 1787548    /usr/lib/libexpat.so.1.0.0
b710e000-b7112000 r-xp 00000000 03:03 1787363    /usr/lib/libXdmcp.so.6.0.0
b7112000-b7113000 rw-p 00003000 03:03 1787363    /usr/lib/libXdmcp.so.6.0.0
b7113000-b7115000 r-xp 00000000 03:03 1787354    /usr/lib/libXau.so.6.0.0
b7115000-b7116000 rw-p 00001000 03:03 1787354    /usr/lib/libXau.so.6.0.0
b7116000-b7117000 rw-p b7116000 00:00 0 
b7117000-b71eb000 r-xp 00000000 03:03 1788037    /usr/lib/libstdc++.so.6.0.8
b71eb000-b71ee000 r--p 000d4000 03:03 1788037    /usr/lib/libstdc++.so.6.0.8
b71ee000-b71f0000 rw-p 000d7000 03:03 1788037    /usr/lib/libstdc++.so.6.0.8
b71f0000-b71f6000 rw-p b71f0000 00:00 0 
b71f6000-b720b000 r-xp 00000000 03:03 1787326    /usr/lib/libICE.so.6.3.0
b720b000-b720c000 rw-p 00014000 03:03 1787326    /usr/lib/libICE.so.6.3.0
b720c000-b720e000 rw-p b720c000 00:00 0 
b720e000-b7216000 r-xp 00000000 03:03 1787344    /usr/lib/libSM.so.6.0.0
b7216000-b7217000 rw-p 00007000 03:03 1787344    /usr/lib/libSM.so.6.0.0
b7217000-b727e000 r-xp 00000000 03:03 1787564    /usr/lib/libfreetype.so.6.3.10
b727e000-b7281000 rw-p 00067000 03:03 1787564    /usr/lib/libfreetype.so.6.3.10
b7281000-b7292000 r-xp 00000000 03:03 1787373    /usr/lib/libXft.so.2.1.2
b7292000-b7293000 rw-p 00010000 03:03 1787373    /usr/lib/libXft.so.2.1.2
b7293000-b7295000 r-xp 00000000 03:03 1787377    /usr/lib/libXinerama.so.1.0.0
b7295000-b7296000 rw-p 00001000 03:03 1787377    /usr/lib/libXinerama.so.1.0.0
b7296000-b7297000 rw-p b7296000 00:00 0 
b7297000-b729f000 r-xp 00000000 03:03 1787359    /usr/lib/libXcursor.so.1.0.2
b729f000-b72a0000 rw-p 00007000 03:03 1787359    /usr/lib/libXcursor.so.1.0.2
b72a0000-b72a2000 r-xp 00000000 03:03 1787387    /usr/lib/libXrandr.so.2.0.0
b72a2000-b72a3000 rw-p 00002000 03:03 1787387    /usr/lib/libXrandr.so.2.0.0
b72a3000-b72aa000 r-xp 00000000 03:03 1787389    /usr/lib/libXrender.so.1.3.0
b72aa000-b72ab000 rw-p 00006000 03:03 1787389    /usr/lib/libXrender.so.1.3.0
b72ab000-b72b2000 r-xp 00000000 03:03 1787375    /usr/lib/libXi.so.6.0.0
b72b2000-b72b3000 rw-p 00006000 03:03 1787375    /usr/lib/libXi.so.6.0.0
b72b3000-b72c6000 r-xp 00000000 03:03 1788094    /usr/lib/libz.so.1.2.3
b72c6000-b72c7000 rw-p 00012000 03:03 1788094    /usr/lib/libz.so.1.2.3
b72c7000-b72ea000 r-xp 00000000 03:03 1786746    /usr/lib/libpng12.so.0.1.2.8
b72ea000-b72eb000 rw-p 00023000 03:03 1786746    /usr/lib/libpng12.so.0.1.2.8
b72eb000-b72ec000 rw-p b72eb000 00:00 0 
b72ec000-b730a000 r-xp 00000000 03:03 1787830    /usr/lib/libjpeg.so.62.0.0
b730a000-b730b000 rw-p 0001d000 03:03 1787830    /usr/lib/libjpeg.so.62.0.0
b730b000-b7355000 r-xp 00000000 03:03 1787393    /usr/lib/libXt.so.6.0.0
b7355000-b7359000 rw-p 00049000 03:03 1787393    /usr/lib/libXt.so.6.0.0
b7359000-b736e000 r-xp 00000000 03:03 1787430    /usr/lib/libaudio.so.2.4
b736e000-b736f000 rw-p 00014000 03:03 1787430    /usr/lib/libaudio.so.2.4
b736f000-b7398000 r-xp 00000000 03:03 1787554    /usr/lib/libfontconfig.so.1.0.4
b7398000-b739d000 rw-p 00028000 03:03 1787554    /usr/lib/libfontconfig.so.1.0.4
b739d000-b739e000 rw-p b739d000 00:00 0 
b739e000-b73a0000 r-xp 00000000 03:03 429071     /lib/tls/i686/cmov/libdl-2.4.so
b73a0000-b73a2000 rw-p 00001000 03:03 429071     /lib/tls/i686/cmov/libdl-2.4.so
b73a2000-b74cf000 r-xp 00000000 03:03 429065     /lib/tls/i686/cmov/libc-2.4.so
b74cf000-b74d1000 r--p 0012c000 03:03 429065     /lib/tls/i686/cmov/libc-2.4.so
b74d1000-b74d3000 rw-p 0012e000 03:03 429065     /lib/tls/i686/cmov/libc-2.4.so
b74d3000-b74d7000 rw-p b74d3000 00:00 0 
b74d7000-b74e1000 r-xp 00000000 03:03 426051     /lib/libgcc_s.so.1
b74e1000-b74e2000 rw-p 00009000 03:03 426051     /lib/libgcc_s.so.1
b74e2000-b7506000 r-xp 00000000 03:03 429073     /lib/tls/i686/cmov/libm-2.4.so
b7506000-b7508000 rw-p 00023000 03:03 429073     /lib/tls/i686/cmov/libm-2.4.so
b7508000-b75b8000 r-xp 00000000 03:03 1788035    /usr/lib/libstdc++.so.5.0.7
b75b8000-b75bd000 rw-p 000af000 03:03 1788035    /usr/lib/libstdc++.so.5.0.7
b75bd000-b75c2000 rw-p b75bd000 00:00 0 
b75c2000-b75d1000 r-xp 00000000 03:03 429091     /lib/tls/i686/cmov/libpthread-2.4.so
b75d1000-b75d3000 rw-p 0000f000 03:03 429091     /lib/tls/i686/cmov/libpthread-2.4.so
b75d3000-b75d5000 rw-p b75d3000 00:00 0 
b75d5000-b769b000 r-xp 00000000 03:03 1787348    /usr/lib/libX11.so.6.2.0
b769b000-b769e000 rw-p 000c5000 03:03 1787348    /usr/lib/libX11.so.6.2.0
b769e000-b76aa000 r-xp 00000000 03:03 1787367    /usr/lib/libXext.so.6.4.0
b76aa000-b76ab000 rw-p 0000c000 03:03 1787367    /usr/lib/libXext.so.6.4.0
b76ab000-b76ac000 rw-p b76ab000 00:00 0 
b76ac000-b7e41000 r-xp 00000000 03:03 1791143    /usr/lib/libqt-mt.so.3.3.6
b7e41000-b7e88000 rw-p 00794000 03:03 1791143    /usr/lib/libqt-mt.so.3.3.6
b7e88000-b7e8b000 rw-p b7e88000 00:00 0 
b7e8b000-b7f3e000 r-xp 00000000 03:03 1787417    /usr/lib/libasound.so.2.0.0
b7f3e000-b7f43000 rw-p 000b2000 03:03 1787417    /usr/lib/libasound.so.2.0.0
b7f43000-b7f4a000 r-xp 00000000 03:03 429095     /lib/tls/i686/cmov/librt-2.4.so
b7f4a000-b7f4c000 rw-p 00006000 03:03 429095     /lib/tls/i686/cmov/librt-2.4.so
b7f4c000-b7f50000 r-xp 00000000 03:03 1851927    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b7f50000-b7f51000 rw-p 00003000 03:03 1851927    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b7f51000-b7f56000 r-xp 00000000 03:03 1788242    /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b7f56000-b7f57000 rw-p 00004000 03:03 1788242    /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b7f57000-b7f59000 rw-p b7f57000 00:00 0 
b7f59000-b7f72000 r-xp 00000000 03:03 426006     /lib/ld-2.4.so
b7f72000-b7f74000 rw-p 00018000 03:03 426006     /lib/ld-2.4.so
bfbfe000-bfc13000 rw-p bfbfe000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

Any Idea will be appreciated. I'd hate to not be able to use skype under Linux and will have to use W....
Tnanks in advance!!!

---

### Post by Delkster on 2006-11-22
Skype doesn't seem to work with SCIM. I don't know exactly why but I also experienced the same issue.

Skype uses the Qt graphical toolkit for the user interface. KDE (in Kubuntu) also uses Qt, but Gnome (in Ubuntu) uses GTK. If you use Ubuntu (and generally Gnome applications instead of KDE ones) you could try disabling SCIM for Qt applications. SCIM won't work in Qt and KDE applications if you do that, but maybe that's not a big deal if you mostly use GTK/Gnome applications.

I don't know if it's possible to enable SCIM only for GTK and disable it for Qt using im-switch (I actually did the same thing in another way because I didn't even know about the im-switch command until now). However, you could try removing the scim-qtimm package for the same effect:

1. Open **System > Administration > Synaptic Package Manager**
2. Use the search to find the **scim-qtimm** package and mark it for removal
3. Apply the changes

---

### Post by freshmaker on 2006-11-22
Did not expected such a quick solution... :D 
Thanks Delkster
I will test it and try to find more detailed answer but this made my Skype run again.
Lots of Appreciation....

freshmaker

---

### Post by ]Nbx*cmD[ on 2007-02-08
Hi,

This solution might work, but in my old laptop I was able to run Skype while having SCIM configured and working. Now I tried to install both in my new laptop and skype won't start anymore, the output message is the same:

```

*** glibc detected *** skype: free(): invalid pointer: 0x08aba0b8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73998bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7399a44]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7158fc1]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb7135d3d]
/usr/lib/libscim-1.0.so.8[0xb6cce633]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xb6ccf8c7]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xb6cca0c5]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xb6d6acf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xb6d6cace]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xb6d65cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7b5001f]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7b4fbec]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xb6e8c85b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xb6e8ca0f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xb6e8cc7e]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7b4fc10]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb78a2a8d]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb78a2d93]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7a2319d]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb79ea49e]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb79e4d68]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb79e8021]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb73488cc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 08:01 522164     /usr/bin/skype
08988000-08ac4000 rw-p 08988000 00:00 0          [heap]
b6b00000-b6b21000 rw-p b6b00000 00:00 0 
b6b21000-b6c00000 ---p b6b21000 00:00 0 
b6c41000-b6c65000 r-xp 00000000 08:01 704698     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6c65000-b6c66000 rw-p 00024000 08:01 704698     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6c66000-b6d3b000 r-xp 00000000 08:01 81851      /usr/lib/libscim-1.0.so.8.1.0
b6d3b000-b6d49000 rw-p 000d5000 08:01 81851      /usr/lib/libscim-1.0.so.8.1.0
b6d4b000-b6d56000 r-xp 00000000 08:01 704699     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6d56000-b6d57000 rw-p 0000a000 08:01 704699     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6d57000-b6d75000 r-xp 00000000 08:01 705316     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6d75000-b6d76000 rw-p 0001e000 08:01 705316     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6d76000-b6de7000 r--p 00000000 08:01 686214     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6de7000-b6e11000 r-xp 00000000 08:01 81701      /usr/lib/liblcms.so.1.0.15
b6e11000-b6e12000 rw-p 00029000 08:01 81701      /usr/lib/liblcms.so.1.0.15
b6e12000-b6e15000 rw-p b6e12000 00:00 0 
b6e15000-b6e80000 r-xp 00000000 08:01 81732      /usr/lib/libmng.so.1.1.0.9
b6e80000-b6e83000 rw-p 0006a000 08:01 81732      /usr/lib/libmng.so.1.1.0.9
b6e87000-b6e90000 r-xp 00000000 08:01 704696     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6e90000-b6e91000 rw-p 00008000 08:01 704696     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6e91000-b6ebb000 r-xp 00000000 08:01 523439     /usr/lib/libkdefx.so.4.2.0
b6ebb000-b6ebc000 rw-p 00029000 08:01 523439     /usr/lib/libkdefx.so.4.2.0
b6ebc000-b6ebe000 r-xp 00000000 08:01 81855      /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6ebe000-b6ebf000 rw-p 00001000 08:01 81855      /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6ebf000-b6ec3000 r-xp 00000000 08:01 704697     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6ec3000-b6ec4000 rw-p 00003000 08:01 704697     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6ec4000-b6ec9000 r-xp 00000000 08:01 704694     /usr/lib/qt3/plugins/imageformats/libqmng.so
b6ec9000-b6eca000 rw-p 00004000 08:01 704694     /usr/lib/qt3/plugins/imageformats/libqmng.so
b6eca000-b6ee8000 r-xp 00000000 08:01 928600     /usr/lib/kde3/plugins/styles/plastik.so
b6ee8000-b6ee9000 rw-p 0001e000 08:01 928600     /usr/lib/kde3/plugins/styles/plastik.so
b6ee9000-b6eea000 ---p b6ee9000 00:00 0 
b6eea000-b6f6a000 rw-p b6eea000 00:00 0 
b6f6a000-b6f6b000 r-xp 00000000 08:01 537892     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b6f6b000-b6f6c000 rw-p 00000000 08:01 537892     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b6f6c000-b6f9f000 r--p 00000000 08:01 570759     /usr/lib/locale/ca_ES.utf8/LC_CTYPE
b6f9f000-b6fa0000 r--p 00000000 08:01 570764     /usr/lib/locale/ca_ES.utf8/LC_NUMERIC
b6fa0000-b6fa1000 r--p 00000000 08:01 570767     /usr/lib/locale/ca_ES.utf8/LC_TIME
b6fa1000-b7078000 r--p 00000000 08:01 570758     /usr/lib/locale/ca_ES.utf8/LC_COLLATE
b7078000-b7079000 r--p 00000000 08:01 570762     /usr/lib/locale/ca_ES.utf8/LC_MONETARY
b7079000-b707c000 rw-p b7079000 00:00 0 
b707c000-b7080000 r-xp 00000000 08:01 522485     /usr/lib/libXfixes.so.3.1.0
b7080000-b7081000 rw-p 00003000 08:01 522485     /usr/lib/libXfixes.so.3.1.0
b7081000-b709d000 r-xp 00000000 08:01 522664     /usr/lib/libexpat.so.1.0.0
b709d000-b709f000 rw-p 0001c000 08:01 522664     /usr/lib/libexpat.so.1.0.0
b709f000-b70a3000 r-xp 00000000 08:01 522479     /usr/lib/libXdmcp.so.6.0.0
b70a3000-b70a4000 rw-p 00003000 08:01 522479     /usr/lib/libXdmcp.so.6.0.0
b70a4000-b70a6000 r-xp 00000000 08:01 522470     /usr/lib/libXau.so.6.0.0
b70a6000-b70a7000 rw-p 00001000 08:01 522470     /usr/lib/libXau.so.6.0.0
b70a7000-b70a8000 rw-p b70a7000 00:00 0 
b70a8000-b717c000 r-xp 00000000 08:01 81892      /usr/lib/libstdc++.so.6.0.8
b717c000-b717f000 r--p 000d4000 08:01 81892      /usr/lib/libstdc++.so.6.0.8
b717f000-b7181000 rw-p 000d7000 08:01 81892      /usr/lib/libstdc++.so.6.0.8
b7181000-b7187000 rw-p b7181000 00:00 0 
b7187000-b719c000 r-xp 00000000 08:01 522442     /usr/lib/libICE.so.6.3.0
b719c000-b719d000 rw-p 00014000 08:01 522442     /usr/lib/libICE.so.6.3.0
b719d000-b719f000 rw-p b719d000 00:00 0 
b719f000-b71a7000 r-xp 00000000 08:01 522460     /usr/lib/libSM.so.6.0.0
b71a7000-b71a8000 rw-p 00007000 08:01 522460     /usr/lib/libSM.so.6.0.0
b71a8000-b720f000 r-xp 00000000 08:01 522680     /usr/lib/libfreetype.so.6.3.10
b720f000-b7212000 rw-p 00067000 08:01 522680     /usr/lib/libfreetype.so.6.3.10
b7212000-b7223000 r-xp 00000000 08:01 522489     /usr/lib/libXft.so.2.1.2
b7223000-b7224000 rw-p 00010000 08:01 522489     /usr/lib/libXft.so.2.1.2
b7224000-b7226000 r-xp 00000000 08:01 522493     /usr/lib/libXinerama.so.1.0.0
b7226000-b7227000 rw-p 00001000 08:01 522493     /usr/lib/libXinerama.so.1.0.0
b7227000-b7228000 rw-p b7227000 00:00 0 
b7228000-b7230000 r-xp 00000000 08:01 522475     /usr/lib/libXcursor.so.1.0.2
b7230000-b7231000 rw-p 00007000 08:01 522475     /usr/lib/libXcursor.so.1.0.2
b7231000-b7233000 r-xp 00000000 08:01 522503     /usr/lib/libXrandr.so.2.0.0
b7233000-b7234000 rw-p 00002000 08:01 522503     /usr/lib/libXrandr.so.2.0.0
b7234000-b723b000 r-xp 00000000 08:01 522505     /usr/lib/libXrender.so.1.3.0
b723b000-b723c000 rw-p 00006000 08:01 522505     /usr/lib/libXrender.so.1.3.0
b723c000-b7243000 r-xp 00000000 08:01 522491     /usr/lib/libXi.so.6.0.0
b7243000-b7244000 rw-p 00006000 08:01 522491     /usr/lib/libXi.so.6.0.0
b7244000-b7257000 r-xp 00000000 08:01 81949      /usr/lib/libz.so.1.2.3
b7257000-b7258000 rw-p 00012000 08:01 81949      /usr/lib/libz.so.1.2.3
b7258000-b727b000 r-xp 00000000 08:01 522223     /usr/lib/libpng12.so.0.1.2.8
b727b000-b727c000 rw-p 00023000 08:01 522223     /usr/lib/libpng12.so.0.1.2.8
b727c000-b727d000 rw-p b727c000 00:00 0 
b727d000-b729b000 r-xp 00000000 08:01 81685      /usr/lib/libjpeg.so.62.0.0
b729b000-b729c000 rw-p 0001d000 08:01 81685      /usr/lib/libjpeg.so.62.0.0
b729c000-b72e6000 r-xp 00000000 08:01 522509     /usr/lib/libXt.so.6.0.0
b72e6000-b72ea000 rw-p 00049000 08:01 522509     /usr/lib/libXt.so.6.0.0
b72ea000-b72ff000 r-xp 00000000 08:01 522546     /usr/lib/libaudio.so.2.4
b72ff000-b7300000 rw-p 00014000 08:01 522546     /usr/lib/libaudio.so.2.4
b7300000-b7329000 r-xp 00000000 08:01 522670     /usr/lib/libfontconfig.so.1.0.4
b7329000-b732e000 rw-p 00028000 08:01 522670     /usr/lib/libfontconfig.so.1.0.4
b732e000-b732f000 rw-p b732e000 00:00 0 
b732f000-b7331000 r-xp 00000000 08:01 195610     /lib/tls/i686/cmov/libdl-2.4.so
b7331000-b7333000 rw-p 00001000 08:01 195610     /lib/tls/i686/cmov/libdl-2.4.so
b7333000-b7460000 r-xp 00000000 08:01 195607     /lib/tls/i686/cmov/libc-2.4.so
b7460000-b7462000 r--p 0012c000 08:01 195607     /lib/tls/i686/cmov/libc-2.4.so
b7462000-b7464000 rw-p 0012e000 08:01 195607     /lib/tls/i686/cmov/libc-2.4.so
b7464000-b7468000 rw-p b7464000 00:00 0 
b7468000-b7472000 r-xp 00000000 08:01 162947     /lib/libgcc_s.so.1
b7472000-b7473000 rw-p 00009000 08:01 162947     /lib/libgcc_s.so.1
b7473000-b7497000 r-xp 00000000 08:01 195611     /lib/tls/i686/cmov/libm-2.4.so
b7497000-b7499000 rw-p 00023000 08:01 195611     /lib/tls/i686/cmov/libm-2.4.so
b7499000-b7549000 r-xp 00000000 08:01 81890      /usr/lib/libstdc++.so.5.0.7
b7549000-b754e000 rw-p 000af000 08:01 81890      /usr/lib/libstdc++.so.5.0.7
b754e000-b7553000 rw-p b754e000 00:00 0 
b7553000-b7562000 r-xp 00000000 08:01 195621     /lib/tls/i686/cmov/libpthread-2.4.so
b7562000-b7564000 rw-p 0000f000 08:01 195621     /lib/tls/i686/cmov/libpthread-2.4.so
b7564000-b7566000 rw-p b7564000 00:00 0 
b7566000-b762c000 r-xp 00000000 08:01 522464     /usr/lib/libX11.so.6.2.0
b762c000-b762f000 rw-p 000c5000 08:01 522464     /usr/lib/libX11.so.6.2.0
b762f000-b763b000 r-xp 00000000 08:01 522483     /usr/lib/libXext.so.6.4.0
b763b000-b763c000 rw-p 0000c000 08:01 522483     /usr/lib/libXext.so.6.4.0
b763c000-b763d000 rw-p b763c000 00:00 0 
b763d000-b7dd2000 r-xp 00000000 08:01 522997     /usr/lib/libqt-mt.so.3.3.6
b7dd2000-b7e19000 rw-p 00794000 08:01 522997     /usr/lib/libqt-mt.so.3.3.6
b7e19000-b7e1c000 rw-p b7e19000 00:00 0 
b7e1c000-b7ecf000 r-xp 00000000 08:01 522533     /usr/lib/libasound.so.2.0.0
b7ecf000-b7ed4000 rw-p 000b2000 08:01 522533     /usr/lib/libasound.so.2.0.0
b7ed4000-b7edb000 r-xp 00000000 08:01 195623     /lib/tls/i686/cmov/librt-2.4.so
b7edb000-b7edd000 rw-p 00006000 08:01 195623     /lib/tls/i686/cmov/librt-2.4.so
b7edd000-b7ede000 r--p 00000000 08:01 570768     /usr/lib/locale/ca_ES.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7ede000-b7edf000 r--p 00000000 08:01 570765     /usr/lib/locale/ca_ES.utf8/LC_PAPER
b7edf000-b7ee0000 r--p 00000000 08:01 570763     /usr/lib/locale/ca_ES.utf8/LC_NAME
b7ee0000-b7ee1000 r--p 00000000 08:01 570757     /usr/lib/locale/ca_ES.utf8/LC_ADDRESS
b7ee1000-b7ee2000 r--p 00000000 08:01 570766     /usr/lib/locale/ca_ES.utf8/LC_TELEPHONE
b7ee2000-b7ee3000 r--p 00000000 08:01 570761     /usr/lib/locale/ca_ES.utf8/LC_MEASUREMENT
b7ee3000-b7eea000 r--s 00000000 08:01 538412     /usr/lib/gconv/gconv-modules.cache
b7eea000-b7eeb000 r--p 00000000 08:01 570760     /usr/lib/locale/ca_ES.utf8/LC_IDENTIFICATION
b7eeb000-b7eed000 rw-p b7eeb000 00:00 0 
b7eed000-b7f06000 r-xp 00000000 08:01 165181     /lib/ld-2.4.so
b7f06000-b7f08000 rw-p 00018000 08:01 165181     /lib/ld-2.4.so
bfbc9000-bfbde000 rw-p bfbc9000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

I'm 100% sure there's a way to run skype without having to uninstall scim, since I had both working in Edgy Eft once, can anybody help me?

---

### Post by ]Nbx*cmD[ on 2007-02-09
Ok, found the solution, sorry.
Just start skype from the command line as follows:

```
XMODIFIERS=@im=none QT_IM_MODULE=xim skype
```

What i just did is to enter this line in a shellscript.

Btw, this won't allow skype to use scim input method, it will just start skype in xim method. If you try to switch to scim, skype will just crash. This is a skype issue, and since it's not free software we'll have to wait for their developers to decide to fix it, if they ever do.

---

### Post by lanchongzi on 2007-02-10
> **']Nbx*cmD[ said:**
> Ok, found the solution, sorry.
Just start skype from the command line as follows:

```
XMODIFIERS=@im=none QT_IM_MODULE=xim skype
```

What i just did is to enter this line in a shellscript.

Btw, this won't allow skype to use scim input method, it will just start skype in xim method. If you try to switch to scim, skype will just crash. This is a skype issue, and since it's not free software we'll have to wait for their developers to decide to fix it, if they ever do.



does work in Xubuntu as well??
cause I am having the same problems with the result of installing Xubuntu again
now I am looking for a way to install Ubuntu ( harder then I thought!!:( )
but if your method works in Xubuntu as well i just wont have to

since i kinda like the simplistic outfit of it:)

---

### Post by ]Nbx*cmD[ on 2007-02-25
Yeah it must work in every gnu/linux distro ever imaginable ;)

---

### Post by ]Nbx*cmD[ on 2007-02-25
By the way, just to help you save time, i attach the script to this post.

---

