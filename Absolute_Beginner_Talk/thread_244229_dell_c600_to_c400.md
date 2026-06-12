---
title: "dell c600 to c400"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by peav007 on 2006-08-26
this is my problem i have 2 dell laptop machines, i have to setup ubuntu on the dell c600 because the c400 has no cd/dvd rom drive. i setup ubuntu on the c600 hoping to put the drive back into the dell c400. i have successful done this before with xandros. now i think my issue are the ati graphics card on the dell c600 and the intel vga controller 82830 on the c400. is there a way to change the graphics driver to the intel controller.
this is the error message i recieve.

 x window system version 7.0.0,
release date:21 december 2005.
 x protocol version 11, revision 7.0.
 building operating system: linux 2.6.15.7.i686 current operating system:
 linux peav007-laptop 2.6.15-26-386#
 PREEMPT THUR AUG 3 02:52:00 UTC 2006 i686
build date: 16 march 2006.
befroe reporting any problems, check [http://wikix.org](http://wikix.org) to make sure you have the latest version,
module loader present.
markers(--) probed, (**) from config file, (==) default setting ,(++)
from command line, (!!) notice,(II) informational, (ww) warning, (EE) error
(NI) not implemented, (??) unknown. (==) log file:" /var/log/xorg.0.log".
time sat aug 26 02:03:38 2006 (==) using config file
" /etc/x11/xorg.config "f"
 (EE) no device detected
 fatal server error 
 no screen found.
 XIO: fatal Io error 104 (connection reset by peer)
 on Xserver "00" after 0 requests (0 known processed) with 0 events remaining.
afetr this it returns to the command line 
 root@peav007-laptop: "#.  
i  need to know if i can change the graphics module/driver from the command line and how i go about doing it 

TIA JOHN :-k :-k :-k

---

### Post by Crosbie on 2006-08-26
Don't know about that specific request, but to solve the basic problem of getting Ubuntu onto your CDless computer, you might try one of the methods on [this page](https://help.ubuntu.com/community/Installation).

---

