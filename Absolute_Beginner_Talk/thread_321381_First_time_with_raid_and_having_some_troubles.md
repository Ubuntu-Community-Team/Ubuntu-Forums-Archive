---
title: "First time with raid and having some troubles"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by TekJunkie2k3 on 2006-12-18
Hi guys. I've recently been playing with ubuntu 6.06 to setup a simple NAS with a computer i took home from work. I got the machine running and samba setup and I decided to add a larger drive when I discovered that the mobo was a Abit BD7-RAID.  Naturally since i'm using this as a NAS for backup I decided to pick up two 320gb drives and hooked them up.  The raid controller is a HPT-372. I setup the drives up in the highpoint bios as a raid-1, but ubunut doesnt see it as one drive, it lists the two seperate drives. I installed dmraid and finally got it to see the raid array, but gParted won't format the drive. I've tried to format the drive in the terminal and it keep getting an error message telling me the drive is busy. Late last night I tried to format the array off of the live cd but i couldnt get dmraid installed to read the partition.  I'm considering trying a software raid-1 setup. Are there any drawbacks to the software raid as opposed t a dedicated controller?

pc specs:
1.8ghz P4
512mb DDR200
40gb WD cavalier
2 x 320gb WD cavalier
geforce 2 mx

Thanks.

---

### Post by Primaris on 2006-12-18
I am a complete newbie to Linux so weigh this reply accordingly.

In the past on XP machines I have fooled around with using software RAID-5.  The RAID works, but is much slower than a hardware RAID-0.  I would expect the same to happen regardless of the operating system since the processor is being tasked when using a software RAID.

---

### Post by chalex on 2006-12-18
Your motherboard has what's known as "fakeraid", that is, all of the logic is implemented in the Windows driver and not in hardware on the motherboard.  That's why the Linux kernel still sees two drives even when you set them to "RAID" in the BIOS.

You should use the Linux software raid through mdadm.  It should be almost as easy as mdadm -C /dev/md0 -l1 -n2 -x0 /dev/sda1 /dev/sdb2 (see man mdadm for details).

Linux software RAID is arguably better than true hardware RAID because you eliminate the RAID controller as a point of failure.  The software RAID usually also has better performance.  Hardware RAID of course wins in higher-end situations, for large arrays, with heavy system load, but in your case, software RAID is best.

---

