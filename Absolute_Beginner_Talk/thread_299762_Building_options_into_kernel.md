---
title: "Building options into kernel"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by sailingboarder on 2006-11-14
I am trying to get my infrared up and running on ubuntu, to sync with my palm pilot
the infrared is built into my IBM Thinkpad A22m
i found a HOWTO at [http://howto.pilot-link.org/irdasync/index.html]("http://howto.pilot-link.org/irdasync/index.html")

it said that i need to rebuild the kernel with certain options enabled
 > If you want to include kernel support for IrDA, you can rebuild your kernel with the following options enabled in your .config file in your Linux kernel source directory:

    CONFIG_IRDA=m
    CONFIG_IRCOMM=m
    CONFIG_IRDA_OPTIONS=y
    CONFIG_IRDA_CACHE_LAST_LSAP=y
    CONFIG_IRDA_FAST_RR=y
    CONFIG_IRDA_DEBUG=y
Do these options come default in dapper, or do i need to rebuild the kernel myself
also, this guide may be alittle out of date
if anyone knows of a better place to find information about infrared and palm pilots, i would appreciate it

---

