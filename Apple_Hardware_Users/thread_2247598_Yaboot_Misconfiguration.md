---
title: "Yaboot Misconfiguration"
date: 2014-10-09
forum: Apple Hardware Users
---

### Post by estrella-ed on 2014-10-09
My system: Lubuntu 12.04 powerpc 
2 partitions ext4, one partition sda3 is lubuntu located. 
The other partition sda4 is for testing another powerpc distro from time to time. 
So, the issue is that i decided to install debian jessie and lubuntu 14.10 for testing purposes on partition sda4.
So having done that, apparently a new yaboot configuration file was created. 
When installation process was finished, in the next reboot i couldn't choose what linux distro to boot. Yaboot just boot the newer linux kernel from the newer linux distro. Is not like grub2 menu where you can choose what system to start. 
Well, then i was thinking in lubuntu 14.10. 
And i had another partition etx4 sda5 (now sda5 is no more) it was just a temporary place for my testing purposes, so again a new yaboot configuration file was created. 
And in the next reboot after fresh installation i have nothing, black screen with no chance to start tty terminal, no nothing, i mean nothing at all, after yaboot prompt saying loading linux kernel, so lubuntu 14.10 sucks really bad in powerpc mac. 
Then I was depressed for all those time consuming issues workaround with no guarantee of permanent solution, so i just delete sda4 and sda5 where my temporary linux distro was installed. Computer shutdown, and i went to sleep.
In the next morning, My yaboot prompt says:
please wait, loading kernel...
pci@f4000000/ara-6@/@1:5,/boot/vmlinux:no such file or directory.
So i was really happy you know. :mad:
And i look google help for some solution, and i read a lot of good information from debian forums and ubuntu forums.
But so far i still cannot boot to my lubuntu 12.04 session.
So this is where i am right now. Asking for help. :cry:
¿There is any way to replace or create a new yaboot.conf file automatically running some command from terminal in live cd session to recover  default yaboot parameters?
i try sudo ybin from live session but says that there is no yaboot.conf in /etc , but i check and yes it has one yaboot.conf file. 
I really dont want to think in lubuntu 12.04 reinstallation for just a yaboot misconfiguration file. 
 ¿What can i do? 

Pd: i try some command in yaboot prompt to manually loading kernel image.
boot: hd:3,/vmlinux root=/dev/hda3 ro 
can't open device hd:0 

every single command i try:
can't open device hd:0



I will still looking for something else.

---

### Post by bapoumba on 2014-10-12
*Thread moved to **Apple Hardware Users**.*

---

### Post by este.el.paz on 2014-10-12
[https://wiki.ubuntu.com/PowerPCFAQ/#How_do_I_configure_yaboot.conf.3F](https://wiki.ubuntu.com/PowerPCFAQ/#How_do_I_configure_yaboot.conf.3F)

@estrella:

Did you read through the PowerPC wiki as I suggested in the other thread?  If so and it didn't help, probably best to re-install, as indeed 14.10 is pretty rough in PPC units  . . . so far.

e.e.p.

---

