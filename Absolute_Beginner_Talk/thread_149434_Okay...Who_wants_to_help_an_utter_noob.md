---
title: "Okay...Who wants to help an utter noob?"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by PFI_Optix on 2006-03-23
I've got two problems. First, I don't know how to install any additional software. Rather, I thought I knew, but **make install** didn't do what I've always been told it should do, so I was wondering if someone could point me ot a good step-by-step guide for installing the typical non-packaged Linux program (fyi, I'm trying to install gPHPEdit).

Second, I can't connect to my file server. It's just an older Quantum Snap! server. Our Windows boxes don't have a problem at all, but I can't do anything. It's acting like it's trying to autheticate with my XP box, which shouldn't be necessary at all. What do I need to do here?

(and yes, I tried finding help...Linux documentation never seems to have anything that explains this sort of thing...it's frustrating)

edit: Okay, found a little bit of help elsewhere. I ran **./configure** and it errored out with this message:
```
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```
Still stuck, just in a different place.

---

### Post by KansasJoe on 2006-03-23
As far as the first problem is concerned you need to be in the directory of the program you want so if you dl to your home then cd gPHPedit (or whatever it's called)...then

./configure
make
sudo make install

note: many programs will install differently so if there is no configure file in there then there's gonna be a different way such as ./setup or it could be anything but ./configure is a good place to start

---

### Post by MartinJ on 2006-03-23
gphpedit is available from the universe repository.  Use Synaptic to install it, a lot easier than building from source.

Have a look at this page if you need help enabling extra repositories -> [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by MartinJ on 2006-03-23
[QUOTE=PFI_Optix]
Okay, found a little bit of help elsewhere. I ran **./configure** and it errored out with this message:
```
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```[/QUOTE]

Can't quite remember, but you might need to install the build-essential tools (includes compiler, etc)

```
sudo apt-get install build-essential
```

Good luck!

---

### Post by PFI_Optix on 2006-03-23
[QUOTE=KansasJoe]As far as the first problem is concerned you need to be in the directory of the program you want so if you dl to your home then cd gPHPedit (or whatever it's called)...then

./configure
make
sudo make install

note: many programs will install differently so if there is no configure file in there then there's gonna be a different way such as ./setup or it could be anything but ./configure is a good place to start[/QUOTE]

./configure is the problem. It's complaining that there's no C compiler, and then I get "command not found" when I try to run make.

---

### Post by PFI_Optix on 2006-03-23
[QUOTE=MartinJ]gphpedit is available from the universe repository.  Use Synaptic to install it, a lot easier than building from source.

Have a look at this page if you need help enabling extra repositories -> [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)[/QUOTE]

Yeah, I actually found that and was editing my post to reflect it, but I'd still like to know why ./configure bombs out.

And not being able to connect to my file server is frustrating me ](*,)

---

### Post by MartinJ on 2006-03-23
Now I'm stuck, don't have much experience with either.  Maybe someone else can help you out. /M

---

### Post by KansasJoe on 2006-03-23
sudo apt-get install build-essential

It won't let you run make until you ./configure goes through and is successful

---

### Post by PFI_Optix on 2006-03-23
[QUOTE=KansasJoe]sudo apt-get install build-essential

It won't let you run make until you ./configure goes through and is successful[/QUOTE]

That seems to be working. I looked in the application installer for gcc and didn't find it.

edit: nevermind. Here are the last few lines when I run .configure now:

```
appending configuration tag "F77" to libtool
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
```

It's stuff like this they really need to make easy to find in the documentation.

---

### Post by KansasJoe on 2006-03-23
sudo basically is a temporary super user mode

note: you will also need parser perl for this program
dl it from [http://search.cpan.org/~msergeant/XML-Parser-2.34/Parser.pm](http://search.cpan.org/~msergeant/XML-Parser-2.34/Parser.pm)

then

tar xzf XML-Parser-2.34.tar.gz   (or right click on folder and select extract here)
perl Makefile.PL
make
sudo make install

there is an easier way to get this program but there's not a better feeling than compiling something yourself and the program always seems to work after compiling (always had trouble with mplayer til i compiled it myself)

i was actually posting this about parser while you were typing it in

---

### Post by PFI_Optix on 2006-03-23
Umm...that didn't work.

I downloaded the file into my home directory, and got this error from tar:

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

So I extracted it in the GUI without a problem. The perl command *seems* to work like it should, but I wouldn't know for certain.

If I try **make**, here's part of what i get (warning, it's rather long...most of it is errors though)

```
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
make[1]: Entering directory `/home/kpope/XML-Parser-2.34/Expat'
cp Expat.pm ../blib/lib/XML/Parser/Expat.pm
/usr/bin/perl /usr/share/perl/5.8.7/ExtUtils/xsubpp -noprototypes -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  Expat.xs > Expat.xsc && mv Expat.xsc Expat.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2  -DVERSION=\"2.34\" -DXS_VERSION=\"2.34\" -fPIC "-I/usr/lib/perl/5.8/CORE"   Expat.c
Expat.xs:12:19: error: expat.h: No such file or directory
Expat.xs:60: error: syntax error before ‘XML_Parser’
Expat.xs:60: warning: no semicolon at end of struct or union
Expat.xs:78: error: syntax error before ‘:’ token
Expat.xs:79: error: syntax error before ‘:’ token
Expat.xs:80: error: syntax error before ‘:’ token
Expat.xs:106: error: syntax error before ‘}’ token
Expat.xs:106: warning: data definition has no type or storage class
Expat.xs:111: error: syntax error before ‘nsdelim’
Expat.xs:111: warning: data definition has no type or storage class
Expat.xs:117: error: syntax error before ‘*’ token
Expat.xs:118: error: syntax error before ‘*’ token
Expat.xs:194: error: syntax error before ‘ms’
Expat.xs:194: warning: initialization makes integer from pointer without a cast
Expat.xs:194: warning: excess elements in scalar initializer
Expat.xs:194: warning: (near initialization for ‘ms’)
Expat.xs:194: warning: excess elements in scalar initializer
Expat.xs:194: warning: (near initialization for ‘ms’)
Expat.xs:194: warning: data definition has no type or storage class
Expat.xs:197: error: syntax error before ‘parser’
Expat.xs: In function ‘append_error’:
Expat.xs:200: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:200: error: (Each undeclared identifier is reported only once
Expat.xs:200: error: for each function it appears in.)
Expat.xs:203: error: syntax error before ‘)’ token
Expat.xs:210: error: ‘err’ undeclared (first use in this function)
Expat.xs:213: error: ‘parser’ undeclared (first use in this function)
Expat.xs: At top level:
Expat.xs:249: error: syntax error before ‘*’ token
Expat.xs: In function ‘generate_model’:
Expat.xs:255: error: ‘model’ undeclared (first use in this function)
Expat.xs:256: error: ‘XML_CQUANT_NONE’ undeclared (first use in this function)
Expat.xs:261: error: ‘XML_CTYPE_NAME’ undeclared (first use in this function)
Expat.xs:265: error: ‘XML_CTYPE_MIXED’ undeclared (first use in this function)
Expat.xs:266: error: ‘XML_CTYPE_CHOICE’ undeclared (first use in this function)
Expat.xs:267: error: ‘XML_CTYPE_SEQ’ undeclared (first use in this function)
Expat.xs: At top level:
Expat.xs:286: error: syntax error before ‘parser’
Expat.xs: In function ‘parse_stream’:
Expat.xs:298: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:301: error: syntax error before ‘)’ token
Expat.xs:311: error: ‘ioref’ undeclared (first use in this function)
Expat.xs:350: error: ‘parser’ undeclared (first use in this function)
Expat.xs:350: warning: initialization makes pointer from integer without a cast
Expat.xs: In function ‘characterData’:
Expat.xs:460: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:460: error: syntax error before ‘)’ token
Expat.xs: In function ‘startElement’:
Expat.xs:480: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:480: error: syntax error before ‘)’ token
Expat.xs: In function ‘endElement’:
Expat.xs:556: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:556: error: syntax error before ‘)’ token
Expat.xs: In function ‘processingInstruction’:
Expat.xs:590: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:590: error: syntax error before ‘)’ token
Expat.xs: In function ‘commenthandle’:
Expat.xs:611: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:611: error: syntax error before ‘)’ token
Expat.xs: In function ‘startCdata’:
Expat.xs:631: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:631: error: syntax error before ‘)’ token
Expat.xs: In function ‘endCdata’:
Expat.xs:651: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:651: error: syntax error before ‘)’ token
Expat.xs: At top level:
Expat.xs:668: error: syntax error before ‘*’ token
Expat.xs: In function ‘nsStart’:
Expat.xs:670: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:670: error: syntax error before ‘)’ token
Expat.xs:678: error: ‘prefix’ undeclared (first use in this function)
Expat.xs:679: error: ‘uri’ undeclared (first use in this function)
Expat.xs: At top level:
Expat.xs:688: error: syntax error before ‘*’ token
Expat.xs: In function ‘nsEnd’:
Expat.xs:690: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:690: error: syntax error before ‘)’ token
Expat.xs:698: error: ‘prefix’ undeclared (first use in this function)
Expat.xs: In function ‘defaulthandle’:
Expat.xs:710: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:710: error: syntax error before ‘)’ token
Expat.xs: At top level:
Expat.xs:729: error: syntax error before ‘XML_Content’
Expat.xs: In function ‘elementDecl’:
Expat.xs:731: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:731: error: syntax error before ‘)’ token
Expat.xs:738: error: ‘model’ undeclared (first use in this function)
Expat.xs:744: error: ‘name’ undeclared (first use in this function)
Expat.xs: In function ‘attributeDecl’:
Expat.xs:761: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:761: error: syntax error before ‘)’ token
Expat.xs: In function ‘entityDecl’:
Expat.xs:802: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:802: error: syntax error before ‘)’ token
Expat.xs: In function ‘doctypeStart’:
Expat.xs:831: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:831: error: syntax error before ‘)’ token
Expat.xs: In function ‘doctypeEnd’:
Expat.xs:852: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:852: error: syntax error before ‘)’ token
Expat.xs: In function ‘xmlDecl’:
Expat.xs:872: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:872: error: syntax error before ‘)’ token
Expat.xs: In function ‘unparsedEntityDecl’:
Expat.xs:901: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:901: error: syntax error before ‘)’ token
Expat.xs: In function ‘notationDecl’:
Expat.xs:929: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:929: error: syntax error before ‘)’ token
Expat.xs: At top level:
Expat.xs:960: error: syntax error before ‘parser’
Expat.xs: In function ‘externalEntityRef’:
Expat.xs:975: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:975: error: syntax error before ‘)’ token
Expat.xs:983: error: ‘pubid’ undeclared (first use in this function)
Expat.xs:985: error: ‘base’ undeclared (first use in this function)
Expat.xs:986: error: ‘sysid’ undeclared (first use in this function)
Expat.xs:1002: error: ‘parser’ undeclared (first use in this function)
Expat.xs:1004: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.xs:1004: error: syntax error before ‘entpar’
Expat.xs:1007: error: ‘entpar’ undeclared (first use in this function)
Expat.xs: At top level:
Expat.xs:1115: error: syntax error before ‘XML_Encoding’
Expat.xs: In function ‘unknownEncoding’:
Expat.xs:1123: error: ‘name’ undeclared (first use in this function)
Expat.xs:1167: error: ‘info’ undeclared (first use in this function)
Expat.xs: In function ‘recString’:
Expat.xs:1185: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1185: error: syntax error before ‘)’ token
Expat.xs: At top level:
Expat.xs:1196: error: syntax error before ‘*’ token
Expat.xs: In function ‘suspend_callbacks’:
Expat.xs:1197: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1199: error: ‘XML_CharacterDataHandler’ undeclared (first use in this function)
Expat.xs:1199: error: syntax error before numeric constant
Expat.xs:1204: error: ‘XML_ProcessingInstructionHandler’ undeclared (first use in this function)
Expat.xs:1204: error: syntax error before numeric constant
Expat.xs:1209: error: ‘XML_CommentHandler’ undeclared (first use in this function)
Expat.xs:1209: error: syntax error before numeric constant
Expat.xs:1215: error: ‘XML_StartCdataSectionHandler’ undeclared (first use in this function)
Expat.xs:1215: error: syntax error before numeric constant
Expat.xs:1221: error: ‘XML_UnparsedEntityDeclHandler’ undeclared (first use in this function)
Expat.xs:1221: error: syntax error before numeric constant
Expat.xs:1226: error: ‘XML_NotationDeclHandler’ undeclared (first use in this function)
Expat.xs:1226: error: syntax error before numeric constant
Expat.xs:1231: error: ‘XML_ExternalEntityRefHandler’ undeclared (first use in this function)
Expat.xs:1231: error: syntax error before numeric constant
Expat.xs: At top level:
Expat.xs:1237: error: syntax error before ‘*’ token
Expat.xs: In function ‘resume_callbacks’:
Expat.xs:1238: error: ‘cbv’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_ParserCreate’:
Expat.c:1290: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1290: error: syntax error before ‘RETVAL’
Expat.xs:1279: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1280: error: variable ‘pep’ has initializer but incomplete type
Expat.xs:1280: error: ‘XML_PARAM_ENTITY_PARSING_NEVER’ undeclared (first use in this function)
Expat.xs:1280: error: storage size of ‘pep’ isn’t known
Expat.xs:1284: error: syntax error before ‘)’ token
Expat.xs:1284: error: syntax error before ‘)’ token
Expat.xs:1320: error: ‘RETVAL’ undeclared (first use in this function)
Expat.xs:1337: error: ‘XML_PARAM_ENTITY_PARSING_UNLESS_STANDALONE’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_ParserRelease’:
Expat.c:1371: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1371: error: syntax error before ‘parser’
Expat.xs:1351: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1351: error: syntax error before ‘)’ token
Expat.c: In function ‘XS_XML__Parser__Expat_ParserFree’:
Expat.c:1390: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1390: error: syntax error before ‘parser’
Expat.xs:1361: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1361: error: syntax error before ‘)’ token
Expat.xs:1430: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_ParseString’:
Expat.c:1476: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1476: error: syntax error before ‘parser’
Expat.xs:1439: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1443: error: syntax error before ‘)’ token
Expat.xs:1446: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_ParseStream’:
Expat.c:1508: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1508: error: syntax error before ‘parser’
Expat.xs:1463: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1465: error: syntax error before ‘)’ token
Expat.xs:1473: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_ParsePartial’:
Expat.c:1543: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1543: error: syntax error before ‘parser’
Expat.xs:1488: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1488: error: syntax error before ‘)’ token
Expat.xs:1490: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_ParseDone’:
Expat.c:1571: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1571: error: syntax error before ‘parser’
Expat.xs:1504: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetStartElementHandler’:
Expat.c:1594: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1594: error: syntax error before ‘parser’
Expat.xs:1518: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1518: error: syntax error before ‘)’ token
Expat.c: In function ‘XS_XML__Parser__Expat_SetEndElementHandler’:
Expat.c:1615: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1615: error: syntax error before ‘parser’
Expat.xs:1529: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1529: error: syntax error before ‘)’ token
Expat.c: In function ‘XS_XML__Parser__Expat_SetCharacterDataHandler’:
Expat.c:1636: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1636: error: syntax error before ‘parser’
Expat.xs:1540: error: ‘XML_CharacterDataHandler’ undeclared (first use in this function)
Expat.xs:1540: error: syntax error before ‘charhndl’
Expat.xs:1541: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1541: error: syntax error before ‘)’ token
Expat.xs:1545: error: ‘charhndl’ undeclared (first use in this function)
Expat.xs:1547: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetProcessingInstructionHandler’:
Expat.c:1663: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1663: error: syntax error before ‘parser’
Expat.xs:1557: error: ‘XML_ProcessingInstructionHandler’ undeclared (first use in this function)
Expat.xs:1557: error: syntax error before ‘prochndl’
Expat.xs:1559: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1559: error: syntax error before ‘)’ token
Expat.xs:1563: error: ‘prochndl’ undeclared (first use in this function)
Expat.xs:1565: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetCommentHandler’:
Expat.c:1691: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1691: error: syntax error before ‘parser’
Expat.xs:1575: error: ‘XML_CommentHandler’ undeclared (first use in this function)
Expat.xs:1575: error: syntax error before ‘cmnthndl’
Expat.xs:1576: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1576: error: syntax error before ‘)’ token
Expat.xs:1580: error: ‘cmnthndl’ undeclared (first use in this function)
Expat.xs:1582: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetDefaultHandler’:
Expat.c:1718: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1718: error: syntax error before ‘parser’
Expat.xs:1592: error: ‘XML_DefaultHandler’ undeclared (first use in this function)
Expat.xs:1592: error: syntax error before ‘dflthndl’
Expat.xs:1593: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1593: error: syntax error before ‘)’ token
Expat.xs:1597: error: ‘dflthndl’ undeclared (first use in this function)
Expat.xs:1600: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetUnparsedEntityDeclHandler’:
Expat.c:1749: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1749: error: syntax error before ‘parser’
Expat.xs:1613: error: ‘XML_UnparsedEntityDeclHandler’ undeclared (first use in this function)
Expat.xs:1613: error: syntax error before ‘unprsdhndl’
Expat.xs:1615: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1615: error: syntax error before ‘)’ token
Expat.xs:1619: error: ‘unprsdhndl’ undeclared (first use in this function)
Expat.xs:1621: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetNotationDeclHandler’:
Expat.c:1777: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1777: error: syntax error before ‘parser’
Expat.xs:1631: error: ‘XML_NotationDeclHandler’ undeclared (first use in this function)
Expat.xs:1631: error: syntax error before ‘nothndlr’
Expat.xs:1632: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1632: error: syntax error before ‘)’ token
Expat.xs:1636: error: ‘nothndlr’ undeclared (first use in this function)
Expat.xs:1638: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetExternalEntityRefHandler’:
Expat.c:1804: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1804: error: syntax error before ‘parser’
Expat.xs:1648: error: ‘XML_ExternalEntityRefHandler’ undeclared (first use in this function)
Expat.xs:1648: error: syntax error before ‘exthndlr’
Expat.xs:1650: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1650: error: syntax error before ‘)’ token
Expat.xs:1654: error: ‘exthndlr’ undeclared (first use in this function)
Expat.xs:1656: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetExtEntFinishHandler’:
Expat.c:1832: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1832: error: syntax error before ‘parser’
Expat.xs:1666: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1666: error: syntax error before ‘)’ token
Expat.c: In function ‘XS_XML__Parser__Expat_SetEntityDeclHandler’:
Expat.c:1858: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1858: error: syntax error before ‘parser’
Expat.xs:1683: error: ‘XML_EntityDeclHandler’ undeclared (first use in this function)
Expat.xs:1683: error: syntax error before ‘enthndlr’
Expat.xs:1685: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1685: error: syntax error before ‘)’ token
Expat.xs:1689: error: ‘enthndlr’ undeclared (first use in this function)
Expat.xs:1691: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetElementDeclHandler’:
Expat.c:1886: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1886: error: syntax error before ‘parser’
Expat.xs:1701: error: ‘XML_ElementDeclHandler’ undeclared (first use in this function)
Expat.xs:1701: error: syntax error before ‘eldeclhndlr’
Expat.xs:1703: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1703: error: syntax error before ‘)’ token
Expat.xs:1707: error: ‘eldeclhndlr’ undeclared (first use in this function)
Expat.xs:1709: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetAttListDeclHandler’:
Expat.c:1914: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1914: error: syntax error before ‘parser’
Expat.xs:1719: error: ‘XML_AttlistDeclHandler’ undeclared (first use in this function)
Expat.xs:1719: error: syntax error before ‘attdeclhndlr’
Expat.xs:1721: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1721: error: syntax error before ‘)’ token
Expat.xs:1725: error: ‘attdeclhndlr’ undeclared (first use in this function)
Expat.xs:1727: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetDoctypeHandler’:
Expat.c:1942: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1942: error: syntax error before ‘parser’
Expat.xs:1737: error: ‘XML_StartDoctypeDeclHandler’ undeclared (first use in this function)
Expat.xs:1737: error: syntax error before ‘dtsthndlr’
Expat.xs:1739: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1739: error: syntax error before ‘)’ token
Expat.xs:1744: error: ‘dtsthndlr’ undeclared (first use in this function)
Expat.xs:1746: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetEndDoctypeHandler’:
Expat.c:1971: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1971: error: syntax error before ‘parser’
Expat.xs:1756: error: ‘XML_EndDoctypeDeclHandler’ undeclared (first use in this function)
Expat.xs:1756: error: syntax error before ‘dtendhndlr’
Expat.xs:1758: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1758: error: syntax error before ‘)’ token
Expat.xs:1762: error: ‘dtendhndlr’ undeclared (first use in this function)
Expat.xs:1764: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetXMLDeclHandler’:
Expat.c:1999: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:1999: error: syntax error before ‘parser’
Expat.xs:1775: error: ‘XML_XmlDeclHandler’ undeclared (first use in this function)
Expat.xs:1775: error: syntax error before ‘xmldechndlr’
Expat.xs:1777: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1777: error: syntax error before ‘)’ token
Expat.xs:1781: error: ‘xmldechndlr’ undeclared (first use in this function)
Expat.xs:1783: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetBase’:
Expat.c:2027: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2027: error: syntax error before ‘parser’
Expat.xs:1803: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_GetBase’:
Expat.c:2054: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2054: error: syntax error before ‘parser’
Expat.xs:1812: error: ‘parser’ undeclared (first use in this function)
Expat.xs:1812: warning: initialization makes pointer from integer without a castExpat.c: In function ‘XS_XML__Parser__Expat_PositionContext’:
Expat.c:2080: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2080: error: syntax error before ‘parser’
Expat.xs:1829: error: ‘parser’ undeclared (first use in this function)
Expat.xs:1829: warning: initialization makes pointer from integer without a castExpat.c: In function ‘XS_XML__Parser__Expat_DefaultCurrent’:
Expat.c:2194: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2194: error: syntax error before ‘parser’
Expat.xs:1920: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1920: error: syntax error before ‘)’ token
Expat.xs:1922: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_RecognizedString’:
Expat.c:2213: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2213: error: syntax error before ‘parser’
Expat.xs:1930: error: ‘XML_DefaultHandler’ undeclared (first use in this function)
Expat.xs:1930: error: syntax error before ‘dflthndl’
Expat.xs:1931: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:1931: error: syntax error before ‘)’ token
Expat.xs:1934: error: ‘dflthndl’ undeclared (first use in this function)
Expat.xs:1942: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_GetErrorCode’:
Expat.c:2256: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2256: error: syntax error before ‘parser’
Expat.c:2260: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_GetCurrentLineNumber’:
Expat.c:2273: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2273: error: syntax error before ‘parser’
Expat.c:2277: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_GetCurrentColumnNumber’:
Expat.c:2290: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2290: error: syntax error before ‘parser’
Expat.c:2294: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_GetCurrentByteIndex’:
Expat.c:2307: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2307: error: syntax error before ‘parser’
Expat.c:2311: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_GetSpecifiedAttributeCount’:
Expat.c:2324: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2324: error: syntax error before ‘parser’
Expat.c:2328: error: ‘parser’ undeclared (first use in this function)
Expat.xs: In function ‘XS_XML__Parser__Expat_ErrorString’:
Expat.xs:1983: warning: initialization makes pointer from integer without a castExpat.c: In function ‘XS_XML__Parser__Expat_OriginalString’:
Expat.c:2484: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2484: error: syntax error before ‘parser’
Expat.xs:2091: error: ‘parser’ undeclared (first use in this function)
Expat.xs:2091: warning: initialization makes pointer from integer without a castExpat.c: In function ‘XS_XML__Parser__Expat_SetStartCdataHandler’:
Expat.c:2512: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2512: error: syntax error before ‘parser’
Expat.xs:2109: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:2109: error: syntax error before ‘)’ token
Expat.xs:2110: error: ‘XML_StartCdataSectionHandler’ undeclared (first use in this function)
Expat.xs:2115: error: ‘scdhndl’ undeclared (first use in this function)
Expat.xs:2117: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_SetEndCdataHandler’:
Expat.c:2540: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2540: error: syntax error before ‘parser’
Expat.xs:2127: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:2127: error: syntax error before ‘)’ token
Expat.xs:2128: error: ‘XML_EndCdataSectionHandler’ undeclared (first use in this function)
Expat.xs:2133: error: ‘ecdhndl’ undeclared (first use in this function)
Expat.xs:2135: error: ‘parser’ undeclared (first use in this function)
Expat.c: In function ‘XS_XML__Parser__Expat_UnsetAllHandlers’:
Expat.c:2568: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2568: error: syntax error before ‘parser’
Expat.xs:2144: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:2144: error: syntax error before ‘)’ token
Expat.xs:2149: error: ‘XML_StartNamespaceDeclHandler’ undeclared (first use in this function)
Expat.xs:2149: error: syntax error before numeric constant
Expat.xs:2153: error: ‘parser’ undeclared (first use in this function)
Expat.xs:2154: error: ‘XML_StartElementHandler’ undeclared (first use in this function)
Expat.xs:2154: error: syntax error before numeric constant
Expat.xs:2158: error: ‘XML_UnknownEncodingHandler’ undeclared (first use in this function)
Expat.xs:2158: error: syntax error before numeric constant
Expat.c: In function ‘XS_XML__Parser__Expat_ElementIndex’:
Expat.c:2600: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2600: error: syntax error before ‘parser’
Expat.xs:2167: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:2167: error: syntax error before ‘)’ token
Expat.c: In function ‘XS_XML__Parser__Expat_SkipUntil’:
Expat.c:2621: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2621: error: syntax error before ‘parser’
Expat.xs:2179: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:2179: error: syntax error before ‘)’ token
Expat.c: In function ‘XS_XML__Parser__Expat_Do_External_Parse’:
Expat.c:2643: error: ‘XML_Parser’ undeclared (first use in this function)
Expat.c:2643: error: syntax error before ‘parser’
Expat.xs:2194: error: ‘cbv’ undeclared (first use in this function)
Expat.xs:2194: error: syntax error before ‘)’ token
Expat.xs:2197: error: ‘parser’ undeclared (first use in this function)
make[1]: *** [Expat.o] Error 1
make[1]: Leaving directory `/home/kpope/XML-Parser-2.34/Expat'
make: *** [subdirs] Error 2
```

---

### Post by KansasJoe on 2006-03-23
you got me stumped...i just reinstalled mine to make sure it worked and it did

perl Makefile.PL
make
sudo make install


maybe redownload the file?

---

### Post by PFI_Optix on 2006-03-24
Okay, I caught the first error message from running **make** this time.

"Error: expat.h: file or directory not found"

(may not be verbatim)

The package installed with Synaptic doesn't work right. Text keeps moving and disappearing as I type and the text cursor is never in the right place. It word-wrapped a five-character line.

This is frustrating. The whole point in going Linux was to have a solid development platform for my work in PHP, complete with a local web server. Figures that nothing works as advertised...that's been my experience with Linux on every attempt I've made at adopting it.

---

### Post by PFI_Optix on 2006-03-24
Okay...starting from scratch this morning.

Thought I'd try going from the ground up. I reinstalled the perl package this morning and grabbed another copy of the XML Parser tarball. Unpacked it, ran the commands above, got the same result.

---

### Post by PFI_Optix on 2006-03-28
Well, I figured out what one problem was.  There's GtkHTML2 dependency with gPHPedit. So I tried to install that, got this error:

```
configure: error: Library requirements (gtk+-2.0 >= 2.1.0 libxml-2.0 >= 2.4.16) 
not met; consider adjusting the PKG_CONFIG_PATH environment variable if your 
libraries are in a nonstandard prefix so pkg-config can find them.
```

All I wanted was an easy-to-use development OS :(

---

### Post by Mustard on 2006-03-28
So I take it there is a reason you don't want to install gphpedit using the package available in the repositories?

---

### Post by PFI_Optix on 2006-03-28
[QUOTE=Mustard]So I take it there is a reason you don't want to install gphpedit using the package available in the repositories?[/QUOTE]

Because the one it installs doesn't work right.

Read above, the text cursor moves all over the page when I type, which makes it impossible to know where the cursor actually is without moving it, and it word wraps at random. Example:

```
<?ph
-p
This shou
-ldn't be word wrapped, but it is.
The cursor should be at the end of this line, but it's up by the ?.
```

---

### Post by Mustard on 2006-03-28
[QUOTE=PFI_Optix]Because the one it installs doesn't work right.

Read above, the text cursor moves all over the page when I type, which makes it impossible to know where the cursor actually is without moving it, and it word wraps at random. Example:

```
<?ph
-p
This shou
-ldn't be word wrapped, but it is.
The cursor should be at the end of this line, but it's up by the ?.
```[/QUOTE]

Well that does look bothersome. :)

When you get the dependency errors are you installing the dependencies using packages from the repos or are you downloading the dependencies and attempting to install them manually as well?

Note:- skip to the bottom where I finally worked it out.

-edit-

Looking over your dependencies and searching for them at [http://packages.ubuntu.com](http://packages.ubuntu.com) I wonder whether they are a bit too recent to be available in the repositories.  I guess you are discovering the true meaning of the phrase 'dependency hell'. :)

I wonder whether there is a less bleeding edge version of gphpedit, that will allow you to use the dependencies from the repositories.

-edit2-

If I am reading the line above correctly, it would seem that the version of libxml its asking for is even beyond that which is being used in the Dapper development release of Ubuntu. o_0

-edit3-

Ah no..its ok..I found the libxml2-dev package in Breezy. :)

-edit4-
I'll revise my first thoughts.  It seems you can get past these issues with Breezy.  I was just showing my ignorance of the latest versions earlier. :D

Ok, I think you need the libxml2-dev and libgtk2.0-dev packages installed, to get past those dependencies.  Compiling from source is just so much fun! :P

You could probably save yourself some grief by installing **libgtkhtml2-dev** and just satisfy the gtkhtml2 dependency that way. Or even go back one step further and install **libxml-perl** for when you hit the [noparse]XML::parser dependency.[/noparse]

A liberal use of the apt-cache search function in command line should help you get through dependency issues.  For something like the xml parser dependency problem I would have done this...

```
apt-cache search xml | grep perl
```

From there you can try to work out which package might fill that dependency.  Mostly when compiling from source you are going to need to install a lot of development packages, which use the notation 'packagename-dev'.

---

### Post by andyjeffries on 2006-06-29
The current version in the repository (0.9.80) should be fine.  Let me know if you still have any issues and I'll try to help.

---

### Post by andyjeffries on 2006-07-06
Also, I've just released 0.9.91 which should definitely fix all display problems like this.  [www.gphpedit.org](www.gphpedit.org)

---

