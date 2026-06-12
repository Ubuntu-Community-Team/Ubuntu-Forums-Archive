---
title: "Assemble MDADM"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Aysah on 2008-01-25
Hey guys, I could use some verification on something here.  What I want to do is do a fresh install on Gutsy on my primary drive, not my secondary drive which is the RAID 0 array, in order to clean out any garbage that I may have created by messing around with things in order to learn.  

My primary concern is being able to keep my array being that I put everything in (i only store things in my array, not the home directory) ..I'm not quite too sure about how to reassemble array...

Is the whole process as simple as this?

```

#fresh install of gutsy on /dev/sda2
sudo apt-get update
sudo apt-get install mdadm
sudo gedit /etc/mdadm.conf 
     ##
     DEVICE		/dev/sdb1 /dev/sdc1
     ARRAY		/dev/md0 devices=/dev/sdb1,/dev/sdc1
     ##
sudo mdadm -As /dev/md0
sudo mount /dev/md0 /media/citadel
sudo gedit /etc/fstab
     ## Add this line to it
     /dev/md0 /mnt/citadel ext3 defaults 0 0
     ##
sudo mv /home /media/citadel/home
sudo ln -s /media/citadel/home /home
```

[SIZE="4"]Before I even attempt to do a fresh install I want to make sure that it's going to work.. so umm... Will this work?? lol  :-k[/SIZE]

---

### Post by Bachstelze on 2008-01-25
Personnally, I'd do :

```
sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm.conf
```

That should be all you need (and then add the line to your fstab of course). If it complains about /dev/md0 not existing, do a

```
cd /dev && sudo MAKEDEV md
```

---

### Post by Aysah on 2008-01-25
> **HymnToLife said:**
> Personnally, I'd do :

```
sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm.conf
```

That should be all you need (and then add the line to your fstab of course). If it complains about /dev/md0 not existing, do a

```
cd /dev && sudo MAKEDEV md
```

oh, so I don't actually have to make the mdadm.conf file first?  also do you mind breaking down the last part of that code 'MAKEDEV md'?  Just want to have an understanding rather than blindly doing a copy and paste...  Thanks again for the response  :-)

---

### Post by Bachstelze on 2008-01-25
> **Aysah said:**
> oh, so I don't actually have to make the mdadm.conf file first?

Nope, the second command will do that for you, for example on my RAID-5, it gives :

```
firas@nobue ~ % sudo mdadm --detail --scan
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=08c6d738:2ac668ef:df1d6930:867c6560

```

Then the second part of the command will write that into /etc/mdadm.conf, so you don't have to do it yourself. You can add the DEVICE line if you wish, but it's purely optional.

> **Aysah said:**
> also do you mind breaking down the last part of that code 'MAKEDEV md'?  Just want to have an understanding rather than blindly doing a copy and paste...  Thanks again for the response  :-)

It will just make the device nodes so the kernel will have somewhere to "attach" the RAID device. I'm unsure about whether it's needed when you reassemble an existing RAID, so only run that if it complains about /dev/md0 not existing.

---

### Post by Aysah on 2008-01-25
well thanks again for your help!   =)  I'm going to be sure to try it when I get home..

---

