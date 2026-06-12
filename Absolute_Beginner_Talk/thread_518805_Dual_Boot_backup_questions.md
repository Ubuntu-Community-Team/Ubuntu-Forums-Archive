---
title: "Dual Boot backup questions"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by dhopley on 2007-08-06
Dear Forum , 
Hi , I have a dual boot Fiesty Faun and Windows 98SE set up with a spare third disk which I am using as backup . The 98SE system is backed up as a snapshot on to a FAT32 partition (Hdc4 or Windows D:) to an image file on that third disk with Norton Ghost 2003 , which I know from previous usage is a reliable recovery mechanism . The Ubuntu system has been backed up to an Hdc1 partition using the SystemRescueCD and I have two files /hdc1/my-hdb1.000 and /hdc1/my-hdb3.000 both given as MIME type application/octet-stream . My questions are : 
1.does this look reasonable ?
2.am I right in thinking I need not back up the MBR via Partimage as this is lodged on my 98SE drive (Hda1 or Windows C:) 
3.will I need to backup the partition tables as I have backed up to hdc1 and plan to restore the my-hdb* files back to their original partitions  
4.am I right to ignore the SWAP partition ?
Any comments very welcome please , as a newbie I've spent a couple of weeks on the Ubuntu system getting the peripherals to work and so on and would appreciate a little reassurance before I restore from the /Hdc1/  backups , 
Derek

---

### Post by milosz.galazka on 2007-08-06
> **dhopley said:**
> 
1.does this look reasonable ?
2.am I right in thinking I need not back up the MBR via Partimage as this is lodged on my 98SE drive (Hda1 or Windows C:) 
3.will I need to backup the partition tables as I have backed up to hdc1 and plan to restore the my-hdb* files back to their original partitions  
4.am I right to ignore the SWAP partition ?
Any comments very welcome please , as a newbie I've spent a couple of weeks on the Ubuntu system getting the peripherals to work and so on and would appreciate a little reassurance before I restore from the /Hdc1/  backups , 
Derek

1. You are keeping backups on third spare drive so this is good. I don't remember but probably  file size limit on fat32 is 4 Gb. Just remember to check your backups after creation...

2. You are probably using grub or lilo so it's easy to reinstall if you have configuration files.

3. It's always good to keep partition table in safe place. Keeping fdisk output (like output from *fdisk -l /dev/sda*) will be sufficient. 

4. Yeah, nothing interesting there.

---

