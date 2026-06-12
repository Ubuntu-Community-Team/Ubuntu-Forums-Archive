---
title: "BIOS Bug?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by ebozzz on 2007-03-18
After running the following command.....

```
egrep -e fail /var/log/messages
```

I get this output.

```
Mar 18 12:43:48 Fusion-desktop kernel: [65382.916565] RPC: failed to contact portmap (errno -5).
Mar 18 12:45:05 Fusion-desktop kernel: [   35.658754] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Mar 18 15:49:28 Fusion-desktop kernel: [11174.183937] RPC: failed to contact portmap (errno -5).
Mar 18 17:55:44 Fusion-desktop kernel: [   34.424351] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
```

Can someone please help me make sense of it? Thank you!

---

### Post by oilchangeguy on 2007-03-18
a google search indicates it may be a usb issue of some sort. it suggest (if you are aware of a usb problem) disable usb legacy support in the bios.

---

### Post by ebozzz on 2007-03-18
Thank you very much for the reply!. I am not aware of any USB issue with the machine in question. The same command on a different machine gives the following results.....

```
*******@Soul-desktop:~$ egrep -e fail /var/log/messages
*******@Soul-desktop:~$ egrep -e fail /var/log/messages
*******@Soul-desktop:~$ 
```

---

### Post by oilchangeguy on 2007-03-18
i just entered the command to see what if anything shows up on this computer. and got a screen full from the last two days showing the cd rom failed to open??????? this computer has two cd drives, and no problems with either one. no blinking light on the drives or anything. so i guess if it ain't broke, don't fix it.

---

### Post by ebozzz on 2007-03-18
> **oilchangeguy said:**
> so i guess if it ain't broke, don't fix it.

:) I'm with you on that! I was just hoping to get some answer as to what was going on.

---

