---
title: "data migration from ubuntu to mac"
date: 2020-03-28
forum: Apple Hardware Users
---

### Post by sram180990 on 2020-03-28
hi, 
I am using Ubuntu 18.04. And I have purchased a macbook.
I would like to migrate my data from ubuntu to mac.
How can i do this.
Please suggest me some ways..
Thank You.

---

### Post by TheFu on 2020-03-28
rsync over ssh.

---

### Post by Impavidus on 2020-03-29
1: Copy the files to your backup drive.
2: Restore your backups to the macbook.

Bonus: This allows you to test your backup routine.

(All assuming your macbook can handle the filesystem on the backup drive. If not, you have to do it via the network, as suggested above.)

---

### Post by slickymaster on 2020-03-29
*Thread moved to **Apple Hardware Users**.*

---

### Post by spswitzer on 2020-03-29
Just a thought.

If you have an Apple iCloud account you can upload your data to iCloud, then use the data from there as needed.  I keep the vast majority of my data in my icloud account and access it from both my Mac and Linux machines.  If you create an iCloud account you will have access to their web based version of word processor, spread sheet, and presentation software, as well as photos, and iCloud Drive.

---

### Post by TheFu on 2020-03-29
> **spswitzer said:**
> Just a thought.

If you have an Apple iCloud account you can upload your data to iCloud, then use the data from there as needed.  I keep the vast majority of my data in my icloud account and access it from both my Mac and Linux machines.  If you create an iCloud account you will have access to their web based version of word processor, spread sheet, and presentation software, as well as photos, and iCloud Drive.

Unless the network is down.  As linux people, we can easily self-host our data and have it securely available from anywhere, removing the issues of privacy that using cloudy services all bring.  People w/ 500 MB of important data probably don't care assuming it is all encrypted BEFORE being pushed onto cloudy storage.  Of course, self-hosting brings liabilities and responsibilities too.

---

