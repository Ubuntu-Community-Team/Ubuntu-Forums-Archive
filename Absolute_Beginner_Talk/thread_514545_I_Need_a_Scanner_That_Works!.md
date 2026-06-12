---
title: "I Need a Scanner That Works!"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by vgrisham on 2007-07-31
As the proud owner of an Epson Perfection Photo printer that worked flawlessly in Dapper but won't give me the time of day in Feisty, I need a recommendation of a photo quality scanner that works "out of the box" in Feisty. I'd like to get it good and broke in so that when it stops working in Gutsy, I can switch back to the Epson, which will undoubtedly start working as soon as I plop down cash for something else. 

If you have a scanner that works well in Feisty, I'd appreciate your help. It's a little humiliating having to borrow my wife's XP laptop to use my scanner. 

Thanks in advance.

---

### Post by pollywog on 2007-07-31
Well I've got a (flatbed) scanner printer combo HPc3150 I got at Sam's for like 60 or 70 bucks. It uses the driver for a C3100, but I think it works great- Good Value. I've always had pretty good luck with HP products. They don't seem to have an axe to grind with Linux- P.W.

---

### Post by the.phantom on 2007-07-31
i'd make sure it is on this list

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

we use the sane for xsane on the scans

---

### Post by jimrz on 2007-07-31
don't see listed on the previously mentioned link, but I have a HP psc 1610 printer/scanner/copier that works quite well on all functions. the scanner , using HPLIP Toolbox utility, functions flawlessly in feisty

---

### Post by lemmy999 on 2007-08-01
I am using an Epson CX3200 under Xsane which works really well

---

### Post by stevebakerj on 2007-08-01
> **vgrisham said:**
> As the proud owner of an Epson Perfection Photo printer that worked flawlessly in Dapper but won't give me the time of day in Feisty, I need a recommendation of a photo quality scanner that works "out of the box" in Feisty. I'd like to get it good and broke in so that when it stops working in Gutsy, I can switch back to the Epson, which will undoubtedly start working as soon as I plop down cash for something else. 

If you have a scanner that works well in Feisty, I'd appreciate your help. It's a little humiliating having to borrow my wife's XP laptop to use my scanner. 

Thanks in advance.

You dont tell use what model it is, is it here:

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

if it is the rest should be easy. Ive just installed the RX700 scanner driver in 2 minutes.

---

### Post by rasdol on 2007-08-01
I use a EPSON RX620 combo. it works perfect! If you need information how to install - welcome

---

### Post by gjtoth on 2007-08-01
I, too, have the Epson RX620 that worked fine under Feisty.  I am helping test Gutsy and it doesn't work with it.  I'm sure the devs will have it fixed by the time of final release though.

---

### Post by starfry on 2007-08-01
I have an HP7210 officejet and I can report that scanning works fine with HPLIP and XSane.

---

### Post by MLX on 2007-08-01
I don't know what model you are using but I am using a Epson Perfection 2400 photo scanner and it works well with Feisty.

---

### Post by overdrank on 2007-08-01
> **vgrisham said:**
> As the proud owner of an Epson Perfection Photo printer that worked flawlessly in Dapper but won't give me the time of day in Feisty, I need a recommendation of a photo quality scanner that works "out of the box" in Feisty. I'd like to get it good and broke in so that when it stops working in Gutsy, I can switch back to the Epson, which will undoubtedly start working as soon as I plop down cash for something else. 

If you have a scanner that works well in Feisty, I'd appreciate your help. It's a little humiliating having to borrow my wife's XP laptop to use my scanner. 

Thanks in advance.

Hi and I guess I have been lucky but my HP psc 1210 all in one has worked in dapper, edgy, and now feisty. I have to knock on wood and hope that it continues to work. :)

---

### Post by BobLand on 2007-08-01
I have an old Epson Perfection.  Worked fine the first time I used it in fiesty.  I'm guessing you have bad, missing or corrupt drivers.  I'd check that out before buying a new scanner.  

Remember, the drivers for a new scanner will most likely NOT have linux drivers so you could be in the same boat but now with 2 boat anchors.

Perfection drivers are standard with fiesty.  Try purging them then reinstalling.  Perhaps, something else got installed and overwrote part of the driver.

Sometimes, problems are right under out noses but we can't see them.

bobland

---

### Post by vgrisham on 2007-08-02
To all who responded asking what scanner I'm using; it's an epson perfection 2580 photo scanner. I followed [these]("http://ubuntuforums.org/showthread.php?p=3121914#post3121914") instructions at  with no luck. What does Avasys do?

---

### Post by vgrisham on 2007-08-02
> **BobLand said:**
> I have an old Epson Perfection.  Worked fine the first time I used it in fiesty.  I'm guessing you have bad, missing or corrupt drivers.  I'd check that out before buying a new scanner.  

Remember, the drivers for a new scanner will most likely NOT have linux drivers so you could be in the same boat but now with 2 boat anchors.

Perfection drivers are standard with fiesty.  Try purging them then reinstalling.  Perhaps, something else got installed and overwrote part of the driver.

Sometimes, problems are right under out noses but we can't see them.

bobland

bobland, how does one go about purging drivers?

---

### Post by vgrisham on 2007-08-02
> **stevebakerj said:**
> You dont tell use what model it is, is it here:

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

if it is the rest should be easy. Ive just installed the RX700 scanner driver in 2 minutes.

Steve, 

Thanks for this link. I have an Epson Perfection 2580 Photo. I found it on the site you referenced. There are alternate files based upon what "GCC" my scanner has. What is a GCC and how can I tell which one to use?

---

### Post by stevebakerj on 2007-08-03
> **vgrisham said:**
> Steve, 

Thanks for this link. I have an Epson Perfection 2580 Photo. I found it on the site you referenced. There are alternate files based upon what "GCC" my scanner has. What is a GCC and how can I tell which one to use?

Its just the GNU C Compiler used, I assume you using Feisty so go for the 3.4 or later (current is 3.4.6).

so d/l:  

iscan-2.8.0-1.c2.i386.rpm 

and follow the instruction given in the pdf file:

userg_revG_e.pdf

AVASYS are an Epson Seiko company (Advanced Added Value System) they have a message board for scanners here:

[http://www.avasys.jp/english/linux_e/bbs_scan.html](http://www.avasys.jp/english/linux_e/bbs_scan.html)

---

### Post by vgrisham on 2007-08-03
> **stevebakerj said:**
> Its just the GNU C Compiler used, I assume you using Feisty so go for the 3.4 or later (current is 3.4.6).

so d/l:  

iscan-2.8.0-1.c2.i386.rpm 

and follow the instruction given in the pdf file:

userg_revG_e.pdf




Yep, I'm using Feisty. I downloaded the file you suggested. Here's what I get after executing "sudo rpm -i iscan-2.8.0-1.c2.i386.rpm":

error: Failed dependencies:
        /bin/sh is needed by iscan-2.8.0-1.c2.i386
        libatk-1.0.so.0 is needed by iscan-2.8.0-1.c2.i386
        libc.so.6 is needed by iscan-2.8.0-1.c2.i386
        libc.so.6(GLIBC_2.0) is needed by iscan-2.8.0-1.c2.i386
        libc.so.6(GLIBC_2.1) is needed by iscan-2.8.0-1.c2.i386
        libc.so.6(GLIBC_2.1.3) is needed by iscan-2.8.0-1.c2.i386
        libc.so.6(GLIBC_2.2) is needed by iscan-2.8.0-1.c2.i386
        libc.so.6(GLIBC_2.3) is needed by iscan-2.8.0-1.c2.i386
        libc.so.6(GLIBC_2.3.4) is needed by iscan-2.8.0-1.c2.i386
        libdl.so.2 is needed by iscan-2.8.0-1.c2.i386
        libdl.so.2(GLIBC_2.0) is needed by iscan-2.8.0-1.c2.i386
        libdl.so.2(GLIBC_2.1) is needed by iscan-2.8.0-1.c2.i386
        libgcc_s.so.1 is needed by iscan-2.8.0-1.c2.i386
        libgcc_s.so.1(GCC_3.0) is needed by iscan-2.8.0-1.c2.i386
        libgdk-x11-2.0.so.0 is needed by iscan-2.8.0-1.c2.i386
        libgdk_pixbuf-2.0.so.0 is needed by iscan-2.8.0-1.c2.i386
        libglib-2.0.so.0 is needed by iscan-2.8.0-1.c2.i386
        libgmodule-2.0.so.0 is needed by iscan-2.8.0-1.c2.i386
        libgobject-2.0.so.0 is needed by iscan-2.8.0-1.c2.i386
        libgtk-x11-2.0.so.0 is needed by iscan-2.8.0-1.c2.i386
        libieee1284.so.3 is needed by iscan-2.8.0-1.c2.i386
        libjpeg.so.62 is needed by iscan-2.8.0-1.c2.i386
        libm.so.6 is needed by iscan-2.8.0-1.c2.i386
        libm.so.6(GLIBC_2.0) is needed by iscan-2.8.0-1.c2.i386
        libnsl.so.1 is needed by iscan-2.8.0-1.c2.i386
        libpango-1.0.so.0 is needed by iscan-2.8.0-1.c2.i386
        libpangox-1.0.so.0 is needed by iscan-2.8.0-1.c2.i386
        libpangoxft-1.0.so.0 is needed by iscan-2.8.0-1.c2.i386
        libstdc++.so.6 is needed by iscan-2.8.0-1.c2.i386
        libstdc++.so.6(CXXABI_1.3) is needed by iscan-2.8.0-1.c2.i386
        libstdc++.so.6(GLIBCXX_3.4) is needed by iscan-2.8.0-1.c2.i386
        libusb-0.1.so.4 is needed by iscan-2.8.0-1.c2.i386
        sane-backends is needed by iscan-2.8.0-1.c2.i386

Help?

---

### Post by Bachstelze on 2007-08-03
Before you go through all that hassle, could you please tell us what your scanner does instead of scanning when you fire up e.g. xsane ? It is likely to be a known issue which will be easy to work around.

---

### Post by mar225 on 2007-08-03
Take a look at vuescan.com   It may cost a few dollars but after fighting ubuntu for months to get my scanner to work I bought it. Two minutes later I had a working scanner.... They have a trial version so you have nothing to lose.

---

### Post by vgrisham on 2007-08-04
> **HymnToLife said:**
> Before you go through all that hassle, could you please tell us what your scanner does instead of scanning when you fire up e.g. xsane ? It is likely to be a known issue which will be easy to work around.

Well when I run sane-find-scanner, it shows up: found USB scanner (vendor=0x04b8 [EPSON], product=0x0121 [EPSON Scanner]) at libusb:002:005)

But when I start xane, I get the message "Failed to open device 'snapscan:libusb:002:005': Invalid argument.

This has been a major issue for the Epson 2580, and there is a Feisty bug report on it with medium importance (kiss of death). Seeing the Avasys site has motivated me to try to salvage this thing though.

Thanks for asking.

---

### Post by vgrisham on 2007-08-04
> **mar225 said:**
> Take a look at vuescan.com   It may cost a few dollars but after fighting ubuntu for months to get my scanner to work I bought it. Two minutes later I had a working scanner.... They have a trial version so you have nothing to lose.

That url didn't work for me. Do you mean hamrick.com?

---

### Post by vgrisham on 2007-08-04
vuescan looks promising, but it didn't work. It locked up as soon as it tried to initiate my scanner, which made a brief sound as if it were going to warm up but then started blinking rapid red, which, being the technical genius that I am, I deduce is bad. vuescan won't even launch after that, and I had to xkill it. 

But thanks for the lead. I appreciate your help.

---

### Post by vgrisham on 2007-08-04
Back to the avasys idea...

I tried to build from source, but I dredged up more problems (I think):

[email]vaughn@vaughn-desktop:~/.inst[/email]all/iscan-2.8.0$ ./configurechecking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking C++ ABI version... 1002
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0... checking for gtk+... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
yes
checking GTK_CFLAGS... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
 
checking GTK_LIBS... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
 
checking for imlibgdk... Package imlibgdk was not found in the pkg-config search path. Perhaps you should add the directory containing `imlibgdk.pc' to the PKG_CONFIG_PATH environment variable No package 'imlibgdk' found
configure: error: Library requirements (imlibgdk) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

---

### Post by David Oxland on 2007-08-04
HP psc 1315xi works fine for me

---

### Post by stevebakerj on 2007-08-04
> **vgrisham said:**
> Yep, I'm using Feisty. I downloaded the file you suggested. Here's what I get after executing "sudo rpm -i iscan-2.8.0-1.c2.i386.rpm":

error: Failed dependencies:
 ETC..
 ETC..
Help?

There is a note in the .pdf file:

  Note
    If the message “error: failed dependencies” appears during
    installation of Image Scan! for Linux, quit the installation. Install
    the necessary packages listed in the message, and then install
    Image Scan! for Linux again.

So go to Synaptic or what ever you use and install the relevant packages.

---

### Post by clanmackay on 2008-06-05
> **MLX said:**
> I don't know what model you are using but I am using a Epson Perfection 2400 photo scanner and it works well with Feisty.

Worked perfectly for me in Feisty, and Gusty, but stopped working as of my last distro upgrade to Hardy (xsane preview-scans the whole document, but then the bottom three-quarters disappear, replaced by blank grey, and when one tries to do a proper scan, the following error appears: "Error during CMS conversion: Could not open scanner ICM profile").  Anyone still following this thread with a workaround or solution?  Google searches for that exact error are unhelpful.

---

