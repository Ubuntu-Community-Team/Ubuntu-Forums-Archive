---
title: "Installing multiple versions of Ubuntu"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by extension on 2008-02-08
I currently have Ubuntu 6.06 installed (dual boot with Windows). Everything I need to work is working really well but I would like to try the latest Ubuntu. Is there a way for me to install Ubuntu 7 (8?) without removing my current installation but allowing it to see my home and data files?

I have a few games set up through Wine which I dont want to have to set up again but I dont want to have to copy my /drive_c over because its quite large and seems like a waste to duplicate.

---

### Post by HappyFeet on 2008-02-08
just create another partition and triple boot. you wont need another swap partition, as the 2 ubuntu's can share.

---

### Post by dstew on 2008-02-08
You can put a lot of distributions on one disk easily by creating a separtate partition, and mounting it on /home in whatever installation you install. Then, if you switch from one to the other, you can have the same /home directory, and configuration files. And yes, you don't need to make a new swap partition for each installed system, you can just reuse the one you already have.

---

### Post by dondad on 2008-02-08
> **HappyFeet said:**
> just create another partition and triple boot. you wont need another swap partition, as the 2 ubuntu's can share.


Not sure what would happen with a triple boot, but I installed hardy on a separate drive in my box that has gutsy installed. When I did the install of hardy, it changed some of the uuid's and my original install of gutsy would not boot. I had to edit fstab in the gutsy install to match to new uuid's in order to get gutsy to boot. (I have sata drives) If that happens, I am not sure what would happen with the windows boot. Just something to be aware of.

---

