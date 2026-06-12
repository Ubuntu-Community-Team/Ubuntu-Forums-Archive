---
title: "Evolution 2.8.1 Install"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by eeverson on 2006-10-19
Hi,

I am not sure if this is the right forum for this? I am pretty new to Ubuntu and Linux...

I am trying to install Evolution 2.8.1. I have run the ./configure and it gets to the following point and then drops out? Can anyone give me some guidance on how to get past this? I have checked and Camel is installed?

Cheers
Euge

------------------------------------
...
checking for HAL_CFLAGS...
checking for HAL_LIBS...
checking for CAMEL_CFLAGS... -I/usr/include/evolution-data-server-1.6
checking for CAMEL_LIBS... -lcamel-1.2 -lcamel-provider-1.2 -ledataserver-1.2
checking for CAMEL_GROUPWISE_CFLAGS...
checking for CAMEL_GROUPWISE_LIBS...
configure: error: Package requirements (camel-provider-1.2 libedataserver-1.2 >= 1.7.90 libegroupwise-1.2 >= 1.7.90) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the CAMEL_GROUPWISE_CFLAGS and CAMEL_GROUPWISE_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
---------------------------------------------------

---

### Post by sv452 on 2006-10-19
hay - i am happy to notice i am not the only one with these issues !!

i do hope someone can provide some info regarding this.

:D

---

### Post by rlozano on 2006-10-21
i dont think Evo upgrade from 2.6 to 2.8 is possible if you are using dapper.  dapper is using gnome 2.6.

you can switch to edgy if you want to use evo 2.8. :-k

---

