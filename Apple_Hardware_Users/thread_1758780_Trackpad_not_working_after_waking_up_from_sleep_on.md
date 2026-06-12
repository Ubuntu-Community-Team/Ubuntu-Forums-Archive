---
title: "Trackpad not working after waking up from sleep on Natty"
date: 2011-05-15
forum: Apple Hardware Users
---

### Post by finitybeyond on 2011-05-15
I have had a issue with the trackpad not working (cursor does not move, does not click) after I wake up my MacBook Pro 4,1 from sleep. I am pretty sure this is an X issue and not a driver issue because if I log out the trackpad works again. This is also sporadic. Sometimes it occurs, sometimes it does not. Is there some configuration I need to set to fix this? Thanks.

I am running Natty x86_64.

---

### Post by binox on 2011-05-15
I have a similar problem on a MacBookPro4.1 with 11.04 aswell.
except me the cursor doesn't even move. I have an external bluetooth mouse which works fine. If I logout and back it works.
I previously fixed this problem before formatting, I had added i8042.reset to /boot/grub/grub.cfg at the end of this line:
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=16a8a65a-e039-4042-a17e-790d47283f3a ro   quiet splash vt.handoff=7
it was actually working! but then I had to format my computer for other reasons and now this solution doesn't work anymore.
The first time I got it working, I had tried several other things before the grub.cfg fix, so possibly it was a combination of several things but I don't remember what else I did to fix it.

Try doing that and see if that works, I'm going to keep searching for what it is that I had done...

---

### Post by finitybeyond on 2011-05-17
Sorry, I miswrote my description. The cursor DOES NOT move for me either. Thanks. I'll try it and I'll keep looking too.

---

### Post by sirphilip on 2011-05-18
I have the same problem. It happened infrequently before I upgraded to Natty, but since the upgrade it has become much more frequent. Let me know if you find a solution.

EDIT: I also have a macbook pro 4,1

---

### Post by mulbric3 on 2011-11-18
I'm affected by this bug on a MBP3,1 and Oneric. Did you guys find a fix?

---

