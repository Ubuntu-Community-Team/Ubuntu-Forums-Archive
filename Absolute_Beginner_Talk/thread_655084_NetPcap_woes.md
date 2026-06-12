---
title: "Net::Pcap woes"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by saviour on 2007-12-31
I have read the other posts concerning the installation of Net::Pcap either with CPAN or from file and I cannot find a solution to my problem. If anyone can throw any light on this it would be much appreciated. I am running Server 7.10 with desktop. Here's th problem when I try to make :-

cpan> force install Net::Pcap
Running install for module Net::Pcap
Running make for S/SA/SAPER/Net-Pcap-0.15.tar.gz
Checksum for /home/kryton/.cpan/sources/authors/id/S/SA/SAPER/Net-Pcap-0.15.tar.gz ok
Net-Pcap-0.15/
Net-Pcap-0.15/bin/
Net-Pcap-0.15/bin/._pcapinfo
Net-Pcap-0.15/bin/pcapinfo
Net-Pcap-0.15/Changes
Net-Pcap-0.15/eg/
Net-Pcap-0.15/eg/pktdump.pl
Net-Pcap-0.15/fallback/
Net-Pcap-0.15/fallback/const-c.inc
Net-Pcap-0.15/fallback/const-xs.inc
Net-Pcap-0.15/Makefile.PL
Net-Pcap-0.15/MANIFEST
Net-Pcap-0.15/META.yml
Net-Pcap-0.15/._Pcap.pm
Net-Pcap-0.15/Pcap.pm
Net-Pcap-0.15/._Pcap.xs
Net-Pcap-0.15/Pcap.xs
Net-Pcap-0.15/ppport.h
Net-Pcap-0.15/README
Net-Pcap-0.15/stubs.inc
Net-Pcap-0.15/t/
Net-Pcap-0.15/t/00-load.t
Net-Pcap-0.15/t/01-api.t
Net-Pcap-0.15/t/02-lookup.t
Net-Pcap-0.15/t/03-openlive.t
Net-Pcap-0.15/t/04-loop.t
Net-Pcap-0.15/t/05-dump.t
Net-Pcap-0.15/t/06-offline.t
Net-Pcap-0.15/t/07-stats.t
Net-Pcap-0.15/t/08-filter.t
Net-Pcap-0.15/t/09-error.t
Net-Pcap-0.15/t/10-fileno.t
Net-Pcap-0.15/t/11-snapshot.t
Net-Pcap-0.15/t/12-next.t
Net-Pcap-0.15/t/13-dispatch.t
Net-Pcap-0.15/t/14-datalink.t
Net-Pcap-0.15/t/15-is_swapped.t
Net-Pcap-0.15/t/16-setnonblock.t
Net-Pcap-0.15/t/17-lib_version.t
Net-Pcap-0.15/t/18-open_dead.t
Net-Pcap-0.15/t/19-breakloop.t
Net-Pcap-0.15/t/20-constants.t
Net-Pcap-0.15/t/pod.t
Net-Pcap-0.15/t/podcover.t
Net-Pcap-0.15/t/portfs.t
Net-Pcap-0.15/t/README
Net-Pcap-0.15/t/samples/
Net-Pcap-0.15/t/samples/ping-ietf-20pk-be.dmp
Net-Pcap-0.15/t/samples/ping-ietf-20pk-le.dmp
Net-Pcap-0.15/t/Utils.pm
Net-Pcap-0.15/typemap
Removing previously used /home/kryton/.cpan/build/Net-Pcap-0.15

  CPAN.pm: Going to build S/SA/SAPER/Net-Pcap-0.15.tar.gz

looking for -lpcap... yes
checking for pcap_lib_version() in -lpcap... yes
detecting available functions... ok
Checking if your kit is complete...
Looks good
Writing Makefile for Net::Pcap
cp Pcap.pm blib/lib/Net/Pcap.pm
cp ._Pcap.pm blib/lib/Net/._Pcap.pm
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  Pcap.xs > Pcap.xsc && mv Pcap.xsc Pcap.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.15\" -DXS_VERSION=\"0.15\" -fPIC "-I/usr/lib/perl/5.8/CORE"  -DHAVE_BLANK -DHAVE_PCAP_LIB_VERSION Pcap.c
In file included from Pcap.xs:43:
stubs.inc:85:2: warning: #warning "the function pcap_findalldevs() is not available, but will be emulated"
In file included from Pcap.xs:43:
stubs.inc:91: error: redefinition of ‘struct pcap_if’
stubs.inc:113:2: warning: #warning "the function pcap_breakloop() is not available"
stubs.inc:127:2: warning: #warning "the function pcap_setnonblock() is not available"
stubs.inc:142:2: warning: #warning "the function pcap_getnonblock() is not available"
stubs.inc:157:2: warning: #warning "the function pcap_dump_file() is not available"
stubs.inc:172:2: warning: #warning "the function pcap_dump_flush() is not available"
stubs.inc:187:2: warning: #warning "the function pcap_list_datalinks() is not available"
stubs.inc:202:2: warning: #warning "the function pcap_set_datalink() is not available"
stubs.inc:217:2: warning: #warning "the function pcap_datalink_name_to_val() is not available"
stubs.inc:232:2: warning: #warning "the function pcap_datalink_val_to_name() is not available"
stubs.inc:247:2: warning: #warning "the function pcap_datalink_val_to_description() is not available"
stubs.inc:262:2: warning: #warning "the function pcap_compile_nopcap() is not available"
stubs.inc:267: error: conflicting types for ‘pcap_compile_nopcap’
/usr/local/include/pcap.h:245: error: previous declaration of ‘pcap_compile_nopcap’ was here
stubs.inc:268: error: conflicting types for ‘pcap_compile_nopcap’
/usr/local/include/pcap.h:245: error: previous declaration of ‘pcap_compile_nopcap’ was here
stubs.inc:277:2: warning: #warning "the function pcap_get_selectable_fd() is not available"
stubs.inc:292:2: warning: #warning "the function pcap_next_ex() is not available"
stubs.inc:307:2: warning: #warning "the function pcap_sendpacket() is not available"
stubs.inc:322:2: warning: #warning "the function pcap_createsrcstr() is not available"
stubs.inc:337:2: warning: #warning "the function pcap_parsesrcstr() is not available"
stubs.inc:352:2: warning: #warning "the function pcap_open() is not available"
stubs.inc:373:2: warning: #warning "the function pcap_setbuff() is not available"
stubs.inc:388:2: warning: #warning "the function pcap_setuserbuffer() is not available"
stubs.inc:403:2: warning: #warning "the function pcap_setmode() is not available"
stubs.inc:418:2: warning: #warning "the function pcap_setmintocopy() is not available"
stubs.inc:433:2: warning: #warning "the function pcap_sendqueue_alloc() is not available"
stubs.inc:455:2: warning: #warning "the function pcap_sendqueue_destroy() is not available"
stubs.inc:469:2: warning: #warning "the function pcap_sendqueue_queue() is not available"
stubs.inc:484:2: warning: #warning "the function pcap_sendqueue_transmit() is not available"
stubs.inc:499:2: warning: #warning "the function pcap_event() is not available"
stubs.inc:514:2: warning: #warning "the function pcap_setsampling() is not available"
Pcap.c: In function ‘XS_Net__Pcap_strerror’:
Pcap.c:1382: warning: assignment discards qualifiers from pointer target type
make: *** [Pcap.o] Error 1
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

---

### Post by blueridgedog on 2008-01-01
Maybe in the dark, but do you have build essentials installed?  You can install it with add/remove.

Also, your cpan session is running as root, ie you started it with sudo?

---

### Post by SLOPirate on 2008-02-26
I'm having the exact same problem as the original poster.  I downloaded and installed the latest form of libpcap (.9.8) from here:  [http://www.tcpdump.org/#current](http://www.tcpdump.org/#current)  and was able to do a make install succesfully.  However, when trying to use cpan to install Net:Pcap I got the same errors.  And, yes I ran it as root.  Thanks in advance for the help.

---

