---
title: "New 500gb hdd.  Want Read/Write permission for Xp / Buntu"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by mithbuntu on 2007-10-15
Hello.  I just purchased a 5th HDD (woot, broke 1TB - dont ask ;D) to store all my music, movies, images, and documents and I'd like to be able to Read and Write from both XP and Linux. 

What is the best way to go about doing this? 

I am also not very clear on how I can link seperate HDDs into linux other than mounting, but that is a separate question.

---

### Post by Hospadar on 2007-10-15
I would format the drive with ntfs and use the ntfs-3g drivers and ntfs-config tool to access the drive through linux.  The ntfs drivers for linux are great and easy to install, there are good ext3 drivers from windows, but I've preffered to put my shared drives on ntfs.

---

### Post by mithbuntu on 2007-10-15
Alright, thanks.  I was having trouble writing to one of my old NTFS drives, but I don't think I was using NTFS tools correctly.  I'll try again.

I had heard FAT32 was the way to go, but I was hoping I could go NTFS - so thanks.

---

