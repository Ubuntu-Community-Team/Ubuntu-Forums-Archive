---
title: "Partitioning Questions"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-04-23
I am re-installing Ubuntu after it blew away my MBR and wouldn't allow me to boot to XP.  

So today, I have put a fresh install of XP back on my machine (good thing I had a backup for my data files).  Now, I am installing Ubuntu again and am the partitioning window.

I have two separate IDE drives (one for XP, and one for Ubuntu).  Ubuntu install is asking which drive I want to use and how I want to format it.  Of course I am going to install on my dedicated Linux drive (IDE 1, a slave drive).  The question I have is:  which formatting method?  Do I use the standard "erase and reformat", or use "LVM" on that drive.  Since I don't want to reinstall everything again, which is the better method to use?  What is the difference?

---

### Post by jorn on 2006-04-23
Use erase and format. LVM is some very complicatet. Uses different disks where you can move patitions more easily and more.

---

### Post by skinnygmg on 2006-04-23
a tip from "Beginning Ubuntu Linux" (a book from Apress):

<b>Caution: </b>Be careful not to select the option marked "Erase entire disk and use LVM."  This is an option for a different kind of Ubuntu setupused by experts.

this book is great if you are new to ubuntu/linux

---

### Post by landsg on 2006-04-23
Thanks all, let's see what happens!

---

### Post by landsg on 2006-04-23
Everything installed fine.  Thanks all!

---

