---
title: "A smooth question about Synaptics"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by weed-n-linux on 2008-04-06
I just want to change the directory to which my software are installed from /home/me to another ext3 partition . is it possible ? if yes , how ?

---

### Post by mick8985 on 2008-04-06
You can mount a partition wherever you want, so what you would do is just mount the partition to /home/you However most people just mount a partition to /home . I often use symlinks for specific folders i want to store on another partition. So I create a partition mount it to /mnt/storage, then use ln -s to symlink folders which are particularly large like videos and music.

Just search for tutorials on using fstab

---

### Post by Martje_001 on 2008-04-06
Programs are not installed to your home-directory, the are mostly installed to */usr/share* and */usr/bin*. User-setting however are saved in your home-dir.

---

### Post by weed-n-linux on 2008-04-06
> **Martje_001 said:**
> Programs are not installed to your home-directory, the are mostly installed to */usr/share* and */usr/bin*. User-setting however are saved in your home-dir.
you're right only the deb files are installed to my home directory , but /home and /usr are both on the same partition for me, and it doesn't have a lot of free space . the other ext3 partition has lots of space , so i want to use it for my programs .

---

### Post by Martje_001 on 2008-04-06
Oh, I see :)

This can be done fairly easily. Can I see your fstab? And what is the device block of the hard disk with free space (/dev/sdx)?

---

### Post by weed-n-linux on 2008-04-07
[HTML]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f23682ac-d30d-4f5f-99ea-8eba1a7e445b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=abda752b-a669-44eb-8a00-a2f4e8107d5a /Linxian        ext3    defaults        0       2
# /dev/sda7
UUID=0A04B99F04B98E67 /NTFS           ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=a977b5ee-2ae1-11dc-82e5-a91fa0aec1cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0[/HTML]$
this is my Fstab file ,it's the sda6 (Linxian) .
thanks alot.

---

### Post by Martje_001 on 2008-04-07
* Make a backup! *

OK, according to what you just posted;
device block **sda6** with UUID **abda752b-a669-44eb-8a00-a2f4e8107d5a** is mounted on **/Linxian**. Right?

This is what you need to do:
Copy /home and /usr to a directory on sda6. In a terminal:
```
sudo mkdir /Linxian/systemfiles
sudo cp -ap /home /Linxian/systemfiles
sudo cp -ap /usr/ /Linxian/systemfiles
```
Verify that's it all copied, and put this in fstab:
```
/Linxian/systemfiles/usr /usr none defaults,bind 0 0
/Linxian/systemfiles/home /home none defaults,bind 0 0
```
Then (and this is important) boot up from a live-cd and mount **/dev/sda1** by typing in a terminal:
```
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1
```
Then use this to remove all the files of the 'old' hard disk.
```

cd /media/sda1
ls #<-- use this to see if everything is correctly mounted!
cd usr
sudo rm *
sudo rm -r *
cd ..
cd home
sudo rm *
sudo rm -r *
```
What you just did is copy the /usr and /home directory to your empty hard disk. Then, you removed the files from you're full one. Fstab now (re)mounts the folders on the Linxian disk to your root.

All the **sudo rm**'s may look dangerous to you, trust me, it is.

If you have questions, please post them before doing all this! ;)

---

### Post by weed-n-linux on 2008-04-07
but the problem is that my cd drive isn't working , any other way to do it ? i have Gparted BTW .

---

### Post by Martje_001 on 2008-04-08
You can do the live-cd-thing also from your existing install. Then it would be:
```
cd /
cd usr
sudo rm *
sudo rm -r *
cd ..
cd home
sudo rm *
sudo rm -r *
```
After that you have to do a 'hard reset'. However, this is a bit more risky.

---

### Post by Martje_001 on 2008-04-08
Make sure you have a rescue system ready, in case it goes wrong and you want to ask something here. And it should be smart if you only copy (and delete) your /home first and after that (testing and verifying that everything works), your /usr.

Good Luck!

---

