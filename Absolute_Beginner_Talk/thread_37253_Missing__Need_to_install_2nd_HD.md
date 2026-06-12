---
title: "Missing / Need to install 2nd HD"
date: 2005-05-26
forum: Absolute Beginner Talk
---

### Post by F1_error on 2005-05-26
I just installed Ubuntu yesterday, I'm trying to figure out how to get it to recognize my other hard drive. Not a partition, another hard drive. It's in my bios. And I've tried following the wiki "installing a new hard drive" article. I don't get beyond the first step

```
user@myubuntubox:~ $ sudo dmesg|less
```

My hard drive is not in the list, infact as far as I can tell, nothing is. I get; 

```
drivers/usb/input/hid-core.c: input irq status -84 received
```

for pages and pages. 

So, can anyone tell me how to find/fix/install my second hard drive?

---

### Post by Kyral on 2005-05-26
try giving the output of "sudo fdisk -l"

This will list all the partition tables that the system can see.

---

### Post by F1_error on 2005-05-26
Ok, I did that, and now I know it's there. And I think I see the problem. In the system column it says "W95 FAT32 (LBA)" so it looks like it didn't get formatted for Linux when I did my install. The HD is blank, so no worries there. 
I guess the next question is how do I format the HD for Linux, and then will it be recognized by Ubuntu?

---

### Post by Kyral on 2005-05-26
Quite easy

In its entry in /etc/fstab, just put vfat under its FS type;

Heck here is the line for my second HD (also FAT32)

```
/dev/sda1       /media/anime    vfat    rw,user,uid=1000,gid=1000,umask=0000 0 0        0       0
``` 

Just replace "sda1" with your partition name and "/media/anime" with where you want to mount it (make sure you mkdir the mountpoint first)

---

### Post by F1_error on 2005-05-26
errm...how do I do that? 
I've fiddled a bit in the command line/terminal but I'm not quite fluent enough in command line code to figure out what you mean. 
I'm very new to this, like yesterday new. :)

---

### Post by Kyral on 2005-05-26
Open a terminal and

```
sudo gedit /etc/fstab
```

Then paste that line in at the bottom and save it

And of course

```
sudo mkdir /media/<insert what you want to call your mountpoint here>
```

then

```
mount /media/<what your called your mountpoint>
```

---

### Post by F1_error on 2005-05-26
That worked great, thanks a lot! 

Now I just have to figure out how to transfer several gigs of music off my Mac without having to burn a hojillion CDs  :smile:

---

### Post by Kyral on 2005-05-26
Crossover cable? (Its an Ethernet Cable that is designed to hook two computers together for a direct connection)

But don't ask me how to set it up :P

---

