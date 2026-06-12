---
title: "Updating irssi"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Shack on 2007-07-16
Hi.

I tried to update my irssi. My current version is 0.8.10 and I saw that there's 0.8.11 available throught [www.irssi.org](www.irssi.org).

When I used sudo apt-get install irssi I got message that I already have the latest version. 
Then I downloaded new irssi from [www.irssi.org](www.irssi.org) and when I tried to install it I got this.

./configure

all above wen't fine but
.........................................
.............................................
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.13.0, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
*** trying without -lgmodule
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.13.0, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
checking for glib-config... no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
*** trying without -lgmodule
checking for glib-config... (cached) no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.

*** If you don't have GLIB, you can get it from [ftp://ftp.gtk.org/pub/glib/](ftp://ftp.gtk.org/pub/glib/)
*** We recommend you get the latest stable GLIB 2 version.
*** Compile and install it, and make sure pkg-config finds it,
*** by adding the path where the .pc file is located to PKG_CONFIG_PATH

-----------------------------------------------------------------------------------------------------------------

What should I do, how can I make my apt-get install to work? 

Thanks.

---

### Post by felicity on 2007-07-16
The apt repositories don't always have the latest versions of software, especially if the software is a new release. 

To manually install, check the README or INSTALL file that comes with the software as it might have special requirements. 

In this case it looks like you need to update your Glib or possibly change the path.

This might work:

```

sudo apt-get install libglib2.0-0

```

If it says you already have it installed, you might need to change the path, check the INSTALL file with irssi for that.

---

### Post by Shack on 2007-07-16
> **felicity said:**
> The apt repositories don't always have the latest versions of software, especially if the software is a new release. 

To manually install, check the README or INSTALL file that comes with the software as it might have special requirements. 

In this case it looks like you need to update your Glib or possibly change the path.

This might work:

```

sudo apt-get install libglib2.0-0

```

If it says you already have it installed, you might need to change the path, check the INSTALL file with irssi for that.

I tried like you told, but with same results. Thanks for your help, but I'm still stuck here :(
BTW: Last night I downloaded glib2 and installed it wen't fine but I'm still having problem with this irssi install.

---

### Post by Shack on 2007-07-17
Any1? Please.

---

### Post by andrew.46 on 2007-08-25
Hi,

 I saw your plea:

> **Shack said:**
> Any1? Please.

 Possibly what you are missing is the dev file which is probably libglib2.0-dev (this is the version available for dapper. To find the version specific to your version of Ubuntu try:

```
apt-cache search libglib2 | grep Development 
```

 All the best,

     Andrew

---

