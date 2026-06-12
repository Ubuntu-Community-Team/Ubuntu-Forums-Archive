---
title: "Delete Widows XP without reformat"
date: 2012-12-09
forum: Any Other OS
---

### Post by ramakanta on 2012-12-09
I have one PC having XP loaded . is there any procedure to erase/delete entire hard disk without using xp cd.(means without booting and format)??.
If possible please help me.
thank you.

---

### Post by pullmoll on 2012-12-09
You can use the command line tool **dd** to wipe out any device. To run a command open a terminal (Applications -> Accessories). First be sure which hard disk it is that you want to erase:```
 sudo fdisk -l
``` This should list all disks and their partitions. If you see the *NTFS* partition in the list, you can then take the listed device name (e.g. **/dev/sdb**) for the output file of the dd command like this: ```
sudo dd if=/dev/zero of=/dev/sdb bs=63b
``` The parameters are

if= input file; /dev/zero is a device that delivers 00 bytes
of= output file; the /dev/sdb (replace with the disk device you found in step 1) is the device that is written to
bs= block size; I used 63b which is 63*512 bytes and is usually the logical size of one track on a HDD. You can choose bigger values like 1M, 32M ... (1 mega byte, 32 mega bytes), which may speed up the process.

The dd command returns with an error when the end of the output file is reached, i.e. when it tries to write beyond the end of the HDD. By then the drive should contain nothing but 00 bytes.

[B]Please do not use the command unless you are absolutely sure you want to wipe the disk device. You will loose all your data if you specify the wrong destination device!
[/B]

---

### Post by kiyop on 2012-12-09
:)Boot with any linux live CD/DVD/USB which supports command "shred".

Execute with root privilege,
```
fdisk -l
```or
```
parted -l
```to know the device file name of the HDD which you want to delete all the information saved in, such as /dev/sda or so.

If the device file name is /dev/sda, execute to delete,
```
shred -n 1 -v /dev/sda
```The above will write randomly 1 or 0 once onto whole the area of /dev/sda.

Refer to
```
man shred
```But....
Why did you write :lolflag:
Is it a kind of JOKE?

ADDED at Mon Dec 10 12:50:03 JST 2012;

Thanks Paady Landau to notice that the above ":lolflag:" is in his signature.:)

---

### Post by Paddy Landau on 2012-12-09
> **ramakanta said:**
> is there any procedure to erase/delete entire hard disk...
You don't make clear if you need the drive "shredded" or if you just want to remove Windows in order to install something else.

If you just want to delete the partition, you can boot from a Live CD (as [post=12395769]kiyop said[/post]) and run either Disks or GParted to delete and recreate the partition. Warning: You will lose everything on the hard drive, including your data!

> **kiyop said:**
> Why did you write [LOL]
I think that's in his signature, not the original post.

---

### Post by Mister08 on 2012-12-09
> **Paddy Landau said:**
> You don't make clear if you need the drive "shredded" or if you just want to remove Windows in order to install something else.

If you just want to delete the partition, you can boot from a Live CD (as [post=12395769]kiyop said[/post]) and run either Disks or GParted to delete and recreate the partition. Warning: You will lose everything on the hard drive, including your data!


I think that's in his signature, not the original post.

To add onto this, if you DO need your drive shredded, rather than just deleting the partition; you can use Darik's Boot and Nuke to shred the drive with several different security standards. Just know that it will take hours for even the most basic method to complete. If you attempt to use the Gutmann method, which is theoretically the most secure it will take days to complete

---

### Post by Paddy Landau on 2012-12-10
> **Mister08 said:**
> … if you DO need your drive shredded…
… and you will never use the drive again, just remove it from the computer and take a hammer to it.

---

### Post by mythic97 on 2012-12-11
<Joke>
Put a shotgun to your hard drive 
that should work
</Joke>
Ermm well save all your data to external storage and you will have to reformat

---

