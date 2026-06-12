---
title: "using external hard drive properly..."
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by lastelement0 on 2007-08-24
i currently am running a dual boot with windows xp and ubuntu studio on my dell e1505 laptop. i have an external drive which i partitioned so it has a ntfs partition to work with windows and a ext3 partition to work in linux. im not sure if i set it up correctly so if you can guide me in setting up the external properly so i can use the external to store software and other files correctly that would be helpful.

id like to have an easier method to access it via terminal as well, not having to dwell deep into the filesystem into media and such. 

any help is appreciated.

---

### Post by mlentink on 2007-08-24
Personally, I would have made only one partition, and format that as VFAT. Then both Windows and Ubuntu would have had equal access to it.  That&#347; what I did with mine and that works fine.

I am afraid I cannot really help you with easier access in terminal. In Unix, and therefore in Ubuntu, everything is a file, even directories, and /media happens to be the place where those external disks are stored. Perhaps you could set up a symlink to it, but right now I'm not sure, have to look it up.

Edit:
It should be possible to use links to access that external disk.

See e.g. [http://unixhelp.ed.ac.uk/tasks/links2.2.html](http://unixhelp.ed.ac.uk/tasks/links2.2.html) or [http://burks.bton.ac.uk/burks/linux/rute/node15.htm](http://burks.bton.ac.uk/burks/linux/rute/node15.htm)

---

### Post by igknighted on 2007-08-24
Why not use ntfs-3g... Ubuntu can use it to read/write to ntfs perfectly.  Or you can use the fs-driver in Windows to read/write just fine to ext3.  These are better options than using vfat/fat32.

It should automount on plugin.  Perhaps because you changed the partition scheme?  Every external drive I have ever used has been recognized and I've never touched a terminal for it.

---

### Post by lastelement0 on 2007-08-24
well i have it already set up and its there i just dont know how i should have the filesystem set up because right now its set up as if it were another root. i just don't know how i would write to it and be able to install linux programs on it and have it run.

---

### Post by mlentink on 2007-08-24
> **igknighted said:**
> These are better options than using vfat/fat32.
Probably completely off-topic, but why do you consider vFAT to be inferior? It is natively supported by both OSs without additional software or drivers, and works fine, unless you use extremely large files.

---

### Post by igknighted on 2007-08-24
> **mlentink said:**
> Probably completely off-topic, but why do you consider vFAT to be inferior? It is natively supported by both OSs without additional software or drivers, and works fine, unless you use extremely large files.

1) I keep DVD iso's on my external - kinda a dealbreaker.  If someone is using it and isnt aware, then downloads a DVD image or rips one, they could be in for a nasty surprise.  They should be made aware when making the choice.

2) fat32 is easily corruptable.  There is no journal, so if your computer has a hard restart or your drive becomes unplugged (raise your hand if you've ever tripped over the USB cable... yeah, thats me), it can corrupt and lose data far easier than the journaled ntfs and ext3

3) It's slower.  Granted the USB disk I/O is so bad you probably won't notice, but still.

---

### Post by mlentink on 2007-08-24
Thanks!

---

### Post by mlentink on 2007-08-24
> **lastelement0 said:**
>  i just don't know how i would write to it and be able to install linux programs on it and have it run.
Ahh...
Is this perhaps the disk you boot from? If it's an external USB-drive, as I've been assuming so far, wouldn't you be using it for data only? You Linux software is installed in the usual places. 

Could you take a look in your /media directory and see if it&#347; there?
You could also simply try to copy a file to it...

---

### Post by lastelement0 on 2007-08-24
it is an external usb drive. im not booting from that. i am booting from my internal drive. however i want to use my external partition as a place to install other software and run it from. so my question is how should i set up the external's file system in order to do so. keeping in mind that is currently formatted ext3

---

### Post by igknighted on 2007-08-24
> **lastelement0 said:**
> it is an external usb drive. im not booting from that. i am booting from my internal drive. however i want to use my external partition as a place to install other software and run it from. so my question is how should i set up the external's file system in order to do so. keeping in mind that is currently formatted ext3

Hmm, the best way to install software to it would be to mount it as /opt, but even then not much would install there.  In reality you are best off leaving your apps on the / partition.

You could start over and put /boot and swap on the main HD, and put / on the external if you need space.

---

### Post by lastelement0 on 2007-08-24
when i set up the external i put / on the external drive. so i have two instances of it one on my internal and on my external

---

### Post by igknighted on 2007-08-24
> **lastelement0 said:**
> when i set up the external i put / on the external drive. so i have two instances of it one on my internal and on my external

I have no idea what you mean... / is the root of your install.  You can only have one of these.

---

### Post by lastelement0 on 2007-08-24
it asked me what mount point i wanted to make my external and i selected / when prompted.

---

### Post by mlentink on 2007-08-24
Yeah, but afaik the mount point is *where* you're mounting it, not as *what* you're mounting it. 

Could you take a look at the top of your filesystem (on your primary hard drive)? There should be a file representing that external drive somewhere

btw mine is in /media/removable just as the USB stick is in /media/usbdrive

---

