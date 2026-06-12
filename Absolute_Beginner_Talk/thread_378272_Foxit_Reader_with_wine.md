---
title: "Foxit Reader with wine"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by eljalill on 2007-03-07
Hello!

I've tried to use the windows Foxit Reader with wine, however it does not work, all I get is a rather lengthy error message starting with:

```
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
wine: Unhandled page fault on read access to 0x047fd918 at address 0x7e507601 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x047fd918 in 32-bit code (0x7e507601).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e507601 ESP:0033fa08 EBP:0033fa40 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000006 EBX:7e55653c ECX:ffffffff EDX:00000000
 ESI:047fd918 EDI:7c0e7548
Stack dump:
0x0033fa08:  ffffffff ffffffff 00000048 00000006
0x0033fa18:  00000000 00000000 00000000 00000000
0x0033fa28:  7c0e75a8 7c0e7548 00000000 047fd918
0x0033fa38:  00000018 7e555120 0033fc00 7e5039ae
0x0033fa48:  00000018 00000018 047fd918 00000048
0x0033fa58:  7c0e7548 ffffffa0 00000300 00000018
Backtrace:
=>1 0x7e507601 in winex11 (+0x27601) (0x0033fa40)
  2 0x7e5039ae in winex11 (+0x239ae) (0x0033fc00)

```

I am rather confused, especially because I've read, that Foxit runs great with wine.... and I made sure to have the newest wine version.
I am using edgy and the wine repositories. 
Am thankful for suggestions!

eljalill

---

### Post by AtrejuT on 2007-03-07
Yeah, I have the same problem:
Whenever I want to run it using
```

wine Foxit\ Reader.exe

```
I get this:
```

wine: Unhandled page fault on read access to 0x047fd5a8 at address 0x7e44d601 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x047fd5a8 in 32-bit code (0x7e44d601).

```

It goes on for a while longer, but this is the im important bit, I guess...

If anyone has an idea I'd appreciate it.!
Oh, and I'm running Feisty by the way...

atreju

---

### Post by AtrejuT on 2007-03-07
I had another idea which did not help, but I thought I'd post it anyways:

So far I always tried starting the standalone version of foxit. So now I started to use the installer instead. This gave me an error about a missing mfc42.dll
This I copied over from my windows install to ~/.wine/drive_c/windows/system32 
After that the install went through without problems - but the reader itself still doesn't work, giving me the same error as before...

suggestions, anyone? 
atreju

---

### Post by AtrejuT on 2007-03-07
no idea anyone?
I'd also be thankful for suggestions as to any other programm that lets me annotate pdf's - I really need that...

atreju

---

### Post by greenjet on 2007-03-07
You could try looking [here]("http://frankscorner.org/index.php?p=office") for help.

---

### Post by eljalill on 2007-03-07
Hey, thanx! Didn't know about that site before and it seems to be pretty handy. :)

But when I follow the instructions there, it doesn't help :( . Same thing still happens, only now the Foxit Reader.exe is in .wine/drive_c.... and so on and so forth.

I really wonder whether I am not overlooking something really obvious, since nearly no-one else has problems with this.

---

### Post by eljalill on 2007-03-07
PS: On the website is says basically the same as AtrejuT in his second post...

---

### Post by eljalill on 2007-03-11
So, I've been looking around more, and have learned some new things about this...
Maybe they are useful to other people as well... :) .

Apparently this error only occurs with Foxit 2.0 , and not with 1.3 . However, 1.3 does not have the editing features of 2.0 (highlight and underline) , which are for me personally the reason to use Foxit in the first place.

There is a bug fix, which might work, if you find a source code old enough to compile it with.... from what I know, it has to be at least younger than 0.9.19 (it's made for 0.9.7) :
[http://bugs.winehq.org/show_bug.cgi?id=4506](http://bugs.winehq.org/show_bug.cgi?id=4506) (Thanks, Dank) . Since I didn't find that source code I am not sure, it actually works.

There is another fix to be tried:
[http://www.winehq.org/pipermail/wine-patches/2007-March/036593.html](http://www.winehq.org/pipermail/wine-patches/2007-March/036593.html) 
  (Thanks Toon) , but since winehq is down at the moment, I have no clue, whether that works either.

I found the help here: [http://groups.google.com/group/comp.emulators.ms-windows.wine/topics](http://groups.google.com/group/comp.emulators.ms-windows.wine/topics) .

If anyone else with that problem gets there before me, let me know, how it goes... (AtrejuT?)

Best,
eljalill

---

### Post by eljalill on 2007-03-11
So, finally, I can report:

That last patch works!
It takes some compiling... so that I had my first real compiling experience...
and you have to remember to put the mcf42 file back in .

And now I can spend many happy hours annotating my .pdfs!

Thus greatly uplifted, ;)
eljalill

---

### Post by 3ntity on 2007-03-20
> **eljalill said:**
> So, finally, I can report:

That last patch works!
It takes some compiling... so that I had my first real compiling experience...
and you have to remember to put the mcf42 file back in .

And now I can spend many happy hours annotating my .pdfs!

Thus greatly uplifted, ;)
eljalill
Hey,

What exactly did you do to make it work? i have the mcf42.dll file in /home/me/.wine/drive_c/windows/system32; the installer worked but i get the same error as you used to. The 'patch' didn't make much sense to me [and the link is written over 2 lines so not 'clickable', just so you know]... And, how well does the program work? 
Thanks for any help in advance

---

### Post by david_kt on 2007-03-20
I am not sure why you want to run foxit reader with wine as there are a lot of pdf readers in native linux, including Acrobat Reader.

Running in wine so for is not perfect yet, as it is still in beta stage. And the start up of the program would be longer than usual.

Regards,
DK

---

### Post by eljalill on 2007-03-21
Well, I fixed the url for the patch now.

What you do to apply this patch, is,
you download the newest source code (if it doesn't work, try an older one, 0.9.32 worked fine for me).
then you copy the text from the patch from the link (start with diff--) into gedit or so and call it patch.diff (or whatever else you want. the .diff in the end is the important part).
then you run patch <patch.diff . Make sure it is in the same directory as the file that has to be patched (in this case dib_convert.c, as you can see from the beginning of the patch).
And then compile the source code.

Everything clear? 
I promise to look back here more often from now on :)

---

### Post by eljalill on 2007-03-21
@david_kt
I use foxit, because I want to be able to highlight in my .pdf and annotate. 
Most .pdfs I read are scientific articles I need to write papers or something else related to Uni, and helps me greatly to be able to mark important phrases and note important omissions or cross links or whatever.

As far as I know, there isn't even a Linux Adobe Writer, even if I had $600 or so left to spend, and I don't know of any other program that does that.

Wine is beta formally, but I have the impression, that other developers wouls have the same version out as 2. something and official release already, other than the mentioned I never had problems with wine.

And for the startup: it does take a little longer, but just a little. And that's ok for me :) .

So I guess, that explains it. Or not?

---

### Post by 3ntity on 2007-03-21
> **david_kt said:**
> I am not sure why you want to run foxit reader with wine as there are a lot of pdf readers in native linux, **including Acrobat Reader**.

Running in wine so for is not perfect yet, as it is still in beta stage. And the** start up of the program would be longer than usual**.


I find Acrobat to be one of the worst programs i've tried. It's resource hungry,  it's slow, resides in your memory [under Windows at least, which you can turn off, but:] and still takes a long time to load. Foxit Reader beats it by far in any and all of those aspects. And wait longer than what, 2 seconds to start? I can wait that long for a program as good foxit reader.

I'll probably have a look into a native linux pdf reader anyways, i'm sure there are good programs around, i'm just not convinced by evince. Which leads to the next: Does anyone know any good pdf reader which is fast & [memory] efiicient and allows for more advanced printing option [print odd/even pages only, reversed order, ...]? [or is the latter a problem of drivers or something of sorts?]
Cheers!

---

### Post by david_kt on 2007-03-21
I am still not sure why you prefer to run foxit reader with wine, when there is even linux version of foxit reader:

[http://www.foxitsoftware.com/foxitreader/FoxitReaderLinux.tar.gz](http://www.foxitsoftware.com/foxitreader/FoxitReaderLinux.tar.gz)

Just extract and run it, no installation needed.

May be the windows version is much better than linux version I guess. I don't know much about pdf reader comparison, but running with wine is the last thing I want to do i.e if there is no linux alternatives.

Regards,
DK

---

### Post by eljalill on 2007-03-21
Well, when I last tried, right before I started this thread it wouldn't run on my edgy laptop.
It would install fine, but then refuse to open any document, and just close itself instead.
Since it's not made for ubuntu, I figured, it's just not ready yet... But as soon as a workable version is out, I will switch :) .
Did you try it out? Is it any better yet?

---

### Post by 3ntity on 2007-03-21
> **david_kt said:**
> I am still not sure why you prefer to run foxit reader with wine, when there is even linux version of foxit reader:

[http://www.foxitsoftware.com/foxitreader/FoxitReaderLinux.tar.gz](http://www.foxitsoftware.com/foxitreader/FoxitReaderLinux.tar.gz)


I tried that a few days back, and it was an extremely annoying 'test version' or something along those lines, which, among other, had a 'Foxit reader trial version' label printed on every page, as well as lacking the good features of foxit reader for windows. But thanks anyways :)

Thanks a lot for the reply, Eljalill, i'll try your method tomorrow, when i have some more time. :) I'll let you know how things went...

---

### Post by david_kt on 2007-03-21
Well, if you want to run underwine and you are not sure how to do it, I suggest you use winetools:

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

But please use wine version 0.9.1, 0.9.2, or 0.9.3 only, and not the latest version. I have tried 0.9.5 is still work. The idea is select the version best for you and _lock wine version_.

Using this method, I could run many windows program, including MS Office 2000. But the disadvantage is you could not use lates wine, and you will need a valid windows license to download dcom98 and internet explorer.

Other choice is to tweak wine using winecfg. Could you give me the link to the foxit reader version you want to install? I will try to tweak wine to run it for you if I have time.

DK

---

### Post by eljalill on 2007-03-22
Thanks for your suggestions.
As said earlier, the problem mentioned at the beginning apparently only occurs with the newest version of foxit reader, and I am not sure, in how far older versions of wine are of help there. Why would you not use a newer version?

However, sine the patch works nicely, and it didn't pose any problem recompiling, I am quite happy with the solution I found, and I am not quite sure why you would consider it not good?

But I am happy to learn!

---

### Post by david_kt on 2007-03-22
If it could work for you offcourse it is good. But I just try to help other that so far could not run it yet. Using winetools is to make sure you can run as many programs as possible without any effort, I have tried it. No tweaking, no compiling. But today I have no time to try foxit reader yet, although I have downloaded the version 2. I hope tommorow I have time, to see whether or not it could run using winetools without any tweaking.

Or, you could use crossover office, very good in my opinion. It is not free, but if you buy crossoveroffice, it is the same like supporting wine developer:

[http://www.codeweavers.com/](http://www.codeweavers.com/)

Regards,
DK

---

### Post by david_kt on 2007-03-22
I have just tried:

Wine version 9.33, 9.27, 9.23, only installer can run (after adding mfc42.dll). The program itself could not run.

Wine 9.5, with winetools, i.e. the whole windows 98 component installed with wine, still only installer run, the program could not run.

Crossover office, unfortunately do not support foxit reader yet.

So, I think it is too difficult to run foxit reader for beginners, unless somebody writes a detailed how to.

DK

---

### Post by 3ntity on 2007-03-27
> **david_kt said:**
> I have just tried:

Wine version 9.33, 9.27, 9.23, only installer can run (after adding mfc42.dll). The program itself could not run.

Wine 9.5, with winetools, i.e. the whole windows 98 component installed with wine, still only installer run, the program could not run.

Crossover office, unfortunately do not support foxit reader yet.

So, I think it is too difficult to run foxit reader for beginners, unless somebody writes a detailed how to.

DK

Wow, what an effort :)
I still haven't had time to try out the suggested fix [had some 'fun time' getting to grips with certain aspects of linux... FAT32 problems, anyone?!], though it would come in handy now :( Hopefully on thursday... I'll get back to you as soon as i've tried it out...

---

### Post by david_kt on 2007-04-01
> **3ntity said:**
> Wow, what an effort :)
I still haven't had time to try out the suggested fix [had some 'fun time' getting to grips with certain aspects of linux... FAT32 problems, anyone?!], though it would come in handy now :( Hopefully on thursday... I'll get back to you as soon as i've tried it out...

If you are still interested in running foxit reader, you have to compile wine yourself, and put a patch before compiling. As Eljalill did not write a detail "how to" of what he did, I will write a little more for other that still could not get it done but want to run foxit reader badly.

**First of all, you will need to install dependency to compile wine:**

[INDENT]Step 1.
 wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Step 2.
For Ubuntu Edgy (6.10):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Dapper (6.06):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list

Step 3
sudo apt-get build-dep wine[/INDENT]

These steps will install a bunch of software just to compile wine. If you do not want it later, you could take note of the software installed here, and uninstall it later after you compile wine.

**And then, you will need to download wine source. I have tried it using lates wine (0.9.34) and it works.**

[http://downloads.sourceforge.net/wine/wine-0.9.34.tar.bz2?modtime=1175273929&big_mirror=1](http://downloads.sourceforge.net/wine/wine-0.9.34.tar.bz2?modtime=1175273929&big_mirror=1)

For example, you will download it on your desktop. After completed, right click on it, and choose "extract here".
[B]
Add patch to wine
[/B]

Open terminal, and navigate to folder contains dib_convert.c:

[INDENT]cd /home/username/Desktop/wine-0.9.34/dlls/winex11.drv[/INDENT]

```
gedit patch.diff
```

and paste below codes and save it:

```
diff --git a/dlls/winex11.drv/dib.c b/dlls/winex11.drv/dib.c
diff --git a/dlls/winex11.drv/dib_convert.c b/dlls/winex11.drv/dib_convert.c
index d946918..dff48be 100644
--- a/dlls/winex11.drv/dib_convert.c
+++ b/dlls/winex11.drv/dib_convert.c
@@ -23,9 +23,12 @@ #include "config.h"
 
 #include <stdlib.h>
 
+#include "wine/debug.h"
+#include "wine/exception.h"
 #include "windef.h"
 #include "x11drv.h"
 
+WINE_DEFAULT_DEBUG_CHANNEL(dib);
 
 /***********************************************************************
  *           X11DRV_DIB_Convert_*
@@ -64,6 +67,12 @@ #include "x11drv.h"
  *   high bits, the green, and the source color in the low bits.
  */
 
+static WINE_EXCEPTION_FILTER(exception_filter)
+{
+    if (GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION)
+        ERR("exception caught with code 0x%08x = %d, app might be buggy?\n", GetExceptionCode(), GetExceptionCode());
+    return EXCEPTION_EXECUTE_HANDLER;
+}
 
 /*
  * 15 bit conversions
@@ -849,7 +858,17 @@ static void convert_888_to_0888_asis(int
         for (x=0; x < w2; x++) {
             /* Do 4 pixels at a time: 3 dwords in and 4 dwords out */
             DWORD srcval1,srcval2;
-            srcval1=srcpixel[0];
+            /* Some apps crash in following code-line, possibly they pass a bad pointer*/ 
+            __TRY
+            {
+              srcval1=srcpixel[0];
+            }
+            __EXCEPT(exception_filter)
+            {
+              return;
+            }
+            __ENDTRY;
+
             dstpixel[0]=( srcval1        & 0x00ffffff); /* h1, g1, l1 */
             srcval2=srcpixel[1];
             dstpixel[1]=( srcval1 >> 24) |              /* l2 */
```

That is the code Eljalill use I guess, and I have tried as well. But in wine forums, it stated that the above code is not very good. Below patch was stated as a better patch (for wine 0.9.7 and 0.9.8) but after I tried with wine 0.9.34 it did not work. So please do not use below patch, unless you want to troubleshoot this patch:

```
--- wine/dlls/x11drv/dib_convert.c	2006-02-10 08:41:04.000000000 +0100
+++ mywine/dlls/x11drv/dib_convert.c	2006-02-16 08:41:52.000000000 +0100
@@ -818,37 +818,39 @@ static void convert_888_to_0888_asis(int
                                      const void* srcbits, int srclinebytes,
                                      void* dstbits, int dstlinebytes)
 {
-    const DWORD* srcpixel;
+    const BYTE* srcpixel;
     DWORD* dstpixel;
+    DWORD prev, curr;
     int x,y;
-    int oddwidth;
 
-    oddwidth=width & 3;
-    width=width/4;
     for (y=0; y<height; y++) {
         srcpixel=srcbits;
         dstpixel=dstbits;
-        for (x=0; x<width; x++) {
-            /* Do 4 pixels at a time: 3 dwords in and 4 dwords out */
-            DWORD srcval1,srcval2;
-            srcval1=srcpixel[0];
-            dstpixel[0]=( srcval1        & 0x00ffffff);  /* h1, g1, l1 */
-            srcval2=srcpixel[1];
-            dstpixel[1]=( srcval1 >> 24) |              /* l2 */
-                        ((srcval2 <<  8) & 0x00ffff00); /* h2, g2 */
-            srcval1=srcpixel[2];
-            dstpixel[2]=( srcval2 >> 16) |              /* g3, l3 */
-                        ((srcval1 << 16) & 0x00ff0000); /* h3 */
-            dstpixel[3]=( srcval1 >>  8);               /* h4, g4, l4 */
-            srcpixel+=3;
-            dstpixel+=4;
-        }
-        /* And now up to 3 odd pixels */
-        for (x=0; x<oddwidth; x++) {
-            DWORD srcval;
-            srcval=*srcpixel;
-            srcpixel=(const DWORD*)(((const char*)srcpixel)+3);
-            *dstpixel++=( srcval         & 0x00ffffff); /* h, g, l */
+        curr = *(const DWORD*)( (int)srcpixel & 0xfffffffc);
+        for( x = 0; x < width; x++) {
+            switch( (int)srcpixel & 0x3) {
+                case 0:
+                    curr = *(const DWORD*)( srcpixel);
+                    *dstpixel = ( curr        & 0x00ffffff);  /* h1, g1, l1 */
+                    break;
+                case 3:
+                    prev = curr;
+                    curr = *(const DWORD*)( srcpixel + 1);
+                    *dstpixel = ( prev >> 24) |              /* l2 */
+                                ((curr <<  8) & 0x00ffff00); /* h2, g2 */
+                    break;
+                case 2:
+                    prev = curr;
+                    curr = *(const DWORD*)( srcpixel + 2);
+                    *dstpixel = ( prev >> 16) |              /* g3, l3 */
+                                ((curr << 16) & 0x00ff0000); /* h3 */
+                    break;
+                case 1:
+                    *dstpixel = ( curr >>  8);               /* h4, g4, l4 */
+                    break;
+            }
+            dstpixel++;
+            srcpixel += 3;
         }
         srcbits = (const char*)srcbits + srclinebytes;
         dstbits = (char*)dstbits + dstlinebytes;
@@ -859,46 +861,45 @@ static void convert_888_to_0888_reverse(
                                         const void* srcbits, int srclinebytes,
                                         void* dstbits, int dstlinebytes)
 {
-    const DWORD* srcpixel;
+    const BYTE* srcpixel;
     DWORD* dstpixel;
+    DWORD prev, curr;
     int x,y;
-    int oddwidth;
 
-    oddwidth=width & 3;
-    width=width/4;
     for (y=0; y<height; y++) {
         srcpixel=srcbits;
         dstpixel=dstbits;
-        for (x=0; x<width; x++) {
-            /* Do 4 pixels at a time: 3 dwords in and 4 dwords out */
-            DWORD srcval1,srcval2;
-
-            srcval1=srcpixel[0];
-            dstpixel[0]=((srcval1 >> 16) & 0x0000ff) | /* h1 */
-                        ( srcval1        & 0x00ff00) | /* g1 */
-                        ((srcval1 << 16) & 0xff0000);  /* l1 */
-            srcval2=srcpixel[1];
-            dstpixel[1]=((srcval1 >>  8) & 0xff0000) | /* l2 */
-                        ((srcval2 <<  8) & 0x00ff00) | /* g2 */
-                        ((srcval2 >>  8) & 0x0000ff);  /* h2 */
-            srcval1=srcpixel[2];
-            dstpixel[2]=( srcval2        & 0xff0000) | /* l3 */
-                        ((srcval2 >> 16) & 0x00ff00) | /* g3 */
-                        ( srcval1        & 0x0000ff);  /* h3 */
-            dstpixel[3]=((srcval1 >> 24) & 0x0000ff) | /* h4 */
-                        ((srcval1 >>  8) & 0x00ff00) | /* g4 */
-                        ((srcval1 <<  8) & 0xff0000);  /* l4 */
-            srcpixel+=3;
-            dstpixel+=4;
-        }
-        /* And now up to 3 odd pixels */
-        for (x=0; x<oddwidth; x++) {
-            DWORD srcval;
-            srcval=*srcpixel;
-            srcpixel=(const DWORD*)(((const char*)srcpixel)+3);
-            *dstpixel++=((srcval  >> 16) & 0x0000ff) | /* h */
-                        ( srcval         & 0x00ff00) | /* g */
-                        ((srcval  << 16) & 0xff0000);  /* l */
+        curr = *(const DWORD*)( (int)srcpixel & 0xfffffffc);
+        for( x = 0; x < width; x++) {
+            switch( (int)srcpixel & 0x3) {
+                case 0:
+                    curr = *(const DWORD*)( srcpixel);
+                    *dstpixel = ((curr >> 16) & 0x0000ff) | /* h1 */
+                                ( curr        & 0x00ff00) | /* g1 */
+                                ((curr << 16) & 0xff0000);  /* l1 */
+                    break;
+                case 3:
+                    prev = curr;
+                    curr = *(const DWORD*)( srcpixel + 1);
+                    *dstpixel = ((prev >>  8) & 0xff0000) | /* l2 */
+                                ((curr <<  8) & 0x00ff00) | /* g2 */
+                                ((curr >>  8) & 0x0000ff);  /* h2 */
+                    break;
+                case 2:
+                    prev = curr;
+                    curr = *(const DWORD*)( srcpixel + 2);
+                    *dstpixel = ( prev        & 0xff0000) | /* l3 */
+                                ((prev >> 16) & 0x00ff00) | /* g3 */
+                                ( curr        & 0x0000ff);  /* h3 */
+                    break;
+                case 1:
+                    *dstpixel = ((curr >> 24) & 0x0000ff) | /* h4 */
+                                ((curr >>  8) & 0x00ff00) | /* g4 */
+                                ((curr <<  8) & 0xff0000);  /* l4 */
+                    break;
+            }
+            dstpixel++;
+            srcpixel += 3;
         }
         srcbits = (const char*)srcbits + srclinebytes;
         dstbits = (char*)dstbits + dstlinebytes;
```

And after that, run this command:

```
patch <patch.diff
```

[B]
After that, the last step is to compile wine.[/B]

Navigate to extracted folder of wine source, where you could find readme file:

```
cd /home/username/Desktop/wine-0.9.34
```

Run the installer

```
./tools/wineinstall
```

It will take quite sometimes. And if you do the above steps without any error, you should be able to run foxit reader. Just make sure all steps are done without any error message.

Regards,
DK

---

### Post by eljalill on 2007-04-03
Thanks, david_kt, 
I've been meaning to do this, once my papers and exams are over...
But I am not sad to see, that you have already done it.

Thanks also for the research done and the new patch. Do you happen to know what makes it better than the old one?

---

### Post by david_kt on 2007-04-05
> **eljalill said:**
> Thanks also for the research done and the new patch. Do you happen to know what makes it better than the old one?

Frankly I do not know how it is better. But the patch you are using has been obsoleted and replaced by the one I posted. But I have tried the first pacth, it still throw some errors although able to run foxit reader. I have not tried the new one, as I am still busy with other thing.

edit: today I tried the better patch, it has some error when patching:

Hunk #1 FAILED at 818.
Hunk #2 FAILED at 861.
2 out of 2 hunks FAILED -- saving rejects to file dib_convert.c.rej

DK

---

### Post by 3ntity on 2007-04-08
> **david_kt said:**
> If you are still interested in running foxit reader, you have to compile wine yourself, and put a patch before compiling. [...] I will write a little more for other that still could not get it done but want to run foxit reader badly.
...
Regards,
DK
Wow... what a fabulous [working!] set of instructions :D I used the first patch you mentioned, which worked fine [0 errors]. I compiled wine 0.9.34 from the link provided, and followed all the instructions, which went very smooth. Compiling + installing took about half an hour i guess, not bad at all :) Thanks a ton for the help! You too eljalill, thanks!

Those patches are written in C, right? If that's the case, i should be able to troubleshoot that sort of patch by next year, but not quite yet...

Will this 'sudo apt-get build-dep programX' work to get all dependencies for any programX? [as long as they're included in the sources list in assume] I've got a long way to go with Linux, but i'm enjoying the ride, haha... Looking forward to Feisty now!

Thanks again!

**Edit**: I'm just using the Foxit Reader 2.0 executable, No installation or anything; has the same working as in windows [at least as far as i've noticed :)]

---

### Post by david_kt on 2007-04-09
> **3ntity said:**
> Those patches are written in C, right? If that's the case, i should be able to troubleshoot that sort of patch by next year, but not quite yet...

Will this 'sudo apt-get build-dep programX' work to get all dependencies for any programX? [as long as they're included in the sources list in assume] I've got a long way to go with Linux, but i'm enjoying the ride, haha... Looking forward to Feisty now!

Thanks again!

**Edit**: I'm just using the Foxit Reader 2.0 executable, No installation or anything; has the same working as in windows [at least as far as i've noticed :)]

Entity,

Fist of all, I am no programmer at all. I am just a user (or you could say super user) so that actually I did not understand programming at all. What I did was just use logic, common sense, past experience, try to seek  advice available in internet, and some trial and error if needed. 

What Eljalill wrote previously was more than enough for linux geek. And even experience user  could understand what he is trying to say. But, for linux beginners, we need to provide a detail "how to" to patch and compile program from the source. That is why previously I tried to run it using available tools but to no avail.

I guess the "sudo apt-get build-dep programX" will not work for all programs, only selected programs.

DK

---

### Post by diegoma on 2007-08-16
I tried to follow the instructions. I'm new in this and I don't know how to solve this error message, can somebody help? This is what I did:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

(I have Ubuntu 7.04)

sudo apt-get build-dep wine

At this point I got this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_feisty_main_source_Sources - open (2 No such file or directory)

---

