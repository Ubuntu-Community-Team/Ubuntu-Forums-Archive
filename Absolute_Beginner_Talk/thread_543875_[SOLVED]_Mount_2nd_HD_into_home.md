---
title: "[SOLVED] Mount 2nd HD into home"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-05
Hi

I have just built my first ubuntu server. I have two disks, an 80Gb and a 500Gb.

I have installed ubuntu on the 80Gb disk (hda1) as follows
1.0 GB    swap
4.0 GB   /
75 GB   /home

what I want to do is mount my 500Gb hard disk somewhere, but I'm not sure where. I'd like to mount it into home, but I'm not sure how.

Thanks.

---

### Post by benerivo on 2007-09-05
Check [this]("http://www.psychocats.net/ubuntu/separatehome")
You  can follow it, but skip the first bit about resizing the partitions as you will not be making a new partition for /home (you'll be using a separate drive).

---

### Post by keymoo on 2007-09-05
Thanks for the reply.

I'd like to utilise the space on hda1 also. I've heard of LVM but not used it - would I need to use LVM to achieve /home across the two drives?

Is that possible to do with my system in its current state?

keymoo

---

### Post by Lycaon on 2007-09-05
Hello keymoo,

I've got a similiar setup with 4 discs. As far as i know, you can NOT mount and empty disk straight to your home directory. It's your home etc blabla.

But you can mount it in a "folder". For example, you can mount the 500 GB disc in /home/storage.

If you would like to achieve that you will have to edit some system files in the terminal.
First the hdd should be reconized by ubuntu, and being mounten in some default dir. Atleast thats the easiest way. 

In your terminal type :
> df

this give you some output similiar to this:
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             25956868    907128  23731208   4% /
varrun                  484848       200    484648   1% /var/run
varlock                 484848         0    484848   0% /var/lock
procbususb              484848        92    484756   1% /proc/bus/usb
udev                    484848        92    484756   1% /dev
devshm                  484848         0    484848   0% /dev/shm
/dev/hda3            124992988 101463240  17180460  86% /DISC1
/dev/hdb1            153834852 145223260    797176 100% /DISC2
/dev/sda1            153834852 142607568   3412868  98% /DISC3
/dev/sdb1            157566568 112444912  37117676  76% /DISC4

As you can see i got 4 discs mounted in the directories /DISC1-4 . 

Look at the first collumn, check for hda1 or sda1 like names. And check if it;s actually 500 GB;) remember the mount point.

After that, write it down or so, we are going to edit the fstab file.
> sudo gedit /etc/fstab

Here we can set custom mount points just cp this and it should work:
> /DISC4/ /home/storage none    bind      0    0

Save the file, and in the terminal type:
> sudo mount -a
This will remount all drives, and your new config;) 

As you can see we mount the DISC4 into the directory /home/storage , now if you go to your directory storage you will be actually writing data on the DISC4 disc.

Im am sorry for the vague explanations and weird sentences but it;s late:)
Hope this is what you had in mind tho.

---

### Post by macogw on 2007-09-05
> **Lycaon said:**
> Hello keymoo,

I've got a similiar setup with 4 discs. As far as i know, you can NOT mount and empty disk straight to your home directory. It's your home etc blabla.

But you can mount it in a "folder". For example, you can mount the 500 GB disc in /home/storage.
You just add an entry in /etc/fstab for the /home dir

---

### Post by benerivo on 2007-09-05
> **keymoo said:**
> Thanks for the reply.

I'd like to utilise the space on hda1 also. I've heard of LVM but not used it - would I need to use LVM to achieve /home across the two drives?

Is that possible to do with my system in its current state?

keymoo

It may be possible (i don't know), but i think you maay be better off resizing (using gparted) your root partition after you have moved /home, so that you have some free space on your 80Gb. Then format it and use it as personal storage or backup of important files (ie. mount the newly formatted partition as /media/backup).

---

### Post by keymoo on 2007-09-06
Thanks I set the system up as follows

hda1 80GB 
sda1 500GB

hda1
/ 4GB
/home 75GB
swap 1GB

sda1
/home/backups 500GB

Seems to work ok.

---

### Post by AusIV4 on 2007-09-06
It may be a bit late, but with as much space as you've got, I think 4 GB for the root partition is a bit lacking. I've got 5 GB and managed to fill it once, leaving my system unbootable. I just ordered a hard drive twice the size of my current one and plan to set my root partition to at least 8 GB.

---

### Post by keymoo on 2007-09-06
> **AusIV4 said:**
> It may be a bit late, but with as much space as you've got, I think 4 GB for the root partition is a bit lacking. I've got 5 GB and managed to fill it once, leaving my system unbootable. I just ordered a hard drive twice the size of my current one and plan to set my root partition to at least 8 GB.


True for a desktop system - but I'm using this as a server with no GUI. I have 76% free space on my root partition with everything that I need installed. AND.. the server is only using 67MB RAM out of 1GB. Lol.

---

