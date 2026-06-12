---
title: "VirtualBox"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-03-21
When I run virtualbox, I get this error...
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device

any idea what's up??

It does open though.
Help is appreciated ; )
Thanks ; )

---

### Post by MrKlean on 2007-03-22
Anybody ???

---

### Post by energiya on 2007-03-22
> **MrKlean said:**
> When I run virtualbox, I get this error...
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device

any idea what's up??

It does open though.
Help is appreciated ; )
Thanks ; )

If it does run normal no need to worry. It seems to me they are just warnings. It is possible that some hardware isn't recognized as it should (?).

---

### Post by MrKlean on 2007-03-22
It seems I olly get it now when I run it from the command line...soooooooo.. I won't LOL! But I'm guessing you're right ; ) Thanks ; ))

---

### Post by AndyCooll on 2007-03-22
Have you tried looking through the main Virtalbox thread? I'm sure this problem has been raised in there somewhere before

[New GPL virtualization software: Virtualbox]("http://www.ubuntuforums.org/showthread.php?t=338931")

:cool:

---

### Post by fsando on 2007-03-22
I use ubuntu 6.10 with beryl/xgl
I get the following error popup
> 
VirtualBox kernel driver not accessible, permission problem.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1909 VERR_VM_DRIVER_NOT_ACCESSIBLE
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

---

