---
title: "Building Mac-On-Linux"
date: 2010-03-30
forum: Apple Hardware Users
---

### Post by Necrom@ncer on 2010-03-30
Okay, I tried the instructions on MOl's wiki ```
apt-get install libc6-dev ncurses-dev zlib1g-dev libasound2-dev xlibs-dev libpng12-dev libxxf86dga-dev automake autoconf

```
But I got this spit back at me: ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6-dev is already the newest version.
Note, selecting libncurses5-dev instead of ncurses-dev
libncurses5-dev is already the newest version.
zlib1g-dev is already the newest version.
Package xlibs-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xlibs-dev has no installation candidate
```

Doing the install procedure anyways?:  ```
make
config.status: creating unconfig
config.status: creating Makefile.defs
config.status: creating config.h
config.status: config.h is unchanged
+ Entering scripts
+ Entering src
+ Entering lib
    Compiling    extralib.o          
    Compiling    llseek.o            
    Compiling    elfload.o           
    Compiling    unicode.o           
    Compiling    backtrace.o         
backtrace.c: In function ‘print_btrace_sym’:
backtrace.c:36: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
    Linking      libcommon.a           
+ Entering main
+ Entering linux
    Compiling    misc.o              
    Linking      libarch.a             
    Compiling    res_manager.o       
    Compiling    molrcget.o          
= Building molrcget              
/usr/bin/ld: Warning: ../../obj-ppc/build/src/main/molrcget uses hard float, ../../obj-ppc/build/src/main/res_manager.o uses soft float
/usr/bin/ld: Warning: ../../obj-ppc/build/src/main/molrcget uses hard float, ../../obj-ppc/build/src/main/molrcget.o uses soft float
    Linking      libres.a              
    Compiling    async.o             
async.c: In function ‘async_cleanup’:
async.c:357: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
    Compiling    main.o              
    Compiling    memory.o            
    Compiling    os_interface.o      
    Compiling    promif.o            
promif.c: In function ‘import_node’:
promif.c:1102: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
    Compiling    session.o           
session.c: In function ‘session_is_loaded’:
session.c:254: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
session.c:259: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
    Compiling    thread.o            
thread.c: In function ‘create_thread’:
thread.c:145: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
thread.c: In function ‘threadpool_init’:
thread.c:175: warning: ignoring return value of ‘pipe’, declared with attribute warn_unused_result
thread.c: In function ‘threadpool_cleanup’:
thread.c:194: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
    Compiling    timer.o             
timer.c: In function ‘doze’:
timer.c:438: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
timer.c: In function ‘abort_doze’:
timer.c:450: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
timer.c: In function ‘timer_init’:
timer.c:574: warning: ignoring return value of ‘pipe’, declared with attribute warn_unused_result
    Linking      libmain.a             
+ Entering drivers
+ Entering disk
    Compiling    blkdev.o            
blkdev.c: In function ‘find_disk_type’:
blkdev.c:101: warning: dereferencing type-punned pointer will break strict-aliasing rules
blkdev.c: In function ‘inspect_disk’:
blkdev.c:150: warning: dereferencing type-punned pointer will break strict-aliasing rules
blkdev.c:168: warning: dereferencing type-punned pointer will break strict-aliasing rules
    Compiling    disk_open.o         
    Compiling    ablk.o              
ablk.c: In function ‘io_thread’:
ablk.c:230: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
ablk.c: In function ‘osip_ablk_kick’:
ablk.c:256: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
ablk.c: In function ‘ablk_init’:
ablk.c:521: warning: ignoring return value of ‘pipe’, declared with attribute warn_unused_result
ablk.c: In function ‘ablk_cleanup’:
ablk.c:536: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
    Compiling    pseudofs.o          
    Compiling    scsi.o              
    Compiling    blk_raw.o           
    Compiling    blk_qcow.o          
blk_qcow.c: In function ‘get_cluster_offset’:
blk_qcow.c:276: warning: ignoring return value of ‘ftruncate’, declared with attribute warn_unused_result
    Compiling    vec_wrap.o          
    Compiling    blk_dmg.o           
In file included from ./include/blk_dmg.h:37,
                 from blk_dmg.c:30:
/usr/include/zlib.h:1374: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gzseek64’
/usr/include/zlib.h:1375: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gztell64’
/usr/include/zlib.h:1376: error: expected declaration specifiers or ‘...’ before ‘off64_t’
/usr/include/zlib.h:1377: error: expected declaration specifiers or ‘...’ before ‘off64_t’
make[3]: *** [../../../obj-ppc/build/src/drivers/disk/blk_dmg.o] Error 1
make[2]: *** [sub-disk-all] Error 2
make[1]: *** [sub-drivers-all] Error 2
make: *** [sub-src-all] Error 2

```


Can somebody tell me what I need to do?

---

### Post by Necrom@ncer on 2010-03-31
Push, I need some help please!?

---

### Post by shongzah on 2010-06-26
FWIW, I could use some help as well. I didn't go over it with a fine toothed comb, but the results look similar to my own. I tried to install through the conventional channels but I had no luck. Got a message saying that Mac On Linux drivers for OSX has un-met dependancies. Help, Help. Has anyone made this work?

---

### Post by oswaldkelso on 2010-06-26
Mol works in lenny, (or it did) This may give you some hints

[http://www.mail-archive.com/debian-p.../msg60060.html](http://www.mail-archive.com/debian-p.../msg60060.html)

[http://ubuntuforums.org/showthread.php?t=1441492&highlight=MOL](http://ubuntuforums.org/showthread.php?t=1441492&highlight=MOL)

---

### Post by shongzah on 2010-06-28
The first link you posted got broken somehow. I managed to track it down elsewhere: [http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg60060.html](http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg60060.html)

---

