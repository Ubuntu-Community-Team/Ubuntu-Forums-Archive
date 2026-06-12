---
title: "Celtx for PPC?"
date: 2007-09-13
forum: Apple PPC Users
---

### Post by neatokino on 2007-09-13
I think I know the answer to this, but I figure I might as well try.  

Celtx, a screenwriting program, is available for i386 Linux and Mac OS, and Windows, but there is no officially compiled PPC version.

Has anyone here, by chance, compiled a version of Celtx to run on PPC?  I'd sure love to be able to use it on my old iMac G4....

TIA

Michael

---

### Post by stmiller on 2007-09-13
Hey thanks for the heads up that looks like an incredible program. Let me see if I can get it to compile on my Powerbook. Since it is mozilla based, it *should* work fine on any platform...

---

### Post by stmiller on 2007-09-14
I got the source from here: [http://www.celtx.com/download/](http://www.celtx.com/download/)

I copied the included linux default config to .mozconfig

```

cp mozconfig-nodebug-linux .mozconfig

```

and to get it to compile I had to add

ac_cv_visibility_pragma=no

to the .mozconfig. You may have to make clean then rebuild if you've already tried building it.

So now it makes after a good hour, but then it fails at the make install with this:

```
make[2]: Leaving directory `/home/stmiller/celtx-098-src/mozilla/celtx/locales'
make[2]: Entering directory `/home/stmiller/celtx-098-src/mozilla/celtx/app'
../../config/static-rules.mk:8: FINAL_LINK_COMP_NAMES = ../../config/final-link-comp-names
../../config/static-rules.mk:9: FINAL_LINK_COMPS = ../../config/final-link-comps
make[3]: Entering directory `/home/stmiller/celtx-098-src/mozilla/celtx/app/profile/extensions'
make[4]: Entering directory `/home/stmiller/celtx-098-src/mozilla/celtx/app/profile/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}'
/home/stmiller/celtx-098-src/mozilla/config/nsinstall -t -m 644 install.rdf  /usr/local/lib/celtx-0.9.8/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
make[4]: Leaving directory `/home/stmiller/celtx-098-src/mozilla/celtx/app/profile/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}'
make[3]: Leaving directory `/home/stmiller/celtx-098-src/mozilla/celtx/app/profile/extensions'
c++ -o celtx-bin  -fno-rtti -fno-exceptions -Wall -Wconversion -Wpointer-arith -Wcast-align -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wno-long-long -pedantic -fshort-wchar -pthread -pipe  -DNDEBUG -DTRIMMED -Os -freorder-blocks -fno-reorder-functions -gstabs+  nsCeltxApp.o nsStaticComponents.o      -L../../dist/bin -L../../dist/lib -L../../dist/lib/components  ../../dist/lib/libxulapp_s.a -L../../dist/bin -lmozjs -L../../dist/bin -lxpcom -lxpcom_core  -L../../dist/lib -lplds4 -lplc4 -lnspr4 -lpthread -ldl -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0     -lX11  -ldl -lm  ../../dist/lib/components/libxpcom_compat_c.a ../../dist/lib/components/libxpconnect.a ../../dist/lib/components/libuconv.a ../../dist/lib/components/libucvmath.a ../../dist/lib/components/libi18n.a ../../dist/lib/components/libmork.a ../../dist/lib/components/libstoragecomps.a ../../dist/lib/components/libnecko.a ../../dist/lib/components/libnecko2.a ../../dist/lib/components/libpref.a ../../dist/lib/components/libcaps.a ../../dist/lib/components/librdf.a ../../dist/lib/components/libhtmlpars.a ../../dist/lib/components/libgfxps.a ../../dist/lib/components/libgfx_gtk.a ../../dist/lib/components/libimglib2.a ../../dist/lib/components/libgkplugin.a ../../dist/lib/components/libwidget_gtk2.a ../../dist/lib/components/libgklayout.a ../../dist/lib/components/libdocshell.a ../../dist/lib/components/libembedcomponents.a ../../dist/lib/components/libwebbrwsr.a ../../dist/lib/components/libeditor.a ../../dist/lib/components/libtxmgr.a ../../dist/lib/components/libcomposer.a ../../dist/lib/components/libnsappshell.a ../../dist/lib/components/liboji.a ../../dist/lib/components/libaccessibility.a ../../dist/lib/components/libchrome.a ../../dist/lib/components/libmozfind.a ../../dist/lib/components/libfileview.a ../../dist/lib/components/libappcomps.a ../../dist/lib/components/libremoteservice.a ../../dist/lib/components/libcommandlines.a ../../dist/lib/components/libtoolkitcomps.a ../../dist/lib/components/libpipboot.a ../../dist/lib/components/libpipnss.a ../../dist/lib/components/libpippki.a ../../dist/lib/components/libcookie.a ../../dist/lib/components/libautoconfig.a ../../dist/lib/components/libsystem-pref.a ../../dist/lib/components/libtransformiix.a ../../dist/lib/components/libuniversalchardet.a ../../dist/lib/components/libauth.a ../../dist/lib/components/libxmlextras.a ../../dist/lib/components/libwebdav.a ../../dist/lib/components/libcalbasecomps.a ../../dist/lib/libunicharutil_s.a ../../dist/lib/libucvutil_s.a ../../dist/lib/libgtkxtbin.a ../../dist/lib/libgfxshared_s.a ../../dist/lib/libgfxpsshar.a ../../dist/lib/libgkgfx.a ../../dist/lib/libjsj.a ../../dist/lib/libxulapp_s.a  -L../../dist/lib -lmozpng -L../../dist/lib -lmozjpeg -L../../dist/lib -lmozz  -L-L../../dist/bin -L../../dist/lib -lcrmf -lsmime3 -lssl3 -lnss3 -lsoftokn3  -lmozcairo -lmozlibpixman   -lXrender -lX11  -lfontconfig -lfreetype  -lXt -lXft -lfontconfig   -L../../dist/lib -lxpcom_compat
../../dist/lib/components/libappcomps.a(nsModule.o): In function `nsAutoCompleteItemConstructor(nsISupports*, nsID const&, void**)':
/home/stmiller/celtx-098-src/mozilla/xpfe/components/build2/nsModule.cpp:64: undefined reference to `nsAutoCompleteItem::nsAutoCompleteItem()'
../../dist/lib/components/libappcomps.a(nsModule.o): In function `nsAutoCompleteResultsConstructor(nsISupports*, nsID const&, void**)':
/home/stmiller/celtx-098-src/mozilla/xpfe/components/build2/nsModule.cpp:65: undefined reference to `nsAutoCompleteResults::nsAutoCompleteResults()'
collect2: ld returned 1 exit status
make[2]: *** [celtx-bin] Error 1
make[2]: Leaving directory `/home/stmiller/celtx-098-src/mozilla/celtx/app'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/stmiller/celtx-098-src/mozilla/celtx'
make: *** [install] Error 2
stmiller@mahler:~/celtx-098-src/mozilla$  
```

 argh errors in the mozilla code. It fails making nsModule.cpp. I'd have to ask a mozilla hacker for how to get around this. :(

---

### Post by neatokino on 2007-09-17
Thanks for trying!  If you find someone to help and ever figure it out I would be eternally grateful.   I really wish I could run celtx on my PPC machine, as everything else is working pretty darn well!

---

