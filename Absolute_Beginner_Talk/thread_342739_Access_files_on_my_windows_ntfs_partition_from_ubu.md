---
title: "Access files on my windows ntfs partition from ubuntu"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by egypharaoh on 2007-01-20
Ok I need to access files on my C drive in my windows partition from Ubuntu.  I am currently running Ubuntu 6.10 and I have no idea how to do this.

Thanks in advance,
Joe

---

### Post by taurus on 2007-01-20
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by MrWally on 2007-02-13
Sorry for the major thread bumpage.

I was wondering the same thing, and when I used tut you linked to taurus, it didn't work for me. When I open the fstab I don't even see my hda1 (windows) partition thus there is nothing for me to edit. Nor can I see my windows installation in my filesystem.

I should add that I have windows installed on a completely separate drive, not just another partition, would this make it more complicated?

---

### Post by Bachstelze on 2007-02-13
It shouldn't matter. Another partition on the same drive or another partition on another drive work the same. What exactly is it that is not working (i.e. what command do you run and what do you get instead of what you expected) ?

---

### Post by MrWally on 2007-02-13
As I said, when I try to edit the fstab ( sudo nano /etc/fstab ) and it opens the file it doesn't show my windows partition whatsoever. Therefore I can't change it and can't do what the tutorial says.

---

### Post by bodhi.zazen on 2007-02-13
> **MrWally said:**
> Sorry for the major thread bumpage.

I was wondering the same thing, and when I used tut you linked to taurus, it didn't work for me. When I open the fstab I don't even see my hda1 (windows) partition thus there is nothing for me to edit. Nor can I see my windows installation in my filesystem.

How exactly did you edit fstab ?

You will get an empty document if you do not sudo (gksudo for gedit) or the path is not correct.

Use: ```
gksudo gedit /etc/fstab
```

> I should add that I have windows installed on a completely separate drive, not just another partition, would this make it more complicated?

No. To list all your partitions, if that helps, :```
sudo fdisk -l
```

---

### Post by wh0rd on 2007-02-13
> **MrWally said:**
> As I said, when I try to edit the fstab ( sudo nano /etc/fstab ) and it opens the file it doesn't show my windows partition whatsoever. Therefore I can't change it and can't do what the tutorial says.

What do you get when you type in:
```

sudo fdisk -l
```

---

### Post by MrWally on 2007-02-13
> **wh0rd said:**
> What do you get when you type in:
```

sudo fdisk -l
```

i get ```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5099    40957686   83  Linux
/dev/hdb2            5100       14542    75850897+  83  Linux
/dev/hdb3           14543       14593      409657+  82  Linux swap / Solaris
david@david:~$ 

```

As you can see my NTFS windows drive (the 250 gig one) is hda1.

However, when I follow the tutorial and go to edit the fstab, there is no hda1 there.

---

### Post by CC_machine on 2007-02-13
i have the same problems with ubuntu - it doesnt recognize my NTFS partitions, or any USB UMS devices i have either!

i would suggest you try knoppix - worked for me :)

---

### Post by MrWally on 2007-02-13
> **CC_machine said:**
> i have the same problems with ubuntu - it doesnt recognize my NTFS partitions, or any USB UMS devices i have either!

i would suggest you try knoppix - worked for me :)


I'd prefer to stick with Ubuntu, though, because I know it's possible

---

### Post by bodhi.zazen on 2007-02-13
Well, to mount the ntfs partition:

```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows
```

To edit fstab : ```
gksudo gedit /etc/fstab
```

You need to add a line for the partition:

Try this :> /dev/hda1 /media/windows ntfs defaults 0 0

After adding this entry to fstab :

```
sudo mount -a
```

---

### Post by MrWally on 2007-02-14
Thanks, I just did everything you said and it made the windows folder in my media directory, but I do not have the permissions to access it because I am not in root. I know this is a really stupid question (It's been a long time since I've done anything with ubuntu), how do I access the files to see if it worked? And more importantly, how can I change it from being root?

The only way I know of using a root command is to type sudo in the terminal. But I'm trying to access a file through the file browser.

---

### Post by bodhi.zazen on 2007-02-14
You can access the files, as root, with nautilus

In a terminal, ```
gksudo nautilus
```

From there it depends a little. Do you need read only (ro) or read-write access ?

for read write access see : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

For ro, use options in mount and fstab

sudo umount /media/windows

sudo mount /dev/hda1 /media/windows -o uid=1000,gid=100

and add these options in fstab :

/dev/hda1 /media/windows ntfs auto,uid=1000,gid=100 0 0

---

### Post by MrWally on 2007-02-14
Oh man thanks so much! I've been trying to get this working through fuse and ntfs-3g for ages now, but nothing.

My last question, is now that I can access the folder. I went to the permissions properties and tried changing the owner from root to my user name and it won't let me. Nor can I create a launch icon to the file for simplicities sake. Any reason why?


EDIT: I should really mess with things before I ask questions. It's all working wonderfully now. Thanks soo much!

---

### Post by bodhi.zazen on 2007-02-14
No fair answering your own question while I'm typing my post :)

---

