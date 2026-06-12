---
title: "Advice for Accessing the same files from ubunutu and windows"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Lokon on 2006-07-04
Allright wanted to ask all ya'll advice concerning how best allow access to the same files from ubuntu and linux.

I have a 250 gb hd, divided into 8 partitions in the fat32 format.  thanks to some great threads here, I figured out how to mount unmount fat32 partitions and do so upon boot.  My first question is, is there any way to mount multiple fat partitions simultenously (either upon booting or once ubuntu is started)?

Secondly, when the drive that contains my music is mounted, amarok wouldn't play/compile the files (this is after running easyubuntu to allow mp3 playback) I assume the same will be the case with my photos with a program like digikam etc (one of the principle reasons I installed ubuntu is to work with metadata and tagging in a way that is impossible for windows), so I am more then willing to erase one of the fat partitions and remake one that is ubuntu dedicated which I can then copy my music too... but how can i go about doing this?  Ubuntu and the swap partitions are is on the c drive hab2+3 methinks but all the fat partitions are on the slave drive.  

Goodness I hope that makes sense.  

Thanks in advance, I have allready been helped immensely by the materials posted here.

---

### Post by atoponce on 2006-07-04
[quote=Lokon]Allright wanted to ask all ya'll advice concerning how best allow access to the same files from ubuntu and linux.

I have a 250 gb hd, divided into 8 partitions in the fat32 format.  thanks to some great threads here, I figured out how to mount unmount fat32 partitions and do so upon boot.  My first question is, is there any way to mount multiple fat partitions simultenously (either upon booting or once ubuntu is started)?[/quote] 
Make sure that you have created directories for each of the partitions, then add those to your /etc/fstab file.  This will mount each one upon boot.

[quote=Lokon]Secondly, when the drive that contains my music is mounted, amarok wouldn't play/compile the files (this is after running easyubuntu to allow mp3 playback)[/quote] 
Have you installe MP3 playback compatibility?  This is not installed by default due to legal restrictions on the codec based in certain countries.

[quote=Lokon]I assume the same will be the case with my photos with a program like digikam etc[/quote] 
Not likely.  Have you tried accessing your photos while the drive is mounted?  Again, I think your issue with the MP3s is that playback is not installed.  Photo accessibility is.

---

### Post by Lokon on 2006-07-05
> Make sure that you have created directories for each of the partitions, then add those to your /etc/fstab file. This will mount each one upon boot.

How would I do this?  And yes you are right, because upon restaring amarok it worked.  Which was pretty dumb of me:(

---

### Post by Dr. Nick on 2006-07-05
well you know how to mount you partiotons once you have rebooted correct? You just dont like doing it every time?

If this is the case then look at the file /etc/fstab It will control mounting partioions.

If you are using gnome then try System-Administration- Disks for a graphical alternative.

---

### Post by aysiu on 2006-07-05
[QUOTE=Lokon]How would I do this?  And yes you are right, because upon restaring amarok it worked.  Which was pretty dumb of me:([/QUOTE]
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Lokon on 2006-07-05
hey thank you guys, I know I probably presented the problem as far more complicated then it was but you answered all my questions.:D

---

