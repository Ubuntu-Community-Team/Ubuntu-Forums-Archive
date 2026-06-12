---
title: "Can I format a windows drive from with in Ubuntu?"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by AJLChase on 2007-09-02
My ubuntu CD is all scratched up and I am not able to partition any drives from with in the installer. I can see the windows drive but can not access it. Is there anyways I can format it and use it with my ubuntu install for more hard drive space?

---

### Post by scxtt on 2007-09-02
what's the output of **sudo fdisk -l**?

---

### Post by jediborger on 2007-09-02
If you have a working Ubuntu installation already, install Gparted from Add/Remove Apps or Synaptic. It'll be listed under System-Administration. Gparted is the same partitioner from the install cd but if you need help with it, just post back or check out the [documentation]("http://gparted.sourceforge.net/documentation.php").

---

### Post by AJLChase on 2007-09-02
Ok, gparted is installed. And I can see my drive. How exactly do I want to partition it? I would like to be able to use all of the hard drive along with my current distro of Ubuntu. I have my OS installed on a 30g HD and would like to have it be able to use my 50g hard drive.

---

### Post by jediborger on 2007-09-02
Ok, good. I should have asked this before, but is all this on one hard drive? If so then you'll right click the windows partition in gparted and select delete. Then you'll right-click and resize your ubuntu partition to take up the free space from the windows partition. Of course these two partitions need to be next to each other for this to work. So if both entries are next to each other in the list then this will work. Otherwise you'll need to move some stuff around. If you're completely lost by what I'm saying just post the output of the following command and we'll go from there.
```
fdisk -l
```
Update: After some of my own tinkering I've found that you need to execute sudo fdisk -l otherwise you get no output.

---

### Post by Duck2006 on 2007-09-02
sudo fdisk -l

---

### Post by AJLChase on 2007-09-02
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        7297    58605120   83  Linux

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4660    37431418+  83  Linux
/dev/hdb2            4661        4865     1646662+   5  Extended
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris
andrew@andrew-desktop:~$ 


  This is what the print out says. Yeah, ive not ever had to do this before so I'm very wet behind the ears.

---

### Post by jediborger on 2007-09-02
Ok so I'm going to venture a guess that the 60 gb hard drive (hda) had windows on it. It looks like you already reformatted it with a linux filesystem. So you can just leave like this and use the space to save files to. This new drive should show up under /media/sda1. If it's not mounted then you'll need to run the following command to mount it.
```
sudo mount /dev/sda1
```

Now you can also choose to move your home directory to the 60 gb volume and leave the 40 gb just for system files. New installation are set up like this with a separate /home partition. Although 40gb is a little overkill for the system files.

Now if you still want to combine the new space with your existing install so it appears as one hard drive then you'll need to set up an lvm volume. This setup is a little more complex and I have little experience with it so bear with me.

So you can leave the hard drive as it is now and just mount hda1 to use the space. Hopefully this helped.

---

### Post by AJLChase on 2007-09-02
Ok, the drive is mounted and I can see it. But it will not allow me to put any files into it what so ever. I can open it up but i can't make any changes to it.

---

### Post by scxtt on 2007-09-02
it's owned by root, which 99.99% of the time isn't the user you should be (if ever) ...

do: sudo chown -R $USER /media/<name of drive>

---

### Post by AJLChase on 2007-09-02
Hey guys. I toyed around with it...and partitioned it as fat32...and it seems that I am able to access it...and ive already mapped my windows pc to the drive to save things to. Should this suffice? Or would it be wiser to do it a different way?

---

### Post by Duck2006 on 2007-09-03
So if you can format it to fat32 you sould be able to format it to ex3 then. Althow fat32 is not bad, you can read/write to the drive in linux and windoze.

---

### Post by southernman on 2007-09-03
If it even came close to a windows OS, I would to this to it first:

```
sudo dd if=/dev/zero of=/dev/hda1
```

press enter and wait for it to wipe the drive out. All it's doing is filling the drive with zeros

60gb should take a little while though not a real long time, I just wiped an 80gb in about two hours. but no worries of trash on the drive afterwards. There is another program called dban (I think that is it) that is used by the government prior to throwing the drive in an incenerator for safely destroying any info contained on them.

YMMV...

---

