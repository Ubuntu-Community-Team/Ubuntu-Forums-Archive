---
title: "What is the .deb file missing defined by: ifeq (,$(KSRC))
$(kernel source not found)?"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-04-05
Hello all !!!

I have bought a Motherboard & struggling for almost a week to make its LAN work!!!

NO LAN === NO Internet...

I have made numerous threads...contacted ASUS support,...NOTHING!!!

I am trying to install the Intel Gigabit LAN drivers & get this error:

> 
root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make install

Makefile:65: *** Linux kernel source not found. Stop.

The above means that line 65 creates some error...

The code of the "Makefile" in lines 64 & 65 say this:

>  ifeq (,$(KSRC))
$(error Linux kernel source not found)

What is defined by the statement:>  ifeq (,$(KSRC))

It seems to me that:
Some "linux kernel source" - ".deb" file is Missing from My Ubuntu, but I can NOT figure out which....?

Can anybody figure out from the above, what ".deb" is missing to Install from Synaptic, write to CD & Install on the PC I want to setup its LAN?

P.S.1> If I take TOOOOO long & NOT manage to Setup the Motherboard's LAN, I will NOT be able to Return the Mobo to the PC Shop for Replacement...
Time is running against me.... PLEASE HELP!!!

P.S.2> For 2 Months now, I have been advertising my Ubuntu SOOOO Much to my Friends, encouraging them to try it out...
It would be a Personal "LOSS" situation to tell them, that I have QUIT Ubuntu & installed Windows on this PC...
They will start laughing at me & make IRONIC statements about UBUNTU...
How am I supposed to bring them IN, if I can NOT setup _MY_ Ubuntu...?
It is going to be a "DISGRACE"!!! Please HELP!!!

---

### Post by htinn on 2006-04-05
Have you just done a "make"? Have you upgraded your linux-headers to the kernel you are using?

---

### Post by dvarsam on 2006-04-05
This is what I got from the ASUS support:

[QUOTE=dvarsam]Dear Customer,

This file describes the Linux* Base Driver for the Intel(R) PRO/1000 Family
of Adapters, version 6.0.x. This driver supports the 2.4.x and 2.6.x kernels.
This driver includes support for Itanium(R)2-based systems.

This driver is only supported as a loadable module at this time.
Intel is not supplying patches against the kernel source to allow for static linking of the driver.
For questions related to hardware requirements, refer to the documentation supplied with your Intel PRO/1000 adapter.
All hardware requirements listed apply to use with Linux.

Love,

Penny
ASUS Customer Service Center (China)[/QUOTE]

Yeah, I LOVE you Too, Penny!!!

But what the f*ck am I going to do with My f*ck*ng ASUS Mobo?

Is anybody else out there from the ASUS family that loves me too?

CAUSE I love you too !!! (@%#$*(*&%)@#$^)

I have been posting for almost a week on this!!!

AND there are 4 more people having the SAME problem!!!

What does this mean:
> This driver is only supported as a loadable module at this time.
Intel is not supplying patches against the kernel source to allow for static linking of the driver.

Anybody?

My Other posts on this:

1. Article#: 102083
2. Article#: 153441
3. Article#: 154076 
4. Article#: 154532
5. Article#: 155497

Other guys that have the SAME problem like ME:

1. User: "jbellny" - Article#: 102038
2. User: "j2fraser" - Article#: 102038
3. User: "p47" - Article#: 102038
4. User: "smelly feet" - Article#: 153441 (This guy has the SAME Motherboard like Me!!!)

Please HELP!!!

IF I get this DONE - it will be like helping 5 PEOPLE - NOT just 1...

Thanks.

---

### Post by htinn on 2006-04-05
? Hello? Are you actually reading my posts?

---

### Post by dvarsam on 2006-04-05
[QUOTE=htinn]? Hello? Are you actually reading my posts?[/QUOTE]

Yes man, I appreciate!!!

This is what I get with running "make"

> 
root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make

Makefile:65: *** Linux kernel source not found.  Stop.

root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src#

Need Five minutes to tell you ror the rest...

Thanks!

---

### Post by dvarsam on 2006-04-05
I performed a "uname -r" & found that my kernel is:

> 2.6.12-9-386

But from Synaptic Manager, I see that:

a. My "linux-headers" are: > 2.6.12-9, 2.6.12-9-386 & linux-headers386 

b. My "linux-kernel-headers" are: > 2.6.11.2

So, my Ubuntu Kernel version & my "linux-kernel-headers" version are Different...

_Question_:
Do I need to "Downgrade" my Ubuntu's Kernel to proceed with the installation of my LAN's drivers?

And How would I do that?

My Ubuntu PC is a 64bit, but I have installed the Regular Desktop Ubuntu 5.10 (Gnome) Breezy.

Thanks.

---

### Post by dvarsam on 2006-04-05
I somehow managed to run "make".
Now, this is what I get:

> root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make
make: Warning: File `Makefile' has modification time 2.3e+06 s in the future
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/elena/Desktop/e1000-7.0.33/src modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[2]: Warning: File `/home/elena/Desktop/e1000-7.0.33/src/Makefile' has modification time 2.3e+06 s in the future
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_main.o
In file included from include/asm/system.h:5,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:17,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:37,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/linux/kernel.h:10:20: error: stdarg.h: No such file or directory
In file included from include/asm/system.h:5,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:17,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:37,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/linux/kernel.h:94: error: syntax error before 'va_list'
include/linux/kernel.h:95: warning: function declaration isn't a prototype
include/linux/kernel.h:98: error: syntax error before 'va_list'
include/linux/kernel.h:99: warning: function declaration isn't a prototype
include/linux/kernel.h:102: error: syntax error before 'va_list'
include/linux/kernel.h:103: warning: function declaration isn't a prototype
include/linux/kernel.h:107: error: syntax error before 'va_list'
include/linux/kernel.h:108: warning: function declaration isn't a prototype
include/linux/kernel.h:119: error: syntax error before 'va_list'
include/linux/kernel.h:120: warning: function declaration isn't a prototype
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c: In function 'e1000_set_mac':
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:2086: warning: pointer targets in passing argument 1 of 'is_valid_ether_addr' differ in signedness
make[2]: *** [/home/elena/Desktop/e1000-7.0.33/src/e1000_main.o] Error 1
make[1]: *** [_module_/home/elena/Desktop/e1000-7.0.33/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [default] Error 2

Any ideas?

---

### Post by halfvolle melk on 2006-04-05
Hey dvarsam,
Haven't got a clue how fix the compiling issues, but maybe it's an idea to check out the Dapper live cd and see if that supports your hardware out of the box. If so it might save you a lot of headaches.

---

### Post by dvarsam on 2006-04-05
[QUOTE=halfvolle melk]Hey dvarsam,
Haven't got a clue how fix the compiling issues, but maybe it's an idea to check out the Dapper live cd and see if that supports your hardware out of the box. If so it might save you a lot of headaches.[/QUOTE]

Dear "halfvolle melk",

Thank you for your repply, maybe I will!

Where would I go to download the ".iso"?


_At the same time, I had some progress_:

I have installed the following packages:

> 1. build-essential
2. cpp-3.4_3.4.4-6ubuntu8.1_i386.deb
3. gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb
4. gcc-3.4_3.4.4-6ubuntu8.1_i386.deb
5. linux-source-2.6.12_2.6.12-10.30_all.deb
6. linux-headers-2.6.12-10_2.6.12-10.30_i386.deb
7. linux-headers-2.6.12-10-386_2.6.12-10.30_i386.deb
8. linux-headers-386_2.6.12.16.1_i386.deb
9. linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb

Now by typing "make", I get the following:

root@ubuntu:/home/elena/Desktop# cd e1000*
root@ubuntu:/home/elena/Desktop/e1000-7.0.33# cd src
root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make

> make: Warning: File `Makefile' has modification time 2.3e+06 s in the future
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/elena/Desktop/e1000-7.0.33/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[2]: Warning: File `/home/elena/Desktop/e1000-7.0.33/src/Makefile' has modification time 2.3e+06 s in the future
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_main.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c: In function 'e1000_set_mac':
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:2086: warning: pointer targets in passing argument 1 of 'is_valid_ether_addr' differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/kcompat.h:37,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_osdep.h:43,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.h:36,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.c:33:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_param.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:29:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:29:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c: At top level:
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:78: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:88: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:101: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:113: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:130: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:143: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:155: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:164: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:173: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:182: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:191: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:200: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c: In function 'e1000_check_options':
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:339: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:369: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:445: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:467: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:489: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:511: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:543: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.c:31:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.c:31:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/kcompat.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/kcompat.h:37,
                 from /home/elena/Desktop/e1000-7.0.33/src/kcompat.c:29:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  LD [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000.o
make[2]: warning:  Clock skew detected.  Your build may be incomplete.
  Building modules, stage 2.
  MODPOST
  CC      /home/elena/Desktop/e1000-7.0.33/src/e1000.mod.o
  LD [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: warning:  Clock skew detected.  Your build may be incomplete.

Does anybody know what do I do with this error message?

Thanks.

---

### Post by dvarsam on 2006-04-05
Should I repost, cause the Subject Title is Misleading now...

Now the Subject Title should be:

"Make" Error: "warning: Clock skew detected. Your build may be incomplete."

What do you think?

P.S.> There are many times where I wish I could change the Subject of My Post in this Forum...
You see, when a solution to a problem is in progress, issues/questions change & there is NO way to correct the Beginning Thread's "Subject Title"...
It would be nice if the Author could change that...

---

