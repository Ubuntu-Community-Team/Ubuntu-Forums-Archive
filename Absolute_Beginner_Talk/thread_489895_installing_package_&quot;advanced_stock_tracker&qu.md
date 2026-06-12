---
title: "installing package &quot;advanced stock tracker&quot; in debian"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by miesnerd on 2007-07-01
So I downloaded a package  to "/home/justin/Desktop/ast-0.2.8-src.tar.gz" and extracted it to the Desktop. Inside the folder, there is a file called "install.pl" and i tried running it in terminal, with nothing. Then, I opened a terminal, got to the directory, and tried to "./comiple" then "sudo make" then sudo make install". I got nothing. Ive have relatively little success manually installing programs from source. Can I get a little help?

Miesnerd

---

### Post by AlexenderReez on 2007-07-01
try to find readme or any text in that folder.......

---

### Post by Raineer on 2007-07-01
Just in case you didn't mess up typing, it's ./configure, not ./compile

But yeah, typically there is a README or INSTALL text file

---

### Post by oilchangeguy on 2007-07-01
add/remove has linux trade. and qtstalker, listed. you might try one of those.

---

### Post by wron_00 on 2007-07-07
w/ QTstalker, this probably sounds really dumb, but can't get any charts to pop up.  What do I enter and what settings do I need to get this puppy showing me some stocks?  I feel like a complete idiot but have jacked w/ this thing for over an hour, trying to get it to download something updates from Yahoo and the other ones listed.  Do I need to enter symbols somewhere?  Will this program allow me to search through leading groups according to Volume fluctuations, RS fluctuations, and crossing of the Moving Average to what I set it at?

I have a lot of questions, because I need a lot of help.  Thanks to anyone that can help me out on some of this.

Newby Justin

---

### Post by PM81 on 2007-12-15
Hello,

I'm relatively new on ubuntu and want to install "advanced stock tracker" but have som problems at the moment I want to "make".

This is the last part of the terminal output I get:


creating librisk.la
(cd .libs && rm -f librisk.la && ln -s ../librisk.la librisk.la)
make[1]: Leaving directory `/home/pieter/ast-0.3.0_pre1/src/librisk'
Making all in afetch
make[1]: Entering directory `/home/pieter/ast-0.3.0_pre1/src/afetch'
g++ -DHAVE_CONFIG_H -I. -I../libawf -I../src -I../ -I/usr/include/libxml2 -I/usr/local/include    -g -O2 -MT afetch.o -MD -MP -MF .deps/afetch.Tpo -c -o afetch.o afetch.cc
mv -f .deps/afetch.Tpo .deps/afetch.Po
/bin/bash ../libtool --tag=CXX   --mode=link g++  -g -O2 -L/usr/lib -lxml2 -L/usr/local/lib -lcurl -lmhash -rdynamic  -all-static -pthread -fno-merge-constants  -o afetch afetch.o cliparse.o ../libadbe/libadbe.la ../libaqe/libaqe.la ../libast-cache/libast-cache.la ../libatf/libatf.la ../libawf/libawf.la ../libopenfdb/libopenfdb.la -L/usr/lib/ta-lib -lta_common_csr -lta_func_csr -lta_libc_csr ../gsoap-2.7/soapcpp2/libgsoap++.a -lz 
g++ -g -O2 -rdynamic -static -pthread -fno-merge-constants -o afetch afetch.o cliparse.o  -L/usr/lib -L/usr/local/lib ../libadbe/.libs/libadbe.a ../libaqe/.libs/libaqe.a /home/pieter/ast-0.3.0_pre1/src/libast-cache/.libs/libast-cache.a /home/pieter/ast-0.3.0_pre1/src/libawf/.libs/libawf.a /home/pieter/ast-0.3.0_pre1/src/libatf/.libs/libatf.a -L/usr/lib/ta-lib ../libast-cache/.libs/libast-cache.a ../libatf/.libs/libatf.a ../libawf/.libs/libawf.a /usr/lib/libxml2.a /usr/local/lib/libcurl.a -lpng12 /usr/local/lib/libgd.a /usr/local/lib/libpng12.a /usr/local/lib/libmhash.a -L/home/pieter/ast-0.3.0_pre1/src/libatf /usr/local/lib/libatf.a ../libopenfdb/.libs/libopenfdb.a /home/pieter/ast-0.3.0_pre1/src/libadbe/.libs/libadbe.a -lta_common_csr -lta_func_csr -lta_libc_csr ../gsoap-2.7/soapcpp2/libgsoap++.a -lz
/usr/bin/ld: cannot find -lta_func_csr
collect2: ld returned 1 exit status
make[1]: *** [afetch] Error 1
make[1]: Leaving directory `/home/pieter/ast-0.3.0_pre1/src/afetch'
make: *** [all-recursive] Error 1
root@telenetPC:~/ast-0.3.0_pre1/src# 


I also tried the install.pl with the perl command and get this output 

checking for disable namespaces in library... no
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating gsoap.pc
config.status: creating gsoap++.pc
config.status: creating gsoapck.pc
config.status: creating gsoapck++.pc
config.status: creating gsoapssl.pc
config.status: creating gsoapssl++.pc
config.status: creating soapcpp2/Makefile
config.status: WARNING:  soapcpp2/Makefile.in seems to ignore the --datarootdir setting
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
Making all in gsoap-2.7
make[1]: Entering directory `/var/www/ast-0.3.0_pre1/src/gsoap-2.7'
make  all-recursive
make[2]: Entering directory `/var/www/ast-0.3.0_pre1/src/gsoap-2.7'
Making all in soapcpp2
make[3]: Entering directory `/var/www/ast-0.3.0_pre1/src/gsoap-2.7/soapcpp2'
ln -s ./stdsoap2.cpp stdsoap2_cpp.cpp
ln: creating symbolic link `stdsoap2_cpp.cpp' to `./stdsoap2.cpp': File exists
make[3]: *** [stdsoap2_cpp.cpp] Error 1
make[3]: Leaving directory `/var/www/ast-0.3.0_pre1/src/gsoap-2.7/soapcpp2'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/www/ast-0.3.0_pre1/src/gsoap-2.7'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/var/www/ast-0.3.0_pre1/src/gsoap-2.7'
make: *** [all-recursive] Error 1
---------------------------------------------------------------------
-                           ERROR OCCURED                           -
---------------------------------------------------------------------
- Installation failed with error:                                   -
- Failed to run make
-                                                                   -
- Please report this bug to:                                        -
-       [email]ast-users@lists.sourceforge.net[/email]                             -
- or    [http://sourceforge.net/tracker/?group_id=148045&atid=770268](http://sourceforge.net/tracker/?group_id=148045&atid=770268) -
---------------------------------------------------------------------
Died at install.pl line 20, <STDIN> line 2.
root@telenetPC:/var/www/ast-0.3.0_pre1# 


I installed the depencies like apache, gnuplot4, zlib, libcurl, libxml2, TA-Lib, mhash, sendmail, libsssh, openssl, gd, libjpeg, libpng, autoconfig, automake and gsoap correctly

I really do not know what the problem is. Can somebody help me?

---

### Post by schorsch on 2007-12-15
Are the development packages of the dependencies installed, too?

---

### Post by PM81 on 2007-12-15
No I did download the source code and did "configure, make and make install" on all the packages and encoutered no errors. I thought  that this was enough.

How do I install the develepment package? On the same way? Do I need to do that for all the packages?

Maybe this is also important to know: the first output I get when I "make" the AST code not in the /var/www directory but in my home directory. The second output is started from the /var/www directory as is mentioned on the website of Advanced stock tracker.

---

### Post by schorsch on 2007-12-16
Can you please provide a link so that I can download the source and compile it? I would try to compile with the official ubuntu packages instead of compiling every dependency ....

---

### Post by PM81 on 2007-12-16
The link: [http://downloads.sourceforge.net/ast/ast-src-0.3.0_pre1.tar.gz?modtime=1190579538&big_mirror=0](http://downloads.sourceforge.net/ast/ast-src-0.3.0_pre1.tar.gz?modtime=1190579538&big_mirror=0)

I did install some extra packages to be sure my apache server works fine

I also did a test to see if ta-lib is installed correctly by running ta_regtest 

and now I get following output. 

/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../libawf -I../src -I../ -I/include/ta-lib -DHAVE_CONFIG_H   -O2 -g0 -pipe -MT test.lo -MD -MP -MF .deps/test.Tpo -c -o test.lo test.cc
tafn.cc:22:23: error: ta_common.h: No such file or directory
tafn.cc:23:21: error: ta_func.h: No such file or directory
tafn.cc:24:21: error: ta_libc.h: No such file or directory
tafn.cc: In constructor 'ta_init::ta_init()':
tafn.cc:41: error: 'TA_Initialize' was not declared in this scope
tafn.cc: In destructor 'ta_init::~ta_init()':
tafn.cc:47: error: 'TA_Shutdown' was not declared in this scope
tafn.cc: In function 'void obv(const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >, std::vector<double, std::allocator<double> >&)':
tafn.cc:82: error: 'TA_OBV' was not declared in this scope
tafn.cc:82: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'void moving_average(const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, moving_average_type, int)':
tafn.cc:110: error: 'TA_MAType' was not declared in this scope
tafn.cc:110: error: 'TA_MA' was not declared in this scope
tafn.cc:110: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'void macd(const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, int, int, int)':
tafn.cc:126: error: 'TA_MACDFIX' was not declared in this scope
tafn.cc:126: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'void stochastic(const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, int, int, int)':
tafn.cc:146: error: 'TA_MAType_EMA' was not declared in this scope
tafn.cc:146: error: 'TA_STOCH' was not declared in this scope
tafn.cc:146: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'void rsi(const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, int)':
tafn.cc:160: error: 'TA_RSI' was not declared in this scope
tafn.cc:160: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'void bollinger_bands(const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, int)':
tafn.cc:175: error: 'TA_REAL_DEFAULT' was not declared in this scope
tafn.cc:175: error: 'TA_MAType_SMA' was not declared in this scope
tafn.cc:175: error: 'TA_BBANDS' was not declared in this scope
tafn.cc:175: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'void williams_r(const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, int)':
tafn.cc:193: error: 'TA_WILLR' was not declared in this scope
tafn.cc:193: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'void money_flow_index(const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, int)':
tafn.cc:213: error: 'TA_MFI' was not declared in this scope
tafn.cc:213: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'void momentum(const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, int)':
tafn.cc:226: error: 'TA_MOM' was not declared in this scope
tafn.cc:226: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'void parabolic_sar(const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, double, double)':
tafn.cc:242: error: 'TA_SAR' was not declared in this scope
tafn.cc:242: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'void adx(const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, int)':
tafn.cc:260: error: 'TA_ADX' was not declared in this scope
tafn.cc:260: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'void adxr(const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, const std::vector<double, std::allocator<double> >&, std::vector<double, std::allocator<double> >&, int)':
tafn.cc:278: error: 'TA_ADXR' was not declared in this scope
tafn.cc:278: error: 'TA_SUCCESS' was not declared in this scope
tafn.cc: In function 'double linest_slope(const std::vector<double, std::allocator<double> >&)':
tafn.cc:290: error: 'TA_LINEARREG_SLOPE' was not declared in this scope
tafn.cc:290: error: 'TA_SUCCESS' was not declared in this scope
make[1]: *** [tafn.lo] Error 1
make[1]: *** Waiting for unfinished jobs....
 g++ -DHAVE_CONFIG_H -I. -I../libawf -I../src -I../ -I/include/ta-lib -DHAVE_CONFIG_H -O2 -g0 -pipe -MT test.lo -MD -MP -MF .deps/test.Tpo -c test.cc -o test.o
mv -f .deps/symbolrecord.Tpo .deps/symbolrecord.Plo
mv -f .deps/test.Tpo .deps/test.Plo
make[1]: Leaving directory `/home/pieter/ast-0.3.0_pre1/src/libaqe'
make: *** [all-recursive] Error 1
---------------------------------------------------------------------
-                           ERROR OCCURED                           -
---------------------------------------------------------------------
- Installation failed with error:                                   -
- Failed to run make
-                                                                   -
- Please report this bug to:                                        -
-       [email]ast-users@lists.sourceforge.net[/email]                             -
- or    [http://sourceforge.net/tracker/?group_id=148045&atid=770268](http://sourceforge.net/tracker/?group_id=148045&atid=770268) -
---------------------------------------------------------------------
Died at install.pl line 20, <STDIN> line 2.
root@telenetPC:~/ast-0.3.0_pre1#

---

