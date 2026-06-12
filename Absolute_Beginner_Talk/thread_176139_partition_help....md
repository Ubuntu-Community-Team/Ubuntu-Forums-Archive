---
title: "partition help..."
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by cowley on 2006-05-14
hi, i am wanting to partition my hard disk so i can keep my home files seperate from root should i need to re-install.  this is my current partition layout... 



[ATTACH]9483[/ATTACH]



what would be the best thing to do here?  and once i have partitioned it would i be able just to drag my home files over with no problems?

thanks

simon

---

### Post by steve.horsley on 2006-05-14
You can't repartition the root file systen, so you will have to use a live CD to do the repartitioning. I duggest you download the gparted live CD and use that. There is a graphical partitioner in the Dapper installer, but after some of the things I've seen it to, I wouldn't trust it an inch.

You could do something like this:
Delete the swap partition
delete the extended partition
shrink the hdc1 partition to maybe 10 Gig
make an extended partition that fills the rest of the disk
create a logical swap partition 
create a logical ext3 partition to fill the rest of the disk
Mount both partitions
move the contents of /home to the new home partition
edit /etc/fstab to mount the new partition as /home
reboot

---

### Post by KeyboardJockey on 2006-05-14
I'd be interested on somedata on this too.

I've managed to completely mess up my Ubuntu 5.10 install by using Automatix and generally being ham fisted.

I've got data on my drive but that I do't want to delete but I want to re install Breezy as no matter what I do it's totally messed up.  Basically I've broken it.  I want to re insall Breezy but not sure how to set up the partitioner without losing my data.

Any ideas?

---

### Post by catlett on 2006-05-14
I don't know if you can  divide your partitions without data loss. I would say yes because I have done so but that is not based on any solid technical knowledge.
You can use the Ubuntu Live CD to rub gparted. You're using gparted now so you already know it.
You want 3 partitions at least.
/root        5gb  ext3 (this is  enough because it is just the base system)
/swap      1.17gb   swap( the rule of thumb is twice ram)
/home      20.77gb ext3(the rest should go to home)

I can't tell if you are using a dual boot with windows. If you are you might want to make a  fat32 partition, /data 10gb. This way you can access this from windows and ubuntu. They both read and write to fat32.
You can add even more for security etcm it's your personal choice. Some people make a small /boot 10-50mb. But if grub is already on the mbr you don't really need it.
You should be able to make these partitions without loosing data. All you have to do is make 1 partition. In gparted choose to make a new partition. Make it 20.77gb (or however close it lets you make it) and make it ext3. That is it if you want to keep it simple. There shouldn't be data loss because it is already ext3. I woul;d think it is just dividing the partition into 5gb and 20.77 gb and not formatting it because it is an ext3 already.
The one thing I don't know is how to let the system know that is now you're Home folder. I don't know if it needs some special command to let it know this is THE HOME FOLDER, as opposed to a folder named home in the new partition.

---

### Post by cowley on 2006-05-14
hi, i am completely windows free (wahoo!), i can use gparted to partition then while running ubuntu?  such as you would with partition magic in windows - and just create and resize partitions as required?   i am a little confused by the firsg reply

thanks

simon

---

