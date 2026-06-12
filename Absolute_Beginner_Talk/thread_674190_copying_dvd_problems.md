---
title: "copying dvd problems"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by beanco on 2008-01-21
trying to copy a dvd and when I put the disc in two things happen

1. the disc does not show up anywhere, not on the desktop, for instance. However, if I try to open it using VLC it will play of if I go back to desktop I can see the icon for there then.

2. Right click on icon, choose copy disc it starts writing, then I get a msg to insert blank disk with 6 gb free space. but this happens within a minute or two of hitting the write button, it has obviously not actually made the temporary copy... so what is going on?

If I had put a blank disc in tat was too small, I would understand why I get that error msg, but this i get it when I have only put the original in.

Thanks

Robi

---

### Post by mrphud on 2008-01-21
Is your device detected? try typing 

```
sudo fdisk -l
```

 and see if you device is listed

---

### Post by beanco on 2008-01-22
not quite sure what you want me to do.

I cna run the command but not sure what it is supposed to do.

this is what I got

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14405   115708131   83  Linux
/dev/sda2           14406       14593     1510110    5  Extended
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris
rob@rob-desktop:~$ 

```

---

