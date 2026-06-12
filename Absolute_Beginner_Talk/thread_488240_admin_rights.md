---
title: "admin rights"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by timelord29 on 2007-06-29
i have two problems with administrator rights when i only have one account on ubuntu.

1) i set up a dual boot system on two separate hard drives, one running ubuntu fiesty and the other running windows xp. if i download something or write something or whatever on ubuntu, i cant save it or transfer it to the windows drive because it says i dont have admin rights.

2) in the Disk Management utility, when i click on it i get a message saying "There are no filesystems which you are allowed to mount or unmount. Contact your administrator." 

help?

---

### Post by overdrank on 2007-06-29
> **timelord29 said:**
> i have two problems with administrator rights when i only have one account on ubuntu.

1) i set up a dual boot system on two separate hard drives, one running ubuntu fiesty and the other running windows xp. if i download something or write something or whatever on ubuntu, i cant save it or transfer it to the windows drive because it says i dont have admin rights.

2) in the Disk Management utility, when i click on it i get a message saying "There are no filesystems which you are allowed to mount or unmount. Contact your administrator." 

help?

Hi and dealing with windows partitions I believe you need to install ntfs-config, just open the terminal and enter
[PHP]sudo apt-get install ntfs-config[/PHP]
Hope this helps!:popcorn:

---

### Post by milambyr on 2007-06-29
Even with the ntfs-config, in the future if you need to change permissions on a drive, use:
sudo chown -R username:username /media/devicename

Where username is your login name and /media/devicename is the location of your HDD.  That will give you full access to the drive.

---

### Post by hyper_ch on 2007-06-30
you have different options:

(1) Install ext2/3 support in windows --> then you can read/write to your linux partitions
(2) Create a common Fat32 partition --> windows and linux have no problems writing to it
(3) Install the ntfs-3g drivers --> linux can then write to ntfs partitions
(4) get rid of windows and solely use linux --> I'd go for that ;)

---

### Post by timelord29 on 2007-06-30
> **overdrank said:**
> Hi and dealing with windows partitions I believe you need to install ntfs-config, just open the terminal and enter
[PHP]sudo apt-get install ntfs-config[/PHP]
Hope this helps!:popcorn:

i already did this. when i open the NTFS-config, it says enable write support for internal and external disks. i can only check external and that is checked, but i cannot select internal and that is what my other drive is.

---

### Post by timelord29 on 2007-06-30
> **milambyr said:**
> Even with the ntfs-config, in the future if you need to change permissions on a drive, use:
sudo chown -R username:username /media/devicename

Where username is your login name and /media/devicename is the location of your HDD.  That will give you full access to the drive.

it didnt work. it would change the permissions because the drive is set to read-only and the owner is root. does this mean i have to be in root mode in the terminal and then enter this code?

---

### Post by overdrank on 2007-06-30
> **hyper_ch said:**
> you have different options:

(1) Install ext2/3 support in windows --> then you can read/write to your linux partitions
(2) Create a common Fat32 partition --> windows and linux have no problems writing to it
[COLOR="Red"](3) Install the ntfs-3g drivers --> linux can then write to ntfs partitions[/COLOR]
(4) get rid of windows and solely use linux --> I'd go for that ;)

Hi try what is suggested in this post.

---

