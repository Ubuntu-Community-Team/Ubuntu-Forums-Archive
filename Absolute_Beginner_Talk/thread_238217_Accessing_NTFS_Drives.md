---
title: "Accessing NTFS Drives"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by rosdahale on 2006-08-17
Hi, Very new to ubuntu and really enjoying it so far !! Following an ubuntu book I bought and learning things pretty well (managed to get internet and nvidia drivers working - took me a day but its a learning process)

Anywho - I was wondering how do I access the other hard drives I have in "Computer" I can access my linux drive no probs of course, but trying to access another drive I have called "Media" Which is a NTFS file system I used with window it just says "Unable to mount the selected volume" under more details it says "error:device dev/hbd1 is not mountable error:could not execute pmount"

Right clicking on the drive and selecting mount does the same thing

Thanks in advance :D

---

### Post by bulldog on 2006-08-17
Well I'm no expert for sure,but in the map Media you should see your CD-Rom drives and your other partitions.

These have names like hda1 or hda5 and should be automounted by Ubuntu,at least I have,and you can see the mount info in fstab.


You could try and change the mount info in fstab or you could mount it manually.

---

### Post by rosdahale on 2006-08-17
The map media ?? is that a program or something ? all my drives are shown in "computer" and are called "Daves Pc" and "Media" which are both the NTFS drives (no hda1 ect...) the other drive is "filesystem" which is the linux one i can access, as I said when trying to mount it using right click it just gives that error message

---

### Post by karan733 on 2006-08-17
If i remember rightly, if your computer had files on it previously (such as windows files), they are your 'media', and thus your windows partition and any space you allocated to it for the future should be in something like 

/dev/hda1/media :: where dev represents a device, and hda1 represent the first partition of the first hard drive (hd-a) 


Now this is where my knowledge runs out - I think you just gave those partitons a random name (ie, Dave's PC), as opposed to telling them what they should contain (ie, /dev/hda1/media)

i dont know how to change it to be correct, hopefully someone with more experience should be able to help! 

(by the way, sorry if ive given you some completely incorrect advice, im new to this too, its just that I think thats whats wrong :( )

best of luck
karan

---

### Post by taurus on 2006-08-17
Okay, here is what you need to do to mount your NTFS, /dev/hdb1.  Open a terminal, Applications -> Accessories -> Terminal, and type in these two commands.

```

sudo mkdir /media/windows <-- create a mount point
(use the same password that you use to login with...)
sudo gedit /etc/fstab <-- edit /etc/fstab 

```
Now, scroll down to the bottom of /etc/fstab and add this line.

```

/dev/hdb1   /media/windows   ntfs   defaults,umask=0222   0   0

```
Save it and run this command at the prompt to mount it...

```

sudo mount -a

```
Your Windows stuff is in /media/windows and from now on, each time you boot, it will be mounted automatically so no need to edit it every single time...

---

### Post by PriceChild on 2006-08-17
Here's a very good guide: [http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by rosdahale on 2006-08-17
Thanks, the guide worked a treat :KS

---

### Post by rosdahale on 2006-08-17
Ah - one more problem now - Drives are mounted, working fine but in read only mode, tried to copy a file over to it with the terminal and its a no go, do i need to change some properites in etc/fstab for it to work ?

---

### Post by taurus on 2006-08-17
If you want to write to NTFS, you need to rebuild your kernel and even with that, it's NOT a good idea, writing to NTFS.  You could screw up your NTFS filesystem big time and bye-bye to all your files on it...  If you want to read and write safely to it, use vfat/fat32 format then.

---

### Post by rosdahale on 2006-08-17
lol ok thanks think ill just leave it then

---

### Post by givré on 2006-08-17
If you want to know the status of ntfs driver in linux, have a look at the beginning of this howto [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

