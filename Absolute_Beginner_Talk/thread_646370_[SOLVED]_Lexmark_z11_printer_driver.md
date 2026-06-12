---
title: "[SOLVED] Lexmark z11 printer driver"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by johnleonard on 2007-12-21
Hi - I am having problems installing the z11 driver lz11-V2-1.1. I downloaded and extracted the file, typed in ./lz11.install as root as per the instructions, selected the foomatic install option and got the following error. Can anyone help?

> 
I will now try to compile the cZ11-V2 driver for your system ...

------------------------------------------------------------------
ERROR while compiling the program!
The program could not be compiled.
the log file reads:

gcc -O3 -DDEBUG=    cZ11-V2.c   -o cZ11-V2
cZ11-V2.c:80:20: error: unistd.h: No such file or directory
cZ11-V2.c:81:23: error: sys/types.h: No such file or directory
cZ11-V2.c:82:19: error: fcntl.h: No such file or directory
cZ11-V2.c:83:19: error: stdio.h: No such file or directory
cZ11-V2.c:84:20: error: stdlib.h: No such file or directory
cZ11-V2.c:85:20: error: string.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from cZ11-V2.c:86:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
cZ11-V2.c:87:20: error: malloc.h: No such file or directory
cZ11-V2.c: In function &#8216;CheckForTerminate&#8217;:
cZ11-V2.c:444: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
cZ11-V2.c:444: error: (Each undeclared identifier is reported only once
cZ11-V2.c:444: error: for each function it appears in.)
cZ11-V2.c:493: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
cZ11-V2.c:493: error: &#8216;stderr&#8217; undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:503: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
cZ11-V2.c:503: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
cZ11-V2.c:503: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
cZ11-V2.c: In function &#8216;filewrite&#8217;:
cZ11-V2.c:510: warning: incompatible implicit declaration of built-in function &#8216;fwrite&#8217;
cZ11-V2.c:510: error: &#8216;size&#8217; undeclared (first use in this function)
cZ11-V2.c:510: error: &#8216;count&#8217; undeclared (first use in this function)
cZ11-V2.c:510: error: &#8216;stream&#8217; undeclared (first use in this function)
cZ11-V2.c: In function &#8216;WidthCMYKtoBIT&#8217;:
cZ11-V2.c:616: error: &#8216;RAND_MAX&#8217; undeclared (first use in this function)
cZ11-V2.c: In function &#8216;WidthRGBtoBIT&#8217;:
cZ11-V2.c:669: error: &#8216;RAND_MAX&#8217; undeclared (first use in this function)
cZ11-V2.c: In function &#8216;InitDataPipe&#8217;:
cZ11-V2.c:705: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
cZ11-V2.c:791: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
cZ11-V2.c: At top level:
cZ11-V2.c:809: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
cZ11-V2.c: In function &#8216;ReadDataPipe&#8217;:
cZ11-V2.c:823: error: &#8216;in&#8217; undeclared (first use in this function)
cZ11-V2.c:824: error: &#8216;EOF&#8217; undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:878: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
cZ11-V2.c: In function &#8216;EndPage&#8217;:
cZ11-V2.c:880: error: &#8216;in&#8217; undeclared (first use in this function)
cZ11-V2.c:880: error: too many arguments to function &#8216;ReadDataPipe&#8217;
cZ11-V2.c: At top level:
cZ11-V2.c:894: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
cZ11-V2.c: In function &#8216;IsDataPipeEmpty&#8217;:
cZ11-V2.c:896: error: &#8216;in&#8217; undeclared (first use in this function)
cZ11-V2.c:896: error: too many arguments to function &#8216;ReadDataPipe&#8217;
cZ11-V2.c: At top level:
cZ11-V2.c:905: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
cZ11-V2.c: In function &#8216;GetNextLine&#8217;:
cZ11-V2.c:915: error: &#8216;in&#8217; undeclared (first use in this function)
cZ11-V2.c:915: error: too many arguments to function &#8216;ReadDataPipe&#8217;
cZ11-V2.c: In function &#8216;StartRndLine&#8217;:
cZ11-V2.c:963: error: &#8216;RAND_MAX&#8217; undeclared (first use in this function)
cZ11-V2.c: In function &#8216;FinishDataPipe&#8217;:
cZ11-V2.c:1067: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
cZ11-V2.c: In function &#8216;ClearBuffer&#8217;:
cZ11-V2.c:1081: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
cZ11-V2.c: In function &#8216;SweepBufferInit&#8217;:
cZ11-V2.c:1097: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
cZ11-V2.c: At top level:
cZ11-V2.c:1119: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
cZ11-V2.c:1129: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
cZ11-V2.c:1145: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
cZ11-V2.c:1155: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
cZ11-V2.c:1252: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
cZ11-V2.c: In function &#8216;PrintSweep&#8217;:
cZ11-V2.c:1281: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
cZ11-V2.c:1282: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
cZ11-V2.c:1311: error: &#8216;out&#8217; undeclared (first use in this function)
cZ11-V2.c:1319: warning: passing argument 2 of &#8216;filewrite&#8217; makes pointer from integer without a cast
cZ11-V2.c:1319: error: too many arguments to function &#8216;filewrite&#8217;
cZ11-V2.c:1322: warning: passing argument 2 of &#8216;filewrite&#8217; makes pointer from integer without a cast
cZ11-V2.c:1322: error: too many arguments to function &#8216;filewrite&#8217;
cZ11-V2.c: At top level:
cZ11-V2.c:1337: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
cZ11-V2.c: In function &#8216;PrintBWSweep&#8217;:
cZ11-V2.c:1345: error: &#8216;out&#8217; undeclared (first use in this function)
cZ11-V2.c:1346: warning: passing argument 3 of &#8216;PrintSweep&#8217; makes pointer from integer without a cast
cZ11-V2.c:1346: warning: passing argument 4 of &#8216;PrintSweep&#8217; from incompatible pointer type
cZ11-V2.c:1346: error: too many arguments to function &#8216;PrintSweep&#8217;
cZ11-V2.c: At top level:
cZ11-V2.c:1443: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
cZ11-V2.c:1727: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
cZ11-V2.c:1913: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
cZ11-V2.c: In function &#8216;DecodeOption&#8217;:
cZ11-V2.c:2130: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
cZ11-V2.c: In function &#8216;DecodeTerminateFile&#8217;:
cZ11-V2.c:2280: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
cZ11-V2.c:2283: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
cZ11-V2.c: In function &#8216;PrintHelp&#8217;:
cZ11-V2.c:2393: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
cZ11-V2.c:2393: error: &#8216;stderr&#8217; undeclared (first use in this function)
cZ11-V2.c:2398: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
cZ11-V2.c: In function &#8216;PrintVersion&#8217;:
cZ11-V2.c:2407: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
cZ11-V2.c:2407: error: &#8216;stderr&#8217; undeclared (first use in this function)
cZ11-V2.c:2408: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
cZ11-V2.c: In function &#8216;InvalidInvokation&#8217;:
cZ11-V2.c:2418: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
cZ11-V2.c:2418: error: &#8216;stderr&#8217; undeclared (first use in this function)
cZ11-V2.c: In function &#8216;ConflictingInvokation&#8217;:
cZ11-V2.c:2429: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
cZ11-V2.c:2429: error: &#8216;stderr&#8217; undeclared (first use in this function)
cZ11-V2.c: In function &#8216;DuplicateInvokation&#8217;:
cZ11-V2.c:2441: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
cZ11-V2.c:2441: error: &#8216;stderr&#8217; undeclared (first use in this function)
cZ11-V2.c: In function &#8216;IncompleteInvokation&#8217;:
cZ11-V2.c:2453: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
cZ11-V2.c:2453: error: &#8216;stderr&#8217; undeclared (first use in this function)
cZ11-V2.c: In function &#8216;IgnoringParameter&#8217;:
cZ11-V2.c:2464: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
cZ11-V2.c:2464: error: &#8216;stderr&#8217; undeclared (first use in this function)
cZ11-V2.c: In function &#8216;main&#8217;:
cZ11-V2.c:2700: error: &#8216;FILE&#8217; undeclared (first use in this function)
cZ11-V2.c:2700: error: &#8216;InputFile&#8217; undeclared (first use in this function)
cZ11-V2.c:2701: error: &#8216;OutPutFile&#8217; undeclared (first use in this function)
cZ11-V2.c:2717: error: &#8216;stdin&#8217; undeclared (first use in this function)
cZ11-V2.c:2718: error: &#8216;stdout&#8217; undeclared (first use in this function)
make: *** [cZ11-V2] Error 1
------------------------------------------------------------------


---

### Post by Sef on 2007-12-21
Check out [Openprinting]("http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-Z11").

---

### Post by johnleonard on 2007-12-21
I downloaded the driver from this page [http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-Z11](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-Z11) .  The problem I am having is with the installation process. I'm using Gutsy by the way.

---

### Post by johnleonard on 2007-12-21
Solved.

I needed to install the build essential package first.
> 
sudo apt-get install build-essential


---

### Post by Sef on 2007-12-21
> Solved.

I needed to install the build essential package first.
Quote:
sudo apt-get install build-essential

Glad you got it solved.

Just remember that when you install via apt-get or aptitude, do it this way:

```
sudo apt-get update
```

```
sudo apt-get install program_name
```

The first one updates so you get the latest repositories.

---

