---
title: "Vista RAID 0 and Ubuntu on its own disk"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Mr. Mumbles on 2007-11-11
I currently have Vista installed on two 80 gig Sata hard drives in RAID 0. If my understanding is correct, to run a dual boot with both Vista and Ubuntu in RAID 0 it will be a major headache. However, will I have any trouble continuing to run Vista in RAID 0 on the two 80 gig hd's, while giving ubuntu it's very own separate hard drive?

---

### Post by Nano Geek on 2007-11-12
Just going by what I think, you shouldn't. But I don't know a whole lot about RAID so I might be wrong.

---

### Post by Mr. Mumbles on 2007-11-15
Any other opinions?

---

### Post by arcanum on 2007-11-15
This is what I did, more of a hack than anything else due to my growing frustration at my elegant solutions not working . I have two 160GB disks in raid 0 running Vista, and a 320GB disk I've put Ubuntu onto. 

1. Unplug my windows raid hard drives

2. Install Ubuntu on my 320GB drive. Shut down computer.

3. Plug in my sata raid drives again

4. Go into bios and set my Ubuntu drive as first boot priority

5. Boot Ubuntu. Go into terminal and type
[INDENT]sudo gedit /boot/grub/menu.lst[/INDENT]
When it asks for the root password just type in whatever you entered for the account you set up.

6. Add the following at the end of the file:
title       Windows Vista
root       (hd1,0)   //ie. 2nd hard drive, 1st partition (numbers start at 0)
chainloader +1

Now save the file, the next time you boot you will have the option of pressing Esc and booting to Vista. You can also make Vista the default boot option if you prefer, but that's covered elsewhere.


For some reason Ubuntu's installer doesn't properly write to the raided MBR for me, hence this convoluted solution. Theoretically, when you install Ubuntu you should be able to set grub to install to the Ubuntu hardrive, then change your bios to boot from this drive. Then use the installation CD to make changes to the grub menu file, if required. It didn't seem to work for me though (I probably make a mistake somewhere) so I resorted to this ugly hack. Well it's all the same in the end.

---

