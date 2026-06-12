---
title: "Best formating option?"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by ovidiu82 on 2006-02-08
I just used the Gparter to convert my windows ntfs partition in ext3 mode..

now I don't see then partition because the program doesn't see a partition anymore where it should be the partition...

What should I do?

---

### Post by Kapre on 2006-02-08
[QUOTE=ovidiu82]I just used the Gparter to convert my windows ntfs partition in ext3 mode..

now I don't see then partition because the program doesn't see a partition anymore where it should be the partition...

What should I do?[/QUOTE]

ovidiu82 - Did you have any errors when you converted (any pop ups or something?). if there is none, try rebooting as changes will not be automagic. Post again.

K

---

### Post by ovidiu82 on 2006-02-08
Thanks a lot for your help...

I think I won'e ever be able to at least use the minimum features of this OS...

Either im dumb, either this ain't easy..

Now I formated the windows partition I had with fat 32...and i can't see it , i can't access it....Any idea why and which are the magic words?

I rebooted but I cannot access the partition...it is unmounted....

thank you...

---

### Post by carlosqueso on 2006-02-08
you need to mount the partition.  First create a directory to mount it, say...../mnt/windows. ```
sudo mkdir /mnt/windows
```  Then mount the partition on the directory.  You need to find what your partition is called by using ```
fdisk -l
```  You can then mount the partition by typing ```
sudo mount /dev/<partition name> /mnt/windows
```  If that works and you want it to mount on boot, add the following line to your fstab file by typing sudo gedit /etc/fstab  ```
/dev/<partition name>   /mnt/windows  vfat  umask=000
```  Don't get discouraged....like anything, linux takes some time to learn, but I promise you it's rewarding.

---

