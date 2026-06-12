---
title: "What is the proper shell command to format a sd card?"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by CujoQuarrel on 2006-10-19
What is the proper command to format a removable media card (or USB drive) from the shell to fat32? 

I'm wanting to build a bash script so I can click on the icon and format it from Nautilus.

---

### Post by glug101 on 2006-10-19
> **CujoQuarrel said:**
> What is the proper command to format a removable media card (or USB drive) from the shell to fat32? 

I'm wanting to build a bash script so I can click on the icon and format it from Nautilus.

** scratches head **

If I remember correctly, the line you would want is:

```
sudo mkdosfs -F 32 devicename
```

Where devicename = the partition location (likely /dev/sda1)

You can discover the correct partition location by mounting a formated media card and then typing:

```
df -h
```

Not sure how well this will work if the drive is already mounted by the Ubuntu automounted, but I'm sure that you'll need to work in gksudo somehow if you want to run it off of a simple click in Nautilus. This command requires root access.

Hope this helps!

---

### Post by CujoQuarrel on 2006-10-19
That works. You have to umount the drive first. 

Now for the next part , figuring out what the device to pass to the script when the icon is right clicked on. 

Anyone have any suggestions for that?

Thanks

---

