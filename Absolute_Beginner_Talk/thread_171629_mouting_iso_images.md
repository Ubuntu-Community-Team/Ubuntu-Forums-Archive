---
title: "mouting iso images?"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by stansz on 2006-05-07
for doing this in windows, all i do is using alcohol 120% and theirs an option available...but in ubuntu...wat program do i use? and how ?

---

### Post by mamato on 2006-05-07
For mounting ISO, you can use the mount command. First, create the direcotry where you want to mount it, for example```
mkdir ~/myimage 
```
and then, execute this command :
```
mount -t iso9660 -o loop filename.iso ~/myimage
```
Hope that helps :D

---

### Post by stansz on 2006-05-07
thnkx ill give that a try....are there any burnign programs with an option to just burn an iso ?? ill try to find one tomorrow morning..but the ones that i had now i cant find the option...

thnkx tho

---

### Post by adrenaline on 2006-05-07
Pretty sure to burn an iso file all you have to do is right-click it and select **Write to Disc**.

---

### Post by medya on 2006-05-07
> mount -t iso9660 -o loop filename.iso ~/myimage

I have the same request...
can you please tell me what these "**-t** **-o **  **loop** and **iso9660 ** do ?


and also I have another question,  I have several kinds of ISOs, (been made by Alcohol or CloneCD ..)  should I mount all of them with the same command?

---

### Post by ds[de] on 2006-05-07
[QUOTE=medya]can you please tell me what these "**-t** **-o **  **loop** and **iso9660 ** do ?[/QUOTE]

**-t** is an option to specify a file system, **iso9660** is the name of the file system used on CDs and DVDs.

I had to check the man pages for **-o loop**, and here's what I found:

If no explicit loop device is mentioned (but just an option ´-o loop´ is given), then **mount** will try to find some unused loop device and use that. If you are not so unwise as to make _/etc/mtab_ a symbolic link to _/proc/mounts_ then any loop device allocated by **mount** will be freed by **umount**. You can also free up a loop device by hand, using ´losetup -d´, see **losetup**( 8 ).

---

