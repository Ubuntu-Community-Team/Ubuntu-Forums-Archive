---
title: "Mounting existing Harddrive query?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by bodyboarding_bum on 2007-02-26
Hey.
I'm new to linux and ubuntu. Im quite competent with windows XP and just moved from windows Vista to Ubuntu. I have 2 harddrives in this computer. The primary one (80GB), that ubuntu is running off, and then a slave drive (40GB)... the 40GB one has all my personal files on it, eg, music and pictures. It is formatted in NTFS format. My question is how do i mount this harddrive so i can access the files on it? I am not wanting to loose all the data on the HD. But am willing to format it once i have retrived the files and copied them onto the main HD with ubuntu on it. Thanks in advance,

Kyle

---

### Post by Terry of Astoria on 2007-02-26
There's a "disks" applet under "System"-"Administration" that may help you. 
Also check the guide - 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows")
--That's for Edgy - 6.10

---

### Post by alienexplorers on 2007-02-26
cd /
sudo mkdir data1
sudo mount -t ntfs /dev/hdb1 data1
cd data1
ls

---

### Post by bodyboarding_bum on 2007-02-26
Thanks heaps 'Terry of Astoria' that worked! Problem solved!
Thanks heaps :)

---

