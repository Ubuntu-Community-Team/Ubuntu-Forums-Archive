---
title: "mv: preserving times for * : Operation not permitted"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by ninocass on 2006-03-22
I have a FAT32 drive mounted and i have been able to mv files to it before but today i have been getting this error
```

nino@laptop:~$ mv package-frame.html /media/storage/
mv: preserving times for `/media/storage/package-frame.html': Operation not permitted
mv: setting permissions for `/media/storage/package-frame.html': Operation not permitted

```

the file does indeed copy but the error message is shown

I also installed InitNG and Samaba today, i have logged in on the non InitNG kernal thingy and am getting the error could it possibly be samba messing around?

---

### Post by Pragmatist on 2006-03-23
Please run this command after you see the problem still occurs:
```
mount
```
Then post the output here.

Also please give output to these commands:
```
cat /etc/fstab
```
```
ls -ld  /media/storage
```
```
ls -ld  /media
```

---

### Post by ninocass on 2006-03-23
thanks for the reply :)

mount
```

nino@laptop:~$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/sda7 on /media/storage type vfat (rw,iocharset=utf8,umask=000)
/dev/sda2 on /media/windows type ntfs (rw,nls=utf8,umask=0222)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

```

my FStab
```

nino@laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda7       /media/storage  vfat    iocharset=utf8,umask=000   0       0
/dev/sda2       /media/windows  ntfs    nls=utf8,umask=0222 0       0

```

ls -d /media/storage
```

drwxrwxrwx  13 root root 8192 2006-03-23 07:54 /media/storage

```

ls -ld /media/
```

drwxr-xr-x  6 root root 4096 2006-03-23 03:47 /media

```

I was algo getting a wierd problem where when i plugged in my USB Pen drive i lost write to the /media/storage drive and could only read

Thanks

---

### Post by meborc on 2006-03-23
hmm... how about **sudo mv**?

---

### Post by ninocass on 2006-03-23
nope

surely i shouldnt need sudo, still getting an error
```

nino@laptop:~$ sudo mv test /media/storage/
Password:
mv: failed to preserve ownership for `/media/storage/test': Operation not permitted

```

---

### Post by dcstar on 2006-03-23
[QUOTE=ninocass]nope

surely i shouldnt need sudo, still getting an error
```

nino@laptop:~$ sudo mv test /media/storage/
Password:
mv: failed to preserve ownership for `/media/storage/test': Operation not permitted

```[/QUOTE]
Just for a test, try moving a file with an initial capital, like "Test", and see if it still occurs.

---

### Post by ninocass on 2006-03-23
tried it with a capital and still got the error i notcied something else tho

i create a file called temp in the ~ folder and do ls -l and i get

```

-rw-r--r--   1  nino  nino    7  2006-03-23-13:58 test

```

but when i move it to the storage drive:

```

mv test /mesdia/storage

```

then when i do a ls -l in the /media/storage i get

```

-rwxrwxrwx 1 root root     7    2006-03-23-13:59 test

```

is there anything in this?

---

### Post by mcduck on 2006-03-23
[QUOTE=ninocass]```

mv: setting permissions for `/media/storage/package-frame.html': Operation not permitted

```
[/QUOTE]
Well, FAT32 doesn't support Linux file permissions, so mv can't set permissions for the new file :) I suppose it's safe to ignore that error message..

---

### Post by ninocass on 2006-03-23
makes sense, was just concerned that it never appeared before thought id br0ked  something lol

thanks

---

### Post by Pragmatist on 2006-03-23
> Originally Posted by: **mcduck**
[QUOTE]**Originally Posted by ninocass**
```
*mv: setting permissions for `/media/storage/package-frame.html': Operation not permitted*
```
*Well, FAT32 doesn't support Linux file permissions, so mv can't set permissions for the new file I suppose it's safe to ignore that error message..*

The reason your getting all the permission bits set is because of this:
/dev/sda7       /media/storage  vfat    iocharset=utf8,**umask=000**   0       0
umask is a way of defining the default permissions of new files.  The way it works is, the umask value is subtracted from 777 (which means all bits set--all permissions given).  The typical umask would be 022 which leads to:
777-022 = 755 which is -rwxr-xr-x  Another way to look at it is:
r=4 w=2 x=1  So if your subtracting a 2, your removing write access.

I noticed this umask of 000 and I was wondering why it is there. I'm not sure yet that this is your main problem, however.

---

### Post by ninocass on 2006-03-23
so if i want to keep write access i should leave the umask=000 then?

---

### Post by Pragmatist on 2006-03-23
> so if i want to keep write access i should leave the umask=000 then?
As I said before, I'm not really sure that the permissions are the problem. To answer your question though, if you own the file, and you want to be able to read and write and you want everybody else to be able to just read it, then you use 644 permission (you get 6 which is 4+2 where 4 is for read and 2 is for write; the group the file belongs to and everybody else just get read = 4 permissions.)  If you want to be able to read/write/and execute, and you want everybody else to be able to read and execute, you use 755 permissions.  Notice, I just added 111 to 644 = 755, because 1 = execute, so I just added execute to owner, group, and other.

So, the answer is...it depends what kind of file it is and what security you want to implement.  If you own the file and it isn't executable, then 644 is usually good (chmod 644 filename)  If it is executable, and you own the file, then 755 is usually good (chmod 755 filename).  After that, it is just generalities and you need to know your situation.

At some point you might consider changing the umask to 022 since having it at 000 is somewhat of a security risk, at least to your personal files.  With the umask at 000, every new file that is created on that partition will, by default, have full permissions for reading, writing, and executing, for anybody.  You can read more about umask with:
```
man umask
```

I'm curious about two things.
1.) What happens if you use **cp** rather than **mv** ?
2.) What happens if you use **cp -p**

So try copying some files over using:
```
cp filename
```
And
```
cp -p filename
```
and give us the results.

---

### Post by ninocass on 2006-03-24
okay when i did 

```

cp filename destination

```

the file copies okay with no errors

when i do
```

cp -p filename destination

```

i get:
```

cp: preserving times for `/media/storage/Kismet-Mar-23-2006-1.xml': Operation not permitted

```

---

### Post by Pragmatist on 2006-03-24
Try this:
Backup your /etc/fstab file:
```
sudo cp /etc/fstab /etc/fstab.BAK
```
Now edit /etc/fstab:
```
sudo gedit /etc/fstab
```
Now change this line:
*/dev/sda7       /media/storage  vfat    iocharset=utf8,umask=000   0       0*
To this line:
**/dev/sda7       /media/storage  vfat    iocharset=utf8,uid=1000, gid=1000,umask=000   0       0**

NOTE: This assumes that your user id and group id are 1000.  To make sure, type this:

```
cat /etc/passwd |grep username
```
So if your username is nino, do this:
```
cat /etc/passwd |grep nino
```
You'll get something like this:
nino: x:1000:1000:whatever:/home/nino:/bin/bash
If those 2 numbers aren't 1000 and 1000, then set uid=the first number and gid=the second number.

Now try moving some file and tell us what happens.  If the same thing happens as before, edit the file again and make one more change: remove the **iocharset=utf8** option.  Then try again.  Also, when picking a file to mv try a filename that has 8 or less characters (make them all letters and numbers for simplicity. If you use numbers, don't make the first character a number.).  You can just open an editor and make a file called "test" and write "This is a test" and save the file.  Then copy the file if you want and and write "This is a second test" and save it as "test2" etc...etc...

---

### Post by ninocass on 2006-03-24
negative on both of those :( still recieving the same error

---

### Post by Pragmatist on 2006-03-24
1. What kind (firewire, usb, scsi, etc...), make (brand name), and model device are you mounting to /media/storage?

2. Do you get the message when you move files **within** /media/storage, or only when you move them from somewhere else (like your hard drive) to /media/storage?

3. Why were you moving files to /media/storage rather than copying them?  Yeah it takes one more step to go remove the extra copies from the original location, but this is considered standard best practice anyway (to avoid mistakes).

---

### Post by ninocass on 2006-03-24
basically my 40 GB HDD is split up into

10GB EXT3 for linux

10GB FAT32 to act as storage space for files that BOTH windows and linux can use java programming etc etc

20GB for windows [i still cant live without the damn thing lol]

i can MV **within** /media/storage/ wihtout getting the error but as ive mentioned as soon as anything goes into /media/storage it says its owned by root!

Normallly i wouldnt mind but i have never got this error before, and i want to know whats changed to make it show itself

Nino

---

### Post by Pragmatist on 2006-03-24
> Originally Posted by: **ninocass**
10GB **FAT32** to act as storage space for files that BOTH windows and linux can use java programming etc etc

Can't you change the partition type to vfat?  Unlike FAT, vfat preserves permissions, modificatino times, etc...

---

