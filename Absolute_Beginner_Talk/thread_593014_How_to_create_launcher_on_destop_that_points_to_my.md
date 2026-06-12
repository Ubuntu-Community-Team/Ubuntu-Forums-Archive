---
title: "How to create launcher on destop that points to my Windows drive"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by john262 on 2007-10-26
I created a launcher that points to the drive on my computer that XP is on. No problem there. But everytime I reboot I have to go to Places|Computer and then click on that drive's icon, then enter my passowrd in order to get the launcher on the desktop to show up again.

Is it possible to change this behavior so that the launcher shows up on my desktop when I reboot without having to enter my password first? 

I am using Gutsy.

Thanks a lot.

---

### Post by crjackson on 2007-10-26
> **john262 said:**
> I created a launcher that points to the drive on my computer that XP is on. No problem there. But everytime I reboot I have to go to Places|Computer and then click on that drive's icon, then enter my passowrd in order to get the launcher on the desktop to show up again.

Is it possible to change this behavior so that the launcher shows up on my desktop when I reboot without having to enter my password first? 

I am using Gutsy.

Thanks a lot.

Go into your synaptics package manager and look for a package called ntfs config.  Install it and it will do exactly what you want.

---

### Post by MegaJim on 2007-10-26
Yes its possible.  What you need to do is add an entry for the partition to the /etc/fstab file.  Ununtu checks this file every time it boots and mounts the partitions listed there.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Read through that link, and let us know how you get on.

Regards, Jim

---

### Post by john262 on 2007-10-26
Thanks a lot for your help guys. I used ntfs config since it looked like it might be easier for a newbie, and it worked like a charm.

---

