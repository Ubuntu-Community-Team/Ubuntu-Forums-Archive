---
title: "Mounting/UnMounting???"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by kcgreg on 2006-09-23
Hey Guys - what exactly is mounting a device?

Does this mean to read from it or it is something external that is added to the computer as hardware???:confused: :confused: :confused: 

Thanks for the help.

Kcgreg

---

### Post by someonedumb on 2006-09-23
I'll reply with an example:

My computer has a windows HD (fat32) and a linux HD. On my Linux desktop I have an empty folder called "Windows". I can gain access to my fat32 HD through the "Windows" folder with this command - "mounnt -t vfat /dev/hdc1 /home/someone/Desktop/Windows"

Now, when I open the "Windows" folder I am actually looking at my fat32 HD.

---

### Post by empcrono on 2006-09-23
> **someonedumb said:**
> I'll reply with an example:

My computer has a windows HD (fat32) and a linux HD. On my Linux desktop I have an empty folder called "Windows". I can gain access to my fat32 HD through the "Windows" folder with this command - "mounnt -t vfat /dev/hdc1 /home/someone/Desktop/Windows"

Now, when I open the "Windows" folder I am actually looking at my fat32 HD.

yeah that is a good question how do u unmount somthing

---

### Post by maaronB on 2006-09-23
unmount /dev/hdc1

---

### Post by empcrono on 2006-09-23
> **maaronB said:**
> unmount /dev/hdc1

does that apply to iso as well because when i try to do the opssite of mounting a iso but change mount to unmount it says unkown and stuff

---

### Post by bodhi.zazen on 2006-09-23
> **empcrono said:**
> yeah that is a good question how do u unmount somthing

sudo umount <mount_point>

To continue with the above example:```
sudo umount /home/someone/Desktop/Windows
```

Comments:[list=number][*]You will need to use sudo unless you edit fstab (/etc/fstab)
[*]Mount in /media if you want the mounted drive to appear on your desktop.
[*]Otherwise mount in /mnt (keeps it organized)
[*]Use a link in your home directory[/list]

To continue with the example:

```
sudo mkdir /mnt/Windows
ln -s /mnt/Windows ~/Windows
sudo mount -t vfat /dev/hdc1
```

Assuming /dev/hdc1 is a FAT partition. NTFS is different.

If you want media, change /mnt/Windows to /media/Windows

For read/write access:```
sudo mounnt -t vfat /dev/hdc1 -o rw
```

---

### Post by bodhi.zazen on 2006-09-23
> **maaronB said:**
> unmount /dev/hdc1

> **empcrono said:**
> does that apply to iso as well because when i try to do the opssite of mounting a iso but change mount to unmount it says unkown and stuff

The command is **umount** _Not unmount_ (no n)

---

### Post by empcrono on 2006-09-23
> **bodhi.zazen said:**
> The command is **umount** _Not unmount_ (no n)

LMAO o >< ic thanks man  (typo's get the best of me some times)

---

### Post by maaronB on 2006-09-23
> **kcgreg said:**
> Hey Guys - what exactly is mounting a device?

Does this mean to read from it or it is something external that is added to the computer as hardware???:confused: :confused: :confused: 

Thanks for the help.

Kcgreg

Quick anwser: makes it possible for linux to read from hardware


Longer anwser:
The linux kernel likes to "think" of everything as a file.  So for it to read from hardware it has to "believe" that the hardware is just another file in its filesystem.  So when you plug in a USB flash drive or CDROM it has to be given a file location of where to read that USB or CDROM from.  So when your computer mounts a CDROM it is given a file location that Linux uses to read and write from.

As someone. pointed out you can partion your harddrive and then mount different portions at different places in your filesystem.  He mounted his Windows portion inside his home directory conviently providing easy access to his Windows files.

You can also unmount your hardware or partions.  You need to do this with flashdrives espically because sometimes the information that you think is being saved to your physical disk is actually just being placed in a buffer to be written to that pretend file.  When you unmount it everything gets pushed out of memory and into the actual disk.

---

### Post by maaronB on 2006-09-23
> **bodhi.zazen said:**
> The command is **umount** _Not unmount_ (no n)

thanks mymistake

---

### Post by kcgreg on 2006-09-23
Wow - thanks guys!!! I didn't think there was so much with mounting & unmounting - but the info was great. Much appreciated!!![-o< :D

---

### Post by bodhi.zazen on 2006-09-23
> **maaronB said:**
> Quick anwser: makes it possible for linux to read from hardware


Longer anwser:
The linux kernel likes to "think" of everything as a file.  So for it to read from hardware it has to "believe" that the hardware is just another file in its filesystem.  So when you plug in a USB flash drive or CDROM it has to be given a file location of where to read that USB or CDROM from.  So when your computer mounts a CDROM it is given a file location that Linux uses to read and write from.

As someone. pointed out you can partion your harddrive and then mount different portions at different places in your filesystem.  He mounted his Windows portion inside his home directory conviently providing easy access to his Windows files.

You can also unmount your hardware or partions.  You need to do this with flashdrives espically because sometimes the information that you think is being saved to your physical disk is actually just being placed in a buffer to be written to that pretend file.  When you unmount it everything gets pushed out of memory and into the actual disk.

LOL :lol:
This is partially true. You should ALWAYS unmount (err... umount that is) a mobile drive, but...

use the sync option, either with mount or in fstab. This eliminates the problem and you will write the data immediately, without delay.

```
sudo mount /mnt/mobile/ -o sync,rw,uid=1000
```

You must specify a user by user ID #. 1000 is the first user in Uubntu (with admin rights).

---

### Post by wildseven on 2006-09-23
> **maaronB said:**
> unmount /dev/hdc1

i am under the impression this is incorrect. shouldnt u unmount the mount point?

wouldnt the command be:
```
sudo umount /home/whatverTheMountPointWas
```

---

### Post by bodhi.zazen on 2006-09-23
Look up....

The command umount is the correct syntax.

umount <mount_point> OR umount <device> BOTH WORK

umount /dev/hdc1 is fine.

---

### Post by wildseven on 2006-09-23
ok, thank you for clearing that ^^

---

### Post by bodhi.zazen on 2006-09-23
Linux usually has AT LEAST 2 ways of doing something. :)

I have found more then 2 ways to break Ubuntu. #-o

---

### Post by wildseven on 2006-09-23
hahaha

---

### Post by maaronB on 2006-09-23
> **wildseven said:**
> i am under the impression this is incorrect. shouldnt u unmount the mount point?

wouldnt the command be:
```
sudo umount /home/whatverTheMountPointWas
```

Yeah, my bad again.  I really don't know anything about the subject just tried to summarize out of a book that I am reading.  Looks like I really screwed that part up.

---

### Post by wildseven on 2006-09-23
it's cool. i didnt know u could umount a device lol. we are all here to learn mate!

---

### Post by Ciego on 2006-09-23
I am getting an error that says mount point does not exist.  what does this meam? Any suggestions?

---

### Post by bodhi.zazen on 2006-09-23
> **Ciego said:**
> I am getting an error that says mount point does not exist.  what does this meam? Any suggestions?

What are  yo trying to mount?

sudo fdisk -l to list partitions (that is a small "L").

---

### Post by Ciego on 2006-09-23
I was trying to mount my CD-RW.  I figured out that I had to create the directory first.  I still have the problem that the CD-RW drive cannot detect any media but I don't think that really falls under this topic.  I have another thread going regarding this problem 

[http://ubuntuforums.org/showthread.php?t=263761](http://ubuntuforums.org/showthread.php?t=263761)

---

