---
title: "How do I install additional Hard Drive"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by cjssmo on 2006-07-25
Have had ubuntu installed for about 3 months now.  Had an old pos that I was using as a file server finally give out.  I had a 160 GB HD in it.  What I would like to do is take that HD and put in my Ubuntu machine.  I know how to phsically connect the drive just not sure how to partition and place ext3 file system on it.  I have already phsically placed the drive in the machine, the bios detects the HD and lists it correctly.  So what do I do next.  Use to partition and format HD's with windows all the time just not sure how to do it with ubuntu.  Would apprecitate links to howto's.

Thank you for your help and assistance 

Charlie

---

### Post by john_spiral on 2006-07-25
will you be using the drive inside Ubuntu and Windows or just Ubuntu?

---

### Post by brentoboy on 2006-07-25
menu: system > admin > disks

play with that for a bit, and then ask questions about things that dont make sense once you are in there...

---

### Post by cjssmo on 2006-07-25
Pure ubuntu system, in the process of switching over other computers on my lan.  Getting totally away from windows

---

### Post by cjssmo on 2006-07-25
I did the sys>admin>disks it only shows one HD when it should show 2

---

### Post by cjssmo on 2006-07-25
ok going to re check every thing.  Going to try HD in another computer to make sure it works, going to check HD jumper setting again.  Thanks for the help

---

### Post by catlett on 2006-07-25
To partition, go to System<Administration<Gnome partition editor That is gparted it is a partitioning application. If for some reason it isn't installed, enter this in the terminal ```
sudo apt-get install gparted
```That can format and partition your drive..
When it opens it will show the first hard drive as a bar graph. In the right upper corner is a drop down menu that will let you select the other hard drive.
If it is in 1 partition then just select it by right clicking on the graph. An option menu will drop down. Select "format to". Choose ext3.
If you want many partitions then delete every partition. Select the empty space and select "new". Then just make it the seize you want. The only thing to remember is you can only have 4 primary partitions. You can have many logical partitions inside a primary partition though.
The next thing you have to do is mount the drive. To do it permanently, you have to edit the /etc/fstab file.
To show you an example, I am going to assume you have made the partition into 1 ext3 partition and that the drive is the second of 2 ide hard drives.

First you have to make a location to mount it to (you can call it anything you want. Ubuntu will just give it it's drive label. I like to give it a description i.e. backup, movies, docs etc. I mount it inside the media folder because things mounted there get an icon on the desktop)
```
sudo mkdir /media/160gb
```Now open the file fstab in an editor 
```
sudo gedit /etc/fstab
```
add this line to the bottom (again this assumes the drive is /dev/hdb1)
```
/dev/hdb1       /media/160gb     ext3    defaults        0       2
```
If all goes well, when you reboot the drive will be mounted and there will be an icon on the desktop.
If you can't wait, this command remounts drives from /etc/fstab
```
sudo mount -a
```
Here is a basic but good explanation of /etc/fstab [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

