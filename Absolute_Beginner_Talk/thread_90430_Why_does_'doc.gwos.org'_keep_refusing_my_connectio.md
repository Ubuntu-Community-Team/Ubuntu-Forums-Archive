---
title: "Why does 'doc.gwos.org' keep refusing my connection"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by Il_Tuo_Nome on 2005-11-14
I was following this link [http://www.ubuntuforums.org/showthread.php?t=85899]("http://www.ubuntuforums.org/showthread.php?t=85899")
and I read and followed the directions to add the 'gmail notifier'. I got as far as the following command: **gian@gian:~$ tar -xjf checkgmail-1.3.tar.bz2** which then reulted in the following: [B]tar: checkgmail-1.3.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors[/B]. I then inadvertantly closed my browser window, and tried to go back to ask about that error, and the URL kept refusing my connection. I'm assuming that error probably means while installing that it came across a snag somewhere? And I was hoping someone could help me with this. Here is the terminal output up to that point, if it's needed.

cp SAX/PurePerl/XMLDecl.pm blib/lib/XML/SAX/PurePerl/XMLDecl.pm
cp SAX/PurePerl/Reader/NoUnicodeExt.pm blib/lib/XML/SAX/PurePerl/Reader/NoUnicod eExt.pm
cp SAX/PurePerl/Reader/String.pm blib/lib/XML/SAX/PurePerl/Reader/String.pm
cp SAX/PurePerl/Reader/URI.pm blib/lib/XML/SAX/PurePerl/Reader/URI.pm
cp SAX/Intro.pod blib/lib/XML/SAX/Intro.pod
cp SAX/PurePerl/DTDDecls.pm blib/lib/XML/SAX/PurePerl/DTDDecls.pm
cp SAX/PurePerl.pm blib/lib/XML/SAX/PurePerl.pm
cp SAX/PurePerl/Reader.pm blib/lib/XML/SAX/PurePerl/Reader.pm
make[1]: Entering directory `/home/gian/.cpan/build/XML-SAX-0.13/XML-SAX-Base'
cp lib/XML/SAX/placeholder.pl ../blib/lib/XML/SAX/placeholder.pl
cp lib/XML/SAX/Base.pm ../blib/lib/XML/SAX/Base.pm
cp lib/XML/SAX/Exception.pm ../blib/lib/XML/SAX/Exception.pm
Manifying ../blib/man3/XML::SAX::Base.3pm
Manifying ../blib/man3/XML::SAX::Exception.3pm
make[1]: Leaving directory `/home/gian/.cpan/build/XML-SAX-0.13/XML-SAX-Base'
Manifying blib/man3/XML::SAX::DocumentLocator.3pm
Manifying blib/man3/XML::SAX.3pm
Manifying blib/man3/XML::SAX::PurePerl.3pm
Manifying blib/man3/XML::SAX::Intro.3pm
Manifying blib/man3/XML::SAX::ParserFactory.3pm
Manifying blib/man3/XML::SAX::PurePerl::Reader.3pm
  /usr/bin/make  -- OK
Running make test
make[1]: Entering directory `/home/gian/.cpan/build/XML-SAX-0.13/XML-SAX-Base'
make[1]: Leaving directory `/home/gian/.cpan/build/XML-SAX-0.13/XML-SAX-Base'
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/00basic........ok
t/01known........ok
t/10xmldecl1.....ok
t/11xmldecl2.....ok
t/12miscstart....ok
t/13int_ent......ok
t/14encoding.....ok
t/15element......ok
t/16large........ok 1/3parsed 80085 bytes in 1 seconds
t/16large........ok
t/20factory......ok
t/21saxini.......ok
t/99cleanup......ok
All tests successful.
Files=12, Tests=94,  3 wallclock secs ( 2.14 cusr +  0.18 csys =  2.32 CPU)
make[1]: Entering directory `/home/gian/.cpan/build/XML-SAX-0.13/XML-SAX-Base'
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, '../blib/lib', '../blib/arch')" t/*.t
t/00basic...............ok
t/01exception...........ok
t/01simpledriver........ok
t/02simplefilter........ok
t/03chdriver............ok
t/04chfilter............ok
t/05dtdhdriver..........ok
t/06lexhdriver..........ok
t/07declhdriver.........ok
t/08errorhdriver........ok
t/09resoldriver.........ok
t/10dochdriver..........ok
t/11sax1multiclass......ok
t/12sax2multiclass......ok
t/13handlerswitch.......ok
t/14downstreamswitch....ok
t/15parentswitch........ok
t/16gethandlers.........ok
All tests successful.
Files=18, Tests=137,  1 wallclock secs ( 0.91 cusr +  0.17 csys =  1.08 CPU)
make[1]: Leaving directory `/home/gian/.cpan/build/XML-SAX-0.13/XML-SAX-Base'
  /usr/bin/make test -- OK
Running make install
make[1]: Entering directory `/home/gian/.cpan/build/XML-SAX-0.13/XML-SAX-Base'
make[1]: Leaving directory `/home/gian/.cpan/build/XML-SAX-0.13/XML-SAX-Base'
Installing /usr/local/share/perl/5.8.7/XML/SAX.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/ParserFactory.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/DocumentLocator.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/Intro.pod
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/placeholder.pl
Installing /usr/local/share/perl/5.8.7/XML/SAX/Base.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/Exception.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/Exception.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/UnicodeExt.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/DocType.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/NoUnicodeExt.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/DebugHandler.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/Productions.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/XMLDecl.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/DTDDecls.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/Reader.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/Reader/UnicodeExt.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/Reader/Stream.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/Reader/NoUnicodeExt.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/Reader/String.pm
Installing /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/Reader/URI.pm
Installing /usr/local/man/man3/XML::SAX::Base.3pm
Installing /usr/local/man/man3/XML::SAX::Exception.3pm
Installing /usr/local/man/man3/XML::SAX::DocumentLocator.3pm
Installing /usr/local/man/man3/XML::SAX.3pm
Installing /usr/local/man/man3/XML::SAX::PurePerl.3pm
Installing /usr/local/man/man3/XML::SAX::Intro.3pm
Installing /usr/local/man/man3/XML::SAX::ParserFactory.3pm
Installing /usr/local/man/man3/XML::SAX::PurePerl::Reader.3pm
Writing /usr/local/lib/perl/5.8.7/auto/XML/SAX/.packlist
Appending installation info to /usr/local/lib/perl/5.8.7/perllocal.pod
could not find ParserDetails.ini in /usr/local/share/perl/5.8.7/XML/SAX
  /usr/bin/make install  -- OK
XML::NamespaceSupport is up to date.
Running make for G/GR/GRANTM/XML-Simple-2.14.tar.gz
  Is already unwrapped into directory /home/gian/.cpan/build/XML-Simple-2.14

  CPAN.pm: Going to build G/GR/GRANTM/XML-Simple-2.14.tar.gz

cp lib/XML/Simple/FAQ.pod blib/lib/XML/Simple/FAQ.pod
cp lib/XML/Simple.pm blib/lib/XML/Simple.pm
Manifying blib/man3/XML::Simple::FAQ.3pm
Manifying blib/man3/XML::Simple.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
# Package                        Version
#  perl                           5.8.7
#  XML::Simple                    2.14
#  Storable                       2.13
#  XML::Parser                    Not Installed
#  XML::SAX                       0.13
#  XML::NamespaceSupport          1.09
#  XML::SAX::PurePerl             0.90 (default parser)
t/0_Config........ok
t/1_XMLin.........ok 2/122Unable to recognise encoding of this document at /usr/ local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 32
#     Failed test (t/1_XMLin.t at line 380)
#          got: 'Unable to recognise encoding of this document at /usr/local/sha re/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
# '
#     expected: ''
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 38
#     Failed test (t/1_XMLin.t at line 426)
#     Structures begin differing at:
#          $got->{cdata} = '<greeting>Hello, world!</greeting>>'
#     $expected->{cdata} = '<greeting>Hello, world!</greeting>'
t/1_XMLin.........NOK 39
#     Failed test (t/1_XMLin.t at line 432)
#     Structures begin differing at:
#          $got->{x} = '<y>one</y>><y>two</y>>'
#     $expected->{x} = '<y>one</y><y>two</y>'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
t/1_XMLin.........NOK 122
#     Failed test (t/1_XMLin.t at line 1443)
#     Structures begin differing at:
#          $got->{pubpath}{test1}{title} = 'web_source -> web_target1'
#     $expected->{pubpath}{test1}{title} = 'web_source -&gt; web_target1'
# Looks like you failed 4 tests of 122.
t/1_XMLin.........dubious
        Test returned status 4 (wstat 1024, 0x400)
DIED. FAILED tests 32, 38-39, 122
        Failed 4/122 tests, 96.72% okay
t/2_XMLout........NOK 47
#     Failed test (t/2_XMLout.t at line 302)
#     Structures begin differing at:
#          $got->{c} = '&amp;C&amp;'
#     $expected->{c} = '&C&'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/2_XMLout........ok 196/196# Looks like you failed 1 test of 196.
t/2_XMLout........dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED test 47
        Failed 1/196 tests, 99.49% okay (less 1 skipped test: 194 okay, 98.98%)
t/3_Storable......ok
t/4_MemShare......ok
t/5_MemCopy.......ok
t/6_ObjIntf.......ok
t/7_SaxStuff......ok
t/8_Namespaces....ok
t/9_Strict........ok 1/38Unable to recognise encoding of this document at /usr/l ocal/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/9_Strict........ok
t/A_XMLParser.....skipped
        all skipped: no XML::Parser
Failed Test  Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/1_XMLin.t     4  1024   122    4   3.28%  32 38-39 122
t/2_XMLout.t    1   256   196    1   0.51%  47
1 test and 1 subtest skipped.
Failed 2/11 test scripts, 81.82% okay. 5/454 subtests failed, 98.90% okay.
make: *** [test_dynamic] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force
gian@gian:~$ sudo perl -MCPAN -e 'install Crypt::SSLeay'
CPAN: Storable loaded ok
Going to read /home/gian/.cpan/Metadata
  Database was generated on Mon, 14 Nov 2005 23:54:57 GMT
Running install for module Crypt::SSLeay
Running make for C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.ta](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.ta) r.gz
CPAN: Digest::MD5 loaded ok
Fetching with LWP:
  [ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/C/CH/CHAMAS/CHECKSUMS](ftp://carroll.cac.psu.edu/pub/CPAN/authors/id/C/CH/CHAMAS/CHECKSUMS)
CPAN: Compress::Zlib loaded ok
Checksum for /home/gian/.cpan/sources/authors/id/C/CH/CHAMAS/Crypt-SSLeay-0.51.t ar.gz ok
Scanning cache /home/gian/.cpan/build for sizes
Deleting from cache: /home/gian/.cpan/build/XML-NamespaceSupport-1.09 (1.4>0.0 M B)
Deleting from cache: /home/gian/.cpan/build/XML-SAX-0.13 (1.3>0.0 MB)
Deleting from cache: /home/gian/.cpan/build/XML-Simple-2.14 (0.5>0.0 MB)
Crypt-SSLeay-0.51/
Crypt-SSLeay-0.51/t/
Crypt-SSLeay-0.51/t/net_ssl.t
Crypt-SSLeay-0.51/t/ssl_context.t
Crypt-SSLeay-0.51/lib/
Crypt-SSLeay-0.51/lib/Crypt/
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/MainContext.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/Conn.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/X509.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/Err.pm
Crypt-SSLeay-0.51/lib/Crypt/SSLeay/CTX.pm
Crypt-SSLeay-0.51/lib/Net/
Crypt-SSLeay-0.51/lib/Net/SSL.pm
Crypt-SSLeay-0.51/certs/
Crypt-SSLeay-0.51/certs/ca-bundle.crt
Crypt-SSLeay-0.51/certs/notacakeynopass.pem
Crypt-SSLeay-0.51/certs/notacacert.pem
Crypt-SSLeay-0.51/MANIFEST
Crypt-SSLeay-0.51/typemap
Crypt-SSLeay-0.51/MANIFEST.SKIP
Crypt-SSLeay-0.51/SSLeay.pm
Crypt-SSLeay-0.51/CHANGES
Crypt-SSLeay-0.51/lwp-ssl-test
Crypt-SSLeay-0.51/net_ssl_test
Crypt-SSLeay-0.51/SSLeay.xs
Crypt-SSLeay-0.51/README
Crypt-SSLeay-0.51/Makefile.PL

  CPAN.pm: Going to build C/CH/CHAMAS/Crypt-SSLeay-0.51.tar.gz

Found OpenSSL (version OpenSSL 0.9.7) installed at /usr
Which OpenSSL build path do you want to link against? [/usr]
'pparently no SSLeay installation at '
Are you sure you got it correct????

================================================
BUILD INFORMATION
================================================

ssl dir:
libraries:      -lssl -lcrypto -lgcc -lRSAglue -lrsaref
/includedir:
ssl header:     ssl.h
/includeidate:

================================================

Checking if your kit is complete...
Looks good
Unrecognized argument in LIBS ignored: '/lib'
Note (probably harmless): No library found for -lgcc
Note (probably harmless): No library found for -lRSAglue
Note (probably harmless): No library found for -lrsaref
Writing Makefile for Crypt::SSLeay
cp lib/Crypt/SSLeay/X509.pm blib/lib/Crypt/SSLeay/X509.pm
cp lib/Net/SSL.pm blib/lib/Net/SSL.pm
cp SSLeay.pm blib/lib/Crypt/SSLeay.pm
cp lib/Crypt/SSLeay/MainContext.pm blib/lib/Crypt/SSLeay/MainContext.pm
cp lib/Crypt/SSLeay/Conn.pm blib/lib/Crypt/SSLeay/Conn.pm
cp lib/Crypt/SSLeay/CTX.pm blib/lib/Crypt/SSLeay/CTX.pm
cp lib/Crypt/SSLeay/Err.pm blib/lib/Crypt/SSLeay/Err.pm
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ ExtUtils/typemap -typemap typemap  SSLeay.xs > SSLeay.xsc && mv SSLeay.xsc SSLea y.c
/include -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-ali asing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.51\" -DXS_VERSION=\"0.51\" -fPIC "-I/usr/lib/perl/5.8/CORE"   SS Leay.c
In file included from SSLeay.xs:25:
crypt_ssleay_version.h:1:17: error: ssl.h: No such file or directory
crypt_ssleay_version.h:2:20: error: crypto.h: No such file or directory
In file included from crypt_ssleay_version.h:3,
                 from SSLeay.xs:25:
/usr/include/err.h:37: error: syntax error before ‘(’ token
crypt_ssleay_version.h:4:18: error: rand.h: No such file or directory
crypt_ssleay_version.h:5:20: error: pkcs12.h: No such file or directory
SSLeay.xs:43: error: syntax error before ‘*’ token
SSLeay.xs: In function ‘InfoCallback’:
SSLeay.xs:48: error: ‘where’ undeclared (first use in this function)
SSLeay.xs:48: error: (Each undeclared identifier is reported only once
SSLeay.xs:48: error: for each function it appears in.)
SSLeay.xs:48: error: ‘SSL_ST_MASK’ undeclared (first use in this function)
SSLeay.xs:50: error: ‘SSL_ST_CONNECT’ undeclared (first use in this function)
SSLeay.xs:52: error: ‘SSL_ST_ACCEPT’ undeclared (first use in this function)
SSLeay.xs:57: error: ‘SSL_CB_LOOP’ undeclared (first use in this function)
SSLeay.xs:58: error: ‘s’ undeclared (first use in this function)
SSLeay.xs:59: error: ‘SSL_CB_ALERT’ undeclared (first use in this function)
SSLeay.xs:61: error: ‘SSL_CB_READ’ undeclared (first use in this function)
SSLeay.xs:63: error: ‘ret’ undeclared (first use in this function)
SSLeay.xs:66: error: ‘SSL_CB_EXIT’ undeclared (first use in this function)
SSLeay.c: In function ‘XS_Crypt__SSLeay__CTX_new’:
SSLeay.c:120: error: ‘SSL_CTX’ undeclared (first use in this function)
SSLeay.c:120: error: ‘RETVAL’ undeclared (first use in this function)
SSLeay.xs:104: error: ‘ctx’ undeclared (first use in this function)
SSLeay.xs:133: error: ‘SSL_OP_ALL’ undeclared (first use in this function)
SSLeay.xs:136: error: ‘SSL_VERIFY_NONE’ undeclared (first use in this function)
SSLeay.c: In function ‘XS_Crypt__SSLeay__CTX_free’:
SSLeay.c:173: error: ‘SSL_CTX’ undeclared (first use in this function)
SSLeay.c:173: error: ‘ctx’ undeclared (first use in this function)
SSLeay.c:177: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__CTX_set_cipher_list’:
SSLeay.c:194: error: ‘SSL_CTX’ undeclared (first use in this function)
SSLeay.c:194: error: ‘ctx’ undeclared (first use in this function)
SSLeay.c:201: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__CTX_use_certificate_file’:
SSLeay.c:219: error: ‘SSL_CTX’ undeclared (first use in this function)
SSLeay.c:219: error: ‘ctx’ undeclared (first use in this function)
SSLeay.c:227: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__CTX_use_PrivateKey_file’:
SSLeay.c:245: error: ‘SSL_CTX’ undeclared (first use in this function)
SSLeay.c:245: error: ‘ctx’ undeclared (first use in this function)
SSLeay.c:253: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__CTX_use_pkcs12_file’:
SSLeay.c:271: error: ‘SSL_CTX’ undeclared (first use in this function)
SSLeay.c:271: error: ‘ctx’ undeclared (first use in this function)
SSLeay.xs:172: error: ‘EVP_PKEY’ undeclared (first use in this function)
SSLeay.xs:172: error: ‘pkey’ undeclared (first use in this function)
SSLeay.xs:173: error: ‘X509’ undeclared (first use in this function)
SSLeay.xs:173: error: ‘cert’ undeclared (first use in this function)
SSLeay.xs:174: error: ‘ca’ undeclared (first use in this function)
SSLeay.xs:175: error: ‘PKCS12’ undeclared (first use in this function)
SSLeay.xs:175: error: ‘p12’ undeclared (first use in this function)
SSLeay.c:286: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__CTX_check_private_key’:
SSLeay.c:325: error: ‘SSL_CTX’ undeclared (first use in this function)
SSLeay.c:325: error: ‘ctx’ undeclared (first use in this function)
SSLeay.c:331: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__CTX_set_verify’:
SSLeay.c:349: error: ‘SSL_CTX’ undeclared (first use in this function)
SSLeay.c:349: error: ‘ctx’ undeclared (first use in this function)
SSLeay.c:358: error: syntax error before ‘)’ token
SSLeay.xs:217: error: ‘SSL_VERIFY_NONE’ undeclared (first use in this function)
SSLeay.xs:221: error: ‘SSL_VERIFY_PEER’ undeclared (first use in this function)
SSLeay.c: In function ‘XS_Crypt__SSLeay__Conn_new’:
SSLeay.c:389: error: ‘SSL_CTX’ undeclared (first use in this function)
SSLeay.c:389: error: ‘ctx’ undeclared (first use in this function)
SSLeay.xs:235: error: ‘SSL’ undeclared (first use in this function)
SSLeay.xs:235: error: ‘ssl’ undeclared (first use in this function)
SSLeay.c:394: error: ‘RETVAL’ undeclared (first use in this function)
SSLeay.c:398: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__Conn_free’:
SSLeay.c:443: error: ‘SSL’ undeclared (first use in this function)
SSLeay.c:443: error: ‘ssl’ undeclared (first use in this function)
SSLeay.c:447: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__Conn_set_fd’:
SSLeay.c:464: error: ‘SSL’ undeclared (first use in this function)
SSLeay.c:464: error: ‘ssl’ undeclared (first use in this function)
SSLeay.c:471: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__Conn_connect’:
SSLeay.c:489: error: ‘SSL’ undeclared (first use in this function)
SSLeay.c:489: error: ‘ssl’ undeclared (first use in this function)
SSLeay.c:495: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__Conn_accept’:
SSLeay.c:513: error: ‘SSL’ undeclared (first use in this function)
SSLeay.c:513: error: ‘ssl’ undeclared (first use in this function)
SSLeay.c:519: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__Conn_write’:
SSLeay.c:537: error: ‘SSL’ undeclared (first use in this function)
SSLeay.c:537: error: ‘ssl’ undeclared (first use in this function)
SSLeay.c:549: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__Conn_read’:
SSLeay.c:590: error: ‘SSL’ undeclared (first use in this function)
SSLeay.c:590: error: ‘ssl’ undeclared (first use in this function)
SSLeay.c:603: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__Conn_get_peer_certificate’:
SSLeay.c:655: error: ‘SSL’ undeclared (first use in this function)
SSLeay.c:655: error: ‘ssl’ undeclared (first use in this function)
SSLeay.c:656: error: ‘X509’ undeclared (first use in this function)
SSLeay.c:656: error: ‘RETVAL’ undeclared (first use in this function)
SSLeay.c:660: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__Conn_get_verify_result’:
SSLeay.c:679: error: ‘SSL’ undeclared (first use in this function)
SSLeay.c:679: error: ‘ssl’ undeclared (first use in this function)
SSLeay.c:684: error: syntax error before ‘)’ token
SSLeay.xs:377: error: ‘X509_V_OK’ undeclared (first use in this function)
SSLeay.c: In function ‘XS_Crypt__SSLeay__Conn_get_shared_ciphers’:
SSLeay.c:704: error: ‘SSL’ undeclared (first use in this function)
SSLeay.c:704: error: ‘ssl’ undeclared (first use in this function)
SSLeay.c:713: error: syntax error before ‘)’ token
SSLeay.xs:388: warning: assignment makes pointer from integer without a cast
SSLeay.c: In function ‘XS_Crypt__SSLeay__Conn_get_cipher’:
SSLeay.c:732: error: ‘SSL’ undeclared (first use in this function)
SSLeay.c:732: error: ‘ssl’ undeclared (first use in this function)
SSLeay.c:738: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__X509_free’:
SSLeay.c:757: error: ‘X509’ undeclared (first use in this function)
SSLeay.c:757: error: ‘cert’ undeclared (first use in this function)
SSLeay.c:761: error: syntax error before ‘)’ token
SSLeay.c: In function ‘XS_Crypt__SSLeay__X509_subject_name’:
SSLeay.c:778: error: ‘X509’ undeclared (first use in this function)
SSLeay.c:778: error: ‘cert’ undeclared (first use in this function)
SSLeay.c:786: error: syntax error before ‘)’ token
SSLeay.xs:412: warning: assignment makes pointer from integer without a cast
SSLeay.c: In function ‘XS_Crypt__SSLeay__X509_issuer_name’:
SSLeay.c:808: error: ‘X509’ undeclared (first use in this function)
SSLeay.c:808: error: ‘cert’ undeclared (first use in this function)
SSLeay.c:816: error: syntax error before ‘)’ token
SSLeay.xs:424: warning: assignment makes pointer from integer without a cast
SSLeay.c: In function ‘XS_Crypt__SSLeay__X509_get_notBeforeString’:
SSLeay.c:838: error: ‘X509’ undeclared (first use in this function)
SSLeay.c:838: error: ‘cert’ undeclared (first use in this function)
SSLeay.c:844: error: syntax error before ‘)’ token
SSLeay.xs:434: error: invalid type argument of ‘->’
SSLeay.c: In function ‘XS_Crypt__SSLeay__X509_get_notAfterString’:
SSLeay.c:863: error: ‘X509’ undeclared (first use in this function)
SSLeay.c:863: error: ‘cert’ undeclared (first use in this function)
SSLeay.c:869: error: syntax error before ‘)’ token
SSLeay.xs:442: error: invalid type argument of ‘->’
make: *** [SSLeay.o] Error 1
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
gian@gian:~$ tar -xjf checkgmail-1.3.tar.bz2
tar: checkgmail-1.3.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
gian@gian:~$ pwd
/home/gian
gian@gian:~$

Thank you very much :razz: 

P.S. I'm sorry about the long report. I hope that's ok?

---

### Post by Il_Tuo_Nome on 2005-11-14
[http://doc.gwos.org/index.php/BreezyCust]("http://doc.gwos.org/index.php/BreezyCust")

OOooops sorry the URL is above 


Thanks

---

### Post by Il_Tuo_Nome on 2005-11-15
Am I to assume there is no insight on this?

---

