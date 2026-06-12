---
title: "installing a second hd"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by mbele3000 on 2007-12-31
I have a system with a 80gig hd that is running 7.1 and I have a hd that came outta a mac.
Plain and simple how the flip do I install it with zero hassle ?

---

### Post by mattgaunt on 2007-12-31
Well when u install physically in the machine, im assuming ubuntu wont pick it up.

So you'll have to play around with your fstab file (I think thats what it's called) and you'll need to add the new drive and mount it.

I think this is sorta thing you want 

[http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/)

Hope that helps a little

Matt

---

### Post by bunnynuts on 2007-12-31
How I would go about this is the following.

I would connect the drive to the cpu then in the terminal run the following command:

```
sudo fdisk -l 
```

This will show you if the drive is available and the device name (e.g. hdb1, sda1 etc...). Next, in the terminal I would mount it somewhere (I would create a new directory somewhere in my home drive to mount it to). For instance:

```
sudo mount /dev/hdb5 /home/username/newdrivename
```

Next I would cd to /etc and edit the fstab file (I believe the previous post contains a link on how to do this, it is simple though). If you are not comfortable editing this file I would recommend that you first make a backup copy of this file. 

```
sudo cp fstab /home/username/fstabcopy
```

Now that I have written this I did not address the formating of the disk. If you already have a file system that is compatible and the one you want you should be good. Otherwise, let us know and we can help you do that too.

---

