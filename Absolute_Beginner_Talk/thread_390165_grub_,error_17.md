---
title: "grub ,error 17"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by wannabuntu on 2007-03-21
Hi there,
              I was having problems with my vista(8*&^*^%$) install and now i cant boot into ubuntu:confused:.

I get 'error 17 cannot mount selected partition' when i select from grub.

I foolishly made some changes to my disk (not the 1st time by the way)

now after i run from live cd and run fdisk i get

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10240000    7  HPFS/NTFS
/dev/hda2            1275        4335    24579072    7  HPFS/NTFS
/dev/hda3            4336       10011    45592470    f  W95 Ext'd (LBA)
/dev/hda5            4336        5675    10763264    b  W95 FAT32
/dev/hda6            5676        8501    22699813+  83  Linux
/dev/hda7            8502        9818    10578771   83  Linux
/dev/hda8            9819       10011     1550241   82  Linux swap / Solaris


when i run 'find /boot/grub/menu.lst' i get

(hd0,6)



I've tried 
'root (hd0,6)' and then 'setup (hd0).  Thats how i got my grub back but after that i get error 17


can anyone help me _again_ please?

---

### Post by mikewhatever on 2007-03-21
What were the changes that caused this?

---

### Post by sad_iq on 2007-03-21
I think it should be root (hd0,**5**)...but not sure though...and there is a long list of stuff about grub here: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) ... just take the time to read it!!!

---

### Post by wannabuntu on 2007-03-24
sorry for the late reply.

                               I stupiidly made some changes to my hard disk and added in more partitions.   My linux partition is still there as i can see it when i mount it from live cd. can anyone help ???

---

