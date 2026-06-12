---
title: "Bit of a problem here"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by waste301 on 2008-04-07
I tried, on the advice of a friend, to check out Firefox 3.4.  I promptly had all kinds of graphical problems and tried to go back to FF2.  Not so easy.

I've perused the threads here, uninstalled with the synaptic manager, re -installed, unistalled, re-installed.
Followed suggestions from ggogling the problem.

Nothing works.  I now have an icon in Applications--->internet that when I click thinks for a few seconds, then does nothing.

When I type "firefox" in a terminal, I get this:

*** glibc detected *** /opt/firefox/firefox-bin: free(): invalid pointer: 0xb7f1a84c ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73b0d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb73b4800]
/opt/firefox/libnspr4.so(PR_Free+0x2b)[0xb7e55dad]
/opt/firefox/libxpcom_core.so(NS_Free_P+0x18)[0xb7efb6ec]
/opt/firefox/libxpcom_core.so(_ZN12nsCSubstring11ReplacePrepEjjj+0xca)[0xb7f0b9ca]
/opt/firefox/libxpcom_core.so(_ZN12nsCSubstring6AssignEPKcj+0x58)[0xb7f0bb28]
/opt/firefox/libxpcom_core.so(_ZN12nsCSubstring6AssignERKS_+0x8b)[0xb7f0bd0f]
/opt/firefox/libxpcom_core.so(_ZN12nsCSubstring6AssignERK19nsACString_internal+0x4c)[0xb7f0be0c]
/opt/firefox/libxpcom_core.so(_ZN19nsACString_internal6AssignERKS_+0x38)[0xb7f10bc4]
/opt/firefox/libxpcom_core.so(NS_CStringCopy_P+0x1b)[0xb7ebaebf]
/opt/firefox/libxpcom.so(NS_CStringCopy+0x1b)[0xb7f24b6d]
/opt/firefox/components/libimgicon.so[0xb6a223c7]
/opt/firefox/components/libimgicon.so[0xb6a21f45]
/opt/firefox/components/libimgicon.so[0xb6a22bbb]
/opt/firefox/firefox-bin[0x812d566]
/opt/firefox/firefox-bin[0x82fe116]
/opt/firefox/firefox-bin[0x82fd6a0]
/opt/firefox/firefox-bin[0x82fec4d]
/opt/firefox/firefox-bin[0x82fe6d4]
/opt/firefox/firefox-bin[0x82fca6b]
/opt/firefox/firefox-bin[0x82fbd85]
/opt/firefox/firefox-bin[0x82fa68f]
/opt/firefox/firefox-bin[0x82f881a]
/opt/firefox/firefox-bin[0x82f705a]
/opt/firefox/firefox-bin[0x82f6f37]
/opt/firefox/firefox-bin[0x82f7a74]
/opt/firefox/firefox-bin[0x82f798f]
/opt/firefox/firefox-bin[0x8419a26]
/opt/firefox/firefox-bin[0x8417122]
/opt/firefox/firefox-bin[0x8422121]
/opt/firefox/firefox-bin[0x84218c4]
/opt/firefox/firefox-bin[0x825dc5c]
/opt/firefox/firefox-bin[0x825db53]
/opt/firefox/firefox-bin[0x82638d7]
/opt/firefox/firefox-bin[0x825b572]
/opt/firefox/firefox-bin[0x825e05e]
/opt/firefox/firefox-bin[0x825db53]
/opt/firefox/firefox-bin[0x82638d7]
/opt/firefox/firefox-bin[0x825b572]
/opt/firefox/firefox-bin[0x825e05e]
/opt/firefox/firefox-bin[0x825db53]
/opt/firefox/firefox-bin[0x82638d7]
/opt/firefox/firefox-bin[0x825b572]
/opt/firefox/firefox-bin[0x825e05e]
/opt/firefox/firefox-bin[0x825db53]
/opt/firefox/firefox-bin[0x82638d7]
/opt/firefox/firefox-bin[0x8258b79]
/opt/firefox/firefox-bin[0x82607f6]
/opt/firefox/firefox-bin[0x8280a2e]
/opt/firefox/firefox-bin[0x8433234]
/opt/firefox/firefox-bin[0x8434efd]
/opt/firefox/firefox-bin[0x8435788]
/opt/firefox/firefox-bin[0x813c6c8]
/opt/firefox/components/libjar50.so[0xb6a150b8]
/opt/firefox/firefox-bin[0x812b9fd]
/opt/firefox/firefox-bin[0x812b771]
/opt/firefox/libxpcom_core.so(_ZN23nsInputStreamReadyEvent12EventHandlerEP7PLEvent+0x30)[0xb7ed9a60]
/opt/firefox/libxpcom_core.so(PL_HandleEvent+0x1d)[0xb7ef11c7]
/opt/firefox/libxpcom_core.so(PL_ProcessPendingEvents+0x70)[0xb7ef111a]
/opt/firefox/libxpcom_core.so[0xb7ef27bc]
/opt/firefox/firefox-bin[0x824d490]
/usr/lib/libglib-2.0.so.0[0xb78ea6ed]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb78bb11c]
======= Memory map: ========
08048000-08a30000 r-xp 00000000 08:03 4376649    /opt/firefox/firefox-bin
08a30000-08a49000 rw-p 009e7000 08:03 4376649    /opt/firefox/firefox-bin
08a49000-0901a000 rw-p 08a49000 00:00 0          [heap]
b4800000-b4821000 rw-p b4800000 00:00 0 
b4821000-b4900000 ---p b4821000 00:00 0 
b4939000-b493a000 ---p b4939000 00:00 0 
b493a000-b513a000 rw-p b493a000 00:00 0 
b513a000-b513b000 ---p b513a000 00:00 0 
b513b000-b593b000 rw-p b513b000 00:00 0 
b593b000-b593c000 ---p b593b000 00:00 0 
b593c000-b613c000 rw-p b593c000 00:00 0 
b613c000-b619c000 rw-s 00000000 00:09 917520     /SYSV00000000 (deleted)
b619c000-b61a8000 r-xp 00000000 08:03 3556838    /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
b61a8000-b61a9000 rw-p 0000b000 08:03 3556838    /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
b61a9000-b61aa000 ---p b61a9000 00:00 0 
b61aa000-b69aa000 rw-p b61aa000 00:00 0 
b69aa000-b69b8000 r-xp 00000000 08:03 4376850    /opt/firefox/components/libspellchecker.so
b69b8000-b69b9000 rw-p 0000e000 08:03 4376850    /opt/firefox/components/libspellchecker.so
b69b9000-b69c3000 r-xp 00000000 08:03 4376849    /opt/firefox/components/libmyspell.so
b69c3000-b69c4000 rw-p 00009000 08:03 4376849    /opt/firefox/components/libmyspell.so
b69c4000-b69d3000 r-xp 00000000 08:03 4376842    /opt/firefox/components/libjsd.so
b69d3000-b69d4000 rw-p 0000f000 08:03 4376842    /opt/firefox/components/libjsd.so
b69d4000-b6a07000 r-xp 00000000 08:03 4376840    /opt/firefox/components/libxpinstall.so
b6a07000-b6a0a000 rw-p 00032000 08:03 4376840    /opt/firefox/components/libxpinstall.so
b6a0a000-b6a1e000 r-xp 00000000 08:03 4376841    /opt/firefox/components/libjar50.so
b6a1e000-b6a1f000 rw-p 00014000 08:03 4376841    /opt/firefox/components/libjar50.so
b6a1f000-b6a29000 r-xp 00000000 08:03 4376780    /opt/firefox/components/libimgicon.so
b6a29000-b6a2a000 rw-p 00009000 08:03 4376780    /opt/firefox/components/libimgicon.so
b6a2a000-b6a2e000 r-xp 00000000 08:03 4376816    /opt/firefox/components/libnkgnomevfs.so
b6a2e000-b6a2f000 rw-p 00004000 08:03 4376816    /opt/firefox/components/libnkgnomevfs.so
b6a2f000-b6b17000 r-xp 00000000 08:03 3457891    /usr/lib/libstdc++.so.6.0.9
b6b17000-b6b1a000 r--p 000e8000 08:03 3457891    /usr/lib/libstdc++.so.6.0.9
b6b1a000-b6b1c000 rw-p 000eb000 08:03 3457891    /usr/lib/libstdc++.so.6.0.9
b6b1c000-b6b22000 rw-p b6b1c000 00:00 0 
b6b24000-b6b2a000 r-xp 00000000 08:03 3525999    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b6b2a000-b6b2b000 rw-p 00005000 08:03 3525999    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b6b2b000-b6b31000 r-xp 00000000 08:03 4376787    /opt/firefox/components/libdbusservice.so
b6b31000-b6b32000 rw-p 00005000 08:03 4376787    /opt/firefox/components/libdbusservice.so
b6b32000-b6bf3000 r-xp 00000000 08:03 3461076    /usr/lib/libasound.so.2.0.0
b6bf3000-b6bf8000 rw-p 000c0000 08:03 3461076    /usr/lib/libasound.so.2.0.0
b6bf8000-b6c2e000 r-xp 00000000 08:03 2031764    /lib/libsepol.so.1
b6c2e000-b6c2f000 rw-p 00035000 08:03 2031764    /lib/libsepol.so.1
b6c2f000-b6c39000 rw-p b6c2f000 00:00 0 
b6c39000-b6c88000 r-xp 00000000 08:03 3458333    /usr/lib/libgcrypt.so.11.2.3
b6c88000-b6c8a000 rw-p 0004e000 08:03 3458333    /usr/lib/libgcrypt.so.11.2.3
b6c8a000-b6c8d000 r-xp 00000000 08:03 3457055    /usr/lib/libgpg-error.so.0.3.0
b6c8d000-b6c8e000 rw-p 00002000 08:03 3457055    /usr/lib/libgpg-error.so.0.3.0
b6c8e000-b6c9d000 r-xp 00000000 08:03 3458356    /usr/lib/libtasn1.so.3.0.9
b6c9d000-b6c9e000 rw-p 0000e000 08:03 3458356    /usr/lib/libtasn1.so.3.0.9
b6c9e000-b6ca5000 r-xp 00000000 08:03 2031850    /lib/libpopt.so.0.0.0
b6ca5000-b6ca6000 rw-p 00006000 08:03 2031850    /lib/libpopt.so.0.0.0
b6ca6000-b6cc6000 r-xp 00000000 08:03 3461622    /usr/lib/libaudiofile.so.0.0.2
b6cc6000-b6cc8000 rw-p 00020000 08:03 3461622    /usr/lib/libaudiofile.so.0.0.2
b6cc8000-b6cd1000 r-xp 00000000 08:03 3461677    /usr/lib/libesd.so.0.2.38
b6cd1000-b6cd2000 rw-p 00009000 08:03 3461677    /usr/lib/libesd.so.0.2.38
b6cd2000-b6cd6000 r-xp 00000000 08:03 3460216    /usr/lib/libORBitCosNaming-2.so.0.1.0
b6cd6000-b6cd7000 rw-p 00003000 08:03 3460216    /usr/lib/libORBitCosNaming-2.so.0.1.0
b6cd7000-b6cd9000 r-xp 00000000 08:03 2031656    /lib/tls/i686/cmov/libutil-2.6.1.so
b6cd9000-b6cdb000 rw-p 00001000 08:03 2031656    /lib/tls/i686/cmov/libutil-2.6.1.so
b6cdb000-b6cef000 r-xp 00000000 08:03 2031765    /lib/libselinux.so.1
b6cef000-b6cf1000 rw-p 00013000 08:03 2031765    /lib/libselinux.so.1
b6cf1000-b6d00000 r-xp 00000000 08:03 2031652    /lib/tls/i686/cmov/libresolv-2.6.1.so
b6d00000-b6d02000 rw-p 0000f000 08:03 2031652    /lib/tls/i686/cmov/libresolv-2.6.1.so
b6d02000-b6d04000 rw-p b6d02000 00:00 0 
b6d04000-b6d12000 r-xp 00000000 08:03 3458220    /usr/lib/libavahi-client.so.3.2.2
b6d12000-b6d13000 rw-p 0000e000 08:03 3458220    /usr/lib/libavahi-client.so.3.2.2
b6d13000-b6d1d000 r-xp 00000000 08:03 3458218    /usr/lib/libavahi-common.so.3.4.4
b6d1d000-b6d1e000 rw-p 00009000 08:03 3458218    /usr/lib/libavahi-common.so.3.4.4
b6d1e000-b6d88000 r-xp 00000000 08:03 3458508    /usr/lib/libgnutls.so.13.3.0
b6d88000-b6d8e000 rw-p 0006a000 08:03 3458508    /usr/lib/libgnutls.so.13.3.0
b6d8e000-b6dc2000 r-xp 00000000 08:03 3457076    /usr/lib/libdbus-1.so.3.3.0
b6dc2000-b6dc3000 rw-p 00033000 08:03 3457076    /usr/lib/libdbus-1.so.3.3.0
b6dc3000-b6ddd000 r-xp 00000000 08:03 3458224    /usr/lib/libdbus-glib-1.so.2.1.0
b6ddd000-b6dde000 rw-p 0001a000 08:03 3458224    /usr/lib/libdbus-glib-1.so.2.1.0
b6dde000-b6ef6000 r-xp 00000000 08:03 3459011    /usr/lib/libxml2.so.2.6.30
b6ef6000-b6efb000 rw-p 00118000 08:03 3459011    /usr/lib/libxml2.so.2.6.30
b6efb000-b6efc000 rw-p b6efb000 00:00 0 
b6efc000-b6f4e000 r-xp 00000000 08:03 3460281    /usr/lib/libbonobo-2.so.0.0.0
b6f4e000-b6f58000 rw-p 00051000 08:03 3460281    /usr/lib/libbonobo-2.so.0.0.0
b6f58000-b6f6c000 r-xp 00000000 08:03 3463098    /usr/lib/libgnome-2.so.0.2000.0
b6f6c000-b6f6d000 rw-p 00014000 08:03 3463098    /usr/lib/libgnome-2.so.0.2000.0
b6f6d000-b6f80000 r-xp 00000000 08:03 3460708    /usr/lib/libbonobo-activation.so.4.0.0
b6f80000-b6f82000 rw-p 00013000 08:03 3460708    /usr/lib/libbonobo-activation.so.4.0.0
b6f82000-b6fd8000 r-xp 00000000 08:03 3460740    /usr/lib/libgnomevfs-2.so.0.2000.0
b6fd8000-b6fdb000 rw-p 00055000 08:03 3460740    /usr/lib/libgnomevfs-2.so.0.2000.0
b6fdb000-b7024000 r-xp 00000000 08:03 3460214    /usr/lib/libORBit-2.so.0.1.0
b7024000-b702d000 rw-p 00049000 08:03 3460214    /usr/lib/libORBit-2.so.0.1.0
b702d000-b702e000 rw-p b702d000 00:00 0 
b702e000-b705d000 r-xp 00000000 08:03 3458216    /usr/lib/libgconf-2.so.4.1.2
b705d000-b7060000 rw-p 0002e000 08:03 3458216    /usr/lib/libgconf-2.so.4.1.2
b7066000-b706f000 r-xp 00000000 08:03 4376781    /opt/firefox/components/libbrowserdirprovider.so
b706f000-b7070000 rw-p 00009000 08:03 4376781    /opt/firefox/components/libbrowserdirprovider.so
b7070000-b7079000 r-xp 00000000 08:03 2031646    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7079000-b707b000 rw-p 00008000 08:03 2031646    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b707b000-b7083000 r-xp 00000000 08:03 2031648    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7083000-b7085000 rw-p 00007000 08:03 2031648    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7085000-b7099000 r-xp 00000000 08:03 2031643    /lib/tls/i686/cmov/libnsl-2.6.1.so
b7099000-b709b000 rw-p 00013000 08:03 2031643    /lib/tls/i686/cmov/libnsl-2.6.1.so
b709b000-b709d000 rw-p b709b000 00:00 0 
b709d000-b70a4000 r-xp 00000000 08:03 2031644    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b70a4000-b70a6000 rw-p 00006000 08:03 2031644    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b70a8000-b70aa000 r-xp 00000000 08:03 3458222    /usr/lib/libavahi-glib.so.1.0.1
b70aa000-b70ab000 rw-p 00001000 08:03 3458222    /usr/lib/libavahi-glib.so.1.0.1
b70ab000-b70ae000 r-xp 00000000 08:03 4376805    /opt/firefox/components/libmozgnome.so
b70ae000-b70af000 rw-p 00003000 08:03 4376805    /opt/firefox/components/libmozgnome.so
b70af000-b70b1000 r-xp 00000000 08:03 3464373    /usr/lib/gconv/UTF-16.so
b70b1000-b70b3000 rw-p 00001000 08:03 3464373    /usr/lib/gconv/UTF-16.so
b70b3000-b70b4000 r-xp 00000000 08:03 3464319    /usr/lib/gconv/ISO8859-1.so
b70b4000-b70b6000 rw-p 00000000 08:03 3464319    /usr/lib/gconv/ISO8859-1.so
b70b6000-b70f5000 r--p 00000000 08:03 3506327    /usr/lib/locale/en_US.utf8/LC_CTYPE
b70f5000-b70f6000 r--p 00000000 08:03 3491785    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b70f6000-b71d6000 r--p 00000000 08:03 3506328    /usr/lib/locale/en_US.utf8/LC_COLLATE
b71d6000-b71d9000 rw-p b71d6000 00:00 0 
b71d9000-b71fb000 r-xp 00000000 08:03 3457436    /usr/lib/libpng12.so.0.15.0
b71fb000-b71fc000 rw-p 00021000 08:03 3457436    /usr/lib/libpng12.so.0.15.0
b71fc000-b71fd000 rw-p b71fc000 00:00 0 
b71fd000-b7212000 r-xp 00000000 08:03 3459124    /usr/lib/libICE.so.6.3.0
b7212000-b7214000 rw-p 00014000 08:03 3459124    /usr/lib/libICE.so.6.3.0
b7214000-b7215000 rw-p b7214000 00:00 0 
b7215000-b721c000 r-xp 00000000 08:03 3459180    /usr/lib/libSM.so.6.0.0
b721c000-b721d000 rw-p 00006000 08:03 3459180    /usr/lib/libSM.so.6.0.0
b721d000-b723b000 r-xp 00000000 08:03 3458002    /usr/lib/libexpat.so.1.0.0
b723b000-b723d000 rw-p 0001e000 08:03 3458002    /usr/lib/libexpat.so.1.0.0
b723d000-b7251000 r-xp 00000000 08:03 3458009    /usr/lib/libz.so.1.2.3.3
b7251000-b7252000 rw-p 00013000 08:03 3458009    /usr/lib/libz.so.1.2.3.3
b7252000-b7259000 r-xp 00000000 08:03 2031653    /lib/tls/i686/cmov/librt-2.6.1.so
b7259000-b725b000 rw-p 00006000 08:03 2031653    /lib/tls/i686/cmov/librt-2.6.1.so
b725b000-b725c000 rw-p b725b000 00:00 0 
b725c000-b7260000 r-xp 00000000 08:03 3457730    /usr/lib/libXdmcp.so.6.0.0
b7260000-b7261000 rw-p 00003000 08:03 3457730    /usr/lib/libXdmcp.so.6.0.0
b7261000-b7263000 r-xp 00000000 08:03 3457728    /usr/lib/libXau.so.6.0.0
b7263000-b7264000 rw-p 00001000 08:03 3457728    /usr/lib/libXau.so.6.0.0
b7264000-b7291000 r-xp 00000000 08:03 3458152    /usr/lib/libpangoft2-1.0.so.0.1800.3
b7291000-b7292000 rw-p 0002c000 08:03 3458152    /usr/lib/libpangoft2-1.0.so.0.1800.3
b7292000-b729a000 r-xp 00000000 08:03 3458307    /usr/lib/libXcursor.so.1.0.2
b729a000-b729b000 rw-p 00007000 08:03 3458307    /usr/lib/libXcursor.so.1.0.2
b729b000-b72a0000 r-xp 00000000 08:03 3458313    /usr/lib/libXrandr.so.2.1.0
b72a0000-b72a1000 rw-p 00005000 08:03 3458313    /usr/lib/libXrandr.so.2.1.0
b72a1000-b72a2000 rw-p b72a1000 00:00 0 
b72a2000-b72a9000 r-xp 00000000 08:03 3458309    /usr/lib/libXi.so.6.0.0
b72a9000-b72aa000 rw-p 00006000 08:03 3458309    /usr/lib/libXi.so.6.0.0
b72aa000-b72ac000 r-xp 00000000 08:03 3458311    /usr/lib/libXinerama.so.1.0.0
b72ac000-b72ad000 rw-p 00001000 08:03 3458311    /usr/lib/libXinerama.so.1.0.0
b72ad000-b72ba000 r-xp 00000000 08:03 3457795    /usr/lib/libXext.so.6.4.0
b72ba000-b72bb000 rw-p 0000d000 08:03 3457795    /usr/lib/libXext.so.6.4.0
b72bb000-b7330000 r-xp 00000000 08:03 3457736    /usr/lib/libcairo.so.2.11.5
b7330000-b7332000 rw-p 00074000 08:03 3457736    /usr/lib/libcairo.so.2.11.5
b7332000-b7336000 r-xp 00000000 08:03 3457756    /usr/lib/libXfixes.so.3.1.0
b7336000-b7337000 rw-p 00003000 08:03 3457756    /usr/lib/libXfixes.so.3.1.0
b7337000-b7338000 rw-p b7337000 00:00 0 
b7338000-b733a000 r-xp 00000000 08:03 3457793    /usr/lib/libXdamage.so.1.1.0
b733a000-b733b000 rw-p 00001000 08:03 3457793    /usr/lib/libXdamage.so.1.1.0
b733b000-b733d000 r-xp 00000000 08:03 3458303    /usr/lib/libXcomposite.so.1.0.0
b733d000-b733e000 rw-p 00001000 08:03 3458303    /usr/lib/libXcomposite.so.1.0.0
b733e000-b7346000 r-xp 00000000 08:03 3458151    /usr/lib/libpangocairo-1.0.so.0.1800.3
b7346000-b7347000 rw-p 00007000 08:03 3458151    /usr/lib/libpangocairo-1.0.so.0.1800.3
b7347000-b748b000 r-xp 00000000 08:03 2031637    /lib/tls/i686/cmov/libc-2.6.1.so
b748b000-b748c000 r--p 00143000 08:03 2031637    /lib/tls/i686/cmov/libc-2.6.1.so
b748c000-b748e000 rw-p 00144000 08:03 2031637    /lib/tls/i686/cmov/libc-2.6.1.so
b748e000-b7491000 rw-p b748e000 00:00 0 
b7491000-b749b000 r-xp 00000000 08:03 2031678    /lib/libgcc_s.so.1
b749b000-b749c000 rw-p 0000a000 08:03 2031678    /lib/libgcc_s.so.1
b749c000-b749d000 rw-p b749c000 00:00 0 
b749d000-b754d000 r-xp 00000000 08:03 3458391    /usr/lib/libstdc++.so.5.0.7
b754d000-b7552000 rw-p 000af000 08:03 3458391    /usr/lib/libstdc++.so.5.0.7
b7552000-b7557000 rw-p b7552000 00:00 0 
b7557000-b756d000 r-xp 00000000 08:03 4376851    /opt/firefox/libxpcom_compat.so
b756d000-b756e000 rw-p 00016000 08:03 4376851    /opt/firefox/libxpcom_compat.so
b756e000-b757f000 r-xp 00000000 08:03 3458148    /usr/lib/libXft.so.2.1.2
b757f000-b7580000 rw-p 00010000 08:03 3458148    /usr/lib/libXft.so.2.1.2
b7580000-b75cd000 r-xp 00000000 08:03 3461237    /usr/lib/libXt.so.6.0.0
b75cd000-b75d1000 rw-p 0004c000 08:03 3461237    /usr/lib/libXt.so.6.0.0
b75d1000-b763d000 r-xp 00000000 08:03 3458012    /usr/lib/libfreetype.so.6.3.16
b763d000-b7641000 rw-p 0006b000 08:03 3458012    /usr/lib/libfreetype.so.6.3.16
b7641000-b7664000 r-xp 00000000 08:03 3457432    /usr/lib/libfontconfig.so.1.2.0
b7664000-b766c000 rw-p 00023000 08:03 3457432    /usr/lib/libfontconfig.so.1.2.0
b766c000-b766d000 rw-p b766c000 00:00 0 
b766d000-b7674000 r-xp 00000000 08:03 3457734    /usr/lib/libXrender.so.1.3.0
b7674000-b7675000 rw-p 00006000 08:03 3457734    /usr/lib/libXrender.so.1.3.0
b7675000-b76bd000 r-xp 00000000 08:03 4376740    /opt/firefox/libsoftokn3.so
b76bd000-b76c1000 rw-p 00047000 08:03 4376740    /opt/firefox/libsoftokn3.so
b76c1000-b7724000 r-xp 00000000 08:03 4376762    /opt/firefox/libnss3.so
b7724000-b7729000 rw-p 00063000 08:03 4376762    /opt/firefox/libnss3.so
b7729000-b774d000 r-xp 00000000 08:03 4376645    /opt/firefox/libssl3.so
b774d000-b774f000 rw-p 00024000 08:03 4376645    /opt/firefox/libssl3.so
b774f000-b776e000 r-xp 00000000 08:03 4376656    /opt/firefox/libsmime3.so
b776e000-b7770000 rw-p 0001f000 08:03 4376656    /opt/firefox/libsmime3.so
b7770000-b7793000 r-xp 00000000 08:03 2031641    /lib/tls/i686/cmov/libm-2.6.1.so
b7793000-b7795000 rw-p 00023000 08:03 2031641    /lib/tls/i686/cmov/libm-2.6.1.so
b7795000-b7799000 r-xp 00000000 08:03 3457750    /usr/lib/libgthread-2.0.so.0.1400.1
b7799000-b779a000 rw-p 00003000 08:03 3457750    /usr/lib/libgthread-2.0.so.0.1400.1
b779a000-b779b000 rw-p b779a000 00:00 0 
b779b000-b7888000 r-xp 00000000 08:03 3457732    /usr/lib/libX11.so.6.2.0
b7888000-b788c000 rw-p 000ed000 08:03 3457732    /usr/lib/libX11.so.6.2.0
b788c000-b7948000 r-xp 00000000 08:03 3457745    /usr/lib/libglib-2.0.so.0.1400.1
b7948000-b7949000 rw-p 000bc000 08:03 3457745    /usr/lib/libglib-2.0.so.0.1400.1
b7949000-b794c000 r-xp 00000000 08:03 3457748    /usr/lib/libgmodule-2.0.so.0.1400.1
b794c000-b794d000 rw-p 00002000 08:03 3457748    /usr/lib/libgmodule-2.0.so.0.1400.1
b794d000-b7987000 r-xp 00000000 08:03 3457749    /usr/lib/libgobject-2.0.so.0.1400.1
b7987000-b7988000 rw-p 0003a000 08:03 3457749    /usr/lib/libgobject-2.0.so.0.1400.1
b7988000-b79c3000 r-xp 00000000 08:03 3458150    /usr/lib/libpango-1.0.so.0.1800.3
b79c3000-b79c5000 rw-p 0003b000 08:03 3458150    /usr/lib/libpango-1.0.so.0.1800.3
b79c5000-b79c6000 rw-p b79c5000 00:00 0 
b79c6000-b79d0000 r-xp 00000000 08:03 3458293    /usr/lib/libpangox-1.0.so.0.1800.3
b79d0000-b79d1000 rw-p 0000a000 08:03 3458293    /usr/lib/libpangox-1.0.so.0.1800.3
b79d1000-b79d7000 r-xp 00000000 08:03 3458294    /usr/lib/libpangoxft-1.0.so.0.1800.3
b79d7000-b79d8000 rw-p 00005000 08:03 3458294    /usr/lib/libpangoxft-1.0.so.0.1800.3
b79d8000-b79ef000 r-xp 00000000 08:03 3458983    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b79ef000-b79f0000 rw-p 00016000 08:03 3458983    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b79f0000-b7a09000 r-xp 00000000 08:03 3457917    /usr/lib/libatk-1.0.so.0.2009.1
b7a09000-b7a0b000 rw-p 00018000 08:03 3457917    /usr/lib/libatk-1.0.so.0.2009.1
b7a0b000-b7a8f000 r-xp 00000000 08:03 3458686    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7a8f000-b7a92000 rw-p 00084000 08:03 3458686    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7a92000-b7e0f000 r-xp 00000000 08:03 3459003    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7e0f000-b7e16000 rw-p 0037c000 08:03 3459003    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7e16000-b7e18000 rw-p b7e16000 00:00 0 
b7e18000-b7e1a000 r-xp 00000000 08:03 2031640    /lib/tls/i686/cmov/libdl-2.6.1.so
b7e1a000-b7e1c000 rw-p 00001000 08:03 2031640    /lib/tls/i686/cmov/libdl-2.6.1.so
b7e1c000-b7e30000 r-xp 00000000 08:03 2031651    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7e30000-b7e32000 rw-p 00013000 08:03 2031651    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7e32000-b7e34000 rw-p b7e32000 00:00 0 
b7e34000-b7e35000 r--p 00000000 08:03 3491806    /usr/lib/locale/en_US.utf8/LC_TIME
b7e35000-b7e36000 r--p 00000000 08:03 3491807    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7e36000-b7e37000 r--p 00000000 08:03 3491790    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7e37000-b7e38000 r--p 00000000 08:03 3491791    /usr/lib/locale/en_US.utf8/LC_PAPER
b7e38000-b7e39000 r--p 00000000 08:03 3491792    /usr/lib/locale/en_US.utf8/LC_NAME
b7e39000-b7e3a000 r--p 00000000 08:03 3491808    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7e3a000-b7e3b000 r--p 00000000 08:03 3491810    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7e3b000-b7e3c000 r--p 00000000 08:03 3491811    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7e3c000-b7e43000 r--s 00000000 08:03 3458003    /usr/lib/gconv/gconv-modules.cache
b7e43000-b7e44000 r--p 00000000 08:03 3491870    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7e44000-b7e6d000 r-xp 00000000 08:03 4376773    /opt/firefox/libnspr4.so
b7e6d000-b7e70000 rw-p 00028000 08:03 4376773    /opt/firefox/libnspr4.so
b7e70000-b7e71000 rw-p b7e70000 00:00 0 
b7e71000-b7e74000 r-xp 00000000 08:03 4376660    /opt/firefox/libplc4.so
b7e74000-b7e75000 rw-p 00003000 08:03 4376660    /opt/firefox/libplc4.so
b7e75000-b7e77000 r-xp 00000000 08:03 4376755    /opt/firefox/libplds4.so
b7e77000-b7e78000 rw-p 00001000 08:03 4376755    /opt/firefox/libplds4.so
b7e78000-b7f1b000 r-xp 00000000 08:03 4376837    /opt/firefox/libxpcom_core.so
b7f1b000-b7f22000 rw-p 000a2000 08:03 4376837    /opt/firefox/libxpcom_core.so
b7f22000-b7f23000 rw-p b7f22000 00:00 0 
b7f23000-b7f25000 r-xp 00000000 08:03 4376663    /opt/firefox/libxpcom.so
b7f25000-b7f26000 rw-p 00001000 08:03 4376663    /opt/firefox/libxpcom.so
b7f26000-b7fbb000 r-xp 00000000 08:03 4376653    /opt/firefox/libmozjs.so
b7fbb000-b7fc1000 rw-p 00094000 08:03 4376653    /opt/firefox/libmozjs.so
b7fc1000-b7fc3000 rw-p b7fc1000 00:00 0 
b7fc3000-b7fdd000 r-xp 00000000 08:03 2031623    /lib/ld-2.6.1.so
b7fdd000-b7fdf000 rw-p 00019000 08:03 2031623    /lib/ld-2.6.1.so
bf842000-bf858000 rw-p bf842000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)


At a loss here, posting with Opera, any help welcome.

---

### Post by waste301 on 2008-04-07
bump

---

### Post by wolfen69 on 2008-04-07
remember after uninstalling, to do:
```
sudo apt-get clean
```
that removes tmp files of whatever you are going to re-install, assuring that you get a new, "clean" app upon re-install. otherwise it justs re-installs from tmp directory instead of downloading a new one. hope this helps.

---

### Post by waste301 on 2008-04-07
> **wolfen69 said:**
> remember after uninstalling, to do:
```
sudo apt-get clean
```
that removes tmp files of whatever you are going to re-install, assuring that you get a new, "clean" app upon re-install. otherwise it justs re-installs from tmp directory instead of downloading a new one. hope this helps.

So enter that command and then use add/remove and get firrefox?

---

### Post by InfinityCircuit on 2008-04-07
Try:
```
sudo rm -rf /opt/firefox
sudo dpkg -P firefox
sudo apt-get install -f
sudo apt-get install firefox
```

You seem to have remnants of firefox 3 in /opt/firefox.  This will clean them up, uninstall your firefox 2, make sure everything is working, and then install a fresh copy of firefox.

---

### Post by Inxsible on 2008-04-07
You should also get rid of the personal settings for firefox under your home directory apart from the apt-get clean advice from wolfen.

Another way to un-install things is to use the purge flag in apt-get```
sudo apt-get purge <program-name>
``` That ensures that all settings files also get removed along with the app.

---

### Post by waste301 on 2008-04-07
> **InfinityCircuit said:**
> Try:
```
sudo rm -rf /opt/firefox
sudo dpkg -P firefox
sudo apt-get install -f
sudo apt-get install firefox
```

You seem to have remnants of firefox 3 in /opt/firefox.  This will clean them up, uninstall your firefox 2, make sure everything is working, and then install a fresh copy of firefox.

OK, the first suggestion didn't work.  I'll try.

---

### Post by waste301 on 2008-04-07
> **InfinityCircuit said:**
> Try:
```
sudo rm -rf /opt/firefox
sudo dpkg -P firefox
sudo apt-get install -f
sudo apt-get install firefox
```

You seem to have remnants of firefox 3 in /opt/firefox.  This will clean them up, uninstall your firefox 2, make sure everything is working, and then install a fresh copy of firefox.

OK - before I try and install anything yet again - my link in applications-->firefox is now dead (good)

What is the best way to now reinstall?

---

### Post by Inxsible on 2008-04-07
> **waste301 said:**
> OK - before I try and install anything yet again - my link in applications-->firefox is now dead (good)

What is the best way to now reinstall?```
sudo aptitude install firefox
``` Simple and sweet !!!

Command Line Rocks !! ;-)

---

### Post by waste301 on 2008-04-07
> **Inxsible said:**
> ```
sudo aptitude install firefox
``` Simple and sweet !!!

Command Line Rocks !! ;-)

None of this is working.  Is there any way to remove all traces of firefox from my PC and install FF2 from scratch?

I can import my bookmarks from Opera and just start over.

---

### Post by InfinityCircuit on 2008-04-07
If you really want to totally purge firefox from your system:

```
sudo updatedb
sudo rm -rf $(locate firefox | xargs)

```

then reinstall firefox.

---

### Post by waste301 on 2008-04-07
> **InfinityCircuit said:**
> If you really want to totally purge firefox from your system:

```
sudo updatedb
sudo rm -rf $(locate firefox | xargs)

```

then reinstall firefox.

 sudo rm -rf $(locate firefox | xargs)
bash: /usr/bin/sudo: Argument list too long

---

### Post by waste301 on 2008-04-07
I cannot get rid of firefox.

---

### Post by InfinityCircuit on 2008-04-07
```
sudo su
locate firefox | xargs rm -rf

```

This is a slight variant on the previous that should work.

If that fails, you can try:

```
sudo find / -name *firefox* -delete
```

---

### Post by waste301 on 2008-04-07
> **InfinityCircuit said:**
> ```
sudo su
locate firefox | xargs rm -rf

```

This is a slight variant on the previous that should work.

If that fails, you can try:

```
sudo find / -name *firefox* -delete
```

i tried the first one, but am holding off on the second, as I would like to preserve my backup.  Should I reboot and try to install firefox?  What is the best way to do that?

Thanks for the response.  My PC actually seemed to do something with tthat command.

---

### Post by Inxsible on 2008-04-07
> **waste301 said:**
> i tried the first one, but am holding off on the second, as I would like to preserve my backup.  Should I reboot and try to install firefox?  What is the best way to do that?

Thanks for the response.  My PC actually seemed to do something with tthat command.
There is no need to reboot when you un-install any software (except for kernel specific packages)

That is one huge advantage of Linux over Windows.

---

### Post by waste301 on 2008-04-07
> **Inxsible said:**
> There is no need to reboot when you un-install any software (except for kernel specific packages)

That is one huge advantage of Linux over Windows.

OK - that is what I thought.

Is there a command I can now use to install Firefox 2?  I am afraid of installing FF3 again.

---

### Post by InfinityCircuit on 2008-04-07
apt-cache policy firefox

will reveal the status of the firefox package in the repositories.  If it is acceptable to you (e.g. 2.0.0.x) then you can install it with:

apt-get install firefox

---

### Post by Inxsible on 2008-04-07
> **waste301 said:**
> OK - that is what I thought.

Is there a command I can now use to install Firefox 2?  I am afraid of installing FF3 again.You can even search for firefox in Synaptic and install that. If you are still using the Gutsy repos, then firefox 2 will definitely be in the repos.

maybe we are using an incorrect package name and thats why you can't install thru command line.

After you install the version in the repos, you can start it up and it will get all the updates.

---

### Post by waste301 on 2008-04-07
> **InfinityCircuit said:**
> apt-cache policy firefox

will reveal the status of the firefox package in the repositories.  If it is acceptable to you (e.g. 2.0.0.x) then you can install it with:

apt-get install firefox

firefox:
  Installed: 2.0.0.13+1nobinonly-0ubuntu0.7.10
  Candidate: 2.0.0.13+1nobinonly-0ubuntu0.7.10
  Version table:
 *** 2.0.0.13+1nobinonly-0ubuntu0.7.10 0
        500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
        100 /var/lib/dpkg/status
     2.0.0.6+2nobinonly-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages

So I am going to try:

apt-get install firefox

I've tried that before and it has failed - I'l wait for a reponse before I do.

---

### Post by waste301 on 2008-04-07
matt@mattspc:~$ apt-get install firefox
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

dammit - I'm getting frustrated

---

### Post by InfinityCircuit on 2008-04-07
You need to use "sudo" to get the correct permissions to use apt-get.  See [http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html) for more information.

---

### Post by waste301 on 2008-04-07
> **InfinityCircuit said:**
> You need to use "sudo" to get the correct permissions to use apt-get.  See [http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html) for more information.

matt@mattspc:~$ sudo apt-get install firefox
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks, but nothing is installing.  I cannot tell whether FF is there and I just don't know where, or if there is some remnant left from uninstalling that makes ubuntu THINK it is there.  I am going to try:

sudo find / -name *firefox* -delete

that looks like it will remove everything FF related, I will then try anyone's suggested reinstall moethod and hope for the best.

---

### Post by waste301 on 2008-04-07
> **waste301 said:**
> matt@mattspc:~$ sudo apt-get install firefox
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks, but nothing is installing.  I cannot tell whether FF is there and I just don't know where, or if there is some remnant left from uninstalling that makes ubuntu THINK it is there.  I am going to try:

sudo find / -name *firefox* -delete

that looks like it will remove everything FF related, I will then try anyone's suggested reinstall moethod and hope for the best.

sudo find / -name *firefox* -delete

appeared to do nothing.  I just got a blinking cursor afterwards.

---

### Post by InfinityCircuit on 2008-04-07
```
sudo dpkg -P firefox
```

See if that generates any errors.

I love linux because there are always 10 million different ways to do something :)

---

### Post by waste301 on 2008-04-07
> **InfinityCircuit said:**
> ```
sudo dpkg -P firefox
```

See if that generates any errors.

I love linux because there are always 10 million different ways to do something :)

matt@mattspc:~$ sudo dpkg -P firefox
(Reading database ... 
dpkg: serious warning: files list file for package `mozilla-firefox-locale-en-gb' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `firefox' missing, assuming package has no files currently installed.
142865 files and directories currently installed.)
Removing firefox ...
Purging configuration files for firefox ...
matt@mattspc:~$ 

Thats what I got - it looks pretty serious.  What would be next?

---

### Post by InfinityCircuit on 2008-04-07
now try a ```
sudo apt-get install -f
sudo apt-get install firefox
```

---

### Post by waste301 on 2008-04-07
> **InfinityCircuit said:**
> now try a ```
sudo apt-get install -f
sudo apt-get install firefox
```

matt@mattspc:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
matt@mattspc:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  firefox-gnome-support latex-xft-fonts
Recommended packages:
  ubufox
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9197kB of archives.
After unpacking 26.7MB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main firefox 2.0.0.13+1nobinonly-0ubuntu0.7.10 [9197kB]
Fetched 9197kB in 25s (354kB/s)                                                
Selecting previously deselected package firefox.
(Reading database ... 
dpkg: serious warning: files list file for package `mozilla-firefox-locale-en-gb' missing, assuming package has no files currently installed.
142866 files and directories currently installed.)
Unpacking firefox (from .../firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb) ...
Setting up firefox (2.0.0.13+1nobinonly-0ubuntu0.7.10) ...
Please restart any running Firefoxes, or you will experience problems.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


OK - it appeared to actually DL something and install it.  Do I dare just goto applications-->internet--->firefox web browser or should I restart or something?

---

### Post by Inxsible on 2008-04-07
No reboots are not needed in Linux (unless you install kernel specific package) Just start up firefox

---

### Post by InfinityCircuit on 2008-04-07
You can just try running firefox.

I'd also recommend trying a:

```
sudo apt-get install --reinstall mozilla-firefox-locale-en-gb
``` to fix that error message.

---

### Post by waste301 on 2008-04-07
> **InfinityCircuit said:**
> You can just try running firefox.

I'd also recommend trying a:

```
sudo apt-get install --reinstall mozilla-firefox-locale-en-gb
``` to fix that error message.

Thanks -  I really appreciate the help.  I still have no icon on my desktop, or the bar at the top of my screen, and when I go into applications-->internet--->firefox I get this:

Failed to execute child process "firefox" (No such file or directory)

I can't stay up any longer and argue with it, I spent all day cleaning and helping suture a chainsaw wound, of all things, and have to get up at 6am tomorrow.  If you can think of anything else to try I will, and reply tomorrow afternoon.

---

### Post by alpdo on 2008-04-07
hello every one

---

### Post by InfinityCircuit on 2008-04-07
A couple of things come to mind:

1. Run firefox from a terminal and see what the output is.  You might just have a broken link in your apps file.

2. Start over and fix the error message it gives you:
```
sudo apt-get remove --purge firefox*
sudo dpkg -P firefox
sudo dpkg -P mozilla-firefox-locale-en-gb
sudo apt-get install -f
sudo apt-get install firefox
```

3. download a tarball of firefox from mozilla:
```
sudo apt-get remove --purge firefox*
sudo dpkg -P firefox
sudo dpkg -P mozilla-firefox-locale-en-gb
wget http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/2.0.0.13/linux-i686/en-GB/firefox-2.0.0.13.tar.gz  
tar -zxvf firefox-2.0.0.13.tar.gz 
sudo ln -s ./firefox/firefox /usr/local/bin/firefox
```

This will manually install firefox in a self-contained directory in your home directory, and put a link to it inside your path.  The old links in the applications folder should still work.

---

### Post by beanco on 2008-05-21
stuck in ff land to. i mena I cannot get it removed or launch it.

if I try to launch from teh comman dline it opens, and then closes in 2 seconds and give me a segmentaion fault/core dumped message


I tried this

```
rob@rob-desktop:~$ sudo dpkg -P firefox
```

 and got 
```

dpkg: dependency problems prevent removal of firefox:
 yelp depends on firefox (>= 1.5).
 epiphany-browser depends on firefox (>= 1.5).
 galeon depends on firefox (>= 1.5).
dpkg: error processing firefox (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 firefox
rob@rob-desktop:~$ 

```

I have tried purging too.. .but I cannot get rid of FF, epiphany or evolution and I cannot get them to launch.

sorry to steal the thread but I need help

thanks

robi

---

