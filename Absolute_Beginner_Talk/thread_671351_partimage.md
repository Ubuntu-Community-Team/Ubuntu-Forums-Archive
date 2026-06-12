---
title: "partimage"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-01-18
im trying to copy my /home partition with partimage and i cant figure it out, i have read there site but still dont get it. I want to save it to a usb hard drive and i dont know how to tell it where to save the image file. I have never used partimage so any help i would like.

thanks :)

---

### Post by mkwerner on 2008-01-18
Hi,
Are you using the graphical or command-line instance of partimage?  Where do you have your usb drive mounted currently?

If you don't know where your usb drive is mounted, open a shell and issue:

mount

to spit out a list of your current mountpoints.

---

### Post by bodhi.zazen on 2008-01-18
Start here :

Partimage [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
		Another partimage : [http://www.ubuntuforums.org/showthread.php?t=287522](http://www.ubuntuforums.org/showthread.php?t=287522)
		Yet another partimage : [http://www.debiantutorials.org/content/view/2/1/](http://www.debiantutorials.org/content/view/2/1/)

Tell us what tutorial you are running and what step seems to hang you up.

FYI : You should run partimage from a live CD as root.

---

### Post by mkwerner on 2008-01-18
> **bodhi.zazen said:**
> FYI : You should run partimage from a live CD as root.I agree - that's definitely a wise recommendation.

---

### Post by legend2440 on 2008-01-18
I can only tell you how I use Partimage to backup
I put **System Rescue CD** in CD drive and boot from that but Ubuntu LiveCD would work also
After it boots up I am at a command prompt and I type 

**mkdir /mnt/temp** this creates a directory called temp where I mount the drive I am going to save backup on 

Then I type 
**mount /dev/sdb1 /mnt/temp** this mounts my usb drive which in my case is /dev/sdb1. If you are not sure of name of your USB device you can type **fdisk -l** to find out
Then
**cd /mnt/temp** this changes to the main dir  on the USB drive
At this point you can type **dir** and you should see any directories or files on your USB drive.
Now if you wanted to you could type something like **mkdir backup** and then **cd backup** if  you wanted to save the image file in a  directory called backup. Its up to you

Then I type** partimage** at the prompt to bring up Partimage and in my case my home directory and everything I want to save is on /dev/hda1 so I highlight that.
Then I hit Tab key and name my backup something like **gutsy.gz**
Now put a check where it says **Save partition into a new image file**
Then I hit F5 key to go to next page of the program  and I choose the Gzip compression type
I usually uncheck where it says **Check partition before saving** and I uncheck **Enter Description**
Then you can decide how you want to split the files if at all.
Then I hit F5 key a few times till it asks me if I want to start the process. That's about all there is to it

Hope that helps. Good Luck

---

