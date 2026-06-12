---
title: "External Harddrive"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-23
I have an external harddrive. 
Its a NTFS. When I put it in via USB. Ubuntu sees it but says it cannot open it because its an NTFS file system. 

How can I get it to read it?
Do I have to format it to FAT32?

---

### Post by jan quark on 2008-03-23
try this 

```
sudo apt-get install ntfs-3g ntfsprogs
```
this will install essential packages for the handling of ntfs formatted partitions

---

### Post by Tom--d on 2008-03-23
Still the same.

This is what is shown on Computer...

---

### Post by iansane on 2008-03-23
after installing ntfs3-g did you run it to set up a mount point in fstab?

---

### Post by Tom--d on 2008-03-23
Er.. how do I do that?

---

### Post by iansane on 2008-03-23
well the app is somewhere in the application menu, (accesories or system tools). Sorry can't say for sure right now, because I'm on a live CD. (problems of my own.)

As for the fstab entry, In terminal type:

```
 sudo gedit /etc/fstab 
```

It should show the entries for your cd drives and any internal drives so you can look at them to make it make sense.

Heres an example (my external)

I created a directory in the media folder and gave it a name (bu1)
then in the fstab file, here's the entry:

dev/sde media/bu1 noauto,force 0 0

noauto tells it not to auto mount when you plug it in or turn it on and force tells it to force a mount when you mount it so you might want to leave that out and you might want to replace noauto with auto so it will auto mount. sde is the drive.There is a command to run to tell you the drives but I don't remember it. The problem with this that I have is that when the drive is on at boot up the system mounts it anyway as "disk" and then I can't get to it and can't mount it to /media/bu1 so it has to be off when the system boots for this to work.

To mount it, do alt+F2 and type sudo mount /media/bu1 and check the box to run in terminal. I'm sure there's an easier method but this worked for me.

---

### Post by Bryab7675 on 2008-03-23
I ran into this problem also.
Plug the hard drive back into a windows computer.  Make sure you can access the hard drive.  Click on the safely remove hardware icon in the lower right task bar.  Windows will then till it is safe to remove your hardware.  Unplug it from windows, and plug it back into Ubuntu and you should be ready to go.
Bryan

---

### Post by iansane on 2008-03-23
Not sure but I had the same problem once. Something to do with unsafe removal leaving it in a unmountable state. I think what fixed it was restarting  system with drive turned on and then unmounting disk, turn it off then restart system, turn drive back on, then mount to media folder. I'm still confused by it, somewhat. I thought that was what the "force" option is for in the fstab entry. Maybe you should wait for a second or third opinion from someone else here though, just to make sure if I'm confusing the matter.

---

### Post by teryowen on 2008-03-23
or you can force the mount by going into sudo su (not sure why just sudo doesnt work)

but do this in terminal

sudo su
mount /dev/the_device1 /media/mount_point

where the_device1 is your device and mount_point is the folder to mount to.

---

### Post by gfg on 2008-03-23
Hi! If you have ntfsprogs installed you can solve this by typing
 ```
ntfsfix /dev/sdb1
```

I had the same problem and this solved it. What it does, I believe, is that it runs the same check that windows sometimes does when it starts up, and fixes any errors it finds.

---

