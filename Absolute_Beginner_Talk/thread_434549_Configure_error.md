---
title: "Configure error"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2007-05-06
Hi,

If I "./configure" in the folder pidgin I get this:
> mehdi@mehdi-desktop:~/Mijn_documenten/Download/pidgin-2.0.0$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Could you help me to install pidgin, please?

Thanks,

---

### Post by igknighted on 2007-05-06
> **linux-beginner said:**
> Hi,

If I "./configure" in the folder pidgin I get this:

Could you help me to install pidgin, please?

Thanks,

You need to install a compiler.  Install the package build-essential and it should install everything you need.  Check out this thread for more help installing pidgin: [http://ubuntuforums.org/showthread.php?t=404508](http://ubuntuforums.org/showthread.php?t=404508)

---

### Post by Sef on 2007-05-06
To install build-essential:

From the terminal:

```
sudo apt-get update
```

```
sudo apt-get install build-essential
```

---

### Post by linux-beginner on 2007-05-06
By command "make install" I get this error:
> mehdi@mehdi-desktop:~/Mijn_documenten/Download/pidgin-2.0.0$ make install
Making install in libpurple
make[1]: Entering directory `/home/mehdi/Mijn_documenten/Download/pidgin-2.0.0/libpurple'
make  install-recursive
make[2]: Entering directory `/home/mehdi/Mijn_documenten/Download/pidgin-2.0.0/libpurple'
Making install in gconf
make[3]: Entering directory `/home/mehdi/Mijn_documenten/Download/pidgin-2.0.0/libpurple/gconf'
make[4]: Entering directory `/home/mehdi/Mijn_documenten/Download/pidgin-2.0.0/libpurple/gconf'
make[4]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/etc/gconf/gconf.xml.defaults /usr/bin/gconftool-2 --makefile-install-rule purple.schemas 2>&1 | \
                grep -v "^WARNING: failed to install schema" | grep -v "^Attached schema" 1>&2
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
None of the resolved addresses are writable; saving configuration settings will not be possible
test -z "/usr/local/etc/gconf/schemas" || mkdir -p -- "/usr/local/etc/gconf/schemas"
 /usr/bin/install -c -m 644 'purple.schemas' '/usr/local/etc/gconf/schemas/purple.schemas'
/usr/bin/install: cannot remove `/usr/local/etc/gconf/schemas/purple.schemas': Permission denied
make[4]: *** [install-schemaDATA] Error 1
make[4]: Leaving directory `/home/mehdi/Mijn_documenten/Download/pidgin-2.0.0/libpurple/gconf'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/mehdi/Mijn_documenten/Download/pidgin-2.0.0/libpurple/gconf'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/mehdi/Mijn_documenten/Download/pidgin-2.0.0/libpurple'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/mehdi/Mijn_documenten/Download/pidgin-2.0.0/libpurple'
make: *** [install-recursive] Error 1


What's wrong?

---

### Post by linux-beginner on 2007-05-06
permission problem! 
Thanks man!

---

