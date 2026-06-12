---
title: "Firefox 2.0.0.6 Crash in Gusty when Bookmarking"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by cvaty on 2007-09-10
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20070827 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6


hi i'm new to this, so i'm not sure exactly where i should post my bugs... maybe someone can point me in the right direction.  but i have a firefox crash that happens when attempting to bookmark anything.  

$ firefox

**  ctrl-D to bookmark  ** (same happens if i bookmarks > add bookmark from the menu
terminal output is:

```
cvaty@cvaty-laptop:~$ firefox
*** glibc detected *** /usr/lib/firefox/firefox-bin: double free or corruption (out): 0x08ab0c80 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76c7d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb76cb800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb74db8c1]
/usr/lib/firefox/components/libgfx_gtk.so[0xb55ae698]
/usr/lib/firefox/components/libgfx_gtk.so[0xb55cd9d3]
/usr/lib/firefox/components/libgklayout.so[0xb56f8e6d]
/usr/lib/firefox/components/libgklayout.so[0xb56f9be7]
/usr/lib/firefox/components/libgklayout.so[0xb573a5c2]
/usr/lib/firefox/components/libgklayout.so[0xb584e821]
/usr/lib/firefox/components/libgklayout.so[0xb584e692]
/usr/lib/firefox/components/libgklayout.so[0xb584e327]
/usr/lib/firefox/components/libgklayout.so[0xb584e785]
/usr/lib/firefox/components/libgklayout.so[0xb584e692]
/usr/lib/firefox/components/libgklayout.so[0xb584e327]
/usr/lib/firefox/components/libgklayout.so[0xb584e785]
/usr/lib/firefox/components/libgklayout.so[0xb584e692]
/usr/lib/firefox/components/libgklayout.so[0xb584e327]
/usr/lib/firefox/components/libgklayout.so[0xb584e785]
/usr/lib/firefox/components/libgklayout.so[0xb584e692]
/usr/lib/firefox/components/libgklayout.so[0xb584e327]
/usr/lib/firefox/components/libgklayout.so[0xb584e785]
/usr/lib/firefox/components/libgklayout.so[0xb584e692]
/usr/lib/firefox/components/libgklayout.so[0xb584e327]
/usr/lib/firefox/components/libgklayout.so[0xb584e785]
/usr/lib/firefox/components/libgklayout.so[0xb584e692]
/usr/lib/firefox/components/libgklayout.so[0xb584e327]
/usr/lib/firefox/components/libgklayout.so[0xb584e785]
/usr/lib/firefox/components/libgklayout.so[0xb5736e99]
/usr/lib/firefox/components/libgklayout.so[0xb5736ce4]
/usr/lib/firefox/components/libgklayout.so[0xb5736567]
/usr/lib/firefox/components/libgklayout.so[0xb5712211]
/usr/lib/firefox/components/libgklayout.so[0xb59e0275]
/usr/lib/firefox/components/libgklayout.so[0xb59e2eb0]
/usr/lib/firefox/components/libgklayout.so[0xb59e914f]
/usr/lib/firefox/components/libgklayout.so[0xb59ea77d]
/usr/lib/firefox/components/libgklayout.so[0xb59eb18c]
/usr/lib/firefox/components/libgklayout.so[0xb59dff76]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb670fdfe]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb6707e02]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb6707e89]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b88ba2]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb7570772]
/usr/lib/libgobject-2.0.so.0[0xb75812fd]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb75825cf]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb75829c9]
/usr/lib/libgtk-x11-2.0.so.0[0xb7cc22f8]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x42f)[0xb7b81eef]
/usr/lib/libgdk-x11-2.0.so.0[0xb79bb831]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0x97)[0xb79bba57]
/usr/lib/libgdk-x11-2.0.so.0[0xb79bbabb]
/usr/lib/libgdk-x11-2.0.so.0[0xb79a1a48]
/usr/lib/libglib-2.0.so.0[0xb74d2551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb74d411c]
/usr/lib/libglib-2.0.so.0[0xb74d755f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb74d7909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7b82314]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb670e74a]
/usr/lib/firefox/components/libtoolkitcomps.so[0xb663b6b2]
/usr/lib/firefox/firefox-bin[0x804ebaa]
/usr/lib/firefox/firefox-bin[0x804ab8f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7674050]
/usr/lib/firefox/firefox-bin[0x804aae1]
======= Memory map: ========
08048000-0805b000 r-xp 00000000 08:01 1021613    /usr/lib/firefox/firefox-bin
0805b000-0805c000 rw-p 00012000 08:01 1021613    /usr/lib/firefox/firefox-bin
0805c000-08bc8000 rw-p 0805c000 00:00 0          [heap]
b1700000-b1746000 rw-p b1700000 00:00 0 
b1746000-b1800000 ---p b1746000 00:00 0 
b1844000-b1867000 r-xp 00000000 08:01 1021214    /usr/lib/firefox/components/libsearchservice.so
b1867000-b1868000 rw-p 00022000 08:01 1021214    /usr/lib/firefox/components/libsearchservice.so
b1868000-b18ec000 r--p 00000000 08:01 1429047    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b18ec000-b18f0000 r-xp 00000000 08:01 560060     /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b18f0000-b18f2000 rw-p 00003000 08:01 560060     /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b18fd000-b18fe000 ---p b18fd000 00:00 0 
b18fe000-b20fe000 rw-p b18fe000 00:00 0 
b20fe000-b20ff000 ---p b20fe000 00:00 0 
b20ff000-b28ff000 rw-p b20ff000 00:00 0 
b28ff000-b2900000 ---p b28ff000 00:00 0 
b2900000-b3200000 rw-p b2900000 00:00 0 
b3200000-b3204000 r-xp 00000000 08:01 1081679    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b3204000-b3205000 rw-p 00003000 08:01 1081679    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b3205000-b3238000 r-xp 00000000 08:01 1019591    /usr/lib/firefox/components/libmork.so
b3238000-b323b000 rw-p 00032000 08:01 1019591    /usr/lib/firefox/components/libmork.so
b323b000-b3245000 r-xp 00000000 08:01 1019612    /usr/lib/firefox/components/libnecko2.so
b3245000-b3246000 rw-p 0000a000 08:01 1019612    /usr/lib/firefox/components/libnecko2.so
b3246000-b329d000 r-xp 00000000 08:01 1019593    /usr/lib/firefox/components/libstoragecomps.so
b329d000-b329f000 rw-p 00057000 08:01 1019593    /usr/lib/firefox/components/libstoragecomps.so
b329f000-b32ff000 rw-s 00000000 00:09 1310743    /SYSV00000000 (deleted)
b32ff000-b338b000 r--p 00000000 08:01 1428066    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b338b000-b339d000 r-xp 00000000 08:01 1019691    /usr/lib/firefox/components/libcomposer.so
b339d000-b339f000 rw-p 00011000 08:01 1019691    /usr/lib/firefox/components/libcomposer.so
b339f000-b33ae000 r-xp 00000000 08:01 1020274    /usr/lib/firefox/components/libspellchecker.so
b33ae000-b33af000 rw-p 0000f000 08:01 1020274    /usr/lib/firefox/components/libspellchecker.so
b33af000-b3448000 r-xp 00000000 08:01 1019687    /usr/lib/firefox/components/libeditor.so
b3448000-b344c000 rw-p 00099000 08:01 1019687    /usr/lib/firefox/components/libeditor.so
b344c000-b3483000 r-xp 00000000 08:01 1020306    /usr/lib/nss/libnssckbi.so
b3483000-b348c000 rw-p 00037000 08:01 1020306    /usr/lib/nss/libnssckbi.so
b348c000-b34c1000 r-xp 00000000 08:01 1020305    /usr/lib/nss/libfreebl3.so
b34c1000-b34c2000 rw-p 00035000 08:01 1020305    /usr/lib/nss/libfreebl3.so
b34c2000-b34c3000 ---p b34c2000 00:00 0 
b34c3000-b3cc3000 rw-p b34c3000 00:00 0 
b3cc3000-b3cc4000 ---p b3cc3000 00:00 0 
b3cc4000-b44c4000 rw-p b3cc4000 00:00 0 
b44c4000-b450d000 r-xp Killed
cvaty@cvaty-laptop:~$ 


```

i also just made a launchpad account, is that an appropriate place to post something like this?  

thanks

---

### Post by cvaty on 2007-09-10
according to [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/123569](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/123569) its because of my theme, someone reported that they removed their .gtk directory and everything functioned....

where is my .gtk directory?

whats the grep command i'd use in the future to find something like this?

---

