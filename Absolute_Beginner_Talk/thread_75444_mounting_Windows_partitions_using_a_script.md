---
title: "mounting Windows partitions using a script"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2005-10-13
I am trying to follow this guide [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28partition%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28partition%29)

I think I have it up until this point

chmod u+x winmac_fstab
sudo ./winmac_fstab

should I be hitting enter after the first line? when I do it says chmod invalid mode string: u+x

if i dont hit enter between the lines it says chmod cannot access 'sudo' : no such file or directory. 

I dont have any idea what I'm doing as you can tell. sorry if this question has been covered.

---

### Post by aysiu on 2005-10-13
I went to that link, and it made no sense to me. I use this instead, and it's always worked for me:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by onesojourner on 2005-10-13
ok I have my windows partition mounted and I can see it. I have about 3 more partitions to go. is there a way that I can see the contents or size with the hda? name?

---

### Post by aysiu on 2005-10-13
If you type ```
sudo fdisk -l
``` in a terminal, it'll list all your partitions (mounted and unmounted) and what their dev names are (/dev/hda1, /dev/hda2, etc.). It'll also say what filesystem type they are (NTFS, FAT16, etc.).

---

### Post by onesojourner on 2005-10-14
ok can some one explain this to me (see screenshot)? I have tried using hda2 hda3 hda4 sda4... it wont except any of them. it says it does not exist. I have a 160 gig drive that I am realy trying to find. the others arent that important. I just dont understand what all the numbers are on this.

---

### Post by Muhammad on 2005-10-14
Don't forget to create a different folder for each partition.

---

### Post by onesojourner on 2005-10-14
I did that. I just dont know what the names of my drives are what drive my 160 gig is.

---

### Post by aysiu on 2005-10-14
[QUOTE=onesojourner]I did that. I just dont know what the names of my drives are what drive my 160 gig is.[/QUOTE] Please see post #4.

---

### Post by onesojourner on 2005-10-14
[QUOTE=aysiu]Please see post #4.[/QUOTE]

I have seen post 4. I posted a screen shot. I would like to know if this
/dev/sda4   ?           1     3626348  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(3626347, 7, 42)
Partition 4 does not end on cylinder boundary.

is this giving me a drive size? if it is where?

---

