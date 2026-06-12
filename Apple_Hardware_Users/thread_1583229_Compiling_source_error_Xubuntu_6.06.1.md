---
title: "Compiling source error Xubuntu 6.06.1"
date: 2010-09-27
forum: Apple Hardware Users
---

### Post by RavenTK on 2010-09-27
Hi all.

I've searched this error on the net but i can't figure out how to solve it....
Now..i've to install efax-gtk.But i can find it only with sources.
So i've to compile it.I'm on iMac G3 with Xubuntu 6.06.1 - Alternate.

So i type ./configure and this is the output i get:
```

cheking for a BSD-compatible install... /usr/bin/install -c
cheking whether build environment is sane ... yes
cheking for a thread-safe mkdir -p... /bin/mkdir -p
cheking for gawk... no
cheking for mawk... mawk
cheking whether make sets $(MAKE)... yes
cheking for style of include used by make... GNU
cheking for gcc... no
cheking for cc... no
cheking for cl.exe... no
configure: error: in '/home/marisa/Desktop/es/efax-gtk-3.2.4':
configure: error: no acceptable C compiler found in $PATH
See 'config.log' for more details.

```

Now the config.log:

```

ecc.ecc..

  $ ./configure

hostname= dhcppc1
uname -m = ppc
uname -r = 2.6.15-26-powerpc
uname -s = Linux
uname -v =#1 Thu Aug 3 02:53:39 UTC 2006

/usr/bin/uname -p = unknown
/bin/uname -x       = unknown

/bin/arch                      = ppc
/usr/bin/arch -k            = unknown
/usr/convex/getsysinfo  = unknown
/usr/bin/hostinfo           = unknown
/bin/machine                = unknown
/usr/bin/uslevel            = unknown
/bin/universe                = unknown
/usr/bin/oslevel            = unknown
/bin/universe                = unknown 

```

And a lot of other lines (i'm typing it so i can't write all the file but it seems that's the intresting part)


Anyone can please tell me how can i solve the problem?
(in packet manager i've installet gcc but it change nothing)

Thanks.

---

### Post by linuxopjemac on 2010-09-27
I would install build-essential.
```
sudo apt-get install build-essential
```

---

### Post by RavenTK on 2010-09-27
Thanks,it worked for the error listed above,but now i've new errors.
I've search a bit on forums and it seems i've to install the package he tell (gtk3)
But...i think i've install all gtk dev package i know... and it don't work jet.
This is the error:

```

some code... (seems to compile succesful)
cheking which version of gtk+ compile against... auto
cheking for pkg-config... /usr/bin/pkg-config
cheking for gtk+-2.0 >= 2.12.0... no
cheking for gtk+-3.0 >= 2.90.0... no
configure: error: Library requirements (gtk 3.0 >=2.90.0) not met: consider adjusting
the PKG_CONFIG_PATH environment variable if your libraries are in nonstandard prefix so pkg_config can find them

```

My GTK installed package:
-libgtk1.2
-libgtk1.2-common
-libgtk1.2-dev
-libgtk2.0-0
-libgtk2.0-bin
-libgtkhtml2.0
-libgtkhtml2-dev
-libgtkhtml3.8-1.5
-libgtkhtml3.8-dev
-libgtkmatview-dev
-libgtkmatview0c2a
-libgtkmm-2.3-1c2a
-libgtkmm-2.4-dev
-libgtkspell-dev
-libgtkspell0

I've installed most of them in panic trying to solve the error but nothing work.


Any ideas on what i've to do?


Thanks.

---

### Post by linuxopjemac on 2010-09-28
-libgtk1.2-dev is too old and does not fulfil the requirements for your build.

I checked the Dapper repositories and I'm afraid that you are stuck. There is no libgtk2.0-dev package. You have to upgrade Dapper to a more recent version of Ubuntu. If you insist on Ubuntu, I would go for Karmic.
[http://packages.ubuntu.com/search?suite=karmic&searchon=names&keywords=libgtk](http://packages.ubuntu.com/search?suite=karmic&searchon=names&keywords=libgtk)

---

### Post by linuxopjemac on 2010-09-28
Isn't it in the repositories for you???

[http://packages.ubuntu.com/dapper/efax-gtk](http://packages.ubuntu.com/dapper/efax-gtk)

---

### Post by RavenTK on 2010-09-28
> **linuxopjemac said:**
> Isn't it in the repositories for you???

[http://packages.ubuntu.com/dapper/efax-gtk](http://packages.ubuntu.com/dapper/efax-gtk)


Thanks,i've putted the deb link in te reposity and then install the 3.0 version well :).

Now i'm trying to install gnash but i'not able to find the rep for the powerpc version.
Does they exist? (i cannot compile a source with make on this machine... yesterday i try to compile efax 2 and,after 2 hour and 45 min i shut down it becouse it was still in "make" command...)


Thanks again.

---

### Post by linuxopjemac on 2010-09-28
Gnash is not in Dapper.
[http://packages.ubuntu.com/search?keywords=gnash](http://packages.ubuntu.com/search?keywords=gnash)

---

### Post by RavenTK on 2010-09-28
Well , thanks for all.
I think that i'll not install flash player (i've understund that the pc is also too old for it...)

Thanks.

Bye!

---

