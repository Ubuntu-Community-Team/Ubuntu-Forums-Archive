---
title: "write access to secondary ntfs hd?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by martin28 on 2007-08-15
Hello,

I'm a Ubuntu beginner and I'm trying to get write access to a secondary ntfs drive.  The problem is that it is owned by root.  When I try to copy to this folder it says I don't have permission to write to this volume.

I have a dual boot set-up with WinXP.  Ubuntu and WinXP are both on the master drive, along with a 90GB data partition (ntfs).  There is also another drive (slave) which has two ntfs partitions.

I can read data from everywhere.  I want to be able to write to all partitions also.  I need to be able to drop files from Linux into a drive that Win XP can also access.  This is because s-video out doesn't work in Linux so when I want to watch a movie on my computer I want to be able to drop it into an ntfs disk then reboot into WinXP and watch on TV.

For the moment I'm burning everything onto DVD's then reboot and copying from DVD to ntfs drive in WinXP - but it's very time consuming. 

The problem is (I think) that the ntfs volumes are owned by root so I don't have write access to them.  How do I change this?

Thanks for your help,
Martin.

---

### Post by shad0w_walker on 2007-08-15
You should be able to change the ownership of the drive using this command

```
sudo chown <username> <mount point>
```

---

### Post by bluenova on 2007-08-15
You need to install ntfs-3g:

```
sudo aptitude install ntfs-3g
```

---

### Post by Hospadar on 2007-08-15
I think if you run "ntfs-config" (it's the companion to the great ntfs-3g drivers, you can install it with a "sudo apt-get install ntfs-config", and then run it from the command line of Applications->System Tools) It will get all your drives set up with write access should you so choose.

You'll have to restart after you do this so the drives remount.

---

### Post by stchman on 2007-08-15
> **martin28 said:**
> Hello,

I'm a Ubuntu beginner and I'm trying to get write access to a secondary ntfs drive.  The problem is that it is owned by root.  When I try to copy to this folder it says I don't have permission to write to this volume.

I have a dual boot set-up with WinXP.  Ubuntu and WinXP are both on the master drive, along with a 90GB data partition (ntfs).  There is also another drive (slave) which has two ntfs partitions.

I can read data from everywhere.  I want to be able to write to all partitions also.  I need to be able to drop files from Linux into a drive that Win XP can also access.  This is because s-video out doesn't work in Linux so when I want to watch a movie on my computer I want to be able to drop it into an ntfs disk then reboot into WinXP and watch on TV.

For the moment I'm burning everything onto DVD's then reboot and copying from DVD to ntfs drive in WinXP - but it's very time consuming. 

The problem is (I think) that the ntfs volumes are owned by root so I don't have write access to them.  How do I change this?

Thanks for your help,
Martin.

To write to an NTFS partition you need to have ntfs-3g installed.

Here is how to get read/write to NTFS partitions.

```

sudo apt-get -y install ntfs-3g

sudo mkdir /medis/<some name>

Edit your /etc/fstab with the following:
/dev/<drive designation>       /media/<some name> ntfs-3g  defaults  0   0

sudo mount -a

```

An icon will appear on your desktop that will allow you to access the NTFS hdd with write ability.

---

### Post by martin28 on 2007-08-15
yeah I have installed ntsf-config and i'm pretty sure i have read-write access set up but what i want is to permanently be able to write to those disks.  the problem is that the owner of the volumes is 'root' and even root doesn't have write access.  I say this because the permissions are 'dr-xr-xr-x' and i was expecting to see a 'w' somehere in there....

if i do the chmod command that was mentioned in one of the previous posts,

a.  what is the <mount point> (yes i can feel my newbieness shining through with that question, thanks for your patience :-) for anwering this)?
b.  do i need to do it for each volume?
c.  is it a lasting change or would i need to do it each time i start up ubuntu?

Thanks for the helpful replies so far.  Hopefully all the replies in here will also serve to help some other guy in my situation down the line.

Martin.

---

### Post by dizzy_spells on 2007-08-15
hope you get a solution, i've been trying to get this to work all evening and i've totally FUBAR'd it to the point i can't see the volume in the places section in my browser (yes i'm a noob too but please don't think i'm hijacking your thread).
i tried doing the above post but nothing seemed to happen so i'm watching this post like a hawk!

Hello, just to let you know that i was able to set up a read/write NTFS mount. If you look in my thread [http://ubuntuforums.org/showthread.php?t=526559](http://ubuntuforums.org/showthread.php?t=526559) (or search for NTFS) it may help you. 
Basically i botched NTFS configuration at the mount point. 
i was told to create a windows directory in terminal
sudo mkdir /media/windows
then edit the fstab line
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_GB.UTF-8 0 0
save and close and then type
sudo mount -a
i reran the NTFS configuration tool at some point after the save but can't remember if it was before or after the mount -a command!
reboot and you should get an icon called Windows on your desktop. You can then create a link to my documents. 
thanks to Inxsible and logos34
good luck!

---

### Post by martin28 on 2007-08-21
Hi all,

Just to let you know that i worked.  I installed ntfs-3g drivers and ran the ntfs-config app.

For some reason it had added two of the drives I needed to write to but not the two I was interested in (and the only two I had tried to write to).

So I did what stchman suggested and added those lines to my etc/fstab file.  Two  of the lines were already there but two were missing.

In order to find the mount points I went to System>Preferences>Hardware Information and there I could find the mount points.

Now when I log in I see them all on my desktop (which I don't really want) but I also have full read/write access to all NTFS volumes which I do really want!

Thanks,
Martin.

---

