---
title: "DvD is not mounting"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by jimstath on 2007-06-04
Hi i'm new to ubuntu and this is my first post.

In my computer i see cd-rom 1 and CD-RW/DVD±RW Drive. 
When i put a cd/dvd inside the CD-RW/DVD±RW Drive is working and recognises it.
But the problem is when i try to download updates it says this message. "Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415) in drive /cdrom/"
i believe something is wrong with the device cd-rom 1.
Can you help me?


Dimitris

---

### Post by jimstath on 2007-06-04
and i forgot to write that the ubuntu studio cd is in the drive when the message appears

---

### Post by oilchangeguy on 2007-06-04
have you tried performing the update without the cd in the drive?

---

### Post by jimstath on 2007-06-04
Yes i have tried ,still the same.

---

### Post by fede on 2007-06-05
Hello,

The update manager is a front end for the package manager. It has several front ends: update manager, synaptic, add / remove software, and the terminal commands apt-get and aptitude. They all work through the package manager system, though some have different focuses: updates, being easy, etc.

Now, the package manager looks for packages within pre-defined locations. The list of these is in the file /etc/apt/sources.list. The installation cd is in this list at install time, since ubuntu installs most (or all) of itself from the cd. When looking for updates, your package manager looks within the places defined in the list, and your install cd is within it.

For some reason I ignore your cd is not being recognised. To solve it:

Open a terminal. Type (or better, copy & paste to avoid typos!):
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup-original
sudo gedit /etc/apt/sources.list
```

look for any lines starting with 

```
deb cdrom:
```

and insert a # at their start: this is to "comment them out", for the package manager to ignore them, like this:

```
#deb cdrom:
```

When finished, save the file. Back in the terminal, type

```
sudo apt-get update
```

This should fix it. What you've done is to remove the install cd from the list of places your package manager looks for updates. 


OPTIONAL:
It might be useful to add your cd as a place to download software from. After removing it (like you've just done) and adding it again it should not keep on complaining. But your system does not need to have the install cd as a software source, it can install everything from the internet servers. I think the purpose of keeping the install cd in your list is to save time & bandwith when installing large programs which you can install from the cd instead of the net.

You can add the install cd again to your sources.list by putting the cd in the drive and typing:

```

sudo apt-cdrom add

```
 



**If you find any problems**, these commands will revert the changes you made:

```
sudo mv /etc/apt/sources.list.backup-original /etc/apt/sources.list 
sudo apt-get update

```

---

### Post by jimstath on 2007-06-06
Thank you very much it seems it is working .Although in computer still shows the following icons
computer:///CD-ROM%25201.drive
computer:///CD-RW%252FDVD%25C2%25B1RW%2520Drive.drive
computer:///Filesystem.desktop

Also when i do sudo mount -t vfat /dev/uba1 /mnt/sda1
because it doesn't recognise the usb stick it says mount point does not exist.
the mount command gives following
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-lowlatency/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

I will appreciate for your help

---

### Post by fede on 2007-06-07
Hello,

Those icons in computer seem strange to me, I've never seen them.

Also, in my ubuntu usb devices are recognized automatically when plugged in. Haven't tried with an usb stick since I haven't got one, but my usb hard disk was detected automatically.

Does the directory you're trying to mount to exist? (/mnt/sda) Perhaps this is the meaning of the error "mount point doesn't exist". If it doesn't, create it.

Sorry if I cannot be of much further help.

PS: the output of the mount command seems normal to me, it is just listing all mounted filesystems and their mount points. My system produces a similar output.

---

