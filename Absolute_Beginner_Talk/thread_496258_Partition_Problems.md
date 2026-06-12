---
title: "Partition Problems"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Dr Zolygon on 2007-07-08
When i  made the partition for ubuntu i did it as so(keep in mind i had little knowledge of what i was doing).

ext3    mount: media/hda1 85GB
ext3    mount: /  10GB
Linux-Swap   3GB

So my problem is that im running out of room because i am only able to save things to /(which is only 10GB)

I did this because i figured i would be able to write to media/hda1 but i can't seem to get it to work.

So what do i do?

Do resize my root partition or am i able to write to my other ext3 partition.

Thanks in advance.

---

### Post by Moop on 2007-07-08
You probably should have set up the large partition as /home but you can still write to it. It probably just needs to be mounted. Look in your file system for a folder named media. That should be the 2nd partiton.

This tutorial will help you set up the partition so it will automatically mount at boot. 
[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by Dr Zolygon on 2007-07-08
Hi

Thanks for the info although when i go to my second partition all there is is a fold called "lost+found" and it won't let me add or change anything.

Im assuming it is mounted because when i right click it, the only option i have is to unmount it.

Is there anyway to make a partition for /home without reinstalling ubuntu?

I tried using gparted but it would not let me specify the mount.

---

### Post by Moop on 2007-07-09
The lost and found folder is just the trash can. There wouldn't be anything else in there if you can't write to it. 

You can create a home partition after Ubuntu is installed. If it's new install I would just start over but that's just my opinion. 

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Dr Zolygon on 2007-07-09
thanks for the info.

I decided to reinstall and make new partition but i have run into a problem when trying to install.

The partitions i made are:

ext3 / 10GB
ext3 /home 150GB
swap 3GB

When i try to install i get an error during the "creating ext3 file system for /home" that says "Failed to create a file system The ext3 file system creation in partition #3 of IDE1 master (hda) failed."

Im not sure what could be causing the problem. I set the partitions to format so cannot think of what might be wrong.

---

### Post by Moop on 2007-07-09
When you boot from the live cd you will need to unmount those partitions before you can format or change their size. Also the live cd has a partition manager under System/Administration that you can use to delete or manage your partitions.

---

### Post by danbar on 2007-07-09
I have made partitions when installing the latest edition of ubuntu (7.04).  Now I wanted to add another one.  The only problem is that I have to mount it every time I switch on the computer.  Can I mount it once for all as I did with the other partitions during installation?  In the terminal after opening the gparted I found the following message: 

libparted : 1.7.1
automounting disabled


Another problem is that the name given by the computer is disk.  Can I change it's name?

I use dual boot and I have two hard drives.  Thanks for your time.

---

### Post by Moop on 2007-07-09
You can have the partition mount at boot. Check my link in the post a few posts above this. Your partition will show up as a folder in your file system. As far as I know you can name it anything you want.

---

