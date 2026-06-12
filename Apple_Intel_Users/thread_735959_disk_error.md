---
title: "disk error"
date: 2008-03-26
forum: Apple Intel Users
---

### Post by xstation on 2008-03-26
I am trying a triple boot and having some problems

this is what disk util tells me 

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *149.1 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:       Microsoft Basic Data UNTITLED 1              74.5 Gi    disk0s2
   3:                  Apple_HFS Untitled 1_2            37.0 Gi    disk0s3
   4:                  Apple_HFS Untitled 1_2_2          37.1 Gi    disk0s4

I   would like xp on UNTITLED 1 xp copies the files then reboots I use EFI to point to the partition 2
but i get a disk error?

partition 4 will be used for ubuntu 
partition 3 already has OSX insalled

any suggestions please

xstation

---

### Post by cyberdork33 on 2008-03-26
I don't exactly know what you mean by "use EFI to point to partition 2" but Windows  will probably have issues if it is not  the last partition of the first 4 partitions on the disk anyway.

Why don't you install everything in the typical fashion:
[LIST=1]
[*]EFI
[*]OSX
[*]Ubuntu
[*]Windows
[*](swap is desired)[/LIST]

---

### Post by xstation on 2008-03-26
yes you are correct thankyou

what i did was to create one partition with disk util then installed OSX then 
EFI is now on its own patition 200mb then OSX

so with bootcamp i crested the xp partition inserted the xp disk and it copied the files then rebooted
but still this time EFI did not start at reboot the xp disk started.

what happens is you are asked to press any key to boot from the xp cd which i did not 
AS the files from the cd had alredy been copied to the partition
what happened next was disk error

So i am in the mess that evey time i boot up my mavboot into the xp disk
no sign of EFI

according to xp my disk looks like this:



E: PARTITION 1     (UNKNOWN)   200MB---------------------->THIS IS THE EFI partition
F; PARTITION 2     (UNKNOWN)   80832mb------------------> this is the osx install
unpartitioned space                           128mb
C: Partition 3          (BOOTCAMP) (fat32)   71468MB  (70877MB FREE)

(i am useing my pc labtop just now to send this post)





xstation

---

### Post by cyberdork33 on 2008-03-26
what hardware?

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by xstation on 2008-03-26
please read my last post again as i have edited it

i am on a imac duo 2 core 10.5.2

xstation

---

### Post by cyberdork33 on 2008-03-26
Have you tried holding the Option key at bootup?

You can follow the installation part of the Macbook pages. It will be very close to the same thing until you have to configure hardware. The Macbook Pro page in particular has detailed information for several dual/triple boot setups.

---

### Post by xstation on 2008-03-26
I am not sure if i have a option key what does it look like? ok i know acceptr on my keyboard below alt it does not say option its a sign but cant really describe it)ok it works as he menu key--THANKYOU

i will have a look at the page you suggested.

but what have i done wrong so far do you think?

xstation

---

### Post by cyberdork33 on 2008-03-26
I actually do not know. Windows did not install correctly from the sound of it.

---

### Post by mrsteveman1 on 2008-03-27
If windows installed correctly you should get a menu when you press option at boot, if selecting the windows entry in the boot menu doesn't boot windows, there is something wrong with windows.

Given all the partitioning you have done, i would make sure your mbr and gpt partition tables are in sync, if you don't know how to do that there should be some info on one of the guides posted by cyberdork33.

---

### Post by cyberdork33 on 2008-03-27
you can install rEFIt to sync your tables. You have to boot into OS X to do that.

---

