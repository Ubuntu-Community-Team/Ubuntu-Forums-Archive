---
title: "Mounting drive and access point"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by jrgibb on 2007-06-15
Ok, I just starting to get my head around the way Linux file system works and the root user system but . . . I have added a 2nd drive to my system, it's nicely formated and ready to go. In Disk Manager I have it pointing to a directory I created in my home folder (the access path), the only problem is that the permissions (on this new folder) have changed to "root" and I cant write to the folder now. How do I change the permissions to allow me to access this folder (and my new drive).

Thanks,

J

---

### Post by aaron_summer on 2007-06-15
I am new to Linux also.

Yesturday I built a RAID 1 device with 2 external USB drives and ran into the same problem when I first mounted the new device.

I used chown to change the ownership of the drive to my username from root.

```
sudo chown -R username device
```

I replaced username with my login and device happened to be /dev/md0.

Let me know if that works for you.

---

### Post by jrgibb on 2007-06-15
Thanks, how would I run this command, sorry not up to speed with running commands, real newbie !

---

### Post by Inxsible on 2007-06-15
Applications --> Accessories --> Terminal
 
Then type in ```
sudo fdisk -l
``` -l is lowercase L
 
This will give you the device name. Post the output here..so we can help you figure out the next command
then you do what the previous poster suggested:
```
sudo chown -R <your username>:<your group> <path obtained from step 1>
```

---

### Post by jrgibb on 2007-06-15
after running fdisk the device name of the new drive is /dev/hdc 

J

---

### Post by steve.horsley on 2007-06-15
What filesystem is it formatted to, and what is the name of the folder where you're mounting it?

I'll assume it is being mounted on a folder called /home/jrgibb/newdisk for now.

If it's a unix type filesystem (ext2/3, reiserfs etc) then it stores the owner and permissions for every file and you can make it all owned by jrgibb with this command:
**sudo chown jrgigg:jrgibb  /home/jrgibb/newdisk**

but if it's a non-unix filesystem (FAT, NTFS etc) then it can't store file ownserships, and they are emulated to a fixed value specified at the time the disk is mounted. The mount option you need is probabaly **umask=0**.

---

### Post by jrgibb on 2007-06-15
Thanks all,

=D>=D>=D>=D>=D>

Sorted, the command was;

sudo chown -R jrgibb:jrgibb /home/jrgibb/*newdisk*

Thanks again !

J

---

