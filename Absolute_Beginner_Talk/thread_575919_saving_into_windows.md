---
title: "saving into windows"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Ramrod_The_Wizard on 2007-10-14
Hey, I'm a complete beginner to linux (hence I'm posting in this forum :p) and I've run into a problem.  Whenever I try to save files into my windows partition directly where I want to save them, an error message says I do not have permission to.  How to I enable the ability to save between my partitions?

---

### Post by llamakc on 2007-10-14
Is your Windows partition NTFS or FAT?

---

### Post by Ramrod_The_Wizard on 2007-10-14
Honestly, I don't know.  How do I check?

---

### Post by wormser on 2007-10-14
You need to install ntfs-3g and ntfs-config if it is a NTFS drive.  Applications> Accessories> Terminal.

```
sudo apt-get install ntfs-3g ntfs-config
```

Then enable it.  Applications> System Tools> NTFS Configuration Tool.

---

### Post by Ramrod_The_Wizard on 2007-10-14
Well, I can save files/folders from windows to ubuntu, but still cannot save files on ubuntu to windows.  :(

---

### Post by HermanAB on 2007-10-14
The stock NTFS device driver for Ubuntu is a read-only driver.  In order to be able to write to NTFS, you need to install ntfs-3g as mentioned above.

---

### Post by Ramrod_The_Wizard on 2007-10-14
> **HermanAB said:**
> The stock NTFS device driver for Ubuntu is a read-only driver.  In order to be able to write to NTFS, you need to install ntfs-3g as mentioned above.

I just did and I enabled write support, though it only gave me the option of external drive.

---

### Post by wormser on 2007-10-14
> **Ramrod_The_Wizard said:**
> I just did and I enabled write support, though it only gave me the option of external drive.

Maybe your internal drive is not NTFS.  Use the following command and report back what type of file system it is.

```
gksudo gparted
```

---

### Post by Frak on 2007-10-14
run
```
gksudo nautilus
```
Navigate to /media/<Windows_Drive> and you should now be able to write.

ntfs-3g is already installed on Feisty and Gutsy.

---

