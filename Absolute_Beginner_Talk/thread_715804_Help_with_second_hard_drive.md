---
title: "Help with second hard drive"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by acl123 on 2008-03-05
Hi, I plugged a second hard drive in - it's a FAT32 drive.
Ubuntu finds it automatically and I can access it but I need to enter my root password. I want to have TimeVault run backups to this drive so this won't work for me.

Googling around it looks like I needed to add a line to /etc/fstab/. So I added this one:
/deb/hdd1 /media/DATA vfat user 0 0

(The name "DATA" is the name given to the drive back when it was on windows, and the name that Ubuntu automatically gives it in Nautilus.)

However, when I reboot I still need a password to access the drive. I also notice there are two entries under the media folder now: "/media/DATA" and "/media/DATA_" (with an underscore at the end)

Nautilus seems a bit confused about this now. In the list of folders on the left hand side it is called "DATA", but when I go to the drive it is called "/media/DATA_" in the location.

Of course, TimeVault still doesn't seem to be working either.

Could someone help me out?

---

### Post by ruy_lopez on 2008-03-05
Unmount.

Remove DATA_

Run chown on /media/DATA, so you own it. Reboot.

---

### Post by acl123 on 2008-03-05
Hi thanks,

I changed the owner and group of the hard drive using this command:
```

chown -hR acl:trusted-local DATA

```


After that I rebooted but the boot sequence crashed and I ended up in a shell. I'm not sure what caused this and whether it was related, but after rebooting again it was OK.

Now DATA_ seems to be gone from /media/ which is good.

I still have a few problems though:
1) In Thunar, the DATA drive is listed in the left-hand tree. However, if I click on it, Thunar freezes and I have to kill it.
2) The DATA drive is not listed in the tree in Nautilus, although I can browse to it through the /media/ folder.
3) TimeVault doesn't seem to be running backups to the drive.

Could you help me out some more?

---

### Post by acl123 on 2008-03-06
There still seems to be something messed up. Just some further info -

Even though I have a folder called /media/DATA/ and I can browse on to my hard drive, according to "mount" there is nothing mounted there.

When I type "umount /media/DATA/" it says "/media/DATA/ is not mounted (according to mtab).

This is with the entry in fstab, so it should be mounted. Although I think that /media/DATA/ folder appeared automatically before I even manually added an entry in fstab.

This is very confusing - could someone please help me?

---

