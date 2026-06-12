---
title: "No Wired or Wireless MacBook7,1"
date: 2012-02-12
forum: Apple Hardware Users
---

### Post by jettechfsr on 2012-02-12
Ok after upgrade to 11.10 Wifi would not connect so I clean installed 11.10 still same can not connect wired or wireless this is going to be hard to troubleshoot I have to log out of Ubuntu to send this is there and another version with the correct drivers I can download?

---

### Post by krolaw on 2012-02-19
Same problem for me on MacBook4,1 - No Wifi.  Appears the broadcom wifi driver is blacklisted in the latest kernel.  Have booted using the previous kernel in the meantime...

Hope there is a fix forth coming.

Cheers.

---

### Post by dakos on 2012-02-25
Just installed 11.10 on MBP7.1, wired works out of the box and wireless working pretty easely using [this link]("https://help.ubuntu.com/community/MacBookPro7-1/Oneiric").

I'm on triple boot (OSX, WIN7, U11.10).

---

### Post by krolaw on 2012-02-25
Been there, tried that.  The Broadcom wifi driver is already installed.  However, it can't activate.  It appears the driver is blacklisted with the latest kernel.

---

### Post by dakos on 2012-02-25
Is the wireless working on OSX? how did you install the wifi driver if you don't have wired as well or is it fixed by now? 
We have the same kernel version don't we? 3.0.0.16 (uname -a in terminal).

---

### Post by krolaw on 2012-02-25
Wifi works in: Ubuntu-MacBook 3.0.0-15-generic which is what I've reverted to...fails in 3.0.0-16.

---

### Post by dakos on 2012-02-25
That's wierd but as long as it works...:)

---

