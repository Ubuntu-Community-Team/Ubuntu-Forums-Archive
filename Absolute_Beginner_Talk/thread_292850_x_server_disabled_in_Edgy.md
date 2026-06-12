---
title: "x server disabled in Edgy"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-04
I've upgraded to Edgy. Restarting the pc, first it says

cannot create  /sys/device/system/cpu/cpu0/...

then it stops at the "Running local boot scripts" for an error on the x server system, which turns out to be "could not open default font fixed"
Then I got two more messages:
The x server is now disabled
Restart GDM when it is configured correctly

But for me it sounds like Chinese.

Any help?

I can send the recovery mode (I have 3 files on desktop which I would like to save, but I don't know how), but then I don't know how to proceed.

:confused: :confused:

---

### Post by bulldog on 2006-11-04
To save your data you can mount your install with the live cd and copy your work.
Boot the live cd and create a mount point with your terminal```
sudo mkdir /mnt/rescue
```

Then mount your install presuming you know which partition your /home exist.
```
sudo mount /dev/??? /mnt/rescue
``` (??? stands for your partition like hd0,3)

Then go to your Desktop and save your files.

Edgy is a nice distro when you can solve problems,but if you have no clough in what's going wrong,Dapper is a better choice.

---

### Post by helphope on 2006-11-04
Thanks.
I'll try.

---

