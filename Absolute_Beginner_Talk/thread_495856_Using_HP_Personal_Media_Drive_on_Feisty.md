---
title: "Using HP Personal Media Drive on Feisty"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by mhenriday on 2007-07-08
Or more generally speaking, backing up files from my **Feisty** partition on an external harddrive. The background to my query is as follows : I am running a triple-boot setup on a **HP Pavilion d4595.se** with an **AMD 64 X2 5000+** and two 250 GB harddrives, one of which (**dev/sda**) is used for my two **Windows** OS (**XP Home** and **Vista Business**, resp), the other (**dev/sdb**) for my **Feisty** setup. I back up **Windows** files using a 320 GB **Packard Bell** external harddrive ; given that the device is formatted and configured to use with **Windows** OS, that presents no problems. In order to be able to back up my **Ubuntu** files, I purchased a 300 GB **HP Personal Media Drive**, but find - not to my great surprise, that I need some help in making it work in **Feisty**. The drive is recognised by the file manager on my system, but when I click it I find three folders, **/media/HP Personal Media Drive/msdownld.tmp**, **/.../RECYCLER**, and **/.../System Volume Information**, none of which mean a great deal to me. I tried to open the latter and found two restore folders, a tracking folder and a database (see the relevant attachment), none of which I could successfully open. What I should like to do is copy my **dev/sdb1 ext 3** files to the external harddrive, which is recognised as **dev/sdg** by **GParted** (see the other attachment). I find myself out of my depth here, and should greatly appreciate any suggestions as to how I should proceed....

Henri

---

### Post by nitro_n2o on 2007-07-08
Why don't you tar everything in a huge tarball  and then send it to the drive 
tar can preserve the file system, directory structure and file permissions

---

### Post by mhenriday on 2007-07-08
Thanks for this interesting suggestion, **nitro_n2o** ! But as I remarked above, I'm out of my depth here, and need very concrete help with regard to how I can (1) tarball my **Feisty** files and (2) «send» them to the HP external drive. It seems to me not unlikely that the drive needs to be formatted to an **ext 3** format in order to accept such a tarball ; in that case, I'm going to need (very concrete) help with that as well....

Henri

PS : Don't inhale too much of the good stuff !...

---

