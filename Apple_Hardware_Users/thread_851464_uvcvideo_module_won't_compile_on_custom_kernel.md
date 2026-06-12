---
title: "uvcvideo module won't compile on custom kernel"
date: 2008-07-06
forum: Apple Hardware Users
---

### Post by dustynus on 2008-07-06
I just compiled a custom 2.6.24 kernel using the gentoo config file, and mactel patches. 
It gives me these errors when I try to recompile uvcvideo for isight installation..
I'm guessing I had missed an option that would have fixed this in the .config, but I don't really know. New to compiling kernels..

```

$ ~/archives/uvcvideo-r205 $ sudo make
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-2.6.24'
  CC [M]  /home/stox/archives/uvcvideo-r205/uvc_driver.o
  LD [M]  /home/stox/archives/uvcvideo-r205/uvcvideo.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "video_device_release" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "video_usercopy" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "video_register_device" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "video_device_alloc" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "video_unregister_device" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "v4l_printk_ioctl" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "video_devdata" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "v4l_compat_ioctl32" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
  LD [M]  /home/stox/archives/uvcvideo-r205/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-2.6.24'

```

```

$ ~/archives/uvcvideo-r205 $ sudo make
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-2.6.24'
  CC [M]  /home/stox/archives/uvcvideo-r205/uvc_driver.o
  LD [M]  /home/stox/archives/uvcvideo-r205/uvcvideo.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "video_device_release" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "video_usercopy" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "video_register_device" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "video_device_alloc" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "video_unregister_device" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "v4l_printk_ioctl" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "video_devdata" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
WARNING: "v4l_compat_ioctl32" [/home/stox/archives/uvcvideo-r205/uvcvideo.ko] undefined!
  LD [M]  /home/stox/archives/uvcvideo-r205/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-2.6.24'

```

Thanks

---

### Post by cyberdork33 on 2008-07-08
look like you may have left the video4linux stuff out of your kernel.

---

