---
title: "Partitioning problem during instalation"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by Bruno Conde on 2005-11-01
Hello to all,

I'd like to ask for help:

I used have Windows 98, but I formated my HD to install Ubuntu. I went thru the first parts of the installation, but I can't run the partitioning section.

The system always showed the same massage: &#8220;Input/output error during read on /dev/ide/host0/bus0/target0/lun0/disc&#8221;.

So the Ubuntu Forum in Brazil told me to type &#8220;hdparm -d 1 -A 1 -m 16 -u 1 -a 64 /dev/hda&#8221; on the boot. I did, but the problem remains, with the same message.

Can someone help me?

Thanks in advance?

Bruno Conde

P.S. The Ubuntu identified my HD as &#8220;IDE1 principal (hda) &#8211; 4.3 GB VG34323A (4.32 GB)&#8221;.

---

### Post by Kapre on 2005-11-01
[QUOTE=Bruno Conde]Hello to all,

I'd like to ask for help:

I used have Windows 98, but I formated my HD to install Ubuntu. I went thru the first parts of the installation, but I can't run the partitioning section.

The system always showed the same massage: &#8220;Input/output error during read on /dev/ide/host0/bus0/target0/lun0/disc&#8221;.

So the Ubuntu Forum in Brazil told me to type &#8220;hdparm -d 1 -A 1 -m 16 -u 1 -a 64 /dev/hda&#8221; on the boot. I did, but the problem remains, with the same message.

Can someone help me?

Thanks in advance?

Bruno Conde

P.S. The Ubuntu identified my HD as &#8220;IDE1 principal (hda) &#8211; 4.3 GB VG34323A (4.32 GB)&#8221;.[/QUOTE]

Bruno - seems like you got a bad cd. Was this CD downloaded? Would you mind trying downloading it again and burn it on a slower speed? 

K

---

### Post by az on 2005-11-01
You may also have some hardware problems with your disk.  Can you run the live cd and try to check your disk?

---

### Post by jeffreyvergara.NET on 2005-11-01
[QUOTE=azz]You may also have some hardware problems with your disk.  Can you run the live cd and try to check your disk?[/QUOTE]

how can you check your disk for problems using the Live CD? what tool should we use? thanks

---

### Post by Bruno Conde on 2005-11-01
First of all, thank you very much for the attention.
I've subscribed in the Ubuntu site to receive two ubuntu CDs (version 5.04) at home. That's the CDs I'm using. Indeed, I've already changed the CD. It still doesn't work.

I don't believe that I have problems in my HD because I was using Windows 98 normaly till last sunday. And I installed Windows NT yesterday without problems (inclusively, I've created partitions all right).

I'm gonna try to procced to the live CD. So what do I do?

Anyway, is there anything else I can try?

Tks,

Bruno Conde

---

### Post by Kapre on 2005-11-01
[QUOTE=jeffreyvergara.NET]how can you check your disk for problems using the Live CD? what tool should we use? thanks[/QUOTE]

Jeff - on the Breezy release there is a tool there that you can verify the disk integrity (just like the ones in FC - to check if you can install using the CD).

K

---

### Post by az on 2005-11-01
[QUOTE=jeffreyvergara.NET]how can you check your disk for problems using the Live CD? what tool should we use? thanks[/QUOTE]
Well, you can format the partition and look for bad blocks.  Formatting destroys all the data there, of course...


sudo mke2fs -c -c /dev/hda5 #(I use /dev/hda5 as an example.  Use the correct device!)


-c     Check the device for bad blocks before creating the file system.
              If this option is specified twice, then a  slower,  destructive,
              read-write test is used instead of a fast read-only test.

---

