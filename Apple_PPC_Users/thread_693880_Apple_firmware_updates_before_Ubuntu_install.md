---
title: "Apple firmware updates before Ubuntu install"
date: 2008-02-11
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-11
Has anyone who is unsuccessful at installing Ubuntu run the apple firmware updates first?

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

I'm just wondering if this might help.  I don't have this problem on my G5 iMac, but thought I'd throw it out there just in case...

---

### Post by VCF on 2008-02-11
Here is how to tell what your firmware version is without having to load

From this page:

[http://docs.info.apple.com/article.html?artnum=60351](http://docs.info.apple.com/article.html?artnum=60351) 

Determining BootROM or Firmware Version 
Last Modified on: March 08, 2005 
Article: 60351 

This article tells how to determine the BootROM or Firmware version on Apple computers introduced after 1998. 


There are two ways to check the revision of the boot ROM.

Apple System Profiler 2.1.2 or later provides Boot ROM revision information. To view the revision information, choose About Apple System Profiler from the Apple Menu. On the System Profile tab under the Production Information selection the following information appears:


(EXAMPLE)
Production information
ROM revision: $77D.44B5
Boot ROM version: 1.1f4
Mac OS ROM file version: 1.3
Serial number: XB00000000XXX-XXX
Software bundle: 694-1137
Sales order number: Not applicable

The version of Apple System Profiler that shipped with Mac OS 8.5 or 8.5.1 retail packages or updates does not include this information. Mac OS 8.6 includes version 2.2 which has this information in the System Profile information. For computers that do not have the correct versions of Apple System Profiler you must check the ROM revision in Open Firmware. To view the revision information:

1. Shut down.
2. Start up and hold down cmd-opt-o-f
3. The Boot ROM Revision is displayed at the top of the screen.
4. Type "bye" followed by <return> to continue starting up in Mac OS.

---

### Post by stream303 on 2008-02-11
Nice!

For general purpose info about Mac models, I find this site to be extremely helpful when you want to narrow down your hardware quickly:

[http://www.everymac.com/](http://www.everymac.com/)

---

