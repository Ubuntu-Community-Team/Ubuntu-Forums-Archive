---
title: "[SOLVED] Mounting and unmounting a USB hard drive"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Boaslad on 2007-12-09
I have a Seagate external hard drive that has a sleep mode hard wired into it. I am pretty sure there is no way to over ride this with software. As you can guess this gets very irritating because every time I want to grab some data from it I have to unmount the device and remount it again.  Since there seems to be no way around this issue, I am thinking of creating an executable file that will do the job of unmount / remount for me so that i can get this job done with a single click rather then the long process I currently use. I am very new to Linux and don't know the terminal commands well, so can some one tell me the terminal commands for this procedure? Also, is there a place that has a simple list of terminal commands and their basic descriptions? (minus the long, drawn out tutorials about how to use every asset of every one) Don't get me wrong, I am currently trying to learn the ins and outs of the terminal and its associated commands, I just want a quick kick start on this particular issue.

---

### Post by PmDematagoda on 2007-12-09
To unmount the HDD:-

```
sudo umount /media/nameofHDD
```

To get the mounting right, I will need the file system of the HDD.

---

### Post by Boaslad on 2007-12-09
thank you for the quick reply
 
btw. I answered my own question regarding a list of terminal commands. One can be found at [http://www.ss64.com/bash/](http://www.ss64.com/bash/) 
Now all I have to do is learn HOW to use them!... lmbo
The file type on this hd is a NTFS

---

### Post by vikramsharma on 2007-12-09
As you have an NTFS hard drives and Ubuntu comes with ntfs-3g installed by default.  All you have to do is install ntfs-config through Synaptic Package Manager or you could use apt-get install to do that, ntfs-config would enable you to write on to the NTFS formatted hard drive.

---

### Post by PmDematagoda on 2007-12-10
To mount your external HDD(Since it is of NTFS), use:-

```
sudo ntfs-3g /dev/locationofdrive /media/mountpoint 
```

To get some help with this, you can use:-

```
ntfs-3g --help
```

---

### Post by Boaslad on 2007-12-11
Thank you very much. I was starting to get frustrated while trying to use "mount" (the assumed logical choice) for this application. The script has been written and works great. Thanks again and have a pleasant holiday season!

---

### Post by PmDematagoda on 2007-12-11
Glad it worked out for you:), and may you have a pleasant holiday season as well:lolflag:.

---

