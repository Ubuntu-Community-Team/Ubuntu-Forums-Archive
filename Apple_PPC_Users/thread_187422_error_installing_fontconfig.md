---
title: "error installing fontconfig"
date: 2006-06-02
forum: Apple PPC Users
---

### Post by iamdigitalman on 2006-06-02
hey everyone. I have been practicing installing packages via the command line (and then uninstalling them). well, I am trying to install fontconfig, which is the really cool font configuration and customization library.

everything goes fine with the ./configure command, but then I start the compiling via the make command. here is a printout from the terminal. notice all the errors and warnings (note: long printout ahead):

```
make  all-recursive
make[1]: Entering directory `/home/leo/Desktop/fontconfig-2.3.2'
Making all in fontconfig
make[2]: Entering directory `/home/leo/Desktop/fontconfig-2.3.2/fontconfig'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/leo/Desktop/fontconfig-2.3.2/fontconfig'
Making all in fc-case
make[2]: Entering directory `/home/leo/Desktop/fontconfig-2.3.2/fc-case'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../src -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes      -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing    -g -O2 -MT fc-case.o -MD -MP -MF ".deps/fc-case.Tpo" \
          -c -o fc-case.o `test -f 'fc-case.c' || echo './'`fc-case.c; \
        then mv -f ".deps/fc-case.Tpo" ".deps/fc-case.Po"; \
        else rm -f ".deps/fc-case.Tpo"; exit 1; \
        fi
gcc  -g -O2   -o fc-case  fc-case.o
rm -f fccase.h
./fc-case ../fc-case/CaseFolding.txt < ../fc-case/fccase.tmpl.h > fccase.h
make[2]: Leaving directory `/home/leo/Desktop/fontconfig-2.3.2/fc-case'
Making all in fc-lang
make[2]: Entering directory `/home/leo/Desktop/fontconfig-2.3.2/fc-lang'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../src -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes      -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing    -g -O2 -MT fc-lang.o -MD -MP -MF ".deps/fc-lang.Tpo" \
          -c -o fc-lang.o `test -f 'fc-lang.c' || echo './'`fc-lang.c; \
        then mv -f ".deps/fc-lang.Tpo" ".deps/fc-lang.Po"; \
        else rm -f ".deps/fc-lang.Tpo"; exit 1; \
        fi
In file included from fc-lang.c:27:
../src/fcstr.c: In function ‘FcStrCaseWalkerInit’:
../src/fcstr.c:86: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
fc-lang.c: In function ‘FcConfigHome’:
fc-lang.c:53: warning: pointer targets in return differ in signedness
gcc  -g -O2   -o fc-lang  fc-lang.o
rm -f fclang.h
./fc-lang -d . aa.orth ab.orth af.orth am.orth ar.orth ast.orth ava.orth ay.orth az.orth az_ir.orth ba.orth bam.orth be.orth bg.orth bh.orth bho.orth bi.orth bin.orth bn.orth bo.orth br.orth bs.orth bua.orth ca.orth ce.orth ch.orth chm.orth chr.orth co.orth cs.orth cu.orth cv.orth cy.orth da.orth de.orth dz.orth el.orth en.orth eo.orth es.orth et.orth eu.orth fa.orth fi.orth fj.orth fo.orth fr.orth ful.orth fur.orth fy.orth ga.orth gd.orth gez.orth gl.orth gn.orth gu.orth gv.orth ha.orth haw.orth he.orth hi.orth ho.orth hr.orth hu.orth hy.orth ia.orth ibo.orth id.orth ie.orth ik.orth io.orth is.orth it.orth iu.orth ja.orth ka.orth kaa.orth ki.orth kk.orth kl.orth km.orth kn.orth ko.orth kok.orth ks.orth ku.orth ku_ir.orth kum.orth kv.orth kw.orth ky.orth la.orth lb.orth lez.orth lo.orth lt.orth lv.orth mg.orth mh.orth mi.orth mk.orth ml.orth mn.orth mo.orth mr.orth mt.orth my.orth nb.orth nds.orth ne.orth nl.orth nn.orth no.orth ny.orth oc.orth om.orth or.orth os.orth pa.orth pl.orth ps_af.orth ps_pk.orth pt.orth rm.orth ro.orth ru.orth sa.orth sah.orth sco.orth se.orth sel.orth sh.orth si.orth sk.orth sl.orth sm.orth sma.orth smj.orth smn.orth sms.orth so.orth sq.orth sr.orth sv.orth sw.orth syr.orth ta.orth te.orth tg.orth th.orth ti_er.orth ti_et.orth tig.orth tk.orth tl.orth tn.orth to.orth tr.orth ts.orth tt.orth tw.orth tyv.orth ug.orth uk.orth ur.orth uz.orth ven.orth vi.orth vo.orth vot.orth wa.orth wen.orth wo.orth xh.orth yap.orth yi.orth yo.orth zh_cn.orth zh_hk.orth zh_mo.orth zh_sg.orth zh_tw.orth zu.orth < ../fc-lang/fclang.tmpl.h > fclang.h
make[2]: Leaving directory `/home/leo/Desktop/fontconfig-2.3.2/fc-lang'
Making all in fc-glyphname
make[2]: Entering directory `/home/leo/Desktop/fontconfig-2.3.2/fc-glyphname'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../src -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes      -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing    -g -O2 -MT fc-glyphname.o -MD -MP -MF ".deps/fc-glyphname.Tpo" \
          -c -o fc-glyphname.o `test -f 'fc-glyphname.c' || echo './'`fc-glyphname.c; \
        then mv -f ".deps/fc-glyphname.Tpo" ".deps/fc-glyphname.Po"; \
        else rm -f ".deps/fc-glyphname.Tpo"; exit 1; \
        fi
fc-glyphname.c: In function ‘scan’:
fc-glyphname.c:108: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
fc-glyphname.c: In function ‘main’:
fc-glyphname.c:289: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
gcc  -g -O2   -o fc-glyphname  fc-glyphname.o
rm -f fcglyphname.h
./fc-glyphname ../fc-glyphname/zapfdingbats.txt < ../fc-glyphname/fcglyphname.tmpl.h > fcglyphname.h
make[2]: Leaving directory `/home/leo/Desktop/fontconfig-2.3.2/fc-glyphname'
Making all in src
make[2]: Entering directory `/home/leo/Desktop/fontconfig-2.3.2/src'
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include  -Wall -Wpointer-arith -Wstrict-prototypes         -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH='"/usr/local/etc/fonts"' -I.. -I../src    -g -O2 -MT fcatomic.lo -MD -MP -MF ".deps/fcatomic.Tpo" \
          -c -o fcatomic.lo `test -f 'fcatomic.c' || echo './'`fcatomic.c; \
        then mv -f ".deps/fcatomic.Tpo" ".deps/fcatomic.Plo"; \
        else rm -f ".deps/fcatomic.Tpo"; exit 1; \
        fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fcatomic.lo -MD -MP -MF .deps/fcatomic.Tpo -c fcatomic.c  -fPIC -DPIC -o .libs/fcatomic.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fcatomic.lo -MD -MP -MF .deps/fcatomic.Tpo -c fcatomic.c -o fcatomic.o >/dev/null 2>&1
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include  -Wall -Wpointer-arith -Wstrict-prototypes         -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH='"/usr/local/etc/fonts"' -I.. -I../src    -g -O2 -MT fcblanks.lo -MD -MP -MF ".deps/fcblanks.Tpo" \
          -c -o fcblanks.lo `test -f 'fcblanks.c' || echo './'`fcblanks.c; \
        then mv -f ".deps/fcblanks.Tpo" ".deps/fcblanks.Plo"; \
        else rm -f ".deps/fcblanks.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fcblanks.lo -MD -MP -MF .deps/fcblanks.Tpo -c fcblanks.c  -fPIC -DPIC -o .libs/fcblanks.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fcblanks.lo -MD -MP -MF .deps/fcblanks.Tpo -c fcblanks.c -o fcblanks.o >/dev/null 2>&1
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include  -Wall -Wpointer-arith -Wstrict-prototypes         -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH='"/usr/local/etc/fonts"' -I.. -I../src    -g -O2 -MT fccache.lo -MD -MP -MF ".deps/fccache.Tpo" \
          -c -o fccache.lo `test -f 'fccache.c' || echo './'`fccache.c; \
        then mv -f ".deps/fccache.Tpo" ".deps/fccache.Plo"; \
        else rm -f ".deps/fccache.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fccache.lo -MD -MP -MF .deps/fccache.Tpo -c fccache.c  -fPIC -DPIC -o .libs/fccache.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fccache.lo -MD -MP -MF .deps/fccache.Tpo -c fccache.c -o fccache.o >/dev/null 2>&1
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include  -Wall -Wpointer-arith -Wstrict-prototypes         -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH='"/usr/local/etc/fonts"' -I.. -I../src    -g -O2 -MT fccfg.lo -MD -MP -MF ".deps/fccfg.Tpo" \
          -c -o fccfg.lo `test -f 'fccfg.c' || echo './'`fccfg.c; \
        then mv -f ".deps/fccfg.Tpo" ".deps/fccfg.Plo"; \
        else rm -f ".deps/fccfg.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fccfg.lo -MD -MP -MF .deps/fccfg.Tpo -c fccfg.c  -fPIC -DPIC -o .libs/fccfg.o
fccfg.c: In function 'FcConfigHome':
fccfg.c:1608: warning: pointer targets in return differ in signedness
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fccfg.lo -MD -MP -MF .deps/fccfg.Tpo -c fccfg.c -o fccfg.o >/dev/null 2>&1
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include  -Wall -Wpointer-arith -Wstrict-prototypes         -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH='"/usr/local/etc/fonts"' -I.. -I../src    -g -O2 -MT fccharset.lo -MD -MP -MF ".deps/fccharset.Tpo" \
          -c -o fccharset.lo `test -f 'fccharset.c' || echo './'`fccharset.c; \
        then mv -f ".deps/fccharset.Tpo" ".deps/fccharset.Plo"; \
        else rm -f ".deps/fccharset.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fccharset.lo -MD -MP -MF .deps/fccharset.Tpo -c fccharset.c  -fPIC -DPIC -o .libs/fccharset.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fccharset.lo -MD -MP -MF .deps/fccharset.Tpo -c fccharset.c -o fccharset.o >/dev/null 2>&1
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include  -Wall -Wpointer-arith -Wstrict-prototypes         -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH='"/usr/local/etc/fonts"' -I.. -I../src    -g -O2 -MT fcdbg.lo -MD -MP -MF ".deps/fcdbg.Tpo" \
          -c -o fcdbg.lo `test -f 'fcdbg.c' || echo './'`fcdbg.c; \
        then mv -f ".deps/fcdbg.Tpo" ".deps/fcdbg.Plo"; \
        else rm -f ".deps/fcdbg.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fcdbg.lo -MD -MP -MF .deps/fcdbg.Tpo -c fcdbg.c  -fPIC -DPIC -o .libs/fcdbg.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fcdbg.lo -MD -MP -MF .deps/fcdbg.Tpo -c fcdbg.c -o fcdbg.o >/dev/null 2>&1
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include  -Wall -Wpointer-arith -Wstrict-prototypes         -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH='"/usr/local/etc/fonts"' -I.. -I../src    -g -O2 -MT fcdefault.lo -MD -MP -MF ".deps/fcdefault.Tpo" \
          -c -o fcdefault.lo `test -f 'fcdefault.c' || echo './'`fcdefault.c; \
        then mv -f ".deps/fcdefault.Tpo" ".deps/fcdefault.Plo"; \
        else rm -f ".deps/fcdefault.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fcdefault.lo -MD -MP -MF .deps/fcdefault.Tpo -c fcdefault.c  -fPIC -DPIC -o .libs/fcdefault.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fcdefault.lo -MD -MP -MF .deps/fcdefault.Tpo -c fcdefault.c -o fcdefault.o >/dev/null 2>&1
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include  -Wall -Wpointer-arith -Wstrict-prototypes         -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH='"/usr/local/etc/fonts"' -I.. -I../src    -g -O2 -MT fcdir.lo -MD -MP -MF ".deps/fcdir.Tpo" \
          -c -o fcdir.lo `test -f 'fcdir.c' || echo './'`fcdir.c; \
        then mv -f ".deps/fcdir.Tpo" ".deps/fcdir.Plo"; \
        else rm -f ".deps/fcdir.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fcdir.lo -MD -MP -MF .deps/fcdir.Tpo -c fcdir.c  -fPIC -DPIC -o .libs/fcdir.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fcdir.lo -MD -MP -MF .deps/fcdir.Tpo -c fcdir.c -o fcdir.o >/dev/null 2>&1
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include  -Wall -Wpointer-arith -Wstrict-prototypes         -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH='"/usr/local/etc/fonts"' -I.. -I../src    -g -O2 -MT fcfreetype.lo -MD -MP -MF ".deps/fcfreetype.Tpo" \
          -c -o fcfreetype.lo `test -f 'fcfreetype.c' || echo './'`fcfreetype.c; \
        then mv -f ".deps/fcfreetype.Tpo" ".deps/fcfreetype.Plo"; \
        else rm -f ".deps/fcfreetype.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/freetype2 -I/usr/local/include -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -DFONTCONFIG_PATH=\"/usr/local/etc/fonts\" -I.. -I../src -g -O2 -MT fcfreetype.lo -MD -MP -MF .deps/fcfreetype.Tpo -c fcfreetype.c  -fPIC -DPIC -o .libs/fcfreetype.ofcfreetype.c:53:10: error: #include expects "FILENAME" or <FILENAME>
fcfreetype.c:58:10: error: #include expects "FILENAME" or <FILENAME>
fcfreetype.c:59:10: error: #include expects "FILENAME" or <FILENAME>
fcfreetype.c:60:10: error: #include expects "FILENAME" or <FILENAME>
fcfreetype.c: In function 'FcSfntNameTranscode':
fcfreetype.c:736: warning: pointer targets in passing argument 2 of 'FcStrCmpIgnoreBlanksAndCase' differ in signedness
fcfreetype.c: In function 'FcSfntNameLanguage':
fcfreetype.c:752: warning: pointer targets in return differ in signedness
fcfreetype.c: In function 'FcVendorMatch':
fcfreetype.c:804: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
fcfreetype.c: At top level:
fcfreetype.c:899: warning: pointer targets in initialization differ in signedness
fcfreetype.c:900: warning: pointer targets in initialization differ in signedness
fcfreetype.c:901: warning: pointer targets in initialization differ in signedness
fcfreetype.c:902: warning: pointer targets in initialization differ in signedness
fcfreetype.c:903: warning: pointer targets in initialization differ in signedness
fcfreetype.c:904: warning: pointer targets in initialization differ in signedness
fcfreetype.c:905: warning: pointer targets in initialization differ in signedness
fcfreetype.c:906: warning: pointer targets in initialization differ in signedness
fcfreetype.c:907: warning: pointer targets in initialization differ in signedness
fcfreetype.c:908: warning: pointer targets in initialization differ in signedness
fcfreetype.c:909: warning: pointer targets in initialization differ in signedness
fcfreetype.c:910: warning: pointer targets in initialization differ in signedness
fcfreetype.c:911: warning: pointer targets in initialization differ in signedness
fcfreetype.c:912: warning: pointer targets in initialization differ in signedness
fcfreetype.c:913: warning: pointer targets in initialization differ in signedness
fcfreetype.c:914: warning: pointer targets in initialization differ in signedness
fcfreetype.c:923: warning: pointer targets in initialization differ in signedness
fcfreetype.c:924: warning: pointer targets in initialization differ in signedness
fcfreetype.c:925: warning: pointer targets in initialization differ in signedness
fcfreetype.c:926: warning: pointer targets in initialization differ in signedness
fcfreetype.c:927: warning: pointer targets in initialization differ in signedness
fcfreetype.c:928: warning: pointer targets in initialization differ in signedness
fcfreetype.c:929: warning: pointer targets in initialization differ in signedness
fcfreetype.c:930: warning: pointer targets in initialization differ in signedness
fcfreetype.c:931: warning: pointer targets in initialization differ in signedness
fcfreetype.c:940: warning: pointer targets in initialization differ in signedness
fcfreetype.c:941: warning: pointer targets in initialization differ in signedness
fcfreetype.c: In function 'FcGetPixelSize':
fcfreetype.c:958: error: dereferencing pointer to incomplete type
fcfreetype.c: In function 'FcFreeTypeQuery':
fcfreetype.c:1157: warning: pointer targets in passing argument 3 of 'FcPatternAddString' differ in signedness
fcfreetype.c:1172: warning: pointer targets in passing argument 1 of 'FcStrCmpIgnoreBlanksAndCase' differ in signedness
fcfreetype.c:1172: warning: pointer targets in passing argument 2 of 'FcStrCmpIgnoreBlanksAndCase' differ in signedness
fcfreetype.c:1176: warning: pointer targets in passing argument 3 of 'FcPatternAddString' differ in signedness
fcfreetype.c:1182: warning: pointer targets in passing argument 1 of 'FcStrCmpIgnoreBlanksAndCase' differ in signedness
fcfreetype.c:1182: warning: pointer targets in passing argument 2 of 'FcStrCmpIgnoreBlanksAndCase' differ in signedness
fcfreetype.c:1186: warning: pointer targets in passing argument 3 of 'FcPatternAddString' differ in signedness
fcfreetype.c:1403: warning: pointer targets in passing argument 1 of 'FcStringIsConst' differ in signedness
fcfreetype.c:1435: error: dereferencing pointer to incomplete type
fcfreetype.c:1437: warning: pointer targets in assignment differ in signedness
fcfreetype.c:1442: error: dereferencing pointer to incomplete type
fcfreetype.c:1465: error: dereferencing pointer to incomplete type
fcfreetype.c:1468: warning: pointer targets in passing argument 1 of 'FcStringIsConst' differ in signedness
fcfreetype.c:1521: warning: pointer targets in assignment differ in signedness
fcfreetype.c:1545: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: warning: implicit declaration of function 'FT_MODULE_CLASS'
fcfreetype.c:1562: warning: nested extern declaration of 'FT_MODULE_CLASS'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1562: error: dereferencing pointer to incomplete type
fcfreetype.c:1562: error: invalid type argument of '->'
fcfreetype.c:1599: error: dereferencing pointer to incomplete type
fcfreetype.c:1609: error: dereferencing pointer to incomplete type
fcfreetype.c:1632: warning: pointer targets in passing argument 3 of 'FcPatternAddString' differ in signedness
fcfreetype.c: In function 'addtag':
fcfreetype.c:2692: warning: pointer targets in passing argument 1 of 'strcat' differ in signedness
fcfreetype.c:2693: warning: pointer targets in passing argument 1 of 'strcat' differ in signedness
fcfreetype.c:2694: warning: pointer targets in passing argument 1 of 'strcat' differ in signedness
fcfreetype.c:2694: warning: pointer targets in passing argument 2 of 'strcat' differ in signedness
fcfreetype.c: In function 'GetScriptTags':
fcfreetype.c:2710: error: 'TT_Face' undeclared (first use in this function)
fcfreetype.c:2710: error: (Each undeclared identifier is reported only once
fcfreetype.c:2710: error: for each function it appears in.)
fcfreetype.c:2710: error: syntax error before 'tt_face'
fcfreetype.c:2719: error: 'tt_face' undeclared (first use in this function)
fcfreetype.c:2722: warning: implicit declaration of function 'FT_STREAM_POS'
fcfreetype.c:2722: warning: nested extern declaration of 'FT_STREAM_POS'
fcfreetype.c:2726: warning: implicit declaration of function 'FT_STREAM_SEEK'
fcfreetype.c:2726: warning: nested extern declaration of 'FT_STREAM_SEEK'
fcfreetype.c:2726: warning: implicit declaration of function 'FT_FRAME_ENTER'
fcfreetype.c:2726: warning: nested extern declaration of 'FT_FRAME_ENTER'
fcfreetype.c:2729: warning: implicit declaration of function 'FT_GET_USHORT'
fcfreetype.c:2729: warning: nested extern declaration of 'FT_GET_USHORT'
fcfreetype.c:2731: warning: implicit declaration of function 'FT_FRAME_EXIT'
fcfreetype.c:2731: warning: nested extern declaration of 'FT_FRAME_EXIT'
fcfreetype.c:2747: warning: implicit declaration of function 'FT_SET_ERROR'
fcfreetype.c:2747: warning: nested extern declaration of 'FT_SET_ERROR'
fcfreetype.c:2747: warning: implicit declaration of function 'FT_MEM_ALLOC_ARRAY'
fcfreetype.c:2747: warning: nested extern declaration of 'FT_MEM_ALLOC_ARRAY'
fcfreetype.c:2747: error: syntax error before 'FT_ULong'
fcfreetype.c:2756: warning: implicit declaration of function 'FT_GET_ULONG'
fcfreetype.c:2756: warning: nested extern declaration of 'FT_GET_ULONG'
fcfreetype.c:2787: warning: implicit declaration of function 'FT_FREE'
fcfreetype.c:2787: warning: nested extern declaration of 'FT_FREE'
fcfreetype.c:2714: warning: unused variable 'memory'
fcfreetype.c: In function 'FcFontCapabilities':
fcfreetype.c:2823: warning: pointer targets in passing argument 1 of 'strcpy' differ in signedness
fcfreetype.c:2800: warning: unused variable 'memory'
make[2]: *** [fcfreetype.lo] Error 1
make[2]: Leaving directory `/home/leo/Desktop/fontconfig-2.3.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/leo/Desktop/fontconfig-2.3.2'
make: *** [all] Error 2

```

so, what am I doing wrong? is it because I am trying to compile this for a PowerPC processor and it expects an x86?

btw, I have compiled several other programs from the source code, and havnt experienced any trouble. note, this is just for practice, and not anything critical.

thanks. -digital ;)

---

### Post by BoneKracker on 2006-06-03
Did you check first to see if fontconfig is already installed and, if so, whether it is an important part of the system?  Don't hose your box while you're experimenting around.

---

### Post by iamdigitalman on 2006-06-03
no, it's not installed. and I figured I had better play with it now and cause damage than when I have all my important files moved over. oh well, just foling around. no harm done.

-digital ;)

---

