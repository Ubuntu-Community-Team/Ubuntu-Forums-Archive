---
title: "Deleting files and folders in an NTFS partition"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-10-05
Cheers,

I have finally able to make my NTFS partitions read/write now I want to delete files and folders that I dont need from it.

but when I do
delphiguy@zion:/media/stuffs$ rm -dr 7-Zip

I get errors something like
rm: cannot remove `7-Zip/Codecs/Swap.dll': Operation not supported
rm: cannot remove `7-Zip/Formats/zip.dll': Operation not supported
rm: cannot remove `7-Zip/Lang/fr.txt': Operation not supported
rm: cannot remove `7-Zip/Lang/fi.txt': Operation not supported
rm: cannot remove `7-Zip/Lang/zh-tw.txt': Operation not supported

also when I do it from Places->Computer and right click on the folder and click on Move to Trash it gives me an error :
Error "Generic error" while deleting "/media/stuffs/7-Zip".

I will eventually get rid of my NTFS partitions but for the meantime I dont have the necessary means to Backup my files off it, so I have to temporary settle with it until I get myself a new HardDrive.

Thanks

---

### Post by delphiguy on 2006-10-05
Also I am wondering why my NTFS partitions are not automatically mounted while I have these in my /etc/fstab
/dev/hda5     /media/stuffs    ntfs-fuse       auto,group=ntfs,umask=007       0       0
/dev/sda1     /media/dropzone    ntfs-fuse       auto,group=ntfs,umask=007       0       0

I still need to do
sudo ntfsmount /dev/hda5 /media/stuffs -o umask=0007

any ideas why is this so?

---

### Post by arkangel on 2006-10-05
I dont know the current  state for NTFS support , but recently  linux was not able to add or remove files from a NTFS partion (reading and rewritting existing files is safe though )   

so be carefully  you could damage your partition  and make it unreadeable even in windows 

here you can [start reading ]("http://www.linux-ntfs.org/")

---

### Post by Ben Sprinkle on 2006-10-05
```
 but recently linux was not able to add or remove files from a NTFS parti
```
Still stands today as I remember it.

---

### Post by PriceChild on 2006-10-05
Yeah linux doesn't support writing to ntfs because MS haven't released the apporpriate specs for the filesystem.

However, there are drivers which are now claiming to be able to write safely to the drive. They do however accept its not perfect and problems could very easily occur.

Most require a script to be run after unmounting and simply forgetting this could cause windows' scandisk to mess up the drive completely and lost most of your data.

Be careful... all the software IS beta.

---

### Post by xyz on 2006-10-05
> **delphiguy said:**
> Also I am wondering why my NTFS partitions are not automatically mounted while I have these in my /etc/fstab
/dev/hda5     /media/stuffs    ntfs-fuse       auto,group=ntfs,umask=007       0       0
/dev/sda1     /media/dropzone    ntfs-fuse       auto,group=ntfs,umask=007       0       0

I still need to do
sudo ntfsmount /dev/hda5 /media/stuffs -o umask=0007

any ideas why is this so?


Hi-
This what mine says:
> /dev/hda1       /media/hda1     ntfs-3g defaults,locale=en_US.utf8   0    0    

I followed Givré's HowTo:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by delphiguy on 2006-10-05
Ok now I seem have read/write and creation/deletion on my NTFS partition, and I have also already deleted all those unwanted folders.  However I noticed that after deleting those folders and issuing "df" in the terminal window that there is still no change in the available space in my ntfs partition.

Did I do something wrong here? btw I deleted those folders from Places->Computers.

---

### Post by givré on 2006-10-05
How did you delete those file ?

> If you just select 'put in trash' or use the delete button, it'll not go in the trash but in a folder call .Trash-<username>, at the root of the partition, that is hidden.
Don't ask me why, i don't really know, that's not a driver issue but a gnome one, we have the same problem for FAT32.
So there is two way of doing things :
- Select explicitly 'delete' or use the <Shift><del> button, so the file/folder will really be deleted (no possibility of recovery)
- You could still use the 'put in trash' function, but don't forget that the trash will be in that case .Trash-<username>, and that you'll have to explicitly delete the files in this folder to 'empty the trash'

Goat Spirit, nice avatar ;)

---

### Post by delphiguy on 2006-10-05
Yep you beat me to it... I found it out by accident by issuing a "ls -a" and was surprised that there was indeed a directory called .Trash-<username>.  I tried doing "rm -dr .Trash-<username>" but that didnt seem to work.  So what I ended up doing is "cd .Trash-<username>" and from there deleted all of the folders.

And after doing that my free space shows up now on "df"

At last my NTFS saga is over, on to more challenging path in my adventure called Ubuntu.  Thanks for all the help.

---

### Post by givré on 2006-10-05
> **delphiguy said:**
> I tried doing "rm -dr .Trash-<username>" but that didnt seem to work.
rm -r .Trash-<username> is enough ;)

---

### Post by delphiguy on 2006-10-05
I'll keep that in mind.  Thanks a lot.

---

### Post by Ben Sprinkle on 2006-10-05
> **givré said:**
> How did you delete those file ?



Goat Spirit, nice avatar ;)
Oh yeah baby. :P

---

