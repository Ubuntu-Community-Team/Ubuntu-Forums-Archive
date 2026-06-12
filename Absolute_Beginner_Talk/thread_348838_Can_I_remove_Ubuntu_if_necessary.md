---
title: "Can I remove Ubuntu if necessary?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Karstadt on 2007-01-29
Hello all,

This muist seem to be a weird message to many of you but, before I install Ubuntu 6.06 LTS as a dual boot job alongside Windows XP, can anyone tell me if I can remove it, if necessary, without doing any harm?

If so, how would I do that?

Many thanks and I do hope people will forgive me this cheeky question.

---

### Post by taurus on 2007-01-29
You just reformat the partition where Ubuntu is on and remove GRUB from the MBR so you can boot directly into your XP again.  Again, before you remove Ubuntu, make sure you remove GRUB while log in to XP or you won't be able to boot XP if you remove Ubuntu since GRUB will look for the info in Ubuntu's partition.

---

### Post by shoaibi on 2007-01-29
or if you forget that in the windows recover mode while installing from cd you can use fixmbr command.

---

### Post by CSMatt on 2007-01-29
What if you reformatted but didn't remove GRUB?  Is there any chance of re-gaining access to Windows XP?  If I re-install GRUB will that fix it?

---

### Post by taurus on 2007-01-29
Then GRUB doesn't know what to do since it would look for /boot/grub/menu.lst which is nowhere to be found now that Ubuntu's partition is gone.  Therefore, you need to boot your machine using the XP CD and fix the MBR.

---

### Post by jvc26 on 2007-01-29
Yes, you can delete the partition you installed Ubuntu to and merge it back in with your XP partition, you could reformat it and then install something else there/use it as a separate partition. You will need to replace GRUB with the Windows Bootloader on the MBR (as mentioned before) as the menu.lst is located on your Ubuntu partition which you will have removed.
Il

---

### Post by CSMatt on 2007-01-29
How am I supposed to edit the MBR?

---

### Post by jvc26 on 2007-01-29
If I remember rightly (its been a while since I've used windows stuff) I seem to remember you need to boot your XP cd to fix the MBR with the Windows bootloader.
Il

---

### Post by Karstadt on 2007-02-09
> **taurus said:**
> You just reformat the partition where Ubuntu is on and remove GRUB from the MBR so you can boot directly into your XP again.  Again, before you remove Ubuntu, make sure you remove GRUB while log in to XP or you won't be able to boot XP if you remove Ubuntu since GRUB will look for the info in Ubuntu's partition.

Many thanks to taurus for this reply some time ago.  Unfortunately, I have been unable to come back on it until now.  Thanks also to others who joined in.  Can someone now tell me [a complete newbie to Linux] exactly how I would do that?

I do hope someone can tell me this.

---

### Post by shoaibi on 2007-02-09
well newbie to Linux or Ubuntu?
To start:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
or
[www.ubuntuguide.org](www.ubuntuguide.org)

or i have a book for ubuntu learning and its quite informative, if you need, i can upload it if required!

---

### Post by shareMenaPeace on 2007-02-09
To clean the MBR in dos use

```
fdisk /MBR
```

Easyest way is to use a flopyp for this - startup boot disc.
[http://bootdisk.com/](http://bootdisk.com/)

---

### Post by Karstadt on 2007-02-09
Many thanks for those two links.  The book would be very interesting but how large is it to upload?  If you can do that, it would be exceptionally and wonderfully kind of you.

Many thanks again.

---

### Post by Karstadt on 2007-02-09
shareMenaPeace

That info looks very, very useful.  Very many thanks.

von Karsdtadt

---

### Post by Karstadt on 2007-02-10
My reply ,thanking you for the links seems to have gone adrift so very many thanks again.  The book would be interesting; perhaps you could guide me to it rather than putting yourself to the trouble of uploading all of it? 

Again, many thanks to everyone,

---

### Post by Karstadt on 2007-02-10
Oops - sorry for the mess folks.

---

