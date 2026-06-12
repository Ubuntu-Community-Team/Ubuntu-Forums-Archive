---
title: "How does Ubuntu know about the SWAP partition?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by AnotherMuggle on 2007-08-27
When installing Ubuntu I created a SWAP partition, but I never told Ubuntu that it was there or that it should use the partition as SWAP space.

Does my system know about the SWAP partition just because it is of the right filesystem type?  How do I check if the system knows about the partition and whether it is using it?

---

### Post by LaRoza on 2007-08-27
> **tomkear2006 said:**
> When installing Ubuntu I created a SWAP partition, but I never told Ubuntu that it was there or that it should use the partition as SWAP space.

Does my system know about the SWAP partition just because it is of the right filesystem type?  How do I check if the system knows about the partition and whether it is using it?

It is listed in fstab.

---

### Post by AnotherMuggle on 2007-08-27
> **LaRoza said:**
> It is listed in fstab.

How do I check it and what am I checking for?

---

### Post by Majorix on 2007-08-27
Also you could use
```
free
```

---

### Post by LaRoza on 2007-08-27
> **tomkear2006 said:**
> How do I check it and what am I checking for?

```

sudo vim /etc/fstab

```

If you alter the file, back it up before hand.

It should be listed there.

---

### Post by AnotherMuggle on 2007-08-27
Top quality service again people.  To think I've been paying M$ for service that it hugely inferior...

Will try the commands after work and see where it gets me :)

---

### Post by LaRoza on 2007-08-27
> **tomkear2006 said:**
> Top quality service again people.  To think I've been paying M$ for service that it hugely inferior...

Will try the commands after work and see where it gets me :)

Sorry! If you don't know vim, use GEdit:

```
 
gksudo gedit /etc/fstab

```

If you started Vim, but don't know how to use it, press ":q" to quit. Vim is modal, so you won't be able to edit without switching modes.

---

### Post by snowjm on 2007-08-27
Just in case you accidently do do something to change the file it won't let you close unless you type ":q!" which will quit without saving the changes you made.

---

### Post by schorsch on 2007-08-27
```
swapon -s
```
would be the easiest way ... :-)

---

### Post by AnotherMuggle on 2007-08-27
tom@tom-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2075004     525084    1549920          0      14332     294816
-/+ buffers/cache:     215936    1859068
Swap:            0          0          0


But I have a 2GB swap partition.  How do I make it work?

---

### Post by schorsch on 2007-08-27
We need to know where your swap partition is located. So what is the output of
```
sudo fdisk -l
```

---

### Post by AnotherMuggle on 2007-08-28
Sorry I have been some time in responding, not had a chance to get to my Ubuntu machine.

Output of the command "sudo fdisk -l" is:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3321    26675901    7  HPFS/NTFS
/dev/hda2            3322        6642    26675932+   b  W95 FAT32
/dev/hda3            6643        9703    24587482+  83  Linux
/dev/hda4            9704        9964     2096482+  82  Linux swap / Solaris

---

### Post by schorsch on 2007-08-28
O.K. your swap device seems to be /dev/hda4. If the following command
```
mount | grep hda4
```
does not give any output please type
```
sudo mkswap /dev/hda4
sudo swapon /dev/hda4
free -mt
```
The last command should tell you that you have ~2GB swap available. If so you should add the following line to /etc/fstab
```
/dev/hda4 none swap sw 0 0
```
via 
```
gksudo gedit /etc/fstab
```
so that swap is available after the next reboot. Of course you should reboot if you want to check this ....

---

### Post by notwen on 2007-08-28
install gParted either through Synaptic or CLI
> sudo apt-get install gparted
Then launch gparted
> sudo gparted
Once gParted is open simply locate your swap partition according to your /etc/fstab it should be /dev/hda4, right-click and enable swap and you should be good.  After doing so, test and use the > free command again in a terminal.  Hope this helps.


---EDIT---
Or the method mentioned in the post above. =]

---

### Post by AnotherMuggle on 2007-08-28
Thanks guys, much appreciated.

---

### Post by Xavier Oddmon on 2007-09-05
Thanks, I had a similar problem, where I resized my swap partition (was set to 8 megs originally  for whatever reason) with gparted, but I had to run swapon manually each boot. Edited fstab, fixed the problem without a hitch.

---

