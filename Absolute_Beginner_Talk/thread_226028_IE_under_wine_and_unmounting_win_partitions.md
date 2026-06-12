---
title: "IE under wine and unmounting win partitions"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Endow on 2006-07-30
1-Okay so I have my three windows partiitons on my desktop and when I umount them they only umount for that session (meaning if I restart the computer they re-appear) : I would like to know how I can permanently umount them and what I should do if in the future I want to access them agehn.


2-I'm trying to get the rest of guys here at home to use Ubuntu.But it has not been easy since there are some uncompatabilities (openoffice VS microsoftoffice) with their previous routine.One of them is those sites whith some specific application that requires internet explorer to run.

So I heard you could use wine to run IE.Can someone tell me exactly what I must do after installing wine(which I already did).


PS:Is there any other, more simple, way to solve my IE pages problem?(maybe some plugin...)

---

### Post by ajgreeny on 2006-07-30
You must have lines in your /etc/fstab file that tell ubuntu to mount the windows partitions at bootup.

Backup your /etc/fstab file in case anything goes wrong then delete the lines that relate to your windows partitions.  They will probably be fairly obvious, and will be the ones with ntfs or vfat as the file system type in the lines.  Save the edited file.

Now it is best to restart your computer to check all is well, so do that.

Assuming it all starts up without any problems and that your windows partitions are not now mounted, you can now mount them manually by opening a terminal and typing:-
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

for winXP in ntfs format, or if in fat32 (also for older windows versions)
type :-

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

To unmount these partitions type:-

sudo umount /media/windows/

This will work for both formatted types.

Sorry I can't help with the wine question as I've never managed to get it to work properly with my system, and I don't need it so have not persevered

---

### Post by Endow on 2006-07-30
Thanks man.I ended up commenting the lines a sopposed to deleting them altogether.It worked :)


Now if anyone could solve my IE problem...

---

### Post by Jagot on 2006-07-30
> **Endow said:**
> Now if anyone could solve my IE problem...

After installing Wine make sure you have run this command:

```
winecfg
```

Then, by far and away the easiest method of installing IE can be found here:

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

### Post by Kilz on 2006-07-30
Since Jagot told you how to install IE, let me add that IE isnt safe. Its ok if you want to use it to get to the 1 or 2 sites that abaslutly wont work without it and you have to go to them. Its also nice to have if you design web pages and want to see how they look in IE. 
But dont go sufing with it. Dont think because you are on linux its ok to use it and bugs cant get you. Wine is a bug for bug windows copy. IE is one huge security hole. Use Firefox :D

---

