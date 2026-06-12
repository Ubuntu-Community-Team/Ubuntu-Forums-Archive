---
title: "G parted wont let me make a nfts partion"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-23
Im trying to dual boot vista, by reninstalling grub, G parted wont let me take my unnlocatd space and format it to nfts pation but lets me do fat 
This is a pic 
[http://img370.imageshack.us/my.php?image=screenshotbu9.png]("http://img370.imageshack.us/my.php?image=screenshotbu9.png")

---

### Post by glennric on 2007-05-23
gparted can't make NTFS partitions.  I don't believe that any linux program can.  I think only windows can make NTFS partitions.

---

### Post by Hobo Joe on 2007-05-23
I've never really understood what 'extended' partition did, it just seems to take up empty space.

Just in case you didn't do this, right-click on the ones you want to edit, and then unmount them, that could be causing problems.

---

### Post by Lucifiel on 2007-05-23
Erm, please don't use GParted to create an ntfs partition. Even if you used the GParted livecd, be warned that this is a very new feature. Thus, your partition could get corrupted over time or have strange behaviours, and you could lose all your data.

You're safer off using Windows to create an ntfs partition. 100% safer, if I may add.

---

### Post by discmaster on 2007-05-23
IIRC, when I started out; GParted wouldn't let you format ntfs, but whan I would run the live cd & click on the installer on the desktop, I could create ntfs through that.

---

### Post by mojo123 on 2007-05-23
it gives me a error on the vista cd

---

### Post by antoz on 2007-05-23
As far as I know you should be able to rightclick on the free space and format to any file system offered. I am pretty sure the live CD will be able to format to NTFS. Just remember you can only have a certain amount (I think it is 4 or 5) primary partitions after that they have to be logical partitions residing in an extented partition.
You could use the disk manager in windows as was suggested as well or use third party software Acronis is propably one of the best but it is not free.

---

