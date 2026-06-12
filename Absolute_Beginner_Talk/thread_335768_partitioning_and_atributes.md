---
title: "partitioning and atributes"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by aoreste on 2007-01-10
Hello. I have a quick partitioning question.

The box that runs ubuntu has two hdds. I formatted one and installed ubuntu on it. Now i want to format my other hdd in NTFS beacause i want to write to it from my windows pcs in my LAN. 
which brings a second question. how do i apply full acces attributes to it (from within the lan)?

thanks a lot

---

### Post by indytim on 2007-01-10
Not directly answering your question, but why don't you format the second hd to FAT32.  That way Windows and Linux can both read-write without jumping through "hoops".  Just a passing thought.... 

IndyTim

---

### Post by louieb on 2007-01-10
If you are going to write to a hard drive over a LAN the computer doing the writing doesn't know and doesn't care what file system is being used by the computer hosting the hard drive.  The host operating system is doing  the actual  reading and writing to the hard drive. In most cases IP (internet protocol)  is what is being used to transfer data from one computer to the other because that is what each computers know.

So what that means is that unless the Ubuntu computer dual boot windows and windows is running on the computer, The best thing to do is use one of the native Linux file systems on the hard drive.

Sounds like you want to use the Ubuntu PC as a file server and give everybody full access to that hard drive. To do that you do a chmod 777 on the hard drive mount point.

---

### Post by Palypup on 2007-01-10
I also have the permissions problem. Ubuntu on hhd1 runs fine but no permissions for hda1, hda2,hdb1, hdd2 and hdd3.  Ran chmod 777 with no change that I was able to detect.
Hdb is ntfs and the rest except Ubuntu & swap on hdd1 are fat32. In previous install of Hoary, was able to see ntfs (I know that you can't write to it.)

---

### Post by louieb on 2007-01-11
> **Palypup said:**
> I also have the permissions problem. Ubuntu on hhd1 runs fine but no permissions for hda1, hda2,hdb1, hdd2 and hdd3.  Ran chmod 777 with no change that I was able to detect.
Hdb is ntfs and the rest except Ubuntu & swap on hdd1 are fat32. In previous install of Hoary, was able to see ntfs (I know that you can't write to it.)
I am not quite sure what type of permissions you are asking for?
Do you need to access data on the same computer or over a network?
If its data on the same computer  check out aysiu's [psychocats]("http://www.psychocats.net/ubuntu/mountwindows")  mounting windows page.  Although he is explaining how to access NTFS the same principal apply to any other partition on the computer.

---

### Post by Palypup on 2007-01-12
I want access to the fat32 partitions that are currently inaccessable.
I want to be able read from the ntfs that is currently unreadable.

---

### Post by benerivo on 2007-01-12
Have you tried altering tour fstab file yet?

---

