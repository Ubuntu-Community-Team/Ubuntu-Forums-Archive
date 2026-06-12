---
title: "What to do with partitions created ?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by valbowsky on 2007-09-19
I installed ubuntu 7.04 two weeks ago. I'm starting to feel a bit comfortable as everything is working and the transition is going well.  Before the installation, I followed an installation guide from a blog regarding partitioning.  So I kept my windows partition, reduced it to create 2 (ext3) partitions, a swap, a fat 32 partition between windows and linux and the installation process went very smooth. My 2 ext3 partitions were named Ubuntu and HOME (caps).  So I did what I was told to, but now I have no ideas what their purposes are, neither that I can't really add files to them,  It seems that they are empty. I think the guy was saying to create partitions like that in case we want to upgrade to a new version of linux someday, by keeping our main files that way. Now i notice the path to most are my files are home/... (without caps) Any suggestions to what I should do ? One last thing, is there a way to access my partitions without ever being prompted to enter a password ? Thanks for your help .

---

### Post by haricharan on 2007-09-19
while installing you should have specified 
Ubuntu as /
HOME as /home
swap as swap

So if you have your /home partition separate, you can install multiple versions without losing your configuration files.

Can you post your fstab
```
cat /etc/fstab
```

---

### Post by valbowsky on 2007-09-19
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
UUID=0a2e6555-fac2-46ed-b450-1013dfd723e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda12
UUID=e5525c4f-cfb1-42c8-9077-c65035194961 none            swap    sw              0       0
/dev/sdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0

Thank you for responding so quickly (it doesn't look good huh ?)

Terry

---

