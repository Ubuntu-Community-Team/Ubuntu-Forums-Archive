---
title: "[SOLVED] Need Terminal Command Help"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2008-03-05
I have created a new partition and named it /dev/sda3. It is formatted ext3. I want to use this partition for my backup files. OK. Now I have the backup files on my desktop and I have no idea of how to move the backup files, which are .tgz files, to my new partition. I cannot find the commands that will do it.

Please help me out.

---

### Post by wormser on 2008-03-05
You can use mv to move them or cp to copy them.  It would be easier to just use Nautilus to drag and drop them.

```
mv ~/Desktop/*.tgz /path/to/backup
```

The ~ is a short cut to typing your home folder and user name.

---

### Post by Scarath on 2008-03-05
If you want to browse the new partition/harddrive (I guess you do?) you need to mount the device. Create a new file in /mnt, call it whatever you like .e.g. disk, etc. 

Then go:
```

sudo mount -t ext3 /dev/sda3 /mnt/disk
```

(replace 'disk' with whatever you named the file)

Now you should be able to browse the file as normal, you may need to alter the permissions to write to it, not sure, when I mounted my second HD i had to chown it to be able to do anything with it.  Hope thats what you wanted?

---

### Post by ruy_lopez on 2008-03-05
Create a mountpoint:

```

sudo mkdir /media/backup

```

Mount the partition:
```

sudo mount -t ext3 /dev/sda3 /media/backup

```

Change the ownership of the mountpoint (replace username with your own username):
```

sudo chown username:username /media/backup

```

Add a line to /etc/fstab to mount automatically on boot:
```

/dev/sda3        /media/backup        ext3        defaults        0        0

```

---

### Post by taurus on 2008-03-05
You probably need to change the ownership of that new mount point, the one /dev/sda3 mounted to, so you can write to it without using sudo/gksudo. 

_Assuming_ your login name is **kinda** and it is mounted to /media/sda3, run

```
sudo chown -R **kinda**:**kinda** /media/sda3
mv *filename.tgz* /media/sda3
```

---

### Post by forestpixie on 2008-03-05
I would have thought that you could use cp or mv, assuming the partition is mounted - cd to Desktop

sudo cp backup /media/sda3/

---

### Post by jken146 on 2008-03-05
First, you need to mount the partition somewhere so that it becomes part of your file system.

Create a mount point:
```
sudo mkdir /mnt/storage
```
The name "storage" is just an example -- use whatever you want.

Mount the partition:
```
sudo mount /dev/sda3 /mnt/storage
```


If you want to make the mounting happen every time you boot up, see [http://www.psychocats.net/ubuntu/mountlinux/](http://www.psychocats.net/ubuntu/mountlinux/)

---

### Post by kindafunnylookin on 2008-03-05
> **ruy_lopez said:**
> Create a mountpoint:
[/code]Add a line to /etc/fstab to mount automatically on boot:
```

/dev/sda3        /media/backup        ext3        defaults        0        0

```
Thanks to all three of you, the line added to /ect/fstab is especially good.
Everything works!

---

