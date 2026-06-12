---
title: "&quot;No rule to make target `install'&quot; error while installing"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-05-15
I am trying to install a little utility on ubuntu which isnt available via automatix/synaptect

This is the utility [http://ps2-scene.org/hdldump/hdl_dumx-0.8.6-20060901-src.tar.bz2](http://ps2-scene.org/hdldump/hdl_dumx-0.8.6-20060901-src.tar.bz2)

and here is a copy past of my terminal window

---------------------------------------------------------------------------------
tabby@tabby-laptop:~$ cd /home/tabby/Desktop/hdl_dump
tabby@tabby-laptop:~/Desktop/hdl_dump$ make
make: Nothing to be done for `all'.
tabby@tabby-laptop:~/Desktop/hdl_dump$ ls
aligned.c        dict.o        hio_udpnet.o    iin_iml.d      net_common.d
aligned.d        doc-pak       hio_win32.c     iin_iml.h      net_common.h
aligned.h        execli        hio_win32.d     iin_iml.o      net_common.o
aligned.o        gui           hio_win32.h     iin_iso.c      net_io.h
apa.c            hdl.c         hio_win32.o     iin_iso.d      ntddscsi.h
apa.d            hdl.d         icon.bin        iin_iso.h      osal.h
apa.h            hdl_dump      icon.h          iin_iso.o      osal_unix.c
apa.o            hdl_dump.c    iin_aspi.c      iin_nero.c     osal_unix.d
aspi_hlio.c      hdl_dump.d    iin_aspi.h      iin_nero.d     osal_unix.o
aspi_hlio.h      hdl_dump.o    iin_cdrwin.c    iin_nero.h     osal_win32.c
AUTHORS          hdl.h         iin_cdrwin.d    iin_nero.o     progress.c
byteseq.c        hdl.o         iin_cdrwin.h    iin_optical.c  progress.d
byteseq.d        hio_dbg.c     iin_cdrwin.o    iin_optical.d  progress.h
byteseq.h        hio_dbg.d     iin_gi.c        iin_optical.h  progress.o
byteseq.o        hio_dbg.h     iin_gi.d        iin_optical.o  ps2_hdd.h
CHANGELOG        hio_dbg.o     iin_gi.h        iin_probe.c    README
common.c         hio.h         iin_gi.o        iin_probe.d    retcodes.h
common.d         hio_probe.c   iin.h           iin_probe.o    rsrc.rc
common.h         hio_probe.d   iin_hio.c       iin_spti.c     scsidefs.h
common.o         hio_probe.o   iin_hio.d       iin_spti.h     sema.h
config.h         hio_trace.c   iin_hio.h       isofs.c        svr
COPYING          hio_trace.d   iin_hio.o       isofs.d        thd_iin.c
CVS              hio_trace.h   iin_img_base.c  isofs.h        thd_iin.d
description-pak  hio_trace.o   iin_img_base.d  isofs.o        thd_iin.h
dict.c           hio_udpnet.c  iin_img_base.h  Makefile       thd_iin.o
dict.d           hio_udpnet.d  iin_img_base.o  mktestimg      TODO
dict.h           hio_udpnet.h  iin_iml.c       net_common.c   wnaspi32.h
tabby@tabby-laptop:~/Desktop/hdl_dump$ make
make: Nothing to be done for `all'.
tabby@tabby-laptop:~/Desktop/hdl_dump$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
--------------------------------------------------------------------------

Im totally new to installing things in this way I have always used one of the install managers before and I have no idea what I am doing wrong. Any help, as always much appreciated.

---

### Post by bobplano on 2007-05-15
that's odd you don't have a makefile. when i downloaded it just now there was a makefile. try reextracting it or redownloading it.

---

### Post by reidms on 2007-05-15
It looks like you are compiling a program from source.

the usual method is
```
./configure
make
make-install
```
(depending on preference)

If possible, I would avoid source until you are confident with compiling

Try getting a binary package like .deb or even .rpm(RPMs must be converted to .deb via a utility called alien)

---

### Post by tabithaboof on 2007-05-15
Unfortunately, this is a bit of a niche piece of software or I would look for .deb.

I redownloaded and retried. I guess i must have moved the makefile or something?

--------------------------
tabby@tabby-laptop:~$ cd /home/tabby/Desktop/hdl_dump
tabby@tabby-laptop:~/Desktop/hdl_dump$ ls
aligned.c    dict.h        icon.bin        iin_iso.h      osal.h
aligned.h    execli        icon.h          iin_nero.c     osal_unix.c
apa.c        gui           iin_aspi.c      iin_nero.h     osal_win32.c
apa.h        hdl.c         iin_aspi.h      iin_optical.c  progress.c
aspi_hlio.c  hdl_dump.c    iin_cdrwin.c    iin_optical.h  progress.h
aspi_hlio.h  hdl.h         iin_cdrwin.h    iin_probe.c    ps2_hdd.h
AUTHORS      hio_dbg.c     iin_gi.c        iin_spti.c     README
byteseq.c    hio_dbg.h     iin_gi.h        iin_spti.h     retcodes.h
byteseq.h    hio.h         iin.h           isofs.c        rsrc.rc
CHANGELOG    hio_probe.c   iin_hio.c       isofs.h        scsidefs.h
common.c     hio_trace.c   iin_hio.h       Makefile       sema.h
common.h     hio_trace.h   iin_img_base.c  mktestimg      svr
config.h     hio_udpnet.c  iin_img_base.h  net_common.c   thd_iin.c
COPYING      hio_udpnet.h  iin_iml.c       net_common.h   thd_iin.h
CVS          hio_win32.c   iin_iml.h       net_io.h       TODO
dict.c       hio_win32.h   iin_iso.c       ntddscsi.h     wnaspi32.h
tabby@tabby-laptop:~/Desktop/hdl_dump$ makre
bash: makre: command not found
tabby@tabby-laptop:~/Desktop/hdl_dump$ make
-e      DEP thd_iin.c
-e      DEP osal_unix.c
-e      DEP hio_udpnet.c
-e      DEP dict.c
-e      DEP byteseq.c
-e      DEP net_common.c
-e      DEP hio_trace.c
-e      DEP hio_dbg.c
-e      DEP hio_win32.c
-e      DEP hio_probe.c
-e      DEP iin_hio.c
-e      DEP iin_probe.c
-e      DEP iin_iml.c
-e      DEP iin_gi.c
-e      DEP iin_nero.c
-e      DEP iin_cdrwin.c
-e      DEP iin_iso.c
-e      DEP iin_optical.c
-e      DEP iin_img_base.c
-e      DEP aligned.c
-e      DEP isofs.c
-e      DEP hdl.c
-e      DEP progress.c
-e      DEP common.c
-e      DEP apa.c
-e      DEP hdl_dump.c
-e      CC  hdl_dump.c
hdl_dump.c:1511: warning: ‘map_device_name_or_exit’ defined but not used
-e      CC  apa.c
-e      CC  common.c
-e      CC  progress.c
-e      CC  hdl.c
-e      CC  isofs.c
-e      CC  aligned.c
-e      CC  iin_img_base.c
-e      CC  iin_optical.c
-e      CC  iin_iso.c
-e      CC  iin_cdrwin.c
-e      CC  iin_nero.c
-e      CC  iin_gi.c
-e      CC  iin_iml.c
-e      CC  iin_probe.c
-e      CC  iin_hio.c
-e      CC  hio_probe.c
-e      CC  hio_win32.c
-e      CC  hio_dbg.c
-e      CC  hio_trace.c
-e      CC  net_common.c
-e      CC  byteseq.c
-e      CC  dict.c
-e      CC  hio_udpnet.c
-e      CC  osal_unix.c
-e      CC  thd_iin.c
-e      LNK hdl_dump
tabby@tabby-laptop:~/Desktop/hdl_dump$ sudo make install
make: *** No rule to make target `install'.  Stop.
tabby@tabby-laptop:~/Desktop/hdl_dump$ 


I notices that the readme contains the line 

"* Linux: Build and copy executable into a directory of your choice.
	make RELEASE=yes"

but I dont understand where to enter this or when. Could this be part of the problem?

---

### Post by Dr Small on 2007-05-15
When running the command "make" run the rest of it with it.
Example:
```
make RELEASE=yes
```

Dr Small

---

### Post by tabithaboof on 2007-05-16
Hi there, im really sorry about this but I am still getting the same error.

```
tabby@tabby-laptop:~$ cd Desktop/hdl_dump
tabby@tabby-laptop:~/Desktop/hdl_dump$ ls
aligned.c    dict.h        icon.bin        iin_iso.h      osal.h
aligned.h    execli        icon.h          iin_nero.c     osal_unix.c
apa.c        gui           iin_aspi.c      iin_nero.h     osal_win32.c
apa.h        hdl.c         iin_aspi.h      iin_optical.c  progress.c
aspi_hlio.c  hdl_dump.c    iin_cdrwin.c    iin_optical.h  progress.h
aspi_hlio.h  hdl.h         iin_cdrwin.h    iin_probe.c    ps2_hdd.h
AUTHORS      hio_dbg.c     iin_gi.c        iin_spti.c     README
byteseq.c    hio_dbg.h     iin_gi.h        iin_spti.h     retcodes.h
byteseq.h    hio.h         iin.h           isofs.c        rsrc.rc
CHANGELOG    hio_probe.c   iin_hio.c       isofs.h        scsidefs.h
common.c     hio_trace.c   iin_hio.h       Makefile       sema.h
common.h     hio_trace.h   iin_img_base.c  mktestimg      svr
config.h     hio_udpnet.c  iin_img_base.h  net_common.c   thd_iin.c
COPYING      hio_udpnet.h  iin_iml.c       net_common.h   thd_iin.h
CVS          hio_win32.c   iin_iml.h       net_io.h       TODO
dict.c       hio_win32.h   iin_iso.c       ntddscsi.h     wnaspi32.h
tabby@tabby-laptop:~/Desktop/hdl_dump$ make RELEASE=yes
-e      DEP thd_iin.c
-e      DEP osal_unix.c
-e      DEP hio_udpnet.c
-e      DEP dict.c
-e      DEP byteseq.c
-e      DEP net_common.c
-e      DEP hio_trace.c
-e      DEP hio_dbg.c
-e      DEP hio_win32.c
-e      DEP hio_probe.c
-e      DEP iin_hio.c
-e      DEP iin_probe.c
-e      DEP iin_iml.c
-e      DEP iin_gi.c
-e      DEP iin_nero.c
-e      DEP iin_cdrwin.c
-e      DEP iin_iso.c
-e      DEP iin_optical.c
-e      DEP iin_img_base.c
-e      DEP aligned.c
-e      DEP isofs.c
-e      DEP hdl.c
-e      DEP progress.c
-e      DEP common.c
-e      DEP apa.c
-e      DEP hdl_dump.c
-e      CC  hdl_dump.c
hdl_dump.c:1511: warning: ‘map_device_name_or_exit’ defined but not used
-e      CC  apa.c
-e      CC  common.c
-e      CC  progress.c
-e      CC  hdl.c
-e      CC  isofs.c
-e      CC  aligned.c
-e      CC  iin_img_base.c
-e      CC  iin_optical.c
-e      CC  iin_iso.c
-e      CC  iin_cdrwin.c
iin_cdrwin.c: In function ‘iin_cdrwin_probe_path’:
iin_cdrwin.c:250: warning: ‘mode’ may be used uninitialized in this function
-e      CC  iin_nero.c
iin_nero.c: In function ‘iin_nero_probe_path’:
iin_nero.c:168: warning: ‘mode’ may be used uninitialized in this function
iin_nero.c:167: warning: ‘footer_size’ may be used uninitialized in this function
iin_nero.c:167: warning: ‘header_size’ may be used uninitialized in this function
-e      CC  iin_gi.c
-e      CC  iin_iml.c
-e      CC  iin_probe.c
-e      CC  iin_hio.c
-e      CC  hio_probe.c
-e      CC  hio_win32.c
-e      CC  hio_dbg.c
-e      CC  hio_trace.c
-e      CC  net_common.c
-e      CC  byteseq.c
-e      CC  dict.c
-e      CC  hio_udpnet.c
-e      CC  osal_unix.c
-e      CC  thd_iin.c
-e      LNK hdl_dump
/bin/sh: upx: not found
make: [hdl_dump] Error 127 (ignored)
tabby@tabby-laptop:~/Desktop/hdl_dump$ make install
make: *** No rule to make target `install'.  Stop.
tabby@tabby-laptop:~/Desktop/hdl_dump$ make RELEASE=yes install
make: *** No rule to make target `install'.  Stop.
tabby@tabby-laptop:~/Desktop/hdl_dump$ 

```

---

