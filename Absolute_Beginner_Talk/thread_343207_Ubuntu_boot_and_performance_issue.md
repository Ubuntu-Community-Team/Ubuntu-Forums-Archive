---
title: "Ubuntu boot and performance issue"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by nitro4file on 2007-01-21
Hi Everyone,

To save your precious time i will try to make questions as complete as possible with all fact and the computer config.

quad core opteron 1.8ghz, 2GB ram ecc reg, 2x Western digital raptor SATA, 256MB XFX video card 256mb, on a tyan board

My first question is about dual boot i read from docs available online that it will resize my windows etc, actually i made provision on the primary drive with one partition NTFS 34GB running windows XP SP2 and the 2nd partition not allocated.

1. I would like to know what is the best way to install ubuntu on the 2nd partition which is unallocated?(2nd Raptor is use under XP to keep data)

2. Considering the capacity of that computer do i still need to create a partition for swaping?

3. Since it a partition will Grub or whatever that some with ubuntu still ask me which OS i want to use at boot?

4. And last:) is the server version of ubuntu which has (LAMP) have GUI interface? like unbuntu? can i install WINE and other application as on ubuntu?

Thanks for your reply.

Nitros

---

### Post by xyz on 2007-01-21
Hi,
Have a look at this site for a start:
[Hermanzone]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Garyu on 2007-01-21
If you don't know what you're doing, let ubuntu partition your drive for you. Just don't select the "Wipe entire drive"-option as that will kill your Windows. But there is an option where ubuntu will setup swap and everything. You ALWAYS need swap space, no matter which computer you are running.

Grub will automatically make a list for you to choose which OS to start from. It is also quite easy to modify this list. /boot/grub/menu.lst

Server version is terminal only. There is no window manager. But you can install ubuntu-desktop to get everything in the normal version. Better way is to install Ubuntu as normal and then install LAMP. Lots of guides on the forum and on google. (For example [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP))

Good luck.

---

