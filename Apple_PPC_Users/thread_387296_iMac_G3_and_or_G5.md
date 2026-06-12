---
title: "iMac G3 and or G5"
date: 2007-03-18
forum: Apple PPC Users
---

### Post by Rozza69@gmail.com on 2007-03-18
hey all, ive been searching arount awhile but i havent come up with much. Right now i have an imac g3 (slot laoding) and imac g5 (revb) that i am quite interested in installing ubuntu on. When i try and install edgy on my g3, the kernal fails, same on the g5, i think it might be something with the disk cause i burnt it on a CD-RW. I have dapp... on another cd, that has got me more sucess. On the g3 the monitor goes out after getting through the screen with the ubuntu logo on it. If i type in live video=ofonly i can et further, bringingme to a terminal like window telling me that 
X window cant display (or something like that, i cant remember, and i forgot to write it down) it then asks me if i want to know why it happend( or something along those lines, sorry, it was early this morning!) it then tells me that "X window system version 7.0.0  release dat 21 december 2005
x protocol version 11, revision 0, release 7.0
build operating system : linux 26.15-26 powerpc64-smpppc
current operating system: linux 26.15-26 powerpc64  #1"    :confused: 

on the g5 i get past the ubuntu logo screen doing all the checks in brown, then i get to a brown screen wiht a white cursor in the middle, and thats when the fans go mental. Ive searched around these forums, and there is some stuff, but they seem to be getting further than me. any help is great! thanks alot.
-Rozza

---

### Post by solar george on 2007-03-18
Try using the alternate cd, X seems to autodetect better during installation than using the live cd

---

### Post by ssam on 2007-03-18
also at the boot prompt see if picking a specific kernel helps. the G5 will probably want the powerpc64 version will the G3 will want a plain powerpc version. (64 refers to 64 bit, the G3 and G4 are 32bit, the G5 is 64bit)

---

### Post by rccharles on 2007-03-19
> **Rozza69@gmail.com said:**
>  On the g3 the monitor goes out after getting through the screen with the ubuntu logo on it. If i type in live video=ofonly i can et further, bringingme to a terminal like window telling me that 
X window cant display (or something like that, i cant remember, and i forgot to write it down) it then asks me if i want to know why it happend( or something along those lines, sorry, it was early this morning!) it then tells me that "X window system version 7.0.0  release dat 21 december 2005
x protocol version 11, revision 0, release 7.0
I'm have successfully installed Ubuntu 6.10 on my iMac g3 600 using the Ubuntu 6.10 alt cd. I had to comment one line in my xorg.conf file.

You will have adjust adjust xorg.conf. See these instructions:
[http://ubuntuforums.org/showthread.php?t=234437](http://ubuntuforums.org/showthread.php?t=234437)
Later releases of Ubuntu have gotten more of xorg.conf correct.  Change what you need.

Ubuntu works from the live CD after changing xorg.conf, but I have not been able to get the install to work from the live CD.

See my post about getting the modem to work if you are using the modem:
[http://www.ubuntuforums.org/showthread.php?t=355205&highlight=modem](http://www.ubuntuforums.org/showthread.php?t=355205&highlight=modem)

Robert

---

