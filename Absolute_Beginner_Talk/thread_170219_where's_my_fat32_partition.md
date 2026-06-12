---
title: "where's my fat32 partition?"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-05-04
I cannot find the partition that I created while installing.
I left the Windows XP (9 GB NTFS) and made an fat32 logical partition (9 GB) and then a third partition for Ubuntu (11 GB).
I have understood that files in this partition should be accessible and writable from both windows and ubuntu. But how do I find it from Ubuntu?

---

### Post by AndyCooll on 2006-05-04
Just a few thoughts to begin the query: 

Can I assume that you followed the dual-booting instructions listed in my sig.?

If so have you edited your /etc/fstab so the partition will automatically be mounted on bootup?

If so, had you created a mount point to mount the partition too, and if so have you checked that file path?

:cool:

---

### Post by frodon on 2006-05-04
You will find the steps to do it here : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by 1002285 on 2006-05-04
[QUOTE=AndyCooll]Just a few thoughts to begin the query: 

Can I assume that you followed the dual-booting instructions listed in my sig.?

If so have you edited your /etc/fstab so the partition will automatically be mounted on bootup?

If so, had you created a mount point to mount the partition too, and if so have you checked that file path?

:cool:[/QUOTE]

OK, thank you. I did use these instructions but I had not read them that carefully. It seemed obvious that Ubuntu will understand that I wanted to use the partition.
So I followed the instructions again, and used 
*sudo touch /forcefsck first - I guess this did not help, but gave another interesting outcome I'll write about further on.
(I have downloaded the install CD image at the time the Breezy stable version just became available).
*sudo mount /dev/hda5 /media/FAT32 gave the positive result and I could save files and see them both from Ubuntu and Windows. But it did not mount again at the next boot.
*Now I tried editing the /etc/fstab file and added the line
/dev/hda5              /media/FAT32             vfat                umask=000               0            0
But at the next boot the system said "failed" at the point of "mounting local file systems". It still showed me my Ubuntu system and CD-ROM, but the FAT32 partition was not mounted. Now I did it again with the command "sudo mount ...
why might it have failed?

And the interesting thing about the "sudo touch /forcefsck first - I" command was that after that I saw the system boot the very first time saying "ok" to "starting hotplug subsystem". I have this problem that the computer often hangs at the reboot at the point of "starting hotplug subsystem" - it has been posted here quite a lot and seems to be common with laptops.
Is this a coincidence or might there be a connetion? And if I find out that this forcefsck is a good thing, can I make the computer do it at every boot?

And where can I find out more about the commands in Ubuntu? For instance I don't even know how to delete a file (If I can't do it from the file manager because I "don't have rights").

And then some of the other things I have not found out about are
- how to make GAIM and skype start at every log-on?
- can the MS Windows start button be made to open the "applications" menu.

Thanks, guys, if you can help on even one of these issues.

---

### Post by aysiu on 2006-05-04
What is all this *sudo touch* stuff?

Try this. Read the whole thing. It starts with NTFS as an example but talks about FAT32, too.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by 1002285 on 2006-05-04
I'm so sorry. I had made a typo in the fstab file. Now it did mount.

---

### Post by Engnome on 2006-05-04
sudo rm name/path to file

that will remove any file, to make something autostart:

System --> Preferences --> Sessions

Then click the start up programstab. Atleast I think this should work, havent tried as I hate apps that autostart.

---

