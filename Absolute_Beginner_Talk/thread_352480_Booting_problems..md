---
title: "Booting problems."
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Dr. Drone on 2007-02-03
Hello Ubuntu Users.

I just thought of trying a different Linux. So I downloaded the Ubuntu ISO and I burnt it successfully, but it just won't boot. When I load up my PC it just goes into Windows and doesn't boot from Disc, any help would be appreciated.

Thanks.

---

### Post by taurus on 2007-02-03
When you first boot, press F2 or Del key to get into the BIOS.  Then, change the boot order from harddrive first to CD-ROM first.  Save the change and reboot.

---

### Post by Dr. Drone on 2007-02-03
I've tried that already and it didn't work.

---

### Post by reabralop on 2007-02-03
Are you sure you burnt the image to the disk. When I did it I just burned using Nero but didn't burn the image. I then realized that I hadn't burnt the image.

---

### Post by taurus on 2007-02-03
Boot your Windows up and insert the CD into the drive.  Now, do you see a menu popping up regarding Ubuntu or so you only see one big file, .iso, on the CD?  If you see one big file on the CD, you have burned it wrong.  You should have burned it as an image file, not a data file.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Dr. Drone on 2007-02-03
> **reabralop said:**
> Are you sure you burnt the image to the disk. When I did it I just burned using Nero but didn't burn the image. I then realized that I hadn't burnt the image.

Wow, I explored the Disc and it wasn't in there. xD

Burning again.

---

### Post by Dr. Drone on 2007-02-03
Sorry for Double Post, just don't want this thread going dead yet.

Could you explain to me how to do a Dual-Boot? I've got Windows Media Center installed and I've got my Unbuntu Disc but I want to have both and I don't really want to erase anything off my HDD. So if you could tell me how to do a Dual-Boot too that would be very much appreciated.

---

### Post by reabralop on 2007-02-03
I started from scratch, meaning I formatted my drive. Using DBAN, I wiped it clean and created two partitions. I basically split my drive down the middle. I then reinstalled Windows on one partition and Ubuntu on the other. I've read that it's better to do Windows first, don't know why. You can do it from the Ubuntu install without wiping Windows but I only know what I've read here;

[www.psychocats.net/ubuntu/installing](www.psychocats.net/ubuntu/installing)

---

### Post by rogue302 on 2007-02-04
i have the same problem, i burnt the disk and its definatley an image disk then i treid to boot the computer from it but it wouldn't work, i've been into the setup and changed it to boot from the cdrom first but it still doesn't work, what am i doing wrong?:confused:

---

### Post by taurus on 2007-02-04
> **rogue302 said:**
> i have the same problem, i burnt the disk and its definatley an image disk then i treid to boot the computer from it but it wouldn't work, i've been into the setup and changed it to boot from the cdrom first but it still doesn't work, what am i doing wrong?:confused:

An image disk you mean you see a bunch of files and directories on the CD!

---

### Post by rogue302 on 2007-02-04
yes i see a bunch of files and directories

---

### Post by taurus on 2007-02-04
And if you insert that CD into a Windows machine, you should see a Ubuntu menu.  See if you can boot that CD with another machine.  If it boots, then there is something wrong with the boot order of your machine since you said that you have changed the order to CD-ROM first.  May want to double check on that in the BIOS.

---

