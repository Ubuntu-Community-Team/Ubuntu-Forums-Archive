---
title: "Why there's no body concern about mounting USB removable drive?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by yogatta on 2008-01-26
i had this problem. when i inserted my SD card into a card reader and plug it into USB port on my computer, nothing happened. i read many thread in this forum and haven't found any good and proper solution.

---

### Post by chewearn on 2008-01-26
Support for usb card reader is good (e.g. I haven't encountered problems with the card readers I have used), but you should understand that it's hard to achieve 100% support, given that linux is not the first choice for manufacturer in creating drivers.

So, to see if your card reader problem can be solved, first plug-in the card reader, then run this:
```
dmesg | tail
```


 (don't do anything else between plugging in the card reader and the commands).

---

### Post by aysiu on 2008-01-26
In answer to your thread title question of *Why there's no body concern about mounting USB removable drive?* people appear not to be concerned, because most of us have out USB removable drives automounted with no problems.

---

### Post by yogatta on 2008-01-27
> **aysiu said:**
> In answer to your thread title question of *Why there's no body concern about mounting USB removable drive?* people appear not to be concerned, because most of us have out USB removable drives automounted with no problems.

why is mine not auto mounted? i think my SD card is not broken because when i insert to my windows OS, it is detected and can be played as normal.

---

### Post by LaRoza on 2008-01-27
Giving the card reader you have would help.

---

### Post by yogatta on 2008-01-27
> **AstalaVista said:**
> Support for usb card reader is good (e.g. I haven't encountered problems with the card readers I have used), but you should understand that it's hard to achieve 100% support, given that linux is not the first choice for manufacturer in creating drivers.

So, to see if your card reader problem can be solved, first plug-in the card reader, then run this:
```
dmesg | tail
```


 (don't do anything else between plugging in the card reader and the commands).

i've done ** dmesg | tail**. and this is the outcome

[  822.864000] sd 4:0:0:0: [sdb] Write Protect is off
[  822.864000] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  822.864000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  822.868000] sd 4:0:0:0: [sdb] 3970048 512-byte hardware sectors (2033 MB)
[  822.868000] sd 4:0:0:0: [sdb] Write Protect is off
[  822.868000] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  822.868000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  822.868000]  sdb: sdb1
[  822.872000] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  822.872000] sd 4:0:0:0: Attached scsi generic sg1 type 0

---

### Post by chewearn on 2008-01-27
Ok, I'm by no means an expert in this area.  But here is what I come up with after some search:
[http://ubuntuforums.org/showthread.php?t=198697](http://ubuntuforums.org/showthread.php?t=198697)

The above thread, while dealing with PCMCIA instead of SD card reader, might still be most relevant to your situation.


Quote from the thread post #2:
>  My guess would be that HAL doesn't think that device is removable. With
the card inserted, try doing "lshal |grep -C3 remov" . That'll output some
text - look for the block that shows your PCMCIA card. What does the
"storage.removable" line say?

If it says "false", file a bug against HAL.

Why don't you try that command and see if your have exactly the same problem.

```
lshal | grep -C3 remov
```

---

