---
title: "Grub loader broken"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by dustman on 2007-02-05
Hello, I have a problem with my grub loader. About 2 months ago I installed Ubuntu 6.06, dual boot with Windows XP. It worked perfectly. I was very pleased Ubuntu, since I've previously installed fedora 5, 6, suse, and couldn't get thing going there. But, yesterday I thought why not giving Windows Vista a try, and I replaced XP with Vista(formatted the XP partition and installed VIsta there). After the first reboot, I saw that the grub loader didn't appear, and that the system saw only Vista installed. I searched for an answer, about how to reinitialize the grub loader, and thought I've found it (it went somenthing like that :
1. Boot your computer up with Ubuntu CD
2. Go through all the process until you reach "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

But it didn't work for me(somehow the installer on the Ubuntu live CD crashed after beginning the installation...several times). So I've reinstalled Ubuntu on the partition where I already had it installed(formatted the partition first). Now when I reboot, the grub loader shows me that I have only Ubuntu installed, and no trace of Vista. Can anyone tell me how to set the grub loader to see both Vista and Ubuntu? 

Thanks!

---

### Post by uboat on 2007-02-05
You might have some success using the live or  alternate install disk to repair this issue.

---

### Post by dustman on 2007-02-05
well I tried to get the former install of Ubuntu going using the live cd, but without formatting the linux partition....but the installer from the CD crashed after beginning the installation...:(

---

### Post by ashmew2 on 2007-02-05
Why dont you try this method : 
1)Load up Live Session from Live CD
2)Open a terminal
3)Type these commands :
```
sudo grub
find /boot/grub/stage1
root (hd0,x).
setup (hd0)
quit
```
4)Reboot.

Replace the (0,x) with what it returned to u when u did find /boot/grub/stage1

---

### Post by dustman on 2007-02-05
I solved it...:D

Just edited the /boot/grub/menu.lst file, with sudo, to the bottom on the file, there are the grub loader options, there I added the code: 

title Microsoft Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1


the "root(hd0,0)" command means tells to load the system on the first HDD - hd0 (I have only one anyway...) and on the first partition (0)...cause I had Vista installed on C:\ (in windows). Works great !! :D. To change something to make this work for anyone, just modify the "root(...)" command, using your HDD ID, and your partition ID. Found this on [http://www.cyberciti.biz/faq/grubconf-for-windows-vista-or-xp-dual-boot/](http://www.cyberciti.biz/faq/grubconf-for-windows-vista-or-xp-dual-boot/)

Cheers!

---

