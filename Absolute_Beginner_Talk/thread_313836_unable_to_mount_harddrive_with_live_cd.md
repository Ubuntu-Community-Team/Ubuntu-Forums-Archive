---
title: "unable to mount harddrive with live cd"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by richiewrt on 2006-12-06
Hi, Im using the live cd on my laptop and cannot mount the my harddrive to view anything under my windows partition. I am trying to right click on it and mount the drive, but it comes up and says unable to mount.  I am completly new to linux and ubuntu so it is probably something stupid but any help will be good.
error message is as follows:
error: device /dev/sda1 is not removable

error: could not execute pmount

---

### Post by taurus on 2006-12-06
Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows
df -h
```

---

### Post by bodhi.zazen on 2006-12-06
> **richiewrt said:**
> Hi, Im using the live cd on my laptop and cannot mount the my harddrive to view anything under my windows partition. I am trying to right click on it and mount the drive, but it comes up and says unable to mount.  I am completly new to linux and ubuntu so it is probably something stupid but any help will be good.
error message is as follows:
error: device /dev/sda1 is not removable

error: could not execute pmount

pmount is a great utility, but it only works with removable devices not internal drives....

---

### Post by richiewrt on 2006-12-06
well that worked great, but I am still unable to look at anything in the windows folder?  How do i fix that?
error i get is:
You do not have the permissions necessary to view the contents of "windows".

---

### Post by taurus on 2006-12-06
```
gksudo nautilus
```

---

### Post by richiewrt on 2006-12-06
I tried the gksudo nautilus and I still can't get into the windows folder. It seems to make it disappear in nautilus until i close nautilus and then reopen it
.When I type it into terminal this is what I get. 

ubuntu@ubuntu:~$ gksudo nautilus

(nautilus:8022): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ubuntu@ubuntu:~$

---

### Post by richiewrt on 2006-12-06
Ok still having the same issue of not being able to get into the windows folder. any other help would be appreciated

---

### Post by housam on 2006-12-06
I did this after the installation , It may work with the live CD.


```
sudo fdisk -l
```
to identify your windows partition i.e. /dev/sd1
then :
```
sudo umount /dev/sd1
sudo mkdir /windows
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
then change the /dev/sd1 to /windows in the same line.
save, exit then :
```
sudo mount -a
```
hope it may help
good luck

---

