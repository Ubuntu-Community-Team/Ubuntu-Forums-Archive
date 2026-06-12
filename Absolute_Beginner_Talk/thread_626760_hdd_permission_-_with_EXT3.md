---
title: "hdd permission - with EXT3????"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by ~&#730;JaZ&#730;~ on 2007-11-29
Hi!

I have an extra HDD 250GB, I formated it with gparted and made it ext3 but i still dont have permission to write or do anything useful with it..:(, I saw a lot of simillar problems on the forum but all of them were conected with NTFS file system so i gues there is no use for installing drivers for reading NTFS. Also this is my first time doing this in linux...so i hope i did everything ok...any help pls...
Oh...every time i restart the machine i have to enter the root password just to see the HDD and it contains a file lost+found also i am unable to open it,,,

TNX
Z.

---

### Post by jcsteele on 2007-11-29
Without knowing the mount point of your hdd off hand, I cant be too exact with the commands...however you will want todo something like below.


Open up a terminal (Applications -> Accessories -> Terminal) and you will see something like below:

$

Now these are the commands you will need to use (again, you will need to substitute your particular mount point and username)

$ chown -R YOURUSERNAME.YOURUSERNAME /YOUR/HDD/MOUNT/POINT
$ chmod -R 755 /YOUR/HDD/MOUNT/POINT

to reiterate again, you will need to subsitute "/YOUR/HDD/MOUNT/POINT" with the actual mount point ofyour hdd, and "YOURUSERNAME.YOURUSERNAME" needs to be your username on the system (ex.  for me it would jcsteele.jcsteele)

For more information, you can google "linux permissions" which turns up lots of resources, the top one being:

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-navigating-ownership.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-navigating-ownership.html)


Hope this helps!

//jcs

---

### Post by ~&#730;JaZ&#730;~ on 2007-11-29
Hi!

hm...how can i check my mount point...the thing is that i mada two partitions, and when i right click on the HDD icon the mount point is empty...i am probebly doing it wrong....
sorry for being so uneducated but i am still learning...tnx...:-s
z.

---

### Post by ~&#730;JaZ&#730;~ on 2007-11-29
btw this is my output for 

sudo nano -w /etc/fstab

If its any help...

---

