---
title: "MOL in gutsy"
date: 2008-02-03
forum: Apple PPC Users
---

### Post by fuoco on 2008-02-03
I cannot install mol right in gutsy - this is a known problem of conflicting versions in the repository which makes it badly broken.
Can someone help me get it to work in gutsy? I wasn't able to compile from source it keeps failing the build (followed the guide and installed necessary packages before compiling...)

thanks a lot

---

### Post by stmiller on 2008-02-03
Hey make sure you have the package linux-headers installed. And also the package subversion. 

Then remove the ubuntu mol packages. They are old and don't work anyway.

Issue this command in a terminal:
```

svn co http://mac-on-linux.svn.sourceforge.net/svnroot/mac-on-linux/trunk mac-on-linux

```

Then change to that directory when it finishes downloading.
```

cd mac-on-linux

```
then type
./autogen.sh
make
sudo make install

to compile and install mol. You'll need to edit the mol config files in /etc/mol/ before running.

then start OS X by issuing this as a normal user:
```

startmol -X

```

You can either create a new virtual machine of OS X, or boot up the OS X partition of a dual boot system (inside Linux).

I can post my /etc/mol/ config files if that would help.

---

### Post by fuoco on 2008-02-03
> **stmiller said:**
> Hey make sure you have the package linux-headers installed. And also the package subversion. 

Then remove the ubuntu mol packages. They are old and don't work anyway.

Issue this command in a terminal:
```

svn co http://mac-on-linux.svn.sourceforge.net/svnroot/mac-on-linux/trunk mac-on-linux

```

Then change to that directory when it finishes downloading.
```

cd mac-on-linux

```
then type
./autogen.sh
make
sudo make install

to compile and install mol. You'll need to edit the mol config files in /etc/mol/ before running.

then start OS X by issuing this as a normal user:
```

startmol -X

```

You can either create a new virtual machine of OS X, or boot up the OS X partition of a dual boot system (inside Linux).

I can post my /etc/mol/ config files if that would help.

Thanks a lot, I could successfully build and install from SVN. Unfortunately when I start 'startmol -X' I get a segmentation fault. Any idea about that? I want to run os x from a dual-boot partition - do i have to set up anything other that 'molvconfig'?

---

### Post by BladeMelbourne on 2008-02-04
I have to run "sudo startmol --osx" to start MoL.

I didn't build the latest from SVN, rather I downloaded the latest release source from October: [http://mac-on-linux.sourceforge.net/news.php](http://mac-on-linux.sourceforge.net/news.php)

You don't just need "linux-headers" - there's many other packages that you need. I think it would be helpful for you to post the results of the "./configure" and "make" commands that you run. We might be able to see some package that you are missing.

MoL is pretty awesome. Sound is a little choppy on a G4 1.42 MHz, but it starts up and shut down faster than booting OS X properly from Yaboot.

A last question... are you running OS X 10.4 or 10.5?

- Mike -

---

### Post by fuoco on 2008-02-04
> **BladeMelbourne said:**
> I have to run "sudo startmol --osx" to start MoL.

I didn't build the latest from SVN, rather I downloaded the latest release source from October: [http://mac-on-linux.sourceforge.net/news.php](http://mac-on-linux.sourceforge.net/news.php)

You don't just need "linux-headers" - there's many other packages that you need. I think it would be helpful for you to post the results of the "./configure" and "make" commands that you run. We might be able to see some package that you are missing.

MoL is pretty awesome. Sound is a little choppy on a G4 1.42 MHz, but it starts up and shut down faster than booting OS X properly from Yaboot.

A last question... are you running OS X 10.4 or 10.5?

- Mike -

Well, I'm working now on trying that compile again and will post the results when I get something. One time it did work and the resulting binary was simply segfaulting. but now it seems it requires me to compile my kernel on my own (not just have the source available) - did you need that too?

I also have G4 1.42Ghz, and it's OS X 10.4 - I mostly intend to use that for skype running - can you tell me if that works or if i'm working in vain?

---

### Post by BladeMelbourne on 2008-02-04
My G4 Mac Mini is running 10.4 too.

The primary reason I have MoL is to:
* View Flash content that doesn't work in GNASH
* Run Skype
* Test pages in Safari

I have only ever used Skype on this box for instant messaging, not for voice chat. Instant messaging works fine. Now our Mini's don't have a Mic input, so voice may be out of the question. Unless MoL could use a USB sound input/output device - I'm not sure if this is possible.

---

### Post by fuoco on 2008-02-04
> **BladeMelbourne said:**
> My G4 Mac Mini is running 10.4 too.

The primary reason I have MoL is to:
* View Flash content that doesn't work in GNASH
* Run Skype
* Test pages in Safari

I have only ever used Skype on this box for instant messaging, not for voice chat. Instant messaging works fine. Now our Mini's don't have a Mic input, so voice may be out of the question. Unless MoL could use a USB sound input/output device - I'm not sure if this is possible.

OK I still want to try it.
When I try to compile mol I get to the point of this error:

+ Entering Linux

 --- Error: Unconfigured kernel source!

make[3]: *** [kernelcheck] Error 1
make[2]: *** [sub-Linux-all] Error 2
make[1]: *** [sub-kmod-all] Error 2
make: *** [sub-src-all] Error 2


Now I do have /usr/src/linux - and i do have there a .config and all. i tried make oldconfig and stuff and nothing changes... any idea?

---

### Post by fuoco on 2008-02-04
Nevermind the last one, I made some improvement, now it fails like that:


+ Entering Linux
  AS [x]   /home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/_traps.o
  Building modules, stage 2.
WARNING: "disable_irq" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "kmalloc_caches" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "__kmalloc" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "get_zeroed_page" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "up_read" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "mem_map" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "vmalloc" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "disable_irq_nosync" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "cur_cpu_spec" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "__up" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "vfree" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "down_read" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "misc_register" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "memset" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "tb_ticks_per_jiffy" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "__copy_tofrom_user" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "printk" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "ioremap" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "mol_trampoline" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "__flush_icache_range" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "find_vma" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "capable" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "kmem_cache_alloc" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "__get_free_pages" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "request_irq" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "force_sig" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "of_get_property" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "init_waitqueue_head" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "__down" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "free_pages" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "handle_mm_fault" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "of_find_node_by_type" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "of_find_node_by_name" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "enable_irq" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "kfree" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "memcpy" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "flush_hash_pages" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "send_sig_info" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "iounmap" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "memmove" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "of_node_put" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "misc_deregister" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
WARNING: "free_irq" [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/mol.ko] undefined!
/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/_kuname.mod.c:8: error: variable ‘__this_module’ has initializer but incomplete type
/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/_kuname.mod.c:9: error: unknown field ‘name’ specified in initializer
/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/_kuname.mod.c:9: warning: excess elements in struct initializer
/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/_kuname.mod.c:9: warning: (near initialization for ‘__this_module’)
/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/_kuname.mod.c:10: error: unknown field ‘arch’ specified in initializer
/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/_kuname.mod.c:10: error: ‘MODULE_ARCH_INIT’ undeclared here (not in a function)
/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/_kuname.mod.c:10: warning: excess elements in struct initializer
/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/_kuname.mod.c:10: warning: (near initialization for ‘__this_module’)
make[5]: *** [/home/gad/prevu/mac-on-linux/obj-ppc/build/src/kmod/_kuname.mod.o] Error 1
make[4]: *** [modules] Error 2
nm: '../../../obj-ppc/build/src/kmod/Linux/..//mol.ko': No such file
nm: '../../../obj-ppc/build/src/kmod/Linux/..//mol.ko': No such file
checker.pl failed
rm: cannot remove `../../../obj-ppc/build/src/kmod/Linux/..//mol.ko': No such file or directory
make[3]: *** [all-local] Error 1
make[2]: *** [sub-Linux-all] Error 2
make[1]: *** [sub-kmod-all] Error 2
make: *** [sub-src-all] Error 2

---

### Post by anders_gud on 2008-02-05
Got it working on Gutsy... (You will need the Gutsy Mol patches)  Here is the steps:

Build a 2.6.22.9 kernel

apt-get source mol

pico -w debian/control (remove mol-drivers dependency)

dpkg-buildpackage -rfakeroot -us

install mol and mol-modules source

cd /usr/src/

unpack, build and install mol-modules

get mol from svn (see above post) and copy  Mol-0.9.72/mol-0.9.72/mollib/drivers/* to /usr/share/mol/drivers/

---

### Post by fuoco on 2008-02-06
I really can't get it right. Eventually all was built OK, but when I run it i still get a segfault. 
Then I noticed the mol.ko is not loaded - because it wasn't even installed in the modules dir, so i did that manually with depmod and all, but it won't load because of unknown symbol.
So here i'm stuck...

---

