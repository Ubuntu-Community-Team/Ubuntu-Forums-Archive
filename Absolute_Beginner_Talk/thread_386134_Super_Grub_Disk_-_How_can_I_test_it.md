---
title: "Super Grub Disk - How can I test it?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Karstadt on 2007-03-16
I hope folks won't mind me asking this question here.  I'm sure someone can give me an answer (Is Herman lurking?)!  

After a few weeks' delay, I am about to install Ubuntu in a dual boot system and am arming myself with as much as possible to cope with the expected disaster - I'm no expert.  I have made a Super Grub Disk CD but want to find a way of testing it safely.  Any suggestions?  Oh - I use Windows XP - nearly forgot.

---

### Post by dannyboy79 on 2007-03-16
sure, simply boot to the super grub disk (i am assuming it is THE REAL super grub disk) once inside of it, go thru the options until you find the option that says boot windows install. if it works and you get inside windows xp than you'll be fine.

let me know what your setup is going to be before you do anything and I can tell exactly what will happen and exactly what to expect, I am pretty darn good with grub myself. make sure you tell me hard drive scheme, partitions, master/slave or using cable select. what hard drive you're going to be booting to. does bios actually have a list so that you can rearrange your hard drives without having to unhook them from 0 or 1 ide channel? are you going to have a /boot partition? do you want to boot up using grub or ntdlr?

---

### Post by Karstadt on 2007-03-17
Thanks for the reply and sorry for the delay.  I live in the UK and the night intervened!  The disk I have is from sgd_0.9583.iso which I downloaded via [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk)
 
I also downloaded a more up to date version (1.72 MB) but cannot seem to open it and write the data to CD.  If I am on the wrong lines, please tell me as I am no expert in this!

---

### Post by dannyboy79 on 2007-03-17
ok, i do have to be kind of blunt here, if you want my help you need to READ my entire post and ANSWER ALL the questions otherwise it's a little irritating to ask for info over and over. i merely wanted to make sure you were using a super grub disk that I am familar with or if you were just saying that you had a super grub disk but it wasn't the real one. now I knoiw that but please answer ALL the other questions if you would like my help. this is advice for the future as well, when someone is trying to help, provide them with all the info the first time otherwise a person can get irritated and just decide to not help you anymore.

---

### Post by Karstadt on 2007-03-17
OK - the other questions -

1  I have one HD, single partition, single OS (Windows XP),    partition size 149 GB, i GB unallocated.

2  Consequently no master/slave situation.

3  I intend to install Ubuntu on to this disk in a separate partition of 25 GB.

4  From all I've read that should allow me to use a dual boot arrangement, using the GRUB which comes with the LiveCD installation.

5  I have no intention of doing anything more than that, using the Graphical Installation instructions.

6  The only reason I am asking about testing the SGD is because I have been told it is a good idea to have one of these in case of problems.

7  As I said, I am no expert, and I do not know what files and folders I should expect to see on one of these disks.

I do hope I have given enough information now.  I emphasise again that I am no expert and know nothing about bootloaders, partitions etc.  Everyone has to start somewhere.

---

### Post by dstew on 2007-03-17
You will be fine. Defragment your drive first, using the Windows defragmentation program in Programs-->Accessories-->System tools, then go ahead and install Ubuntu linux from the Live CD. Shrink your Windows partition by 25gb, then make your Linux partitions for root and swap out of the space you freed up.

Grub will install itself easily. Do not be afraid to install grub to the master boot record (MBR) of the disk. If you change your mind later, and decide not use the grub boot loader, it is very easy to put the windows boot loader back into the MBR. The windows loader, however, cannot dual-boot. It only boots Windows, and ignores all other operating systems you might have.

Here is a nice graphical run-through of a typical installation process:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Karstadt on 2007-03-17
Very many thanks for the re-assurance.  If you could help with one more thing it would be handy.  Through nervousness etc I have a LiveCD for 6.06 and one for 6.10!  Which version would you suggest?

Again - many thanks.

---

### Post by dstew on 2007-03-17
If you are at all anxious about getting your system to run, and intimidated a little by the possibility of having to make changes to configuration files, then go with 6.06 Dapper. You can try out all the desktop features running the live CD only, before you install anything on your hard drive. However, if the 6.06 Live CD doesn't run properly, try the 6.10 version.

---

### Post by Karstadt on 2007-03-17
Many thanks for that.  Best wishes.

---

