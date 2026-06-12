---
title: "Help me with xvnkb"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by derek_wu on 2007-01-10
Hello everybody!
I've just start using Ubuntu. I'm a Vietnamese so I need to use OpenOffice to input text in Vietnamese. I heard that xvnkb is a good software to input text in Vietnamese but I don't know how to install it. Somebody help me! :-k 
Thanks in advance.

---

### Post by kerry_s on 2007-01-10
You must mean " xvkbd " you can use synaptic to install it or from command line> sudo apt-get install xvkbd

But i don't think it has Vietnamese. See pic->

---

### Post by david_kt on 2007-01-29
> **kerry_s said:**
> You must mean " xvkbd " you can use synaptic to install it or from command line> sudo apt-get install xvkbd

But i don't think it has Vietnamese. See pic->

It is XVNKB, a program to type Vietnamese fonts.

First of all, you need to install the dependency:

[INDENT]sudo apt-get install build-essential gcc xlibs-dev libxft-dev xserver-xorg-dev[/INDENT]

Make sure all above dependency are installed without any error. If there is an error, just repeat:

INDENT]sudo apt-get install build-essential gcc xlibs-dev libxft-dev xserver-xorg-dev[/INDENT]

After that, follow below step:

[INDENT]sudo mkdir /usr/X11R6/include[/INDENT]
[INDENT]sudo ln -s /usr/include/X11 /usr/X11R6/include/X11[/INDENT]
[INDENT]tar xvzf xvnkb.x.x.tar.gz[/INDENT]

Enter the directory just created:

[INDENT]cd xvnkb[/INDENT]

Amd then issue below command:

[INDENT]./autogen.sh[/INDENT]
[INDENT]./configure --use-extstroke --use-abcstroke [/INDENT]

Below is the output of ./configure --use-extstroke --use-abcstroke  above:

[INDENT]Configuration for xvnkb 0.2.9 on Linux

  Type "./configure --help" for more information

Checking uchar... no
Checking ushort... yes
Checking uint... yes
Checking ulong... yes
Checking dynamic linking loader... yes
Checking X11 lib... /usr/X11R6
Checking pkg-config... yes
Checking Xft... yes

Compile options:
  Enable XFT: yes
  Enable spell checking: yes
  Enable extended keystroke: yes
  Enable ABC liked Telex keystroke: yes
done.

Type "make" to compile[/INDENT]


After that, just run below comand:

[INDENT]make[/INDENT]

followed by:

[INDENT]sudo make install[/INDENT]

You can launch it by typing xvnkb in terminal. After that, you could type vietnamese in any application, except firefox. If you want to type vietnamese in firefox, you should install CHIM:

[http://xvnkb.sourceforge.net/chim/chim.xpi](http://xvnkb.sourceforge.net/chim/chim.xpi)

But this CHIM version could not run in Firefox 2. But I have edited it to run on firefox 2. In case you are using firefox 2.0.0.1 I will upload this file.

Regards,
DK

---

### Post by wwood on 2007-02-25
Hi, I tried the above using xvnkb 2.9a and 2.9 and both gave me the following error. Using gcc 4.1.2.

```

>./configure --use-extstroke --use-abcstroke

Configuration for xvnkb 0.2.9 on Linux

  Type "./configure --help" for more information

Checking uchar... no
Checking ushort... yes
Checking uint... yes
Checking ulong... yes
Checking dynamic linking loader... yes
Checking X11 lib... /usr/X11R6
Checking pkg-config... yes
Checking Xft... yes

Compile options:
  Enable XFT: yes
  Enable spell checking: yes
  Enable extended keystroke: yes
  Enable ABC liked Telex keystroke: yes
done.

Type "make" to compile



> make && s make install
cc -fpic -O3 -s -fomit-frame-pointer -D_REENTRANT -DUSE_XFT -I/usr/include/freetype2   -DVERSION=\"0.2.9\" -Wall -I/usr/X11R6/include -c xvnkb.c
In file included from typedefs.h:24,
                 from xvnkb.c:32:
config.h:1: error: expected identifier or ‘(’ before ‘-’ token
config.h:1: error: stray ‘#’ in program
In file included from typedefs.h:24,
                 from xvnkb.c:32:
config.h:7:2: error: #endif without #if
In file included from xvnkb.c:32:
typedefs.h:28: warning: data definition has no type or storage class
typedefs.h:28: warning: type defaults to ‘int’ in declaration of ‘vk_methods’
xvnkb.c: In function ‘key_handler’:
xvnkb.c:155: error: ‘VKM_OFF’ undeclared (first use in this function)
xvnkb.c:155: error: (Each undeclared identifier is reported only once
xvnkb.c:155: error: for each function it appears in.)
xvnkb.c: In function ‘XNextEvent’:
xvnkb.c:347: error: ‘VKM_OFF’ undeclared (first use in this function)
make: *** [xvnkb.o] Error 1

```

---

### Post by wwood on 2007-02-25
The difficulty was typedefs.h

-e #ifndef __VK_CONFIG_H
#define __VK_CONFIG_H
#define VK_CHECK_SPELLING
#define VK_USE_ABCSTROKE
#define VK_USE_EXTSTROKE
#define VK_NEED_UCHAR
#endif


To fix the problem all I had to do was delete the '-e ' at the start (perhaps my C is a little rusty but the compiler agrees that this is a syntax error). I'm using:
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)

Fixed version of typedefs.h

#ifndef __VK_CONFIG_H
#define __VK_CONFIG_H
#define VK_CHECK_SPELLING
#define VK_USE_ABCSTROKE
#define VK_USE_EXTSTROKE
#define VK_NEED_UCHAR
#endif

---

### Post by wwood on 2007-02-25
Quoting an email from the xvnkb author:

> 
Hi,

Thank you for your feedback!  Actually, the file is config.h which will be created when running configure (bash shell script). Unfortunately, Ubuntu changed /bin/sh from bash to ash (from Ubuntu 5.10 => Ubunbu 6.06) so it didn't understand -e option and output the option to config.h file.  I'll fix this issue in next release.  Thanks again.

Lam


---

### Post by tungpham42 on 2008-04-14
> **wwood said:**
> The difficulty was typedefs.h

-e #ifndef __VK_CONFIG_H
#define __VK_CONFIG_H
#define VK_CHECK_SPELLING
#define VK_USE_ABCSTROKE
#define VK_USE_EXTSTROKE
#define VK_NEED_UCHAR
#endif


To fix the problem all I had to do was delete the '-e ' at the start (perhaps my C is a little rusty but the compiler agrees that this is a syntax error). I'm using:
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)

Fixed version of typedefs.h

#ifndef __VK_CONFIG_H
#define __VK_CONFIG_H
#define VK_CHECK_SPELLING
#define VK_USE_ABCSTROKE
#define VK_USE_EXTSTROKE
#define VK_NEED_UCHAR
#endif
I think the difficulty was config.h.
Just omit -e at the beginning of the code.

---

### Post by wangjih on 2008-04-26
yep ! but config.h is generated by configure ! so to modify correctly
one has to modify - eliminate this -e - really in

  config/configure at line 130

"```
# Create config.h
echo -e "#ifndef __VK_CONFIG_H\n#define __VK_CONFIG_H" > config.h

```

then everything will get correctly with configure

---

