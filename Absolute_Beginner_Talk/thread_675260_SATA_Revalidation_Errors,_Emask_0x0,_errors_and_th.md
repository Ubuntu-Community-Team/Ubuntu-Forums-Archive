---
title: "SATA Revalidation Errors, Emask 0x0, errors and the like"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by MoonDoggie on 2008-01-22
Ok, this is starting to drive me crazy, I've successfully been Ubuntu for several days with this persistent  issue.  I have read all related posts and no-one else seems to be experiencing the same problem. 

My specs are as follows:
Mobo: Asus P5W DH Deluxe
CPU: intel core 2 duo e6600 (@3.0ghz)
HD: 300gb Seagate SATA Drive

I apologize for not being able to isolate the issue, but here is what happens.

After a few boots into linux, it starts giving me "ata3.00 Revalidation errors" etc. "Exception to Emask 0x0" blah blah, the only way to fix this problem is to append "piix" to the file /etc/initramfs-tools/modules file and update it with "update-initramfs -u" however, it never seems to fix the bootup problem for long.

I've checked the modules.conf file and found that you can set it to not rebuild the modules file, so I tried that so it doesn't keep overwritting the file, but that still doesn't allow me to always boot.  

Whenever it doesn't boot, I have to go to the LIVE cd and in the gnome-terminal look at the contents of the /etc/initramfs-tools/modules file via

```

cat /etc/initramfs-tools/modules

```

and it always is reverted back to the same blank (except for comments) file...Then when I do the above steps (add "piix" to the end of the file, and re-update) it boots normally.  

But it's an endless cycle where the file keeps getting overwritten, and is the only thing that's wrong with my system.  Hopefully someone will have experience or an idea on how to load this driver by default another way rather than initramfs.  

Many thanks for all you guys do for us new users,
Colin

---

### Post by skymera on 2008-01-22
try adding piix to /etc/modules

just a guess, put the file you trying to change [etc/initramfs-tools/moduels] as a read-only?

---

### Post by MoonDoggie on 2008-01-22
Are you saying mark the initramfs-tools/modules file as read only? or warning me to make sure it's not?   :)

Do I need to do any kind of an update-modules -u or anything after I edit the /etc/modules file?

-Colin

---

### Post by skymera on 2008-01-22
erm im not sure about the file.
its a gamble i never done it.

but the /etc/modules i think you just restart

try the second one first :D

---

### Post by MoonDoggie on 2008-01-22
Thanks for the suggestion I will try it.  Any other ideas?

---

### Post by MoonDoggie on 2008-01-22
Tried adding it to the modules didn't seem to make a difference.  However, I did figure something else out.  When it doesn't boot and starts throwing Revalidation Errors, if I restart it sometimes it restarts perfectly.  And I'm noticing the /etc/initramfs-tools/modules file isn't getting overwritten at all, it is failing to boot for another reason.  I suspect a driver issue.

---

### Post by MoonDoggie on 2008-01-23
bump :)

---

