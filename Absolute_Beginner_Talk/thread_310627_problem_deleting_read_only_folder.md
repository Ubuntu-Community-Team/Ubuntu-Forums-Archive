---
title: "problem deleting read only folder"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by kditty on 2006-12-01
i am having trouble deleting a folder, i mounted an iso image to use with dvdshrink, and it left a folder on my desktop /home/kditty/Desktop/video_ts/, the folder is read only, and ive tried everything i know to delete this folder.

sudo chown -R kditty:kditty /home/kditty/Desktop/video_ts/
didnt work

gksudo nautilus didnt work, i need to know how to change these permissions to make the folder read write and execute.

---

### Post by echo $USER on 2006-12-01
> **kditty said:**
> i am having trouble deleting a folder, i mounted an iso image to use with dvdshrink, and it left a folder on my desktop /home/kditty/Desktop/video_ts/, the folder is read only, and ive tried everything i know to delete this folder.

sudo chown -R kditty:kditty /home/kditty/Desktop/video_ts/
didnt work

gksudo nautilus didnt work, i need to know how to change these permissions to make the folder read write and execute.

Open terminal
> cd /home/kditty/Desktop
> sudo rm -rf video_ts

---

### Post by kditty on 2006-12-01
kditty@kdapper:~$ cd /home/kditty/Desktop
kditty@kdapper:~/Desktop$ sudo rm -rf video_ts
Password:
rm: cannot remove `video_ts/video_ts.bup': Read-only file system
rm: cannot remove `video_ts/video_ts.ifo': Read-only file system
rm: cannot remove `video_ts/vts_01_0.bup': Read-only file system
rm: cannot remove `video_ts/vts_01_0.ifo': Read-only file system
rm: cannot remove `video_ts/vts_01_0.vob': Read-only file system
rm: cannot remove `video_ts/vts_01_1.vob': Read-only file system
rm: cannot remove `video_ts/vts_01_2.vob': Read-only file system
rm: cannot remove `video_ts/vts_01_3.vob': Read-only file system
rm: cannot remove `video_ts/vts_01_4.vob': Read-only file system
rm: cannot remove `video_ts/vts_01_5.vob': Read-only file system
rm: cannot remove `video_ts/vts_01_6.vob': Read-only file system
rm: cannot remove `video_ts/vts_01_7.vob': Read-only file system
rm: cannot remove `video_ts/vts_01_8.vob': Read-only file system
rm: cannot remove `video_ts/vts_02_0.bup': Read-only file system
rm: cannot remove `video_ts/vts_02_0.ifo': Read-only file system
rm: cannot remove `video_ts/vts_02_1.vob': Read-only file system

---

### Post by echo $USER on 2006-12-01
Is the .iso still mounted?  If so, unmount and try again.

---

### Post by dwblas on 2006-12-01
> Is the .iso still mounted? If so, unmount and try again.Esactly.  Sounds like the partition is mounted as read only.  Check /etc/fstab to see if there is an "ro" for this partition in the fourth column over.  Umount and mount /dev/whatever /mount-point should fix the problem, or just delete the "ro" in /etc/fstab and umount and remount if that is the problem.  Check man mount if you want to know more.

---

### Post by dynamicdude on 2007-07-20
[COLOR="Red"][SIZE="6"]**i m having the same problem here... and i dont know wat to do or how i can change or unmount or delete the "Read-only file system"**[/SIZE][/COLOR]:confused::confused::confused::confused:

---

