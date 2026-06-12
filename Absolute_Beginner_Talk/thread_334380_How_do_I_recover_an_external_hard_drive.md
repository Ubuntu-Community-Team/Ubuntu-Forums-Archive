---
title: "How do I recover an external hard drive"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-08
OK, I'll admit it, I'm a dummy. I've tried several distros before settling for ubuntu. I have 4 hard drives. Windoze XP pro is on the first drive (80  GB), ubuntu on the second (120 GB). My problem is I tried to install another distro that someone recommended (Freespire) on the first external and it failed.It's now not usable by either ubuntu or Windoze. I'd like to use it for storage of downloaded stuff (music, videos & Software) for ubuntu. How can I recover it?](*,) ](*,) ](*,) ](*,)

---

### Post by scj on 2007-01-08
If you are in Ubuntu type "sudo fdisk -l" should show you what drives are available.

I must admit I'm confused what drive is having problems, and what type of filesystem is on it.  Are your external drives 3rd and 4th (by your count)?  The result of fdisk should answer the later question.

---

### Post by tagra123 on 2007-01-08
> **kliljedahl said:**
> OK, I'll admit it, I'm a dummy. I've tried several distros before settling for ubuntu. I have 4 hard drives. Windoze XP pro is on the first drive (80  GB), ubuntu on the second (120 GB). My problem is I tried to install another distro that someone recommended (Freespire) on the first external and it failed.It's now not usable by either ubuntu or Windoze. I'd like to use it for storage of downloaded stuff (music, videos & Software) for ubuntu. How can I recover it?](*,) ](*,) ](*,) ](*,)


You can use gparted to wipe the disk, make partitions and format the drive.

to install

sudo apt-get install gparted

gparted will be in the System-Administration menu.

Make sure when deleting partition that you are on the usb drive.

---

### Post by scj on 2007-01-08
Sorry, I thought you wanted to recover the data on the disk, rather than the disk itself...

---

### Post by kliljedahl on 2007-01-08
Here's the screen shot, I'm still confused as to where to go and what to do: [IMG]http://i38.photobucket.com/albums/e121/kliljedahl/MySpace/Screenshot.png[/IMG]

---

### Post by maniacmusician on 2007-01-08
do you see where it says /dev/hda ear the top right corner? you have to click that, and a drop down menu will appear with other choices. Your external drive is probably something like "/dev/sda". Click on it. Your partitions will show up. 

If you're sure that this is your external drive, delete all the partitions on there. 

Then, click the "New" button to create a new ext3 partition. 

After adjusting the size and making it however you want, click the big  "Apply" button (with the check mark next to it) to apply those changes.

hope that works out for ya.

---

### Post by kliljedahl on 2007-01-09
I figured it out, thank you very much. I formatted it as Fat32, then booted to windows and reformatted as NTFS. Thanks for your help, it is greatly appreciated.

---

