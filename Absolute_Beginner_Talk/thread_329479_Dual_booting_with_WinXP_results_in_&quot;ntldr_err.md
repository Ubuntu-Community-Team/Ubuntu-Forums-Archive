---
title: "Dual booting with WinXP results in &quot;ntldr error&quot;"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by inkybutton on 2007-01-01
Hi,
I decided to install Windows XP back (yes, I tried my best to avoid it), so I fished out a spare 10GB hard disk and installed XP on it. Here is how I did it:

1) Remove the hard drive containing Ubuntu and other data.
2) Install the 10GB hard drive, and installed Windows XP.

Now Windows XP booted up perfectly, so I proceed to put the Ubuntu hard drive back and setting it as master, while the Windows XP hard drive is the slave.

After POST and stuff, GRUB boots up. After slightly editing the option to boot Windows XP (I used to have WinXP installed on my Ubuntu hard drive, thus the option exists) to reflect the location WinXP is in, I tried to boot WinXP.

Here is the altered option.
```
title           Windows NT/2000/XP (loader)
root            (hd1,0)
savedefault
makeactive
chainloader     +1




```

Here is the result (from my memory)
```

Filesystem is FAT, ...
...
Error: NTLDR not found. Press any key to restart.

```

I thought there is something wrong with the boot.ini file of WinXP, so I also altered some of the numbers bolded below:
```
[boot loader]
timeout=30
default=multi(**0**)disk(**1**)rdisk(**0**)partition(**1**)\WINDOWS
[operating systems]
multi(0)disk(**1**)rdisk(**0**)partition(**1**)\WINDOWS="Windows XP Professional" /fastdetect

```

Still, it doesn't work. Any ideas? Thanks! :)

---

### Post by hoges on 2007-01-01
It doesn't seem to be finding the os. Is hd1,0 the right address for xp?

Also, there is a chance that it could be conflicting with the windows boot manager. If the windows one is still there, and the two os's are one different drives, than there are ways around it.

Does you bios have a boot selection option? Mine's f8. This way you can select which hdd you want to boot from, thus avoiding any conflicts. To some this is just as easy as editing grub.

---

### Post by adaptr on 2007-01-01
> **inkybutton said:**
> Hi,
I decided to install Windows XP back (yes, I tried my best to avoid it), so I fished out a spare 10GB hard disk and installed XP on it. Here is how I did it:

1) Remove the hard drive containing Ubuntu and other data.
2) Install the 10GB hard drive, and installed Windows XP.

Now Windows XP booted up perfectly, so I proceed to put the Ubuntu hard drive back and setting it as master, while the Windows XP hard drive is the slave.
Errrrngh!
That's what screwed your Windows boot loader - it is no longer on drive **C:**.
I know, it's sad - but it **has** to be on the **first bootable hard disk** for Windows to work.

> After POST and stuff, GRUB boots up. After slightly editing the option to boot Windows XP (I used to have WinXP installed on my Ubuntu hard drive, thus the option exists) to reflect the location WinXP is in, I tried to boot WinXP.
Mistake # 2 ;-)
All you really need to do is convince Windows that it is in fact booting from the first HD, which you can do with Grub's map() command.
> title           Windows NT/2000/XP (loader)
root            (hd1,0)
[B]map (hd0) (hd1)
map (hd1) (hd0)
[/B]savedefault
makeactive
chainloader     +1
should take care of that.

But when that works, you run into another problem - Windows itself is not on the first drive anymore.
Thus we alter the boot.ini file:

> [boot loader]
timeout=30
default=multi(**0**)disk(**0**)rdisk(**1**)partition(**0**)\WINDOWS
[operating systems]
multi(0)disk(**0**)rdisk(**1**)partition(**0**)\WINDOWS="Windows XP Professional" /fastdetect

The **rdisk** is actually the physical hard disk; the **disk** part refers to a bus (like IDE-1, or SCSI-2).

SHould you manage to now boot Windows, it might work.
Why go through all of this trouble in the first place ?

- Install Windows like you did, on a new drive installed solo.
- add back the Ubuntu drive as the **slave**, **leave the Windows drive as the master**.
- now re-install GRUB in the windows drive, alter the grub menu, and edit /etc/fstab to reflect the new device mount points.
A lot less painful, it only takes one reboot, and it is **guaranteed** to work - unlike tweaking Windoze...

---

### Post by gn2 on 2007-01-01
This is how I would do it: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

However, if hardware is up to the task I would advocate virtualisation using VMWare Server free version instead of dual-booting .

---

### Post by inkybutton on 2007-01-02
Thanks for all of the replies! Will try.

---

