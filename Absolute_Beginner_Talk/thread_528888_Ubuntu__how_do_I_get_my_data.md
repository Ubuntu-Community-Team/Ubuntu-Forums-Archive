---
title: "Ubuntu ****** how do I get my data?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Cirion75 on 2007-08-18
Now my Ubuntu does not boot, and I have tried lots of **** with no luck... Now I just want to dump my data to my NAS and reinstall the drive.

HOW?

I've tried using the live CD and connected to my NAS, but I have no permission to copy my files. I also partitioned my HD and installed Ubuntu again, and that boots... But I still have no permission to copy my old files.

How do I get permission to my data on a Ext3 partition? I can se the drive, and the folders, but most of them are locked and I cant copy them.

If you are thinking of helping me get that old partition to boot, I cant do that.... I have tried, dont remember the errors and i ****** the boot files even further so I dont have that option in my grub menu any more.

---

### Post by pbwalker on 2007-08-18
can you boot into rescue mode?

---

### Post by wirelessmonkey on 2007-08-18
in situations where you don't have permissions, _**sudo**_ is your very best friend.

---

### Post by bodhi.zazen on 2007-08-18
Either use sudo as suggested by wirelessmonkey

Or if you want a graphical interface, ```
gksu nautilus
```

Basic permissions : [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

You also understand you need to mount the old hard drive before you can copy the data ?

---

### Post by amazingtaters on 2007-08-18
Is it just your bootloader that is not working? If so, try burning a SuperGrub cd and boot from that to reinstall grub.

---

### Post by Cirion75 on 2007-08-18
It's the GUI that is not booting so I tried to reconfigure x and followed the wizard, not possible for me to get that to work:(

On the live CD, the drives pop up.. I have no need for mounting them, just want read access.

---

### Post by Cirion75 on 2007-08-18
gksudo nautilus could work... But I dont see my drives there... Do I need to mount? How? I'm still on the live CD.

---

### Post by amazingtaters on 2007-08-18
> **Cirion75 said:**
> It's the GUI that is not booting so I tried to reconfigure x and followed the wizard, not possible for me to get that to work:(

On the live CD, the drives pop up.. I have no need for mounting them, just want read access.

You can get read access lemme look and find the console stuff you need.

---

### Post by bodhi.zazen on 2007-08-18
To munt your partition :

sudo mount /dev/hdax /mnt

or 

sudo mount /dev/sdax /mnt

If you need more then 1 partition mounted, you will need to make mount points

sudo mkdir /media/drive 1 /media/drive2
sudo mount /dev/hda1 /media/drive1
sudo mount /dev/hda2 /media/drive 2

etc

then gksu nautilus and navigate to /media

---

### Post by Cirion75 on 2007-08-18
mount: special device /dev/hdax does not exits
mount: special device /dev/sdax does not exits
mount: special device /dev/hda1 does not exits
mount: special device /dev/sda1 does not exits
mount: special device /dev/sda2 does not exits
mount: special device /dev/sda2 does not exits

I have tried unmounting the drives, and I still get the same message.
Is there no way to get read access to a ext3 drive?!?

---

### Post by Cirion75 on 2007-08-18
My drive has 3 partitions, one NTFS with windows and 2 Ext3... There used to be one, but since I was not able to copy out my stuff I tried partitioning the drive and installed ubuntu on the third partition. Still not able to read it... Well, I can read something, but I'm missing permissions on most of the drive.

---

### Post by bodhi.zazen on 2007-08-19
Well you need to know your partitions.

To list them in a terminal enter this command : ```
sudo fdisk -l
```

Once they are mounted, you can use the previous commands I gave you. You might be best with ```
gksu nautilus
```

---

### Post by Cirion75 on 2007-08-19
My 2 ext3 partisions where named sda3 and sda4...

So I mounted sda3 and opened nautilus with gksu and tried copying my home folder...

ERROR WHILE COPYING:
"/mnt/home/...db4f89.png" cannot be copied because you do not have permissions to read it.

What now?

---

### Post by Cirion75 on 2007-08-19
Well now I was able to rightclick my home folder and set read & write access permissions, but when I copy the entire folder, there are still lots of files I have no access to. I have to press skip over and over again..

One example, a file called googleearth. I t has a an arrow so it looks like a shortcut, and it has a red X and a Lock so I know I cannot read it. When I rightclick it an go into permissions it is in group NTFS (not root like the others) and Access is Read and write on Owner, Group and Others. 

Since that file is a shortcut, I dont need it at all. But just wondering why that file didnt change permissions like the others. And if it is on a Ext3 partition why is it in group ntfs?

At least now  I can read out my most important folders :)

---

