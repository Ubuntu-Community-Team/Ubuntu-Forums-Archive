---
title: "Is there a way to install amsn0.95 very easily and working at 100 percent ?"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-01-07
(I tried easyamsn but got segmentation fault when ./amsn)
:-(
  
Kind regards, 

Patrick

---

### Post by pbb on 2006-01-07
I haven't had any problems installing aMSN. I didn't use any "easyamsn" program, just installed aMSN by itself.

Did you try that, and what happened then?

One thing to note, is that the aMSN site doesn't offer the regular Ubuntu version as a choice, only the Ubuntu PowerPC version. But if you go to [http://amsn.amnestysalinas.org/](http://amsn.amnestysalinas.org/) (that is the link in the top of aMSN's download page), then you can download the regular Ubuntu version.

---

### Post by patrick295767 on 2006-01-07
[QUOTE=pbb]I haven't had any problems installing aMSN. I didn't use any "easyamsn" program, just installed aMSN by itself.

Did you try that, and what happened then?

One thing to note, is that the aMSN site doesn't offer the regular Ubuntu version as a choice, only the Ubuntu PowerPC version. But if you go to [http://amsn.amnestysalinas.org/](http://amsn.amnestysalinas.org/) (that is the link in the top of aMSN's download page), then you can download the regular Ubuntu version.[/QUOTE]
   
aahhhhhhhhhhhh !!! :-)
  
I try ... 

Thank you very much !

---

### Post by patrick295767 on 2006-01-07
```
 # dpkg -i amsn_0.95-3.ubuntu.deb
Selecting previously deselected package amsn.
(Reading database ... 87861 files and directories currently installed.)
Unpacking amsn (from amsn_0.95-3.ubuntu.deb) ...
dpkg: dependency problems prevent configuration of amsn:
 amsn depends on libc6 (>= 2.3.4-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
dpkg: error processing amsn (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amsn

```
  
I got an error message ... 
  
I dont know what to do .. .

Greetz'

---

### Post by patrick295767 on 2006-01-07
(I install breezy right now ... we'll see the result)
see ya' in 40min ...

---

### Post by pbb on 2006-01-07
This is the important part:

> dpkg: dependency problems prevent configuration of amsn:
 amsn depends on libc6 (>= 2.3.4-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.

It means that aMSN needs a newer version of the "common package" libc6 to function. You've got version 2.3.2(blah) installed, while version 2.3.4-1 or higher is needed.

You can download version 2.3.5(blah) from [http://packages.ubuntu.com/breezy/base/libc6](http://packages.ubuntu.com/breezy/base/libc6). Install that the same way with dpkg, and afterwards try again with aMSN.

---

### Post by patrick295767 on 2006-01-07
Amsn 0.95: it works !!! 
  
Thank you very much !!
  
I have it after 2 weeks of searching !
Thanks a looooooooooot !! 

Patrick !

---

### Post by patrick295767 on 2006-01-07
Installation of amsn 0.95 solved and very easy !!
Webcam is possible in this amsn :-)

Kind regards, 

Patrick

---

### Post by djlilyazi on 2006-01-07
[QUOTE=patrick295767](I tried easyamsn but got segmentation fault when ./amsn)
:-(
  
Kind regards, 

Patrick[/QUOTE]

just do excatly that the site says....

[http://www.ubuntuforums.org/showthread.php?t=75276](http://www.ubuntuforums.org/showthread.php?t=75276)

i did it and its super easyyyyyyyyyyyyyyyyyyyyyyyyy

---

### Post by pbb on 2006-01-08
I would definetly advice newbies AGAINST installing CVS versions! These are not stable, but bleeding-edge development. Not something to try if you don't know how to fix problems.

Simply downloading the .deb package and installing it with sudo dpkg -i <filename>.deb is also a lot easier than a page-long explaination to install that CVS version.

---

### Post by patrick295767 on 2006-01-08
[QUOTE=pbb]I would definetly advice newbies AGAINST installing CVS versions! These are not stable, but bleeding-edge development. Not something to try if you don't know how to fix problems.

Simply downloading the .deb package and installing it with sudo dpkg -i <filename>.deb is also a lot easier than a page-long explaination to install that CVS version.[/QUOTE]
  
Maybe in 5 years of experience with linux at home, I hope I 'll manage to install and have everthg working... 
Patience is the key !
  
Thank you for all  your wise advices !

Patrick

---

### Post by toorima on 2006-01-08
I installed the ubuntu pack from [http://amsn.amnestysalinas.org/](http://amsn.amnestysalinas.org/) and it works well but I can't get logging to work, the option "Log all conversations to aMSN's History for future viewing" is greyed out.
Is there spell checking in amsn as it is in gaim? I haven't found it but would like to have it because english isn't my native language.

---

### Post by patrick295767 on 2006-01-08
I got the invitation to see one webcam and get this error message: 
I accept it 
```
----------
 Initialization of the Audio/Video Plugin failed. Call Canceled
----------
----------
 Video Conference call canceled
```
  
I could see the first day of installation (before rebooting) a small webcam on he top of the screen of message.
Only rebooting removed this, sthg happen when rebooting. 
I cannot then see webcam's of others ... 
  
How to make it work ?

 Thank you !

---

### Post by patrick295767 on 2006-01-08
[QUOTE=toorima]I installed the ubuntu pack from [http://amsn.amnestysalinas.org/](http://amsn.amnestysalinas.org/) and it works well but I can't get logging to work, the option "Log all conversations to aMSN's History for future viewing" is greyed out.
Is there spell checking in amsn as it is in gaim? I haven't found it but would like to have it because english isn't my native language.[/QUOTE] 
 
I didnt find the "Log all conversations to aMSN's History for future viewing"
Can you login to start the msn messenger  ?
  
Greetz

---

### Post by patrick295767 on 2006-01-08
I found this :
[http://amsn.sourceforge.net/wiki/tiki-index.php?page=Webcam+In+aMSN](http://amsn.sourceforge.net/wiki/tiki-index.php?page=Webcam+In+aMSN)
```

Webcamsn extension is not loaded. You have to compile it. (On Linux)


You need to make sure there is a webcamsn.so in /msn/utils/webcamsn/
and also in /msn/utils/webcamsn/webcamsn/

If these do not exist, you need to enter each of those directories and type make to compile the source into a webcamsn.so file.


beast@1[webcamsn]$ ls
aclocal.m4 config.sub INSTALL Makefile.in webcamsn
AUTHORS configure install-sh missing webcamsn.dll
ChangeLog configure.ac libmimic.pc mkinstalldirs webcamsn.so
config.guess COPYING libmimic.pc.in NEWS webcamsn.tcl
config.h CVS libtool pkgIndex.tcl
config.h.in datastream.bin ltmain.sh README
config.log depcomp Makefile src
config.status doc Makefile.am stamp-h1



beast@1[webcamsn]$ make

beast@1[webcamsn]$ ls
CVS Makefile webcamsn.c webcamsn.o webcamsn.vcproj
libmimic.a Makefile.in webcamsn.h webcamsn.so
```  
  
But I have this webcamsn.so file ...
I dotn know what to do to have webcam in linux ...

Is yahoo mesesnger working better ?

---

### Post by toorima on 2006-01-08
Yeah the messenger works but if you go Tools - Preferences - logging you will see the "log all..." and mine is greyed out and don't save any history, text or webcam sessions :(
I don't have a webcam myself, I can view others but not save it or any text

---

### Post by pbb on 2006-01-08
Logging is available on my computer, I can enable it under Tools > Preferences > Logging. However, I have no idea where I can find the log that will be created...

I haven't tried webcamming yet.

---

### Post by toorima on 2006-01-08
If you want to see history for the person you are talking to, press ctrl+h other is Tools - view history
Logs are in ~/.amsn/logs but mine is emty

---

### Post by pbb on 2006-01-08
Okay, my log seems to work, but it is not in ~/.amsn/logs. I found my log in ~./amsn/<username>/logs...

---

### Post by toorima on 2006-01-08
hmm did you create any profile or something in amsn? read somethig about that but I just logged in and don't have the ~/.amsn/<username> dir

just found the "add new profile" even says there "without profile you cannot use the History...." should work now

---

### Post by toorima on 2006-01-08
Any one found anything about spell check? I kinda like that feature in gaim so would be nice to have in amsn too

---

### Post by pbb on 2006-01-08
I haven't found anything about spell-checking in aMSN, so I think you're out of luck on that one? Was there a reason why you expected spell-checking? As far as I know, there are not many IM programs that offer it.

---

### Post by toorima on 2006-01-08
> Was there a reason why you expected spell-checking?
No never used amsn before, been a gaim user all the time but wanted webcam support so just hoped there would be spell check like in gaim, would be a nice feature or plugin maybe

---

### Post by patrick295767 on 2006-01-08
[QUOTE=patrick295767]I found this :
[http://amsn.sourceforge.net/wiki/tiki-index.php?page=Webcam+In+aMSN](http://amsn.sourceforge.net/wiki/tiki-index.php?page=Webcam+In+aMSN)
```

Webcamsn extension is not loaded. You have to compile it. (On Linux)


You need to make sure there is a webcamsn.so in /msn/utils/webcamsn/
and also in /msn/utils/webcamsn/webcamsn/

If these do not exist, you need to enter each of those directories and type make to compile the source into a webcamsn.so file.


beast@1[webcamsn]$ ls
aclocal.m4 config.sub INSTALL Makefile.in webcamsn
AUTHORS configure install-sh missing webcamsn.dll
ChangeLog configure.ac libmimic.pc mkinstalldirs webcamsn.so
config.guess COPYING libmimic.pc.in NEWS webcamsn.tcl
config.h CVS libtool pkgIndex.tcl
config.h.in datastream.bin ltmain.sh README
config.log depcomp Makefile src
config.status doc Makefile.am stamp-h1



beast@1[webcamsn]$ make

beast@1[webcamsn]$ ls
CVS Makefile webcamsn.c webcamsn.o webcamsn.vcproj
libmimic.a Makefile.in webcamsn.h webcamsn.so
```  
  
But I have this webcamsn.so file ...
I dotn know what to do to have webcam in linux ...

Is yahoo mesesnger working better ?[/QUOTE]
  
Concerning your webcam support working, u did only installed the amsn with alvaro ? Did you download any plugin to enable ACCEPT the webcam invitation.  
  
Would you know how I can see the webcam of my friends users ?

Thank you, 

Pat

---

### Post by djlilyazi on 2006-01-08
[QUOTE=pbb]I would definetly advice newbies AGAINST installing CVS versions! These are not stable, but bleeding-edge development. Not something to try if you don't know how to fix problems.

Simply downloading the .deb package and installing it with sudo dpkg -i <filename>.deb is also a lot easier than a page-long explaination to install that CVS version.[/QUOTE]


it took me 3 min to install it and i am a newbie of like one week on ubuntu...

---

### Post by djlilyazi on 2006-01-08
another thing thats kool to use insted of aMSn is Kmsn is amazingggggggg i love it

---

### Post by public_void on 2006-01-08
I just used the .deb, very very easy to install, one line and done. Don't know if having a previous version helped. But I'd recommend the .deb route, but its up you.

---

### Post by hen3rz on 2006-01-08
do you guys know why the font looks so crappy on my aMSN and how i can make it look beter????

(i have msttcorefonts)

---

### Post by patrick295767 on 2006-01-09
Btw, is there another program than kopete which has the webcam support ?
  
Thank you, 

Patrick

---

### Post by pbb on 2006-01-09
[QUOTE=hen3rz]do you guys know why the font looks so crappy on my aMSN and how i can make it look beter????

(i have msttcorefonts)[/QUOTE]

I agree with this, the fonts are tiny and very blocky, nothing like the common Gnome fonts.

---

### Post by pbb on 2006-01-09
[QUOTE=toorima]hmm did you create any profile or something in amsn? read somethig about that but I just logged in and don't have the ~/.amsn/<username> dir

just found the "add new profile" even says there "without profile you cannot use the History...." should work now[/QUOTE]

No, I did nothing special. When you go to Tools > Preferences, does the title of the window say "Preferences - Profiled Config"?

---

### Post by toorima on 2006-01-09
Yes now it does but I just logged in at first and then things like logging will not work, one has to create a profile for that, did that and now everything works :)
Still wouldn't mind if anyone made a plugin with spell check ;)

---

### Post by pbb on 2006-01-09
[QUOTE=toorima]Still wouldn't mind if anyone made a plugin with spell check ;)[/QUOTE]

Like they say in the OS world: "Go ahead, what are you waiting for?" ;)

---

### Post by toorima on 2006-01-09
hmm yeah maybe if I get more free time later

---

### Post by patrick295767 on 2006-01-09
[QUOTE=toorima]Yes now it does but I just logged in at first and then things like logging will not work, one has to create a profile for that, did that and now everything works :)
Still wouldn't mind if anyone made a plugin with spell check ;)[/QUOTE]
  
"Evrthg workign": 
Even ur webcam support ? 
DId you try to ask for webcam seeing to one of ur buddy list friend ?
  Do you see him ? 
  
Greetz,

Pat'

---

### Post by toorima on 2006-01-09
Well I don't have a webcam of my own so can't try that but yes i can see my friends webcams

---

### Post by coaxx on 2006-01-14
installed that deb here on dapper and everything works well. Webcam works. I just had to portforward 6890-6900 to my client.

---

