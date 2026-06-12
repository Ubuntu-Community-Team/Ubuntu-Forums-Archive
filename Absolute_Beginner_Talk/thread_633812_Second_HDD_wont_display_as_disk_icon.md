---
title: "Second HDD wont display as disk icon"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by jbrevik on 2007-12-06
I'm trying to get my second HDD that I have mounted on /mnt/storage to shop up on my desktop as the disk icon for easy access. I know how to link it, but I kinda like the cool icon.

---

### Post by Partyboi2 on 2007-12-07
I am not sure what you are meaning. If you are wanting to change the icon picture you right click on the icon of the drive on the desktop and select properties then click on the current icon pic and change it to what you want
or
Are you trying to get the 2nd hard drive to be displayed on the desktop when it is mounted?

---

### Post by jbrevik on 2007-12-07
The later. I recently wiped my windows HDD which I was dual booting Windows XP. I reformated it to ext3 and mounted /dev/sdb1 to /mnt/storage (directory I created). I just assumed that the newly mounted drive would show up as a disk icon in Computers, but its just a folder. I know I can change the emblem by using properties but the disk icons is not available. I know this is kind of silly because of I have no problems accessing the drive but I like the icon.

---

### Post by Duck2006 on 2007-12-07
You would have to set it up as /media/(name you want it called) for it to show up on the desktop.

---

### Post by jbrevik on 2007-12-08
Thanks that worked perfecto!! For all the noobs like me, be sure to 
1. umount the volume
2. create your new storage file in /media/(dir_name)
3. modify the /etc/fstab entry 
4. Reboot for the changes to take effect

Well anyways that worked for me...=)

---

### Post by mcduck on 2007-12-08
If you want the automatic icon, you need to mount the drive inside /media directory.

---

### Post by jbrevik on 2007-12-08
Yup mounting in the /media directory did work. Thankyou!!

---

### Post by Duck2006 on 2007-12-08
This may help.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

