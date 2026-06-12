---
title: "Mounting directory on startup"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by ld99 on 2006-01-30
Hi,

After some hours I finally figured out how to mount my Windows 2000 (FAT32) partition.

Now it is mounted as /mnt/d_drive

I managed to mount one of the directory into my home folder by using the command line:
"sudo mount --bind /mnt/d_drive/tv /home/ld99/TV"

My question is, how can I mount the directory automatically on startup?

Thanks!!

---

### Post by moephan on 2006-01-30
Try going System->Preferences->Sessions, selecting the "Start Up Programs" tab, clicking the Add button, and pasting your command in there. 

Cheers, Rick

---

### Post by Klaidas on 2006-01-30
This guide should be helpful: [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

EDIT: oh, this link if for mounting windows :/ I didn;t read all the post so it's kinda wrong guide

---

### Post by AndyCooll on 2006-01-30
You need to edit your /etc/fstab to include a line something like the following:

/dev/hda5       /nameofyourWin2000drive          vfat    defaults        0       0

:cool:

---

### Post by ld99 on 2006-01-31
moephan:

Thank you for that tip, but unfortunately, because the command requires "sudo" (which normally prompts for password) and putting in the command in that "Start Up Programs" tab probably caused the command aborts without error.

I am quite sure about the accuracy of the command line that I put in there... because if I copy and paste it into a console, the directory (/mnt/d_drive/tv) is mounted at the new location (/home/ld99/TV), AFTER I entered the correct password.

And yet the same command line had no effect when it was in the "Start Up Programs". :cry: 

Klaidas:

Thank you for the link, but unfortunately (as you have also realised), the guide is for mounting windows partitions and I have already done that. What I would like to know is, how to automatically mount a directory to a different location on startup? (The fact that the directory was on a windows partition (which has already been mounted) shouldn't really change anything, should it?)

But thanks anyway. :) 

AndyCooll:

Thanks, but the line you quoted mounts my windows partition, which I have already done. But thank you anyway. :)

---

### Post by frodon on 2006-01-31
[QUOTE=ld99]Hi,

After some hours I finally figured out how to mount my Windows 2000 (FAT32) partition.

Now it is mounted as /mnt/d_drive

I managed to mount one of the directory into my home folder by using the command line:
"sudo mount --bind /mnt/d_drive/tv /home/ld99/TV"

My question is, how can I mount the directory automatically on startup?

Thanks!![/QUOTE]If i understand well you want to mount /mnt/d_drive/tv directory in /home/ld99/TV on startup. So add a line like that in your fstab file and do a "sudo mount -a" or reboot : ```
/mnt/d_drive/tv /home/ld99/TV vfat bind 0 0
```

---

### Post by ld99 on 2006-01-31
[QUOTE=frodon]If i understand well you want to mount /mnt/d_drive/tv directory in /home/ld99/TV on startup.[/QUOTE]
That is exactly it!!!

[QUOTE=frodon]```
/mnt/d_drive/tv /home/ld99/TV vfat bind 0 0
```[/QUOTE]
That is exactly it!!!

\\:D/ 

That "bind" worked like a charm. Thank you so much!! My mistake was that I kept putting "defaults" in the option field instead of "bind". Silly me. :rolleyes:

---

