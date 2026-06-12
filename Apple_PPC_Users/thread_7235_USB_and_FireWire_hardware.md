---
title: "USB and FireWire hardware"
date: 2004-12-05
forum: Apple PPC Users
---

### Post by luboshiq on 2004-12-05
I have just installed Ubuntu 4.10 on my iMac G3. Everything is working as should except my two devices:

1. Harman/Kardon Soundsticks (connected through USB)
    - I can see it in Volume Control but the sound is playing through built-in iMac speakers. How do I select that it should use Soundsticks? Is it possible to disable built-in speakers (I don't want to use them at all under Ubuntu)?

2. External LaCie DVD writer (connected through FireWire)
    - when I the disc in and try to open CD ROM 2 it says: 
mount: special device /dev/scd0 does not exist
    - CD ROM 1 represents built-in cdrom and works fine

Can you help? Thanks.

---

### Post by luboshiq on 2004-12-05
Meanwhile I fixed the sound issue:
iMac built-in audio is controlled by kernel module called snd-powermac so I disabled it in file /etc/modules. Now I only see Soundsticks in Volume Control.

Any suggestions about the external DVD?

---

### Post by luboshiq on 2004-12-06
OK, fixed that too.
I told the system to mount /dev/sr0 instead of /scd0

Thanks everybody for help  :grin:

---

