---
title: "How to setup a Canon scanner?"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-21
Hi,

How should I go about setting up my Canon (CanoScan 650U) ?

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-21
Wow !

Applications > Graphics > XSane Image Scanner.

I have to stuff around so much with XP to get it working and XSane just did it!

Problem solved :D

---

### Post by ampes on 2006-06-21
I have Canon printer with built-in scanner on top (MP370) connected via USB port..Problem is when I start XSane I got this popup error "No devices available"..

here is my lsusb
```
Bus 005 Device 005: ID 04a9:263d Canon, Inc.
Bus 005 Device 002: ID 07cc:0301 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0518:0005 EzKEY Corp.
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
```

Are there workarounds to make XSane detects my scanner??No problem with printer setup,only scanner..

---

### Post by Synt4x_3rr0r on 2006-12-14
> **ampes said:**
> I have Canon printer with built-in scanner on top (MP370) connected via USB port..Problem is when I start XSane I got this popup error "No devices available"..

here is my lsusb
```
Bus 005 Device 005: ID 04a9:263d Canon, Inc.
Bus 005 Device 002: ID 07cc:0301 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0518:0005 EzKEY Corp.
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
```

Are there workarounds to make XSane detects my scanner??No problem with printer setup,only scanner..

I have the same printer/scanner and have the same problem. It can print fine, but the scanner wont be found.
I'm using Ubuntu Edgy Eft.

Has anyone solved this?

---

### Post by collier on 2006-12-28
I'm having the same problem.  Canon imageCLASS MP390; printer works just fine using some other driver; scanner is not found.

It appears, so far as I have been able to discern, that there is not (yet) a driver for these devices ](*,) 

Canon is no help whatever!

John

---

