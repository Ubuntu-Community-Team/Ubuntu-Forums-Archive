---
title: "inatall and uninstall"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by dd1313 on 2008-01-20
Hi Guys

I want to install Ubuntu on my work laptop but I also want to uninstall if I leave the company
I have XP pro currently on the laptop.

I know how to do an insstall, how do I uninstall it

Thanks
DD

---

### Post by jleaker01z on 2008-01-20
You can just resize the Windows partition to take up the whole disk, or you can format the Ubuntu partition, format it NTFS, and set it up as a '2nd' drive for Windows.

---

### Post by wireddad on 2008-01-20
You could try [http://wubi-installer.org/](http://wubi-installer.org/).

---

### Post by Kilz on 2008-01-20
> **dd1313 said:**
> Hi Guys

I want to install Ubuntu on my work laptop but I also want to uninstall if I leave the company
I have XP pro currently on the laptop.

I know how to do an insstall, how do I uninstall it

Thanks
DD

If the laptop is the property of your employer, you may want to get permission from them before even trying to install Ubuntu.

---

### Post by Potatoj316 on 2008-01-22
Normally you wouldn't want to run this command (don't do it unless you want Ubuntu gone) You will still have a few partitions to take care of (try using GParted) But the command in the terminal (make sure you want ubuntu gone before running) would be 

sudo rm -rf /

[B]Unless you know what your doing (deleting everything on your hard drive and leaving you with an inoperable linux system) do not run this.  
**Be VERY careful with this command.  **[/B]

This will remove everything on your hard drive starting with the root and going through every directory that exists without asking you first.

---

