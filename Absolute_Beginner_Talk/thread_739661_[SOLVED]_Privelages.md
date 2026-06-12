---
title: "[SOLVED] Privelages"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by sirisaac87 on 2008-03-29
I have my music partitoned when i was running vista, now i am trying to mount this drive in ubuntu but it is saying "You are not privileged to mount the volume 'Music'."  How do I gain privileges to perform this operation?

---

### Post by herbster on 2008-03-29
Paste the output of

```
sudo fdisk -l
```

and

```
df -h
```

Using [code] tags please. Also, what kind of drive is it? Internal? External? USB? etc.

---

### Post by sirisaac87 on 2008-03-29
It is a internal hard drive...

---

### Post by herbster on 2008-03-29
Paste the output from those commands above please.

---

### Post by sirisaac87 on 2008-03-29
sirisaac@Bossman07:~$ sudo fdisk -l
[sudo] password for sirisaac:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d3c4d3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8056    64709788+   7  HPFS/NTFS
/dev/sda2           10546       14462    31463302+   7  HPFS/NTFS
/dev/sda3           14463       14593     1052226   d7  Unknown
/dev/sda4            8057       10545    19992892+   5  Extended
/dev/sda5   *        8057       10435    19109286   83  Linux
/dev/sda6           10436       10545      883543+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984      991747+   6  FAT16

Disk /dev/dm-0: 1015 MB, 1015549440 bytes
255 heads, 63 sectors/track, 123 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System

Disk /dev/dm-1: 66.2 GB, 66262823424 bytes
255 heads, 63 sectors/track, 8055 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 32.2 GB, 32218421760 bytes
255 heads, 63 sectors/track, 3917 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 1077 MB, 1077479424 bytes
255 heads, 63 sectors/track, 130 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-3p1   ?       13578      119522   850995205   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(368, 111, 45) logical=(13577, 238, 11)
Partition 1 has different physical/logical endings:
     phys=(371, 101, 51) logical=(119521, 238, 60)
Partition 1 does not end on cylinder boundary.
/dev/dm-3p2   ?       45382       79243   271987362   74  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(67, 115, 32) logical=(45381, 70, 3)
Partition 2 has different physical/logical endings:
     phys=(299, 114, 44) logical=(79242, 34, 29)
Partition 2 does not end on cylinder boundary.
/dev/dm-3p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(114, 111, 32) logical=(10498, 56, 41)
Partition 3 has different physical/logical endings:
     phys=(353, 115, 52) logical=(10498, 56, 40)
Partition 3 does not end on cylinder boundary.
/dev/dm-3p4          167628      167631       25817+  4c  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(336, 0, 17) logical=(167627, 190, 52)
Partition 4 has different physical/logical endings:
     phys=(0, 89, 0) logical=(167630, 245, 26)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order




sirisaac@Bossman07:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              18G  2.7G   15G  16% /
varrun                755M  104K  755M   1% /var/run
varlock               755M  4.0K  755M   1% /var/lock
udev                  755M  100K  755M   1% /dev
devshm                755M     0  755M   0% /dev/shm
lrm                   755M   34M  722M   5% /lib/modules/2.6.22-14-generic/volatile

---

### Post by iSplicer on 2008-03-29
Are you trying to mount from the terminal or the GUI? If you are trying to mount using a terminal command, put "sudo" in front of the command

---

### Post by herbster on 2008-03-29
Do you know which drive and/or partition the music is on? Was it on a Windows partition that you since haven't touched (as in, haven't formatted or anything)? Then it would one of the NTFS drives.

---

### Post by sirisaac87 on 2008-03-29
I am trying to mount from the terminal and what would be the exact command that I would use to do that?  I also tried from the GUI, but that is when I get the message that I don't have the privileges to perform the operation.  Also the drive sda2 is the one that I am trying to mount.  This drive was originally partitoned in windows vista and i have not re partitioned at all for Ubuntu

---

### Post by herbster on 2008-03-30
Okay, so that's an NTFS part. What command were you issuing exactly? Paste it here so we can be sure it's correct before you use sudo perhaps mistakingly.

---

### Post by sirisaac87 on 2008-03-30
1) sudo mkdir /mnt/sda2
2) sudo ntfs-3g /dev/sda2 /mnt/sda2

---

### Post by sirisaac87 on 2008-03-30
is this the code I should be using? or is there another one that will do the trick?

---

### Post by sirisaac87 on 2008-03-30
Can Someone PLEASE help me?

---

### Post by herbster on 2008-03-30
Have you tried using ntfs-3g? Applications > System, I think.

---

### Post by rkd on 2008-03-30
The commands you showed in post #10 seem correct to me.

If you said in one of your posts that you got the error message about not being privileged to mount the volume when using the GUI.  What message do you get when using those commands in post #10?  That might tell us something more specific.

I just did a little Google searching for that error message, and what I found seems to indicate that it can mean that the NTFS volume was not cleanly closed by Windows the last time.  I don't know what that has to do with privileges, but that is what I see reported.

If you haven't tried this already, boot into Vista, login and make sure that you can access the files on that volume, then use Vista's option to turn off the computer (I think you click the Start button and choose something from there which gives you choices such as shutdown, restart, sleep, switch user, and probably more -- I'm not a Vista user so I'm not familiar with it). Once the computer has turned off, start it up again and boot into Ubuntu and see whether you can access that volume.

If you want to have Music mounted automatically when you boot Ubuntu, that is possible and usually just requires entering a line into the file /etc/fstab.  But let's first get past the problem you are having now before trying to make it automatic.

---

### Post by spydon on 2008-03-30
You can try: ```
sudo mount -t auto /dev/sda2 /mnt/sda2
``` too, but I don't think it will work if ntfs-3g doesn't...

---

### Post by sirisaac87 on 2008-03-30
I went into Vista and access this drive with no problems.  I check the disk and fixed any errors it may have while I was in vista.  I then shutdown the computer through the start menu and booted up in linux.  I still dont have access to this drive. When I go through the GUI and try to mount it it says "You are not privileged to mount the volume 'Music'."

When it try through command line:

sirisaac@Bossman07:~$ sudo mount -t auto /dev/sda2 /mnt/sda2
[sudo] password for sirisaac:
fuse: mount failed: Device or resource busy

or

sirisaac@Bossman07:~$ sudo ntfs-3g /dev/sda2 /media/sda2
fuse: mount failed: Device or resource busy

---

### Post by sirisaac87 on 2008-03-30
how do I get past this? is it even possible to mount this drive?

---

### Post by rkd on 2008-03-30
Please reboot into Ubuntu again and without trying to use the GUI method, try the command line method. It might be that the earlier attempt to mount using the GUI is preventing us from seeing the main problem.

Just use the command:```
sudo ntfs-3g /dev/sda2 /media/sda2
```The other one is approximately equivalent, but I think the ntfs-3g one is a little better.

If that attempt gets the same uninformative message, there are other things to try, but they are more complicated, so let's try the simple way first.

---

### Post by sirisaac87 on 2008-03-30
I did exactly as you said do, and I got the same result

---

### Post by rkd on 2008-03-30
Okay, on to a slightly harder test.

I'm trying to find an error message that tells what mount is finding wrong with the volume.  We couldn't see it at the command line, apparently because something is happening automatically before you get to attempt the mount from the command line.

One place to look for error messages in this situation is in the system log file.  There are a couple of ways to look at the system log file, and it has a very large number of messages, which makes finding relevant ones difficult, but I think that is the best next step.  Here is what to do:

1. Note the current time from Ubuntu's clock -- in the upper right of the screen, if you have the normal setup.

2. Reboot and login as usual.

3. When you are logged in, open a Terminal and enter the command to attempt to mount the volume.  We know it won't work.

4. Now enter this command:```
gksu gedit /var/log/syslog
```You can use a different editor if you prefer it to gedit.

5. When the editor opens and displays the file, page down until you find lines with the time corresponding to the time you noted before rebooting.  There will be some messages something like```

Mar 29 15:34:13 athlon kernel: Inspecting /boot/System.map-2.6.22-14-generic
Mar 29 15:34:13 athlon kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Mar 29 15:34:13 athlon kernel: Symbols match kernel version 2.6.22
```These messages come at the start of the boot process.

6. Open another editor to create a new file in your home directory.  Make the new file with any name you like, but be sure to give it the .txt extension at the end of the name.  Something like log.txt would be fine.

7. Copy and paste all of the messages from the beginning of the boot process to the end of the file into the other editor. Save the file in the other editor and close both editors.

8. Make a post here in the forum and attach the file you created above.  Don't paste its text into the post -- that would make the post extremely long.  The attach function is found below the message composition box when creating a posting.  Look for the heading "Additional Options" (in red) and below that, "Attach files".

---

### Post by sirisaac87 on 2008-03-30
I tried to upload it, but the document exceeds the upload limit. the document is 389.9kb and the limit is 19.8...what should I do?

---

### Post by rkd on 2008-03-30
Try compressing it with gzip.  Suppose the file is named log.txt. Try the commands:```
cp log.txt log-save.txt
gzip log-save.txt
ls -l log-save*
```I suggest making the copy first because gzip replaces the file you give it with the compressed file. Those command should create a file named log-save.txt.gz, and the ls command at the end should show you its size.  If it is small enough, attach it to a post.  If it is still too large, and I'm afraid it might be, perhaps you should look through log.txt for messages that mention /dev/sda2, pull out a few messages around each occurrence, and post those excerpts.  That still might overlook something important, but it might give enough clues to point to the problem.

---

