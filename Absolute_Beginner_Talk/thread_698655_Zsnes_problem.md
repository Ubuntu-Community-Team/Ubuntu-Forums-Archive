---
title: "Zsnes problem"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by acropolen on 2008-02-16
Hello, I'm running 7.10 Gutsy and I am having difficulty with Zsnes. The first few times I used it, it worked great. Now whenever I try to open it from apps it shows a black window and then immediately disappears. I typed zsnes into terminal and got this:
gendo@gendo-desktop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** glibc detected *** zsnes: free(): invalid pointer: 0x08948f78 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7bb0d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7bb4800]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7d78d81]
/usr/lib/libmcop.so.1(_ZN4Arts11readTypeSeqINS_12InterfaceDefEEEvRNS_6BufferERSt6vectorIT_SaIS5_EE+0x1a4)[0xa4284e34]
/usr/lib/libmcop.so.1(_ZN4Arts9ModuleDef8readTypeERNS_6BufferE+0x5f)[0xa426106f]
/usr/lib/libmcop.so.1(_ZN4Arts9ModuleDefC1ERNS_6BufferE+0xa4)[0xa42612f4]
/usr/lib/libmcop.so.1(_ZN4Arts10IDLFileReg7startupEv+0xb5)[0xa4261ef5]
/usr/lib/libmcop.so.1(_ZN4Arts14StartupManager7startupEv+0x3e)[0xa4235dbe]
/usr/lib/libmcop.so.1(_ZN4Arts10DispatcherC1EPNS_9IOManagerENS0_11StartServerE+0x830)[0xa426a840]
/usr/lib/libartscbackend.so.0(arts_backend_init+0xa0)[0xa4508360]
/usr/lib/libartsc.so.0(arts_init+0x239)[0xb7f298d9]
/usr/lib/ao/plugins-2/libarts.so(ao_plugin_test+0x17)[0xb7f2e987]
/usr/lib/libao.so.2(ao_default_driver_id+0x63)[0xb7e55253]
zsnes[0x82ebf05]
======= Memory map: ========
08048000-08305000 r-xp 00000000 08:11 2594476    /usr/bin/zsnes
08305000-08344000 rw-p 002bc000 08:11 2594476    /usr/bin/zsnes
08344000-08cbc000 rw-p 08344000 00:00 0          [heap]
a3f00000-a3f21000 rw-p a3f00000 00:00 0 
a3f21000-a4000000 ---p a3f21000 00:00 0 
a408f000-a40c5000 r-xp 00000000 08:11 2596776    /usr/lib/libkmedia2_idl.so.1.0.0
a40c5000-a40d3000 rw-p 00035000 08:11 2596776    /usr/lib/libkmedia2_idl.so.1.0.0
a40d3000-a40ed000 r-xp 00000000 08:11 2595787    /usr/lib/libvorbis.so.0.4.0
a40ed000-a40fb000 rw-p 0001a000 08:11 2595787    /usr/lib/libvorbis.so.0.4.0
a40fb000-a4106000 r-xp 00000000 08:11 2595789    /usr/lib/libvorbisenc.so.2.0.3
a4106000-a41f4000 rw-p 0000b000 08:11 2595789    /usr/lib/libvorbisenc.so.2.0.3
a41f4000-a4294000 r-xp 00000000 08:11 2596777    /usr/lib/libmcop.so.1.0.0
a4294000-a42a2000 rw-p 000a0000 08:11 2596777    /usr/lib/libmcop.so.1.0.0
a42a2000-a4332000 r-xp 00000000 08:11 2596768    /usr/lib/libartsflow_idl.so.1.0.0
a4332000-a435a000 rw-p 00090000 08:11 2596768    /usr/lib/libartsflow_idl.so.1.0.0
a435a000-a43a8000 r-xp 00000000 08:11 2596780    /usr/lib/libsoundserver_idl.so.1.0.0
a43a8000-a43bf000 rw-p 0004e000 08:11 2596780    /usr/lib/libsoundserver_idl.so.1.0.0
a43bf000-a44c8000 r-xp 00000000 08:11 2596767    /usr/lib/libartsflow.so.1.0.0
a44c8000-a44e6000 rw-p 00108000 08:11 2596767    /usr/lib/libartsflow.so.1.0.0
a44e6000-a44eb000 rw-p a44e6000 00:00 0 
a44ff000-a450d000 r-xp 00000000 08:11 2596764    /usr/lib/libartscbackend.so.0.0.0
a450d000-a4510000 rw-p 0000d000 08:11 2596764    /usr/lib/libartscbackend.so.0.0.0
a4510000-a451e000 rw-p a50bd000 00:00 0 
a451e000-a451f000 r-xp 00000000 08:11 3513449    /usr/lib/gconv/ISO8859-1.so
a451f000-a4521000 rw-p 00000000 08:11 3513449    /usr/lib/gconv/ISO8859-1.so
a4521000-a4528000 r--s 00000000 08:11 3513025    /usr/lib/gconv/gconv-modules.cache
a4528000-a46a7000 rw-p a4528000 00:00 0 
a46b0000-a4bb0000 rw-s 0000b000 00:0d 16965      /dev/dri/card0
a4bb0000-a50b0000 rw-s 0000a000 00:0d 16965      /dev/dri/card0
a50b0000-a50ba000 rw-p a50b0000 00:00 0 
a50ba000-a50bd000 rw-s 00028000 00:0d 16965      /dev/dri/card0
a50bd000-a50c1000 r-xp 00000000 08:11 2595623    /usr/lib/libogg.so.0.5.3
a50c1000-a50c2000 rw-p 00003000 08:11 2595623    /usr/lib/libogg.so.0.5.3
a50c2000-a5103000 rw-p a50c2000 00:00 0 
a5103000-a5243000 rw-s 00025000 00:0d 16965      /dev/dri/card0
a5243000-a5883000 rw-s 00007000 00:0d 16965      /dev/dri/card0
a5883000-a5983000 rw-s 00006000 00:0d 16965      /dev/dri/card0
a5983000-a5993000 rw-s 00004000 00:0d 16965      /dev/dri/card0
a5993000-b5973000 rw-s 00003000 00:0d 16965      /dev/dri/card0
b5973000-b5a23000 r-xp 00000000 08:11 2594508    /usr/lib/libstdc++.so.5.0.7
b5a23000-b5a28000 rw-p 000af000 08:11 2594508    /usr/lib/libstdc++.so.5.0.7
b5a28000-b5a2d000 rw-p b5a28000 00:00 0 
b5a2d000-b62bb000 r-xp 00000000 08:11 3266801    /usr/lib/dri/fglrx_dri.so
b62bb000-b6306000 rw-p 0088e000 08:11 3266801    /usr/lib/dri/fglrx_dri.so
b6306000-b6390000 rw-p b6306000 00:00 0 
b6390000-b6394000 r-xp 00000000 08:11 2595065    /usr/lib/libXfixes.so.3.1.0
b6394000-b6395000 rw-p 00003000 08:11 2595065    /usr/lib/libXfixes.so.3.1.0
b6395000-b639d000 r-xp 00000000 08:11 2595055    /usr/lib/libXcursor.so.1.0.2
b639d000-b639e000 rw-p 00007000 08:11 2595055    /usr/lib/libXcursor.so.1.0.2
b639e000-b63a3000 r-xp 00000000 08:11 2595083    /usr/lib/libXrandr.so.2.1.0
b63a3000-b63a4000 rw-p 00005000 08:11 2595083    /usr/lib/libXrandr.so.2.1.0
b63a4000-b63ab000 r-xp 00000000 08:11 2595085    /usr/lib/libXrender.so.1.3.0
b63ab000-b63ac000 rw-p 00006000 08:11 2595085    /usr/lib/libXrender.so.1.3.0
b63ac000-b63ad000 ---p b63ac000 00:00 0 
b63ad000-b6bad000 rwxp b63ad000 00:00 0 
b6bad000-b76dc000 rw-p b6bad000 00:00 0 
b76dc000-b7729000 r-xp 00000000 08:11 2595089    /usr/lib/libXt.so.6.0.0
b7729000-b772d000 rw-p 0004c000 08:11 2595089    /usr/lib/libXt.so.6.0.0
b772d000-b7742000 r-xp 00000000 08:11 2596747    /usr/lib/libaudio.so.2.4
b7742000-b7743000 rw-p 00014000 08:11 2596747    /usr/lib/libaudio.so.2.4
b7743000-b7763000 r-xp 00000000 08:11 2595125    /usr/lib/libaudiofile.so.0.0.2
b7763000-b7765000 rw-p 00020000 08:11 2595125    /usr/lib/libaudiofile.so.0.0.2
b7767000-b776e000 r-xp 00000000 08:11 2595791    /usr/lib/libvorbisfile.so.3.2.0
b776e000-b776f000 rw-p 00006000 08:11 2595791    /usr/lib/libvorbisfile.so.3.2.0
b776f000-b7772000 rw-p b776f000 00:00 0 
b7772000-b7779000 rwxp b7772000 00:00 0 
b7779000-b778e000 r-xp 00000000 08:11 2595020    /usr/lib/libICE.so.6.3.0
b778e000-b7790000 rw-p 00014000 08:11 2595020    /usr/lib/libICE.so.6.3.0
b7790000-b7791000 rw-p b7790000 00:00 0 
b7791000-b7798000 r-xp 00000000 08:11 2595038    /usr/lib/libSM.so.6.0.0
b7798000-b7799000 rw-p 00006000 08:11 2595038    /usr/lib/libSM.so.6.0.0
b7799000-b779c000 r-xp 00000000 08:11 295531     /lib/libcap.so.1.10
b779c000-b779d000 rw-p 00002000 08:11 295531     /lib/libcap.so.1.10
b779d000-b77d4000 r-xp 00000000 08:11 2597340    /usr/lib/libpulse.so.0.2.0
b77d4000-b77d5000 rw-p 00037000 08:11 2597340    /usr/lib/libpulse.so.0.2.0
b77d5000-b77d8000 r-xp 00000000 08:11 2597341    /usr/lib/libpulse-simple.so.0.0.0
b77d8000-b77d9000 rw-p 00002000 08:11 2597341    /usr/lib/libpulse-simple.so.0.0.0
b77d9000-b7895000 r-xp 00000000 08:11 2595342    /usr/lib/libglib-2.0.so.0.1400.1
b7895000-b7896000 rw-p 000bc000 08:11 2595342    /usr/lib/libglib-2.0.so.0.1400.1
b7896000-b789d000 r-xp 00000000 08:11 344809     /lib/tls/i686/cmov/librt-2.6.1.so
b789d000-b789f000 rw-p 00006000 08:11 344809     /lib/tls/i686/cmov/librt-2.6.1.so
b789f000-b78a3000 r-xp 00000000 08:11 2595454    /usr/lib/libgthread-2.0.so.0.1400.1
b78a3000-b78a4000 rw-p 00003000 08:11 2595454    /usr/lib/libgthread-2.0.so.0.1400.1
b78a4000-b78a5000 rw-s 00005000 00:0d 16965      /dev/dri/card0
b78a5000-b78a7000 rw-s 00002000 00:0d 16965      /dev/dri/card0
b78a7000-b78a9000 r-xp 00000000 08:11 2626705    /usr/lib/ao/plugins-2/liboss.so
b78a9000-b78aa000 rw-p 00001000 08:11 2626705    /usr/lib/ao/plugins-2/liboss.so
b78aa000-b78ab000 r-xp 00000000 08:11 2626704    /usr/lib/ao/plugins-2/libnas.so
b78ab000-b78ac000 rw-p 00001000 08:11 2626704    /usr/lib/ao/plugins-2/libnas.so
b78ac000-b78b5000 r-xp 00000000 08:11 2594140    /usr/lib/libesd.so.0.2.38
b78b5000-b78b6000 rw-p 00009000 08:11 2594140    /usr/lib/libesd.so.0.2.38
b78b6000-b78b7000 r-xp 00000000 08:11 2626703    /usr/lib/ao/plugins-2/libesd.so
b78b7000-b78b8000 rw-p 00000000 08:11 2626703    /usr/lib/ao/plugins-2/libesd.so
b78b8000-b78c1000 r-xp 00000000 08:11 344802     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b78c1000-b78c3000 rw-p 00008000 08:11 344802     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b78c3000-b78cb000 r-xp 00000000 08:11 344804     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b78cb000-b78cd000 rw-p 00007000 08:11 344804     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b78cd000-b78e1000 r-xp 00000000 08:11 344799     /lib/tls/i686/cmov/libnsl-2.6.1.so
b78e1000-b78e3000 rw-p 00013000 08:11 344799     /lib/tls/i686/cmov/libnsl-2.6.1.so
b78e3000-b78e5000 rw-p b78e3000 00:00 0 
b78e5000-b78ec000 r-xp 00000000 08:11 344800     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b78ec000-b78ee000 rw-p 00006000 08:11 344800     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b78ee000-b78f0000 rw-p b78ee000 00:00 0 
b78f0000-b78f4000 r-xp 00000000 08:11 2595059    /usr/lib/libXdmcp.so.6.0.0
b78f4000-b78f5000 rw-p 00003000 08:11 2595059    /usr/lib/libXdmcp.so.6.0.0
b78f5000-b78f7000 r-xp 00000000 08:11 2595048    /usr/lib/libXau.so.6.0.0
b78f7000-b78f8000 rw-p 00001000 08:11 2595048    /usr/lib/libXau.so.6.0.0
b78f8000-b79e5000 r-xp 00000000 08:11 2595042    /usr/lib/libX11.so.6.2.0
b79e5000-b79e9000 rw-p 000ed000 08:11 2595042    /usr/lib/libX11.so.6.2.0
b79e9000-b79f6000 r-xp 00000000 08:11 2595063    /usr/lib/libXext.so.6.4.0
b79f6000-b79f7000 rw-p 0000d000 08:11 2595063    /usr/lib/libXext.so.6.4.0
b79f7000-b79f8000 rw-p b79f7000 00:00 0 
b79f8000-b7a06000 r-xp 00000000 08:11 2595202    /usr/lib/libdirect-0.9.so.25.0.0
b7a06000-b7a07000 rw-p 0000e000 08:11 2595202    /usr/lib/libdirect-0.9.so.25.0.0
b7a07000-b7a0c000 r-xp 00000000 08:11 2595268    /usr/lib/libfusion-0.9.so.25.0.0
b7a0c000-b7a0d000 rw-p 00004000 08:11 2595268    /usr/lib/libfusion-0.9.so.25.0.0
b7a0d000-b7a62000 r-xp 00000000 08:11 2595204    /usr/lib/libdirectfb-0.9.so.25.0.0
b7a62000-b7a64000 rw-p 00055000 08:11 2595204    /usr/lib/libdirectfb-0.9.so.25.0.0
b7a64000-b7a66000 r-xp 00000000 08:11 344796     /lib/tls/i686/cmov/libdl-2.6.1.so
b7a66000-b7a68000 rw-p 00001000 08:11 344796     /lib/tls/i686/cmov/libdl-2.6.1.so
b7a68000-b7b29000 r-xp 00000000 08:11 2595115    /usr/lib/libasound.so.2.0.0
b7b29000-b7b2e000 rw-p 000c0000 08:11 2595115    /usr/lib/libasound.so.2.0.0
b7b2e000-b7b42000 r-xp 00000000 08:11 344807     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7b42000-b7b44000 rw-p 00013000 08:11 344807     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7b44000-b7b47000 rw-p b7b44000 00:00 0 
b7b47000-b7c8b000 r-xp 00000000 08:11 344793     /lib/tls/i686/cmov/libc-2.6.1.so
b7c8b000-b7c8c000 r--p 00143000 08:11 344793     /lib/tls/i686/cmov/libc-2.6.1.so
b7c8c000-b7c8e000 rw-p 00144000 08:11 344793     /lib/tls/i686/cmov/libc-2.6.1.so
b7c8e000-b7c91000 rw-p b7c8e000 00:00 0 
b7c91000-b7c9b000 r-xp 00000000 08:11 295555     /lib/libgcc_s.so.1
b7c9b000-b7c9c000 rw-p 0000a000 08:11 295555     /lib/libgcc_s.so.1
b7c9c000-b7cbf000 r-xp 00000000 08:11 344797     /lib/tls/i686/cmov/libm-2.6.1.so
b7cbf000-b7cc1000 rw-p 00023000 08:11 344797     /lib/tls/i686/cmov/libm-2.6.1.so
b7cc1000-b7da9000 r-xp 00000000 08:11 2595756    /usr/lib/libstdc++.so.6.0.9
b7da9000-b7dac000 r--p 000e8000 08:11 2595756    /usr/lib/libstdc++.so.6.0.9
b7dac000-b7dae000 rw-p 000eb000 08:11 2595756    /usr/lib/libstdc++.so.6.0.9
b7dae000-b7db4000 rw-p b7dae000 00:00 0 
b7db4000-b7e4c000 r-xp 00000000 08:11 2597107    /usr/lib/libGL.so.1.2
b7e4c000-b7e51000 rw-p 00098000 08:11 2597107    /usr/lib/libGL.so.1.2
b7e51000-b7e54000 rw-p b7e51000 00:00 0 
b7e54000-b7e57000 r-xp 00000000 08:11 2595105    /usr/lib/libao.so.2.1.3
b7e57000-b7e58000 rw-p 00003000 08:11 2595105    /usr/lib/libao.so.2.1.3
b7e58000-b7e7a000 r-xp 00000000 08:11 2594535    /usr/lib/libpng12.so.0.15.0
b7e7a000-b7e7b000 rw-p 00021000 08:11 2594535    /usr/lib/libpng12.so.0.15.0
b7e7b000-b7e7c000 rw-p b7e7b000 00:00 0 
b7e7c000-b7ee1000 r-xp 00000000 08:11 2595036    /usr/lib/libSDL-1.2.so.0.11.0
b7ee1000-b7ee3000 rw-p 00065000 08:11 2595036    /usr/lib/libSDL-1.2.so.0.11.0
b7ee3000-b7f0b000 rw-p b7ee3000 00:00 0 
b7f0b000-b7f1f000 r-xp 00000000 08:11 2595826    /usr/lib/libz.so.1.2.3.3
b7f1f000-b7f20000 rw-p 00013000 08:11 2595826    /usr/lib/libz.so.1.2.3.3
b7f20000-b7f21000 rw-p b7f20000 00:00 0 
b7f21000-b7f23000 r-xp 00000000 08:11 2626706    /usr/lib/ao/plugins-2/libpulse.so
b7f23000-b7f24000 rw-p 00001000 08:11 2626706    /usr/lib/ao/plugins-2/libpulse.so
b7f24000-b7f27000 r-xp 00000000 08:11 2595352    /usr/lib/libgmodule-2.0.so.0.1400.1
b7f27000-b7f28000 rw-p 00002000 08:11 2595352    /usr/lib/libgmodule-2.0.so.0.1400.1
b7f28000-b7f2d000 r-xp 00000000 08:11 2596745    /usr/lib/libartsc.so.0.0.0
b7f2d000-b7f2e000 rw-p 00004000 08:11 2596745    /usr/lib/libartsc.so.0.0.0
b7f2e000-b7f2f000 r-xp 00000000 08:11 2626702    /usr/lib/ao/plugins-2/libarts.so
b7f2f000-b7f30000 rw-p 00000000 08:11 2626702    /usr/lib/ao/plugins-2/libarts.so
b7f30000-b7f33000 r-xp 00000000 08:11 2626701    /usr/lib/ao/plugins-2/libalsa09.so
b7f33000-b7f34000 rw-p 00002000 08:11 2626701    /usr/lib/ao/plugins-2/libalsa09.so
b7f34000-b7f36000 rw-p b7f34000 00:00 0 
b7f36000-b7f50000 r-xp 00000000 08:11 295501     /lib/ld-2.6.1.so
b7f50000-b7f52000 rw-p 00019000 08:11 295501     /lib/ld-2.6.1.so
bff4f000-bff64000 rwxp bff4f000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

Any help is greatly appreciated.

---

### Post by Linux_Man on 2008-02-16
Try reinstalling it

sudo apt-get purge zsnes
sudo apt-get install zsnes

---

### Post by acropolen on 2008-02-16
no good, still the same problem

---

### Post by acropolen on 2008-02-16
bump

---

