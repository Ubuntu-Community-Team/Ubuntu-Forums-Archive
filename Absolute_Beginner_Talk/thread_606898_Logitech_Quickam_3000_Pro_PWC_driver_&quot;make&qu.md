---
title: "Logitech Quickam 3000 Pro PWC driver &quot;make&quot; error"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2007-11-08
I am running Gutsy (kernel: 2.6.22-14-generic).

I have a logitech quickcam 3000 pro.

While I had fiesty I tried getting my cam to work using the pwc driver and I remember it working briefly. But after that I gave up as skype did not even have a video option. Now that skype has that option I want to get my cam working again.

So I went to the pwc site and downloaded the latest one: pwc-10.0.12-rc1.

I followed the instructions, unpacked the tarball and did make and this is what I get:

```

make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/abhiroop/Desktop/pwc-10.0.12-rc1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.o
In file included from /home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:69:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc.h:28:26: error: linux/config.h: No such file or directory
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:166: error: variable &#8216;pwc_template&#8217; has initializer but incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:167: error: unknown field &#8216;owner&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:167: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:167: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:168: error: unknown field &#8216;name&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:168: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:168: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:169: error: unknown field &#8216;type&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:169: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:169: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:170: error: unknown field &#8216;hardware&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:170: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:170: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: error: unknown field &#8216;release&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: error: &#8216;video_device_release&#8217; undeclared here (not in a function)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:172: error: unknown field &#8216;fops&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:172: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:172: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:173: error: unknown field &#8216;minor&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:173: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:173: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_isoc_init&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:921: warning: assignment from incompatible pointer type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;cd_to_pwc&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1019: warning: implicit declaration of function &#8216;to_video_device&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1019: warning: initialization makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1020: warning: implicit declaration of function &#8216;video_get_drvdata&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1020: warning: return makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_create_sysfs_files&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1062: warning: initialization makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1064: warning: implicit declaration of function &#8216;video_device_create_file&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_remove_sysfs_files&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1070: warning: initialization makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1072: warning: implicit declaration of function &#8216;video_device_remove_file&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_open&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1112: warning: implicit declaration of function &#8216;video_devdata&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1112: warning: initialization makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1117: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_close&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1231: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_read&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1292: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_poll&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1359: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_ioctl&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1375: warning: implicit declaration of function &#8216;video_usercopy&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_mmap&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1388: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;usb_pwc_probe&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1722: warning: implicit declaration of function &#8216;video_device_alloc&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1722: warning: assignment makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1730: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1731: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1732: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1733: warning: implicit declaration of function &#8216;video_set_drvdata&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1756: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: warning: implicit declaration of function &#8216;video_register_device&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: error: &#8216;VFL_TYPE_GRABBER&#8217; undeclared (first use in this function)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: error: (Each undeclared identifier is reported only once
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: error: for each function it appears in.)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1760: warning: implicit declaration of function &#8216;video_device_release&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1765: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;usb_pwc_disconnect&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1819: warning: implicit declaration of function &#8216;video_unregister_device&#8217;
make[2]: *** [/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.o] Error 1
make[1]: *** [_module_/home/abhiroop/Desktop/pwc-10.0.12-rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

```

any ideas as to what I should do? really want this cam working.

When I just plug the cam in the green light stays on and doing lsusb shows:

```

Bus 003 Device 004: ID 1241:1503 Belkin 
Bus 003 Device 003: ID 09da:022b A4 Tech Co., Ltd 
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:08b0 Logitech, Inc. QuickCam 3000 Pro [pwc]
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

So it has been detected, but where do I go from here?

Skype is showing "no video devices".

---

### Post by abhiroopb on 2007-11-11
bump...

---

### Post by aug_aug on 2007-11-12
I have the same problem, black screen in Skype with ATI mobility video card. Any success at all? :(:-({|=

---

### Post by abhiroopb on 2007-11-12
i solved the problem on this thread...

[http://ubuntuforums.org/showthread.php?t=610847](http://ubuntuforums.org/showthread.php?t=610847)

but unfortunately my cam still isn't getting detected. It shows up on lsusb but I don't know what to do from there as it doesn't show up on skype.

---

