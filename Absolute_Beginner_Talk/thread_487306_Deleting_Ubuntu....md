---
title: "Deleting Ubuntu..."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by CM Xtasy on 2007-06-28
If I'm dual-booting Windows XP and Feisty Fawn, and I delete all my Ubuntu-related partitions, will stuff go back to normal with XP (such as booting up).

---

### Post by rickycodie on 2007-06-28
yes, but why are you doing it?

---

### Post by CM Xtasy on 2007-06-28
> **rickycodie said:**
> yes, but why are you doing it?

Just wondering in case I found another distro I liked more than Ubuntu.

---

### Post by pistcivet on 2007-06-28
No. If you delete the Ubuntu partitions you won't be able to boot Windows anymore.
See here for solutions:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Digitallysick on 2007-06-28
you will probably have to go back into the repair console from your xp disk, and do a fdisk /mbr and fixboot to fix back the menu to normal, and then go into xp and remove the partition

---

### Post by tarek on 2007-06-28
Here's how you can fix the master boot: [http://blog.csmonkey.com/2007/04/fix-master-boot-record.html]("http://blog.csmonkey.com/2007/04/fix-master-boot-record.html")

---

### Post by anewguy on 2007-06-29
If you don't want to use Windows recovery console, just boot in Windows first, download a free program called "fixmbr" from dowloads.com.  This program will "redo" your boot record so that it will just boot straight into Windows with no other options like Linux.  Once you've done that just boot the LiveCD and rub parted to get rid of your Linux partitions and extend your Windows partition back over the now unused space.  When you reboot Windows it will probably run a chkdsk which is ok.  (Thanks to gcos7 for this information he posted before.  He said it is easy to do.);)

---

### Post by tarek on 2007-06-29
cool, didn't know that.

---

### Post by CM Xtasy on 2007-06-30
I'll still be able to keep my data right?

---

### Post by tarek on 2007-06-30
If you delete your Ubuntu partition then you'll lose the data on that partition.

Your data on Windows partition should be fine. HOWEVER, it's best to backup your data anyway.

tk

---

