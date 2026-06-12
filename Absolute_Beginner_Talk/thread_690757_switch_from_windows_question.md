---
title: "switch from windows question"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by tone33 on 2008-02-07
So I am in the process of learning ubuntu in order to switch from Vista for everything (except my .NET work).  Running windows I have always been able to recover my data files in the event of an install or registry corruption.  I realize that with Linux my chances of corrupting the OS install are greater - mind you, I'm a developer and not illiterate of the ways of a computer, but I am a newbie to Linux.  

1) If I am to corrupt my ubuntu install beyond repair, can you give me an idea of what is involved to retrieve my data, or repair my system?  

2) Vista has handy restore points - is this available in Ubuntu?

3) Any other thoughts on this?  

I realize these questions are a little general, I'm just trying to get an idea of what I'm getting into as I have several gigs (~110GB) of home videos and pictures (among other things) I will be moving to and managing from linux.

Thanks.

---

### Post by Origin415 on 2008-02-07
1) You can use the live cd you installed Ubuntu with as a sort of rescue disk, and move files off onto another partition/drive/computer. It also has disk repair and partitioning utilities.

2) Not by default, but you can find a program to do this for you without much difficulty. Google's Flyback attempts to recreate Apple's Time Machine and could be what your looking for.

---

### Post by alwiap on 2008-02-07
Yeah, I don't believe of any native restore program to ubuntu.  If you are messing around a lot, make sure to back up your xorg.conf, as it will help you return to a visual setting that works in the case you fool around with multiple displays or other stuff.

---

### Post by jrharvey on 2008-02-07
I have always found it usefull to keep a separate partition for your files and such. That way if you mess something up all you have to do is reinstall the OS and not all your files. I dont believe that corrupting ubuntu is as likely as vista. Windows gets alot of malware that you just dont have to worry about with ubuntu.

---

### Post by tone33 on 2008-02-07
> **jrharvey said:**
> I have always found it usefull to keep a separate partition for your files and such. That way if you mess something up all you have to do is reinstall the OS and not all your files. I dont believe that corrupting ubuntu is as likely as vista. Windows gets alot of malware that you just dont have to worry about with ubuntu.

What's a good partition size for Linux?  I will likely install several different apps over time.  Looks like Ubuntu (w/the included application suite) is ~9GB.  I have two 300GB sata drives so space isn't really a concern, but I would like to have an appropriately sized partition.

---

### Post by erfahren on 2008-02-07
> **tone33 said:**
> What's a good partition size for Linux?  I will likely install several different apps over time.  Looks like Ubuntu (w/the included application suite) is ~9GB.  I have two 300GB sata drives so space isn't really a concern, but I would like to have an appropriately sized partition.
6 to 10GB is plenty for the root ( / ) 

it can help to make your /home as a seperate partition. that way if the install gets messed up you can just reinstall the OS itself and retain all of your configuration files. *Most* individual programs create and retain their configuration files in your /home directory (as hidden directories) along with the configration files for your desktop, etc.

Another trick you can do if you think you'll need to reinstall the OS is this: the packages of the updates and programs you install are kept in /var/cache/apt/archives (unless you clean it out). So once you downloaded all the updates (and downloaded programs too) you can copy the packages out of there to another partition or to CD. - They can be copied out of there as a normal user, and then on the new install you'd open a file browser with root (admin) permissions and paste them back into that directory. - then "apt" (the package manager) will fetch them out of there instead of downloading again.

---

### Post by tone33 on 2008-02-07
this is all great info!  So I initially setup a 50GB partition for my Ubuntu install - if I want to decrease this is there a way to do so without repartitioning and reinstalling?

---

### Post by wiseguyxp on 2008-02-07
For backing up, I use G4L, a partition/drive image making live linux distro.  Make an image when you first install, then make a "stable" image once you get programs functioning like you want them.  It supports backing up to and restoring from FTP servers, which makes it really easy.  I'd say keep 10gb for a root partition and whatever you think you might need as a storage partition.

edit: And you can resize partitions very easily with the Ubuntu Live CD, it's in System > Administration when you boot the live CD.  The ext filesystem doesn't fragment easily, so resizing partitions is amazingly easy.  You can't resize a mounted partition, so you can't do it while the OS installed to the HD is booted.

---

