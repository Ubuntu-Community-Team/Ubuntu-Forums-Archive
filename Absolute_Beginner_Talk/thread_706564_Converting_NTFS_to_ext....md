---
title: "Converting NTFS to ext..."
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by wabbster on 2008-02-24
Hi,

I recently threw Win XP out of the window and installed Ubuntu 7.10. So, I'm learning new things each day and, well, messing things up in the process.

My latest misadventure was deleting an ntfs partition (the data was backed up and all that). I used QTParted, since GParted was being slow and throwing up some error while scanning for devices.

So, now that I have deleted the ntfs partition, I cannot view that particular chunk of memory. Is there anyway that I can get that partition back? Please help!

Wabbster.

---

### Post by ruy_lopez on 2008-02-24
I don't understand. If you have a backup why do you need to restore the partition to NTFS?

---

### Post by Duck2006 on 2008-02-24
Are you saying that gparted willn't let you fromat the space to ext3?

---

### Post by seventhc on 2008-02-24
you can run gparted from the live cd, or to install it - open a terminal and paste this in
```
sudo apt-get install gparted
```Once installed you can run it from the terminal or from the menu [I]System>Administration>Partition Editor
[/I]if from the terminal```
gksu gparted
```

---

### Post by wabbster on 2008-02-24
Hey, thanks for the replies... I'm sorry if I wasn't clear before...

Here's what happened. I backed up all the data on the ntfs partition - transferred all of it to an external hard drive. I then started GParted which kept 'scanning all devices' for eons. I took a look at the system log and here's what I saw: "Feb 25 08:08:34 WabbMachine kernel: [ 4006.562990] Buffer I/O error on device fd0, logical block 0" which I'm assuming is preventing the program from running.

So, I installed QTParted, which detected the ntfs partition. I deleted the partition and committed the changes. I should have an ext3 partition (or something along similar lines) now, right? This isn't happening. 

What do you folks think I should do? Please don't tell me anything that'll lead me to the terminal, that place is scary! :'(

Thanks!

Wabbster.

---

### Post by crjackson on 2008-02-24
> **wabbster said:**
> Hey, thanks for the replies... I'm sorry if I wasn't clear before...

Here's what happened. I backed up all the data on the ntfs partition - transferred all of it to an external hard drive. I then started GParted which kept 'scanning all devices' for eons. I took a look at the system log and here's what I saw: "Feb 25 08:08:34 WabbMachine kernel: [ 4006.562990] Buffer I/O error on device fd0, logical block 0" which I'm assuming is preventing the program from running.

So, I installed QTParted, which detected the ntfs partition. I deleted the partition and committed the changes. I should have an ext3 partition (or something along similar lines) now, right? This isn't happening. 

What do you folks think I should do? Please don't tell me anything that'll lead me to the terminal, that place is scary! :'(

Thanks!

Wabbster.

Okay, so it sounds like you deleted the NTFS partition and that's it.  Now you need to create your new EXT3 partition and format it as such.  Nothing hard about it...

---

### Post by wabbster on 2008-02-24
Okay...

The EXT3 partition has been created. I have couple more problems now; I don't know if it belongs here or if I should start a new thread for this.

1. The EXT3 partition does not mount automatically like the other partitions/storage devices.
2. Every time I try to mount it, I'm asked for my password. This is really irritating. Is there any way to turn it off? Besides, I have three more people using the 'puter here and I want to make this transition to linux as smooth as possible for them too.

Any ideas?

Thanks.

Wabbster.

---

### Post by bodhi.zazen on 2008-02-24
You will need to manually add it to /etc/fstab

See this link : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by achianese on 2008-02-24
You can edit your fstab file to automatically mount the partition at startup. Find the name of the device in  System - Gnome partition editor (something like /dev/sd##)

then, open a terminal, and type:

sudo cp /etc/fstab /etc/fstab.backup
sudo gedit /etc/fstab

In the editor, add a line at the end to mount your partition. I have one that looks like this:

/dev/sdb1 /mnt/250gb ext3 defaults 0 0

"sdb1" is the name of the partition, and "/mnt/250gb" is the folder in your filesystem where the partition will be mounted. You should make a folder like this, by typing:

sudo mkdir /mnt/xxx

Then, on reboot, the folder will contain your partition. To mount everything in fstab without rebooting, type:

sudo mount -a

---

### Post by wabbster on 2008-02-27
I think I messed up again. So, I wiped the entire disk and reinstalled Ubuntu fresh... Oh well.. :)

Thanks all! :)

---

