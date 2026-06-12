---
title: "noob w/?'s"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by yotadriver on 2007-12-08
hello all, new guy here..... i have a few questions i haven't found answers to browsing the forums.

 1) i have Ubuntu installed on a maxtor PATA 120 gig HD but i am unable to find my WD 320 gig SATA drive. windows recognized it and when i unplugged my maxtor drive and booted from the Ubuntu cd it could see the WD drive. any assistance would be great!

2) when i first installed Ubuntu i noticed a cool effect when a window was closed but when i went to restricted drivers manager and installed the graphics driver that effect went away. when i go to visual effects its is set to none. when i change it it says "no composite extension is not available". how can i correct this? i have a ATI 9800 pro video card.

Thanks in advance for any assistance.:)

---

### Post by Martje_001 on 2007-12-08
> **yotadriver said:**
> 2) when i first installed Ubuntu i noticed a cool effect when a window was closed but when i went to restricted drivers manager and installed the graphics driver that effect went away. when i go to visual effects its is set to none. when i change it it says "no composite extension is not available". how can i correct this? i have a ATI 9800 pro video card.
Don't install the closed-source video drivers from Ati (maby in next version of Ubuntu).

---

### Post by astoltz on 2007-12-08
To help with question 1, would you post the contents of your /etc/fstab file?  From a terminal, enter the command:```
cat /etc/fstab
```
For, question 2, the ATI driver that currently comes with Gutsy needs an extra "layer" to be able to run those effects.  It's called xserver-xgl.  You should probably search around a little to find some more info as I can't offer much more than that.  The drivers that Martje_001 is referring to are new and while they don't require xserver-xgl, they are not as easy to install.

---

### Post by meborc on 2007-12-08
to help even more with q1, do "sudo fdisk -l" in the terminal to see what partitions are visible

---

### Post by thelatinist on 2007-12-08
Could it be something as simple as master/slave jumpers?

---

### Post by yotadriver on 2007-12-08
ok. i changed the jumper on the Pata driver from CS to salve so knowwhen i boot i have the option to boot windows which works. however, when i boot Ubuntu i see a screen saying something about a logical block 0 and it just adds another line of the same thing everyfew minutes. when i disconnect the SATA drive i can boot Ubuntu again fine. is this an MBR issue? thanks for the replies so far

---

### Post by astoltz on 2007-12-08
Just to clarify, both Windows and Ubuntu are installed on the PATA drive?  Not sure that changing the jumper on the PATA drive would help at all with the SATA drive.  I also don't think it's a MBR issue since Windows is booting OK.  I'd guess that since you changed the jumper, the drive is getting ID'ed by the system differently causing Grub to look in the wrong place when booting Ubuntu.

---

