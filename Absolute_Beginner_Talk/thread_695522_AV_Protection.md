---
title: "AV Protection"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by b10nutz on 2008-02-13
1.From what i can read on this forum,i got to the conclusion that the only thing i have to use to protect my PC from virus is to configurate my firewall, is that true??

2.So if i use: [Bitdefender Antivirus Scaner]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html") (u can request a free lincese) it woud be just a waste of resouces?

---

### Post by SteveHillier on 2008-02-13
> **b10nutz said:**
> 1.From what i can read on this forum,i got to the conclusion that the only thing i have to use to protect my PC from virus is to configurate my firewall, is that true??

2.So if i use: [Bitdefender Antivirus Scaner]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html") (u can request a free lincese) it woud be just a waste of resouces?

A firewall will not protect against a virus.  It does protect against intrusions by other less scrupulous people.  It isolates your machine from the rest of the world with the exception of that traffic that YOU allow through in either direction.
The thing about Linux is that you really don't need an anti virus, there are very few out there that attack a Linux based machine because they won't install without user acceptance (which is the exact opposite to the Windows world pre Vista).  If you are paranoid then there is a Panda offering try [www.pandasoftware.com](www.pandasoftware.com) to investigate.

---

### Post by kpkeerthi on 2008-02-13
A firewall will not protect you from viruses. It stops unauthorized access from and to your system unless configured to allow. 

Ubuntu has firewall built-in (iptables). By default, it blocks all inbound connections and lets all outbound connections. Firestarter is a nice GUI to iptables.

I have not heard of any linux virus destroying a linux system. But most of the AV for linux are good at cleaning windows viruses. So you may need one if you share a lot of files with windows folks.

---

### Post by NIT006.5 on 2008-02-13
I've never run any AV on Linux before and I'm yet to see a virus even "try" to infect my PC. However, unless you're short of resources already, it might still be an idea to run something decent. I've been meaning to, but it's not a major priority.

---

### Post by _aXXe_ on 2008-04-07
> **SteveHillier said:**
> A firewall will not protect against a virus.  It does protect against intrusions by other less scrupulous people.  It isolates your machine from the rest of the world with the exception of that traffic that YOU allow through in either direction.
The thing about Linux is that you really don't need an anti virus, there are very few out there that attack a Linux based machine because they won't install without user acceptance (which is the exact opposite to the Windows world pre Vista).  If you are paranoid then there is a Panda offering try [www.pandasoftware.com](www.pandasoftware.com) to investigate.

I'm trying to install the Panda Anti Virus because I used it in Windows and I DO interact with many windows users. Plus I like the idea of having the mail checked. I have 12 E Mail addresses so I like to be sure nothing is trying to sneak in. I do look at the from and subject so most of the offending/suspicious E Mails are dumped by me before I open them.

When I try to install, I get this:

Verifying archive integrity... All good.
Uncompressing DesktopSecure for Linux 1.00.00...............................................................................................
Setting variable installation_type to value typical
In file included from /tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:20:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:479: warning: initialization from incompatible pointer typeSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:480: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:484: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:503: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:519: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:523: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:527: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:528: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:532: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:536: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:537: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:541: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:545: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:548: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:551: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:552: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:553: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:554: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:581: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:605: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:612: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:627: error: unknown field ‘socket_getpeersec’ specified in initializer
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_sb_statfs’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:280: warning: passing argument 1 of ‘dazuko_security_ops.sb_statfs’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:280: warning: passing argument 1 of ‘dazuko_security_default_ops.sb_statfs’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_create’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:366: warning: passing argument 3 of ‘dazuko_security_ops.inode_create’ makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:366: error: too few arguments to function ‘dazuko_security_ops.inode_create’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:366: warning: passing argument 3 of ‘dazuko_security_default_ops.inode_create’ makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:366: error: too few arguments to function ‘dazuko_security_default_ops.inode_create’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_link’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: warning: passing argument 2 of ‘dazuko_security_ops.inode_link’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: warning: passing argument 3 of ‘dazuko_security_ops.inode_link’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: error: too few arguments to function ‘dazuko_security_ops.inode_link’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: warning: passing argument 2 of ‘dazuko_security_default_ops.inode_link’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: warning: passing argument 3 of ‘dazuko_security_default_ops.inode_link’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: error: too few arguments to function ‘dazuko_security_default_ops.inode_link’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_unlink’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:394: error: too few arguments to function ‘dazuko_security_ops.inode_unlink’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:394: error: too few arguments to function ‘dazuko_security_default_ops.inode_unlink’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_symlink’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:401: warning: passing argument 3 of ‘dazuko_security_ops.inode_symlink’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:401: error: too few arguments to function ‘dazuko_security_ops.inode_symlink’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:401: warning: passing argument 3 of ‘dazuko_security_default_ops.inode_symlink’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:401: error: too few arguments to function ‘dazuko_security_default_ops.inode_symlink’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_mkdir’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:415: warning: passing argument 3 of ‘dazuko_security_ops.inode_mkdir’ makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:415: error: too few arguments to function ‘dazuko_security_ops.inode_mkdir’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:415: warning: passing argument 3 of ‘dazuko_security_default_ops.inode_mkdir’ makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:415: error: too few arguments to function ‘dazuko_security_default_ops.inode_mkdir’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_rmdir’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:429: error: too few arguments to function ‘dazuko_security_ops.inode_rmdir’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:429: error: too few arguments to function ‘dazuko_security_default_ops.inode_rmdir’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_mknod’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:436: warning: passing argument 3 of ‘dazuko_security_ops.inode_mknod’ makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:436: error: too few arguments to function ‘dazuko_security_ops.inode_mknod’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:436: warning: passing argument 3 of ‘dazuko_security_default_ops.inode_mknod’ makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:436: error: too few arguments to function ‘dazuko_security_default_ops.inode_mknod’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_rename’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: warning: passing argument 3 of ‘dazuko_security_ops.inode_rename’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: warning: passing argument 4 of ‘dazuko_security_ops.inode_rename’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: error: too few arguments to function ‘dazuko_security_ops.inode_rename’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: warning: passing argument 3 of ‘dazuko_security_default_ops.inode_rename’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: warning: passing argument 4 of ‘dazuko_security_default_ops.inode_rename’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: error: too few arguments to function ‘dazuko_security_default_ops.inode_rename’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_readlink’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:464: error: too few arguments to function ‘dazuko_security_ops.inode_readlink’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:464: error: too few arguments to function ‘dazuko_security_default_ops.inode_readlink’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_setattr’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:485: warning: passing argument 2 of ‘dazuko_security_ops.inode_setattr’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:485: error: too few arguments to function ‘dazuko_security_ops.inode_setattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:485: warning: passing argument 2 of ‘dazuko_security_default_ops.inode_setattr’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:485: error: too few arguments to function ‘dazuko_security_default_ops.inode_setattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_setxattr’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: warning: passing argument 2 of ‘dazuko_security_ops.inode_setxattr’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: warning: passing argument 4 of ‘dazuko_security_ops.inode_setxattr’ makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: error: too few arguments to function ‘dazuko_security_ops.inode_setxattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: warning: passing argument 2 of ‘dazuko_security_default_ops.inode_setxattr’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: warning: passing argument 4 of ‘dazuko_security_default_ops.inode_setxattr’ makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: error: too few arguments to function ‘dazuko_security_default_ops.inode_setxattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_post_setxattr’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: warning: passing argument 2 of ‘dazuko_security_ops.inode_post_setxattr’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: warning: passing argument 4 of ‘dazuko_security_ops.inode_post_setxattr’ makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: error: too few arguments to function ‘dazuko_security_ops.inode_post_setxattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: warning: passing argument 2 of ‘dazuko_security_default_ops.inode_post_setxattr’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: warning: passing argument 4 of ‘dazuko_security_default_ops.inode_post_setxattr’ makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: error: too few arguments to function ‘dazuko_security_default_ops.inode_post_setxattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_getxattr’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:522: warning: passing argument 2 of ‘dazuko_security_ops.inode_getxattr’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:522: error: too few arguments to function ‘dazuko_security_ops.inode_getxattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:522: warning: passing argument 2 of ‘dazuko_security_default_ops.inode_getxattr’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:522: error: too few arguments to function ‘dazuko_security_default_ops.inode_getxattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_listxattr’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:529: error: too few arguments to function ‘dazuko_security_ops.inode_listxattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:529: error: too few arguments to function ‘dazuko_security_default_ops.inode_listxattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_inode_removexattr’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:537: warning: passing argument 2 of ‘dazuko_security_ops.inode_removexattr’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:537: error: too few arguments to function ‘dazuko_security_ops.inode_removexattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:537: warning: passing argument 2 of ‘dazuko_security_default_ops.inode_removexattr’ from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:537: error: too few arguments to function ‘dazuko_security_default_ops.inode_removexattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_task_kill’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:813: error: too few arguments to function ‘dazuko_security_ops.task_kill’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:813: error: too few arguments to function ‘dazuko_security_default_ops.task_kill’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_getprocattr’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:983: error: too many arguments to function ‘dazuko_security_ops.getprocattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:983: error: too many arguments to function ‘dazuko_security_default_ops.getprocattr’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_netlink_recv’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1016: error: too few arguments to function ‘dazuko_security_ops.netlink_recv’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1016: error: too few arguments to function ‘dazuko_security_default_ops.netlink_recv’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1018: error: too few arguments to function ‘cap_netlink_recv’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function ‘dazuko_security_socket_getpeersec’:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1197: error: ‘struct security_operations’ has no member named ‘socket_getpeersec’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1197: error: ‘struct security_operations’ has no member named ‘socket_getpeersec’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1197: error: ‘struct security_operations’ has no member named ‘socket_getpeersec’
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1197: error: ‘struct security_operations’ has no member named ‘socket_getpeersec’
make[2]: *** [/tmp/dazuko-2.1.1/dazuko_linux26_lsm.o] Error 1
make[1]: *** [_module_/tmp/dazuko-2.1.1] Error 2
make: *** [dummy_rule] Error 2

Then the Panda DesktopSecure for Linux Installation screen shows this:
Installation Complete

Cannot install the automatic file protection module. This may be caused by several reasons.

You haven't installed the compiler for your kernel

You haven't install the correct kernel headers

You haven't installed the necessary development tools

SELinux is active on your system


My kernel is is the generic 2.16.22-14 (I think that's right) and as for the other in the list I have no idea. I wish more information from the installer.

So, how do I make sure all the above are corrected and which (if any) compiler, kernel headers and development tools do I find and install? As for SELinux, I presume it is not an underlying part of Ubuntu.
 
Any sugesstions would be appreciated.

Chris

---

### Post by Perfect Storm on 2008-04-07
Panda software is one big bloatware (it will have signific impact on your computer performance).

Try with F-prot or AVG to detect window virus'.

---

### Post by hyper_ch on 2008-04-07
no AV needed and very likely you use a router... if you do, then you are already behind a hardware firewall and hence I'd recommend to configure that and leave iptables unconfigured on your computer.

---

### Post by gandaran on 2008-04-07
> **_aXXe_ said:**
> I'm trying to install the Panda Anti Virus because I used it in Windows and I DO interact with many windows users. Plus I like the idea of having the mail checked. I have 12 E Mail addresses so I like to be sure nothing is trying to sneak in. I do look at the from and subject so most of the offending/suspicious E Mails are dumped by me before I open them.

When I try to install, I get this:

Verifying archive integrity... All good.
Uncompressing DesktopSecure for Linux 1.00.00...............................................................................................
Setting variable installation_type to value typical
In file included from /tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:20:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:479: warning: initialization from incompatible pointer typeSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:480: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:484: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:503: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:519: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:523: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:527: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:528: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:532: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:536: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:537: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:541: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:545: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:548: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:551: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:552: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:553: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:554: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:581: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:605: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:612: warning: initialization from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.h:627: error: unknown field &#8216;socket_getpeersec&#8217; specified in initializer
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_sb_statfs&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:280: warning: passing argument 1 of &#8216;dazuko_security_ops.sb_statfs&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:280: warning: passing argument 1 of &#8216;dazuko_security_default_ops.sb_statfs&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_create&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:366: warning: passing argument 3 of &#8216;dazuko_security_ops.inode_create&#8217; makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:366: error: too few arguments to function &#8216;dazuko_security_ops.inode_create&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:366: warning: passing argument 3 of &#8216;dazuko_security_default_ops.inode_create&#8217; makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:366: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_create&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_link&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: warning: passing argument 2 of &#8216;dazuko_security_ops.inode_link&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: warning: passing argument 3 of &#8216;dazuko_security_ops.inode_link&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: error: too few arguments to function &#8216;dazuko_security_ops.inode_link&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: warning: passing argument 2 of &#8216;dazuko_security_default_ops.inode_link&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: warning: passing argument 3 of &#8216;dazuko_security_default_ops.inode_link&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:380: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_link&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_unlink&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:394: error: too few arguments to function &#8216;dazuko_security_ops.inode_unlink&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:394: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_unlink&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_symlink&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:401: warning: passing argument 3 of &#8216;dazuko_security_ops.inode_symlink&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:401: error: too few arguments to function &#8216;dazuko_security_ops.inode_symlink&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:401: warning: passing argument 3 of &#8216;dazuko_security_default_ops.inode_symlink&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:401: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_symlink&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_mkdir&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:415: warning: passing argument 3 of &#8216;dazuko_security_ops.inode_mkdir&#8217; makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:415: error: too few arguments to function &#8216;dazuko_security_ops.inode_mkdir&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:415: warning: passing argument 3 of &#8216;dazuko_security_default_ops.inode_mkdir&#8217; makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:415: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_mkdir&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_rmdir&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:429: error: too few arguments to function &#8216;dazuko_security_ops.inode_rmdir&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:429: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_rmdir&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_mknod&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:436: warning: passing argument 3 of &#8216;dazuko_security_ops.inode_mknod&#8217; makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:436: error: too few arguments to function &#8216;dazuko_security_ops.inode_mknod&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:436: warning: passing argument 3 of &#8216;dazuko_security_default_ops.inode_mknod&#8217; makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:436: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_mknod&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_rename&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: warning: passing argument 3 of &#8216;dazuko_security_ops.inode_rename&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: warning: passing argument 4 of &#8216;dazuko_security_ops.inode_rename&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: error: too few arguments to function &#8216;dazuko_security_ops.inode_rename&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: warning: passing argument 3 of &#8216;dazuko_security_default_ops.inode_rename&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: warning: passing argument 4 of &#8216;dazuko_security_default_ops.inode_rename&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:450: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_rename&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_readlink&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:464: error: too few arguments to function &#8216;dazuko_security_ops.inode_readlink&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:464: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_readlink&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_setattr&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:485: warning: passing argument 2 of &#8216;dazuko_security_ops.inode_setattr&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:485: error: too few arguments to function &#8216;dazuko_security_ops.inode_setattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:485: warning: passing argument 2 of &#8216;dazuko_security_default_ops.inode_setattr&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:485: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_setattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_setxattr&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: warning: passing argument 2 of &#8216;dazuko_security_ops.inode_setxattr&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: warning: passing argument 4 of &#8216;dazuko_security_ops.inode_setxattr&#8217; makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: error: too few arguments to function &#8216;dazuko_security_ops.inode_setxattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: warning: passing argument 2 of &#8216;dazuko_security_default_ops.inode_setxattr&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: warning: passing argument 4 of &#8216;dazuko_security_default_ops.inode_setxattr&#8217; makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:505: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_setxattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_post_setxattr&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: warning: passing argument 2 of &#8216;dazuko_security_ops.inode_post_setxattr&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: warning: passing argument 4 of &#8216;dazuko_security_ops.inode_post_setxattr&#8217; makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: error: too few arguments to function &#8216;dazuko_security_ops.inode_post_setxattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: warning: passing argument 2 of &#8216;dazuko_security_default_ops.inode_post_setxattr&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: warning: passing argument 4 of &#8216;dazuko_security_default_ops.inode_post_setxattr&#8217; makes pointer from integer without a cast
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:517: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_post_setxattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_getxattr&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:522: warning: passing argument 2 of &#8216;dazuko_security_ops.inode_getxattr&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:522: error: too few arguments to function &#8216;dazuko_security_ops.inode_getxattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:522: warning: passing argument 2 of &#8216;dazuko_security_default_ops.inode_getxattr&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:522: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_getxattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_listxattr&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:529: error: too few arguments to function &#8216;dazuko_security_ops.inode_listxattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:529: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_listxattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_inode_removexattr&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:537: warning: passing argument 2 of &#8216;dazuko_security_ops.inode_removexattr&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:537: error: too few arguments to function &#8216;dazuko_security_ops.inode_removexattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:537: warning: passing argument 2 of &#8216;dazuko_security_default_ops.inode_removexattr&#8217; from incompatible pointer type
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:537: error: too few arguments to function &#8216;dazuko_security_default_ops.inode_removexattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_task_kill&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:813: error: too few arguments to function &#8216;dazuko_security_ops.task_kill&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:813: error: too few arguments to function &#8216;dazuko_security_default_ops.task_kill&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_getprocattr&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:983: error: too many arguments to function &#8216;dazuko_security_ops.getprocattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:983: error: too many arguments to function &#8216;dazuko_security_default_ops.getprocattr&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_netlink_recv&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1016: error: too few arguments to function &#8216;dazuko_security_ops.netlink_recv&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1016: error: too few arguments to function &#8216;dazuko_security_default_ops.netlink_recv&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1018: error: too few arguments to function &#8216;cap_netlink_recv&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c: In function &#8216;dazuko_security_socket_getpeersec&#8217;:
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1197: error: &#8216;struct security_operations&#8217; has no member named &#8216;socket_getpeersec&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1197: error: &#8216;struct security_operations&#8217; has no member named &#8216;socket_getpeersec&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1197: error: &#8216;struct security_operations&#8217; has no member named &#8216;socket_getpeersec&#8217;
/tmp/dazuko-2.1.1/dazuko_linux26_lsm.c:1197: error: &#8216;struct security_operations&#8217; has no member named &#8216;socket_getpeersec&#8217;
make[2]: *** [/tmp/dazuko-2.1.1/dazuko_linux26_lsm.o] Error 1
make[1]: *** [_module_/tmp/dazuko-2.1.1] Error 2
make: *** [dummy_rule] Error 2

Then the Panda DesktopSecure for Linux Installation screen shows this:
Installation Complete

Cannot install the automatic file protection module. This may be caused by several reasons.

You haven't installed the compiler for your kernel

You haven't install the correct kernel headers

You haven't installed the necessary development tools

SELinux is active on your system


My kernel is is the generic 2.16.22-14 (I think that's right) and as for the other in the list I have no idea. I wish more information from the installer.

So, how do I make sure all the above are corrected and which (if any) compiler, kernel headers and development tools do I find and install? As for SELinux, I presume it is not an underlying part of Ubuntu.
 
Any sugesstions would be appreciated.

Chris

you need to install the 'build-essential' package for compiling, but I advise you against installing panda software as you won't be able to load the dazuko module, ubuntu as some security applications that conflict with dazuko, so unless you uninstall those applications dazuko will not run.
if you want a antivirus for linux it's best to install a simpler AV like avast or f-prot or bitdefender and do a manual scan of you mail or files.
I recommend clam AV (you can install from the repository's) and instead installing the dazuko engine for real time scanning, you can use it with another engine just for scanning mail I think it's 'amavisd-new'.

---

### Post by SunnyRabbiera on 2008-04-07
you dont need antivirus in linux, but if you want to monitor your windows system clamAV is pretty good, its got a graphic front end called KlamAV

---

### Post by zvacet on 2008-04-07
> I DO interact with many windows users.

Let them take care of their security.You don´t have to worry about viruses made for windows.It is same as you try to install any program made for windows in linux system.It will not work.Why?Because program is made for windows not for linux.Read [this.](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by coolen on 2008-04-07
The list of Linux viruses is about a dozen or so long, many of them proof on concept, none of them seen in the wild.

---

### Post by _aXXe_ on 2008-04-08
> **zvacet said:**
> Let them take care of their security.You don´t have to worry about viruses made for windows.It is same as you try to install any program made for windows in linux system.It will not work.Why?Because program is made for windows not for linux.Read [this.](http://ubuntuforums.org/showthread.php?t=510812)


Okay, I thank all of you for a timely and informative response. I think I'll drop the whole virus scan idea and just go with the flow \\:D/  The KISS (keep it simple stupid) principle is always best.

---

