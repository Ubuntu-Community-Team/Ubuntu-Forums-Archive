---
title: "Ok, Im ready"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-05-21
How do you format the master hard drive from linux.

---

### Post by Gannin on 2006-05-21
Formatting occurs automatically as part of the installation process, when you're doing your partitions.

---

### Post by aysiu on 2006-05-21
The master hard drive...?

---

### Post by JNowka on 2006-05-21
Yes I want to wipe my windows drive.  It is set as my master drive.  And I want it for extra space.  I have talked with several people on how to do this while keeping ubuntu on the slave and bootable, make all important backups onto another computer.  And am ready to format the master hardrive of the Evil that is...

---

### Post by Piggah on 2006-05-21
[QUOTE=JNowka]Yes I want to wipe my windows drive.  It is set as my master drive.  And I want it for extra space.  I have talked with several people on how to do this while keeping ubuntu on the slave and bootable, make all important backups onto another computer.  And am ready to format the master hardrive of the Evil that is...[/QUOTE]

You mean erase windows and install Ubuntu in place of it?

As posted above, you're able to do that during the installation process. You'll have an option to erase the entire disk.

---

### Post by JNowka on 2006-05-21
No, I already have Ubuntu on my slave as I said in the last post.  I have figured out through several threads how to format the master, keep the MBR, and keep Ubuntu running on the slave.  I just want the extra space on the other hard drive.

---

### Post by aysiu on 2006-05-21
If you already have Ubuntu installed and Grub on the MBR, just boot up Ubuntu, unmount the Windows partition (most likely the command you want is ```
sudo umount /dev/hda1
``` but to be sure you should check what /dev Windows is: ```
sudo fdisk -l
```), and install GParted: ```
sudo apt-get update
sudo apt-get install gparted ntfsprogs
gksudo gparted
``` and delete the Windows partition and format it as Ext3. Then create a mount point for it ```
sudo mkdir /data
``` and add it to the /etc/fstab ```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Tack on this line ```
/dev/hda1 /data ext3 defaults 0 0
``` Save (control-x), confirm (y), exit (Enter). ```
sudo mount -a
sudo chown -R jnowka:jnowka /data
sudo chmod -R 755 /data
```

---

### Post by JNowka on 2006-05-21
I would like to announce one more windows free machine.

---

### Post by rahelvey on 2006-05-21
:) :)

---

### Post by Gannin on 2006-05-22
Congratulations :)

---

### Post by henriquemaia on 2006-05-22
[quote=JNowka]I would like to announce one more windows free machine.[/quote] 
And the community rejoices!

---

