---
title: "Ubuntu 13.04 molt inestable?"
date: 2013-05-08
forum: Catalan Team
---

### Post by serracat on 2013-05-08
Bones, fa un parell de dies m'he actualitzat a l'Ubuntu 13.04 (venint del 12.10), vaig actualitzar-me perquè el 12.10 em "petava" per tot arreu, però ara es molt més exagerat, gairebé amb tots els programes al fer clic amb el boto dret (i de vegades ni fent clic amb el boto dret), es tanquen i/o reinicien


Una mica d'informació del pc:
```

Ubuntu 13.04 32b
Intel® Core™ i5 CPU M 520 @ 2.40GHz × 4 
Gallium 0.4 on AMD RV710
RAM 4GB
```


Us poso el que mostra la terminal quan obro el Rhythmbox ja que només iniciant-lo es tanca.

Just quan es tanca posa: 

*a667a000-a667f000 r-xp 00000000 08:06 4982797    /usr/lib/python2.7/dist-packages/gi/_glib/_glib.soUnable to open ~/.mtpz-data for reading, MTPZ disabled.Avortat (bolcat de la imatge del nucli)*

Què vol dir *bolcat de la imatge del nucli*? Pot ser que sigui alguna cosa del python?

Moltes gràcies.


```

Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/ubuntuone/ubuntuone.py", line 21, in <module>
    from dbus import SessionBus, DBusException
  File "/usr/lib/python2.7/dist-packages/dbus/__init__.py", line 103, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 39, in <module>
    from dbus.bus import BusConnection
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 39, in <module>
    from dbus.connection import Connection
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 37, in <module>
    from dbus.proxies import ProxyObject
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 34, in <module>
    from dbus._expat_introspect_parser import process_introspection_data
  File "/usr/lib/python2.7/dist-packages/dbus/_expat_introspect_parser.py", line 26, in <module>
    from xml.parsers.expat import ParserCreate
  File "/usr/local/lib/python2.7/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: /usr/local/lib/python2.7/lib-dynload/pyexpat.so: undefined symbol: PyUnicodeUCS2_Decode


(rhythmbox:11308): libpeas-WARNING **: Error loading plugin 'ubuntuone'
*** Error in `rhythmbox': free(): corrupted unsorted chunks: 0x08a82e40 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x767e2)[0xb6fc37e2]
/lib/i386-linux-gnu/libc.so.6(+0x77530)[0xb6fc4530]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_ZdlPv+0x1f)[0xb3d09b4f]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_ZNSbIwSt11char_traitsIwESaIwEE4_Rep10_M_destroyERKS1_+0x1b)[0xb3d7535b]
/usr/lib/i386-linux-gnu/pango/1.8.0/modules/graphite/pango-graphite.so(_ZN2gr12FreetypeFontD1Ev+0xb9)[0xb0b3f1a9]
/usr/lib/i386-linux-gnu/pango/1.8.0/modules/graphite/pango-graphite.so(_ZN2gr11PangoGrFontD1Ev+0x39)[0xb0b40339]
/usr/lib/i386-linux-gnu/pango/1.8.0/modules/graphite/pango-graphite.so(_ZN2gr11PangoGrFontD0Ev+0x22)[0xb0b40382]
/usr/lib/i386-linux-gnu/pango/1.8.0/modules/graphite/pango-graphite.so(graphite_PangoGlyphString+0x141)[0xb0b41681]
/usr/lib/i386-linux-gnu/pango/1.8.0/modules/graphite/pango-graphite.so(+0x723b)[0xb0b4223b]
/usr/lib/i386-linux-gnu/libpango-1.0.so.0(+0x18c8e)[0xb5063c8e]
/usr/lib/i386-linux-gnu/libpango-1.0.so.0(pango_shape_full+0xf4)[0xb50751d4]
/usr/lib/i386-linux-gnu/libpango-1.0.so.0(+0x9e18)[0xb5054e18]
/usr/lib/i386-linux-gnu/libpango-1.0.so.0(+0xa146)[0xb5055146]
/usr/lib/i386-linux-gnu/libpango-1.0.so.0(+0x1f9f3)[0xb506a9f3]
/usr/lib/i386-linux-gnu/libpango-1.0.so.0(+0x20920)[0xb506b920]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0x18986c)[0xb528686c]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0x2225fb)[0xb531f5fb]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0xa2a7a)[0xb519fa7a]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0x2225fb)[0xb531f5fb]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0x158344)[0xb5255344]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0x2225fb)[0xb531f5fb]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0xa2a7a)[0xb519fa7a]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0x2225fb)[0xb531f5fb]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0xa2a7a)[0xb519fa7a]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0x2225fb)[0xb531f5fb]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0x2fc7f0)[0xb53f97f0]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0x2225fb)[0xb531f5fb]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(gtk_widget_get_preferred_size+0xac)[0xb531fcac]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0x2fd81b)[0xb53fa81b]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0x3045b3)[0xb54015b3]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOIDv+0x2a)[0xb722c9ea]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xc587)[0xb7229587]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xdee1)[0xb722aee1]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x4da)[0xb724465a]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x33)[0xb7245233]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(gtk_container_check_resize+0x8a)[0xb51ec7ca]
/usr/lib/i386-linux-gnu/libgtk-3.so.0(+0xefaaa)[0xb51ecaaa]
/usr/lib/i386-linux-gnu/libgdk-3.so.0(+0x141de)[0xb73e51de]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x44f10)[0xb7160f10]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x143)[0xb71643b3]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x48750)[0xb7164750]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_context_iteration+0x41)[0xb7164831]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(g_application_run+0x1cc)[0xb730bcfc]
rhythmbox(main+0x15f)[0x8048c0f]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf5)[0xb6f66935]
rhythmbox[0x8048c69]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:06 4989979    /usr/bin/rhythmbox
08049000-0804a000 r--p 00001000 08:06 4989979    /usr/bin/rhythmbox
0804a000-0804b000 rw-p 00002000 08:06 4989979    /usr/bin/rhythmbox
0863a000-096ca000 rw-p 00000000 00:00 0          [heap]
a08a3000-a5d6a000 r--p 00000000 08:06 5505908    /usr/share/icons/gnome/icon-theme.cache
a5d6a000-a5d8f000 r-xp 00000000 08:06 4984919    /usr/lib/libbrasero-media3.so.1.2.3
a5d8f000-a5d90000 r--p 00024000 08:06 4984919    /usr/lib/libbrasero-media3.so.1.2.3
a5d90000-a5d91000 rw-p 00025000 08:06 4984919    /usr/lib/libbrasero-media3.so.1.2.3
a5dae000-a5dbb000 r-xp 00000000 08:06 5115836    /usr/lib/rhythmbox/plugins/generic-player/libgeneric-player.so
a5dbb000-a5dbc000 r--p 0000c000 08:06 5115836    /usr/lib/rhythmbox/plugins/generic-player/libgeneric-player.so
a5dbc000-a5dbd000 rw-p 0000d000 08:06 5115836    /usr/lib/rhythmbox/plugins/generic-player/libgeneric-player.so
a5dbd000-a5dc8000 r-xp 00000000 08:06 5115648    /usr/lib/rhythmbox/plugins/dbus-media-server/libdbus-media-server.so
a5dc8000-a5dc9000 r--p 0000a000 08:06 5115648    /usr/lib/rhythmbox/plugins/dbus-media-server/libdbus-media-server.so
a5dc9000-a5dca000 rw-p 0000b000 08:06 5115648    /usr/lib/rhythmbox/plugins/dbus-media-server/libdbus-media-server.so
a5dca000-a5dea000 r-xp 00000000 08:06 5115597    /usr/lib/rhythmbox/plugins/audioscrobbler/libaudioscrobbler.so
a5dea000-a5deb000 r--p 0001f000 08:06 5115597    /usr/lib/rhythmbox/plugins/audioscrobbler/libaudioscrobbler.so
a5deb000-a5dec000 rw-p 00020000 08:06 5115597    /usr/lib/rhythmbox/plugins/audioscrobbler/libaudioscrobbler.so
a5dec000-a5e03000 r-xp 00000000 08:06 4983918    /usr/lib/libimobiledevice.so.3.0.1
a5e03000-a5e04000 r--p 00016000 08:06 4983918    /usr/lib/libimobiledevice.so.3.0.1
a5e04000-a5e05000 rw-p 00017000 08:06 4983918    /usr/lib/libimobiledevice.so.3.0.1
a5e05000-a5e71000 r-xp 00000000 08:06 4983620    /usr/lib/i386-linux-gnu/libgpod.so.4.3.2
a5e71000-a5e72000 ---p 0006c000 08:06 4983620    /usr/lib/i386-linux-gnu/libgpod.so.4.3.2
a5e72000-a5e76000 r--p 0006c000 08:06 4983620    /usr/lib/i386-linux-gnu/libgpod.so.4.3.2
a5e76000-a5e77000 rw-p 00070000 08:06 4983620    /usr/lib/i386-linux-gnu/libgpod.so.4.3.2
a5e77000-a5e78000 rw-p 00000000 00:00 0 
a5e78000-a5e7d000 r-xp 00000000 08:06 5115567    /usr/lib/rhythmbox/plugins/cd-recorder/libcd-recorder.so
a5e7d000-a5e7e000 r--p 00004000 08:06 5115567    /usr/lib/rhythmbox/plugins/cd-recorder/libcd-recorder.so
a5e7e000-a5e7f000 rw-p 00005000 08:06 5115567    /usr/lib/rhythmbox/plugins/cd-recorder/libcd-recorder.so
a5e7f000-a5e82000 r-xp 00000000 08:06 5115828    /usr/lib/rhythmbox/plugins/mmkeys/libmmkeys.so
a5e82000-a5e83000 r--p 00003000 08:06 5115828    /usr/lib/rhythmbox/plugins/mmkeys/libmmkeys.so
a5e83000-a5e84000 rw-p 00004000 08:06 5115828    /usr/lib/rhythmbox/plugins/mmkeys/libmmkeys.so
a5e84000-a5e87000 r-xp 00000000 08:06 4984979    /usr/lib/i386-linux-gnu/gio/modules/libgiognomeproxy.so
a5e87000-a5e88000 r--p 00002000 08:06 4984979    /usr/lib/i386-linux-gnu/gio/modules/libgiognomeproxy.so
a5e88000-a5e89000 rw-p 00003000 08:06 4984979    /usr/lib/i386-linux-gnu/gio/modules/libgiognomeproxy.so
a5e89000-a5e93000 r-xp 00000000 08:06 5115826    /usr/lib/rhythmbox/plugins/iradio/libiradio.so
a5e93000-a5e94000 r--p 00009000 08:06 5115826    /usr/lib/rhythmbox/plugins/iradio/libiradio.so
a5e94000-a5e95000 rw-p 0000a000 08:06 5115826    /usr/lib/rhythmbox/plugins/iradio/libiradio.so
a5e95000-a5ea7000 r-xp 00000000 08:06 5115626    /usr/lib/rhythmbox/plugins/ipod/libipod.so
a5ea7000-a5ea8000 r--p 00011000 08:06 5115626    /usr/lib/rhythmbox/plugins/ipod/libipod.so
a5ea8000-a5ea9000 rw-p 00012000 08:06 5115626    /usr/lib/rhythmbox/plugins/ipod/libipod.so
a5ea9000-a5eba000 r-xp 00000000 08:06 4719191    /lib/i386-linux-gnu/libusb-1.0.so.0.1.0
a5eba000-a5ebb000 r--p 00010000 08:06 4719191    /lib/i386-linux-gnu/libusb-1.0.so.0.1.0
a5ebb000-a5ebc000 rw-p 00011000 08:06 4719191    /lib/i386-linux-gnu/libusb-1.0.so.0.1.0
a5ebc000-a5eff000 r-xp 00000000 08:06 4980943    /usr/lib/i386-linux-gnu/libmtp.so.9.0.5
a5eff000-a5f02000 r--p 00043000 08:06 4980943    /usr/lib/i386-linux-gnu/libmtp.so.9.0.5
a5f02000-a5f09000 rw-p 00046000 08:06 4980943    /usr/lib/i386-linux-gnu/libmtp.so.9.0.5
a5f0d000-a5f13000 r-xp 00000000 08:06 4986232    /usr/lib/libusbmuxd.so.1.0.8
a5f13000-a5f14000 r--p 00005000 08:06 4986232    /usr/lib/libusbmuxd.so.1.0.8
a5f14000-a5f15000 rw-p 00006000 08:06 4986232    /usr/lib/libusbmuxd.so.1.0.8
a5f15000-a5f24000 r-xp 00000000 08:06 5116065    /usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so
a5f24000-a5f25000 r--p 0000e000 08:06 5116065    /usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so
a5f25000-a5f26000 rw-p 0000f000 08:06 5116065    /usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so
a5f26000-a5f39000 r-xp 00000000 08:06 5115633    /usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so
a5f39000-a5f3a000 r--p 00012000 08:06 5115633    /usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so
a5f3a000-a5f3b000 rw-p 00013000 08:06 5115633    /usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so
a5f3b000-a5f46000 r-xp 00000000 08:06 4719003    /lib/i386-linux-gnu/libnss_files-2.17.so
a5f46000-a5f47000 r--p 0000a000 08:06 4719003    /lib/i386-linux-gnu/libnss_files-2.17.so
a5f47000-a5f48000 rw-p 0000b000 08:06 4719003    /lib/i386-linux-gnu/libnss_files-2.17.so
a5f48000-a5f5d000 r-xp 00000000 08:06 4719023    /lib/i386-linux-gnu/libnsl-2.17.so
a5f5d000-a5f5e000 r--p 00014000 08:06 4719023    /lib/i386-linux-gnu/libnsl-2.17.so
a5f5e000-a5f5f000 rw-p 00015000 08:06 4719023    /lib/i386-linux-gnu/libnsl-2.17.so
a5f5f000-a5f61000 rw-p 00000000 00:00 0 
a5f62000-a5f6b000 r-xp 00000000 08:06 4983840    /usr/lib/libplist.so.1.1.8
a5f6b000-a5f6c000 r--p 00008000 08:06 4983840    /usr/lib/libplist.so.1.1.8
a5f6c000-a5f6d000 rw-p 00009000 08:06 4983840    /usr/lib/libplist.so.1.1.8
a5f6d000-a5f76000 r-xp 00000000 08:06 5115631    /usr/lib/rhythmbox/plugins/mpris/libmpris.so
a5f76000-a5f77000 ---p 00009000 08:06 5115631    /usr/lib/rhythmbox/plugins/mpris/libmpris.so
a5f77000-a5f78000 r--p 00009000 08:06 5115631    /usr/lib/rhythmbox/plugins/mpris/libmpris.so
a5f78000-a5f79000 rw-p 0000a000 08:06 5115631    /usr/lib/rhythmbox/plugins/mpris/libmpris.so
a5f79000-a5f7c000 r-xp 00000000 08:06 5116066    /usr/lib/rhythmbox/plugins/power-manager/libpower-manager.so
a5f7c000-a5f7d000 r--p 00002000 08:06 5116066    /usr/lib/rhythmbox/plugins/power-manager/libpower-manager.so
a5f7d000-a5f7e000 rw-p 00003000 08:06 5116066    /usr/lib/rhythmbox/plugins/power-manager/libpower-manager.so
a5f7e000-a5f81000 r-xp 00000000 08:06 4983568    /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
a5f81000-a5f82000 r--p 00002000 08:06 4983568    /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
a5f82000-a5f83000 rw-p 00003000 08:06 4983568    /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
a5f83000-a5f93000 r-xp 00000000 08:06 4985564    /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
a5f93000-a5f94000 r--p 0000f000 08:06 4985564    /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
a5f94000-a5f95000 rw-p 00010000 08:06 4985564    /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
a5f95000-a5fa1000 r-xp 00000000 08:06 4986282    /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
a5fa1000-a5fa2000 r--p 0000b000 08:06 4986282    /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
a5fa2000-a5fa3000 rw-p 0000c000 08:06 4986282    /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
a5fa3000-a5fcb000 r-xp 00000000 08:06 4983833    /usr/lib/libdmapsharing-3.0.so.2.9.15
a5fcb000-a5fcd000 r--p 00027000 08:06 4983833    /usr/lib/libdmapsharing-3.0.so.2.9.15
a5fcd000-a5fce000 rw-p 00029000 08:06 4983833    /usr/lib/libdmapsharing-3.0.so.2.9.15
a5fce000-a5fd6000 rw-p 00000000 00:00 0 
a5fd6000-a5fe0000 r-xp 00000000 08:06 4719014    /lib/i386-linux-gnu/libnss_nis-2.17.so
a5fe0000-a5fe1000 r--p 00009000 08:06 4719014    /lib/i386-linux-gnu/libnss_nis-2.17.so
a5fe1000-a5fe2000 rw-p 0000a000 08:06 4719014    /lib/i386-linux-gnu/libnss_nis-2.17.so
a5fe2000-a5fe9000 r-xp 00000000 08:06 4718739    /lib/i386-linux-gnu/libnss_compat-2.17.so
a5fe9000-a5fea000 r--p 00006000 08:06 4718739    /lib/i386-linux-gnu/libnss_compat-2.17.so
a5fea000-a5feb000 rw-p 00007000 08:06 4718739    /lib/i386-linux-gnu/libnss_compat-2.17.so
a5ff3000-a600b000 r-xp 00000000 08:06 4981259    /usr/lib/python2.7/dist-packages/_dbus_bindings.so
a600b000-a600c000 r--p 00017000 08:06 4981259    /usr/lib/python2.7/dist-packages/_dbus_bindings.so
a600c000-a6018000 rw-p 00018000 08:06 4981259    /usr/lib/python2.7/dist-packages/_dbus_bindings.so
a6018000-a613c000 rw-p 00000000 00:00 0 
a613c000-a615a000 r-xp 00000000 08:06 4981806    /usr/lib/python2.7/dist-packages/gi/_gobject/_gobject.so
a615a000-a615b000 r--p 0001d000 08:06 4981806    /usr/lib/python2.7/dist-packages/gi/_gobject/_gobject.so
a615b000-a615d000 rw-p 0001e000 08:06 4981806    /usr/lib/python2.7/dist-packages/gi/_gobject/_gobject.so
a615d000-a617e000 r-xp 00000000 08:06 4981805    /usr/lib/python2.7/dist-packages/gi/_gi.so
a617e000-a617f000 r--p 00021000 08:06 4981805    /usr/lib/python2.7/dist-packages/gi/_gi.so
a617f000-a6182000 rw-p 00022000 08:06 4981805    /usr/lib/python2.7/dist-packages/gi/_gi.so
a6182000-a6204000 rw-p 00000000 00:00 0 
a6204000-a6494000 r-xp 00000000 08:06 4982181    /usr/lib/i386-linux-gnu/libpython2.7.so.1.0
a6494000-a6495000 r--p 00290000 08:06 4982181    /usr/lib/i386-linux-gnu/libpython2.7.so.1.0
a6495000-a64f4000 rw-p 00291000 08:06 4982181    /usr/lib/i386-linux-gnu/libpython2.7.so.1.0
a64f4000-a6500000 rw-p 00000000 00:00 0 
a6500000-a6521000 rw-p 00000000 00:00 0 
a6521000-a6600000 ---p 00000000 00:00 0 
a6602000-a6603000 rwxp 00000000 00:00 0 
a6603000-a6618000 r-xp 00000000 08:06 5115652    /usr/lib/rhythmbox/plugins/daap/libdaap.so
a6618000-a6619000 r--p 00014000 08:06 5115652    /usr/lib/rhythmbox/plugins/daap/libdaap.so
a6619000-a661a000 rw-p 00015000 08:06 5115652    /usr/lib/rhythmbox/plugins/daap/libdaap.so
a661a000-a661d000 r-xp 00000000 08:06 4981804    /usr/lib/i386-linux-gnu/libpyglib-gi-2.0-python2.7.so.0.0.0
a661d000-a661e000 r--p 00002000 08:06 4981804    /usr/lib/i386-linux-gnu/libpyglib-gi-2.0-python2.7.so.0.0.0
a661e000-a661f000 rw-p 00003000 08:06 4981804    /usr/lib/i386-linux-gnu/libpyglib-gi-2.0-python2.7.so.0.0.0
a661f000-a6660000 rw-p 00000000 00:00 0 
a6660000-a6662000 r-xp 00000000 08:06 4719021    /lib/i386-linux-gnu/libutil-2.17.so
a6662000-a6663000 r--p 00001000 08:06 4719021    /lib/i386-linux-gnu/libutil-2.17.so
a6663000-a6664000 rw-p 00002000 08:06 4719021    /lib/i386-linux-gnu/libutil-2.17.so
a6664000-a6665000 r-xp 00000000 08:06 4984051    /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-cedilla.so
a6665000-a6666000 r--p 00000000 08:06 4984051    /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-cedilla.so
a6666000-a6667000 rw-p 00001000 08:06 4984051    /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-cedilla.so
a6667000-a6676000 r-xp 00000000 08:06 6947750    /usr/local/lib/python2.7/lib-dynload/datetime.so
a6676000-a6677000 r--p 0000e000 08:06 6947750    /usr/local/lib/python2.7/lib-dynload/datetime.so
a6677000-a667a000 rw-p 0000f000 08:06 6947750    /usr/local/lib/python2.7/lib-dynload/datetime.so
a667a000-a667f000 r-xp 00000000 08:06 4982797    /usr/lib/python2.7/dist-packages/gi/_glib/_glib.soUnable to open ~/.mtpz-data for reading, MTPZ disabled.Avortat (bolcat de la imatge del nucli)



```

---

### Post by serracat on 2013-05-08
Quan es tanca el Chrome, em diu això:

```

[11852:11877:0508/181641:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[11852:11877:0508/181641:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[11852:11852:0508/181642:ERROR:omnibox_view_gtk.cc(431)] Not implemented reached in virtual void OmniboxViewGtk::ApplyCaretVisibility()
[11852:11852:0508/181642:ERROR:object_proxy.cc(529)] Failed to call method: org.chromium.Mtpd.EnumerateStorages: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files
[11852:11852:0508/181646:ERROR:omnibox_view_gtk.cc(431)] Not implemented reached in virtual void OmniboxViewGtk::ApplyCaretVisibility()
[11852:11852:0508/181649:ERROR:omnibox_view_gtk.cc(431)] Not implemented reached in virtual void OmniboxViewGtk::ApplyCaretVisibility()
Violació de segment (bolcat de la imatge del nucli)

```

---

### Post by wgarcia on 2013-05-08
Jo tinc un maquinari molt semblant al teu i tinc l'experiència contrària, estic a la 13.04 des de quasi dos mesos abans del llançament i per a mi ha estat una de les versions més estables i de ràpida resposta des que faig servir Ubuntu. 

Sembla que tens algun problema seriós d'instal·lació. El primer missatge m'havia fet pensar que potser hi havia algun problema de permisos al teu directori d'usuari, però el segon sembla molt diferent. 

Una prova que es pot fer és intentar entrar amb un altre usuari per descartar allò dels permisos d'usuari, tot i que com dic segons el segon missatge el problema sembla no ser això. 

Una altra cosa que es pot provar és iniciar la sessió des de un USB o CD autònom (LIVE) i veure què tal funciona el sistema des d'aquí, en cas que funcioni bé confirma que hi ha algun problema amb la instal·lació. Pot ser el problema s'arrossega des de la 12.10, com vas actualitzar, directament des de la 12.10 o vas fer instal·lació nova?

---

### Post by serracat on 2013-05-12
Vaig actualitzar des de la versió 12.10. 
Ara he provat de fer un usuari nou, i el resultat es el mateix... 
Provaré d'arrencar des de un USB però crec que serà que arrossego algun error com dius. Hi ha alguna manera de fer una instal·lació nova mantenint els programes? o potser el problema és d'algun programa i millor faig una instal·lació de 0?

---

### Post by wgarcia on 2013-05-12
Difícilment un sol programa pot generar els símptomes que veus. 

Molt important: Fes una còpia de les dades importants que tinguis, per si un cas (tot i que això de la còpia és important sempre, un disc dur o qualsevol component pot fallar en qualsevol moment). 

Primer prova què fa el sistema des del CD o USB autònom, i sí que hi ha manera de tornar a instal·lar tots els programes a una instal·lació nova, però primer convindria mirar si es pot arreglar el problema sense reinstal·lar (hi ha gent que prefereix reinstal·.lar, i fins i tot fer sempre actualitzacions a partir d'instal·lacions noves, però no és el meu cas, prefereixo sempre actualitzar des de la versió existent i si hi ha algun problema intentar esbrinar-lo i arreglar-lo).

---

### Post by serracat on 2013-05-27
Hola wgarcia, al final vaig reinstal·lar jaja, com dius, tampoc no m'agrada reinstal·lar sense abans buscar el problema, però es que era molt inestable, i després de provar amb un live-CD i veure que anava tant bé, va acabar de donar-me l'espenta per reinstal·lar-ho jeje.
[COLOR=#000000][/COLOR]
Ara això ja és una altre cosa (encara que no t'enganyaré, em "peta" per algun lloc de vegades), però bé, et voldria fer una pregunta, ja que vares dir que també tens el 13.04 instal·lat i un equip amb un maquinari semblant.

Quina temperatura tens de mitjana? És que de normal tinc la temperatura a uns 7Xº amb el cpufreq posat a Estalvi d'energia, "capant" una mica el processador.

I una altre pregunta, si em permets, Unity o Gnome3? Ara mateix tinc el gnome 3.8, i m'agradaria saber si algun dels problemes que puc tenir es causat pel gnome o no (que crec que és així...) :S

Moltes Gràcies avançades! Salut!

---

### Post by wgarcia on 2013-05-27
La meva temperatura és al voltant de 50º, i no tinc res configurat de freqüència de CPU. 

Faig servir Unity. Em sembla que per la 13.04 la versió de Gnome suportada és la 3.6, potser la 3.8 tingui algunes coses que no van del tot bé encara, em sembla que s'instal·la des d'una PPA, oi?

---

### Post by HermesM on 2013-06-09
Unity no m'agrada gaire però al començament vaig instal·lar Ubuntu-Gnome afegint-li Gnome 3.8 ¡Catastròfic! Sempre m'he servit de Gnome doncs, ara, amb aquesta guerra soterrada entre Canonical i Gnome els que rebem som els usuaris.
Ara tiro d'Unity, si més no em servirà d'entrenament per a la tablet que voldria comprar aquest any.

---

### Post by papapep on 2013-09-03
Hola a tothom, 

Ubuntu, tècnicament desconec el perquè, però "políticament" ho tindrem tots ben clar, no és, ni de bon tros, la distribució que dóna el millor suport ni la millor integració amb Gnome 3. Fa temps que empro la 3.6 i ara la 3.8 amb Fedora, i és una meravella de simple i funcional, mai havia treballat de forma tan àgil.
A Debian, evidentment, també funciona perfecte, però les versions són tan terriblement antigues...
El Unity, ben lluny, però molt. (per gustos els colors, oi?)

Tornant al tema original del fil, que l'heu segrestat vílment (llegi :P), serracat, el teu error original feia referència a les llibreries MTP (Unable to open ~/.mtpz-data for reading, **MTP**Z disabled.", que són les que gestionen la conexió dels aparells com telèfons "espavilats", tauletes, etc, a l'ordinador i per a què te'ls munti com una unitat d'emmagatzematge extern. Sòn necessàries amb l'Android a partir de la versió 3.5 en endavant, si no l'erro. Abans es muntaven automàgicament. 
Per això lliga l'error amb el fet de que te'l cantava quan obries el Rhythmbox, que també les deu fer servir per connectar-se als aparells aquests i sincronitzar les col·leccions musicals. Tot això m'ho empesco sense saber-ho del cert, però és lògic.

---

