---
title: "Hard drive install"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by christhemonkey on 2006-05-04
Was just wondering if it was possible to do a hard drive install?

By a hard drive install, i mean that i have the dapper .iso image in my home directory, and would like to install it, but have no CDs to burn it on.

I know you can do this with Redhat
According to [here]("http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/install-guide/s1-begininstall-hd.html")
But can i do this on ubuntu?

---

### Post by Sef on 2006-05-04
This is from the Ubuntu wiki:

[https://wiki.ubuntu.com/Installation/HardDriveAndPcmcia?highlight=%28Install%29]("https://wiki.ubuntu.com/Installation/HardDriveAndPcmcia?highlight=%28Install%29")

---

### Post by christhemonkey on 2006-05-04
Ok, will try that tonight, not sure how just copying the vmlinuz and tuther one across will do an install though. Hmmmm

---

### Post by christhemonkey on 2006-05-05
Ok i see how copying the vmlinuz and initrd makes it boot and start installing,

but now my problem is that it looks for the cd to install packages off, and there isnt one.

I tried dropping to a shell and then mount /dev/hda3 (where the .iso is)
but it says device does not exist.
I tried all the other partitions listed as well, but none of them worked.

```
mount -t ext3 /dev/hda3 /mnt
```
Was the command i was using,

any ideas?/help?

---

### Post by christhemonkey on 2006-05-06
ok, in my ongoing epic saga to install dapper from a .iso.

I have managed to move the iso onto a partition i can mount (fat partition seemed to be the only one that wanted to mount)
using ```
sudo mount -t vfat /dev/hda5 /mnt
```

But now when i go to mount the iso with
```
sudo mount -o loop -t iso 9660 /mnt/dapper-install-i386.iso /cdrom
```

It fails saying there are no loop devices available.

If i pass that command with a -l option (mount -tl iso ...bla)
it mounts fine but the installer says it cant find the cd.


Please any help/suggestions?

---

### Post by christhemonkey on 2006-05-07
Ok
Now i am giving up on that install (was a flight 5 anyway)
So now am downloading the flight 7 live cd, so i should be able to install easier!

---

### Post by AnRuaRi on 2006-05-07
check out this thread, it may help, (I've never done any of this so i cant help myself)

[http://www.ubuntuforums.org/showthread.php?t=171629]("http://www.ubuntuforums.org/showthread.php?t=171629")

---

### Post by christhemonkey on 2006-05-07
Ok, so i gather your not meant to leave a space between the iso and the 9660.
Thankyou for your help AnRuaRi!


If i do get it to work installing from an iso, i might write a howto...
(although that is a big if!)

---

