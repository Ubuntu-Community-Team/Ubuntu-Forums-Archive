---
title: "how to read files from hfs+"
date: 2009-07-03
forum: Apple Hardware Users
---

### Post by sefs on 2009-07-03
I have a downed macbook

I was able to boot with ubuntu 8.10

and mount the mac partition to the /mnt/macosx folder

but I cant copy the files due to permission problems

I tried launching nautilus with gksudo but my root user can not see the files.

How can I go about copying files from the macbook hfs+ to an external drive...so close but yet so far.

Thanks guys.

---

### Post by bruce_g on 2009-07-03
Do you have the hfsplus package installed?

---

### Post by sefs on 2009-07-03
what do i do with it after installation?

I'm just trying to copy some files off a macbook thats giving trouble...but am running into permissions problems

---

### Post by tiagobt on 2009-07-05
What permission problem are you having? Could you post your /etc/X11/xorg.conf?

---

### Post by tiresia on 2009-07-06
How did you mount the macosx partition on /mnt/macosx?
Actually you shouldn't need to do it via terminal. The System will do it for just selecting the icon of your MacOSX Partition in 'Places'

You don't need any hfsplus package, the linux kernel is able to read hfsplus filesystem.

Last, lunch nautilus with root prilegies running```
gksu nautilus
```

---

### Post by cyberdork33 on 2009-07-06
> **sefs said:**
>  I tried launching nautilus with gksudo but my root user can not see the files.
Can you give more detail about how you are mounting the drive?

---

### Post by sefs on 2009-07-07
> **tiresia said:**
> How did you mount the macosx partition on /mnt/macosx?
Actually you shouldn't need to do it via terminal. The System will do it for just selecting the icon of your MacOSX Partition in 'Places'

You don't need any hfsplus package, the linux kernel is able to read hfsplus filesystem.

Last, lunch nautilus with root prilegies running```
gksu nautilus
```

```

sudo mount -t hfsplus /dev/sda1 /mnt/macosx

```

---

### Post by tiresia on 2009-07-07
Don't you see anything with ```
ls /mnt/macosx
```
Are you sure that sda1 is your drive?

---

