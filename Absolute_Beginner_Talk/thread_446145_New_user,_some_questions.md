---
title: "New user, some questions"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by elchucko on 2007-05-16
First thing, I'm gonna apologize for any questions that have already been asked and I haven't been able to find. 

Ok. I managed to get Ubuntu 7.04 installed and working for the most part on my PC (I'm an ex windows user, not willing to make the jump to Vista, but not wanting to deal with XP anymore). My questions are these:

1. I have a 64.8GB partition on my drive (ntfs), that I want to format and change the file system of. I think I read something about having to use the boot disk to handle this task. I wouldn't mind just using this partition as it is, but I'm unable to do anything with it right now since everything is read only and I can't delete the old files that are on the drive.

2. I have an ATI Radeon 9250 Power Color that I'm hoping to set up to work with this OS. I have very limited experience in the command line editing in a Linux environment. I'm used to using DOS for the most part, and even there, it's fairly limited.

My previous Linux experience was back in 2001 with Redhat 7.0, and we did only a brief introduction to the system. I hope that someone might be able to help me to solve these problems without taking too much of your time. 

Thanks a million in advance!

---

### Post by Happy_Man on 2007-05-16
1. Do you want anything on that partition? If so, back it up, because reformatting wipes it all off. Then, install Gparted ```
sudo apt-get install gparted
``` unmount your partition, ```
sudo umount /dev/sda<insert partition number here>
```, and reformat using the aforementioned Gparted utility. 

2. As for the Radeon... hmm.... have you tried manually specifying to use the ati driver?
```
sudo dpkg-reconfigure xserver-xorg
``` Leave everything the same, except when you get to the screen with the list of drivers, scroll to choose "ati" and then press ctrl+alt+backspace when you finish. Hopefully, it'll work. 

Hope this novel helps!

EDIT: BTW, all the code parts are meant to be typed in a terminal: Applications-->Accessories-->Terminal.

---

### Post by celticbhoy on 2007-05-16
1. Using gparted from the live cd will allow you to format the drive

2. If you search the forums for "radeon how to" there are lots of posts which will enable you to use the card. Dont be affraid of the terminal, just take care to read threads from first post to last to make sure that other users have not had probs with the instructions before you start.

---

### Post by steve.horsley on 2007-05-16
You could install gparted as Happy_Man suggested.
Or you could run gparted from the install CD.

Or thirdly, if the partition is the right size, you don't need a partition editor - you just need to reformat it: First, identify the right partition by looking at the output of 
**sudo fdisk -l**
then unmount it if it's mounted:
**sudo umount /dev/sda?**
Then format it:
**sudo mkfs.ext3 /dev/sda?**
Then correct the entry in /etc/fstab to the right filesystem type:
**gksudo gedit /etc/fstab**

I just checked, and gparted gives the option to reformat. On feisty, gparted gives some bogus error boxes, but it still works. I don't know if gparted is smart enough to correct /etc/fstab.

---

### Post by elchucko on 2007-05-16
Ok, ended up getting Gparted, and I realize now just how Linux inept that I really am. I can't even get the program installed. Boo me. I attempted to look through the INSTALL readme that was included and ended up getting confused. I'm starting to think that maybe switching from a comfortable windows environment wasn't the best thing for me. I'm not ready to give up yet though...

---

### Post by elchucko on 2007-05-16
Ok, tried your options steve, everything went fine up to the last step. I opened the fstab text editing portion, and changed the line concerning the fs for "sda1" from ntfs to ext3. I then went to remount the drive (sudo mount /dev/sda1) and got this error:

charles@neves:~$ sudo mount /dev/sda1
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/9CF4C389F4C363DC,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


any info you can give on this would help. I'm pretty dull right about now. lol...

---

### Post by kh4nh on 2007-05-16
> **elchucko said:**
> 
charles@neves:~$ sudo mount /dev/sda1


Your syntax is not correct, you are missing the mount point. Try this

sudo mkdir /mnt/windows

sudo mount -t ntfs -o ro /dev/sda1 /mnt/windows


If you want to write to ntfs partition, you have to install ntfs-3g

sudo aptitude install ntfs-3g

mount -t ntfs-3g /dev/hda1 /mnt/windows

---

### Post by steve.horsley on 2007-05-17
How did you try to install gparted? Sounds like you tried to donwnload and compile the source from the web site? What on earth for? 

Go System->Administration->Synaptic, search for gparted, select and mark for installation and Apply.

That error on mount is because it's liooking for the UUID partition ID, which gets overwritten by formatting. Ditch the **UUID=** clause and replace it with the normal **/dev/sda1** identifier. Ro run the command **blkid** and find out what the new UUID is.

---

### Post by elchucko on 2007-05-17
actually got the issue sorted out, and now I'm working on getting my ATI radeon 9250 set up, thanks for the help with the drive!

---

