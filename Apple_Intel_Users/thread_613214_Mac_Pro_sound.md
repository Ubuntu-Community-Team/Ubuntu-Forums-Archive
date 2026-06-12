---
title: "Mac Pro sound"
date: 2007-11-14
forum: Apple Intel Users
---

### Post by uidzer0 on 2007-11-14
Hey everyone,

I just installed ubuntu 7.10 on my mac pro however, I can _barely_ hear the sound. I can only hear a faint noise when I go into the gnome sound settings and click test. I get a faint humming noise there. I used alsamixer to max out all of the volume settings. Can anyone shed some light on this?

Thanks!

Ben

---

### Post by cyberdork33 on 2007-11-14
Some others have mentioned this in the forum. I thought there was a fix, but I can't seem to find it.

Look here for info:
[http://macprolinux.blogspot.com/](http://macprolinux.blogspot.com/)

[http://gentoo-wiki.com/MacPro](http://gentoo-wiki.com/MacPro)

[http://ubuntuforums.org/showthread.php?t=578698](http://ubuntuforums.org/showthread.php?t=578698)

This one is old, so might be best to skip to the end:
[http://ubuntuforums.org/showthread.php?t=234676](http://ubuntuforums.org/showthread.php?t=234676)

EDIT: Found it!
[http://ubuntuforums.org/showthread.php?t=518391](http://ubuntuforums.org/showthread.php?t=518391)

---

### Post by uidzer0 on 2007-11-15
> **cyberdork33 said:**
> 

EDIT: Found it!
[http://ubuntuforums.org/showthread.php?t=518391](http://ubuntuforums.org/showthread.php?t=518391)

Hey there, thanks for the reply. 

I attempted to build the latest alsa package from source and got the following:

```

if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
cp -auvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make  dep
make[1]: Entering directory `/Users/benl/alsa-driver-1.0.9rc4a'
make[2]: Entering directory `/Users/benl/alsa-driver-1.0.9rc4a/acore'
make  -C ioctl32 fastdep
make[3]: Entering directory `/Users/benl/alsa-driver-1.0.9rc4a/acore/ioctl32'
/Users/benl/alsa-driver-1.0.9rc4a/include/sndversions.h was updated
gcc -M -D__KERNEL__ -D__isapnp_now__ -DMODULE=1 -I/Users/benl/alsa-driver-1.0.9rc4a/include  -I/lib/modules/2.6.22-14-rt/build/include -O2 -mno-red-zone -mcmodel=kernel -fno-reorder-blocks -fno-strength-reduce -finline-limit=2000 -D__SMP__ -DCONFIG_SMP -DLINUX -DALSA_BUILD -nostdinc -iwithprefix include  ioctl32.c pcm32.c rawmidi32.c timer32.c hwdep32.c seq32.c > .depend
ioctl32.c:1:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/notifier.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/memory_hotplug.h:7,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/mmzone.h:466,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.22-14-rt/build/include/asm/local.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/module.h:19,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from ioctl32_new.c:21,
                 from ioctl32.c:27:
/lib/modules/2.6.22-14-rt/build/include/linux/rwsem.h:39:66: error: asm/rwsem.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/sched.h:57,
                 from ioctl32_new.c:22,
                 from ioctl32.c:27:
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
pcm32.c:2:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/notifier.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/memory_hotplug.h:7,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/mmzone.h:466,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.22-14-rt/build/include/asm/local.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/module.h:19,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from pcm32_new.c:21,
                 from pcm32.c:16:
/lib/modules/2.6.22-14-rt/build/include/linux/rwsem.h:39:66: error: asm/rwsem.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/sched.h:57,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/sound/core.h:25,
                 from pcm32_new.c:25,
                 from pcm32.c:16:
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
rawmidi32.c:2:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/notifier.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/memory_hotplug.h:7,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/mmzone.h:466,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.22-14-rt/build/include/asm/local.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/module.h:19,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from rawmidi32_new.c:21,
                 from rawmidi32.c:16:
/lib/modules/2.6.22-14-rt/build/include/linux/rwsem.h:39:66: error: asm/rwsem.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/sched.h:57,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/barrier.h:22,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/fs.h:287,
                 from rawmidi32_new.c:23,
                 from rawmidi32.c:16:
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
timer32.c:2:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/notifier.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/memory_hotplug.h:7,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/mmzone.h:466,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.22-14-rt/build/include/asm/local.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/module.h:19,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from timer32_new.c:21,
                 from timer32.c:16:
/lib/modules/2.6.22-14-rt/build/include/linux/rwsem.h:39:66: error: asm/rwsem.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/sched.h:57,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/barrier.h:22,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/fs.h:287,
                 from timer32_new.c:23,
                 from timer32.c:16:
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
hwdep32.c:2:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/notifier.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/memory_hotplug.h:7,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/mmzone.h:466,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.22-14-rt/build/include/asm/local.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/module.h:19,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hwdep32_new.c:21,
                 from hwdep32.c:16:
/lib/modules/2.6.22-14-rt/build/include/linux/rwsem.h:39:66: error: asm/rwsem.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/sched.h:57,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/barrier.h:22,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/fs.h:287,
                 from hwdep32_new.c:23,
                 from hwdep32.c:16:
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
seq32.c:2:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/notifier.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/memory_hotplug.h:7,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/mmzone.h:466,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.22-14-rt/build/include/asm/local.h:4,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/module.h:19,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /Users/benl/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from seq32_new.c:21,
                 from seq32.c:16:
/lib/modules/2.6.22-14-rt/build/include/linux/rwsem.h:39:66: error: asm/rwsem.h: No such file or directory
In file included from /lib/modules/2.6.22-14-rt/build/include/linux/sched.h:57,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/barrier.h:22,
                 from /lib/modules/2.6.22-14-rt/build/include/linux/fs.h:287,
                 from seq32_new.c:23,
                 from seq32.c:16:
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
/lib/modules/2.6.22-14-rt/build/include/linux/jiffies.h:219:31: error: division by zero in #if
make[3]: *** [fastdep] Error 1
make[3]: Leaving directory `/Users/benl/alsa-driver-1.0.9rc4a/acore/ioctl32'
make[2]: *** [_sfdep_ioctl32] Error 2
make[2]: Leaving directory `/Users/benl/alsa-driver-1.0.9rc4a/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/Users/benl/alsa-driver-1.0.9rc4a'
make: *** [include/sndversions.h] Error 2

```

I tried to compile with previous versions of alsa and got the same error. What am I missing here?

Thanks!

Ben

---

### Post by uidzer0 on 2007-11-15
Never mind that! I got the package to build but I'm not sure how to get the module to load. After running make install I restarted but I've still got the same _verrry_ low sound.

Any ideas?

---

### Post by cyberdork33 on 2007-11-15
Looks like you were trying to build an older version.... 1.0.9rc4a. Latest is 1.0.15

try ```
sudo depmod -a
``` then reboot again.

---

### Post by uidzer0 on 2007-11-15
Ok I just realized that my problem is that the _front_ headphone jack is what isn't working properly. When plugged into the rear is works just fine. Is there any known fixes for this?

---

### Post by cyberdork33 on 2007-11-16
> **uidzer0 said:**
> Ok I just realized that my problem is that the _front_ headphone jack is what isn't working properly. When plugged into the rear is works just fine. Is there any known fixes for this?

Oh yea that was mentioned. The biggest issue with sound on the Macs now is getting audio channels to control the correct piece of hardware. The headphone jacks have been kind of low priority since everyone is trying to get sound to work at all.

There is a user named nicfagn that has been working on patches for these types of issues, he might be able to help.

---

### Post by kkalinux on 2007-11-17
> **uidzer0 said:**
> Hey everyone,

I just installed ubuntu 7.10 on my mac pro however, I can _barely_ hear the sound. I can only hear a faint noise when I go into the gnome sound settings and click test. I get a faint humming noise there. I used alsamixer to max out all of the volume settings. Can anyone shed some light on this?

Thanks!

Ben

Hi Ben,

I also had that same problem with the previous version of Ubuntu. With the Gutsy version the sound it right on my Mac Pro Quadcore. 

Hope you all don't flame me but I am really a Fedora user but give Ubuntu/Kubuntu a try every so often.  I will say that this version is impressive. :)

Kurt

---

