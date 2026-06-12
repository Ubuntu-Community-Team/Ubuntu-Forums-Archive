---
title: "Dual Boot Windows Won't Work"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by bertman56 on 2007-01-12
Please Help!!!


I am new to Linux. I was a bit too hasty in installing ubuntu 6.06 on a second HD. Now when I boot Windows 2000 it will not run correctly. I can't access the internet, or use the start menu.

My question is how do I uninstall Linux so that I can fix windows?

Thanks in advance for your help. 

Bert

---

### Post by Tomosaur on 2007-01-12
You shouldn't need to uninstall Ubuntu to fix Windows, but why Windows isn't working in the first place is a bit confusing. Can you please open a terminal and type the following command:
```

sudo fdisk -lu

```
The password it asks for is the same password you use to log on.

---

### Post by netadptr0719 on 2007-01-12
If you have a windows disk put it in and boot from the CD. Once it starts you can go into repair console and this will give you a command prompt. Then enter fixboot and then fixmbr. This should get grub off your system. Boot from the CD again and then this time don't go to a repair console. Wait till it shows you your partition table, chose where Windows is at and it should give you a "repair" choice at the bottom. If that doesn't work you just lost Windows pretty much.

---

