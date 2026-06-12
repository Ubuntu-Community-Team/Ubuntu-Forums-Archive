---
title: "how can i Mount windows ME in ubuntu"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by realdog on 2006-01-29
ok, i want to mount my fat32 windows me that resized in my ubuntu, but when i go to gedit etc/fstab dont show my hda1 partition, what is wrong, i want to mount because  my modem is lucent win modem v.90 cheetah i cant connect to internet and i want to share files downloaded from internet from my windows partition to ubuntu, how can i do this possible, to resolve my problem of connection in ubuntu.

---

### Post by dueY on 2006-01-29
You have to add the line to fstab yourself it won't be there waiting for you!

---

### Post by dueY on 2006-01-29
Here:

```
sudo mkdir /media/windows
```
```
sudo gedit /etc/fstab
```

Add in ```
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
```

Assuming hda1 is where it is like you mentioned.

---

### Post by aysiu on 2006-01-29
dueY is right.
If you want more details and to know if it's /dev/hda1, see the fourth link of my signature.

---

### Post by dueY on 2006-01-29
[QUOTE=aysiu]dueY is right.
If you want more details and to know if it's /dev/hda1, see the fourth link of my signature.[/QUOTE]

aysiu: Do you own the psychocats.net domain?  You always seem to be pimping it out, just wondering :-\"

---

### Post by realdog on 2006-01-29
ok i did reinstall and made a partition of 1 gb fat 32, this partition is detected in my windows me, but isnt in ubuntu, i did fdisk -l and show me hda1 as windows 98 fat 32 lba, and hda6 as fat 32, but when i go to fstab they arent there,
 How can i make them visibles in fstab and make the changes and mounted in ubuntu. please help, i read all day and nothing has helped me.

---

### Post by Herman on 2006-01-29
[http://users.bigpond.net.au/hermanzone/p10.htm]("http://users.bigpond.net.au/hermanzone/p10.htm")
Try the above link and see if that helps. It's really just the same information as you have already been given, but sometimes it helps when things are explained again in a slightly different way.
If you are using 'Breezy' as opposed to 'Hoary' Ubuntu, your other partitions should normally appear automatically on boot-up as icons on your desktop, but you may need to edit /etc/fstab as explained, for the read+write permissions. 

Another (secondary) thought:
 One computer I have wouldn't automount on boot-up, and needed them manually mounted each time, until one day when it did an automatic forced file-system check. (They all do that once every thirty re-boots).
After that mine automatically mounted the other partitions. The file system check fixed it. If you suspect that could be your problem, to bring on a file-system check earlier, (similar to scan-disk) open a terminal and type in:
```
sudo touch /forcefsck
``` The, re-boot your computer and watch as it re-boots. 
(A row of === signs should progress across your monitor, with a spinning / in front). That will only help you if that's what your problem is though. It won't do any harm to try it anyway.

---

### Post by realdog on 2006-01-29
Thanks herman
 Thats what i need new info to try this, im going to do it i will later post results.

---

### Post by realdog on 2006-01-30
Nothing ocurrs when i did 
sudo touch /fsorcefsck
nothing occurs when i did
sudo mount /dev/hda1 /media/hda1 -t vfat -o iorcharset=utf8,unmask=000
results
wrong fstype, bad option, bad superblock on dev/hda1
I did 
dmesg
results last line  : FAT 32:Unrecognized mount option "iorcharset=utf88" or mising value

Im totally lost i want to use  linux but im thinking this is not for me, too geek,
i cant mount nothing i want to use cd dvd floppy nada Iim litttle frustrated right now, What can i do, try another distro or will be the same steps than this one.
i hope use the floppy to run scanmodem, later i will try post more details.

---

### Post by Ptero-4 on 2006-01-30
> nothing occurs when i did
sudo mount /dev/hda1 /media/hda1 -t vfat -o iorcharset=utf8,unmask=000

Hi. Realdog. you seem to have a typo in the iocharset and the umask parts. That may be what's causing the errors.

It should look like this
```
sudo mount /dev/hda1 /media/hda1 -t vfat -o iocharset=utf8,umask=000
```

---

### Post by realdog on 2006-01-30
Well i typed every combination and nada, but i finally could mount the floppy and take these screen shots

[IMG][[IMG]http://img297.imageshack.us/img297/8477/screenshot4ua.png[/IMG]](http://imageshack.us)[/IMG]
In these image you'll see that i have one windows partition where i have windows me (hda1)and the another that i created in ubuntu partitoner of 1 gb (fat32) logical (hda5)
[IMG][[IMG]http://img218.imageshack.us/img218/125/screenshot15lu.png[/IMG]](http://imageshack.us)[/IMG]
In these i dont see hda1 & hda5 that's why i cant make any chages.

That's what im tellin to you all i hope there is someone outhere with the right answer to finally see some light:-k

---

### Post by realdog on 2006-02-01
Well, all this seems to be my fault, english is not my native language, i couldn't understand until now, the answer was in the first responses, here what i did.
sudo gedit /etc/fstab
I add this line
/dev/hda5       /media/windows  auto,vfat   rw,umask=000   0       0
save,close
sudo mkdir /media/windows
with the partition hda5 i made
sudo mkfs.vfat -c /dev/hda5
then i go to "System"  "share folders" enter password and install samba
next
sudo mount /media/windows
and finally i coul read and write in the drive but i dont see in the desktop (icon)
Next task make my modem work i hope isn't going to be this bad.

---

