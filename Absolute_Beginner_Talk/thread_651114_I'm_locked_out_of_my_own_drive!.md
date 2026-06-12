---
title: "I'm locked out of my own drive!"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2007-12-27
Hello Everybody,

Once again, I find myself locked out of my own drive. I have an external USB drive which is currently formatted in ext3, but I need to copy some valuable photos over from my one remaining Windoze computer. The Windoze computer doesn't see the drive, presumably because it doesn't recognise ext3, so I connected it to my Ubuntu m/c, opened GParted with the intention of re-formating it to ntfs. Unfortunately, it shows a padlock on the drive and I can't do a thing with it.

Looking over the forums on similar topics, I came across the 'sudo chown' command which worked once for me before, but won't work now. Why is this drive locked by default? I created it and now it doesn't allow me to do whatever I want to do with it.

Thanks in advance for all the advice.

Charlie

---

### Post by JurB on 2007-12-27
You have to unmount the disk first.
In Gparted, just right-click the partition/disk and select "Unmount"

---

### Post by lswest on 2007-12-27
also, depending on the size of the drive, fat32 might be a better idea for an external hard drive, but now that gutsy can read & write ntfs anyways it doesn't really matter much.

---

### Post by jken146 on 2007-12-27
If you like ext3 you might want to install some ext2 dirvers for windows.  [www.fs-driver.org](www.fs-driver.org)

---

### Post by Charlie Chick on 2007-12-27
Thanks everybody, I'll try your suggestions tomorrow morning.

---

