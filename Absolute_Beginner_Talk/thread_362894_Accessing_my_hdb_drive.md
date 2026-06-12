---
title: "Accessing my hdb drive"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by geovino on 2007-02-16
How do you access another drive on your network besides the Winxp one? I was given instructions on accessing and seeing my Winxp (hda1) in Network Servers, but nobody knows how to add another partition to Network Servers so I can see my PCLOS (hdb) drive?

Out of all the intelligent people in this forum, someone should know how to do that? 
Give me a clue. :)

---

### Post by Tomosaur on 2007-02-16
I'm a little confused. Are you asking how to connect to completely different machines, or to mount a hard drive on your **current** machine? If the former -sorry, I can't help you. I've never needed to do that in Ubuntu (yet). I generally just use SSH and sftp for that kind of thing.

If the latter: Open up a terminal, and type the following commands:
```

mkdir ~/Desktop/my_hd
sudo mount /dev/hda1 ~/Desktop/my_hd

```

This should create a folder on your desktop through which you can access your XP hard drive :)

---

### Post by geovino on 2007-02-16
This PC has:
hda1 - Winxp
hda2 - Ubuntu
hdb - PCLOS

I have added to my fstab file:
/dev/hda1 /mnt/win ntfs nls=iso8859-1,ro,unmask=0 0 0

once that was added, I can now see my winxp files in Network Servers.

I just want to be able to do the same to access my PCLOS in the hdb drive.
Would it be something similar?

---

### Post by geovino on 2007-02-17
> **Tomosaur said:**
> I'm a little confused. Are you asking how to connect to completely different machines, or to mount a hard drive on your **current** machine? If the former -sorry, I can't help you. I've never needed to do that in Ubuntu (yet). I generally just use SSH and sftp for that kind of thing.

If the latter: Open up a terminal, and type the following commands:
```

mkdir ~/Desktop/my_hd
sudo mount /dev/hda1 ~/Desktop/my_hd

```

This should create a folder on your desktop through which you can access your XP hard drive :)

OK, I did that but it has a lock on it. How do I give it permission to unlock?

---

### Post by geovino on 2007-02-17
I tried to give it share properties with smb, but it still doesn't open. How do I get rid of it if I don't want it? It can't go to the trash. Can I unmount it?

Here's what the icon looks like:

---

### Post by psycosmyth on 2007-02-17
I came over to give a bump.

---

### Post by geovino on 2007-02-17
I need some assistance to solve this problem?

Someone out there should know how to correct this problem.

How do I undo this?

mkdir ~/Desktop/my_hd
sudo mount /dev/hda1 ~/Desktop/my_hd

So I can get that icon off the desktop!

Thank you.

---

### Post by geovino on 2007-02-18
After rebooting and going into Ubuntu, the folder for hda1 with the lock is now unlocked!
I was able to delete it. Very strange.

One day I'll learn how to access all drives on this PC.

---

### Post by chggr on 2007-02-18
> **geovino said:**
> I need some assistance to solve this problem?

Someone out there should know how to correct this problem.

How do I undo this?

mkdir ~/Desktop/my_hd
sudo mount /dev/hda1 ~/Desktop/my_hd

So I can get that icon off the desktop!

Thank you.

You could alternatively:

sudo umount ~/Desktop/my_hd
sudo rmdir ~/Desktop/my_hd

The first command unmounts the device and the second deletes the folder.
The reason why you couldn't delete the folder was that the device was mounted on it and you should unmount it first.

---

### Post by chggr on 2007-02-18
> **geovino said:**
> OK, I did that but it has a lock on it. How do I give it permission to unlock?

The folder was locked because only the root user was able to see inside it. In order to mount a NTFS partion or hard disk, you should edit the /etc/fstab file and add the following line:

/dev/hdb       /media/MyDrive   ntfs    rw,user,auto,umask=000   0       0

where /media/MyDrive is a file created by you, using this command

sudo mkdir /media/MyDrive

The directive "umask=000" gives read permissions to you. Remember that you cannot have write permissions because Linux does not support writing on ntfs. The directive "auto" mounts the drive every time your computer boots up. If you want to find more information concerning these directives, type "man mount" into a console.

---

### Post by geovino on 2007-02-18
Thanks for the info. I'll keep this for future reference.

I have this line in my fstab file:
/dev/hda1   /mnt/win   ntfs   nls=utf8,umask=0222   0   0

With that I can see the Winxp in Network Servers. That  works great. I just wanted to be able to access another hd which is PCLOS on hdb. I thought someone could show me how to write that line for the fstab file so I could see my files in PCLOS (another Linux distro)

But it is strange that the one folder for hda1 (winxp) that was on the desktop, lost its lock icon and I was able to delete it. How can that happen?

Overall I have to say that I'm enjoying Ubuntu very much after having troubles with it in the past.

---

### Post by spd106 on 2007-02-18
For easy management of partitions may I recommend installing gparted. It's the same tool used by Edgy's Desktop cd during installation.

Remember that you mount partitions rather than disks, i.e. hdb1 rather than hdb.

---

### Post by geovino on 2007-02-18
So I would mount the hdb hard drive as the hdb1  partition?
So what would the line be in fstab? or would I do it differently?


I'll install Gparted for future use. Thanks.

---

