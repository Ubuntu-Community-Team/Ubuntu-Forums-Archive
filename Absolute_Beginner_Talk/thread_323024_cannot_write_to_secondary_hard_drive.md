---
title: "cannot write to secondary hard drive"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by loo on 2006-12-21
i just installed linuxmint on my primary drive i have a second hard drive that i like to use strictly for data and storage i cannot write to it or delete files however except as root. i initially could not access this drive and i used the following command which i found in a library book to remedy

sudo mount -t vfat -o umask=000 /dev/hdb1 /mnt/hdb

this worked but then next time i booted i couldnt access my secondary drive, so
i looked up some help for a point and click remedy to mounting and accessing my second drive and noticed i was missing the disk manager and proceeded to install storage device manager by downloading pysdm via synaptic and this allowed me to mount and access my secondary drive but i cannot write to it or delete files i can simply access files. so i tried changing permissions but since i am not comfortable with the command line just yet i tried to point and click. i wasnt allowed to change permissions with my user account so i enabled admin login, rebooted and logd in as root, right-clicked the secondary hard drive icon on the desktop clicked on properties and tried to change permissions for others to create/delete files but could not. i would click the tab and scroll to create/delete files press enter but the tab would just revert to access files. help please

---

### Post by Bachstelze on 2006-12-21
Please paste the contents of /etc/fstab

---

### Post by historypodcast on 2006-12-21
You need to add a line to fstab to get it to mount on re-boot:

/dev/hda5 /storage ext3 defaults 0 0

change hda5 to whatever your second slave HD's name is (use fdisk -l to find out)
change /storage to whatever the directory is that you created

Example:

Mine is like this:
/dev/hdb /media/linuxstore ext3 defaults 0 0

This line is added as the last line in fstab

to open fstab type:  sudo /etc/fstab
You will then have to type in the password you made when installing Ubuntu.

You have to use sudo if you want to be able to save the file after you make the changes.

If you want to be able to write to the drive (save/ create files) use:

sudo chown -R marie:marie /storage
sudo chmod -R 755 /storage

Where "marie" is your username and /storage is the directory you made for the HD.

See this guide:  It helped me do the same thing:  [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Good luck!
Jason

---

### Post by loo on 2006-12-21
thanks jason, i am able to write to my storage device now after looking at the psychocats guide. i used sudo mount for fat32.

---

