---
title: "grub missing?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by yeheii on 2007-07-09
help.

i think i lost my grub.
i installed feisty last june
and it was running smoothly since.
by the way, win xp is already installed way before
but i left 60Gb unpartitioned and unformatted,
and now i finally decided to partition the 60Gb
by booting through win xp CD.
after creating the partition, i restarted and then grub won't load anymore.
is there anything i can do without reinstalling feisty?

---

### Post by alphane on 2007-07-09
Not particularly helpful response, but I think if you do anything with the WinXP CD that is to do with paritions, it will make itself the default boot option and take contol of the MBR.  

Please correct me if I'm wrong people?

As for fixing this, sorry not sure, just mentioning in case it helps someone else...

---

### Post by into_311 on 2007-07-09
This is correct, using the Windows cd will usually try and re-write your MBR if you are doing a repair. It also llikes to take up your whole hard drive when it installed. It doesn't care that you already have existing linux partitions on the hard drive.

I would recommend you booting up to the Ubuntu Live cd environment again. In which point you should be able to run a repair and fix grub. You didn't delete the ext3 partition that your root filesystem was housed on did you??

---

### Post by UnixAnt on 2007-07-09
Have a look at:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by yeheii on 2007-07-10
yeheii
thanks a lot, man!
 that link was very helpful :)

---

