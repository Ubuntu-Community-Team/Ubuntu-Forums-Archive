---
title: "&quot;Unknown Error&quot; iPod mounting problem"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Henaro on 2007-11-12
Hello everyone~

I seem to be having a little iPod problem.  For the longest time the way I've been mounting my iPod was by simply right clicking it's Desktop icon and hitting mount.  But now I keep getting "Unknown Error" and that's all.  Also the iPod's name isn't showing up like it usually does.  

Anyone know what I can do to fix this?

---

### Post by Henaro on 2007-11-13
Bumpin' it up for some help.  :(

---

### Post by Henaro on 2007-11-13
Bumpin' up for more help.  Am I stranded here?

---

### Post by llamakc on 2007-11-13
No but you're going to have to be patient. Or go check the bugs at launchpad.net.

How can anybody help? You don't give specifics. 

Feisty/Gutsy?

What iPod? 

Be specific.

Plug the iPod in and open a Terminal. Right after plugging it in, type:

```

dmesg

```

And cut/paste the last 10 or so lines into your reply here. And if I don't get back to this tonight, have patience.

---

### Post by Henaro on 2007-11-14
> **llamakc said:**
> No but you're going to have to be patient. Or go check the bugs at launchpad.net.

How can anybody help? You don't give specifics. 

Feisty/Gutsy?

What iPod? 

Be specific.

Plug the iPod in and open a Terminal. Right after plugging it in, type:

```

dmesg

```

And cut/paste the last 10 or so lines into your reply here. And if I don't get back to this tonight, have patience.
Sorry but 20 hours is my patience limit.  

I'm using Gusty and my iPod is a 1G Nano.  



Here is my iPod stuff:
```
[  126.457272] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  126.509199] sd 2:0:0:0: [sda] 3999743 512-byte hardware sectors (2048 MB)
[  126.510135] sd 2:0:0:0: [sda] Write Protect is off
[  126.510138] sd 2:0:0:0: [sda] Mode Sense: 68 00 00 08
[  126.510141] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  126.511722] sd 2:0:0:0: [sda] 3999743 512-byte hardware sectors (2048 MB)
[  126.512755] sd 2:0:0:0: [sda] Write Protect is off
[  126.512758] sd 2:0:0:0: [sda] Mode Sense: 68 00 00 08
[  126.512760] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  126.512764]  sda: sda1 sda2
[  126.518133] sd 2:0:0:0: [sda] Attached SCSI removable disk
[  126.530936] sd 2:0:0:0: Attached scsi generic sg0 type 0

```

---

### Post by Henaro on 2007-11-15
This problem is still here.

---

