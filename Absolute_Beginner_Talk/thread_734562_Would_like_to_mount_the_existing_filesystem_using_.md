---
title: "Would like to mount the existing filesystem using uninstalled ubuntu"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by imageburn on 2008-03-24
I will be using the "golive" version of Ubuntu, 7.10 to be specific, to mount and access the files on an existing hard drive;the filesystem on the hard drive is an older Ubuntu install that has a boot issue. Boot issue notwithstanding, how can I mount and use (GIMP, etc...) those files on my hard drive? I haven't used a terminal in over a year so please be specific ; P

---

### Post by Rocket2DMn on 2008-03-24
You need to get the partition from
```
sudo fdisk -l
```
Create a mountpoint (of your preference)
```
sudo mkdir /media/*your_mount_point*
```
Then mount
```
sudo mount -t ext3 /dev/*device_num* /media/*your_mount_point*
```
where /dev/*device_num* is something like /dev/sda1

---

### Post by imageburn on 2008-03-24
Thx for the response Rocket, but the terminal says that the device does not exist, and this is under several names('hda1', 'hda', 'sda1', etc...). Is this now a hardware issue?

---

### Post by Rocket2DMn on 2008-03-24
I don't understand, it has to exist if it was listed under 
```
sudo fdisk -l
```
-That's a lowercase L, by the way.  You can't just go guessing at the device, you have to check where the device is using that command.  Perhaps you can show me some screenshots and/or terminal output, it's difficult to help if I don't have structured feedback from the stuff you're trying.
Is your golive distro a LiveCD or an installed linux?
When you do get it mounted, you will have to own the contents, so at that point you will run
```
sudo chown -R *yourusername* /media/*your_mount_point*/home/*youroldusername*
```
That will give you access to your old username's home directory.

---

### Post by imageburn on 2008-03-25
I'm using the Ubuntu installation disk in trial mode. I just want to scan my hard drive for anything i would regret losing before i reformat and re-install. 

Typing 'sudo fdisk -l' doesn't give ANY result. Just thinks for a second and returns to command line.

---

### Post by Rocket2DMn on 2008-03-25
What if you try without sudo?
If GParted is available on this ubuntu distro Live CD (it should be), go to System->Administration->Partition Editor and see if the drive is listed form the dropdown box in the upper right.  If it ISN'T, then your hard drive may be broken and you should not attempt to install to it.

---

### Post by imageburn on 2008-03-25
Interesting... GParted detects one 'unallocated' drivespace as if the drive were online, and gives it the name of 'hda'. But the mount procedure you gave me returns a 'no device found' dialog. So this means the drive is effectively blank and unpartitioned but still functioning?

---

### Post by Rocket2DMn on 2008-03-25
If it says unallocated space, then yes, the drive will have a label like hda, but no partitions on it like hda1, hda2, etc.  So yes, there is nothing accessible on the drive, like you deleted the partitions.  If you are positive that you never deleted the partitions on the drive, then the drive may somehow be corrupted and should not be trusted with anything important.  Otherwise, you can format the space and use it for your new install.
Sorry if you lost anything important.

---

