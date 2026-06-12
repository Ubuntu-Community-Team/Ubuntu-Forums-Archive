---
title: "OpenOffice startup problem"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by -=Ghostlike=- on 2007-04-18
I use Feisty beta and my openoffice doesn't start, it gives an invalid pointer exception:

```
*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080d03b8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6c767cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6c79e30]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb72cb0bd]
/usr/lib/openoffice/program/soffice.bin[0x809192e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x8091966]
/usr/lib/libscim-1.0.so.8[0xa9771156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xa9771f77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xa976cf05]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xa980ff7b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb5c7fb41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa2f)[0xb5c661cf]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb5c665ef]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb5c667a0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xa9804b57]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xa981427c]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb575fd29]
/usr/lib/libgtk-x11-2.0.so.0[0xb576093b]
/usr/lib/libgtk-x11-2.0.so.0[0xb5760b39]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb575df0e]
/usr/lib/libgtk-x11-2.0.so.0[0xb570771f]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb5c6d9d9]
/usr/lib/libgobject-2.0.so.0[0xb5c5ee49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5c6062b]
/usr/lib/libgobject-2.0.so.0[0xb5c7159a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5c72627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5c727e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba)[0xb589bbea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de)[0xb589c1ce]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xd3)[0xb5734ec3]
/usr/lib/libgtk-x11-2.0.so.0[0xb5734f08]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59)[0xb5c6cee9]
/usr/lib/libgobject-2.0.so.0[0xb5c5ee49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5c6062b]
/usr/lib/libgobject-2.0.so.0[0xb5c7159a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5c72627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5c727e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c)[0xb56eb1bc]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb59cb2bd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb59cd043]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb59d7abd]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e26ff5]
/usr/lib/openoffice/program/libvcl680li.so[0xb7db409b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x67)[0xb7db4ac7]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x3e)[0xb788199e]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x4a)[0xb78531da]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x4f)[0xb785055f]
/usr/lib/openoffice/program/libspl680li.so[0xa992a926]
/usr/lib/openoffice/program/libspl680li.so[0xa9921024]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xd59)[0x806bc39]
/usr/lib/openoffice/program/libvcl680li.so[0xb7c34c3c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7c34d45]
/usr/lib/openoffice/program/soffice.bin(main+0x65)[0x805ff85]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6c24ebc]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x805fe11]
======= Memory map: ========
08048000-0809c000 r-xp 00000000 08:06 325753     /usr/lib/openoffice/program/soffice.bin
0809c000-0809e000 rw-p 00053000 08:06 325753     /usr/lib/openoffice/program/soffice.bin
0809e000-08358000 rw-p 0809e000 00:00 0          [heap]
a9600000-a9621000 rw-p a9600000 00:00 0 
a9621000-a9700000 ---p a9621000 00:00 0 
a9709000-a97dd000 r-xp 00000000 08:06 229521     /usr/lib/libscim-1.0.so.8.1.0
a97dd000-a97eb000 rw-p 000d4000 08:06 229521     /usr/lib/libscim-1.0.so.8.1.0
a97f8000-a9819000 r-xp 00000000 08:06 292697     /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a9819000-a981a000 rw-p 00021000 08:06 292697     /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a981a000-a987a000 rw-s 00000000 00:08 688141     /SYSV00000000 (deleted)
a987a000-a988a000 r-xp 00000000 08:06 326032     /usr/lib/openoffice/program/libfileacc.so
a988a000-a988b000 rw-p 00010000 08:06 326032     /usr/lib/openoffice/program/libfileacc.so
a988b000-a98e8000 r-xp 00000000 08:06 326062     /usr/lib/openoffice/program/libpackage2.so
a98e8000-a98eb000 rw-p 0005d000 08:06 326062     /usr/lib/openoffice/program/libpackage2.so
a98eb000-a9907000 r-xp 00000000 08:06 292755     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
a9907000-a9908000 rw-p 0001b000 08:06 292755     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
a9908000-a990f000 r-xp 00000000 08:06 292661     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
a990f000-a9910000 rw-p 00007000 08:06 292661     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
a9910000-a9942000 r-xp 00000000 08:06 325977     /usr/lib/openoffice/program/libspl680li.so
a9942000-a9944000 rw-p 00032000 08:06 325977     /usr/lib/openoffice/program/libspl680li.so
a9944000-a9984000 rw-p a9944000 00:00 0 
a9984000-a9992000 r-xp 00000000 08:06 326037     /usr/lib/openoffice/program/libgcc3_uno.so
a9992000-a9993000 rw-p 0000e000 08:06 326037     /usr/lib/openoffice/program/libgcc3_uno.so
a9993000-a9c77000 r-xp 00000000 08:06 325952     /usr/lib/openoffice/program/libfwk680li.so
a9c77000-a9c87000 rw-p 002e3000 08:06 325952     /usr/lib/openoffice/program/libfwk680li.so
a9c87000-a9c88000 rw-p a9c87000 00:00 0 
a9c88000-a9d23000 r-xp 00000000 08:06 325992     /usr/lib/openoffice/program/libxcr680li.so
a9d23000-a9d28000 rw-p 0009a000 08:06 325992     /usr/lib/openoffice/program/libxcr680li.so
a9d28000-a9e8b000 r-xp 00000000 08:06 325967     /usr/lib/openoffice/program/libsb680li.so
a9e8b000-a9e9c000 rw-p 00163000 08:06 325967     /usr/lib/openoffice/program/libsb680li.so
a9e9c000-a9e9d000 rw-p a9e9c000 00:00 0 
a9e9d000-a9f37000 r-xp 00000000 08:06 325950     /usr/lib/openoffice/program/libfwe680li.so
a9f37000-a9f3b000 rw-p 0009a000 08:06 325950     /usr/lib/openoffice/program/libfwe680li.so
a9f3b000-aa2e5000 r-xp 00000000 08:06 325972     /usr/lib/openoffice/program/libsfx680li.so
aa2e5000-aa2fe000 rw-p 003a9000 08:06 325972     /usr/lib/openoffice/program/libsfx680li.so
aa2fe000-aa2ff000 rw-p aa2fe000 00:00 0 
aa2ff000-aa301000 r-xp 00000000 08:06 926680     /lib/libnss_mdns4.so.2
aa301000-aa302000 rw-p 00001000 08:06 926680     /lib/libnss_mdns4.so.2
aa302000-aa306000 r-xp 00000000 08:06 959938     /lib/tls/i686/cmov/libnss_dns-2.5.so
aa306000-aa308000 rw-p 00003000 08:06 959938     /lib/tls/i686/cmov/libnss_dns-2.5.so
aa308000-aa30a000 r-xp 00000000 08:06 926681     /lib/libnss_mdns4_minimal.so.2
aa30a000-aa30b000 rw-p 00001000 08:06 926681     /lib/libnss_mdns4_minimal.so.2
aa30b000-aa366000 r-xp 00000000 08:06 326094     /usr/lib/openoffice/program/libucpfile1.so
aa366000-aa369000 rw-p 0005a000 08:06 326094     /usr/lib/openoffice/program/libucpfile1.so
aa369000-aa3a3000 r-xp 00000000 08:06 325951     /usr/lib/openoffice/program/libfwi680li.so
aa3a3000-aa3a5000 rw-p 0003a000 08:06 325951     /usr/lib/openoffice/program/libfwi680li.so
aa3a5000-aa3c8000 r-xp 00000000 08:06 325953     /usr/lib/openoffice/program/libfwl680li.so
aa3c8000-aa3c9000 rw-p 00023000 08:06 325953     /usr/lib/openoffice/program/libfwl680li.so
aa3c9000-aa3ff000 r-xp 00000000 08:06 926710     /lib/libsepol.so.1
aa3ff000-aa400000 rw-p 00035000 08:06 926710     /lib/libsepol.so.1
aa400000-aa40a000 rw-p aa400000 00:00 0 
aa40a000-aa40d000 r-xp 00000000 08:06 229230     /usr/lib/libgpg-error.so.0.3.0
aa40d000-aa40e000 rw-p 00002000 08:06 229230     /usr/lib/libgpg-error.so.0.3.0
aa40e000-aa45d000 r-xp 00000000 08:06 229113     /usr/lib/libgcrypt.so.11.2.2
aa45d000-aa45f000 rw-p 0004e000 08:06 229113     /usr/lib/libgcrypt.so.11.2.2
aa45f000-aa473000 r-xp 00000000 08:06 229570     /usr/lib/libtasn1.so.3.0.6
aa473000-aa474000 rw-p 00013000 08:06 229570     /usr/lib/libtasn1.so.3.0.6
aa474000-aa476000 r-xp 00000000 08:06 959949     /lib/tls/i686/cmov/libutil-2.5.so
aa476000-aa478000 rw-p 00001000 08:06 959949     /lib/tls/i686/cmov/libutil-2.5.so
aa478000-aa48c000 r-xp 00000000 08:06 926709     /lib/libselinux.so.1
aa48c000-aa48e000 rw-p 00013000 08:06 926709     /lib/libselinux.so.1
aa48e000-aa49d000 r-xp 00000000 08:06 959945     /lib/tls/i686/cmov/libresolv-2.5.so
aa49d000-aa49f000 rw-p 0000f000 08:06 959945     /lib/tls/i686/cmov/libresolv-2.5.so
aa49f000-aa4a1000 rw-p aa49f000 00:00 0 
aa4a1000-aa4af000 r-xp 00000000 08:06 228956     /usr/lib/libavahi-client.so.3.2.2
aa4af000-aa4b0000 rw-p 0000e000 08:06 228956     /usr/lib/libavahi-client.so.3.2.2
aa4b0000-aa4ba000 r-xp 00000000 08:06 228339     /usr/lib/libavahi-common.so.3.4.3
aa4ba000-aa4bb000 rw-p 00009000 08:06 228339     /usr/lib/libavahi-common.so.3.4.3
aa4bb000-aa525000 r-xp 00000000 08:06 229226     /usr/lib/libgnutls.so.13.0.9
aa525000-aa52b000 rw-p 0006a000 08:06 229226     /usr/lib/libgnutls.so.13.0.9
aa52b000-aa581000 r-xp 00000000 08:06 228656     /usr/lib/libgnomevfs-2.so.0.1800.1
aa581000-aa584000 rw-p 00055000 08:06 228656     /usr/lib/libgnomevfs-2.so.0.1800.1
aa587000-aa589000 r-xp 00000000 08:06 229525     /usr/lib/libscim-x11utils-1.0.so.8.1.0
aa589000-aa58a000 rw-p 00001000 08:06 229525     /usr/lib/libscim-x11utils-1.0.so.8.1.0
aa58a000-aa590000 r-xp 00000000 08:06 325956     /usr/lib/openoffice/program/libj680li_g.so
aa590000-aa591000 rw-p 00006000 08:06 325956     /usr/lib/openoffice/program/libj680li_g.so
aa591000-aa5b5000 r-xp 00000000 08:06 325396     /usr/lib/openoffice/program/ucpgvfs1.uno.so
aa5b5000-aa5b7000 rw-p 00023000 08:06 325396     /usr/lib/openoffice/program/ucpgvfs1.uno.so
aa5b7000-aa5f6000 r-xp 00000000 08:06 326090     /usr/lib/openoffice/program/libucb1.so
aa5f6000-aa5f9000 rw-p 0003e000 08:06 326090     /usr/lib/openoffice/program/libucb1.so
aa5f9000-aa5fe000 r-xp 00000000 08:06 325613     /usr/lib/openoffice/program/libspl_unx680li.so
aa5fe000-aa5ff000 rw-p 00004000 08:06 325613     /usr/lib/openoffice/program/libspl_unx680li.so
aa5ff000-aa600000 ---p aa5ff000 00:00 0 
aa600000-aae00000 rwxp aa600000 00:00 0 
aae00000-aae12000 r-xp 00000000 08:06 326100     /usr/lib/openoffice/program/uriproc.uno.so
aae12000-aae14000 rw-p 00011000 08:06 326100     /usr/lib/openoffice/program/uriproc.uno.so
aae14000-aae15000 ---p aae14000 00:00 0 
aae15000-ab615000 rwxp aae15000 00:00 0 
ab615000-ab61d000 r-xp 00000000 08:06 326084     /usr/lib/openoffice/program/localebe1.uno.so
ab61d000-ab61e000 rw-p 00008000 08:06 326084     /usr/lib/openoffice/program/localebe1.uno.so
ab61e000-ab63a000 r-xp 00000000 08:06 326074     /usr/lib/openoffice/program/sax.uno.so
ab63a000-ab63b000 rw-p 0001c000 08:06 326074     /usr/lib/openoffice/program/sax.uno.so
ab63b000-ab684000 r-xp 00000000 08:06 228857     /usr/lib/libORBit-2.so.0.1.0
ab684000-ab68e000 rw-p 00048000 08:06 228857     /usr/lib/libORBit-2.so.0.1.0
ab68e000-ab6bd000 r-xp 00000000 08:06 229111     /usr/lib/libgconf-2.so.4.1.2
ab6bd000-ab6c0000 rw-p 0002e000 08:06 229111     /usr/lib/libgconf-2.so.4.1.2
ab6c1000-ab6c2000 rwxp ab6c1000 00:00 0 
ab6c2000-ab6cc000 r-xp 00000000 08:06 326011     /usr/lib/openoffice/program/behelper.uno.so
ab6cc000-ab6cd000 rw-p 00009000 08:06 326011     /usr/lib/openoffice/program/behelper.uno.so
ab6cd000-ab6dc000 r-xp 00000000 08:06 325391     /usr/lib/openoffice/program/gconfbe1.uno.so
ab6dc000-ab6dd000 rw-p 0000f000 08:06 325391     /usr/lib/openoffice/program/gconfbe1.uno.so
ab6dd000-ab6e1000 r-xp 00000000 08:06 325610     /usr/lib/openoffice/program/desktopbe1.uno.so
ab6e1000-ab6e2000 rw-p 00003000 08:06 325610     /usr/lib/openoffice/program/desktopbe1.uno.so
ab6e2000-ab6ee000 r-xp 00000000 08:06 326010     /usr/lib/openoffice/program/sysmgr1.uno.so
ab6ee000-ab6ef000 rw-p 0000c000 08:06 326010     /usr/lib/openoffice/program/sysmgr1.uno.so
ab6ef000-ab6f7000 r-xp 00000000 08:06 326085     /usr/lib/openoffice/program/typeconverter.uno.so
ab6f7000-ab6f8000 rw-p 00008000 08:06 326085     /usr/lib/openoffice/program/typeconverter.uno.so
ab6f8000-ab90c000 r-xp 00000000 08:06 326009     /usr/lib/openoffice/program/configmgr2.uno.so
ab90c000-ab920000 rw-p 00213000 08:06 326009     /usr/lib/openoffice/program/configmgr2.uno.so
ab920000-ab959000 r-xp 00000000 08:06 326068     /usr/lib/openoffice/program/regtypeprov.uno.so
ab959000-ab95d000 rw-p 00038000 08:06 326068     /usr/lib/openoffice/program/regtypeprov.uno.so
ab95d000-abb65000 r--s 00000000 08:06 325865     /usr/lib/openoffice/program/services.rdb
abb65000-abebd000 r--s 00000000 08:06 325850     /usr/lib/openoffice/program/types.rdb
abebd000-abefd000 r--s 00000000 08:06 325608     /usr/lib/openoffice/program/oovbaapi.rdb
abefd000-abf1a000 r-xp 00000000 08:06 326076     /usr/lib/openoffice/program/security.uno.so
abf1a000-abf1c000 rw-p 0001c000 08:06 326076     /usr/lib/openoffice/program/security.uno.so
abf1c000-abf30000 r-xp 00000000 08:06 326045     /usr/lib/openoffice/program/implreg.uno.so
abf30000-abf31000 rw-p 00013000 08:06 326045     /usr/lib/openoffice/program/implreg.uno.so
abf31000-abf59000 r-xp 00000000 08:06 326086     /usr/lib/openoffice/program/typemgr.uno.so
abf59000-abf5b000 rw-p 00028000 08:06 326086     /usr/lib/openoffice/program/typemgr.uno.so
abf5b000-abf6a000 r-xp 00000000 08:06 326020     /usr/lib/openoffice/program/nestedreg.uno.so
abf6a000-abf6b000 rw-p 0000f000 08:06 326020     /usr/lib/openoffice/program/nestedreg.uno.so
abf6b000-abf7c000 r-xp 00000000 08:06 326077     /usr/lib/openoffice/program/simplereg.uno.so
abf7c000-abf7d000 rw-p 00010000 08:06 326077     /usr/lib/openoffice/program/simplereg.uno.so
abf7d000-abf83000 r-xp 00000000 08:06 326017     /usr/lib/openoffice/program/shlibloader.uno.so
abf83000-abf84000 rw-p 00005000 08:06 326017     /usr/lib/openoffice/program/shlibloader.uno.so
abf84000-abfa4000 r-xp 00000000 08:06 326078     /usr/lib/openoffice/program/servicemgr.uno.so
abfa4000-abfa6000 rw-p 0001f000 08:06 326078     /usr/lib/openoffice/program/servicemgr.uno.so
abfa6000-abfc2000 r-xp 00000000 08:06 326081     /usr/lib/openoffice/program/libstore.so.3
abfc2000-abfc3000 rw-p 0001b000 08:06 326081     /usr/lib/openoffice/program/libstore.so.3
abfc3000-abfe5000 r-xp 00000000 08:06 326070     /usr/lib/openoffice/program/libreg.so.3
abfe5000-abfe6000 rw-p 00021000 08:06 326070     /usr/lib/openoffice/program/libreg.so.3
abfe6000-abff7000 r-xp 00000000 08:06 325609     /usr/lib/openoffice/program/libexlink680li.so
abff7000-abff8000 rw-p 00011000 08:06 325609     /usr/lib/openoffice/program/libexlink680li.so
abff8000-ac138000 rw-s 00011000 00:0d 17118      /dev/dri/card0
ac138000-ac778000 rw-s 00007000 00:0d 17118      /dev/dri/card0
ac778000-ac878000 rw-s 00006000 00:0d 17118      /dev/dri/card0
ac878000-ac888000 rw-s 00004000 00:0d 17118      /dev/dri/card0
ac888000-b4888000 rw-s 00003000 00:0d 17118      /dev/dri/card0
b4888000-b4938000 r-xp 00000000 08:06 229562     /usr/lib/libstdc++.so.5.0.7
b4938000-b493d000 rw-p 000af000 08:06 229562     /usr/lib/libstdc++.so.5.0.7
b493d000-b4942000 rw-p b493d000 00:00 0 
b4942000-b519f000 r-xp 00000000 08:06 244901     /usr/lib/dri/fglrx_dri.so
b519f000-b51e9000 rw-p 0085d000 08:06 244901     /usr/lib/dri/fglrx_dri.so
b51e9000-b5273000 rw-p b51e9000 00:00 0 
b5273000-b530b000 r-xp 00000000 08:06 228026     /usr/lib/libGL.so.1.2
b530b000-b5310000 rw-p 00098000 08:06 228026     /usr/lib/libGL.so.1.2
b5310000-b5313000 rw-p b5310000 00:00 0 
b5313000-b531c000 r-xp 00000000 08:06 959939     /lib/tls/i686/cmov/libnss_files-2.5.so
b531c000-b531e000 rw-p 00008000 08:06 959939     /lib/tls/i686/cmov/libnss_files-2.5.so
b531e000-b5326000 r-xp 00000000 08:06 959941     /lib/tls/i686/cmov/libnss_nis-2.5.so
b5326000-b5328000 rw-p 00007000 08:06 959941     /lib/tls/i686/cmov/libnss_nis-2.5.so
b5328000-b532f000 r-xp 00000000 08:06 959937     /lib/tls/i686/cmov/libnss_compat-2.5.so
b532f000-b5331000 rw-p 00006000 08:06 959937     /lib/tls/i686/cmov/libnss_compat-2.5.so
b5331000-b5333000 r-xp 00000000 08:06 228954     /usr/lib/libavahi-glib.so.1.0.1
b5333000-b5334000 rw-p 00001000 08:06 228954     /usr/lib/libavahi-glib.so.1.0.1
b5334000-b5335000 rw-p b5334000 00:00 0 
b5335000-b5337000 rw-s 00002000 00:0d 17118      /dev/dri/card0
b5337000-b533e000 rwxp b5337000 00:00 0 
b533e000-b5415000 r--p 00000000 08:06 293652     /usr/lib/locale/en_IE.utf8/LC_COLLATE
b5415000-b5462000 r-xp 00000000 08:06 228916     /usr/lib/libXt.so.6.0.0
b5462000-b5466000 rw-p 0004c000 08:06 228916     /usr/lib/libXt.so.6.0.0
b5466000-b54a8000 r-xp 00000000 08:06 228834     /usr/lib/libFLAC.so.7.0.0
b54a8000-b54a9000 rw-p 00041000 08:06 228834     /usr/lib/libFLAC.so.7.0.0
b54a9000-b54b1000 r-xp 00000000 08:06 229362     /usr/lib/libstartup-notification-1.so.0.0.0
b54b1000-b54b2000 rw-p 00007000 08:06 229362     /usr/lib/libstartup-notification-1.so.0.0.0
b54b2000-b54c7000 r-xp 00000000 08:06 228345     /usr/lib/libaudio.so.2.4
b54c7000-b54c8000 rw-p 00015000 08:06 228345     /usr/lib/libaudio.so.2.4
b54c8000-b54ce000 r-xp 00000000 08:06 229488     /usr/lib/libportaudio.so.0.0.18
b54ce000-b54cf000 rw-p 00005000 08:06 229488     /usr/lib/libportaudio.so.0.0.18
b54cf000-b5526000 r-xp 00000000 08:06 229544     /usr/lib/libsndfile.so.1.0.16
b5526000-b5528000 rw-p 00056000 08:06 229544     /usr/lib/libsndfile.so.1.0.16
b5528000-b552c000 rw-p b5528000 00:00 0 
b552c000-b553f000 r-xp 00000000 08:06 959936     /lib/tls/i686/cmov/libnsl-2.5.so
b553f000-b5541000 rw-p 00012000 08:06 959936     /lib/tls/i686/cmov/libnsl-2.5.so
b5541000-b5543000 rw-p b5541000 00:00 0 
b5543000-b55c2000 r-xp 00000000 08:06 325965     /usr/lib/openoffice/program/libvclplug_gen680li.so
b55c2000-b55ca000 rw-p 0007f000 08:06 325965     /usr/lib/openoffice/program/libvclplug_gen680li.so
b55ca000-b55cb000 rw-p b55ca000 00:00 0 
b55cb000-b55fc000 r-xp 00000000 08:06 229010     /usr/lib/libdbus-1.so.3.2.0
b55fc000-b55fd000 rw-p 00031000 08:06 229010     /usr/lib/libdbus-1.so.3.2.0
b55fd000-b5617000 r-xp 00000000 08:06 229012     /usr/lib/libdbus-glib-1.so.2.1.0
b5617000-b5618000 rw-p 0001a000 08:06 229012     /usr/lib/libdbus-glib-1.so.2.1.0
b5618000-b561f000 r-xp 00000000 08:06 959946     /lib/tls/i686/cmov/librt-2.5.so
b561f000-b5621000 rw-p 00006000 08:06 959946     /lib/tls/i686/cmov/librt-2.5.so
b5621000-b563a000 r-xp 00000000 08:06 228949     /usr/lib/libatk-1.0.so.0.1809.1
b563a000-b563c000 rw-p 00018000 08:06 228949     /usr/lib/libatk-1.0.so.0.1809.1
b563c000-b598d000 r-xp 00000000 08:06 228110     /usr/lib/libgtk-x11-2.0.so.0.1000.11
b598d000-b5993000 rw-p 00351000 08:06 228110     /usr/lib/libgtk-x11-2.0.so.0.1000.11
b5993000-b5994000 rw-p b5993000 00:00 0 
b5994000-b5995000 rw-s 00005000 00:0d 17118      /dev/dri/card0
b5995000-b5996000 r-xp 00000000 08:06 244268     /usr/lib/gconv/ISO8859-1.so
b5996000-b5998000 rw-p 00000000 08:06 244268     /usr/lib/gconv/ISO8859-1.so
b5998000-b5999000 r--p 00000000 08:06 293658     /usr/lib/locale/en_IE.utf8/LC_NUMERIC
b5999000-b599a000 r--p 00000000 08:06 293548     /usr/lib/locale/en_IE.utf8/LC_TIME
b599a000-b599b000 r--p 00000000 08:06 293549     /usr/lib/locale/en_IE.utf8/LC_MONETARY
b599b000-b599c000 r--p 00000000 08:06 308890     /usr/lib/locale/en_IE.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b599c000-b599d000 r--p 00000000 08:06 293659     /usr/lib/locale/en_IE.utf8/LC_PAPER
b599d000-b599e000 r--p 00000000 08:06 293558     /usr/lib/locale/en_IE.utf8/LC_NAME
b599e000-b599f000 r--p 00000000 08:06 293550     /usr/lib/locale/en_IE.utf8/LC_ADDRESS
b599f000-b59a0000 r--p 00000000 08:06 293551     /usr/lib/locale/en_IE.utf8/LC_TELEPHONE
b59a0000-b59a1000 r--p 00000000 08:06 293655     /usr/lib/locale/en_IE.utf8/LC_MEASUREMENT
b59a1000-b59ec000 r-xp 00000000 08:06 325395     /usr/lib/openoffice/program/libvclplug_gtk680li.so
b59ec000-b59f2000 rw-p 0004a000 08:06 325395     /usr/lib/openoffice/program/libvclplug_gtk680li.so
b59f2000-b5a2d000 r--p 00000000 08:06 293653     /usr/lib/locale/en_IE.utf8/LC_CTYPE
b5a2d000-b5a31000 rw-p b5a2d000 00:00 0 
b5a31000-b5a53000 r-xp 00000000 08:06 229482     /usr/lib/libpng12.so.0.15.0
b5a53000-b5a54000 rw-p 00021000 08:06 229482     /usr/lib/libpng12.so.0.15.0
b5a54000-b5a7e000 r-xp 00000000 08:06 229496     /usr/lib/libpangoft2-1.0.so.0.1600.2
b5a7e000-b5a7f000 rw-p 0002a000 08:06 229496     /usr/lib/libpangoft2-1.0.so.0.1600.2
b5a7f000-b5a80000 rw-p b5a7f000 00:00 0 
b5a80000-b5b97000 r-xp 00000000 08:06 229620     /usr/lib/libxml2.so.2.6.27
b5b97000-b5b9d000 rw-p 00116000 08:06 229620     /usr/lib/libxml2.so.2.6.27
b5b9d000-b5bbb000 r-xp 00000000 08:06 229068     /usr/lib/libexpat.so.1.0.0
b5bbb000-b5bbd000 rw-p 0001d000 08:06 229068     /usr/lib/libexpat.so.1.0.0
b5bbd000-b5c51000 r-xp 00000000 08:06 229178     /usr/lib/libglib-2.0.so.0.1200.11
b5c51000-b5c52000 rw-p 00093000 08:06 229178     /usr/lib/libglib-2.0.so.0.1200.11
b5c52000-b5c54000 r-xp 00000000 08:06 229184     /usr/lib/libgmodule-2.0.so.0.1200.11
b5c54000-b5c55000 rw-p 00002000 08:06 229184     /usr/lib/libgmodule-2.0.so.0.1200.11
b5c55000-b5c56000 rw-p b5c55000 00:00 0 
b5c56000-b5c8f000 r-xp 00000000 08:06 229228     /usr/lib/libgobject-2.0.so.0.1200.11
b5c8f000-b5c90000 rw-p 00039000 08:06 229228     /usr/lib/libgobject-2.0.so.0.1200.11
b5c90000-b5cfe000 r-xp 00000000 08:06 228868     /usr/lib/libcairo.so.2.11.1
b5cfe000-b5d00000 rw-p 0006d000 08:06 228868     /usr/lib/libcairo.so.2.11.1
b5d00000-b5d3c000 r-xp 00000000 08:06 229435     /usr/lib/libpango-1.0.so.0.1600.2
b5d3c000-b5d3e000 rw-p 0003b000 08:06 229435     /usr/lib/libpango-1.0.so.0.1600.2
b5d3e000-b5d42000 r-xp 00000000 08:06 228892     /usr/lib/libXfixes.so.3.1.0
b5d42000-b5d43000 rw-p 00003000 08:06 228892     /usr/lib/libXfixes.so.3.1.0
b5d43000-b5d4b000 r-xp 00000000 08:06 228882     /usr/lib/libXcursor.so.1.0.2
b5d4b000-b5d4c000 rw-p 00007000 08:06 228882     /usr/lib/libXcursor.so.1.0.2
b5d4c000-b5d51000 r-xp 00000000 08:06 228910     /usr/lib/libXrandr.so.2.1.0
b5d51000-b5d52000 rw-p 00005000 08:06 228910     /usr/lib/libXrandr.so.2.1.0
b5d52000-b5d53000 rw-p b5d52000 00:00 0 
b5d53000-b5d5a000 r-xp 00000000 08:06 228898     /usr/lib/libXi.so.6.0.0
b5d5a000-b5d5b000 rw-p 00006000 08:06 228898     /usr/lib/libXi.so.6.0.0
b5d5b000-b5d5d000 r-xp 00000000 08:06 228900     /usr/lib/libXinerama.so.1.0.0
b5d5d000-b5d5e000 rw-p 00001000 08:06 228900     /usr/lib/libXinerama.so.1.0.0
b5d5e000-b5d65000 r-xp 00000000 08:06 228912     /usr/lib/libXrender.so.1.3.0
b5d65000-b5d66000 rw-p 00006000 08:06 228912     /usr/lib/libXrender.so.1.3.0
b5d66000-b5d6d000 r-xp 00000000 08:06 229436     /usr/lib/libpangocairo-1.0.so.0.1600.2
b5d6d000-b5d6e000 rw-p 00007000 08:06 229436     /usr/lib/libpangocairo-1.0.so.0.1600.2
b5d6e000-b5d84000 r-xp 00000000 08:06 227941     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b5d84000-b5d85000 rw-p 00015000 08:06 227941     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b5d85000-b5e08000 r-xp 00000000 08:06 228109     /usr/lib/libgdk-x11-2.0.so.0.1000.11
b5e08000-b5e0b000 rw-p 00083000 08:06 228109     /usr/lib/libgdk-x11-2.0.so.0.1000.11
b5e0b000-b5e0c000 rw-p b5e0b000 00:00 0 
b5e0c000-b5e0e000 r-xp 00000000 08:06 229469     /usr/lib/libpaper.so.1.1.2
b5e0e000-b5e0f000 rw-p 00001000 08:06 229469     /usr/lib/libpaper.so.1.1.2
b5e0f000-b67be000 r--p 00000000 08:06 229324     /usr/lib/libicudata.so.36.0
b67be000-b67bf000 rw-p 009ae000 08:06 229324     /usr/lib/libicudata.so.36.0
b67bf000-b67c3000 r-xp 00000000 08:06 228886     /usr/lib/libXdmcp.so.6.0.0
b67c3000-b67c4000 rw-p 00003000 08:06 228886     /usr/lib/libXdmcp.so.6.0.0
b67c4000-b67c6000 r-xp 00000000 08:06 228875     /usr/lib/libXau.so.6.0.0
b67c6000-b67c7000 rw-p 00001000 08:06 228875     /usr/lib/libXau.so.6.0.0
b67c7000-b67c8000 rw-p b67c7000 00:00 0 
b67c8000-b67cd000 r-xp 00000000 08:06 959932     /lib/tls/i686/cmov/libcrypt-2.5.so
b67cd000-b67cf000 rw-p 00004000 08:06 959932     /lib/tls/i686/cmov/libcrypt-2.5.so
b67cf000-b67f6000 rw-p b67cf000 00:00 0 
b67f6000-b67fd000 r-xp 00000000 08:06 926690     /lib/libpam.so.0.79
b67fd000-b67fe000 rw-p 00007000 08:06 926690     /lib/libpam.so.0.79
b67fe000-b6802000 r-xp 00000000 08:06 326073     /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b6802000-b6803000 rw-p 00003000 08:06 326073     /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b6803000-b681a000 r-xp 00000000 08:06 326106     /usr/lib/openoffice/program/libjvmfwk.so.3
b681a000-b681b000 rw-p 00017000 08:06 326106     /usr/lib/openoffice/program/libjvmfwk.so.3
b681b000-b681c000 rw-p b681b000 00:00 0 
b681c000-b683a000 r-xp 00000000 08:06 229353     /usr/lib/libjpeg.so.62.0.0
b683a000-b683b000 rw-p 0001d000 08:06 229353     /usr/lib/libjpeg.so.62.0.0
b683b000-b685e000 r-xp 00000000 08:06 229074     /usr/lib/libfontconfig.so.1.2.0
b685e000-b6866000 rw-p 00023000 08:06 229074     /usr/lib/libfontconfig.so.1.2.0
b6866000-b6879000 r-xp 00000000 08:06 229632     /usr/lib/libz.so.1.2.3
b6879000-b687a000 rw-p 00012000 08:06 229632     /usr/lib/libz.so.1.2.3
b687a000-b68e2000 r-xp 00000000 08:06 227777     /usr/lib/libfreetype.so.6.3.10
b68e2000-b68e5000 rw-p 00068000 08:06 227777     /usr/lib/libfreetype.so.6.3.10
b68e5000-b68e9000 r-xp 00000000 08:06 326055     /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b68e9000-b68ea000 rw-p 00003000 08:06 326055     /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b68ea000-b68eb000 rw-p b68ea000 00:00 0 
b68eb000-b6990000 r-xp 00000000 08:06 325964     /usr/lib/openoffice/program/libpsp680li.so
b6990000-b69d9000 rw-p 000a5000 08:06 325964     /usr/lib/openoffice/program/libpsp680li.so
b69d9000-b69db000 rw-p b69d9000 00:00 0 
b69db000-b6a1a000 r-xp 00000000 08:06 229330     /usr/lib/libicule.so.36.0
b6a1a000-b6a1c000 rw-p 0003f000 08:06 229330     /usr/lib/libicule.so.36.0
b6a1c000-b6b32000 r-xp 00000000 08:06 229336     /usr/lib/libicuuc.so.36.0
b6b32000-b6b39000 rw-p 00116000 08:06 229336     /usr/lib/libicuuc.so.36.0
b6b39000-b6b3b000 rw-p b6b39000 00:00 0 
b6b3b000-b6bb1000 r-xp 00000000 08:06 325990     /usr/lib/openoffice/program/libbasegfx680li.so
b6bb1000-b6bb2000 rw-p 00076000 08:06 325990     /usr/lib/openoffice/program/libbasegfx680li.so
b6bb2000-b6c0b000 r-xp 00000000 08:06 325974     /usr/lib/openoffice/program/libsot680li.so
b6c0b000-b6c0e000 rw-p 00059000 08:06 325974     /usr/lib/openoffice/program/libsot680li.so
b6c0e000-b6c0f000 rw-p b6c0e000 00:00 0 
b6c0f000-b6d4a000 r-xp 00000000 08:06 959930     /lib/tls/i686/cmov/libc-2.5.so
b6d4a000-b6d4b000 r--p 0013b000 08:06 959930     /lib/tls/i686/cmov/libc-2.5.so
b6d4b000-b6d4d000 rw-p 0013c000 08:06 959930     /lib/tls/i686/cmov/libc-2.5.so
b6d4d000-b6d50000 rw-p b6d4d000 00:00 0 
b6d50000-b6d5b000 r-xp 00000000 08:06 926656     /lib/libgcc_s.so.1
b6d5b000-b6d5c000 rw-p 0000a000 08:06 926656     /lib/libgcc_s.so.1
b6d5c000-b6d81000 r-xp 00000000 08:06 959934     /lib/tls/i686/cmov/libm-2.5.so
b6d81000-b6d83000 rw-p 00024000 08:06 959934     /lib/tls/i686/cmov/libm-2.5.so
b6d83000-b6e62000 r-xp 00000000 08:06 229564     /usr/lib/libstdc++.so.6.0.8
b6e62000-b6e65000 r--p 000de000 08:06 229564     /usr/lib/libstdc++.so.6.0.8
b6e65000-b6e67000 rw-p 000e1000 08:06 229564     /usr/lib/libstdc++.so.6.0.8
b6e67000-b6e6d000 rw-p b6e67000 00:00 0 
b6e6d000-b6eff000 r-xp 00000000 08:06 229566     /usr/lib/libstlport.so.5.1.0
b6eff000-b6f03000 rw-p 00091000 08:06 229566     /usr/lib/libstlport.so.5.1.0
b6f03000-b6f07000 rw-p b6f03000 00:00 0 
b6f07000-b6f1a000 r-xp 00000000 08:06 959944     /lib/tls/i686/cmov/libpthread-2.5.so
b6f1a000-b6f1c000 rw-p 00013000 08:06 959944     /lib/tls/i686/cmov/libpthread-2.5.so
b6f1c000-b6f1f000 rw-p b6f1c000 00:00 0 
b6f1f000-b6f21000 r-xp 00000000 08:06 959933     /lib/tls/i686/cmov/libdl-2.5.so
b6f21000-b6f23000 rw-p 00001000 08:06 959933     /lib/tls/i686/cmov/libdl-2.5.so
b6f23000-b7010000 r-xp 00000000 08:06 227895     /usr/lib/libX11.so.6.2.0
b7010000-b7014000 rw-p 000ed000 08:06 227895     /usr/lib/libX11.so.6.2.0
b7014000-b7029000 r-xp 00000000 08:06 228847     /usr/lib/libICE.so.6.3.0
b7029000-b702b000 rw-p 00014000 08:06 228847     /usr/lib/libICE.so.6.3.0
b702b000-b702c000 rw-p b702b000 00:00 0 
b702c000-b7034000 r-xp 00000000 08:06 228865     /usr/lib/libSM.so.6.0.0
b7034000-b7035000 rw-p 00007000 08:06 228865     /usr/lib/libSM.so.6.0.0
b7035000-b7042000 r-xp 00000000 08:06 228890     /usr/lib/libXext.so.6.4.0
b7042000-b7043000 rw-p 0000d000 08:06 228890     /usr/lib/libXext.so.6.4.0
b7043000-b7044000 r--p 00000000 08:06 293552     /usr/lib/locale/en_IE.utf8/LC_IDENTIFICATION
b7044000-b7048000 r-xp 00000000 08:06 229282     /usr/lib/libgthread-2.0.so.0.1200.11
b7048000-b7049000 rw-p 00003000 08:06 229282     /usr/lib/libgthread-2.0.so.0.1200.11
b7049000-b7050000 r--s 00000000 08:06 244327     /usr/lib/gconv/gconv-modules.cache
b7050000-b7281000 r-xp 00000000 08:06 325984     /usr/lib/openoffice/program/libtk680li.so
b7281000-b72a9000 rw-p 00231000 08:06 325984     /usr/lib/openoffice/program/libtk680li.so
b72a9000-b72ac000 rw-p b72a9000 00:00 0 
b72ac000-b72f9000 r-xp 00000000 08:06 326072     /usr/lib/openoffice/program/libuno_sal.so.3
b72f9000-b72fc000 rw-p 0004c000 08:06 326072     /usr/lib/openoffice/program/libuno_sal.so.3
b72fc000-b72fe000 rw-p b72fc000 00:00 0 
b72fe000-b732c000 r-xp 00000000 08:06 326018     /usr/lib/openoffice/program/libuno_cppu.so.3
b732c000-b732d000 rw-p 0002d000 08:06 326018     /usr/lib/openoffice/program/libuno_cppu.so.3
b732d000-b7399000 r-xp 00000000 08:06 326019     /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b7399000-b739c000 rw-p 0006c000 08:06 326019     /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b739c000-b73be000 r-xp 00000000 08:06 326103     /usr/lib/openoffice/program/libvos3gcc3.so
b73be000-b73c0000 rw-p 00022000 08:06 326103     /usr/lib/openoffice/program/libvos3gcc3.so
b73c0000-b743b000 r-xp 00000000 08:06 326091     /usr/lib/openoffice/program/libucbhelper3gcc3.so
b743b000-b743f000 rw-p 0007b000 08:06 326091     /usr/lib/openoffice/program/libucbhelper3gcc3.so
b743f000-b7440000 rw-p b743f000 00:00 0 
b7440000-b753c000 r-xp 00000000 08:06 326014     /usr/lib/openoffice/program/libcomphelp4gcc3.so
b753c000-b7544000 rw-p 000fc000 08:06 326014     /usr/lib/openoffice/program/libcomphelp4gcc3.so
b7544000-b7545000 rw-p b7544000 00:00 0 
b7545000-b7549000 r-xp 00000000 08:06 326042     /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b7549000-b754a000 rw-p 00004000 08:06 326042     /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b754a000-b75e9000 r-xp 00000000 08:06 325985     /usr/lib/openoffice/program/libtl680li.so
b75e9000-b75ec000 rw-p 0009e000 08:06 325985     /usr/lib/openoffice/program/libtl680li.so
b75ec000-b7679000 r-xp 00000000 08:06 325988     /usr/lib/openoffice/program/libutl680li.so
b7679000-b767e000 rw-p 0008c000 08:06 325988     /usr/lib/openoffice/program/libutl680li.so
b767e000-b7a60000 r-xp 00000000 08:06 325980     /usr/lib/openoffice/program/libsvt680li.so
b7a60000-b7a85000 rw-p 003e1000 08:06 325980     /usr/lib/openoffice/program/libsvt680li.so
b7a85000-b7a87000 rw-p b7a85000 00:00 0 
b7a87000-b7b9b000 r-xp 00000000 08:06 325979     /usr/lib/openoffice/program/libsvl680li.so
b7b9b000-b7ba1000 rw-p 00114000 08:06 325979     /usr/lib/openoffice/program/libsvl680li.so
b7ba1000-b7f0f000 r-xp 00000000 08:06 325991     /usr/lib/openoffice/program/libvcl680li.so
b7f0f000-b7f23000 rw-p 0036e000 08:06 325991     /usr/lib/openoffice/program/libvcl680li.so
b7f23000-b7f26000 rw-p b7f23000 00:00 0 
b7f26000-b7f3f000 r-xp 00000000 08:06 926596     /lib/ld-2.5.so
b7f3f000-b7f41000 rw-p 00019000 08:06 926596     /lib/ld-2.5.so
bf96d000-bf9b1000 rwxp bf96d000 00:00 0          [stack]
bf9b1000-bf9b4000 rw-p bf9b1000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

** (process:5986): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

Does anyone know where this problem comes from, I already reinstalled openoffice, but that doesn;t help.
It works on all OO aps, not just writer

Casper

---

### Post by Hagar Delest on 2007-04-18
I've found this thread, searching a little : [ openoffice 2.2 start up error on Feisty]("http://ubuntuforums.org/showthread.php?p=2424921").

---

### Post by aldeby on 2007-05-28
If you installed SCIM imput for non latin languages this fix done the job for me: 
> [http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)
Hope it helps. It has been a very annoying bug.

---

