---
title: "Howto format an existing Partition and howto see the real size?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-01-11
The disk usage analyzer just tells me a particular device is just 160kb huge.
But this isn't ok, it had an earlyer ubuntu install which i manualy deleted.
So i got 2 question regarding this:

1. How can i see the actual partition size?

2. How can i format the partition or do steps to fix the device size?

Thanks

---

### Post by jvc26 on 2007-01-11
To format the partition, get a GParted cd: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) run it, select the partition you want to get rid of, delete it and repartition with the filesystem you want. Also running Gparted from the Ubuntu Live cd would be able to let you see how big the partitions were and allow you to reformat them.
Il

---

### Post by Wim Sturkenboom on 2007-01-11
1)
sudo fdisk -l
optional you can pass the device (i.e. /dev/hda1)

---

### Post by jvc26 on 2007-01-11
Note the -l is a lower case L (as in for Larry) just in case you get an error/wonder what it is :)
Il

---

### Post by shareMenaPeace on 2007-01-11
Hi, i will try the command

gparted i was able to install with synapyic package manager.

The thing is i manually deleted teh device now i cant see any content but  gparted shows is full.

And i cant unmount it

I need to format i check this command, thanks

---

### Post by Bachstelze on 2007-01-11
Could you please provide a screenshot of the GParted window for the drive ?

---

### Post by shareMenaPeace on 2007-01-11
I tried to unmount but cant .... anyone know how todo this manually?

unmount /dev/sdx ?

---

### Post by jvc26 on 2007-01-11
the unmount command would be
```

sudo umount /dev/DEVICE NAME

```

Have a look here:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)
[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)
For more info on mounting.

Also go to terminal and take a peek at:
```

man mount
man umount

```

Il

---

### Post by Bachstelze on 2007-01-11
The command to unmount a device is *umount*, not *u**n**mount*. You'll need *sudo*, too.

---

### Post by shareMenaPeace on 2007-01-11
Image of gparted

---

### Post by shareMenaPeace on 2007-01-11
Tahnks but the console now tells me after sudo umount /dev/sda6 that the device is busy...any idea?

Well all i want is the sda6 empty....

Thx

---

### Post by jvc26 on 2007-01-11
I'm just wondering... If it is an extended partition does this mean that it will be mounted with the original / drive? In which case all those extended partitions will all be mounted, and you cant unmount them from within the filesystem? Just speculation, but that may cause you issues, in which case booting up from the GParted Live CD will allow you to sort it out as that won't boot your filesystem up.
Il

---

### Post by shareMenaPeace on 2007-01-11
Great idea i going to try this now, thanks.

Will report back :)

---

### Post by jvc26 on 2007-01-11
Remember as with all filesystem altering type things ensure you have a backup of data in case it all goes horribly wrong :)
Il

---

### Post by shareMenaPeace on 2007-01-11
I formated the dev and booted.

During boot ubuntu was not able to mount sda3 extended anymore and the boot halted. 
There was a message about an error log, but i cant find it ....

And i had to start dsl connection now manually.....

Please tell me now where i can find the error log and how i can mount the sda6 again?

Thanks

---

### Post by shareMenaPeace on 2007-01-11
Got the log now

> Log of fsck -C -R -A -a 
Thu Jan 11 18:53:20 2007

fsck 1.39 (29-May-2006)
/dev/sda2: clean, 11/272544 files, 25763/544201 blocks
fsck.ext3: Unable to resolve 'UUID=529b09ba-0750-4dde-baed-19c0fedd5eae'
/dev/sda7: clean, 18/1661376 files, 2270026/3321430 blocks
fsck died with exit status 8

Thu Jan 11 18:53:20 2007

It also says i need to manualy fix this.

Any idea?

---

### Post by shareMenaPeace on 2007-01-11
> **Illuvator said:**
> Remember as with all filesystem altering type things ensure you have a backup of data in case it all goes horribly wrong :)
Il

I must note that i find it not very helpfull of you to give me tips which you obvious aware not very save. And than when problems occur not saying a word.

Cheap

---

### Post by jvc26 on 2007-01-11
> **Illuvator said:**
> I'm just wondering... If it is an extended partition does this mean that it will be mounted with the original / drive? In which case all those extended partitions will all be mounted, and you cant unmount them from within the filesystem? Just speculation, but that may cause you issues, in which case booting up from the GParted Live CD will allow you to sort it out as that won't boot your filesystem up.
Il

Note I did say what I thought was just speculation! As it happens booting from the GParted cd did allow you to format that partition, which was what you were having problems with:
> **shareMenaPeace said:**
> 
Well all i want is the sda6 empty....


As to your issue now, I'm afraid Im not 100% sure on how to solve it, however to level the accusation of 'cheap' at me is a bit harsh, as you asked how you could reformat that partition, and you couldnt do it the other way, the way I suggested worked, the issue is just slightly different now, and I should think resolvable. If I didnt have the faintest of how you could do something I wouldnt have bothered to suggest the solution I did. Also as to backing up your files - thats common sense regardless of how safe/dangerous a procedure is! All things which involve reformatting also should out of common sense involve a backup - as highly unlikely as it is that you would format the wrong partition its not unknown! My lack of response wasnt due to avoiding the issue, merely the fact I'd gone elsewhere to get a bite to eat.

Il

---

### Post by shareMenaPeace on 2007-01-11
Well its ok, i just thought u guide me to the fullest ... np i will fix this maybe with data loose....there is still this windows partition and extended what i need to get rid of anyway :P

---

### Post by jvc26 on 2007-01-11
Hey there, apologies for that - I would have guided you right to the end, but I was more unsure about the next steps: My guess would have been the UUID would have changed with the GParted hence you couldnt have used it you would have to go back to the /dev/sda method to mount the drive, I hope you got it all sorted out :)
Il

---

### Post by shareMenaPeace on 2007-01-11
Thx, got it sorted now, even got rid of the windows NTFS - the complete extended partition.

All i had todo is to modify the fstab and create the new sdaX inside /media/, the fstab exampel is at the other thread.

Thx again!

---

### Post by jvc26 on 2007-01-11
Ah excellent news - I hadnt seen your other post til then. Good to know its a'workin :)
Il

---

