---
title: "[SOLVED] cannot mount volume"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by short3000y on 2007-12-06
in ubuntu, when i go to [places>computer] and try to go into another one of my drives i get the "cannot mount volume" error messege. please help!

~Nate

---

### Post by PmDematagoda on 2007-12-06
Post the output of:-
```

cat /etc/mtab
```
 
And what drive label are you trying to open?

---

### Post by short3000y on 2007-12-06
/dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0



im trying to poen a partioned drive (both C and D)

---

### Post by PmDematagoda on 2007-12-06
Post the result of:-

```
sudo fdisk -l
```

---

### Post by short3000y on 2007-12-06
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x547d547d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3918    31471303+   7  HPFS/NTFS
/dev/sda2            3919        9729    46676857+   f  W95 Ext'd (LBA)
/dev/sda5            3919        9295    43190721    7  HPFS/NTFS
/dev/sda6            9296        9729     3486073+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc50bc1f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29645   238123431   83  Linux
/dev/sdb2           29646       30401     6072570    5  Extended
/dev/sdb5           29646       30401     6072538+  82  Linux swap / Solaris




please help!

---

### Post by short3000y on 2007-12-06
please someone help!

---

### Post by kpkeerthi on 2007-12-06
1. Make folders where the partions will be mounted
```

sudo mkdir /media/windows_c
sudo mkdir /media/windows_d

```

2. Open /etc/fstab
```

gksudo gedit /etc/fstab

```

3. Add the following lines at the end of the file
```

/dev/sda5 /media/windows_c ntfs-3g defaults 0 0
/dev/sda6 /media/windows_d ntfs-3g defaults 0 0

```

4. Save and Exit. 

5. **Restart ** (you should now see shortcuts on your desktop)

---

### Post by short3000y on 2007-12-06
at step 2, what do i edit? like what do i do?

---

### Post by kpkeerthi on 2007-12-06
Follow step 3.

---

### Post by lswest on 2007-12-06
what he means in step 2 is to enter the command given into a terminal, and at the end of the text file which was opened, append the following lines from step 3

---

### Post by short3000y on 2007-12-06
i followed the steps, and rebooted and it still has the same error...

---

### Post by kpkeerthi on 2007-12-06
OK. lets see if we could capture the error details.
Open terminal post the output of
```

sudo mount -t ntfs-3g /dev/sda5 /media/windows_c

```

---

### Post by short3000y on 2007-12-06
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/windows_c -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/windows_c ntfs-3g defaults,force 0 0

---

### Post by kpkeerthi on 2007-12-06
There you go. The error message says it all. Boot into windows and make sure you shut it down properly incase you did not do it last time or if you have windows hibernated.

Note: I have this message thrown at me sometimes (very rarely per se) even though my windows shuts down properly. All I do is boot windows again and shut it down again and the partitions mount.

---

### Post by short3000y on 2007-12-06
it worked!!!!! thank you thank you thank you!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by kpkeerthi on 2007-12-06
You are welcome :).Can you put this thread to SOLVED.

---

### Post by vikramsharma on 2007-12-06
The same thing occurs when you hibernate in windows, for ntfs-3g to work properly you would have to perform proper (clean) shutdown of windows so that the windows partition can be mounted on Linux.

---

### Post by PmDematagoda on 2007-12-06
> **vikramsharma said:**
> The same thing occurs when you hibernate in windows, for ntfs-3g to work properly you would have to perform proper (clean) shutdown of windows so that the windows partition can be mounted on Linux.

Not necessarily, what if you had an external HDD having an NTFS filesystem on a PC that is 100% Linux and that particular HDD was not cleanly unmounted?
That cause a bit of a problem, so in cases like that you can use the force option of ntfs-3g to force the drive to be mounted which works just as well.

---

### Post by karasuhebi on 2008-03-01
What if I have a HDD that's just documents? It has no OS on it. How can I mount that one? I'm running from a Xubuntu Live CD and it says I have to be root to be able to mount. :-\

-Karasuhebi

---

### Post by karasuhebi on 2008-03-01
I just dug up one of my REALLY old HDDs (it's 6GBs big, lol) and installed Xubuntu on it. I'm using it right now to type this. I STILL can't mount my 250GB HDD (the one that doesn't have an OS on it). It keeps giving me the same error.

Help? :S
-Karasuhebi

---

### Post by PmDematagoda on 2008-03-01
Did you append the command to mount the drive with "sudo" which would allow you to run the command with root privileges?

---

### Post by karasuhebi on 2008-03-01
What I did was this:
-Opened terminal
-typed in "su root" and pressed enter
-typed in my password and pressed enter
-opened up fstab (in the /etc/ folder)
-added this line to fstab:
     "/dev/sdb1/media/250GB HDD" nfts-3g defaults,force 0 0

Was that the correct thing to do? Or did I do something wrong?
-Karasuhebi

---

