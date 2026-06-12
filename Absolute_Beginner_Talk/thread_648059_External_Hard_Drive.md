---
title: "External Hard Drive"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by sinisterman on 2007-12-23
New Ubuntu user using Kubuntu desktop. I just got an Western Digital Passport external hard drive. It is ntfs formatted. It comes up fine under ubuntu but I am unable to write to it. Thanks

---

### Post by LaRoza on 2007-12-23
> **sinisterman said:**
> New Ubuntu user using Kubuntu desktop. I just got an Western Digital Passport external hard drive. It is ntfs formatted. It comes up fine under ubuntu but I am unable to write to it. Thanks

Which version of Ubuntu are you using?

(If you don't need to use this drive with Windows, use GParted to reformat it to EXT2 or EXT3)

---

### Post by sinisterman on 2007-12-23
I installed GParted but how do I use it. Running 6.10 by the way

---

### Post by kleo skywalker on 2007-12-23
See [this thread]("http://ubuntuforums.org/showthread.php?t=528703"). (I know it's long, but there are a bunch of solutions in it.)

---

### Post by LaRoza on 2007-12-23
> **sinisterman said:**
> I installed GParted but how do I use it. Running 6.10 by the way

The newest version of Ubuntu comes with NTFS write support, but for older releases, you will have to install the ntfs driver.

---

### Post by LaRoza on 2007-12-23
> **sinisterman said:**
> I installed GParted but how do I use it. Running 6.10 by the way

System->Administration->Partition Editor

---

### Post by sinisterman on 2007-12-23
I cant seem to format it as anything other then ext2. When I do this I am still unable to write to the drive and now there is a locked folder within the drive calle lost+found

---

### Post by Harpoon on 2007-12-23
I bet that if you right click on the desktop icon for the drive, and check its permissions, you will find it is owned by root and it says you can't change anything.  If that is the case, and I am correct that the drive is now formatted in ext2, you should be able to fix the problem by opening a terminal and running:
sudo chown -R username:username /dev/<your driive>. Replace <yourdrive> with the appropriate reference, e.g. hda1 or sda2  . . . 

The above also works if formatted as ext3.

Strange that you can't format to ext3 using "gksu gparted" in the terminal . . . .
If you get that sorted out, then you might want to consider one more step. 

The locked folder is space reserved for root to be able to write critical files even when the disk is "out of space."   If the drive is only for your data, and not for system files, then you can run

sudo tune2fs -m 0

which will reduce the reserved space to 0.

Hope that helps.

---

### Post by sinisterman on 2007-12-23
Not sure what this was supposed to do but here is the output

sinisterman@Laviathan:~$ sudo chown -R sinisterman:sinisterman /dev/sda1
Password:
sinisterman@Laviathan:~$ sudo tune2fs -m 0
tune2fs 1.39 (29-May-2006)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
        [-i interval[d|m|w]] [-j] [-J journal_options]
        [-l] [-s sparse_flag] [-m reserved_blocks_percent]
        [-o [^]mount_options[,...]] [-r reserved_blocks_count]
        [-u user] [-C mount_count] [-L volume_label] [-M last_mounted_dir]
        [-O [^]feature[,...]] [-T last_check_time] [-U UUID] device
sinisterman@Laviathan:~$

---

### Post by sinisterman on 2007-12-23
Ran this and it says write protect is off. I dont get this

sinisterman@Laviathan:~$ dmsg | tail
bash: dmsg: command not found
sinisterman@Laviathan:~$ dmesg | tail
[17181241.196000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17181241.196000] sda: Write Protect is off
[17181241.196000] sda: Mode Sense: 21 00 00 00
[17181241.196000] sda: assuming drive cache: write through
[17181241.196000]  sda: sda1
[17181241.244000] sd 2:0:0:0: Attached scsi disk sda
[17181241.244000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17181242.200000] kjournald starting.  Commit interval 5 seconds
[17181242.212000] EXT3 FS on sda1, internal journal
[17181242.212000] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by orky87 on 2007-12-24
Hello people
Could some one tell me how to post 
I just cant find that option, this is why Im in the reply section 
Sorry 
Much appreciated

---

### Post by kleo skywalker on 2007-12-24
> **orky87 said:**
> Hello people
Could some one tell me how to post 
I just cant find that option, this is why Im in the reply section 
Sorry 
Much appreciated

Log in, click on Absolute Beginner Talk. On the left, you'll see a yellow box that says "Make new post" - click and post.

---

