---
title: "OpenBSD Custom iso."
date: 2012-09-30
forum: Any Other OS
---

### Post by Haghiri75 on 2012-09-30
Hi all. 

I installed OpenBSD 5.1 and I've installed a lot of programs (about 2GBs) on the machine. and now i have to cheange my operating system.
I need a tool like remastersys or relinux to create backup ISO image. 
(I tried openbsd-custom-livecd.sh script but it doesn't work correctly)

Regards.

---

### Post by spottraining on 2012-09-30
You want to change the OpenBSD to Linux? Or You want reinstall the OpenBSD?

---

### Post by mips on 2012-09-30
[http://openbsd.org/faq/faq14.html#Backup](http://openbsd.org/faq/faq14.html#Backup)

You could also use dd to image the drive/partitions

---

### Post by Haghiri75 on 2012-09-30
> **spottraining said:**
> You want to change the OpenBSD to Linux? Or You want reinstall the OpenBSD?
I have to change to linux for 2-3 days and  I don't want to re-install the packages on Open**BSD** (Internet speed is slow in iran :D)  .

---

### Post by Haghiri75 on 2012-09-30
> **mips said:**
> [http://openbsd.org/faq/faq14.html#Backup](http://openbsd.org/faq/faq14.html#Backup)

You could also use dd to image the drive/partitions
thanks. but I want to install my customized OpenBSD on other laptop ;)

---

### Post by mips on 2012-09-30
> **Haghiri75 said:**
> thanks. but I want to install my customized OpenBSD on other laptop ;)

Try imaging the partition across.

---

### Post by Haghiri75 on 2012-09-30
> **mips said:**
> Try imaging the partition across.
what's that? like g4u?

---

### Post by mips on 2012-09-30
Yes that's one of many.

---

### Post by Haghiri75 on 2012-09-30
> **mips said:**
> Yes that's one of many.
Ok. I tried g4u but it can't detect my hard drive :-O ! 
and now I try Acronis True Image bootable disk , but it doesn't work too :)

---

### Post by Haghiri75 on 2012-10-02
I can't create ISO image with partition imaging software :(. 
How do i can install squashfs-tools on OpenBSD?

---

### Post by mips on 2012-10-02
Have you tried dd or clonezilla to image the partitions across?

---

### Post by Haghiri75 on 2012-10-02
> **mips said:**
> Have you tried dd or clonezilla to image the partitions across?
yes.
but I need a tool like remastersys , because I have to install my customized OpenBSD on other laptops.

---

### Post by mips on 2012-10-02
[http://www.mindtwist.de/main/openbsd/1-openbsd-live-cd/2-how-to-create-a-custom-open-bsd-live-cd.html](http://www.mindtwist.de/main/openbsd/1-openbsd-live-cd/2-how-to-create-a-custom-open-bsd-live-cd.html)

---

### Post by Haghiri75 on 2012-10-02
> **mips said:**
> [http://www.mindtwist.de/main/openbsd/1-openbsd-live-cd/2-how-to-create-a-custom-open-bsd-live-cd.html](http://www.mindtwist.de/main/openbsd/1-openbsd-live-cd/2-how-to-create-a-custom-open-bsd-live-cd.html)
If you read 1st post , I've explained it's 1st tool that I tested on OpenBSD and it doesn't work :(
I need sysutils or squashfs-tools :|

---

### Post by Haghiri75 on 2012-10-05
Finally I use dd and iso have bin created :D
Thanks.

---

