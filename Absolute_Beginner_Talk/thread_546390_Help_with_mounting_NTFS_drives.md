---
title: "Help with mounting NTFS drives"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by DAE_JA_VOO on 2007-09-08
Hi there everyone.

I tried to follow [this](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html) guide, but i'm not succeeding. As soon as i RUN the ntfs configuration tool, this is the first dialog that i get:

[IMG]http://i29.photobucket.com/albums/c267/DAE_JA_VOO/more2/ntfsconfig1.png[/IMG]


And if i do anything after that, it gives me errors. As far as i understand, i should get all my partitions first. Any help?

Thanks guys :)

---

### Post by Linux_Man on 2007-09-08
Is it a partition or a drive? External or Internal? If it is a partion go to places then to computer then go to the XX.X GB volume and just right click and it should mount it, it does just fine for me (Ubuntu 7.04) Some external drives should also appear there too.

---

### Post by DAE_JA_VOO on 2007-09-08
> **Linux_Man said:**
> Is it a partition or a drive? External or Internal? If it is a partion go to places then to computer then go to the XX.X GB volume and just right click and it should mount it, it does just fine for me (Ubuntu 7.04) Some external drives should also appear there too.

It's a partition on an internal drive. The drive is mounted already, but i need to be able to WRITE to it as well...

---

### Post by Beggar on 2007-09-08
Then you need to click the button that says "enable write support for internal device", its displayed quite prominantly in the screen shot you showed us.

---

### Post by DAE_JA_VOO on 2007-09-09
I might be a linux n00b, but i'm not illeterate ;)

As i said in my first post, anything i do from that dialog gives me an error, like this:

[IMG]http://i29.photobucket.com/albums/c267/DAE_JA_VOO/more2/error.png[/IMG]


I get one of those for each of my NTFS partitions/disks.

---

### Post by saisho on 2007-09-09
I would just followup the instructions on the screenshot you posted. If you got a dual boot system, boot into Windows, access the drives (just open a file) and then shut down properly.

---

### Post by vanadium on 2007-09-09
Indeed, you are not illiterate ;) and the instructions are quite clear. There is fortunately a solution given not requiring Windows. Since you indeed posted this in the newbie forum, I'll elaborate on that:

"run ntfsfix version 1.13.1 unless you have Vista"

This means that Microsoft changed ntfs specifications again with Vista, and the open source community did not yet catch up with these changes (they are not being published, they have to be found by trial-and-error, reverse engeneering, imangine that!). Thus, if you have Vista, your only option is to repair it in Windows Vista. If you have another version of Windows, you can stay in Linux:

Open a command terminal (Applications - Accessories - Terminal)
First, you will need to now the name of your Vista partition: type

sudo fdisk -l

This will show all partitions that are around. Under "System" you see which one is ntfs, in the first column, you see the name of the partition, something like /dev/sda5 (I'll take that as the example)

Now run ntfsfix:

ntfsfix /dev/sda5

Now "reload" /etc/fstab, the file that regulates where and how all drives are to be mounted.

sudo mount -a

Now try to run ntfsconfig again: chances are it will work all right, without rebooting!

---

### Post by Wiebelhaus on 2007-09-09
this is very simple , basically all this means is that the NTFS log file is Unclean , you need to shut down the windows partition properly before trying to access it , the man that wrote ntfs-3g did this for a very good reason.

---

