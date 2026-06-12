---
title: "Mounting Windows drives"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by dgub on 2007-02-04
I have installed Edgy and have trying to mount the Win drives. I have searched here and followed the links but they make no sense or logic. Why oh why does it have to be so difficult?

There is an applet, I think in Preferences that allows you to auto mount removeable and optical storage. No why cannot they also add the option to select certain partitions instead of having to go into text mode and use a very primitive text editor that I left years ago in DOS?

I don't mean to run down Linux and we all know what rubbish Windows is under the surface, but the fact is that it is easy to use Win I and can get work done in a simple manner.

Sorry to rant on but having spent the morning getting nowhere and more angy and frustrated. I suppose Linux is just not for me.

---

### Post by taurus on 2007-02-04
Do you still want to know how to mount your Windows partition or do you just want to whine about it?  If you do want to know how, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
(That would be lower case letter l as in larry...)

---

### Post by machoo02 on 2007-02-04
Check out [https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions").  I use method 2 from here (FUSE + ntfs-3g), and it works very well.

Cheers!

---

### Post by dgub on 2007-02-04
> **taurus said:**
> Do you still want to know how to mount your Windows partition or do you just want to whine about it?  If you do want to know how, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
(That would be lower case letter l as in larry...)

This is not a whine but frustration at obscure commands when it should all be so much simpler. I have however come across the following

> 
Mount Partions Automatically
Under Ubuntu, partitions must be 'mounted' before they can be accessed. Mounting is simply the process of telling Ubuntu a certain partition exists, what it is, and where in the filesystem it should go.

In a future release, when [WWW] LiveCD does not mount hard disk partitions (yet) is fixed, this step should be almost automatic. Until then, however, the instructions provided on this page may be used to mount any needed existing data. 


So it seems this is being addressed.

---

### Post by dgub on 2007-02-04
> **machoo02 said:**
> Check out [https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions").  I use method 2 from here (FUSE + ntfs-3g), and it works very well.

Cheers!

Thanks for you helpful reply. I followed your link and ended up here

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

That gave me a script to run and after a reboot all the drives were shown on the desktop. I note in that link that this is set to be built into Ubuntu.

---

