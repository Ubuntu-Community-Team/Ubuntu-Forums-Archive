---
title: "Formating my NTFS drive to something else?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by hironez on 2008-03-30
Hello everyone!

I have installed Ubuntu now. When I want to open my slave drive I get a message that I can't mount the volume.

When I look at the details of the warning message it says following: (translating to english)

Hibernated non-system partition, refused to mount. Failed to mount '//hdb1': The operation is not allowed The NFTS partition is hibernated. Please resume and shutdown Windows properly, so mounting could be done safely.

P.S  I have Ntfs system on that drive from previews windows. I have runned Ubuntu for a couple of months without figuring out how to format and transform the drive into another system than NTFS. I don't plan to use Windows on this computer. But I want to change it to something compatible for linux and format the drive.

Thankful for instructional answears. I am desperate to get this to work properly. =P
I will do my best to do any clarifications if needed! ;)

---

### Post by Rocket2DMn on 2008-03-30
If you just want to erase everything on the drive and don't need to recover anything, you can install and run GParted from within Ubuntu
```
sudo apt-get install gparted
``` then go to System->Administration->Partition Editor and do whatever you want to the drive.
You can't modify partitions that are mounted, like you root partition, but you can deal with this drive :)
You will probably want to use the ext3 filesystem on the drive, this is default in linux.

---

### Post by hironez on 2008-03-30
Thank you very much. :popcorn: I really enjoy the apt-get function. Now that I have the program and can run it. Must I delete the hdb and then reinstall it in some way? or can I just right-klick and change the system? However that is what I did. And my system don't see the drive anymore. :/

---

### Post by Inxsible on 2008-03-30
No simply select the slave drive in GParted and then select format. You can then specify the filesystem you want on it. If you want a linux filesystem, select ext3

---

### Post by Rocket2DMn on 2008-03-30
It is easiest to delete all the partitions on the drive so you are left with unallocated space, then just format that however you see fit :)

---

### Post by Inxsible on 2008-03-30
Just make sure you select the correct drive though. Do not format your main drive where your OS is installed :)

---

### Post by Rocket2DMn on 2008-03-30
> **Inxsible said:**
> Just make sure you select the correct drive though. Do not format your main drive where your OS is installed :)

Hehe, always a great call, esp. if you are using the LiveCD or the [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/"), but you can't format your root partition from within Ubuntu because it is mounted.  Another advantage of formatting drives through your normal install.

---

### Post by Inxsible on 2008-03-30
> **Rocket2DMn said:**
> Hehe, always a great call, esp. if you are using the LiveCD or the [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/"), but you can't format your root partition from within Ubuntu because it is mounted.  Another advantage of formatting drives through your normal install.True. but you could still mistakenly format your some other partition(if you have a separate one) and that in itself could be quite a headache.
As they say, Prevention is better than cure. :)

---

### Post by Rocket2DMn on 2008-03-30
If your /home partition is unmounted, yes.  Definitely better safe than sorry!

---

### Post by hironez on 2008-03-30
Ok I have removed the hdb and formated it again. Everything is working so far. thank you! :P How do I mount the drive?

---

### Post by Rocket2DMn on 2008-03-30
You're going to want to add an fstab entry for it.  So say you have one partition on it called hdb1 and it's ext3 formatted.  You don't have to call the mountpoint "sdb1" under /media, but I am for convenience.
```
sudo mkdir /media/sdb1
gksudo gedit /etc/fstab
```
Add the line
```
/dev/sdb1 /media/sdb1 ext3 defaults 0 0
```
Save and close, then run
```
sudo mount -a
```
If everything is good, it will just return to the next line.  If you have errors, post them here.  Now you need to to own the directory and its contents (though there should be none yet)
```
sudo chown -R yourusername:yourusername /media/sdb1
```
Now whenever you boot the computer, the partition will be mounted there, and you won't need to chown anything, it only needs to be done this once.

You can find more information about mounting here: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by hironez on 2008-03-30
> **Rocket2DMn said:**
> You're going to want to add an fstab entry for it.  So say you have one partition on it called hdb1 and it's ext3 formatted.  You don't have to call the mountpoint "sdb1" under /media, but I am for convenience.
```
sudo mkdir /media/sdb1
gksudo gedit /etc/fstab
```
Add the line
```
/dev/sdb1 /media/sdb1 ext3 defaults 0 0
```
Save and close, then run
```
sudo mount -a
```
If everything is good, it will just return to the next line.  If you have errors, post them here.  Now you need to to own the directory and its contents (though there should be none yet)
```
sudo chown -R yourusername:yourusername /media/sdb1
```
Now whenever you boot the computer, the partition will be mounted there, and you won't need to chown anything, it only needs to be done this once.

You can find more information about mounting here: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Ok but where in fstab should I write "/dev/sdb1 /media/sdb1 ext3 defaults 0 0"? I ask because it didn't work. I get the message (in swedish)"mount: specialenheten /dev/sdb1 finns inte" in the terminal. It says that it doesn't exist.

---

### Post by Inxsible on 2008-03-30
You have to create a folder called sbd1 under /media
```
sudo mkdir /media/sdb1
```Then it will work. Make sure you use the same name in both places tho.

---

### Post by hironez on 2008-03-30
I can't make the directory because "the file already exists"? I typed exactly as instructed. :S

---

### Post by hironez on 2008-03-30
The directory is there but I can't execute any other of the commands. That's what I meant. Does it really matter where you type "/dev/sdb1	/media/sdb1	ext3	defaults	0	0" in fstab?

---

### Post by Inxsible on 2008-03-30
Can you post the output of this command```
sudo fdisk -l
``` that is a lowercase L. and no it does not matter where you have it in the fstab

---

### Post by hironez on 2008-03-30
Disk /dev/hda: 82,3 GB, 82348277760 byte
255 huvuden, 63 sektorer/spår, 10011 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x2fea2fe9

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1   *           1        9634    77385073+  83  Linux
/dev/hda2            9635       10011     3028252+   5  Utökad
/dev/hda5            9635       10011     3028221   82  Linux växling / Solaris

Disk /dev/hdb: 250,0 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xdfbf69bb

    Enhet Start     Början        Slut     Block    Id  System
/dev/hdb1               1       30401   244196001   83  Linux

---

### Post by hironez on 2008-03-30
Oops I forgot to say that the output is in Swedish. :D

---

### Post by Rocket2DMn on 2008-03-30
Looks like you want to be using /dev/hdb1 instead of /dev/sdb1 - I just used that as an example.  Try that.  If it doesn't work, post fstab
```
cat /etc/fstab
```

---

### Post by hironez on 2008-03-30
Ok I tried that too and it didn't work.

---

### Post by hironez on 2008-03-30
Ok I discovered that I forgot to change to hdb1 on one place in that file. Thank you everybody! Now it is working! =D:guitar:

---

