---
title: "USB hard disk on Macbook"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by guj4_n3b3sk4 on 2008-04-19
I own Macbook. I am interested in buying extern USB hard disk. Does Macbook support this? If yes, which hard disk do you recommend me? How clewer it is to keep that disk constantly pluged in and write/read on/from it? I have two OS on Macbook - Tiger and Ubuntu. Can I write and read that USB hard disk from Ubuntu, and how?

Lame questions, but hope I'll get some answers.

Thank You.

---

### Post by dark_harmonics on 2008-04-19
> **guj4_n3b3sk4 said:**
> I own Macbook. I am interested in buying extern USB hard disk. Does Macbook support this? If yes, which hard disk do you recommend me? How clewer it is to keep that disk constantly pluged in and write/read on/from it? I have two OS on Macbook - Tiger and Ubuntu. Can I write and read that USB hard disk from Ubuntu, and how?

Lame questions, but hope I'll get some answers.

Thank You.

I use a macbook pro and also utilize an external 500gb drive. The one i use is a western digital "my book". I actually have an NTFS partition on mine, because i installed a WINPE 2.0 (one of the only cool tools of Vista) boot onto it and use it to backup images from windows computers.
 
As far as being able to read/write from both Ubuntu and Mac. Here is something my searches pulled up on the subject. I will research a little deeper and post results. 

[http://ubuntuforums.org/archive/index.php/t-619909.html](http://ubuntuforums.org/archive/index.php/t-619909.html)

I do know that i have problems booting to my USB drive from my macbook pro. I think it only likes to boot to firewire but im not sure :(



**EDIT**
It seems that read only access to HFS+ and EXT3 from OSX or UBUNTU respectively is achievable without causing problems. You could always divide up your hard drive like this: 235gb EXT3 235GB HFS+ 30GB fat32 and use the fat32 partition to swap your data between the two...

---

