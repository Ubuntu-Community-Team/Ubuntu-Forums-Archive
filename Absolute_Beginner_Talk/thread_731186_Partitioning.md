---
title: "Partitioning"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by hvacr on 2008-03-21
I am setting up my laptop that has a 100 gig drive. I want to set up one partition as / and one as swap. All is ok up to that point. I want a third partition for my downloads. I am having a problem setting a mounting point. What should the mounting point be called in order for ubuntu to see it after the installation.

---

### Post by Nikhil Gohil on 2008-03-21
before(during) the installation, ubuntu asks for a mount point for your home drive("/"). do you mean that?

---

### Post by hvacr on 2008-03-21
nope, the home and swap files are ok. I want to make a third partition, thats the one I am having probs with. I have tried/download, but after ubuntu is installed, it does not see that partition.

---

### Post by Nikhil Gohil on 2008-03-21
do you already have ubuntu installed? if so go to system, preferences , hardware information and see if you partition is listed. if so, go to the advanced tab and check the values of volume.is_mounted & volume.mount_point.

---

### Post by bodhi.zazen on 2008-03-21
You will need to manually add the new partition to fstab.

The default location is /media , but you can use any location yuo like.

```
sudo mkdir /media/downloads
```

List your partitions with ```
sudo blkid
```

```
gksu gedit /etc/fstab
```

Add a line for your new partition, get the uuid form the bklid command

> UUID=xxx.yyy.zzz /media/downloads defaults 0 2

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by ayenack on 2008-03-21
Edit: Miss read the question. Bellow is null.

/ (Will be your root partition)
/home (will be your home partition)
and your swap will be set by you at install.

I would have a 10GIG / (root) partition. 1GIG for swap (just in case) and the rest for home. Then within your your home folder you can add a folder called downloads and direct all downloads to that. 

If you want to have a totally separate partition for your downloads then add /downloads during the partitioning stage of setup. After you boot the /downloads partition will be owned by root so you'll have to change that by doing something like this.

**sudo chown YOUR_USER_NAME_HERE:YOUR_USER_NAME_HERE -R /dev/hda3** (Where /dev/hda3 is the partition you want to use for the downloads.)

To list the drives/partitions do this.

**sudo fdisk -l**

I would advise adding the downloads folder in your home folder rather than setting up a totally separate partition for downloads. It's easier and less risk of messing things up. If you need to share the folder you can do so by simply changing the permissions on the folder by right clicking it.

---

### Post by bodhi.zazen on 2008-03-21
You should NOT change the ownership / permissions of the device (/dev/sdxy) but rather the mount point with the partition mounted (/media/downloads).

---

