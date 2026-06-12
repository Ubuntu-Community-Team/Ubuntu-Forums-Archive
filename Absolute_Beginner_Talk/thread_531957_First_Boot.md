---
title: "First Boot"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Kemik88 on 2007-08-22
Hello,

After installing Ubuntu over my old Ubuntu installation (I haven't used it in about two months so I wanted to reformat) it done the first boot checks such as error checking.

It said something about drivers and having no buffer available but the more scary thing is the fault/error checking bar failed and it said there are errors on the primary partition.

Should I reformat again or will it automatically fix the errors?

Thanks.

---

### Post by tyggna1 on 2007-08-22
Did you create a swap partition?  That could account for having "no buffer available"

If that's the case, then you'll either have to resize your partition in the GNOME partition manager (I love that utility, but there are others that will work) and format a swap.

---

### Post by Kemik88 on 2007-08-22
Yeap, I just used the old swap. It was about 4GB because I have 2GB of RAM.

I remember seeing it on the partition list during install. It says the primary partition then the swap space.

Here it is :)
> /dev/sda3           23800       24321     4192965   82  Linux swap / Solaris

---

### Post by tyggna1 on 2007-08-22
It'd be helpful to know what it said about drivers.  I'm gonna do some digging and see what turns up.   Did you format in extension 3 or something else?

---

### Post by Jimmyfj on 2007-08-22
I would simple reformat the repartition the drive and see if this brings up further error messages - What are the driver errors you mentioned? Is it related to your hard drive or to other devices in your system?

---

### Post by tyggna1 on 2007-08-22
Here's something else you can try if reformatting isn't your thing or doesn't work:

First, see if a volume can be unmounted--if it's your root, then don't bother.

```
umount directory
```

If it can, then you can use

```
e2fsck -p
```

on it.  This will automatically repair bad sectors on your hard drive.


If it can't be unmounted--then you'll want to try this from either a live CD or try recovery mode later.
For now, try a:
```
e2fsck -n
``` 

If you get an error code 4 on the -n check, then try the -p from your live CD, and that ought to do it.  Without the actual error messages and the stuff about the drivers, though, it's hard to say if this will fix it for sure.

e2fsck just checks your hard drive for bad sectors and the -p automatically fixes them.

---

### Post by Kemik88 on 2007-08-22
It said there were errors on the final check. I remember seeing something like file check hasn't been done for 4700 days. Forced check. I saw the [FAIL] but didn't get chance to read the full message.

I reformatted sda2 and edited the partition (on the manual format screen) to / as sda1 is my NTFS partition, sda3 is the swap.

Ubuntu booted up fine after that. I just want to update everything to find that it starts screwing up because it's unstable or missing files.

I'll run the commands and get back to you.

EDIT: It cannot be unmounted and e2fsck -n and e2fsck -p gives me a list of available commands for e2fsck. I'll boot using the cd and see what I can do there.

---

### Post by Kemik88 on 2007-08-22
I just did a reformat. The SWAP space is working now but I still get the "drive might have errors" message.

I'll do those checks again and get back to you.

---

### Post by tyggna1 on 2007-08-22
If your hard drive is old (more than 6 years, I'd say) it might be dying--in which case you'd want to back everything up.

Even if it is old, it might still be working--there's just a few bad parts that aren't.  The disk checking utility in linux should find those and the -p should repair them.  

I'm using Feisty, and I really don't know how to do this in any other distributions.

If the errors are on the windows segment of the drive, then the windows commands to check and fix this are:
```

click on run from the start bar
type cmd and press enter
from the prompt, type in:  chkdsk /r
type y at the prompt
reboot into windows
```

---

