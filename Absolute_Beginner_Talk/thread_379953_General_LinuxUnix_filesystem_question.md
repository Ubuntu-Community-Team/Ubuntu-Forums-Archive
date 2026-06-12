---
title: "General Linux/Unix filesystem question"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by gordonsowner on 2007-03-09
Hi,

This may seem dumb, but I am really confused about one aspect of the file system... that is the concept of mapping the root directory '/' to a partition like '/dev/hda1'.

My question is that this seems like a real chicken-egg deal... when i mount or set this mapping in fstab, i wonder, 'how does the system know how to locate /dev/hda1 in the first place if I am just now, with this command, telling the system the definition of '/'?'  Doesn't it need to know how to resolve '/' in the first place to find the 'dev' directory and then the 'hda1' device?

Does this question make sense?  I mean, how can i tell the system to map '/dev/hda1' to '/' ***unless it already knows the definition of '/'*** and uses it to help resolve the location of /dev/hda1?  doesn't the system need to know '/' before it can start navigating to '/dev/hda1' because '/' is what starts out the definition of '/dev/hda1' by being it's starting directory?

I hope this question makes sense, because I am having the most difficult time trying to explain the question.

thanks,

---

### Post by igknighted on 2007-03-09
I believe at boot the kernel uses the initrd file to give it it's bearings (plus grub can read the FS).  When you boot there is a parameter root=/dev/hda1 and once it mounts that it reads from the file system.  Since the file system is standard, the kernel assumes thing are where they belong.

---

### Post by gordonsowner on 2007-03-09
Hi,

Thanks... I'm still a bit confused.  It's still using '/' in the definition of it's root path (even though now it calls '/' 'root').  I'm wondering... in the beginning of the process, is '/' not defined, but the 'dev' directory and it's devices known (independent of '/')?  I assume that this is like 'boot'.  Then, is '/' created, and the 'dev' directory is then put under it, creating the directory structure '/dev'?  I could understand if '/dev' really doesn't mean "the 'dev' directory under the '/' directory" in the beginning, but once '/' is associated with '/dev/hda1', then '/' is actually used in filesystem navigation parsing.

Perhaps this is a way to phrase the question... Are all of the following paths equal?:

/dev
/dev/hda1/dev
/dev/hda1/dev/hda1/dev
/dev/hda1/dev/hda1/dev/hda1/dev

etc.?

thanks,

---

### Post by melancholeric on 2007-03-09
> **gordonsowner said:**
> Hi,

Thanks... I'm still a bit confused.  It's still using '/' in the definition of it's root path (even though now it calls '/' 'root').  I'm wondering... in the beginning of the process, is '/' not defined, but the 'dev' directory and it's devices known (independent of '/')?  I assume that this is like 'boot'.  Then, is '/' created, and the 'dev' directory is then put under it, creating the directory structure '/dev'?  I could understand if '/dev' really doesn't mean "the 'dev' directory under the '/' directory" in the beginning, but once '/' is associated with '/dev/hda1', then '/' is actually used in filesystem navigation parsing.

Perhaps this is a way to phrase the question... Are all of the following paths equal?:

/dev
/dev/hda1/dev
/dev/hda1/dev/hda1/dev
/dev/hda1/dev/hda1/dev/hda1/dev

etc.?

thanks,
hda means the first hard drive. hda0 means the first partition on it. hda1 is the second. hdb is the second hard drive. hdb0 is the first partition. (Ok, so it's not quite that simple, but I don't feel like getting into it any deeper now).

Now, when linux boots, it just finds the hard drives and partitions, and assigns them those names accordingly. Then, after the root partition has been mounted, it adds them to the /dev/ directory.

The hda0 etc. files in /dev do not contain the contents of the partitions at all, just the devices (in linux, everything is a file. The user is a file, all devices are files ... everything, really). That's why you have to mount them (either manually or via fstab) to a mount point (typically in /mnt or /media) in order to actually access them. So, /dev/hda0/something would definitely not be a valid path.

Also, the /dev is (usually) a directory in the root partition. The root partitions mount point is, obviously, /. That's another reason why /dev/hda0/dev/hda0 can't work (apart from the device versus filesystem problem explained above).

I hope this cleared it up a bit.

---

### Post by Tomosaur on 2007-03-09
I think you're a bit confused. When you're mapping root to whichever partition - you're doing this from RAM. The installation software can read your partitions - it's just asking you where you want the  files to go. Nothing is on the partition until after you've mapped it and installed it - everything is running from RAM up to that point.

There is also a special reserved section called the MBR (Master Boot Record). This has a record of places on the hard drive which are bootable. When you install an operating system, this MBR gets updated to say 'there's a new OS at this position, you can boot into it'. When you map root to a certain partition - you're just telling the MBR and the bootloader that there's a new operating system there. It has nothing to do with Linux itself - it happens for every operating system you will ever install. Windows will overwrite your MBR to only point to Windows - it doesn't even ask you what you want to do - which is why there are so many threads saying 'I installed Windows and now I can't boot into Linux!'. Linux is still there, but the MBR doesn't know it.

---

### Post by gordonsowner on 2007-03-09
Thanks to everyone for your help so far... I am still confused, though.  Can any one point me to a good piece of documentation (preferably web accessible) that talks through the whole process of making a file system and mounting partitions?  I'd even like to read about disk hardware structure, driver info, and such, but mostly I'd like to see the detail of the step-by-step process linux/unix/os'es go through in creating a usable filesytem directory and what the nature of the files that represent devices in /dev are and how they work...

like i've said, the biggest hurdle for me is infinitely recursive-seeming nature of mapping '/' via a directory path that uses '/' in it's definition.

thanks,

---

### Post by dstew on 2007-03-09
Grub loads the operating system, and understands the meaning of /dev/hda even though the linux file system is not mounted. It knows the linux names of disks "by heart" and doesn't need to look them up. It basically hangs everything where it needs to go, turns over control to linux, then quits. The partition that will become root is defined before the file system is mounted, before linux can even read /dev. So, in that sense, '/' is not defined by an entry in /dev, but by grub during the boot process.

---

### Post by gordonsowner on 2007-03-09
Ok, I think dstew's answer really helped me clear up the 'chicken-egg' problem i was having... but if someone has links for more info, I'd appreciate it.

thanks,

---

### Post by igknighted on 2007-03-09
> **gordonsowner said:**
> Ok, I think dstew's answer really helped me clear up the 'chicken-egg' problem i was having... but if someone has links for more info, I'd appreciate it.

thanks,

Grub is installed on the MBR, but also parts of it are in /boot.  Grub know how to get to its config, that is built into the program.  In /boot is a System.map file and an initrd file.  These contain the initial direction for the kernel (also in /boot) to start the OS and mount the / partition.  Then once / is mounted fstab takes over and the rest of the file systems available can be mounted.

---

### Post by Bachstelze on 2007-03-09
There is not necessarily an initrd, though, if all modules required to boot are compiled into the kernel.

---

### Post by Patrick K on 2007-03-09
Here you go. More than you ever wanted to know:
[http://e2fsprogs.sourceforge.net/ext2intro.html](http://e2fsprogs.sourceforge.net/ext2intro.html)
EXT3 is the same file system as EXT2 with a couple extensions (journaling being the main one), so everything you read about EXT2 applies.

---

### Post by gordonsowner on 2007-03-13
Thanks!  I'm halfway through...

---

### Post by gordonsowner on 2007-03-16
Another related question that might help... as everything on linux is a file, are devices like /dev/hda really a file?  I mean, when I look at them either through GNOME or a CLI, it tells me that the file size is 0 bytes, or the file size is replaced by the major/minor number of the device.

I know that devices behave like a file, but if they are of size 0 bytes, what really is at the location, like /dev/hda?  When you mount a directory to a device, and pass it a path to the device in the /dev directory, what is really being used for the device?  Is there a 'there' there at the device location, or does it just know how to parse the string that is the '/dev/hda' for information on device location?

This might further clarify some of the lingering questions I have on this.

Thanks,

---

