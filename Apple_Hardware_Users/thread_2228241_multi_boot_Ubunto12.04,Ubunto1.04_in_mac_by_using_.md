---
title: "multi boot Ubunto12.04,Ubunto1.04 in mac by using rEFIT"
date: 2014-06-06
forum: Apple Hardware Users
---

### Post by flora2 on 2014-06-06
I'm trying to triple boot Ubuntu 12.04, Ubuntu 14.04 and mac OS.  So I installed the two versions of Ubuntu in two partitions on my mac hard drive. When I reboot my system only the latest installed system will show up in the boot menu with the original mac OS. i.e only two system will boot not all the three of them.


Any idea how can I fix the Problem?

Thanks,
Flora

---

### Post by oldfred on 2014-06-06
Moving your thread to the Apple sub-forum where those who know Macs may be able to help.
I do not know Macs nor how refit or rEFInd works.

Are all systems in UEFI boot mode. I think Ubuntu only has one ubuntu folder in the efi partition. But then grub menu should show the other install and let you boot it. Or does rEFInd bypass grub menu?
Did you run this?

sudo update-grub

---

### Post by flora2 on 2014-06-06
Thank you so much for your reply. As you mentioned, I found all the installed systems under the grub menu. I was expecting to see three icons one for each OS but It was only two one for mac and the other one for Ubuntu so not two separate icons Ubuntu. 

Once again, thanks I've been googling and trying different solutions since five hours and non of them has worked for me !!!!!!!!

---

### Post by oldfred on 2014-06-06
I think it creates the icons based on the folders in the efi partition.
Not sure if it would work with a Mac or not, but you can experiment with copying ubuntu folder to add another as ubuntu2 folder and edit its grub.cfg to chain to the second install's grub.
Of course backup entire efi partition before trying things.

---

