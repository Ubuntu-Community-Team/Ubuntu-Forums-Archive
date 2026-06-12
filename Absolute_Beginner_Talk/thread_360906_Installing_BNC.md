---
title: "Installing BNC"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by rev0 on 2007-02-13
So hey im new to linux.. i already did

sudo apttitude upgrade

And i was wondering about installing BNC on Ubuntu.

I tried various choices for the "make" syntax but receive erros.

Help please.

rev0@ubuntu1:~/Desktop/identwd$ make
Please specify the type of system you wish to build for.
Valid systems are:

        sunos3          SunOS 3.x (tested with 3.5)
        sunos4          Sun SunOS 4
        sunos5          Sun SunOS 5 (Solaris 2)
        bsdi            BSD/386 (The commercial one)
        386bsd          386BSD (The free one)
        netbsd          NetBSD
        freebsd         FreeBSD 2.x
        2.11bsd         2.11BSD
        4.3bsd          4.3BSD Reno
        4.3bsd-tahoe    4.3BSD Tahoe
        dynix3          Sequent Dynix 3
        riscos4         MIPS RISC/OS 4
        aix3            IBM AIX 3.2
        aix4            IBM AIX 4.0 or 4.1
        aix42           IBM AIX 4.2
        irix4           Silicon Graphics IRIX 4
        irix5           Silicon Graphics IRIX 5 (< 5.3)
        irix53          Silicon Graphics IRIX 5.3
        irix6           Silicon Graphics IRIX 6.0
        irix62          Silicon Graphics IRIX 6.2
        irix64          Silicon Graphics IRIX 6.4
 hiuxwe2                Hitachi HI-UX/WE2
        hpux7           Hewlett-Packard HP-UX 7
        hpux8           Hewlett-Packard HP-UX 8
        hpux9           Hewlett-Packard HP-UX 9
        hpux10          Hewlett-Packard HP-UX 10
        sco32_40        SCO unix System V release 3.2 (v4.0 & 4.1)
        sco32_42        SCO Unix System V Release 3.2v4.2
        sco32_5         SCO Unix System V Release 3.2v5
        svr4            Generic System V Release 4 UNIX
        attsvr4         AT&T's own System V Release 4
        uw1             Novell UnixWare v1.x
        uw2             Novell UnixWare v2.x
        aux2            Apple A/UX 2
        aux3            Apple A/UX 3.0 only
        aux301          Apple A/UX 3.0.1 or newer
        ultrix3         Digital Ultrix 3
        ultrix4         Digital Ultrix 4
        apollo          Apollo Domain/OS SR10.x
        alpha           Digital Alpha AXP OSF
        alpha3          Digital Alpha AXP OSF; 3.0 or later
        digitalunix     Digital Alpha AXP Digital Unix
        linux           Linux 0.99.13q or later
        unicos6         Cray UNICOS 6
        convex          Convex ConvexOS
        next            NeXT/Mach (NeXTSTEP 2 or 3.0)
        nextmab         NeXT/Mach (NeXTSTEP 3.1 MAB)
        sony_mips_bsd   Sony NEWS (BSD version)
        pyramid4        Pyramid's dualPort OSx 4
        ptx4            Sequent's Dynix/ptx version 4
        ptx2            Sequent's Dynix/ptx version 2
        machten         Tenon MachTen 4.0.x
        other           Other BSD-based Unixes

For example: make sunos4

---

### Post by RomeReactor on 2007-02-13
> **rev0 said:**
> So hey im new to linux.. i already did

sudo apttitude upgrade

And i was wondering about installing BNC on Ubuntu.

I tried various choices for the "make" syntax but receive erros.

Help please.

rev0@ubuntu1:~/Desktop/identwd$ make
Please specify the type of system you wish to build for.
Valid systems are:

        sunos3          SunOS 3.x (tested with 3.5)
        sunos4          Sun SunOS 4
        sunos5          Sun SunOS 5 (Solaris 2)
        bsdi            BSD/386 (The commercial one)
        386bsd          386BSD (The free one)
        netbsd          NetBSD
        freebsd         FreeBSD 2.x
        2.11bsd         2.11BSD
        4.3bsd          4.3BSD Reno
        4.3bsd-tahoe    4.3BSD Tahoe
        dynix3          Sequent Dynix 3
        riscos4         MIPS RISC/OS 4
        aix3            IBM AIX 3.2
        aix4            IBM AIX 4.0 or 4.1
        aix42           IBM AIX 4.2
        irix4           Silicon Graphics IRIX 4
        irix5           Silicon Graphics IRIX 5 (< 5.3)
        irix53          Silicon Graphics IRIX 5.3
        irix6           Silicon Graphics IRIX 6.0
        irix62          Silicon Graphics IRIX 6.2
        irix64          Silicon Graphics IRIX 6.4
 hiuxwe2                Hitachi HI-UX/WE2
        hpux7           Hewlett-Packard HP-UX 7
        hpux8           Hewlett-Packard HP-UX 8
        hpux9           Hewlett-Packard HP-UX 9
        hpux10          Hewlett-Packard HP-UX 10
        sco32_40        SCO unix System V release 3.2 (v4.0 & 4.1)
        sco32_42        SCO Unix System V Release 3.2v4.2
        sco32_5         SCO Unix System V Release 3.2v5
        svr4            Generic System V Release 4 UNIX
        attsvr4         AT&T's own System V Release 4
        uw1             Novell UnixWare v1.x
        uw2             Novell UnixWare v2.x
        aux2            Apple A/UX 2
        aux3            Apple A/UX 3.0 only
        aux301          Apple A/UX 3.0.1 or newer
        ultrix3         Digital Ultrix 3
        ultrix4         Digital Ultrix 4
        apollo          Apollo Domain/OS SR10.x
        alpha           Digital Alpha AXP OSF
        alpha3          Digital Alpha AXP OSF; 3.0 or later
        digitalunix     Digital Alpha AXP Digital Unix
        **linux**           Linux 0.99.13q or later
        unicos6         Cray UNICOS 6
        convex          Convex ConvexOS
        next            NeXT/Mach (NeXTSTEP 2 or 3.0)
        nextmab         NeXT/Mach (NeXTSTEP 3.1 MAB)
        sony_mips_bsd   Sony NEWS (BSD version)
        pyramid4        Pyramid's dualPort OSx 4
        ptx4            Sequent's Dynix/ptx version 4
        ptx2            Sequent's Dynix/ptx version 2
        machten         Tenon MachTen 4.0.x
        other           Other BSD-based Unixes

For example: make sunos4

This is just a guess, but my choice would be

```
make linux
```

---

### Post by rev0 on 2007-02-13
Nope I get...

```

rev0@ubuntu1:~/Desktop/identwd$ make linux
Building for Linux 0.99.13q or later ...
make[1]: Entering directory `/home/rev0/Desktop/identwd/src'
cc -DLINUX -DNO_KVM -DINCLUDE_EXTENSIONS -DSTRONG_LOG -DALLOW_FORMAT  -DPATH_CONFIG='"/etc/identd.conf"' -DPATH_DESKEY='"/etc/identd.key"'   -c -o identd.o identd.c
identd.c:35:19: error: stdio.h: No such file or directory
identd.c:36:19: error: ctype.h: No such file or directory
identd.c:37:19: error: errno.h: No such file or directory
identd.c:38:19: error: netdb.h: No such file or directory
identd.c:39:20: error: signal.h: No such file or directory
identd.c:40:19: error: fcntl.h: No such file or directory
identd.c:42:23: error: sys/types.h: No such file or directory
identd.c:43:23: error: sys/param.h: No such file or directory
identd.c:44:23: error: sys/ioctl.h: No such file or directory
identd.c:45:24: error: sys/socket.h: No such file or directory
identd.c:47:24: error: sys/file.h: No such file or directory
identd.c:49:22: error: sys/time.h: No such file or directory
identd.c:50:22: error: sys/wait.h: No such file or directory
identd.c:52:17: error: pwd.h: No such file or directory
identd.c:53:17: error: grp.h: No such file or directory
identd.c:55:24: error: netinet/in.h: No such file or directory
identd.c:58:25: error: arpa/inet.h: No such file or directory
In file included from identd.c:76:
error.h:15:20: error: syslog.h: No such file or directory
identd.c:101: error: &#8216;NULL&#8217; undeclared here (not in a function)
identd.c: In function &#8216;gethost&#8217;:
identd.c:189: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct in_addr&#8217; 
identd.c:189: error: &#8216;AF_INET&#8217; undeclared (first use in this function)
identd.c:189: error: (Each undeclared identifier is reported only once
identd.c:189: error: for each function it appears in.)
identd.c:189: warning: assignment makes pointer from integer without a cast
identd.c:193: error: dereferencing pointer to incomplete type
identd.c:193: warning: assignment makes pointer from integer without a cast
identd.c:202: error: dereferencing pointer to incomplete type
identd.c:202: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct in_addr&#8217; 
identd.c:203: error: dereferencing pointer to incomplete type
identd.c:207: error: dereferencing pointer to incomplete type
identd.c:207: warning: return makes pointer from integer without a cast
identd.c: In function &#8216;main&#8217;:
identd.c:276: error: storage size of &#8216;sin&#8217; isn&#8217;t known
identd.c:277: error: storage size of &#8216;laddr&#8217; isn&#8217;t known
identd.c:277: error: storage size of &#8216;faddr&#8217; isn&#8217;t known
identd.c:278: error: storage size of &#8216;l_sa&#8217; isn&#8217;t known
identd.c:278: error: storage size of &#8216;f_sa&#8217; isn&#8217;t known
identd.c:280: error: storage size of &#8216;tv&#8217; isn&#8217;t known
identd.c:353: warning: assignment makes pointer from integer without a cast
identd.c:355: error: &#8216;LOG_ERR&#8217; undeclared (first use in this function)
identd.c:355: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
identd.c:355: error: &#8216;stderr&#8217; undeclared (first use in this function)
identd.c:355: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
identd.c:355: error: &#8216;stdout&#8217; undeclared (first use in this function)
identd.c:355: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
identd.c:358: error: dereferencing pointer to incomplete type
identd.c:359: error: dereferencing pointer to incomplete type
identd.c:371: warning: assignment makes pointer from integer without a cast
identd.c:373: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
identd.c:373: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
identd.c:373: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
identd.c:375: error: dereferencing pointer to incomplete type
identd.c:392: error: &#8216;LOG_PID&#8217; undeclared (first use in this function)
identd.c:405: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
identd.c:406: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
identd.c:471: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
identd.c:504: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
identd.c:504: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
identd.c:504: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
identd.c:536: error: storage size of &#8216;addr&#8217; isn&#8217;t known
identd.c:554: error: &#8216;AF_INET&#8217; undeclared (first use in this function)
identd.c:554: error: &#8216;SOCK_STREAM&#8217; undeclared (first use in this function)
identd.c:565: error: &#8216;INADDR_ANY&#8217; undeclared (first use in this function)
identd.c:574: warning: assignment makes pointer from integer without a cast
identd.c:579: error: dereferencing pointer to incomplete type
identd.c:587: warning: assignment makes pointer from integer without a cast
identd.c:590: error: dereferencing pointer to incomplete type
identd.c:635: error: &#8216;fd_set&#8217; undeclared (first use in this function)
identd.c:635: error: expected &#8216;;&#8217; before &#8216;read_set&#8217;
identd.c:636: error: storage size of &#8216;sad&#8217; isn&#8217;t known
identd.c:648: error: &#8216;SIGCHLD&#8217; undeclared (first use in this function)
identd.c:648: error: &#8216;SIG_IGN&#8217; undeclared (first use in this function)
identd.c:675: warning: incompatible implicit declaration of built-in function &#8216;bzero&#8217;
identd.c:675: error: &#8216;read_set&#8217; undeclared (first use in this function)
identd.c:676: error: &#8216;NBBY&#8217; undeclared (first use in this function)
identd.c:698: error: &#8216;errno&#8217; undeclared (first use in this function)
identd.c:698: error: &#8216;EINTR&#8217; undeclared (first use in this function)
identd.c:768: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
identd.c:796: error: &#8216;stdin&#8217; undeclared (first use in this function)
make[1]: *** [identd.o] Error 1
make[1]: Leaving directory `/home/rev0/Desktop/identwd/src'
make: *** [linux] Error 2
rev0@ubuntu1:~/Desktop/identwd$ 


```


I got the deb package from the repository for pident but after it was going to install it says something like "grep /etc/XXX.conf no such file or directory"

?

---

### Post by rev0 on 2007-02-14
bump.. to the top... please help!

---

### Post by Styles on 2007-02-27
```
sudo apt-get install build-essential dialog
```

```
./configure
```

```
make
```

```
./bncsetup
```

```
./bnc
```

---

