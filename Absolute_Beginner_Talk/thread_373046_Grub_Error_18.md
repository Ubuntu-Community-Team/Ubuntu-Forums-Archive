---
title: "Grub Error 18"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by castoroil97 on 2007-02-28
installed 6.10 from the live cd.  Once it reboots grub 1.5 starts then all I get is "Error 18"

I REALLY do not want to go back to Windoze.

Thank You

My system is about 8 years old.  Aopen mainboard. PIII-450. Runs the live cd beautiful, except it can't do my sound blaster awe 64 card, but at the moment it is not important.  However if you know how to get that working, that would be kool too.

---

### Post by rccharles on 2007-02-28
> **castoroil97 said:**
> installed 6.10 from the live cd.  Once it reboots grub 1.5 starts then all I get is "Error 18"


I found this post by Buffalo Soldier's:

Buffalo Soldier's Avatar 	
Buffalo Soldier Buffalo Soldier is offline
Ubuntu Master Roaster
	  	
Join Date: Nov 2004
Location: Kuala Lumpur, Malaysia
Beans: 1,232
Ubuntu 6.10 Edgy User
Send Message via Jabber to Buffalo Soldier
Re: Error 18
Hope you won't mind telling us more about your installation:

- Did you use the whole harddisk for Ubuntu? Or are you dual booting with Windows?
- During installation, the installer asked whether you would like to install GRUB at MBR. What did you choose?
- How big is your harddisk and how old is your computer?

Refering to the GRUB Manual at [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

It states that "Error 18" means,

Quote:
Selected cylinder exceeds maximum supported by BIOS.

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).
If you're comfortable with changing BIOS settings, you could check harddisk mode. If it's LBA or AUTO try changing it to NORMAL.

==================

For a drive greater than 8gig, you could repartition your harddrive so the first partition is 8gig, put the home partition on the second partition, put swap on third.


Robert

---

### Post by castoroil97 on 2007-03-01
Thank you for your reply.

I did discover that as well.

to answer your questions--
- Did you use the whole harddisk for Ubuntu? YES

- During installation, the installer asked whether you would like to install GRUB at MBR. What did you choose? INSTALLED AT MBR
- How big is your harddisk and how old is your computer? 122 GB

I changed the bios setting so it now reads 122 GB

I had used a disk manager before and it did not matter what the bios said.  When I installed UBUNTU it wiped that out and gave me the problem.

I adjusted the bios correctly and IT WORKED!!!!!
:lolflag: 

I can finally turn down the empire and Darth Bill

:-D 

thanks again for the reply!!

---

