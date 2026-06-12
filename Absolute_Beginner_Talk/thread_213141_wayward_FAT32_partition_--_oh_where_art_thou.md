---
title: "wayward FAT32 partition -- oh where art thou?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Susan.Desanco on 2006-07-10
[SIZE=2][COLOR=Black]I've tried to study up on this topic so that I could get somewhere on my own.  Having learned a lot, I still don't know what to do...

I'd like to locate my FAT32 partition while in Ubuntu OS, so that I can use it!

Note: Info below comes from two distinct sources!  Read carefully.

When I use the GParted LiveCD, I see my fat32 partition as this:
/dev/sda6   fat32   not mounted
[/COLOR][/SIZE]
_[SIZE=5][COLOR=Black]**HOWEVER...**[/COLOR][/SIZE]_[SIZE=5][COLOR=Black][SIZE=2]
When I am in Ubuntu OS and I go to: System-->Admin-->System Monitor--> Devices, I see it like this:
/dev/sda6     vfat(fat32)    /windows

Now, it is my understanding that since I see ' /windows' listed as the Directory for this device when I am in Ubuntu, it would mean that, in fact, Ubuntu sees the device as mounted.

Great!  If I am correct, I don't need to mount that partition.  Yes?  Right?

If it is in fact mounted, then where do I find the bugger so that I can drop files into it?

Thanks in advance.

[/SIZE][/COLOR][/SIZE]

---

### Post by nalmeth on 2006-07-10
Does it appear in the places menu?

Physically, I think it should be mounted in /media/windows or something similar.

---

### Post by o_fortuna on 2006-07-10
The "/windows" at the end of the line is where it's mounted. So, click on the Places menu (at the top) and then Computer, and look for a folder named "windows."

If you still can't find it, go into the System-->Administration menu and click "Disks." Select the "Partitions" tab and then select the device. There will be a "Browse" button if it is mounted. You can also change the place where it is mounted ("Access Path").

---

### Post by Susan.Desanco on 2006-07-10
Thank you!  I found it where you described, and checked properties to confirm the volume size info.  Sure enough -- that's it -- my missing 27.9 GB fat32 partition.

Thanks again for the help!!

---

