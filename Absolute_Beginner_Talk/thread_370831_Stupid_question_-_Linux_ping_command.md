---
title: "Stupid question - Linux ping command"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by getut on 2007-02-26
Ok.. I have tried every switch in man ping that I thought should have done the trick but I still can't get ping to SHOW dropped ping requests.

In windows, ping shows "request timed out" if a ping request gets dropped. But so far in Ubuntu, you have to pay close attention to the sequence number and looking for missing ones to tell if you are sporadically dropping packets.

How can I make it DISPLAY the dropped sequence?

---

### Post by halitech on 2007-02-26
why not use the PING tool in the Network Tools?

System - Admin - Network Tools

---

### Post by getut on 2007-02-26
Most of the time its just a speed/accessibility thing... but sometimes necessity when I'm on my Ubuntu server without gui.

---

### Post by energiya on 2007-02-26
try
```

mtr host

```
it could be of much use...

---

