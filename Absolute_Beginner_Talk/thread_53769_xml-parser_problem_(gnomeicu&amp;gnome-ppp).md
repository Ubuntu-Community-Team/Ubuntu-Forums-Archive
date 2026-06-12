---
title: "xml-parser problem (gnomeicu&amp;gnome-ppp)"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by ram32 on 2005-08-02
Hello! I like this distributive. Thank you!
But I have one problem. I had downloaded...
gnomeicu-0.99.5.tar.bz2
gnome-ppp-0.3.23.tar.bz2
... and when I'm trying to...
./configure
... it, it said:

root@ubuntu:/home/ram32/gnomeicu-0.99.5 # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for perl... /usr/bin/perl
configure: error: XML::Parser perl module is required for intltool


I have Ubuntu 5.04 for Intel x86. What must I do? Help me, please! :)

---

### Post by SGC on 2005-08-02
To install the XML parser, run the following command:
```

sudo perl -MCPAN -e shell

```

When asked to do a manual configuration, type **no**

At  the**cpan>** prompt type:
```

install XML::Parser

```

After the installation complete, type **exit** and try to install gnomeicu and gnome-ppp again

---

### Post by ram32 on 2005-08-02
[QUOTE=SGC]To install the XML parser, run the following command:
```

sudo perl -MCPAN -e shell

```

When asked to do a manual configuration, type **no**

At  the**cpan>** prompt type:
```

install XML::Parser

```

After the installation complete, type **exit** and try to install gnomeicu and gnome-ppp again[/QUOTE]
 It's not available!

---

### Post by SGC on 2005-08-02
[QUOTE=ram32]It's not available![/QUOTE]
 Could you please clearify more?

---

### Post by ryan76 on 2005-10-15
Hi, i'm having the same problem and followed these instructions and got this output:

cpan> install XML::Parser
CPAN: Storable loaded ok
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz](ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz)
LWP failed with code[404] message[File '01mailrc.txt.gz' not found]
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz](ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz)
Couldn't fetch 01mailrc.txt.gz from ftp.perl.org

Trying with "/usr/bin/wget -O -" to get
    [ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz](ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz)
--07:25:35--  [ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz](ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz)
           => `-'
Resolving ftp.perl.org... failed: Host not found.

System call "/usr/bin/wget -O - "ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.tx t.gz"  > /root/.cpan/sources/authors/01mailrc.txt"
returned status 1 (wstat 256)
Warning: expected file [/root/.cpan/sources/authors/01mailrc.txt.gz] doesn't exi st
Issuing "/usr/bin/ftp -n"
ftp: ftp.perl.org: Host name lookup failure
Not connected.
Local directory now /root/.cpan/sources/authors
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Bad luck... Still failed!
Can't access URL [ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz](ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz).

Please check, if the URLs I found in your configuration file () are valid.
The urllist can be edited. E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch authors/01mailrc.txt.gz
Fetching with LWP:
  [ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz](ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: Bad hostname 'ftp.perl.o rg']
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz](ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz)

Trying with "/usr/bin/wget -O -" to get
    [ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz](ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz)
--07:25:39--  [ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz](ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz)
           => `-'
Resolving ftp.perl.org... failed: Host not found.

System call "/usr/bin/wget -O - "ftp://ftp.perl.org/pub/CPAN/modules/02packages. details.txt.gz"  > /root/.cpan/sources/modules/02packages.details.txt"
returned status 1 (wstat 256)
Warning: expected file [/root/.cpan/sources/modules/02packages.details.txt.gz] d oesn't exist
Issuing "/usr/bin/ftp -n"
ftp: ftp.perl.org: Host name lookup failure
Not connected.
Local directory now /root/.cpan/sources/modules
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Bad luck... Still failed!
Can't access URL [ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz](ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz).

Please check, if the URLs I found in your configuration file () are valid.
The urllist can be edited. E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch modules/02packages.details.txt.gz
Fetching with LWP:
  [ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz](ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz)
LWP failed with code[500] message[LWP::Protocol::MyFTP: Bad hostname 'ftp.perl.o rg']
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz](ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz)

Trying with "/usr/bin/wget -O -" to get
    [ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz](ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz)
--07:25:43--  [ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz](ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz)
           => `-'
Resolving ftp.perl.org... failed: Host not found.

System call "/usr/bin/wget -O - "ftp://ftp.perl.org/pub/CPAN/modules/03modlist.d ata.gz"  > /root/.cpan/sources/modules/03modlist.data"
returned status 1 (wstat 256)
Warning: expected file [/root/.cpan/sources/modules/03modlist.data.gz] doesn't e xist
Issuing "/usr/bin/ftp -n"
ftp: ftp.perl.org: Host name lookup failure
Not connected.
Local directory now /root/.cpan/sources/modules
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Bad luck... Still failed!
Can't access URL [ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz](ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz).

Please check, if the URLs I found in your configuration file () are valid.
The urllist can be edited. E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch modules/03modlist.data.gz
Going to write /root/.cpan/Metadata
Warning: Cannot install XML::Parser, don't know what it is.
Try the command

    i /XML::Parser/

to find objects with matching identifiers.

cpan> i /XML::Parser/
No objects found of any type for argument /XML::Parser/



Help! I'm trying to install firestarter 1.0.3... need a firewall!

Thanks for any help

---

### Post by Jussi Kukkonen on 2005-10-15
*Help! I'm trying to install firestarter 1.0.3... need a firewall!*

Just checking... Are you aware that Breezy has Firestarter 1.0.3 in the repositories (so you could install via synaptic or apt-get)?

---

### Post by ryan76 on 2005-10-15
I'm running 5.04 on AMD64... can I apt-get things from the breezy badge repositories? If so how do I know what to apt-get?

sorry for the newbie-ness.

I tried 

apt-get install firestarter

and it installed 1.0.2, grr.

---

### Post by Jussi Kukkonen on 2005-10-18
I wouldn't do that (use 5.10 repos in 5.04).

You could try installing the xml parser like this: 
[LIST=1]
[*]Download [http://www.cpan.org/modules/by-module/XML/XML-Parser-2.34.tar.gz](http://www.cpan.org/modules/by-module/XML/XML-Parser-2.34.tar.gz).
[*]Untar the archive.
[*]and make:
```
perl Makefile.pl
make install
```
[/LIST]

EDIT:
Hey wait a minute... firestarter 1.0.3 is in hoary-backports. Try that first. See [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by mirkov on 2005-10-20
I need the same perl module, but for teatime applet (last version is 2.6.xx and the one in repos is 2.4.xx) and under Breezy, but found this thread: 

I cannot install XML::Parser - after the install command I get a lot of error messages, starting with 

Expat.xs:12:19: error: expat.h: No such file or directory
Expat.xs:60: error: syntax error before âXML_Parserâ

I also tried downloading the module and then installing it with

```

perl Makefile.pl
make install

```

but the error message is the same. I tried googling for the first line but I'm not much of a perl expert ;) 

Any ideas?

---

### Post by sbernst on 2005-11-07
Folks with expat.h issues... I just discovered that while expat is installed, the _development_ version is needed for expat.h to be available to the system!  

If you type:

ls /usr/include/expat.h 

and an error message comes back; add the package 'libexpat-dev'

(apt-get install libexpat-dev)

Click yes even though 2 other small packages get installed along with it.  Then go back to building your parsers and what not.  

Note: I also had to apt-get install make and gcc for building some things.

Hope this helps!

Steven B.

---

### Post by unixnorks on 2005-11-08
well, encountered almost the same problem and to all kindhearted there please help me solve my problem..

cpan> install XML::Parser
CPAN: Storable loaded ok
Going to read /home/norman/.cpan/Metadata
  Database was generated on Tue, 08 Nov 2005 07:01:16 GMT
Running install for module XML::Parser
Running make for M/MS/MSERGEANT/XML-Parser-2.34.tar.gz
CPAN: Digest::MD5 loaded ok
Checksum for /home/norman/.cpan/sources/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz ok
Scanning cache /home/norman/.cpan/build for sizes
XML-Parser-2.34
XML-Parser-2.34/Changes
XML-Parser-2.34/Expat
XML-Parser-2.34/Expat/encoding.h
XML-Parser-2.34/Expat/Expat.pm
XML-Parser-2.34/Expat/Expat.xs
XML-Parser-2.34/Expat/Makefile.PL
XML-Parser-2.34/Expat/typemap
XML-Parser-2.34/Makefile.PL
XML-Parser-2.34/MANIFEST
XML-Parser-2.34/Parser
XML-Parser-2.34/Parser/Encodings
XML-Parser-2.34/Parser/Encodings/big5.enc
XML-Parser-2.34/Parser/Encodings/euc-kr.enc
XML-Parser-2.34/Parser/Encodings/iso-8859-2.enc
XML-Parser-2.34/Parser/Encodings/iso-8859-3.enc
XML-Parser-2.34/Parser/Encodings/iso-8859-4.enc
XML-Parser-2.34/Parser/Encodings/iso-8859-5.enc
XML-Parser-2.34/Parser/Encodings/iso-8859-7.enc
XML-Parser-2.34/Parser/Encodings/iso-8859-8.enc
XML-Parser-2.34/Parser/Encodings/iso-8859-9.enc
XML-Parser-2.34/Parser/Encodings/Japanese_Encodings.msg
XML-Parser-2.34/Parser/Encodings/README
XML-Parser-2.34/Parser/Encodings/windows-1250.enc
XML-Parser-2.34/Parser/Encodings/windows-1252.enc
XML-Parser-2.34/Parser/Encodings/x-euc-jp-jisx0221.enc
XML-Parser-2.34/Parser/Encodings/x-euc-jp-unicode.enc
XML-Parser-2.34/Parser/Encodings/x-sjis-cp932.enc
XML-Parser-2.34/Parser/Encodings/x-sjis-jdk117.enc
XML-Parser-2.34/Parser/Encodings/x-sjis-jisx0221.enc
XML-Parser-2.34/Parser/Encodings/x-sjis-unicode.enc
XML-Parser-2.34/Parser/LWPExternEnt.pl
XML-Parser-2.34/Parser/Style
XML-Parser-2.34/Parser/Style/Debug.pm
XML-Parser-2.34/Parser/Style/Objects.pm
XML-Parser-2.34/Parser/Style/Stream.pm
XML-Parser-2.34/Parser/Style/Subs.pm
XML-Parser-2.34/Parser/Style/Tree.pm
XML-Parser-2.34/Parser.pm
XML-Parser-2.34/README
XML-Parser-2.34/samples
XML-Parser-2.34/samples/canonical
XML-Parser-2.34/samples/canontst.xml
XML-Parser-2.34/samples/ctest.dtd
XML-Parser-2.34/samples/REC-xml-19980210.xml
XML-Parser-2.34/samples/xmlcomments
XML-Parser-2.34/samples/xmlfilter
XML-Parser-2.34/samples/xmlstats
XML-Parser-2.34/t
XML-Parser-2.34/t/astress.t
XML-Parser-2.34/t/cdata.t
XML-Parser-2.34/t/decl.t
XML-Parser-2.34/t/defaulted.t
XML-Parser-2.34/t/encoding.t
XML-Parser-2.34/t/ext.ent
XML-Parser-2.34/t/ext2.ent
XML-Parser-2.34/t/external_ent.t
XML-Parser-2.34/t/file.t
XML-Parser-2.34/t/finish.t
XML-Parser-2.34/t/foo.dtd
XML-Parser-2.34/t/namespaces.t
XML-Parser-2.34/t/parament.t
XML-Parser-2.34/t/partial.t
XML-Parser-2.34/t/skip.t
XML-Parser-2.34/t/stream.t
XML-Parser-2.34/t/styles.t
Removing previously used /home/norman/.cpan/build/XML-Parser-2.34

  CPAN.pm: Going to build M/MS/MSERGEANT/XML-Parser-2.34.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for XML::Parser::Expat
Writing Makefile for XML::Parser
cp Parser/Encodings/x-sjis-cp932.enc blib/lib/XML/Parser/Encodings/x-sjis-cp932.enc
cp Parser/Encodings/iso-8859-7.enc blib/lib/XML/Parser/Encodings/iso-8859-7.enc
cp Parser/Style/Tree.pm blib/lib/XML/Parser/Style/Tree.pm
cp Parser/Encodings/iso-8859-9.enc blib/lib/XML/Parser/Encodings/iso-8859-9.enc
cp Parser/Encodings/x-euc-jp-unicode.enc blib/lib/XML/Parser/Encodings/x-euc-jp-unicode.enc
cp Parser/Encodings/README blib/lib/XML/Parser/Encodings/README
cp Parser/Encodings/euc-kr.enc blib/lib/XML/Parser/Encodings/euc-kr.enc
cp Parser/Encodings/windows-1250.enc blib/lib/XML/Parser/Encodings/windows-1250.enc
cp Parser/Encodings/windows-1252.enc blib/lib/XML/Parser/Encodings/windows-1252.enc
cp Parser/Encodings/big5.enc blib/lib/XML/Parser/Encodings/big5.enc
cp Parser/Encodings/iso-8859-3.enc blib/lib/XML/Parser/Encodings/iso-8859-3.enc
cp Parser/Encodings/Japanese_Encodings.msg blib/lib/XML/Parser/Encodings/Japanese_Encodings.msg
cp Parser/Style/Subs.pm blib/lib/XML/Parser/Style/Subs.pm
cp Parser/Encodings/iso-8859-4.enc blib/lib/XML/Parser/Encodings/iso-8859-4.enc
cp Parser/Encodings/iso-8859-8.enc blib/lib/XML/Parser/Encodings/iso-8859-8.enc
cp Parser/Encodings/x-euc-jp-jisx0221.enc blib/lib/XML/Parser/Encodings/x-euc-jp-jisx0221.enc
cp Parser/Encodings/iso-8859-2.enc blib/lib/XML/Parser/Encodings/iso-8859-2.enc
cp Parser/Encodings/x-sjis-jdk117.enc blib/lib/XML/Parser/Encodings/x-sjis-jdk117.enc
cp Parser/Encodings/x-sjis-unicode.enc blib/lib/XML/Parser/Encodings/x-sjis-unicode.enc
cp Parser/LWPExternEnt.pl blib/lib/XML/Parser/LWPExternEnt.pl
cp Parser/Style/Objects.pm blib/lib/XML/Parser/Style/Objects.pm
cp Parser.pm blib/lib/XML/Parser.pm
cp Parser/Style/Debug.pm blib/lib/XML/Parser/Style/Debug.pm
cp Parser/Encodings/x-sjis-jisx0221.enc blib/lib/XML/Parser/Encodings/x-sjis-jisx0221.enc
cp Parser/Style/Stream.pm blib/lib/XML/Parser/Style/Stream.pm
cp Parser/Encodings/iso-8859-5.enc blib/lib/XML/Parser/Encodings/iso-8859-5.enc
make[1]: Entering directory `/home/norman/.cpan/build/XML-Parser-2.34/Expat'
cp Expat.pm ../blib/lib/XML/Parser/Expat.pm
/usr/bin/perl /usr/share/perl/5.8.4/ExtUtils/xsubpp -noprototypes -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  Expat.xs > Expat.xsc && mv Expat.xsc Expat.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"2.34\" -DXS_VERSION=\"2.34\" -fPIC "-I/usr/lib/perl/5.8/CORE"   Expat.c
/bin/sh: cc: command not found
make[1]: *** [Expat.o] Error 127
make[1]: Leaving directory `/home/norman/.cpan/build/XML-Parser-2.34/Expat'
make: *** [subdirs] Error 2
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  [SIZE="3"][COLOR="Red"]make had returned bad status, install seems impossible[/COLOR][/SIZE]

any help is highly appreciated

---

### Post by _Mo_ on 2005-11-09
[QUOTE=ram32]checking whether -lc should be explicitly linked in... no
creating libtool
checking for perl... /usr/bin/perl
configure: error: XML::Parser perl module is required for intltool

I have Ubuntu 5.04 for Intel x86. What must I do? Help me, please! :)[/QUOTE]
Hi! I had the same problem (with other software) and installing package "libxml-parser-perl" solved it.

I'm running 5.10, so I don't know if it'll work for you...

Cheers
Mo

---

### Post by Nivriki on 2005-12-20
[QUOTE=sbernst]Folks with expat.h issues... I just discovered that while expat is installed, the _development_ version is needed for expat.h to be available to the system!  

If you type:

ls /usr/include/expat.h 

and an error message comes back; add the package 'libexpat-dev'

(apt-get install libexpat-dev)

Steven B.[/QUOTE]

Thanks... XML::Parser installed without any hitch after getting libexpat-dev (it's libexpat1-dev now).

---

