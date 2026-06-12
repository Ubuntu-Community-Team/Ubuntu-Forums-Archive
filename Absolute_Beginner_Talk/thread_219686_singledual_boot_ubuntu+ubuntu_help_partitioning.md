---
title: "single/dual boot ubuntu+ubuntu? help partitioning"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by frafu on 2006-07-20
Hallo,



I am planing to build a pc whose main job will be to be a nfs- or smb-server. I thought to use ubuntu as os. As the machine does only have to run as a server a few hours a day, I also want to use it to play around, test and learn about ubuntu and linux. 

Now I am wondering whether I should install ubuntu 1 time or 2 times on the machine. Maybe I should install ubuntu 2 times: the first ubuntu-os as server and the second ubuntu-os as playing-machine without having to fear to destroy the server-os. 

After the desktop installation, will it be much work to configure it as nfs-server? If it is not much work, it may not be worthwhile to install a dual boot of 2 ubuntus!? 


Moreover, I have read that it is possible to put /home in a separate partition; this would have the advantage of not having to reconfigure the system when installing a new version of ubuntu. If I have /home in a separate partition, does I only have to reinstall ubuntu to have the server running again if I kill the system? 



Can I proceed in this manner (I have read a bit around in this formum about partinioning and dual booting; but keep in mind that I am a newbie in linux): 

- I will begin with installing ubuntu desktop on the 300 GB hard disk and configure it as server. I have read that the installer will partition the hard disk automatically, but should I not partition it manually as I want the served data to be in its own partition? If so, how many GB should I devote to ubuntu, to /home if I should create it, to the data partition? 

- If after a while, I would decide to go for the dual boot strategy (grub as far as I could read on this forum), will I be able to shrink the data-partition to create a new partition for the second ubuntu? (I have read that it is only possible to shrink the last partition of a hard disk; elsewhere I have read that the installer puts the swap partition as last partition of the hard disk; consequently I won't be able to shrink the data-partition as it won't be the last partition!?) 

Or will I be able to install the second ubuntu on a second hard disk to avoid shrinking partitions? Will the second ubuntu use the swap-partition of the first ubuntu or will I also need a second swap-partition? 



Finally, any advice that you can give me about what strategy I should adopt and about how to proceed will be greatly apreciated. 

frafu

---

### Post by fhqwhgads on 2006-07-20
Hi frafu,

If your server is not mission critical, it's probably easiest to just install a regular ubuntu desktop and add the server stuff. This link should help. Also, search the forum for LAMP.

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

Regarding partitions, during the install you can setup partitions manually. On my laptop, I have 10GB for root, 2GB for swap (it's probably too big, but I have more disk space than I need, should be around 1.5x RAM size), and the rest for /home. You may want another seperate partion for data to be used for  server purposes. If that data doesn't change often it will make /home backups quicker and easier.

---

### Post by frafu on 2006-07-20
@ fhqwhgads

First of all, thanks for your reply.

If I understand it correctly, the 10 GB for root will contain the system without the user applications!? (Otherwise I am afraid that the 10GB won't be enough!?)

frafu

---

### Post by fhqwhgads on 2006-07-20
Depends on how many apps you're installing, my install is pretty full featured and it takes up a little over 6GB. Feel free to make it 20GB or whatever you want if you have the space to spare.

---

