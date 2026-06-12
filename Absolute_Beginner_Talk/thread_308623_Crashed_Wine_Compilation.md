---
title: "Crashed Wine Compilation"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by horsebakk on 2006-11-28
Hey all,

total linux nooblet here.

ive been trying to install wine on ubuntu, and after figuring out how to properly use sudo aptitude, ive finally gotten all the dependencies out of the way, but after the install when the compile is happening, it crashes and says "haha no fun for you!"

I dont know if or where there is a document in Ubuntu that lists/records the proggie errors that i could post up here for you, but at least heres the last bit of the Terminal text. please tell me if theres a better way to   do this.

i was made to use "./tools/wineinstall" from terminal as root from the source folder. the install part had a bunch of "no's" that went by too fast to read but it still let me compile. is this normal? 

> 
make[2]: Entering directory `/home/jesse/Desktop/wine-0.9.26/dlls/netapi32'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_SVRAPI_ -D_REEN TRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwri te-strings -Wpointer-arith  -g -O2  -o nbt.o nbt.c
nbt.c: In function ‘NetBTNameReq’:
nbt.c:208: warning: implicit declaration of function ‘WS’
nbt.c:208: error: syntax error before ‘u_short’
nbt.c:208: error: syntax error before ‘)’ token
nbt.c:211: error: syntax error before ‘u_short’
nbt.c:211: error: syntax error before ‘)’ token
nbt.c:216: error: syntax error before ‘u_short’
nbt.c:216: error: syntax error before ‘)’ token
nbt.c:219: error: syntax error before ‘u_short’
nbt.c:219: error: syntax error before ‘)’ token
nbt.c:220: error: syntax error before ‘u_short’
nbt.c:220: error: syntax error before ‘)’ token
nbt.c:221: error: syntax error before ‘u_short’
nbt.c:221: error: syntax error before ‘)’ token
nbt.c:222: error: syntax error before ‘u_short’
nbt.c:222: error: syntax error before ‘)’ token
nbt.c:226: error: syntax error before ‘u_short’
nbt.c:226: error: syntax error before ‘)’ token
nbt.c:227: error: syntax error before ‘u_short’
nbt.c:227: error: syntax error before ‘)’ token
nbt.c: In function ‘NetBTSendNameQuery’:
nbt.c:257: error: syntax error before ‘u_short’
nbt.c:257: error: syntax error before ‘)’ token
nbt.c: In function ‘NetBTWaitForNameResponse’:
nbt.c:336: error: syntax error before ‘u_short’
nbt.c:336: error: syntax error before ‘)’ token
nbt.c:340: error: syntax error before ‘u_short’
nbt.c:340: error: syntax error before ‘)’ token
nbt.c:341: error: syntax error before ‘u_short’
nbt.c:341: error: syntax error before ‘)’ token
nbt.c:342: error: syntax error before ‘u_short’
nbt.c:342: error: syntax error before ‘)’ token
nbt.c:371: error: syntax error before ‘u_short’
nbt.c:371: error: syntax error before ‘==’ token
nbt.c:376: error: syntax error before ‘u_short’
nbt.c:376: error: syntax error before ‘)’ token
nbt.c: In function ‘NetBTSessionReq’:
nbt.c:929: error: syntax error before ‘u_short’
nbt.c:929: error: syntax error before ‘)’ token
nbt.c: In function ‘NetBTCall’:
nbt.c:1022: error: syntax error before ‘u_short’
nbt.c:1022: error: syntax error before ‘)’ token
nbt.c: In function ‘NetBTSend’:
nbt.c:1098: error: syntax error before ‘u_short’
nbt.c:1098: error: syntax error before ‘)’ token
nbt.c: In function ‘NetBTRecv’:
nbt.c:1205: error: syntax error before ‘u_short’
nbt.c:1205: error: syntax error before ‘)’ token
nbt.c: In function ‘NetBTEnum’:
nbt.c:1374: error: syntax error before ‘u_long’
nbt.c:1374: error: syntax error before ‘)’ token
nbt.c:1381: error: ‘newNetwork’ undeclared (first use in this function)
nbt.c:1381: error: (Each undeclared identifier is reported only once
nbt.c:1381: error: for each function it appears in.)
nbt.c:1399: error: ‘ndx’ undeclared (first use in this function)
nbt.c: At top level:
nbt.c:1412: error: syntax error before ‘else’
nbt.c:1414: error: syntax error before ‘__FUNCTION__’
nbt.c:1414: warning: type defaults to ‘int’ in declaration of ‘wine_dbg_log’
nbt.c:1414: error: conflicting types for ‘wine_dbg_log’
nbt.c:1414: note: a parameter list with an ellipsis can’t match an empty paramet er name list declaration
../../include/wine/debug.h:174: error: previous declaration of ‘wine_dbg_log’ wa s here
nbt.c:1414: warning: data definition has no type or storage class
make[2]: *** [nbt.o] Error 1
make[2]: Leaving directory `/home/jesse/Desktop/wine-0.9.26/dlls/netapi32'
make[1]: *** [netapi32] Error 2
make[1]: Leaving directory `/home/jesse/Desktop/wine-0.9.26/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.


I would certainly appreciate any help on this subject, most of the prior hangups were stuff i could figure out using old forum posts and whatnot but this crashy business, i donno... :-? what the heck does this mean, and what should i do to fix it?

Horsebakk

---

### Post by po0f on 2006-11-28
horsebakk,

You can wait for the Wine devs to fix the source, or you can fix it yourself and submit a patch in with your fix.  :)

You'd be better off trying to compile an older version of Wine, if you don't feel comfortable messing with the source.

---

### Post by MWAAAHAAA on 2006-11-28
> **horsebakk said:**
> but after the install when the compile is happening

After you install the package you don't have to compile it, so I am confused. Did you install using aptitude or downloaded the source from winehq?

---

### Post by horsebakk on 2006-11-29
hey guys,

well i didn't know you don't have to compile it to use it. 

the only concern is that the install itself aborts afterward. stating: "Compilation failed, aborting install." :confused: 

Compiling it just seemed to be a logical place to follow since the install itself asked me if i wanted to do so. 

I could not find the way to just install it using "sudo aptitude install wine" as it said "download candidate not available" which i assumed meant  they just didnt have it, seeing how most other things they didnt have suggested logical alternatives. Does this just mean im a tard and havent spelled it well enough or something, or is there some different syntax i should use?

I downloaded the latest source from winehq.

I guess i should ask what the diff is between installing and compiling. i had thought it to be part of the installation process that windows hid from me hehehe :mrgreen:  

i will try and install an older version as well and see if that works.

Thanks for the responses i really appreciate the help!

Horsebakk

---

### Post by MWAAAHAAA on 2006-11-29
Perhaps you should try updating your database with 'aptitude update' and try to install the package again.

---

