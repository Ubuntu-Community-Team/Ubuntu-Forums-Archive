---
title: "Help I cant boot ubuntu"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-09-13
Heres the low down:

I installed ubuntu as well as windows 2000 which I was running at the time, they dual booted fine. However, since I installed windows xp it naturally deleted the dual boot options and defaulted to windows xp. I tried the super grub disc but that seemed to delete my MBR entirely and I had to restore it. So I am back at square one having tried several options. I am now looking to explore some other options does anyone know of the simplest solution to dual boot these two already installed operating systems.

Thanks very much in advance, Id like to get back to using ubuntu ASAP because windoze is driving me crazy!!

---

### Post by Najand on 2006-09-13
Check this out:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Najand on 2006-09-13
Recovering ubuntu after installing Windows?
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by tommy1987 on 2006-09-13
I want to use the following:

1. Pop in the Live CD, boot from it until you reach the desktop. 

2. Open a terminal window or switch to a tty (Ctrl + Alt + F1). 

3. Type "sudo grub" 

4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub). 

5. Type "setup (hd0)", ot whatever your harddisk nr is. 

6. Quit grub by typing "quit". 

7. Reboot. 


....However I am not sure wot my hard disk and partition numbers are all about and what mine is set to, what can i do?

I only have one HDD and my only other OS is windows if it helps..

---

### Post by Najand on 2006-09-13
can you run:

```

sudo fdisk -l

```
and write it down here?

Also,
```

sudo grub
grub> find /boot/grub/stage1

```
if possible.

---

