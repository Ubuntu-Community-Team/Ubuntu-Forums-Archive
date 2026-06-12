---
title: "yzis install problem"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-06-30
i am trying to install the yzis text editor (version M3). I know that i t requires Lua 5.0, which i've installed from Synaptic, but during the ./configure process it says that Lua.h is missing or it is not the good version. Pls help

---

### Post by FuzZy2006 on 2006-07-01
Can anybody try to install this program? [http://yzis.org.free.fr/releases/yzis-M3.tar.bz2](http://yzis.org.free.fr/releases/yzis-M3.tar.bz2). Yzis milestone 3. PLS help

---

### Post by AndreasJ on 2006-09-07
This thread is becoming quite old but if anyone else have the problem try ./configure --with-lua-includes=/usr/include/lua50 that should resolve it.

---

