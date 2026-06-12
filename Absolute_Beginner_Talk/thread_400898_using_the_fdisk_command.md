---
title: "using the fdisk command"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by carverj on 2007-04-04
Hi all. I am using live DSL CD to format a hard drive. I enter sudo fdisk /devl/hda and it says it's cylinders for disk set to 1467, not 1024. Warns me that this may be bad for early LILO. Then I have a list of commands. How do I format teh drive completely?

---

### Post by mojorising on 2007-04-04
Probably the best (at least easiest) way to go about this would be to get the gparted live cd ([http://gparted.sourceforge.net/livecd.php)](http://gparted.sourceforge.net/livecd.php)). It can delete/ create/ resize partitions with many different filesystem types. This CD is great to have around for when you need to do this type of thing.

Of course, if you are doing this to install Ubuntu (and you must be, since this is an Ubuntu forum), you can simply use the Ubuntu installer's built in partitioning components. They work very well and will get the job done in one go without having to run separate utilities and such. 

Mike

---

