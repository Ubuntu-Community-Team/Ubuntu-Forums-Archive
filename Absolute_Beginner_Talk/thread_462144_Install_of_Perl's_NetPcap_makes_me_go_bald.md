---
title: "Install of Perl's Net::Pcap makes me go bald"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by zeeboo on 2007-06-02
So I'm having a heck of a time getting Net::PCap installed on my box. I remember it being particularly bitch last time. I believe to have everything.

My *nix flavor:
```
uname -a
Linux kubuntu-boy 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux 
```

My installed libraries:
```
dpkg -l "*libpcap*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
pn  libpcap-dev               <none>                    (no description available)
ii  libpcap0.7                0.7.2-7                   System interface for user-level packet capture
pn  libpcap0.7-dev            <none>                    (no description available)
ii  libpcap0.8                0.9.5-1build1             System interface for user-level packet capture
ii  libpcap0.8-dev            0.9.5-1build1             Development library and header files for libpcap 0.8
```

When I use Perl's CPAN to install or when executing a 'make test' on the downloaded Net-Pcap files (v0.14 and v0.15) I get a failure at t/03-openlive. Here's the error from the make test:
```
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/00-load...........ok 1/1# Testing Net::Pcap 0.15_01 under Perl 5.008008
t/00-load...........ok
t/01-api............ok
t/02-lookup.........ok
t/03-openlive.......ok 12/14
#   Failed test ' - $err must be set: SIOCGIFHWADDR: No such device'
#   at t/03-openlive.t line 70.
#                   'SIOCGIFHWADDR: No such device'
#     doesn't match '/^(?:bind|ioctl): (?:No such device)/'
# Looks like you failed 1 test of 14.
t/03-openlive.......dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED test 13
        Failed 1/14 tests, 92.86% okay 
```

Searches on Google and GoogleGroups are coming up empty. I'm beginning to wonder if the libpcap.so libraries are ok or if they are missing some key ingredient.  Apologies in advance if I posted this in the wrong forum and big thanks to someone who knows. :-)

---

### Post by zeeboo on 2007-06-03
bump?

---

### Post by Raul07 on 2007-07-19
bump
i've come across this same problem, someone could help me out? thanks!

---

### Post by Capt-Nuss on 2007-09-07
Hi,

i've got almost the same problem, my libs are:
```
||/ Name                Version             Beschreibung
+++-===================-===================-======================================================
pn  libpcap-dev         <keine>             (keine Beschreibung vorhanden)
pn  libpcap0.7          <keine>             (keine Beschreibung vorhanden)
pn  libpcap0.7-dev      <keine>             (keine Beschreibung vorhanden)
ii  libpcap0.8          0.9.7-1             System interface for user-level packet capture
ii  libpcap0.8-dev      0.9.7-1             Development library and header files for libpcap 0.8
pn  libpcap0.9          <keine>             (keine Beschreibung vorhanden)

```
I get this error during installation:
```
...
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/00-load...........# Testing Net::Pcap 0.14 under Perl 5.008008
t/00-load...........ok
t/01-api............ok
t/02-lookup.........ok
t/03-openlive.......NOK 13/14
#   Failed test ' - $err must be set: SIOCGIFHWADDR: No such device'
#   at t/03-openlive.t line 70.
#                   'SIOCGIFHWADDR: No such device'
#     doesn't match '/^(?:bind|ioctl): (?:No such device)/'
# Looks like you failed 1 test of 14.
t/03-openlive.......dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED test 13
        Failed 1/14 tests, 92.86% okay
t/04-loop...........ok
...

```

Yours

Roland

---

### Post by Capt-Nuss on 2007-09-08
Hi,

i've got the answer form a anther forum. They told me to use "force install" insted of "install". Now Net::Pcap is installed, und my script is running.

---

### Post by Bpa on 2008-07-21
Hello all,

I cannot even get to the "make install" step because "make" gives me the following output:

Net-Pcap-0.14$ sudo make
cp Pcap.pm blib/lib/Net/Pcap.pm
AutoSplitting blib/lib/Net/Pcap.pm (blib/lib/auto/Net/Pcap)
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share
+/perl/5.8/ExtUtils/typemap -typemap typemap  Pcap.xs > Pcap.xsc && mv
+ Pcap.xsc Pcap.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-s
+trict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE
+_OFFSET_BITS=64 -O2   -DVERSION=\"0.14\" -DXS_VERSION=\"0.14\" -fPIC 
+"-I/usr/lib/perl/5.8/CORE"  -DHAVE_BLANK -DHAVE_PCAP_COMPILE_NOPCAP -
+DHAVE_PCAP_FINDALLDEVS -DHAVE_PCAP_FREEALLDEVS -DHAVE_PCAP_GETNONBLOC
+K -DHAVE_PCAP_OPEN_DEAD -DHAVE_PCAP_SETNONBLOCK Pcap.c
In file included from Pcap.xs:43:
stubs.inc:71:2: warning: #warning "the function pcap_lib_version() is 
+not available, but will be emulated"
stubs.inc:113:2: warning: #warning "the function pcap_breakloop() is n
+ot available"
stubs.inc:157:2: warning: #warning "the function pcap_dump_file() is n
+ot available"
stubs.inc:172:2: warning: #warning "the function pcap_dump_flush() is 
+not available"
stubs.inc:187:2: warning: #warning "the function pcap_list_datalinks()
+ is not available"
stubs.inc:202:2: warning: #warning "the function pcap_set_datalink() i
+s not available"
stubs.inc:217:2: warning: #warning "the function pcap_datalink_name_to
+_val() is not available"
stubs.inc:232:2: warning: #warning "the function pcap_datalink_val_to_
+name() is not available"
stubs.inc:247:2: warning: #warning "the function pcap_datalink_val_to_
+description() is not available"
stubs.inc:277:2: warning: #warning "the function pcap_get_selectable_f
+d() is not available"
stubs.inc:292:2: warning: #warning "the function pcap_next_ex() is not
+ available"
stubs.inc:307:2: warning: #warning "the function pcap_sendpacket() is 
+not available"
stubs.inc:322:2: warning: #warning "the function pcap_createsrcstr() i
+s not available"
stubs.inc:337:2: warning: #warning "the function pcap_parsesrcstr() is
+ not available"
stubs.inc:352:2: warning: #warning "the function pcap_open() is not av
+ailable"
stubs.inc:373:2: warning: #warning "the function pcap_setbuff() is not
+ available"
stubs.inc:388:2: warning: #warning "the function pcap_setuserbuffer() 
+is not available"
stubs.inc:403:2: warning: #warning "the function pcap_setmode() is not
+ available"
stubs.inc:418:2: warning: #warning "the function pcap_setmintocopy() i
+s not available"
stubs.inc:433:2: warning: #warning "the function pcap_sendqueue_alloc(
+) is not available"
stubs.inc:455:2: warning: #warning "the function pcap_sendqueue_destro
+y() is not available"
stubs.inc:469:2: warning: #warning "the function pcap_sendqueue_queue(
+) is not available"
stubs.inc:484:2: warning: #warning "the function pcap_sendqueue_transm
+it() is not available"
stubs.inc:499:2: warning: #warning "the function pcap_event() is not a
+vailable"
stubs.inc:514:2: warning: #warning "the function pcap_setsampling() is
+ not available"
Pcap.xs: In function ‘XS_Net__Pcap_lookupnet’:
Pcap.xs:143: warning: passing argument 1 of ‘pcap_lookupnet’ discards 
+qualifiers from pointer target type
Pcap.xs: In function ‘XS_Net__Pcap_open_live’:
Pcap.xs:256: warning: passing argument 1 of ‘pcap_open_live’ discards 
+qualifiers from pointer target type
Running Mkbootstrap for Net::Pcap ()
chmod 644 Pcap.bs
rm -f blib/arch/auto/Net/Pcap/Pcap.so
cc  -shared -L/usr/local/lib Pcap.o  -o blib/arch/auto/Net/Pcap/Pcap.s
+o     \
       -lpcap      \
      
chmod 755 blib/arch/auto/Net/Pcap/Pcap.so
cp Pcap.bs blib/arch/auto/Net/Pcap/Pcap.bs
chmod 644 blib/arch/auto/Net/Pcap/Pcap.bs
cp bin/pcapinfo blib/script/pcapinfo
/usr/bin/perl "-MExtUtils::MY" -e "MY->fixin(shift)" blib/script/pcapi
+nfo
Manifying blib/man1/pcapinfo.1p
Manifying blib/man3/Net::Pcap.3pm

Do I need to point the Makefile to a different place so it finds the libpcap headers?  Where are these headers?

I have the following packages installed:


libnet1
libnet1-dev
libpcap0.7
libpcap0.7-dev
libpcap0.8
libnet-pcap-perl

---

