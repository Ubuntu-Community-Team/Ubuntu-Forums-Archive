---
title: "Ubunto installer won't detect linux partitios"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by totalnewbie on 2006-11-16
HI i have no idea why but i ran into a very strange proble, i've had uvuntu installed for a while but recently i saw the need to format my windows partiton, after doing so i went to the rpocess of reinstalling grub as i've done before, but turned out that grub just see the entire hardrive as one single partition instad of my two NTFS 1 fat and 1 reisefs and 1 swap, when i'm under windows i see my 2 ntfs and my fat 32 partitions there and with acronis partition manager i can see all of the partitions, now ubuntu /kubuntu disk don't even see the partitions for reinstall purposes so any ideas or suggestions are welcome.

Thank you very much in advance.

---

### Post by mahy on 2006-11-16
Can you boot into your Ubuntu? I think so, coz you only formatted your ntfs partition. How do you know the partitions are not seen by Ubuntu? Look into /dev and check for hd<something> and/or sd<something> files.

---

### Post by totalnewbie on 2006-11-17
When i use live cd and run the installer it only says there is one hda partition 120gb and no more and ask me if i want to delete that aprtiton or install there and no more options, however if i run mount from console i-m able to mount the partitions all of then even the ntfs and fat partitions.

---

### Post by seshomaru samma on 2006-11-17
Did you try to reinstall the Grub menu without mounting anything?
Boot into the live CD 
open a terminal and run :
```
sudo grub
```
then:
```
find /boot/grub/stage1
```
replace the question marks in the following command with the output of the last command :
```
root (hd?,?)
```
[like : root (hdo,1) ,probably]
then:
```

setup (hd0)
```
and
```
quit
```

if you get any errors copy them in your next post
hope this helps

---

