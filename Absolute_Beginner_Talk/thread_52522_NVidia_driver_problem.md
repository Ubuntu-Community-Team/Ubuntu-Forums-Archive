---
title: "NVidia driver problem"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by daejavu on 2005-07-28
hi to all ... 
i have a big time problem with my display driver which is not getting installed at all .. 
i downloaded the latest Driver for the Nvidia graphic card from their site and when i start to install it it says something like the kernel is not supportive or some shit like that ... 
then i downloaded an old tar file (since the card is also old) unpacked the kernel headers files and tried to compile it and it says 

    "You appear to be compiling the NVdriver kernel module with
     a compiler different from the one that was used to compile
     the running kernel. This may be perfectly fine, but there
     are cases where this can lead to unexpected behaviour and
     system crashes.

     If you know what you are doing and want to override this 
     check, you can do so by setting IGNORE_CC_MISMATCH.

     In any other case, set the CC environment variable to the
     name of the compiler that was used to compile the kernel.

what to do now .. ?

---

### Post by Knome_fan on 2005-07-28
Hi,
the easiest way to install the nvidia drivers is to use the ones that come with ubuntu.
Take a look here:
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

If you want to for whatever reason to install the nvidia driver from the nvidia site, take a look at this howto:
[http://www.ubuntuforums.org/showthread.php?t=39743&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=39743&highlight=nvidia)

Hope this helps!  :grin:

---

