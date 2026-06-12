---
title: "[SOLVED] Problem Compiling Cairo"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by lordfkiller on 2007-09-18
Hello.

I am trying to compile libgdiplus. During compilation process(make) an error occurs.
After some work, I found that during compilation, it attempts to compile cairo as well(source code of cairo is also included with libgdiplus) and the error occurs there.

I went to cairo folder and ran ./autogen.sh (I'm using SVN). Following is the result:
[INDENT]./autogen.sh: running `libtoolize --copy --force'
Putting files in AC_CONFIG_AUX_DIR, `..'.
./autogen.sh: running `aclocal-1.9'
./autogen.sh: running `autoheader'
./autogen.sh: running `automake-1.9 --add-missing'
./autogen.sh: running `autoconf'
cd: 171: can't cd to /opt/SVN/Mono
[/INDENT]

Notice the last line. It is searching for Mono in /opt/SVN. But my Mono source code is not there. Nor is it installed there. Does anybody know why?

Thanks for any help.

---

### Post by lordfkiller on 2007-09-18
Just found where the problem is!

Cairo is here: /opt/SVN/Mono Project/libgdiplus/cairo/ . Now, when it wants to cd to somewhere in this path, it has run a command like this: cd "/opt/SVN/Mono Project/somewhere/". But it doesn't place those quotation marks and cd thinks the path is "/opt/SVN/Mono".

Renamed that folder and everything is okay now ;)

---

