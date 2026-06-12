---
title: "installing a second distro"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by maddot on 2007-06-21
okay... after some though, atm i have windows installed on one hard disk. The hard disk i installed ubuntu crashed...because of some nasty error....never it's my fault. Anyway, i reformatted the entire drive. Now, it hold's 60 gigs. I want to set ubuntu to be installed on the slave hard disk using only 30gb. I then intend to install opensuse onto the second have of the hard disk...how do i go about doing that?

---

### Post by aeiah on 2007-06-21
install ubuntu first and create these partitions:

1. create two ext3 primary partitions, one for ubuntu and one for suse, both, say, 12GB*
2. create your swap partition. both OSs can use the same swap. this should be twice the size of your ram
3. create an extended partition taking up the remainder
4. create two ext3 home partitions of equal size, one for each OS

run the ubuntu install , choose to manually configure your partitions and select one of the primary ext3 partitions for root and one of the extended partitions for home. you can choose to mount the suse partitions if you want, perhaps mounting them to /media/suse and /media/susehome in case you need to edit the xorg.conf files etc from within ubuntu

install normally, selecting the normal place for grub

install suse as you normally would. i assume the installation is similar. you can probably make it mount the ubuntu partitions to /media/ubuntu and /media/ubuntuhome for the same reasons as mentioned prior. it'll probably ask you where you want to install grub again, perhaps. if so, just select the same place and it should make a grub menu.lst that has both operating systems in it, plus windows.

make sure your bios is set to boot from your ubuntu / suse hard drive

---

### Post by aeiah on 2007-06-21
* suse may require more space, i dont know. if so, you can take a bit from the ubuntu partition, or the home partition or wherever

---

### Post by maddot on 2007-06-21
that means in theory.. i can have more than 2 distros as well?

---

### Post by maddot on 2007-06-21
also, does the extended partition have to be of equal size to the primary partition? The primary is root right? Then what is extended?

---

