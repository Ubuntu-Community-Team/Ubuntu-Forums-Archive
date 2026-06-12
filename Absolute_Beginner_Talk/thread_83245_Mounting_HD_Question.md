---
title: "Mounting HD Question"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by Darrin on 2005-10-28
I mounted my windows partition and a second HD. Both are on my desktop. I can browse the windows partition fine, but the second HD I cannot. I click on it and get a message saying I dont have permissions. But if I go to Menu>System>Administration>Disks, select the drive and click on the partitions tab and click on browse, I can brows that drive fine. That particular drive is NTFS. I would like to be able to read and write on that drive. I understand that I cannot because its a NTFS. The data on there is just back up data. So do you think I would be better of just reformating it as Fat32 so the ability to read and write will be there? I can easily replace the place the data back on it again. Are there any disadvantages in making it Fat32?

---

### Post by Robgould on 2005-10-28
I would format it as fat32.  Micorsoft will not release the technical details of NTFS, so people try and reverse engineer it.  Even if you could write to it, I would not suggest it.  The only downsided to FAT32 is that you will not be able to assign NTFS permissions to the data from windows.  If you are not worried about that, and your data is easy to replace, go for the fat.  Will be much better solution.

---

### Post by Darrin on 2005-10-28
Ok thanks. Ill probably go ahead and do that then. Its just backup photos, documents, and program backup files. Im assuming I could always drag them on my primary windows drive and drag them back once the drive has been reformated.

---

### Post by Wolki on 2005-10-28
[QUOTE=Darrin]I mounted my windows partition and a second HD. Both are on my desktop. I can browse the windows partition fine, but the second HD I cannot. I click on it and get a message saying I dont have permissions. But if I go to Menu>System>Administration>Disks, select the drive and click on the partitions tab and click on browse, I can brows that drive fine. That particular drive is NTFS. I would like to be able to read and write on that drive. I understand that I cannot because its a NTFS. The data on there is just back up data. So do you think I would be better of just reformating it as Fat32 so the ability to read and write will be there? I can easily replace the place the data back on it again. Are there any disadvantages in making it Fat32?[/QUOTE]

You can't really write to NTFS (you can if you either risk data loss or pay for paragon's drivers). You should be able to access them as a normal user though. Partitions enabled with the Disks utility are usually readable only by root, but you can add them manually to your /etc/fstab to allow yourself to view the partitions. More Info here: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

Diadvantages to Fat32 are for example that checking the disk after windows crahes takes longer. I'd go for it.

---

### Post by Mustard on 2005-10-28
[QUOTE=Darrin]Ok thanks. Ill probably go ahead and do that then. Its just backup photos, documents, and program backup files. Im assuming I could always drag them on my primary windows drive and drag them back once the drive has been reformated.[/QUOTE]

That sounds like a pretty good assumption, space limitations permitting.

---

### Post by patrick295767 on 2005-10-28
[QUOTE=Wolki]You can't really write to NTFS (you can if you either risk data loss or pay for paragon's drivers). You should be able to access them as a normal user though. Partitions enabled with the Disks utility are usually readable only by root, but you can add them manually to your /etc/fstab to allow yourself to view the partitions. More Info here: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

Diadvantages to Fat32 are for example that checking the disk after windows crahes takes longer. I'd go for it.[/QUOTE]
   
I know that at the beginning Linux is very difficult to handle with ... 
But u'll see, after some time, u'll be totally free with ur linux and will findn it amazing ... much, more powerful than Windows and
with crossover weager u can even run most windows apps ... 
soo... what's more required ...
  
Me i am now busy with making lot of dvd backup of my ntfs big hdd to pass them to ext3 ...
  
No windows anymore 'cos linux is much more than a simple windows !!
  
Paragon is eventually the best solution or maybe the dual boot ... 
  or Patience maybe ...
  
Courage & Let us know about your progress about it !

Patrick

---

### Post by Darrin on 2005-10-28
[QUOTE=patrick295767]I know that at the beginning Linux is very difficult to handle with ... 
But u'll see, after some time, u'll be totally free with ur linux and will findn it amazing ... much, more powerful than Windows and
with crossover weager u can even run most windows apps ... 
soo... what's more required ...[/QUOTE]

Your correct at times it does seem difficult for me to work with. I am learning things as I go and what seemed difficult in my first launch of linux now seems easy. Thats how the progression is turning out slowly. At the moment it seems hard to imagine being windows free, it seems so far out there for me right now. But that is a goal I would like to be at. 
Its been a pleasant experience in the forums here. I havent had anyone bash me for asking lame questions. But Ive always received responses. I hate being the new guy. In the future Im sure Ill be able to answer questions as well.

---

