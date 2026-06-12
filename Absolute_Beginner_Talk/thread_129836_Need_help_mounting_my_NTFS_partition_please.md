---
title: "Need help mounting my NTFS partition please"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by Clark Nova on 2006-02-14
I have tried to follow the guide I found [here]("http://www.psychocats.net/linux/mountwindows.php") to get my file store from my XP partition mounted but it didn't seem to work. Here is the output from sudo fdisk -l :


```
simon@Desktop:~$ sudo fdisk -l

Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        2550    20474842+   f  W95 Ext'd (LBA)
/dev/hda2   *        2551       20023   140351841    7  HPFS/NTFS
/dev/hda5               2        2550    20474811    7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32        4998    39897427+   5  Extended
/dev/hdb5              32        4998    39897396   8e  Linux LVM
simon@Desktop:~$

```

The partition I want to mount is the 140gb one labelled hda2. Would somebody be so kind as to tell me what I need to type exactly? When I tried to mopunt it it said something about it being the wrong kind of partition.:???: 

Thanks:)

---

### Post by luckyaba on 2006-02-14
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

put this in the fstab file

/dev/hda2    /media/windows ntfs  nls=utf8,umask=0222 0    0

save and it should automount when you reboot to /media/windows

---

### Post by Clark Nova on 2006-02-14
Thanks so much! \\:D/ 

Now I feel like I really might be able to drop Windows altogether. I can play my movies and music from Linux and look at my photos. Am I correct thinking that I can only read from an NTFS partition and would need to convert it to FAT32 if I want to rearrange things in there?


Thanks again, you're a :KS

---

### Post by taurus on 2006-02-14
[QUOTE=SiBuntu]Am I correct thinking that I can only read from an NTFS partition and would need to convert it to FAT32 if I want to rearrange things in there?[/QUOTE]
That would be correct.  You can only read from NTFS for now but you can read and write to vfat (or fat32 as some people call it) from both Linux and Windows...

---

### Post by luckyaba on 2006-02-14
Yeah. I believe there is ways to give write access in NTFS partitions but i am pretty sure its fairly dangerous.

---

### Post by Clark Nova on 2006-02-14
Is it possible for me to convert it to FAT32 from Ubuntu or do I need to go back into XP and do it from there?
:???: 


Still chuffed to bits here\\:D/ \\:D/

---

### Post by taurus on 2006-02-14
[QUOTE=luckyaba]Yeah. I believe there is ways to give write access in NTFS partitions but i am pretty sure its fairly dangerous.[/QUOTE]
Oh sure, you can write to NTFS from Linux if you want to but when you try to boot into Windows, you will be greeted with an annoying message about your corrupt/damage partition!  Then, you will feel like you would run into a wall for doing such a dump task!!!

---

### Post by cjm5229 on 2006-02-14
If you try to reformat your ntfs partition you will lose all data that is on it. Reformatting erases everything and the writes the new file system over the top. If you can backup everything on it to another drive then format it to fat32 you can restore it that partition. It might be easier to make a fat 32 partition and transfer the files you want through it to Ubuntu.:D

---

### Post by luckyaba on 2006-02-14
[QUOTE=taurus]Oh sure, you can write to NTFS from Linux if you want to but when you try to boot into Windows, you will be greeted with an annoying message about your corrupt/damage partition!  Then, you will feel like you would run into a wall for doing such a dump task!!![/QUOTE]


yeah what he said.

---

### Post by Clark Nova on 2006-02-14
Is it possible then for me to just drag and drop the items from the NTFS partition and put them in a folder on my Ubuntu HDD? When I tried to do this with a photo and then edit it, Ubuntu said I did not have the permissions to do so. Do this mean that I need to do all of this from Windows?

---

### Post by Mustard on 2006-02-14
[QUOTE=SiBuntu]Is it possible then for me to just drag and drop the items from the NTFS partition and put them in a folder on my Ubuntu HDD? When I tried to do this with a photo and then edit it, Ubuntu said I did not have the permissions to do so. Do this mean that I need to do all of this from Windows?[/QUOTE]

I'm guessing a bit here, but I suspect that since the media was being taken off a 'read only' media, it may still have 'read only' permissions when it is moved to your local ubuntu folder.  This would definitely cause a permissions error if you tried to edit it anyway.  Permissions can be changed with the chmod command from terminal. If you gave an example of a filename and what folder it was in then I could show you basically what the chmod command would look like.  The chmod command could process a number of files all at one time.

If you feel like reading the manual on chmod try this command in terminal...

```
man chmod
#press the 'q' key to exit the manual
```

Alternatively, you could right click on the file icon and go to permissions tab and tick the relevant box to give it 'write' permissions for your user, but this would require that you do this for every file individually, and might be a tedious process if you have a lot of files.

---

### Post by cjm5229 on 2006-02-15
You could try it from Root Nautilus.
```
sudo nautilus
```
Then you can go to the permissions file and change the permissions on the file you transfered to Ubuntu.

---

### Post by Mustard on 2006-02-15
A safer way to run nautilus as root is to use..

```
gksudo nautilus
```

---

