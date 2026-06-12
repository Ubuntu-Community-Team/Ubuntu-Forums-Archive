---
title: "Second Hard Drive"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Donut417 on 2007-10-08
I have a second hard disk in my machine. Its for data. Videos and such. Its formated in NTFS so windows can use it. However Ubuntu can read NTFS. Which is all I need it to do. I need to be able to have Ubuntu to read this drive so I can watch videos from that drive in Linux. It can see the drive but their is no Icon to access it and it wont let me access it any other way.

---

### Post by Arwen on 2007-10-08
When you say it can see the drive,you mean it's added in your fstab but there's nothing in /media or wherever your drive has been mounted?

---

### Post by Donut417 on 2007-10-08
Yeh, I beleive it just as you said. It can tell the drive is present if i go in to the disk manger. But it wont let me access it.

---

### Post by rax_m on 2007-10-08
Do you mean that you can see the files, but you can't write to the files?? 

In order to write access to an NTFS partition, you have to install ntfs-3g and ntfs-config
The config application allows you to configure which drives you can access without having to access the command line.. 

Hope that helps.

---

### Post by Donut417 on 2007-10-08
No as in Linux can see the drive exist. But I have no access to any files. It says I dont have permission to read files

---

### Post by SneakPeak on 2007-10-08
Howdy,

While you are talking about this: How do I get Kubuntu to mount a drive every time at boot.  I have a drive physically installed and formatted as a Linux partition but I can't access it.  Hope I am not butting in out of turn here.

SneakPeak

---

### Post by notbitmonk on 2007-10-08
See if this thread helps:
[http://ubuntuforums.org/showthread.php?t=531415]("http://ubuntuforums.org/showthread.php?t=531415")

---

### Post by SneakPeak on 2007-10-08
Ok, thanks I'll give it a try.

---

