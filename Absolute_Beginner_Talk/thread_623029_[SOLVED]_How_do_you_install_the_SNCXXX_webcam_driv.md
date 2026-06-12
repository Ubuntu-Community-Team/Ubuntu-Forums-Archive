---
title: "[SOLVED] How do you install the SNCXXX webcam driver in Gutsy?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-11-25
Hello,

I'm looking for a way to install the SN9CXXX driver for my webcam in Gutsy. I found the .deb package at :
[http://www.linux-projects.org/modules/news/]("http://www.linux-projects.org/modules/news/")

When I tried installing it, I got an error message in regard to the kernel (I guess it wants Feisty's kernel).

How can I install the package in Gutsy with the current kernel?

Your help would be very appreciated!!! Thanks!

---

### Post by philinux on 2007-11-25
Thats strange because I installed realplayer for feisty last night and got no such error. :confused:

Maybe cos the driver needs something to compile it from feisty

---

### Post by the8thstar on 2007-11-25
> Maybe cos the driver needs something to compile it from feisty 

That's a good guess. I had a feeling the package was lousy the moment I landed on their page.

---

### Post by philinux on 2007-11-25
Whats the full make and model of your webcam. And can you post the output of 

```
[FONT="Times New Roman"]lsusb[/FONT]
```

---

### Post by the8thstar on 2007-11-25
> **[COLOR="Blue"]Bus 005 Device 003: ID 045e:00f4 Microsoft Corp.[/COLOR]** 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05dc:0080 Lexar Media, Inc. Jumpdrive Secure 64MB
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

My webcam is a Microsoft VX-6000.

---

