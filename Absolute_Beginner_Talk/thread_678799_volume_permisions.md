---
title: "volume permisions"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-26
how can i do the following tasks in nautilus under Ubuntu 7.10?

- rename a volume label
- create new files/folders in a volume outside the user directory

thanks.

---

### Post by Moop on 2008-01-26
You can use ```
sudo nautilus
``` to make changes outside your home directory. It would be a good idea to make backups to any files you want to change.

---

### Post by Raccoon1400 on 2008-01-26
You could also log in as root.
system>admin>login window>security tab and select "allow local system admin login"
go to the welcome screen, enter root for username and then your password.

---

### Post by spydon on 2008-01-26
> **Raccoon1400 said:**
> You could also log in as root.
system>admin>login window>security tab and select "allow local system admin login"
go to the welcome screen, enter root for username and then your password.

This is not a good idea, it is not safe to log in as root, especially if youre new to linux.

If you are going to run nautilus as root do:

```
dpkg nautilus
```

instead of

```
sudo nautilus
```

---

### Post by Matt26 on 2008-01-26
i have run the command 'gksudo nautilus' to access the file browser with root permissions, but i don't see the volumes i am looking for located under Computer (they were recently created under my regular user account).  how can i change the labels from here and add files/folders to these volumes as needed?  thanks.

---

### Post by Moop on 2008-01-26
I'm confused about what you're trying to do. Did you create new partitions and you want to mount them with read-write permissions? 

Maybe this tutorial will help. [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by Matt26 on 2008-01-26
i have installed a new hard drive which i have divided into 2 separate ext3 partitions.  i can view both of these volumes under Computer now, however i can't rename their labels or add files and folders under these volumes in the nautilus graphical file browser- in other words, they show up as '35.3 GB Volume: disk' and '39.2 GB Volume: disk-1' under Computer and i want to change these labels, but i'm not able to since i get an error message whenever i try to, and the option to create new files and folders is greyed out when i go into the volume- so i have started nautilus with root permissions using the command 'gksudo nautilus' in order to change the labels and add my files and folders under the volumes.  now that i have nautilus opened with root permissions, all i can see under Computer is the Filesystem- no signs of the volumes i want to change.

how can i make these changes, and where do i go to make them?

---

### Post by Moop on 2008-01-26
The tutorial I linked to in my last post will guide you through what you want to do. In the future when you want to add partitions, create them with the partition editor and choose a mount point. If you mount them in /media and name them anything you want, you will end up with what you wanted to do.

---

### Post by Matt26 on 2008-01-27
thanks- i think i understand most of that article:)

i took a look in GParted and these volumes are mounting at \media\disk and \media\disk-1

so what i would like to do is to rename these volumes as they are, instead of creating new folders and modifying different files to achieve this- frankly, that sounds like a lot more work than one should have to go though just to rename a volume!

what i am looking for is the equivalent of what Windows allows you to do right from My Computer- right-click on the drive icon, and rename it.

there is a rename option available when you do this under Computer in Ubuntu, but it always gives an error message when i try doing it this way- even when i open nautilus under gksudo- so why is it there if it doesn't work!  that is what i want to be able to do.

---

### Post by MasterJS on 2008-01-27
The rename option is for folders and files only. Ubuntu looks at partitions, not the disk as a whole. Each partition has its own mount point, which I'm not sure if you added. What you need to do is download GParted (i believe its in the repositories, you can search synaptic for it), unmount the disk, and reformat it through GParted, specifying the mount points as /media/THENAMEYOUWANT.

---

### Post by Matt26 on 2008-01-27
i created the volumes originally under gparted, and never seen the option for choosing the mount point- first i have to set the disklabel, which i set to msdos, then i created 2 new partitions on the disk, both ext3, but there was not an option that i saw which would allow me to choose where the mount point should be.. only options for partition type (primary, logical etc) filesystem (i used ext3 for both) and the size of the new partition.  so what am i doing wrong here?

---

