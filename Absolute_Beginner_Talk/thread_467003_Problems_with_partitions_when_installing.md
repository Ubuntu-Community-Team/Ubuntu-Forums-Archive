---
title: "Problems with partitions when installing"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ercle on 2007-06-07
I am trying to install ubuntu alongside my vista installation, however i am having a few problems with my partitions and thought it better to ask for help rather than risk wiping everything.

 I currently have 5 partitions: 

222GB  ( Used for windows - NTFS), 9.99GB ( Recovery - NTFS), 2GB      ( Linux-swap), 116GB   (go between for windows and linux - FAT32)


In the partition section of the installer, i put the mount point for the 114GB section as "/" and the mount point for the go between as "/media/data" but when i try to go to the next step i get a warning message "file system doesn't have expected sizes for windows to like it. cluster size is 2l (1k expected); number of clusters is 24026 (47959 expected); size of FATs is 94 sectors (188 expected)". 

Could anyone help me with what i need to do to solve this problem? any help will be greatly apriciated :D

---

### Post by Inxsible on 2007-06-07
Could you take a screenshot of the GParted screen where it shows you your partitions?
 
To take a screenshot, Go to Applications --> Accessories --> Take Screen Shot

---

### Post by ercle on 2007-06-07
since i am using the internet on a different computer, i have a photo instead as it is quicker than unloading ubuntu

[http://www.imagehosting.com/out.php/i744988_DSC0006Large.JPG](http://www.imagehosting.com/out.php/i744988_DSC0006Large.JPG)

---

### Post by hillbilly on 2007-06-07
Could you clarify whether windows XP service pack 2 is already installed on your system ? What about the FAT32 partition. Does it already exist ? Or are you creating a new one ?
I think you already have a FAT32 partition on Windows and you are mounting it while installing Ubuntu ? If so rather than mount it during install, do it after the installation is over. Maybe that would ease your problems ?

---

### Post by lalita_car on 2007-06-14
> **ercle said:**
> since i am using the internet on a different computer, i have a photo instead as it is quicker than unloading ubuntu

[http://www.imagehosting.com/out.php/i744988_DSC0006Large.JPG](http://www.imagehosting.com/out.php/i744988_DSC0006Large.JPG)


Hi, I have the same problem, What can i do? Ignore? or Cancel?

---

### Post by afmpaz on 2007-07-13
i have same problem and i dont have a fat32 system file, i cant undertand what the meaning of this warning

---

