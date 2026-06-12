---
title: "change home location"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by spadhawk on 2008-01-03
i installed Ubuntu duel boot with windows awile ago now iv gotten rid of widows and hava a free partiotion that is large i would like to put my home folder on the partition how could i do this

---

### Post by forestpixie on 2008-01-03
there is some information on psychocats site on that 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by taurus on 2008-01-03
Somebody asked a similar question (was that you) not that long ago but check out this link then, [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome).

---

### Post by spadhawk on 2008-01-03
i dont unnderstand that guide like i have the partition and now i want to us t a my home but i dont under stand what to do 
lol u both gave me the same guide

---

### Post by joe.turion64x2 on 2008-01-03
You don't need to reallocate your /home directory to use that free space. You can simply create a new Linux partition out of it and mount it in your home user directory.

Here are the steps you may need to follow in case you want to follow that procedure.

1.- Open Gparted (it should be in the menus).
2.- Create an ext3 partition out of the free space (Gparted is an asy GUI, just be careful to don't mess with already existent Linux partitions; trust me, you'll find your way in Gparted). If Gparted is not installed you can install it with Synaptic.
3.- Take note of the name your new partition has (something as /dev/sda1).
4.- Create a new directory in your user home directory (something as storage).
5.- Edit the fstab file to make the system aware of the new partition:
> sudo gedit /etc/fstab
and add a line referring to your new partition and mount point. Supposing your new partition is an **ext3**, it is called **/dev/sda1** and you want to mount it in a directory called **storage** under your home directory then add the following line:
> /dev/sda1          /home/user/storage       ext3      defaults    0   0
where user must be your user name.
6.- Give permissions to your new directory:
> sudo chown -R **user** /home/**user**/storage
where user is your user name.
7.-> sudo mount -a to mount your new partition and you are done.

Joe.

---

### Post by philinux on 2008-01-03
Post the output of [FONT="Courier New"]sudo fdisk -l[/FONT]

Thats a small L.

The above poster is correct .

---

