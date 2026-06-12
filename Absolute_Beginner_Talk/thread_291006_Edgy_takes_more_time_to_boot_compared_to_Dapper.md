---
title: "Edgy takes more time to boot compared to Dapper"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Tamil on 2006-11-01
Dapper used to boot within 2 minutes but now Edgy (clean install) takes more than 3 minutes.

Edgy stops blinking for about 90 seconds after this.
> Checking file systems...
fsck 1.39 (29-may-2006)
/dev/sda2 clean 10582/2606080 files, 161180/5242880 blocks [ok]

How to reduce boot time?

---

### Post by Tamil on 2006-11-02
](*,)

---

### Post by firetux on 2006-11-02
Are you using reiserfs?

---

### Post by dillbertdabomb on 2006-11-02
there must be an error, try a diffrent section of the forums


I think that is accually a common error, your not the only one suffering

---

### Post by firetux on 2006-11-02
Install bootchart, reboot. In /var/log/bootchart there should be an image where you can see which processes take most time.

---

### Post by Shay Stephens on 2006-11-02
My edgy install was doing this too.  Turned out to be my data drive, which was fat32.  I backed it up, then formatted it to ext3 and loaded the data back on it.  Since then I have not had the constant disk checking.

So depending on your configuration, you may just need to backup and reformat a drive.

---

### Post by marx2k on 2006-11-02
Im a newbie but have been playing with mounting, resizing partitions and fstab...

The last option in /etc/fstab for each drive is either 0 or 1

0 = Do not fsck upon booting
1 = DO fsck upon booting

if you 'sudo gedit /etc/fstab' and see that there is a '1' at the end of the mount line for the drive youre complaining about being checked, change it to a '0' and reboot, see if that helps.

Im on an XP box right now so i cant recreate what the line looks like but from memory, mine looks something like

"/dev/hdb1 /media/hdb1 ext3 defaults 0 0"

If yours has a "0 1" at the end, you want to change that.

If yours has a "0 0" at the end, disregard this entire post :)

---

### Post by Tamil on 2006-11-03
> **marx2k said:**
> Im a newbie but have been playing with mounting, resizing partitions and fstab...

The last option in /etc/fstab for each drive is either 0 or 1

0 = Do not fsck upon booting
1 = DO fsck upon booting

if you 'sudo gedit /etc/fstab' and see that there is a '1' at the end of the mount line for the drive youre complaining about being checked, change it to a '0' and reboot, see if that helps.

Im on an XP box right now so i cant recreate what the line looks like but from memory, mine looks something like

"/dev/hdb1 /media/hdb1 ext3 defaults 0 0"

If yours has a "0 1" at the end, you want to change that.

If yours has a "0 0" at the end, disregard this entire post :)Thanks. Now it takes only 45 seconds to boot. :o

---

