---
title: "Change permissions so as to remove files in termial"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by ljbirns on 2007-09-05
My wifes XP Laptop 's HD crashed.  I used Ubuntu live Cd and salvaged some of the files to an external HD. I am taking the drive to a ' Restoration expert' to see if any others are salavagable.
There are some Microsft money files which I salvaged  to the external HD but I would like to delete them from the Fixed damaged  HD  BEFORE I give it to the expert.  I can only access these files in Terminal.  When I try RM I am told the file is read only.  How can I change the permission so i can delete the files. ?
 The books I have only give how to do it with Nautilis

Thanks

Lew

---

### Post by SOULRiDER on 2007-09-05
try to add sudo before rm. Also, you may not have propper drivers for writing on NTFS drives. Check this guide out, it shows how to install an NTFS driver:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by nowshining on 2007-09-05
do a sudo before and then enter your password example

sudo rm /etc/Desktop/filesiwanttodelete.jpg

---

### Post by bone2006 on 2007-09-05
If you booted from the liveCD did you try typing in sudo before the command?

---

### Post by ljbirns on 2007-09-05
I Tried this:

root@ubuntu~#  sudo  rm  /mnt/hda2/My*Money.mny

/mnt/hda2     is the directory   My Money.mny is the file I want to delete

The response is :    Read- only file system

Lew

---

### Post by [Alsharifi] on 2007-09-05
Try

```
sudo rm -r path/Firlename
```

---

### Post by ljbirns on 2007-09-05
sudo rm -r path/Firlename

root@ubuntu:~# sudo rm -r /mnt/hda2/My*Money.mny


Still produces;       rm:  cannot remove    ' /mnt/hda2/My Money.mny ' :  Read only file system

Lew

---

### Post by SOULRiDER on 2007-09-05
Check out my post (post #2) you probably need drivers to write on that drive.

---

### Post by ljbirns on 2007-09-05
SOULRiDER

I believe you are correct.  I don't think I can download the drivers to use on a  live cd .

I am downloading Ubuntu 7.04 which I believe has the proper driver  I will report back.

Thank you all very much.  It is really great that you can get answers and help like this.
The books don't cover it all and then they miss the strange stuff.

Thanks 

Lew

---

### Post by bone2006 on 2007-09-06
I'm not sure what drivers you would need unless it's NTFS?  If so I don't believe the latest version of Ubuntu offers write support on the liveCD.  I know Mepis liveCD has NTFS write support with ntfs-3g, so you could just boot up from Mepis and delete the file there.

---

### Post by alienexplorers on 2007-09-06
try:
> sudo chown user_name:user_name /mnt/hda2
sudo chmod 744 /mnt/hda2

---

