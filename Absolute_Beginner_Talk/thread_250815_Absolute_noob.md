---
title: "Absolute noob"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by kockbeard on 2006-09-04
I understand that the search function is my friend, however most of the instruction seems to be a little beyond me.

Anyway I have some quite large storage requirements, I've recently installed Ubuntu onto a 40GB hdd, I've been using it for around five days now, and am very impressed, I'm by no means a computer genius, but I used to be able to get around Windows quite easily. After installing onto the smaller harddrive I wish to use my larger drive as my library, it's a 250GB drive but it's got an XP installation on it, is there a simple way to format it and use it as my library for files, and leave all the programs on the smaller drive. 

I can't get into the XP installation to do anything from there, so I'm hoping there's a way to do it from Ubuntu. Ubuntu can see a "232.9 GB Volume" but won't let me do anything with it, it say's it's unable to mount it

[quote="Ubuntu"]error: device /dev/hdb1 is not removable

error: could not execute pmount[/quote]

I'm happy to lose everything on the larger hard drive, but may need perhaps a little more direction than the average user.

---

### Post by comppsyco on 2006-09-04
Firstly, welcome to Ubuntu.
The program that you want to use is called gparted. Type into the terminal (Applications - Accessories - Terminal)
```
sudo aptitude install gparted
``` followed by your password. Then launch gparted by typing ```
gksudo gparted
```

This should launch a graphical partitioning tool. Select the hard drive that you want to format (hdb, it sounds like), then select the partition that you want to format, and tell gparted to format it. You probably want to format it as ext3. If you need any more help, don't hesitate to ask.

---

### Post by catlett on 2006-09-04
This will OVERWRITE ALL THE DATA on the 250gb drive. If you want to keep that data, you can acces it first and copy out any data. Since this is going to get a little long, I won't give the instructions for accessing your drive as it is now but if you repost asking for them I'll post another reply with the directions.

First you need to format the drive to a linux filesystem. Go to System<Administration<Gnome Partition Editor. If it isn't installed, open the terminal (found in Applications<acccessories<Terminal) and enter ```
sudo apt-get install gparted
``` When you finally get into gparted go to the top right and select the 250 gb drive from the drop down menu.
Highlight the drive and select "delete". Then select "apply". Next select "new". When it gives you the options window, you want to make it a primary partition and make it ext3. Select "apply" again. After it is finished exit the application.

Now we have to make a place for it and make an entry in the file that mounts drives.
Open the terminal and enter this to make the folder to hold the drive (I am putting it in media because ubuntu mounts partitions there and I am calling it library but you can call it whatever you want. Just make sure if you don't use library, you replace library in the next command with what you use)
```
sudo mkdir /media/library
```
Now open up the /etc/fstab file in a text editor```
 sudo gedit /etc/fstab
```Add this line to the bottom of the file
```
/dev/hdb1  /media/library     ext3 defaults 0 0
```
If there is already an entry for /dev/hdb1, erase it and replace it with this one. If there isn't just add that.

Next we have to set the permissions so you can access it as a regular user. You need to use whatever your username is on your system. I am using you forum I.D. because that is all I know. Enter this in the terminal.
```
sudo chown -R kockbeard:kockbeard  /media/library
sudo chmod -R 755  /media/library
```
You can either reboot or enter this command in the terminal to now mount the drive
```
sudo mount -a
``` Either an icon will appear on your desktop or go to Places<Computer<Filesystem<Media and double click on the library folder. There should be a folder "lost and found" in there. That is what is in empty formatted drives in linux will have in it.
That should be it. You should have the second drive formatted to the linux filesystem ext3 and mounted at /media/library with full permissions for you as a user anbd as root.

If you want to get the data out post or if you have any errors or issue , post.

---

### Post by kockbeard on 2006-09-04
Cheers guys, that was a great help, not too sure why I'm writing the bits that I am in the terminal, but it seems like it will start to make sense soon

---

