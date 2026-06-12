---
title: "wishing to install generic wireless usb device"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by forrestguide on 2007-03-07
Greetings folks,

I have a usb wifi device which worked with winxp (sorry for the swear word):mad:  

The cd came with linux stuff and I copied it onto the desk top. Now how do I install it? There were no instuctions on the cd at all.  I guess they assume I know what I´m doing. :confused: 

Any help would be wonderful.

Thank you,

Greg

---

### Post by moshuptrail on 2007-03-07
What can you tell us about the "Linux stuff" that came on the CD?
Names of files?
Versions of Linux supported?
Anything?
Is a "readme" file included?

---

### Post by forrestguide on 2007-03-07
Hi 

here is a list of the files that I copied. sorry for the extra stuff. I just cut and pasted.

there seems to be no readme or install information.


file:///home/nightjar/Desktop/wlan/zydas_common.h

file:///home/nightjar/Desktop/wlan/zdversion.h

file:///home/nightjar/Desktop/wlan/zdutils.h

file:///home/nightjar/Desktop/wlan/zdusb.h

file:///home/nightjar/Desktop/wlan/zdusb.c

file:///home/nightjar/Desktop/wlan/zdtypes.h

file:///home/nightjar/Desktop/wlan/zdtkipseed.h

file:///home/nightjar/Desktop/wlan/zdtkipseed.c

file:///home/nightjar/Desktop/wlan/zdsynch.c

file:///home/nightjar/Desktop/wlan/zdsorts.h

file:///home/nightjar/Desktop/wlan/zdsm.h

file:///home/nightjar/Desktop/wlan/zdshared.h

file:///home/nightjar/Desktop/wlan/zdshared.c

file:///home/nightjar/Desktop/wlan/zdpsmon.h

file:///home/nightjar/Desktop/wlan/zdpsmon.c

file:///home/nightjar/Desktop/wlan/zdpmfilter.h

file:///home/nightjar/Desktop/wlan/zdpmfilter.c

file:///home/nightjar/Desktop/wlan/zdpci_pcmcia.h

file:///home/nightjar/Desktop/wlan/zdpci_pcmcia.c

file:///home/nightjar/Desktop/wlan/zdpci_hotplug.h

file:///home/nightjar/Desktop/wlan/zdpci_hotplug.c

file:///home/nightjar/Desktop/wlan/zdos.h

file:///home/nightjar/Desktop/wlan/zdmmrx.h

file:///home/nightjar/Desktop/wlan/zdmmrx.c

file:///home/nightjar/Desktop/wlan/zdmic.h

file:///home/nightjar/Desktop/wlan/zdmic.c

file:///home/nightjar/Desktop/wlan/zdinlinef.h

file:///home/nightjar/Desktop/wlan/zdhw.h

file:///home/nightjar/Desktop/wlan/zdhw.cpp

file:///home/nightjar/Desktop/wlan/zdhw.c

file:///home/nightjar/Desktop/wlan/zdhci.h

file:///home/nightjar/Desktop/wlan/zdhci.c

file:///home/nightjar/Desktop/wlan/zdglobal.h

file:///home/nightjar/Desktop/wlan/zdglobal.c

file:///home/nightjar/Desktop/wlan/zdequates.h

file:///home/nightjar/Desktop/wlan/zdencrypt.h

file:///home/nightjar/Desktop/wlan/zdencrypt.c

file:///home/nightjar/Desktop/wlan/zddebug2.h

file:///home/nightjar/Desktop/wlan/zddebug2.c

file:///home/nightjar/Desktop/wlan/zddebug.h

file:///home/nightjar/Desktop/wlan/zddebug.c

file:///home/nightjar/Desktop/wlan/zdconfig

file:///home/nightjar/Desktop/wlan/zdcompat.h

file:///home/nightjar/Desktop/wlan/zdbuf.h

file:///home/nightjar/Desktop/wlan/zdbuf.c

file:///home/nightjar/Desktop/wlan/zdauthrsp.c

file:///home/nightjar/Desktop/wlan/zdauthreq.c

file:///home/nightjar/Desktop/wlan/zdasocsvc.c

file:///home/nightjar/Desktop/wlan/zdapi.h

file:///home/nightjar/Desktop/wlan/zd80211.h

file:///home/nightjar/Desktop/wlan/zd1211.h

file:///home/nightjar/Desktop/wlan/zd1211.c

file:///home/nightjar/Desktop/wlan/zd1205_proc.c

file:///home/nightjar/Desktop/wlan/zd1205.h

file:///home/nightjar/Desktop/wlan/zd1205.c

file:///home/nightjar/Desktop/wlan/WS11Ur.h

file:///home/nightjar/Desktop/wlan/WS11UPhR.h

file:///home/nightjar/Desktop/wlan/WS11UPhm.h

file:///home/nightjar/Desktop/wlan/WS11UPh.h

file:///home/nightjar/Desktop/wlan/WS11Ub.h

file:///home/nightjar/Desktop/wlan/WRITE_Handler.h

file:///home/nightjar/Desktop/wlan/WRITE_Handler.c

file:///home/nightjar/Desktop/wlan/utils.h

file:///home/nightjar/Desktop/wlan/utils.c

file:///home/nightjar/Desktop/wlan/TextForm.h

file:///home/nightjar/Desktop/wlan/TextForm.c

file:///home/nightjar/Desktop/wlan/TallyReg.h

file:///home/nightjar/Desktop/wlan/TallyReg.c

file:///home/nightjar/Desktop/wlan/TallyCnt.c

file:///home/nightjar/Desktop/wlan/sta

file:///home/nightjar/Desktop/wlan/Root

file:///home/nightjar/Desktop/wlan/Repository

file:///home/nightjar/Desktop/wlan/RegDefine.h

file:///home/nightjar/Desktop/wlan/READ_Handler.h

file:///home/nightjar/Desktop/wlan/READ_Handler.c

file:///home/nightjar/Desktop/wlan/menudbg.c

file:///home/nightjar/Desktop/wlan/menu_drv_macro.h

file:///home/nightjar/Desktop/wlan/Makefile

file:///home/nightjar/Desktop/wlan/macro.h

file:///home/nightjar/Desktop/wlan/ioctl_op.h

file:///home/nightjar/Desktop/wlan/ioctl_op.c

file:///home/nightjar/Desktop/wlan/Entries

file:///home/nightjar/Desktop/wlan/copying

file:///home/nightjar/Desktop/wlan/apdbg.c

---

### Post by moshuptrail on 2007-03-08
This could be rough.  What they've given you is a source code kit.  That means you will need to compile it all.  Fortunately they've included a Makefile.  You might try typing: sudo make
in this directory.  Post the output back here!   Good luck!

---

### Post by forrestguide on 2007-03-08
> **moshuptrail said:**
> This could be rough.  What they've given you is a source code kit.  That means you will need to compile it all.  Fortunately they've included a Makefile.  You might try typing: sudo make
in this directory.  Post the output back here!   Good luck!

Okay Ill give it a go, and let you know.

Greg

---

### Post by forrestguide on 2007-03-08
okay, here&#347; the result.  I´m wondering if I should use another file ie: Madwifi that I read so much about.

The response follows.

nightjar@MSHOME:~/Desktop/wlan$ sudo make
cc menudbg.c TextForm.c ioctl_op.c WRITE_Handler.c READ_Handler.c utils.c TallyReg.c TallyCnt.c  -lncurses -lform -o menudbg
menudbg.c:1:18: error: form.h: No such file or directory
menudbg.c:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
menudbg.c:12: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
menudbg.c: In function ‘main’:
menudbg.c:21: warning: incompatible implicit declaration of built-in function ‘exit’
menudbg.c:29: error: ‘KEY_DOWN’ undeclared (first use in this function)
menudbg.c:29: error: (Each undeclared identifier is reported only once
menudbg.c:29: error: for each function it appears in.)
menudbg.c:31: error: ‘my_form’ undeclared (first use in this function)
menudbg.c:31: error: ‘REQ_NEXT_FIELD’ undeclared (first use in this function)
menudbg.c:34: error: ‘REQ_END_LINE’ undeclared (first use in this function)
menudbg.c:36: error: ‘KEY_UP’ undeclared (first use in this function)
menudbg.c:38: error: ‘REQ_PREV_FIELD’ undeclared (first use in this function)
menudbg.c:41: error: ‘KEY_BACKSPACE’ undeclared (first use in this function)
menudbg.c:42: error: ‘REQ_DEL_PREV’ undeclared (first use in this function)
menudbg.c:44: error: ‘KEY_RIGHT’ undeclared (first use in this function)
menudbg.c:45: error: ‘REQ_VALIDATION’ undeclared (first use in this function)
menudbg.c:48: error: ‘curscr’ undeclared (first use in this function)
menudbg.c:50: error: ‘KEY_LEFT’ undeclared (first use in this function)
TextForm.c:1:18: error: form.h: No such file or directory
TextForm.c:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
TextForm.c:6: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
TextForm.c: In function ‘HighLightCurrent’:
TextForm.c:10: error: ‘field’ undeclared (first use in this function)
TextForm.c:10: error: (Each undeclared identifier is reported only once
TextForm.c:10: error: for each function it appears in.)
TextForm.c:12: error: ‘O_AUTOSKIP’ undeclared (first use in this function)
TextForm.c:14: error: ‘my_form’ undeclared (first use in this function)
TextForm.c: In function ‘SetMessage’:
TextForm.c:20: warning: incompatible implicit declaration of built-in function ‘memset’
TextForm.c: In function ‘SetResult’:
TextForm.c:27: warning: incompatible implicit declaration of built-in function ‘memset’
TextForm.c: In function ‘dbg_form_init’:
TextForm.c:39: error: ‘stdscr’ undeclared (first use in this function)
TextForm.c:39: error: ‘TRUE’ undeclared (first use in this function)
TextForm.c:42: error: ‘COLOR_WHITE’ undeclared (first use in this function)
TextForm.c:42: error: ‘COLOR_BLUE’ undeclared (first use in this function)
TextForm.c:43: error: ‘COLOR_BLACK’ undeclared (first use in this function)
TextForm.c:47: error: ‘field’ undeclared (first use in this function)
TextForm.c:56: error: ‘O_AUTOSKIP’ undeclared (first use in this function)
TextForm.c:60: error: ‘my_form’ undeclared (first use in this function)
TextForm.c:72: error: ‘LINES’ undeclared (first use in this function)
TextForm.c: In function ‘dbg_form_end’:
TextForm.c:79: error: ‘my_form’ undeclared (first use in this function)
TextForm.c:81: error: ‘field’ undeclared (first use in this function)
WRITE_Handler.c:1:18: error: form.h: No such file or directory
WRITE_Handler.c:8: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
WRITE_Handler.c:9: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
WRITE_Handler.c: In function ‘Handle_WRITE’:
WRITE_Handler.c:18: error: ‘my_form’ undeclared (first use in this function)
WRITE_Handler.c:18: error: (Each undeclared identifier is reported only once
WRITE_Handler.c:18: error: for each function it appears in.)
WRITE_Handler.c:19: warning: incompatible implicit declaration of built-in function ‘memset’
WRITE_Handler.c:23: error: ‘field’ undeclared (first use in this function)
WRITE_Handler.c:23: warning: assignment makes pointer from integer without a cast
WRITE_Handler.c:24: warning: assignment makes pointer from integer without a cast
WRITE_Handler.c:25: warning: incompatible implicit declaration of built-in function ‘strncpy’
WRITE_Handler.c:47: warning: assignment makes pointer from integer without a cast
WRITE_Handler.c:48: warning: assignment makes pointer from integer without a cast
READ_Handler.c:1:18: error: form.h: No such file or directory
READ_Handler.c:8: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
READ_Handler.c:9: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
READ_Handler.c: In function ‘Handle_READ’:
READ_Handler.c:18: error: ‘my_form’ undeclared (first use in this function)
READ_Handler.c:18: error: (Each undeclared identifier is reported only once
READ_Handler.c:18: error: for each function it appears in.)
READ_Handler.c:19: warning: incompatible implicit declaration of built-in function ‘memset’
READ_Handler.c:23: error: ‘field’ undeclared (first use in this function)
READ_Handler.c:23: warning: assignment makes pointer from integer without a cast
READ_Handler.c:24: warning: assignment makes pointer from integer without a cast
READ_Handler.c:25: warning: incompatible implicit declaration of built-in function ‘strncpy’
READ_Handler.c:48: warning: assignment makes pointer from integer without a cast
READ_Handler.c:49: warning: assignment makes pointer from integer without a cast
utils.c: In function ‘rtrim’:
utils.c:5: warning: incompatible implicit declaration of built-in function ‘strlen’
TallyReg.c:1:18: error: form.h: No such file or directory
TallyReg.c:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
TallyReg.c:12: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
TallyCnt.c:1:18: error: form.h: No such file or directory
TallyCnt.c:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
TallyCnt.c:12: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [all] Error 1
nightjar@MSHOME:~/Desktop/wlan$

---

### Post by moshuptrail on 2007-03-09
Believe it or not, you only have one error:  Missing file, form.h
What you are seeing is it's trying to compile several c programs.  For each program the first error is: form.h: No such file or directory
As a result of the missing file there are dozens of other errors.

That's really too bad.  I don't know if form.h is a standard file that you could find elsewhere, or something specific for your software.  But that's your next quest: find form.h

---

### Post by forrestguide on 2007-03-10
> **moshuptrail said:**
> Believe it or not, you only have one error:  Missing file, form.h
What you are seeing is it's trying to compile several c programs.  For each program the first error is: form.h: No such file or directory
As a result of the missing file there are dozens of other errors.

That's really too bad.  I don't know if form.h is a standard file that you could find elsewhere, or something specific for your software.  But that's your next quest: find form.h


Well, I see that finding it isn't easy.  Search the net and the best I get  are refereces to form.h but no links to a site with it archived. Nada on sourceforge, and even ubuntu. Hmmmm.  I'll keep looking I'm gong to bed now. I'll let you know if I find anything.

Thanks,

Greg

---

