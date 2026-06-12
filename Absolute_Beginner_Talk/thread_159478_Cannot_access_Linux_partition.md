---
title: "Cannot access Linux partition"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by iplgecko on 2006-04-13
Hi Im new to ubuntu, I just recently successfully installed ubuntu 5.10 only when I boot it everything seems normal except when I try to access my harddrive which is labled "hda1" it comes up with an error saying the contents could not be displayed and that I do not have permissions necessary. if anyone can help me with this Id appreciate it alot. Thanks.

-Jason.

---

### Post by nemequ on 2006-04-13
How are you trying to access it? You need to gain superuser priveldges before you change much of anything outside of your home directory... What are you trying to do?

---

### Post by aysiu on 2006-04-13
Can you go to Applications > Accessories > Terminal and post the output of this command? ```
sudo fdisk -l
```

---

### Post by iplgecko on 2006-04-13
Thanks very much for the fast reply. Well im really new to all this and it seems so different. I was just trying to open it from the desktop seeing as there is already a short cut. I was just going to use it for storing things eg. videos. Also I plugged my ipod in and a shortcut came up on my desktop but I cannot even access that :s

---

### Post by aysiu on 2006-04-13
Please see my last post.

Is /dev/hda1 your Windows partition? Your title would indicate otherwise, but you don't seem to have any trouble logging into Ubuntu...

---

### Post by iplgecko on 2006-04-13
Yes my windows partition is /dev/hda1. It's weird. When I go to system > administration > disks I can access everything.

EDIT: When I click on the "hda1" shortcut on my desktop and select properties it says it is 19gb which is my linux partition.

---

### Post by aysiu on 2006-04-13
So this thread should really be titled **Cannot access Windows partition**.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by iplgecko on 2006-04-13
Ok. How do I access the root of linux one, and what is in it? Is it full of all my system folders?

---

### Post by aysiu on 2006-04-13
[QUOTE=iplgecko]Ok. How do I access the root of linux one, and what is in it? Is it full of all my system folders?[/QUOTE] Maybe this might help? [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by iplgecko on 2006-04-13
Thanks ill give it a read. =]

---

### Post by iplgecko on 2006-04-13
Wow linux seems so different and confusing :S. How do I install anything, do I just run an executable?

---

### Post by aysiu on 2006-04-13
[QUOTE=iplgecko]Wow linux seems so different and confusing :S. How do I install anything, do I just run an executable?[/QUOTE] [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

