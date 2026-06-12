---
title: "Installing Over Fedora"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Zzl1xndd on 2006-08-30
Hi right now Im running a dual boot with Xp and Fedora Core 5 right now and I wanna switch to Ubuntu. And I was just wondering if I can just toss Ubuntu in the drive restart and install over the Fedora Partition and if so will I have to do anything with Grub or will it all be automatic?

---

### Post by edrodgers731 on 2006-08-30
I havent tried it, but I think the Ubuntu install will overwrite the MBR with your new grub config.

Ed

---

### Post by edrodgers731 on 2006-08-30
It must actually, because the FC5 grub config will be gone...

---

### Post by Zzl1xndd on 2006-08-30
Thanks I'll give it a shot on my next day off. but if anyone else has any advice ill take it.

---

### Post by zxee on 2006-08-30
The ubuntu installer should do what you want provided you tell it to use the partition that FC5 is on, it should also set up grub to dual boot with XP. 
Sometimes unexpected things happen though. I recommend you read the official install guides: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Zzl1xndd on 2006-08-30
Thanks.

---

