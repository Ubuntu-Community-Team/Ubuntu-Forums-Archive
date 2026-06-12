---
title: "compiling urban terror on ppc"
date: 2014-12-09
forum: Apple Hardware Users
---

### Post by robert-mathew-harris on 2014-12-09
i recently revived a PowerMAC G5 that didnt have a hard drive so i installed Lubuntu 14.04.1 ppc on a new harddrive.
well i love urban terror and want to get it runing on this machine. i downloaded the source for iourbanterror source and extractd it a folder and when running the "sudo make" command i get some errors. i dont know what to do from here. any tips on where to go would be great.
[TABLE="width: 500"]
[TR]
[TD][sudo] password for bobby: 
make[1]: Entering directory `/home/bobby/UrbanTerror/source/ioUrbanTerrorClientSource'
make -C code/tools/lcc install
make[2]: Entering directory `/home/bobby/UrbanTerror/source/ioUrbanTerrorClientSource/code/tools/lcc'
install -s -m 0755 build-linux-ppc64/q3lcc ../
install -s -m 0755 build-linux-ppc64/q3cpp ../
install -s -m 0755 build-linux-ppc64/q3rcc ../
make[2]: Leaving directory `/home/bobby/UrbanTerror/source/ioUrbanTerrorClientSource/code/tools/lcc'
make -C code/tools/asm install
make[2]: Entering directory `/home/bobby/UrbanTerror/source/ioUrbanTerrorClientSource/code/tools/asm'
gcc -O2 -Wall -Werror -fno-strict-aliasing -o q3asm q3asm.c cmdlib.c
q3asm.c: In function ‘TryAssembleENDPROC’:
q3asm.c:958:10: error: variable ‘v2’ set but not used [-Werror=unused-but-set-variable]
  int  v, v2;
          ^
q3asm.c:958:7: error: variable ‘v’ set but not used [-Werror=unused-but-set-variable]
  int  v, v2;
       ^
cc1: all warnings being treated as errors
cmdlib.c: In function ‘_printf’:
cmdlib.c:188:3: error: format not a string literal and no format arguments [-Werror=format-security]
   printf(text);
   ^
cmdlib.c: In function ‘Q_getwd’:
cmdlib.c:402:11: error: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result [-Werror=unused-result]
    getcwd (out, 256);
           ^
cc1: all warnings being treated as errors
make[2]: *** [q3asm] Error 1
make[2]: Leaving directory `/home/bobby/UrbanTerror/source/ioUrbanTerrorClientSource/code/tools/asm'
make[1]: *** [tools] Error 2
make[1]: Leaving directory `/home/bobby/UrbanTerror/source/ioUrbanTerrorClientSource'
make: *** [release] Error 2[/TD]
[/TR]
[/TABLE]

---

### Post by robert-mathew-harris on 2014-12-30
Well I've had to downgrade to Ubuntu 12.04, had some other issues. Tried to compile it again with same result.I wasn't ready to give up yet so I installed openarena from software center, now I run into another issue. When I try to run open arena I get an error about opengl. I go to the log I see its looking for renderer_opengl1_ppc.so in open arena and ioquake3 folders. I copy the one from ioquake3 to open arena folder, yet another error. In the open arena log I see. 
"Failed loading /usr/lib/games/openarena/renderer_opengl1_ppc.so: /usr/lib/games/openarena/renderer_opengl1_ppc.so: undefined symbol: com_altivec" 
down at the end. Off to Google I go, I find its a known issue and is supposedly fixed in the latest ioquake3 builds. So I git clone the latest ioquake3 source and attempt to compile, what do you know more errors. I get this when I try to make, this  the error I get is..

CC-linux-ppc64/client/cl_cgame.o] Error 1
 code/client/cl_cgame.c
In file included from code/client/../libcurl-7.35.0/curl/curl.h:35:0,
                 from code/client/cl_curl.h:31,
                 from code/client/client.h:34,
                 from code/client/cl_cgame.c:24:
code/client/../libcurl-7.35.0/curl/curlrules.h:142:3: error: size of array ‘__curl_rule_01__’ is negative
make[2]: *** [build/release make[2]: Leaving directory `/home/bobby/Documents/ioquake3/ioq3'
make[1]: *** [targets] Error 2
make[1]: Leaving directory `/home/bobby/Documents/ioquake3/ioq3'
make: *** [release] Error 2

I'm lost.anyone have any suggestions?
Edit.
I did Google the curl error and read somewhere someone suggested installing an i386 version of lib curl dev but I don't know.if anyone knows a better place to post let me know I don't post I. forums a lot I Google first ask questions later. I would realy like see this thing play some games consider I can play hi-def movies without any sort of GPU rendering and it still doesn't lag.

---

### Post by robert-mathew-harris on 2014-12-30
Another thought would I be better off trying to cross compile it on a 32 bit machine for PPC, if so how would I go about doing that in Ubuntu 14.04? Or would I just run into the error with my current openarena/ioquake3 install? The undefined symbol?

---

### Post by robert-mathew-harris on 2014-12-30
Oh by the way the reason I'm post in Mac hardware section is because I have a hunch its a PowerPC related issue.

---

### Post by rsavage on 2014-12-30
Urban terror:

The significant wording is "[COLOR=#000000]cc1: all warnings being treated as errors"
[/COLOR]
You need to remove the -Werror flag. 

Have you tried compiling it on non PowerPC?

Open arena:

Try compiling the deb packages from more recent versions of Ubuntu.[COLOR=#000000]




[/COLOR]

---

### Post by rsavage on 2014-12-30
[http://www.urbanterror.info/forums/topic/28351-compile-fails/](http://www.urbanterror.info/forums/topic/28351-compile-fails/)
[http://forums.gentoo.org/viewtopic-t-854153-view-previous.html?sid=913863dcb18cc94a9075736c35971a8d](http://forums.gentoo.org/viewtopic-t-854153-view-previous.html?sid=913863dcb18cc94a9075736c35971a8d)[COLOR=#000000]



[/COLOR]

---

### Post by robert-mathew-harris on 2014-12-31
Hey thanks a lot for the help rsavage. I couldn't get urt to compile but getting the latest ioquake3 .deb file done the trick for open arena.although I spoke too soon about speed. Now time to find a better driver for my video card

---

### Post by robert-mathew-harris on 2015-01-04
ive seen alot of views on this thread so i figured id share that you can run urban terror as a mod in open arena just like you used to in quake. thats how i got it to run on PPC. just copy the "q3ut4" folder from urbanterror that has the zpak files into your 
" /home/"YOUR USER NAME"/.openarena " folder. then run openarena, click mods, urban terror, load. now your running urban terror on PPC linux.works for urban terror 4.1

---

