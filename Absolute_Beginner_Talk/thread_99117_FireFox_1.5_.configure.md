---
title: "FireFox 1.5 ./configure"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by Naddiseo on 2005-12-04
Hello, I tried installing firefox1.5 again from source but I'm getting some errors.

I ran: 
```

 ./configure --enable-threads=posix --prefix=/usr --with-local-prefix=/usr/local --infodir=/usr/share/info --mandir=/usr/share/man --libdir=/usr/lib --libexecdir=/usr/lib --disable-checking --enable-java-awt=gtk --enable-application=browser

```

And got:
```

checking for libIDL-2.0 >= 0.8.0... checking for glib-config... no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
checking for libIDL-config... no
checking for libIDL - version >= 0.6.3... no
*** The libIDL-config script installed by libIDL could not be found
*** If libIDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the LIBIDL_CONFIG environment variable to the
*** full path to libIDL-config.
checking for libIDL-2.0 >= 0.8.0... Package libIDL-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libIDL-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libIDL-2.0' found
configure: error: Library requirements (libIDL-2.0 >= 0.8.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

I did a search for libIDL and I have /usr/lib/libIDL-2.so.0.0.0 doesn't that qualify?

I'm running off links :( And reinstalling firefox doesn't want to work, even if I completely remove then reinstall. (The 1.0.7 that is)

Any ideas? Or other threads that have had the same problem?

Thanks.

---

### Post by Naddiseo on 2005-12-04
It seems that installing libIDL-dev has cured it :D

---

