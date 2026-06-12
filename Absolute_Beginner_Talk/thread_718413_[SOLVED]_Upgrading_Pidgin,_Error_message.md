---
title: "[SOLVED] Upgrading Pidgin, Error message"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Deedlit on 2008-03-08
I am trying to upgrade from pidgin 2.2 to pidgin 2.4.0.  I downloaded it okay, ran ./configure, ran make and then make install. this is what I got:

-2.0   ../libpurple/libpurple.la -lnsl -lresolv 
make[3]: Leaving directory `/home/deedlit/pidgin-2.4.0/pidgin'
make[2]: Leaving directory `/home/deedlit/pidgin-2.4.0/pidgin'
Making all in m4macros
make[2]: Entering directory `/home/deedlit/pidgin-2.4.0/m4macros'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deedlit/pidgin-2.4.0/m4macros'
Making all in po
make[2]: Entering directory `/home/deedlit/pidgin-2.4.0/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deedlit/pidgin-2.4.0/po'
Making all in share/ca-certs
make[2]: Entering directory `/home/deedlit/pidgin-2.4.0/share/ca-certs'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deedlit/pidgin-2.4.0/share/ca-certs'
Making all in share/sounds
make[2]: Entering directory `/home/deedlit/pidgin-2.4.0/share/sounds'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deedlit/pidgin-2.4.0/share/sounds'
make[2]: Entering directory `/home/deedlit/pidgin-2.4.0'
make[2]: Leaving directory `/home/deedlit/pidgin-2.4.0'
make[1]: Leaving directory `/home/deedlit/pidgin-2.4.0'
deedlit@Eeyore:~/pidgin-2.4.0$ make install
Making install in libpurple
make[1]: Entering directory `/home/deedlit/pidgin-2.4.0/libpurple'
make  install-recursive
make[2]: Entering directory `/home/deedlit/pidgin-2.4.0/libpurple'
Making install in gconf
make[3]: Entering directory `/home/deedlit/pidgin-2.4.0/libpurple/gconf'
make[4]: Entering directory `/home/deedlit/pidgin-2.4.0/libpurple/gconf'
make[4]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/etc/gconf/gconf.xml.defaults /usr/bin/gconftool-2 --makefile-install-rule purple.schemas 2>&1 | \
                grep -v "^WARNING: failed to install schema" | grep -v "^Attached schema" 1>&2

(gconftool-2:29082): GConf-WARNING **: None of the resolved addresses are writable; saving configuration settings will not be possible
test -z "/usr/local/etc/gconf/schemas" || /bin/mkdir -p "/usr/local/etc/gconf/schemas"
 /usr/bin/install -c -m 644 'purple.schemas' '/usr/local/etc/gconf/schemas/purple.schemas'
/usr/bin/install: cannot remove `/usr/local/etc/gconf/schemas/purple.schemas': Permission denied
make[4]: *** [install-schemaDATA] Error 1
make[4]: Leaving directory `/home/deedlit/pidgin-2.4.0/libpurple/gconf'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/deedlit/pidgin-2.4.0/libpurple/gconf'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/deedlit/pidgin-2.4.0/libpurple'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/deedlit/pidgin-2.4.0/libpurple'
make: *** [install-recursive] Error 1
deedlit@Eeyore:~/pidgin-2.4.0$ 

I don't know where to go from here, but 2.4.0 is not running.  There is far more text if you need it.

Thanks for the help.

---

### Post by chirpilittle on 2008-03-08
Try completely removing pidgin and installing the new version from scratch. Or else check that the package you downloaded was the correct version. If that doesn't work, try Amsn instead. I personally find it better than pidgin.  
(I'm not that experienced with Ubuntu. Good luck)

---

### Post by ryanhaigh on 2008-03-08
Just grab the debs from [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin), download all the debs to a folder on your desktop then use
```
sudo dpkg -i *
``` inside that folder to install the packages.

Make sure you have removed the files from your failed source install. Once installed from these debs you can then install the plugings like pidgin-libnotify etc from ubuntus repos.

---

