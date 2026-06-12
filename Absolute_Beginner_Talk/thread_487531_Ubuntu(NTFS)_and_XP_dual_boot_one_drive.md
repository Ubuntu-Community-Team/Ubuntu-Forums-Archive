---
title: "Ubuntu(NTFS) and XP dual boot one drive"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by hill0093 on 2007-06-29
Can someone please tell me in elementary language if and how I can install Ubuntu and XP dual boot one drive both NTFS?

---

### Post by overdrank on 2007-06-29
> **hill0093 said:**
> Can someone please tell me in elementary language if and how I can install Ubuntu and XP dual boot one drive both NTFS?

Hi, Ubuntu can not be used on NTFS but you can dual boot, Here is a link that may help
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Hope this helps and Good luck! :KS

---

### Post by Gausian on 2007-06-29
NTFS is a windows filesystem.  Im pretty sure that you cant install Ubuntu (or any Linux) on an ntfs filesystem.

Linux needs FAT or ext2/3

---

### Post by mikewhatever on 2007-06-29
Ubuntu can't right to ntfs by default, ntfs being a proprietary file system, so if you wanted Ubuntu installed on ntfs formatted partition, forget about it. The link above, posted by overdrunk, shows a traditional installation, which is what most of the users want. There are other options, for example [http://wubi-installer.org/](http://wubi-installer.org/)
I have not tried it, and it looks  like a virtual machine, in short, read the FAQ.

---

### Post by gn2 on 2007-06-29
> **Gausian said:**
> Im pretty sure that you cant install Ubuntu (or any Linux) on an ntfs filesystem.



Wubi is one way of doing so. [http://wubi-installer.org/index.php](http://wubi-installer.org/index.php)

---

### Post by mlentink on 2007-06-29
> **mikewhatever said:**
> There are other options, for example [http://wubi-installer.org/](http://wubi-installer.org/)
I have not tried it, and it looks  like a virtual machine, in short, read the FAQ.

Wubi is NOT a virtual machine, but a method of installing Ubuntu on a 'virtual disk', a wrapper of sorts, in Windows. It has advantages for those who want to try out ubuntu but are afraid of repartitioning before they take the plunge.
I have used it before and it works well, I felt the use of the alternate install disk to be a bit of a drawback. Other then that I can recommend it, because it also allows for easy uninstall of Ubuntu. That's what I did before devoting my whole disk to Ubuntu

EDIT (ADD): If the OP is uncertain about whether or not he/she will be able to access the data on the other partition: fear not, there are tools to do that.

---

### Post by mikewhatever on 2007-06-29
> **mlentink said:**
> Wubi is NOT a virtual machine, but a method of installing Ubuntu on a 'virtual disk', a wrapper of sorts, in Windows. It has advantages for those who want to try out ubuntu but are afraid of repartitioning before they take the plunge.
I have used it before and it works well, I felt the use of the alternate install disk to be a bit of a drawback. Other then that I can recommend it, because it also allows for easy uninstall of Ubuntu. That's what I did before devoting my whole disk to Ubuntu

EDIT (ADD): If the OP is uncertain about whether or not he/she will be able to access the data on the other partition: fear not, there are tools to do that.

Does the virtual machine not create a virtual disk? What happens when Ubuntu is installed? Do you boot into Windows and then start Wubi, or can you boot into Ubuntu proper? What happens with all the Windows processes while Ubuntu is running, namely, do they run in the background too?

---

### Post by mlentink on 2007-06-29
You boot into Ubuntu. There are no Windows processes to suspend etc. because windows is not running when you chose ubuntu at start-up. 
It is the same as dual boot, with the exception that in this case, the ubuntu partition is a wrapper, a virtual disk on ntfs. So no, this is not similar to a virtual machine at all

---

### Post by mikewhatever on 2007-06-29
> **mlentink said:**
> You boot into Ubuntu. There are no Windows processes to suspend etc. because windows is not running when you chose ubuntu at start-up. 
It is the same as dual boot, with the exception that in this case, the ubuntu partition is a wrapper, a virtual disk on ntfs. So no, this is not similar to a virtual machine at all

Sounds interesting, thanks.

---

