---
title: "mounting ext3 partitions to /home"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by niall111 on 2007-03-17
Aside from a separate drive that ubuntu is installed to, i've formatted my 160gb hard drive to one large ext3 partition.  I currently only have 25gb free in my /home directory, and i want to add the other 160gb partition to the free space in /home.  However, when i use:

/dev/sdb1	/home	ext3	rw,user,auto,exec	0	0


I will get errors all around....  :(  Is this even possible?

---

### Post by kambei on 2007-03-17
> **niall111 said:**
> Aside from a separate drive that ubuntu is installed to, i've formatted my 160gb hard drive to one large ext3 partition.  I currently only have 25gb free in my /home directory, and i want to add the other 160gb partition to the free space in /home.  However, when i use:

/dev/sdb1	/home	ext3	rw,user,auto,exec	0	0


I will get errors all around....  :(  Is this even possible?

If you are looking at combining multiple partitions scattered across multiple drives into a single seamless storage area for /home that you can grown and shrink at will... consider using LVM, which is something you usually setup during your initial install.

If you don't want to backup and re-install Ubuntu, a quick workaround might be to create a subfolder inside your home partition - for example, '/home/extras' - and mount that 160GB ext3 partition to it, and use it for extra storage.

---

### Post by ninjaboy13 on 2007-03-18
It's pretty simple,

First create a folder within your home partition.

For example:

mkdir /home/ninjaboy13/media

Now we edit your /etc/fstab entry with the following, I am assuming you are using a SATA drive.

sudo gedit /etc/fstab

add the following line:

/dev/sdb1      /home/ninjaboy13/media    ext     defaults    0 2

Save and reboot, if you can't write to the folder after you boot back up simply open a terminal and type the following:

sudo chown -R ninjaboy13:ninjaboy13 /home/ninjaboy13/media

And that should be it.

Remember to change the user names where needed in my examples.

nb13

---

### Post by ninjaboy13 on 2007-03-18
Btw, if you are using a ide drive then change the sdb1 to hdb1 for the fstab line.  You may want to do a dmesg | grep hd or dmesg | grep sd to know for sure what your kernal sees your drive as.

nb13

---

### Post by niall111 on 2007-03-18
Ahhh, well it looks like LVM might have done what i want, but there's no way i'm reinstalling after spending the last 2 weeks configuring ubuntu, and i'm only half done!   :)  

i can deal with the other solutions of just creating a new folder for it under my own home directory.  Thanks a lot guys!

---

