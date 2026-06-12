---
title: "compiz conundrum"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by je1117 on 2007-02-04
Using [Compiz's compiling guide]("http://www.go-compiz.org/index.php?title=Compiling") I get the output requested in step 2, but when I try Make it gives me this:

make  all-recursive
make[1]: Entering directory `/home/joshwa/compiz-0.3.6'
Making all in include
make[2]: Entering directory `/home/joshwa/compiz-0.3.6/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/joshwa/compiz-0.3.6/include'
Making all in src
make[2]: Entering directory `/home/joshwa/compiz-0.3.6/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/libpng12 -I/usr/include/startup-notification-1.0 -I../include -DPLUGINDIR=\"/usr/lib/compiz\" -DIMAGEDIR=\"/usr/share/compiz\"    -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
In file included from main.c:37:
../include/compiz.h:46:19: error: GL/gl.h: No such file or directory
../include/compiz.h:47:20: error: GL/glx.h: No such file or directory
In file included from main.c:37:
../include/compiz.h:203: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘defaultColor’
../include/compiz.h:764: error: expected specifier-qualifier-list before ‘GLenum’
../include/compiz.h:996: error: expected specifier-qualifier-list before ‘GLfloat’
../include/compiz.h:1006: error: expected specifier-qualifier-list before ‘GLushort’
../include/compiz.h:1184: error: expected specifier-qualifier-list before ‘GLuint’
../include/compiz.h:1292: warning: type defaults to ‘int’ in declaration of ‘GLubyte’
../include/compiz.h:1292: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
../include/compiz.h:1295: error: expected declaration specifiers or ‘...’ before ‘GLXDrawable’
../include/compiz.h:1299: error: expected declaration specifiers or ‘...’ before ‘GLXDrawable’
../include/compiz.h:1302: error: expected declaration specifiers or ‘...’ before ‘GLXDrawable’
../include/compiz.h:1307: error: expected declaration specifiers or ‘...’ before ‘GLXDrawable’
../include/compiz.h:1329: error: expected declaration specifiers or ‘...’ before ‘*’ token
../include/compiz.h:1332: warning: type defaults to ‘int’ in declaration of ‘GLXPixmap’
../include/compiz.h:1332: error: ‘GLXPixmap’ declared as function returning a function
../include/compiz.h:1332: warning: function declaration isn’t a prototype
../include/compiz.h:1334: error: expected ‘)’ before ‘texture’
../include/compiz.h:1335: error: expected ‘)’ before ‘texture’
../include/compiz.h:1337: error: expected ‘)’ before ‘n’
../include/compiz.h:1339: error: expected ‘)’ before ‘n’
../include/compiz.h:1341: error: expected ‘)’ before ‘target’
../include/compiz.h:1343: error: expected ‘)’ before ‘target’
../include/compiz.h:1347: error: expected ‘)’ before ‘target’
../include/compiz.h:1354: error: expected ‘)’ before ‘n’
../include/compiz.h:1356: error: expected ‘)’ before ‘n’
../include/compiz.h:1358: error: expected ‘)’ before ‘target’
../include/compiz.h:1360: error: expected declaration specifiers or ‘...’ before ‘*’ token
../include/compiz.h:1360: error: expected ‘)’ before ‘target’
../include/compiz.h:1361: error: expected ‘)’ before ‘target’
../include/compiz.h:1366: error: expected ‘)’ before ‘target’
../include/compiz.h:1530: error: expected specifier-qualifier-list before ‘GLint’
../include/compiz.h:1839: error: expected declaration specifiers or ‘...’ before ‘GLenum’
../include/compiz.h:1956: error: expected specifier-qualifier-list before ‘GLint’
main.c:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘defaultColor’
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/joshwa/compiz-0.3.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/joshwa/compiz-0.3.6'
make: *** [all] Error 2

I was wondering if someone could point me in the right direction? I am running an AMD64 and  am trying to compile the newer version of compiz.

---

### Post by jordanmthomas on 2007-02-05
```
../include/compiz.h:46:19: error: GL/gl.h: No such file or directory
../include/compiz.h:47:20: error: GL/glx.h: No such file or directory
```

According to a quick package search, what you need is in the following package:
```
sudo aptitude install libgl1-mesa-dev mesa-common-dev
```

glx.h also appears in libgl1-mesa-swx11-dev

maybe this'll get you rolling?

---

