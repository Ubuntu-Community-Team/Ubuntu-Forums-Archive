---
title: "[SOLVED] ./configure doesn't work"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by sailor2001 on 2007-10-02
have checked all forum posts but but no help at all...... ./configure only says "no such file or directory"  Have tried all kinds of configuration, etc to no avail. Have been trying to configure for 2 years..and yes build-essential is installed.

---

### Post by CAD-MAN on 2007-10-02
I have the same problem - consider this a friendly bump :)

---

### Post by ghostcrab on 2007-10-02
what are you trying to do?

---

### Post by dwhitney67 on 2007-10-02
You have been working on this for 2 years and just now started looking for advice?  I commend you for your persistence in trying to solve a problem on your own!

"configure" is not a command that is associated with Ubuntu/Linux/Unix.  It is just a commonly used name for a shell script in many source packages.

If you want to run ./configure, you first have to change directory to where this script is located at.  For instance:

$ cd src_pkg_dir
$ ./configure

If at this point "configure" fails to run, it could mean that the script is not an executable, or that it is failing because there are certain dependencies that are missing from your system that are a prerequisite to build the software package you are configuring.

If it is not an executable, then perhaps this command would be more appropriate:

$ sh ./configure

---

### Post by master_kernel on 2007-10-02
Specifically what program are you trying to compile?

---

### Post by taurus on 2007-10-02
If you need to build something from source, you just unpack/uncompress the file that you download and THEN you change into the newly created directory.  That's where you run that command, ./configure, to compile it.

```
tar xvzf filename.tar.gz
cd filename
./configure
```

---

### Post by master_kernel on 2007-10-02
But if it says no such file or directory you must not be in the source dir.

---

### Post by ghostcrab on 2007-10-02
here is a good example logg in as root
```

root@ghostcrab:/home/ghostcrab# cd /home/ghostcrab/metadata
root@ghostcrab:/home/ghostcrab/metadata# ./confgure
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... found
checking for perl... /usr/bin/perl
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc-i18n-tool/Makefile
config.status: creating doc/Makefile
config.status: creating intltool-extract.in
config.status: creating intltool-merge.in
config.status: creating intltool-prepare
config.status: creating intltool-unicodify
config.status: creating intltool-update.in
config.status: creating intltool.spec
config.status: creating intltoolize
config.status: creating tests/Makefile
config.status: creating tests/cases/Makefile
config.status: creating tests/results/Makefile
config.status: creating tests/selftest.pl
config.status: creating xml-i18n-toolize
root@ghostcrab:/home/ghostcrab/metadata# exiv2 rm '/home/ghostcrab/Desktop/100NCD70/DSC_3041.JPG' 

```


:)

---

### Post by sailor2001 on 2007-10-02
> **taurus said:**
> If you need to build something from source, you just unpack/uncompress the file that you download and THEN you change into the newly created directory.  That's where you run that command, ./configure, to compile it.

```
tar xvzf filename.tar.gz
cd filename
./configure
```

this isn't for any particular app, but all apps in general.. ./configure just does not work. and this includes the command sh./configure
  Cairo-dock was the latest.... but I did find a deb for that. However how to configure all linux users should know..........I just cannot compile.

---

### Post by dwhitney67 on 2007-10-02
Most savvy Linux users would, before jumping into a directory and running 'configure', peruse the README or the INSTALL text files for instructions before doing anything.  Many times there are useful parameters that one can pass to the 'configure' script to customize the build and installation procedure.

Suffice to say, not all source packages are the same; not all of them come with a 'configure' script because it may not be necessary or it is not designed to use one.  Those who say otherwise are wrong.  The most fundamental package that comes with Linux is the kernel itself.  The source package for the kernel does not have a 'configure' script.  It has only a Makefile that when used appropriately, uses the settings within a configuration file.

---

### Post by jw5801 on 2007-10-02
> **sailor2001 said:**
> this isn't for any particular app, but all apps in general.. ./configure just does not work. and this includes the command sh./configure
  Cairo-dock was the latest.... but I did find a deb for that. However how to configure all linux users should know..........I just cannot compile.

Could we perhaps have an example of the terminal input you tried and what output it gave you? Lets focus on one app and show you what to do there.

---

### Post by sailor2001 on 2007-10-02
ok. I have cairo-dock on the desktop right now ......this is for drill as I got the deb for it....... so I have /home/sailor/Desktop/cairo-1.2.6.tar.gz and also have it extracted on the desktop . so : tar xvzf cairo-1.2.6.tar.gz  .....   cd Desktop ( tried that also)       ./configure   "no such file or directory"

---

### Post by jw5801 on 2007-10-02
Please post exactly what you see in the terminal when you try this, including what you typed in. Also after you change directories, use ```
ls
```to see if there actually is a configure script in the folder you're in. And if that's the command you ran, then you didn't actually extract anything in the first place. Try, ```
cd ~/Desktop
tar -xzvf cairo-1.2.6.tar.gz
cd *whatever-folder-is-extracted* #you should be able to see this as everything is extracted since you've used the verbose switch.
ls
```
And copy and paste exactly what you see.

---

### Post by Celegorm on 2007-10-02
Try ```
cd /home/sailor/Desktop/cairo-1.2.6/
``` And then run ./configure, assuming extracting the tar.gz file gives you a directory called cairo-1.2.6. If that doesn't work, post the output of 'ls' in the directory in which you are running ./configure.

---

### Post by sailor2001 on 2007-10-02
don't know what happened. but something worked this time..........cairo-1.2.6/pixman/src/
cairo-1.2.6/pixman/src/pixman.h
cairo-1.2.6/pixman/src/fbedge.c
cairo-1.2.6/pixman/src/icrop.h
cairo-1.2.6/pixman/src/pixman-remap.h
cairo-1.2.6/pixman/src/pixman-xserver-compat.h
cairo-1.2.6/pixman/src/ictransform.c
cairo-1.2.6/pixman/src/renderedge.c
cairo-1.2.6/pixman/src/icpixels.c
cairo-1.2.6/pixman/src/icutil.c
cairo-1.2.6/pixman/src/fbpict.h
cairo-1.2.6/pixman/src/slim_internal.h
cairo-1.2.6/pixman/src/pixregionint.h
cairo-1.2.6/pixman/src/fbedgeimp.h
cairo-1.2.6/pixman/src/fbmmx.c
cairo-1.2.6/pixman/src/icbltone.c
cairo-1.2.6/pixman/src/icblt.c
cairo-1.2.6/pixman/src/icimage.h
cairo-1.2.6/pixman/src/ictrap.c
cairo-1.2.6/pixman/src/pixregion.c
cairo-1.2.6/pixman/src/icrect.c
cairo-1.2.6/pixman/src/fbpict.c
cairo-1.2.6/pixman/src/Makefile.in
cairo-1.2.6/pixman/src/Makefile.am
cairo-1.2.6/pixman/src/iccolor.c
cairo-1.2.6/pixman/src/icint.h
cairo-1.2.6/pixman/src/ictri.c
cairo-1.2.6/pixman/src/renderedge.h
cairo-1.2.6/pixman/src/icstipple.c
cairo-1.2.6/pixman/src/icimage.c
cairo-1.2.6/pixman/src/fbmmx.h
cairo-1.2.6/pixman/src/fbtrap.c
cairo-1.2.6/pixman/src/fbcompose.c
cairo-1.2.6/pixman/src/icformat.c
cairo-1.2.6/pixman/ChangeLog
cairo-1.2.6/pixman/NEWS
cairo-1.2.6/pixman/INSTALL
cairo-1.2.6/pixman/README
cairo-1.2.6/pixman/ChangeLog.libpixregion
cairo-1.2.6/pixman/TODO
cairo-1.2.6/pixman/AUTHORS
cairo-1.2.6/pixman/Makefile.in
cairo-1.2.6/pixman/Makefile.am
cairo-1.2.6/pixman/ChangeLog.slim
cairo-1.2.6/config.h.in
cairo-1.2.6/COPYING-LGPL-2.1
cairo-1.2.6/ChangeLog
cairo-1.2.6/compile
cairo-1.2.6/CODING_STYLE
cairo-1.2.6/doc/
cairo-1.2.6/doc/public/
cairo-1.2.6/doc/public/tmpl/
cairo-1.2.6/doc/public/tmpl/cairo-surface.sgml
cairo-1.2.6/doc/public/tmpl/cairo-image.sgml
cairo-1.2.6/doc/public/tmpl/cairo-version.sgml
cairo-1.2.6/doc/public/tmpl/cairo-text.sgml
cairo-1.2.6/doc/public/tmpl/cairo.sgml
cairo-1.2.6/doc/public/tmpl/cairo-unused.sgml
cairo-1.2.6/doc/public/tmpl/cairo-svg.sgml
cairo-1.2.6/doc/public/tmpl/cairo-png.sgml
cairo-1.2.6/doc/public/tmpl/cairo-paths.sgml
cairo-1.2.6/doc/public/tmpl/cairo-glitz.sgml
cairo-1.2.6/doc/public/tmpl/cairo-beos.sgml
cairo-1.2.6/doc/public/tmpl/cairo-pdf.sgml
cairo-1.2.6/doc/public/tmpl/cairo-ft.sgml
cairo-1.2.6/doc/public/tmpl/cairo-atsui.sgml
cairo-1.2.6/doc/public/tmpl/cairo-quartz.sgml
cairo-1.2.6/doc/public/tmpl/cairo-ps.sgml
cairo-1.2.6/doc/public/tmpl/cairo-font-options.sgml
cairo-1.2.6/doc/public/tmpl/cairo-transforms.sgml
cairo-1.2.6/doc/public/tmpl/cairo-xcb.sgml
cairo-1.2.6/doc/public/tmpl/cairo-xlib.sgml
cairo-1.2.6/doc/public/tmpl/cairo-xcb-xrender.sgml
cairo-1.2.6/doc/public/tmpl/cairo-status.sgml
cairo-1.2.6/doc/public/tmpl/cairo-pattern.sgml
cairo-1.2.6/doc/public/tmpl/cairo-win32.sgml
cairo-1.2.6/doc/public/tmpl/cairo-font.sgml
cairo-1.2.6/doc/public/tmpl/cairo-xlib-xrender.sgml
cairo-1.2.6/doc/public/tmpl/cairo-scaled-font.sgml
cairo-1.2.6/doc/public/tmpl/cairo-win32-fonts.sgml
cairo-1.2.6/doc/public/tmpl/cairo-matrix.sgml
cairo-1.2.6/doc/public/tmpl/cairo-types.sgml
cairo-1.2.6/doc/public/cairo-docs.xml
cairo-1.2.6/doc/public/cairo-overrides.txt
cairo-1.2.6/doc/public/language-bindings.xml
cairo-1.2.6/doc/public/cairo-sections.txt
cairo-1.2.6/doc/public/version.xml.in
cairo-1.2.6/doc/public/Makefile.in
cairo-1.2.6/doc/public/Makefile.am
cairo-1.2.6/doc/public/version.xml
cairo-1.2.6/doc/public/html/
cairo-1.2.6/doc/public/html/pt01.html
cairo-1.2.6/doc/public/html/cairo-cairo-t.html
cairo-1.2.6/doc/public/html/bindings-fonts.html
cairo-1.2.6/doc/public/html/cairo.devhelp2
cairo-1.2.6/doc/public/html/cairo-cairo-font-face-t.html
cairo-1.2.6/doc/public/html/ix02.html
cairo-1.2.6/doc/public/html/cairo-XLib-Surfaces.html
cairo-1.2.6/doc/public/html/cairo-Error-handling.html
cairo-1.2.6/doc/public/html/cairo-Transformations.html
cairo-1.2.6/doc/public/html/cairo-Version-Information.html
cairo-1.2.6/doc/public/html/cairo-Scaled-Fonts.html
cairo-1.2.6/doc/public/html/Fonts.html
cairo-1.2.6/doc/public/html/language-bindings.html
cairo-1.2.6/doc/public/html/cairo-Win32-Fonts.html
cairo-1.2.6/doc/public/html/ix01.html
cairo-1.2.6/doc/public/html/cairo-Font-Options.html
cairo-1.2.6/doc/public/html/Drawing.html
cairo-1.2.6/doc/public/html/cairo-SVG-Surfaces.html
cairo-1.2.6/doc/public/html/bindings-memory.html
cairo-1.2.6/doc/public/html/cairo-PNG-Support.html
cairo-1.2.6/doc/public/html/cairo-Paths.html
cairo-1.2.6/doc/public/html/bindings-errors.html
cairo-1.2.6/doc/public/html/Surfaces.html
cairo-1.2.6/doc/public/html/bindings-surfaces.html
cairo-1.2.6/doc/public/html/bindings-return-values.html
cairo-1.2.6/doc/public/html/cairo-Image-Surfaces.html
cairo-1.2.6/doc/public/html/pt02.html
cairo-1.2.6/doc/public/html/cairo-PostScript-Surfaces.html
cairo-1.2.6/doc/public/html/cairo-FreeType-Fonts.html
cairo-1.2.6/doc/public/html/index.sgml
cairo-1.2.6/doc/public/html/left.png
cairo-1.2.6/doc/public/html/style.css
cairo-1.2.6/doc/public/html/cairo-Patterns.html
cairo-1.2.6/doc/public/html/bindings-path.html
cairo-1.2.6/doc/public/html/up.png
cairo-1.2.6/doc/public/html/right.png
cairo-1.2.6/doc/public/html/cairo-cairo-surface-t.html
cairo-1.2.6/doc/public/html/home.png
cairo-1.2.6/doc/public/html/Support.html
cairo-1.2.6/doc/public/html/bindings-streams.html
cairo-1.2.6/doc/public/html/cairo-Win32-Surfaces.html
cairo-1.2.6/doc/public/html/cairo.devhelp
cairo-1.2.6/doc/public/html/bindings-patterns.html
cairo-1.2.6/doc/public/html/cairo-cairo-matrix-t.html
cairo-1.2.6/doc/public/html/cairo-Types.html
cairo-1.2.6/doc/public/html/index.html
cairo-1.2.6/doc/public/html/bindings-overloading.html
cairo-1.2.6/doc/public/html/cairo-Text.html
cairo-1.2.6/doc/public/html/cairo-PDF-Surfaces.html
cairo-1.2.6/doc/public/xml/
cairo-1.2.6/doc/public/xml/cairo-text.xml
cairo-1.2.6/doc/public/xml/cairo-version.xml
cairo-1.2.6/doc/public/xml/cairo-glitz.xml
cairo-1.2.6/doc/public/xml/cairo-xcb.xml
cairo-1.2.6/doc/public/xml/cairo-beos.xml
cairo-1.2.6/doc/public/xml/cairo-surface.xml
cairo-1.2.6/doc/public/xml/cairo-pdf.xml
cairo-1.2.6/doc/public/xml/cairo-font-options.xml
cairo-1.2.6/doc/public/xml/cairo-ft.xml
cairo-1.2.6/doc/public/xml/cairo-svg.xml
cairo-1.2.6/doc/public/xml/cairo-transforms.xml
cairo-1.2.6/doc/public/xml/cairo-win32.xml
cairo-1.2.6/doc/public/xml/cairo-types.xml
cairo-1.2.6/doc/public/xml/cairo-paths.xml
cairo-1.2.6/doc/public/xml/cairo-ps.xml
cairo-1.2.6/doc/public/xml/cairo-xlib-xrender.xml
cairo-1.2.6/doc/public/xml/cairo-xlib.xml
cairo-1.2.6/doc/public/xml/cairo-image.xml
cairo-1.2.6/doc/public/xml/cairo-win32-fonts.xml
cairo-1.2.6/doc/public/xml/cairo-matrix.xml
cairo-1.2.6/doc/public/xml/cairo-status.xml
cairo-1.2.6/doc/public/xml/cairo-xcb-xrender.xml
cairo-1.2.6/doc/public/xml/cairo-scaled-font.xml
cairo-1.2.6/doc/public/xml/cairo-pattern.xml
cairo-1.2.6/doc/public/xml/cairo-png.xml
cairo-1.2.6/doc/public/xml/cairo-font.xml
cairo-1.2.6/doc/public/xml/cairo-quartz.xml
cairo-1.2.6/doc/public/xml/cairo.xml
cairo-1.2.6/doc/public/cairo.types
cairo-1.2.6/doc/Makefile.in
cairo-1.2.6/doc/Makefile.am
cairo-1.2.6/NEWS
cairo-1.2.6/configure
cairo-1.2.6/test/
cairo-1.2.6/test/ft-text-antialias-none-ps-argb32-ref.png
cairo-1.2.6/test/get-group-target.c
cairo-1.2.6/test/dash-zero-length-ps-argb32-ref.png
cairo-1.2.6/test/ft-text-vertical-layout-type3-svg-ref.png
cairo-1.2.6/test/push-group-rgb24-ref.png
cairo-1.2.6/test/dash-caps-joins.c
cairo-1.2.6/test/line-width-scale.c
cairo-1.2.6/test/caps-joins.c
cairo-1.2.6/test/caps-joins-alpha-svg-ref.png
cairo-1.2.6/test/clip-fill-rule-pixel-aligned.c
cairo-1.2.6/test/operator-source-rgb24-ref.png
cairo-1.2.6/test/caps-sub-paths-ref.png
cairo-1.2.6/test/nil-surface-ref.png
cairo-1.2.6/test/move-to-show-surface-ref.png
cairo-1.2.6/test/clip-nesting-ps-argb32-ref.png
cairo-1.2.6/test/select-font-face.c
cairo-1.2.6/test/source-surface-scale-paint.c
cairo-1.2.6/test/dash-caps-joins-ref.png
cairo-1.2.6/test/cairo-test.h
cairo-1.2.6/test/rectangle-rounding-error-ref.png
cairo-1.2.6/test/scale-source-surface-paint-rgb24-ref.png
cairo-1.2.6/test/self-intersecting-rgb24-ref.png
cairo-1.2.6/test/mask-beos-bitmap-rgb24-ref.png
cairo-1.2.6/test/line-width-scale-ps-argb32-ref.png
cairo-1.2.6/test/text-rotate.c
cairo-1.2.6/test/nil-surface.c
cairo-1.2.6/test/line-width-scale-ref.png
cairo-1.2.6/test/composite-integer-translate-source-ref.png
cairo-1.2.6/test/mask-ctm-svg-argb32-ref.png
cairo-1.2.6/test/self-copy-ref.png
cairo-1.2.6/test/select-font-face-ref.png
cairo-1.2.6/test/fill-rule-ps-argb32-ref.png
cairo-1.2.6/test/ft-text-vertical-layout-type1-ref.png
cairo-1.2.6/test/operator-clear-ref.png
cairo-1.2.6/test/device-offset-positive-ref.png
cairo-1.2.6/test/font-matrix-translation-ps-argb32-ref.png
cairo-1.2.6/test/linear-gradient-svg-ref.png
cairo-1.2.6/test/caps-sub-paths.c
cairo-1.2.6/test/mask-rgb24-ref.png
cairo-1.2.6/test/paint.c
cairo-1.2.6/test/dash-scale.c
cairo-1.2.6/test/clip-twice-ps-argb32-ref.png
cairo-1.2.6/test/clip-nesting.c
cairo-1.2.6/test/a8-mask.c
cairo-1.2.6/test/scale-source-surface-paint-ref.png
cairo-1.2.6/test/unbounded-operator-ref.png
cairo-1.2.6/test/clip-twice-rgb24-ref.png
cairo-1.2.6/test/composite-integer-translate-over-svg-ref.png
cairo-1.2.6/test/composite-integer-translate-over.c
cairo-1.2.6/test/create-from-png-ref.png
cairo-1.2.6/test/show-text-current-point-svg-ref.png
cairo-1.2.6/test/source-clip.c
cairo-1.2.6/test/text-rotate-ref.png
cairo-1.2.6/test/pdf2png.c
cairo-1.2.6/test/fill-and-stroke-alpha.c
cairo-1.2.6/test/pixman-rotate-ref.png
cairo-1.2.6/test/leaky-polygon.c
cairo-1.2.6/test/push-group-svg-rgb24-ref.png
cairo-1.2.6/test/infinite-join-ps-argb32-ref.png
cairo-1.2.6/test/device-offset-rgb24-ref.png
cairo-1.2.6/test/composite-integer-translate-over-ref.png
cairo-1.2.6/test/leaky-dash.c
cairo-1.2.6/test/new-sub-path-rgb24-ref.png
cairo-1.2.6/test/unbounded-operator.c
cairo-1.2.6/test/create-from-png.c
cairo-1.2.6/test/mask-beos-rgb24-ref.png
cairo-1.2.6/test/linear-gradient.c
cairo-1.2.6/test/push-group-ref.png
cairo-1.2.6/test/degenerate-path-ref.png
cairo-1.2.6/test/dash-zero-length-rgb24-ref.png
cairo-1.2.6/test/infinite-join-ref.png
cairo-1.2.6/test/long-lines.c
cairo-1.2.6/test/clip-twice.c
cairo-1.2.6/test/text-antialias-subpixel-ref.png
cairo-1.2.6/test/mask-ctm-svg-rgb24-ref.png
cairo-1.2.6/test/trap-clip-rgb24-ref.png
cairo-1.2.6/test/push-group.c
cairo-1.2.6/test/composite-integer-translate-over-repeat-ref.png
cairo-1.2.6/test/copy-path-ps-argb32-ref.png
cairo-1.2.6/test/transforms-ps-argb32-ref.png
cairo-1.2.6/test/ft-text-vertical-layout-type3.c
cairo-1.2.6/test/source-clip-ref.png
cairo-1.2.6/test/mask-surface-ctm-rgb24-ref.png
cairo-1.2.6/test/text-pattern-svg-argb32-ref.png
cairo-1.2.6/test/text-antialias-subpixel.c
cairo-1.2.6/test/extend-reflect.c
cairo-1.2.6/test/caps-joins-ref.png
cairo-1.2.6/test/user-data.c
cairo-1.2.6/test/set-source-svg-rgb24-ref.png
cairo-1.2.6/test/paint-source-alpha-pdf-argb32-ref.png
cairo-1.2.6/test/rectangle-rounding-error.c
cairo-1.2.6/test/caps-joins-alpha.c
cairo-1.2.6/test/linear-gradient-ref.png
cairo-1.2.6/test/gradient-alpha-ref.png
cairo-1.2.6/test/degenerate-path.c
cairo-1.2.6/test/multi-page.c
cairo-1.2.6/test/ft-text-vertical-layout-type1.c
cairo-1.2.6/test/line-width-ps-argb32-ref.png
cairo-1.2.6/test/set-source-beos-rgb24-ref.png
cairo-1.2.6/test/fill-and-stroke-alpha-ref.png
cairo-1.2.6/test/make-html.pl
cairo-1.2.6/test/mask.c
cairo-1.2.6/test/clip-fill-rule-rgb24-ref.png
cairo-1.2.6/test/pixman-rotate-rgb24-ref.png
cairo-1.2.6/test/leaky-polygon-ps-argb32-ref.png
cairo-1.2.6/test/paint-source-alpha-svg-ref.png
cairo-1.2.6/test/select-font-face-svg-ref.png
cairo-1.2.6/test/set-source-beos-bitmap-rgb24-ref.png
cairo-1.2.6/test/move-to-show-surface.c
cairo-1.2.6/test/device-offset.c
cairo-1.2.6/test/imagediff.c
cairo-1.2.6/test/create-from-png-stream.c
cairo-1.2.6/test/translate-show-surface-ref.png
cairo-1.2.6/test/mask-surface-ctm-svg-argb32-ref.png
cairo-1.2.6/test/create-from-png-stream-ref.png
cairo-1.2.6/test/text-antialias-none.c
cairo-1.2.6/test/cairo-test.c
cairo-1.2.6/test/pattern-get-type.c
cairo-1.2.6/test/font-matrix-translation-ref.png
cairo-1.2.6/test/show-text-current-point-ref.png
cairo-1.2.6/test/source-surface-scale-paint-ref.png
cairo-1.2.6/test/clip-fill-rule-ref.png
cairo-1.2.6/test/glyph-cache-pressure-ps-argb32-ref.png
cairo-1.2.6/test/set-source-ref.png
cairo-1.2.6/test/bitmap-font-ref.png
cairo-1.2.6/test/dash-scale-ref.png
cairo-1.2.6/test/caps-sub-paths-ps-argb32-ref.png
cairo-1.2.6/test/dash-scale-ps-argb32-ref.png
cairo-1.2.6/test/README
cairo-1.2.6/test/6x13.pcf
cairo-1.2.6/test/self-copy.c
cairo-1.2.6/test/ft-text-antialias-none.c
cairo-1.2.6/test/xlib-surface.c
cairo-1.2.6/test/trap-clip-svg-rgb24-ref.png
cairo-1.2.6/test/ps-features.c
cairo-1.2.6/test/operator-source-ref.png
cairo-1.2.6/test/scale-source-surface-paint-svg-argb32-ref.png
cairo-1.2.6/test/dash-zero-length.c
cairo-1.2.6/test/unbounded-operator-rgb24-ref.png
cairo-1.2.6/test/dash-no-dash-ref.png
cairo-1.2.6/test/ft-text-vertical-layout-type1-svg-ref.png
cairo-1.2.6/test/glyph-cache-pressure-svg-ref.png
cairo-1.2.6/test/pixman-rotate.c
cairo-1.2.6/test/dash-no-dash.c
cairo-1.2.6/test/source-surface-scale-paint-rgb24-ref.png
cairo-1.2.6/test/paint-with-alpha-ref.png
cairo-1.2.6/test/fill-and-stroke-ps-argb32-ref.png
cairo-1.2.6/test/font-matrix-translation-svg-ref.png
cairo-1.2.6/test/degenerate-path-ps-argb32-ref.png
cairo-1.2.6/test/fallback-resolution.c
cairo-1.2.6/test/clip-fill-rule-ps-argb32-ref.png
cairo-1.2.6/test/dash-zero-length-ref.png
cairo-1.2.6/test/surface-pattern.c
cairo-1.2.6/test/fill-and-stroke-ref.png
cairo-1.2.6/test/device-offset-ref.png
cairo-1.2.6/test/clip-twice-ref.png
cairo-1.2.6/test/source-clip-scale-svg-ref.png
cairo-1.2.6/test/xmalloc.c
cairo-1.2.6/test/mask-ctm-ref.png
cairo-1.2.6/test/close-path.c
cairo-1.2.6/test/composite-integer-translate-source.c
cairo-1.2.6/test/device-offset-positive.c
cairo-1.2.6/test/trap-clip.c
cairo-1.2.6/test/scale-source-surface-paint-svg-rgb24-ref.png
cairo-1.2.6/test/nil-surface-rgb24-ref.png
cairo-1.2.6/test/text-pattern-ref.png
cairo-1.2.6/test/text-pattern.c
cairo-1.2.6/test/mask-svg-rgb24-ref.png
cairo-1.2.6/test/fill-and-stroke-alpha-svg-ref.png
cairo-1.2.6/test/bitmap-font-rgb24-ref.png
cairo-1.2.6/test/glyph-cache-pressure.c
cairo-1.2.6/test/ft-text-antialias-none-ref.png
cairo-1.2.6/test/text-pattern-svg-rgb24-ref.png
cairo-1.2.6/test/ft-text-vertical-layout-type3-ref.png
cairo-1.2.6/test/trap-clip-ref.png
cairo-1.2.6/test/transforms-ref.png
cairo-1.2.6/test/mask-surface-ctm.c
cairo-1.2.6/test/show-text-current-point.c
cairo-1.2.6/test/unantialiased-shapes.c
cairo-1.2.6/test/cairo-test-directfb.h
cairo-1.2.6/test/rel-path-ref.png
cairo-1.2.6/test/line-width-ref.png
cairo-1.2.6/test/pdf-features.c
cairo-1.2.6/test/buffer-diff.c
cairo-1.2.6/test/leaky-polygon-ref.png
cairo-1.2.6/test/cairo-test-directfb.c
cairo-1.2.6/test/composite-integer-translate-over-repeat.c
cairo-1.2.6/test/operator-clear.c
cairo-1.2.6/test/close-path-ref.png
cairo-1.2.6/test/filter-nearest-offset.c
cairo-1.2.6/test/filter-nearest-offset-ref.png
cairo-1.2.6/test/fill-rule-ref.png
cairo-1.2.6/test/dash-caps-joins-ps-argb32-ref.png
cairo-1.2.6/test/copy-path-ref.png
cairo-1.2.6/test/mask-beos-bitmap-argb32-ref.png
cairo-1.2.6/test/composite-integer-translate-over-pdf-argb32-ref.png
cairo-1.2.6/test/set-source-rgb24-ref.png
cairo-1.2.6/test/text-rotate-rgb24-ref.png
cairo-1.2.6/test/clip-nesting-rgb24-ref.png
cairo-1.2.6/test/fill-rule-rgb24-ref.png
cairo-1.2.6/test/zero-alpha-ref.png
cairo-1.2.6/test/new-sub-path.c
cairo-1.2.6/test/get-group-target-ref.png
cairo-1.2.6/test/degenerate-path-rgb24-ref.png
cairo-1.2.6/test/operator-source.c
cairo-1.2.6/test/Makefile.in
cairo-1.2.6/test/text-antialias-gray-ref.png
cairo-1.2.6/test/clip-operator.c
cairo-1.2.6/test/ft-font-create-for-ft-face.c
cairo-1.2.6/test/get-and-set.c
cairo-1.2.6/test/rel-path-rgb24-ref.png
cairo-1.2.6/test/mask-ctm.c
cairo-1.2.6/test/paint-source-alpha-ref.png
cairo-1.2.6/test/romedalen.png
cairo-1.2.6/test/select-font-face-ps-argb32-ref.png
cairo-1.2.6/test/self-intersecting.c
cairo-1.2.6/test/svg-surface.c
cairo-1.2.6/test/cairo-test-beos.cpp
cairo-1.2.6/test/mask-surface-ctm-ref.png
cairo-1.2.6/test/push-group-svg-argb32-ref.png
cairo-1.2.6/test/select-font-no-show-text.c
cairo-1.2.6/test/Makefile.am
cairo-1.2.6/test/operator-clear-rgb24-ref.png
cairo-1.2.6/test/xmalloc.h
cairo-1.2.6/test/trap-clip-beos-rgb24-ref.png
cairo-1.2.6/test/fill-rule.c
cairo-1.2.6/test/dash-offset-negative-ref.png
cairo-1.2.6/test/truetype-tables.c
cairo-1.2.6/test/svg2png.c
cairo-1.2.6/test/set-source.c
cairo-1.2.6/test/clip-nesting-ref.png
cairo-1.2.6/test/text-antialias-gray.c
cairo-1.2.6/test/svg-clip.c
cairo-1.2.6/test/paint-with-alpha.c
cairo-1.2.6/test/png-flatten.c
cairo-1.2.6/test/fill-and-stroke-alpha-add-ref.png
cairo-1.2.6/test/glyph-cache-pressure-ref.png
cairo-1.2.6/test/surface-finish-twice.c
cairo-1.2.6/test/scale-source-surface-paint.c
cairo-1.2.6/test/clip-operator-rgb24-ref.png
cairo-1.2.6/test/device-offset-positive-rgb24-ref.png
cairo-1.2.6/test/copy-path.c
cairo-1.2.6/test/bitmap-font.c
cairo-1.2.6/test/source-clip-scale.c
cairo-1.2.6/test/clip-all-ref.png
cairo-1.2.6/test/source-clip-scale-ref.png
cairo-1.2.6/test/show-glyphs-many-ref.png
cairo-1.2.6/test/clip-fill-rule-pixel-aligned-ref.png
cairo-1.2.6/test/gradient-alpha-rgb24-ref.png
cairo-1.2.6/test/fill-and-stroke-alpha-add.c
cairo-1.2.6/test/pthread-show-text.c
cairo-1.2.6/test/line-width.c
cairo-1.2.6/test/close-path-ps-argb32-ref.png
cairo-1.2.6/test/new-sub-path-ref.png
cairo-1.2.6/test/font-face-get-type.c
cairo-1.2.6/test/dash-offset-negative-ps-argb32-ref.png
cairo-1.2.6/test/trap-clip-beos-bitmap-rgb24-ref.png
cairo-1.2.6/test/text-cache-crash.c
cairo-1.2.6/test/bitmap-font-pdf-argb32-ref.png
cairo-1.2.6/test/mask-ref.png
cairo-1.2.6/test/caps-joins-ps-argb32-ref.png
cairo-1.2.6/test/trap-clip-svg-argb32-ref.png
cairo-1.2.6/test/transforms.c
cairo-1.2.6/test/paint-source-alpha.c
cairo-1.2.6/test/infinite-join.c
cairo-1.2.6/test/fill-and-stroke-rgb24-ref.png
cairo-1.2.6/test/gradient-alpha.c
cairo-1.2.6/test/clip-fill-rule-pixel-aligned-rgb24-ref.png
cairo-1.2.6/test/mask-ctm-rgb24-ref.png
cairo-1.2.6/test/show-text-current-point-ps-argb32-ref.png
cairo-1.2.6/test/caps-joins-alpha-ref.png
cairo-1.2.6/test/clip-operator-ref.png
cairo-1.2.6/test/zero-alpha.c
cairo-1.2.6/test/text-pattern-rgb24-ref.png
cairo-1.2.6/test/surface-pattern-ref.png
cairo-1.2.6/test/text-antialias-none-ref.png
cairo-1.2.6/test/set-source-svg-argb32-ref.png
cairo-1.2.6/test/rel-path.c
cairo-1.2.6/test/mask-surface-ctm-svg-rgb24-ref.png
cairo-1.2.6/test/long-lines-ref.png
cairo-1.2.6/test/create-for-stream.c
cairo-1.2.6/test/dash-offset-negative.c
cairo-1.2.6/test/scale-source-surface-paint-pdf-argb32-ref.png
cairo-1.2.6/test/translate-show-surface.c
cairo-1.2.6/test/clip-fill-rule.c
cairo-1.2.6/test/a8-mask-ref.png
cairo-1.2.6/test/cairo-test-beos.h
cairo-1.2.6/test/buffer-diff.h
cairo-1.2.6/test/unantialiased-shapes-ref.png
cairo-1.2.6/test/font-matrix-translation.c
cairo-1.2.6/test/paint-with-alpha-svg-ref.png
cairo-1.2.6/test/leaky-dash-ref.png
cairo-1.2.6/test/mask-svg-argb32-ref.png
cairo-1.2.6/test/fill-and-stroke.c
cairo-1.2.6/test/new-sub-path-ps-argb32-ref.png
cairo-1.2.6/test/self-intersecting-ref.png
cairo-1.2.6/test/clip-all.c
cairo-1.2.6/test/paint-ref.png
cairo-1.2.6/PORTING_GUIDE
cairo-1.2.6/INSTALL
cairo-1.2.6/README
cairo-1.2.6/COPYING-MPL-1.1
cairo-1.2.6/BUGS
cairo-1.2.6/TODO
cairo-1.2.6/ROADMAP
cairo-1.2.6/RELEASING
cairo-1.2.6/AUTHORS
cairo-1.2.6/ChangeLog.mk
cairo-1.2.6/missing
cairo-1.2.6/depcomp
cairo-1.2.6/Makefile.in
cairo-1.2.6/configure.in
cairo-1.2.6/Makefile.am
cairo-1.2.6/ChangeLog.pre-1.0
cairo-1.2.6/gtk-doc.make
cairo-1.2.6/config.sub
cairo-1.2.6/install-sh
cairo-1.2.6/acinclude.m4


what changed, I don't know.....ls= cairo-1.2.6/pixman/src/
cairo-1.2.6/pixman/src/pixman.h
cairo-1.2.6/pixman/src/fbedge.c
cairo-1.2.6/pixman/src/icrop.h
cairo-1.2.6/pixman/src/pixman-remap.h
cairo-1.2.6/pixman/src/pixman-xserver-compat.h
cairo-1.2.6/pixman/src/ictransform.c
cairo-1.2.6/pixman/src/renderedge.c
cairo-1.2.6/pixman/src/icpixels.c
cairo-1.2.6/pixman/src/icutil.c
cairo-1.2.6/pixman/src/fbpict.h
cairo-1.2.6/pixman/src/slim_internal.h
cairo-1.2.6/pixman/src/pixregionint.h
cairo-1.2.6/pixman/src/fbedgeimp.h
cairo-1.2.6/pixman/src/fbmmx.c
cairo-1.2.6/pixman/src/icbltone.c
cairo-1.2.6/pixman/src/icblt.c
cairo-1.2.6/pixman/src/icimage.h
cairo-1.2.6/pixman/src/ictrap.c
cairo-1.2.6/pixman/src/pixregion.c
cairo-1.2.6/pixman/src/icrect.c
cairo-1.2.6/pixman/src/fbpict.c
cairo-1.2.6/pixman/src/Makefile.in
cairo-1.2.6/pixman/src/Makefile.am
cairo-1.2.6/pixman/src/iccolor.c
cairo-1.2.6/pixman/src/icint.h
cairo-1.2.6/pixman/src/ictri.c
cairo-1.2.6/pixman/src/renderedge.h
cairo-1.2.6/pixman/src/icstipple.c
cairo-1.2.6/pixman/src/icimage.c
cairo-1.2.6/pixman/src/fbmmx.h
cairo-1.2.6/pixman/src/fbtrap.c
cairo-1.2.6/pixman/src/fbcompose.c
cairo-1.2.6/pixman/src/icformat.c
cairo-1.2.6/pixman/ChangeLog
cairo-1.2.6/pixman/NEWS
cairo-1.2.6/pixman/INSTALL
cairo-1.2.6/pixman/README
cairo-1.2.6/pixman/ChangeLog.libpixregion
cairo-1.2.6/pixman/TODO
cairo-1.2.6/pixman/AUTHORS
cairo-1.2.6/pixman/Makefile.in
cairo-1.2.6/pixman/Makefile.am
cairo-1.2.6/pixman/ChangeLog.slim
cairo-1.2.6/config.h.in
cairo-1.2.6/COPYING-LGPL-2.1
cairo-1.2.6/ChangeLog
cairo-1.2.6/compile
cairo-1.2.6/CODING_STYLE
cairo-1.2.6/doc/
cairo-1.2.6/doc/public/
cairo-1.2.6/doc/public/tmpl/
cairo-1.2.6/doc/public/tmpl/cairo-surface.sgml
cairo-1.2.6/doc/public/tmpl/cairo-image.sgml
cairo-1.2.6/doc/public/tmpl/cairo-version.sgml
cairo-1.2.6/doc/public/tmpl/cairo-text.sgml
cairo-1.2.6/doc/public/tmpl/cairo.sgml
cairo-1.2.6/doc/public/tmpl/cairo-unused.sgml
cairo-1.2.6/doc/public/tmpl/cairo-svg.sgml
cairo-1.2.6/doc/public/tmpl/cairo-png.sgml
cairo-1.2.6/doc/public/tmpl/cairo-paths.sgml
cairo-1.2.6/doc/public/tmpl/cairo-glitz.sgml
cairo-1.2.6/doc/public/tmpl/cairo-beos.sgml
cairo-1.2.6/doc/public/tmpl/cairo-pdf.sgml
cairo-1.2.6/doc/public/tmpl/cairo-ft.sgml
cairo-1.2.6/doc/public/tmpl/cairo-atsui.sgml
cairo-1.2.6/doc/public/tmpl/cairo-quartz.sgml
cairo-1.2.6/doc/public/tmpl/cairo-ps.sgml
cairo-1.2.6/doc/public/tmpl/cairo-font-options.sgml
cairo-1.2.6/doc/public/tmpl/cairo-transforms.sgml
cairo-1.2.6/doc/public/tmpl/cairo-xcb.sgml
cairo-1.2.6/doc/public/tmpl/cairo-xlib.sgml
cairo-1.2.6/doc/public/tmpl/cairo-xcb-xrender.sgml
cairo-1.2.6/doc/public/tmpl/cairo-status.sgml
cairo-1.2.6/doc/public/tmpl/cairo-pattern.sgml
cairo-1.2.6/doc/public/tmpl/cairo-win32.sgml
cairo-1.2.6/doc/public/tmpl/cairo-font.sgml
cairo-1.2.6/doc/public/tmpl/cairo-xlib-xrender.sgml
cairo-1.2.6/doc/public/tmpl/cairo-scaled-font.sgml
cairo-1.2.6/doc/public/tmpl/cairo-win32-fonts.sgml
cairo-1.2.6/doc/public/tmpl/cairo-matrix.sgml
cairo-1.2.6/doc/public/tmpl/cairo-types.sgml
cairo-1.2.6/doc/public/cairo-docs.xml
cairo-1.2.6/doc/public/cairo-overrides.txt
cairo-1.2.6/doc/public/language-bindings.xml
cairo-1.2.6/doc/public/cairo-sections.txt
cairo-1.2.6/doc/public/version.xml.in
cairo-1.2.6/doc/public/Makefile.in
cairo-1.2.6/doc/public/Makefile.am
cairo-1.2.6/doc/public/version.xml
cairo-1.2.6/doc/public/html/
cairo-1.2.6/doc/public/html/pt01.html
cairo-1.2.6/doc/public/html/cairo-cairo-t.html
cairo-1.2.6/doc/public/html/bindings-fonts.html
cairo-1.2.6/doc/public/html/cairo.devhelp2
cairo-1.2.6/doc/public/html/cairo-cairo-font-face-t.html
cairo-1.2.6/doc/public/html/ix02.html
cairo-1.2.6/doc/public/html/cairo-XLib-Surfaces.html
cairo-1.2.6/doc/public/html/cairo-Error-handling.html
cairo-1.2.6/doc/public/html/cairo-Transformations.html
cairo-1.2.6/doc/public/html/cairo-Version-Information.html
cairo-1.2.6/doc/public/html/cairo-Scaled-Fonts.html
cairo-1.2.6/doc/public/html/Fonts.html
cairo-1.2.6/doc/public/html/language-bindings.html
cairo-1.2.6/doc/public/html/cairo-Win32-Fonts.html
cairo-1.2.6/doc/public/html/ix01.html
cairo-1.2.6/doc/public/html/cairo-Font-Options.html
cairo-1.2.6/doc/public/html/Drawing.html
cairo-1.2.6/doc/public/html/cairo-SVG-Surfaces.html
cairo-1.2.6/doc/public/html/bindings-memory.html
cairo-1.2.6/doc/public/html/cairo-PNG-Support.html
cairo-1.2.6/doc/public/html/cairo-Paths.html
cairo-1.2.6/doc/public/html/bindings-errors.html
cairo-1.2.6/doc/public/html/Surfaces.html
cairo-1.2.6/doc/public/html/bindings-surfaces.html
cairo-1.2.6/doc/public/html/bindings-return-values.html
cairo-1.2.6/doc/public/html/cairo-Image-Surfaces.html
cairo-1.2.6/doc/public/html/pt02.html
cairo-1.2.6/doc/public/html/cairo-PostScript-Surfaces.html
cairo-1.2.6/doc/public/html/cairo-FreeType-Fonts.html
cairo-1.2.6/doc/public/html/index.sgml
cairo-1.2.6/doc/public/html/left.png
cairo-1.2.6/doc/public/html/style.css
cairo-1.2.6/doc/public/html/cairo-Patterns.html
cairo-1.2.6/doc/public/html/bindings-path.html
cairo-1.2.6/doc/public/html/up.png
cairo-1.2.6/doc/public/html/right.png
cairo-1.2.6/doc/public/html/cairo-cairo-surface-t.html
cairo-1.2.6/doc/public/html/home.png
cairo-1.2.6/doc/public/html/Support.html
cairo-1.2.6/doc/public/html/bindings-streams.html
cairo-1.2.6/doc/public/html/cairo-Win32-Surfaces.html
cairo-1.2.6/doc/public/html/cairo.devhelp
cairo-1.2.6/doc/public/html/bindings-patterns.html
cairo-1.2.6/doc/public/html/cairo-cairo-matrix-t.html
cairo-1.2.6/doc/public/html/cairo-Types.html
cairo-1.2.6/doc/public/html/index.html
cairo-1.2.6/doc/public/html/bindings-overloading.html
cairo-1.2.6/doc/public/html/cairo-Text.html
cairo-1.2.6/doc/public/html/cairo-PDF-Surfaces.html
cairo-1.2.6/doc/public/xml/
cairo-1.2.6/doc/public/xml/cairo-text.xml
cairo-1.2.6/doc/public/xml/cairo-version.xml
cairo-1.2.6/doc/public/xml/cairo-glitz.xml
cairo-1.2.6/doc/public/xml/cairo-xcb.xml
cairo-1.2.6/doc/public/xml/cairo-beos.xml
cairo-1.2.6/doc/public/xml/cairo-surface.xml
cairo-1.2.6/doc/public/xml/cairo-pdf.xml
cairo-1.2.6/doc/public/xml/cairo-font-options.xml
cairo-1.2.6/doc/public/xml/cairo-ft.xml
cairo-1.2.6/doc/public/xml/cairo-svg.xml
cairo-1.2.6/doc/public/xml/cairo-transforms.xml
cairo-1.2.6/doc/public/xml/cairo-win32.xml
cairo-1.2.6/doc/public/xml/cairo-types.xml
cairo-1.2.6/doc/public/xml/cairo-paths.xml
cairo-1.2.6/doc/public/xml/cairo-ps.xml
cairo-1.2.6/doc/public/xml/cairo-xlib-xrender.xml
cairo-1.2.6/doc/public/xml/cairo-xlib.xml
cairo-1.2.6/doc/public/xml/cairo-image.xml
cairo-1.2.6/doc/public/xml/cairo-win32-fonts.xml
cairo-1.2.6/doc/public/xml/cairo-matrix.xml
cairo-1.2.6/doc/public/xml/cairo-status.xml
cairo-1.2.6/doc/public/xml/cairo-xcb-xrender.xml
cairo-1.2.6/doc/public/xml/cairo-scaled-font.xml
cairo-1.2.6/doc/public/xml/cairo-pattern.xml
cairo-1.2.6/doc/public/xml/cairo-png.xml
cairo-1.2.6/doc/public/xml/cairo-font.xml
cairo-1.2.6/doc/public/xml/cairo-quartz.xml
cairo-1.2.6/doc/public/xml/cairo.xml
cairo-1.2.6/doc/public/cairo.types
cairo-1.2.6/doc/Makefile.in
cairo-1.2.6/doc/Makefile.am
cairo-1.2.6/NEWS
cairo-1.2.6/configure
cairo-1.2.6/test/
cairo-1.2.6/test/ft-text-antialias-none-ps-argb32-ref.png
cairo-1.2.6/test/get-group-target.c
cairo-1.2.6/test/dash-zero-length-ps-argb32-ref.png
cairo-1.2.6/test/ft-text-vertical-layout-type3-svg-ref.png
cairo-1.2.6/test/push-group-rgb24-ref.png
cairo-1.2.6/test/dash-caps-joins.c
cairo-1.2.6/test/line-width-scale.c
cairo-1.2.6/test/caps-joins.c
cairo-1.2.6/test/caps-joins-alpha-svg-ref.png
cairo-1.2.6/test/clip-fill-rule-pixel-aligned.c
cairo-1.2.6/test/operator-source-rgb24-ref.png
cairo-1.2.6/test/caps-sub-paths-ref.png
cairo-1.2.6/test/nil-surface-ref.png
cairo-1.2.6/test/move-to-show-surface-ref.png
cairo-1.2.6/test/clip-nesting-ps-argb32-ref.png
cairo-1.2.6/test/select-font-face.c
cairo-1.2.6/test/source-surface-scale-paint.c
cairo-1.2.6/test/dash-caps-joins-ref.png
cairo-1.2.6/test/cairo-test.h
cairo-1.2.6/test/rectangle-rounding-error-ref.png
cairo-1.2.6/test/scale-source-surface-paint-rgb24-ref.png
cairo-1.2.6/test/self-intersecting-rgb24-ref.png
cairo-1.2.6/test/mask-beos-bitmap-rgb24-ref.png
cairo-1.2.6/test/line-width-scale-ps-argb32-ref.png
cairo-1.2.6/test/text-rotate.c
cairo-1.2.6/test/nil-surface.c
cairo-1.2.6/test/line-width-scale-ref.png
cairo-1.2.6/test/composite-integer-translate-source-ref.png
cairo-1.2.6/test/mask-ctm-svg-argb32-ref.png
cairo-1.2.6/test/self-copy-ref.png
cairo-1.2.6/test/select-font-face-ref.png
cairo-1.2.6/test/fill-rule-ps-argb32-ref.png
cairo-1.2.6/test/ft-text-vertical-layout-type1-ref.png
cairo-1.2.6/test/operator-clear-ref.png
cairo-1.2.6/test/device-offset-positive-ref.png
cairo-1.2.6/test/font-matrix-translation-ps-argb32-ref.png
cairo-1.2.6/test/linear-gradient-svg-ref.png
cairo-1.2.6/test/caps-sub-paths.c
cairo-1.2.6/test/mask-rgb24-ref.png
cairo-1.2.6/test/paint.c
cairo-1.2.6/test/dash-scale.c
cairo-1.2.6/test/clip-twice-ps-argb32-ref.png
cairo-1.2.6/test/clip-nesting.c
cairo-1.2.6/test/a8-mask.c
cairo-1.2.6/test/scale-source-surface-paint-ref.png
cairo-1.2.6/test/unbounded-operator-ref.png
cairo-1.2.6/test/clip-twice-rgb24-ref.png
cairo-1.2.6/test/composite-integer-translate-over-svg-ref.png
cairo-1.2.6/test/composite-integer-translate-over.c
cairo-1.2.6/test/create-from-png-ref.png
cairo-1.2.6/test/show-text-current-point-svg-ref.png
cairo-1.2.6/test/source-clip.c
cairo-1.2.6/test/text-rotate-ref.png
cairo-1.2.6/test/pdf2png.c
cairo-1.2.6/test/fill-and-stroke-alpha.c
cairo-1.2.6/test/pixman-rotate-ref.png
cairo-1.2.6/test/leaky-polygon.c
cairo-1.2.6/test/push-group-svg-rgb24-ref.png
cairo-1.2.6/test/infinite-join-ps-argb32-ref.png
cairo-1.2.6/test/device-offset-rgb24-ref.png
cairo-1.2.6/test/composite-integer-translate-over-ref.png
cairo-1.2.6/test/leaky-dash.c
cairo-1.2.6/test/new-sub-path-rgb24-ref.png
cairo-1.2.6/test/unbounded-operator.c
cairo-1.2.6/test/create-from-png.c
cairo-1.2.6/test/mask-beos-rgb24-ref.png
cairo-1.2.6/test/linear-gradient.c
cairo-1.2.6/test/push-group-ref.png
cairo-1.2.6/test/degenerate-path-ref.png
cairo-1.2.6/test/dash-zero-length-rgb24-ref.png
cairo-1.2.6/test/infinite-join-ref.png
cairo-1.2.6/test/long-lines.c
cairo-1.2.6/test/clip-twice.c
cairo-1.2.6/test/text-antialias-subpixel-ref.png
cairo-1.2.6/test/mask-ctm-svg-rgb24-ref.png
cairo-1.2.6/test/trap-clip-rgb24-ref.png
cairo-1.2.6/test/push-group.c
cairo-1.2.6/test/composite-integer-translate-over-repeat-ref.png
cairo-1.2.6/test/copy-path-ps-argb32-ref.png
cairo-1.2.6/test/transforms-ps-argb32-ref.png
cairo-1.2.6/test/ft-text-vertical-layout-type3.c
cairo-1.2.6/test/source-clip-ref.png
cairo-1.2.6/test/mask-surface-ctm-rgb24-ref.png
cairo-1.2.6/test/text-pattern-svg-argb32-ref.png
cairo-1.2.6/test/text-antialias-subpixel.c
cairo-1.2.6/test/extend-reflect.c
cairo-1.2.6/test/caps-joins-ref.png
cairo-1.2.6/test/user-data.c
cairo-1.2.6/test/set-source-svg-rgb24-ref.png
cairo-1.2.6/test/paint-source-alpha-pdf-argb32-ref.png
cairo-1.2.6/test/rectangle-rounding-error.c
cairo-1.2.6/test/caps-joins-alpha.c
cairo-1.2.6/test/linear-gradient-ref.png
cairo-1.2.6/test/gradient-alpha-ref.png
cairo-1.2.6/test/degenerate-path.c
cairo-1.2.6/test/multi-page.c
cairo-1.2.6/test/ft-text-vertical-layout-type1.c
cairo-1.2.6/test/line-width-ps-argb32-ref.png
cairo-1.2.6/test/set-source-beos-rgb24-ref.png
cairo-1.2.6/test/fill-and-stroke-alpha-ref.png
cairo-1.2.6/test/make-html.pl
cairo-1.2.6/test/mask.c
cairo-1.2.6/test/clip-fill-rule-rgb24-ref.png
cairo-1.2.6/test/pixman-rotate-rgb24-ref.png
cairo-1.2.6/test/leaky-polygon-ps-argb32-ref.png
cairo-1.2.6/test/paint-source-alpha-svg-ref.png
cairo-1.2.6/test/select-font-face-svg-ref.png
cairo-1.2.6/test/set-source-beos-bitmap-rgb24-ref.png
cairo-1.2.6/test/move-to-show-surface.c
cairo-1.2.6/test/device-offset.c
cairo-1.2.6/test/imagediff.c
cairo-1.2.6/test/create-from-png-stream.c
cairo-1.2.6/test/translate-show-surface-ref.png
cairo-1.2.6/test/mask-surface-ctm-svg-argb32-ref.png
cairo-1.2.6/test/create-from-png-stream-ref.png
cairo-1.2.6/test/text-antialias-none.c
cairo-1.2.6/test/cairo-test.c
cairo-1.2.6/test/pattern-get-type.c
cairo-1.2.6/test/font-matrix-translation-ref.png
cairo-1.2.6/test/show-text-current-point-ref.png
cairo-1.2.6/test/source-surface-scale-paint-ref.png
cairo-1.2.6/test/clip-fill-rule-ref.png
cairo-1.2.6/test/glyph-cache-pressure-ps-argb32-ref.png
cairo-1.2.6/test/set-source-ref.png
cairo-1.2.6/test/bitmap-font-ref.png
cairo-1.2.6/test/dash-scale-ref.png
cairo-1.2.6/test/caps-sub-paths-ps-argb32-ref.png
cairo-1.2.6/test/dash-scale-ps-argb32-ref.png
cairo-1.2.6/test/README
cairo-1.2.6/test/6x13.pcf
cairo-1.2.6/test/self-copy.c
cairo-1.2.6/test/ft-text-antialias-none.c
cairo-1.2.6/test/xlib-surface.c
cairo-1.2.6/test/trap-clip-svg-rgb24-ref.png
cairo-1.2.6/test/ps-features.c
cairo-1.2.6/test/operator-source-ref.png
cairo-1.2.6/test/scale-source-surface-paint-svg-argb32-ref.png
cairo-1.2.6/test/dash-zero-length.c
cairo-1.2.6/test/unbounded-operator-rgb24-ref.png
cairo-1.2.6/test/dash-no-dash-ref.png
cairo-1.2.6/test/ft-text-vertical-layout-type1-svg-ref.png
cairo-1.2.6/test/glyph-cache-pressure-svg-ref.png
cairo-1.2.6/test/pixman-rotate.c
cairo-1.2.6/test/dash-no-dash.c
cairo-1.2.6/test/source-surface-scale-paint-rgb24-ref.png
cairo-1.2.6/test/paint-with-alpha-ref.png
cairo-1.2.6/test/fill-and-stroke-ps-argb32-ref.png
cairo-1.2.6/test/font-matrix-translation-svg-ref.png
cairo-1.2.6/test/degenerate-path-ps-argb32-ref.png
cairo-1.2.6/test/fallback-resolution.c
cairo-1.2.6/test/clip-fill-rule-ps-argb32-ref.png
cairo-1.2.6/test/dash-zero-length-ref.png
cairo-1.2.6/test/surface-pattern.c
cairo-1.2.6/test/fill-and-stroke-ref.png
cairo-1.2.6/test/device-offset-ref.png
cairo-1.2.6/test/clip-twice-ref.png
cairo-1.2.6/test/source-clip-scale-svg-ref.png
cairo-1.2.6/test/xmalloc.c
cairo-1.2.6/test/mask-ctm-ref.png
cairo-1.2.6/test/close-path.c
cairo-1.2.6/test/composite-integer-translate-source.c
cairo-1.2.6/test/device-offset-positive.c
cairo-1.2.6/test/trap-clip.c
cairo-1.2.6/test/scale-source-surface-paint-svg-rgb24-ref.png
cairo-1.2.6/test/nil-surface-rgb24-ref.png
cairo-1.2.6/test/text-pattern-ref.png
cairo-1.2.6/test/text-pattern.c
cairo-1.2.6/test/mask-svg-rgb24-ref.png
cairo-1.2.6/test/fill-and-stroke-alpha-svg-ref.png
cairo-1.2.6/test/bitmap-font-rgb24-ref.png
cairo-1.2.6/test/glyph-cache-pressure.c
cairo-1.2.6/test/ft-text-antialias-none-ref.png
cairo-1.2.6/test/text-pattern-svg-rgb24-ref.png
cairo-1.2.6/test/ft-text-vertical-layout-type3-ref.png
cairo-1.2.6/test/trap-clip-ref.png
cairo-1.2.6/test/transforms-ref.png
cairo-1.2.6/test/mask-surface-ctm.c
cairo-1.2.6/test/show-text-current-point.c
cairo-1.2.6/test/unantialiased-shapes.c
cairo-1.2.6/test/cairo-test-directfb.h
cairo-1.2.6/test/rel-path-ref.png
cairo-1.2.6/test/line-width-ref.png
cairo-1.2.6/test/pdf-features.c
cairo-1.2.6/test/buffer-diff.c
cairo-1.2.6/test/leaky-polygon-ref.png
cairo-1.2.6/test/cairo-test-directfb.c
cairo-1.2.6/test/composite-integer-translate-over-repeat.c
cairo-1.2.6/test/operator-clear.c
cairo-1.2.6/test/close-path-ref.png
cairo-1.2.6/test/filter-nearest-offset.c
cairo-1.2.6/test/filter-nearest-offset-ref.png
cairo-1.2.6/test/fill-rule-ref.png
cairo-1.2.6/test/dash-caps-joins-ps-argb32-ref.png
cairo-1.2.6/test/copy-path-ref.png
cairo-1.2.6/test/mask-beos-bitmap-argb32-ref.png
cairo-1.2.6/test/composite-integer-translate-over-pdf-argb32-ref.png
cairo-1.2.6/test/set-source-rgb24-ref.png
cairo-1.2.6/test/text-rotate-rgb24-ref.png
cairo-1.2.6/test/clip-nesting-rgb24-ref.png
cairo-1.2.6/test/fill-rule-rgb24-ref.png
cairo-1.2.6/test/zero-alpha-ref.png
cairo-1.2.6/test/new-sub-path.c
cairo-1.2.6/test/get-group-target-ref.png
cairo-1.2.6/test/degenerate-path-rgb24-ref.png
cairo-1.2.6/test/operator-source.c
cairo-1.2.6/test/Makefile.in
cairo-1.2.6/test/text-antialias-gray-ref.png
cairo-1.2.6/test/clip-operator.c
cairo-1.2.6/test/ft-font-create-for-ft-face.c
cairo-1.2.6/test/get-and-set.c
cairo-1.2.6/test/rel-path-rgb24-ref.png
cairo-1.2.6/test/mask-ctm.c
cairo-1.2.6/test/paint-source-alpha-ref.png
cairo-1.2.6/test/romedalen.png
cairo-1.2.6/test/select-font-face-ps-argb32-ref.png
cairo-1.2.6/test/self-intersecting.c
cairo-1.2.6/test/svg-surface.c
cairo-1.2.6/test/cairo-test-beos.cpp
cairo-1.2.6/test/mask-surface-ctm-ref.png
cairo-1.2.6/test/push-group-svg-argb32-ref.png
cairo-1.2.6/test/select-font-no-show-text.c
cairo-1.2.6/test/Makefile.am
cairo-1.2.6/test/operator-clear-rgb24-ref.png
cairo-1.2.6/test/xmalloc.h
cairo-1.2.6/test/trap-clip-beos-rgb24-ref.png
cairo-1.2.6/test/fill-rule.c
cairo-1.2.6/test/dash-offset-negative-ref.png
cairo-1.2.6/test/truetype-tables.c
cairo-1.2.6/test/svg2png.c
cairo-1.2.6/test/set-source.c
cairo-1.2.6/test/clip-nesting-ref.png
cairo-1.2.6/test/text-antialias-gray.c
cairo-1.2.6/test/svg-clip.c
cairo-1.2.6/test/paint-with-alpha.c
cairo-1.2.6/test/png-flatten.c
cairo-1.2.6/test/fill-and-stroke-alpha-add-ref.png
cairo-1.2.6/test/glyph-cache-pressure-ref.png
cairo-1.2.6/test/surface-finish-twice.c
cairo-1.2.6/test/scale-source-surface-paint.c
cairo-1.2.6/test/clip-operator-rgb24-ref.png
cairo-1.2.6/test/device-offset-positive-rgb24-ref.png
cairo-1.2.6/test/copy-path.c
cairo-1.2.6/test/bitmap-font.c
cairo-1.2.6/test/source-clip-scale.c
cairo-1.2.6/test/clip-all-ref.png
cairo-1.2.6/test/source-clip-scale-ref.png
cairo-1.2.6/test/show-glyphs-many-ref.png
cairo-1.2.6/test/clip-fill-rule-pixel-aligned-ref.png
cairo-1.2.6/test/gradient-alpha-rgb24-ref.png
cairo-1.2.6/test/fill-and-stroke-alpha-add.c
cairo-1.2.6/test/pthread-show-text.c
cairo-1.2.6/test/line-width.c
cairo-1.2.6/test/close-path-ps-argb32-ref.png
cairo-1.2.6/test/new-sub-path-ref.png
cairo-1.2.6/test/font-face-get-type.c
cairo-1.2.6/test/dash-offset-negative-ps-argb32-ref.png
cairo-1.2.6/test/trap-clip-beos-bitmap-rgb24-ref.png
cairo-1.2.6/test/text-cache-crash.c
cairo-1.2.6/test/bitmap-font-pdf-argb32-ref.png
cairo-1.2.6/test/mask-ref.png
cairo-1.2.6/test/caps-joins-ps-argb32-ref.png
cairo-1.2.6/test/trap-clip-svg-argb32-ref.png
cairo-1.2.6/test/transforms.c
cairo-1.2.6/test/paint-source-alpha.c
cairo-1.2.6/test/infinite-join.c
cairo-1.2.6/test/fill-and-stroke-rgb24-ref.png
cairo-1.2.6/test/gradient-alpha.c
cairo-1.2.6/test/clip-fill-rule-pixel-aligned-rgb24-ref.png
cairo-1.2.6/test/mask-ctm-rgb24-ref.png
cairo-1.2.6/test/show-text-current-point-ps-argb32-ref.png
cairo-1.2.6/test/caps-joins-alpha-ref.png
cairo-1.2.6/test/clip-operator-ref.png
cairo-1.2.6/test/zero-alpha.c
cairo-1.2.6/test/text-pattern-rgb24-ref.png
cairo-1.2.6/test/surface-pattern-ref.png
cairo-1.2.6/test/text-antialias-none-ref.png
cairo-1.2.6/test/set-source-svg-argb32-ref.png
cairo-1.2.6/test/rel-path.c
cairo-1.2.6/test/mask-surface-ctm-svg-rgb24-ref.png
cairo-1.2.6/test/long-lines-ref.png
cairo-1.2.6/test/create-for-stream.c
cairo-1.2.6/test/dash-offset-negative.c
cairo-1.2.6/test/scale-source-surface-paint-pdf-argb32-ref.png
cairo-1.2.6/test/translate-show-surface.c
cairo-1.2.6/test/clip-fill-rule.c
cairo-1.2.6/test/a8-mask-ref.png
cairo-1.2.6/test/cairo-test-beos.h
cairo-1.2.6/test/buffer-diff.h
cairo-1.2.6/test/unantialiased-shapes-ref.png
cairo-1.2.6/test/font-matrix-translation.c
cairo-1.2.6/test/paint-with-alpha-svg-ref.png
cairo-1.2.6/test/leaky-dash-ref.png
cairo-1.2.6/test/mask-svg-argb32-ref.png
cairo-1.2.6/test/fill-and-stroke.c
cairo-1.2.6/test/new-sub-path-ps-argb32-ref.png
cairo-1.2.6/test/self-intersecting-ref.png
cairo-1.2.6/test/clip-all.c
cairo-1.2.6/test/paint-ref.png
cairo-1.2.6/PORTING_GUIDE
cairo-1.2.6/INSTALL
cairo-1.2.6/README
cairo-1.2.6/COPYING-MPL-1.1
cairo-1.2.6/BUGS
cairo-1.2.6/TODO
cairo-1.2.6/ROADMAP
cairo-1.2.6/RELEASING
cairo-1.2.6/AUTHORS
cairo-1.2.6/ChangeLog.mk
cairo-1.2.6/missing
cairo-1.2.6/depcomp
cairo-1.2.6/Makefile.in
cairo-1.2.6/configure.in
cairo-1.2.6/Makefile.am
cairo-1.2.6/ChangeLog.pre-1.0
cairo-1.2.6/gtk-doc.make
cairo-1.2.6/config.sub
cairo-1.2.6/install-sh
cairo-1.2.6/acinclude.m4

ls=1f44ce8c.gif  cairo-1.2.6  cairo-1.2.6.tar.gz  ms tax.doc

---

### Post by jw5801 on 2007-10-02
You actually extracted something that time. For future reference, if you're going to post something that long please enclose it in "code tags" There's a little # in the advanced post editor bit that will give you them, or else put tags like in the title of this post (if I put them in the body then it does this: ```
code goes here
```

You'll notice that there isn't actually a file named "configure" in the folder you extracted. But there is one called "install-sh." There's also one called "README" which will almost certainly tell you what you're meant to do now. It's also probably easier to just use the graphical interface to extract the archive for you. If you browse to the archive in nautilus (the default gnome file browser), then you should be able to right click on it and extract it that way.

---

### Post by sailor2001 on 2007-10-02
thanks all you guys. That's been something that's been bugging me for a long time.

---

