---
title: "Install apps without internet"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by JayKav on 2007-12-19
Here's the situation:

I'm trying to set up an Ubuntu box. It has an ethernet port but no wireless. My only connection to the internet is using an XP laptop to access a communal wireless connection. I have no access to wired internet and no other linux PC.

What I've been able to do so far:

Download the Ubuntu installation and burn it onto a CD. Install Ubuntu on the new PC. As far as I can tell it works fine.

What I need to do:

Install various other packages, starting with VLC and various codecs.

This has completely defeated me. Here's a few things I've tried:

1. Directly connect Ubuntu PC to laptop so I can use internet connection sharing. This works when both PCs are running XP. Seems I need to install Samba first (is this correct?). But I can't install Samba until I connect to the internet.

2. Use APTonCD to make a CD and then use this to install the packages. Problem is APTonCD won't run on my XP machine.

3. Manually install the deb files. This is working but takes forever. I have to download a deb file, put it on to a USB stick, transfer the stick to the Ubuntu PC, copy it into my repository, try to install it, note the file that it is dependent on, search for new file. I spent several hours doing this last night and managed to install about 3 files.

So, what's the correct way of doing this?

Jay.

---

### Post by weblordpepe on 2007-12-19
You can look in synaptic and see what the dependencies are for a particular package, and then download each of them.
There is a command called dkpg which should have heaps of options for downloading packages but I can't remember exactly how to use it.

---

### Post by kpkeerthi on 2007-12-19
> 
1. Directly connect Ubuntu PC to laptop so I can use internet connection sharing. This works when both PCs are running XP. Seems I need to install Samba first (is this correct?). But I can't install Samba until I connect to the internet.

Gutsy comes with Samba installed. Are you not using Gutsy?

---

### Post by hyper_ch on 2007-12-19
you could also fetch the ubuntu-dvd which contains quite a few applications that you need...

---

### Post by JayKav on 2007-12-20
> **kpkeerthi said:**
> Gutsy comes with Samba installed. Are you not using Gutsy?

I'm using 7.10. Samba doesn't appear to be installed e.g. smbstatus gives 'command not found'.

I tried

  sudo apt-get install samba smbclient

but it didn't work. "... samba not accessible... replaced by smbclient samba-common..."

I tried with samba-common and it said package already installed.

So now I'm completely confused about whether I have samba installed or not :)

---

### Post by capink on 2007-12-20
One option is using virtualbox under windows and install ubuntu as a guest. form there you can use apt in the guest system since it will have internet as follows:

1. Download and install all the packages you want in the guest system. And after being done backup the guest system by:

```
sudo tar cvzp --exclude=/proc/* --exclude=/lost+found/* --exclude=/tmp/* --exclude=/mnt/* --exclude=/sys/* --exclude=/etc/fstab --exclude=/path/to/backup.tgz --exclude=/boot/grub/menu.lst --one-file-system -f /path/to/backup.tgz /
```

Note1: We excluded both fstab and menu.lst because the settings in the virtual machine will not reflect those in your actual system.

Note2: Don't forget to replace /path/to/backup.tgz with the actual path. Notice that it is referenced twice in the last command.

Note3: make sure that the backup.tar.gz is in a shared folder ( or usb disk ) so that you have access to it from your windows host

2. Now copy the backup.tar.gz form your windows machine to your ubuntu machine and extract over you system using:

```
sudo tar xvzp --same-owner -f /path/to/backup.tgz -C /
```

DISCLAIMER: THIS IS THEORETICAL. I HAVE NOT TRIED IT SO BE SURE TO BACKUP BEFORE PROCEEDING.

---

### Post by ugm6hr on 2007-12-20
> **JayKav said:**
> 
So, what's the correct way of doing this?


I would recommend this: [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

It is explained here: [http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

It is a lot easier than messing with any of the other options.

---

### Post by capink on 2007-12-20
> **ugm6hr said:**
> I would recommend this: [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

It is explained here: [http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

It is a lot easier than messing with any of the other options.

This is a very nice solution. I did not know something like this existed. It solves the problem better than any other option.

---

### Post by ugm6hr on 2007-12-20
> **capink said:**
> This is a very nice solution. I did not know something like this existed. It solves the problem better than any other option.

I agree.  It was started by a community member - which is pretty impressive, eh?

I genuinely believe it should be publicised (and perhaps supprted) by Ubuntu / Canonical for those people without internet.

---

### Post by capink on 2007-12-20
Yes. And I think this thread should be sticky as it would save the forums and members form a lot of hassle.

---

### Post by buccaneere on 2007-12-21
> **JayKav said:**
> Here's the situation:

I'm trying to set up an Ubuntu box. It has an ethernet port but no wireless. My only connection to the internet is using an XP laptop to access a communal wireless connection. I have no access to wired internet and no other linux PC.

What I've been able to do so far:

Download the Ubuntu installation and burn it onto a CD. Install Ubuntu on the new PC. As far as I can tell it works fine.

What I need to do:

Install various other packages, starting with VLC and various codecs.

This has completely defeated me. Here's a few things I've tried:

1. Directly connect Ubuntu PC to laptop so I can use internet connection sharing. This works when both PCs are running XP. Seems I need to install Samba first (is this correct?). But I can't install Samba until I connect to the internet.

2. Use APTonCD to make a CD and then use this to install the packages. Problem is APTonCD won't run on my XP machine.

3. Manually install the deb files. This is working but takes forever. I have to download a deb file, put it on to a USB stick, transfer the stick to the Ubuntu PC, copy it into my repository, try to install it, note the file that it is dependent on, search for new file. I spent several hours doing this last night and managed to install about 3 files.

So, what's the correct way of doing this?

Jay.

Hi Jay...

Download [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/). This will allow windows to map your linux drive and partitions, and allow you to save your linux apps onto the linux drive.

There might be another way, but that's first to come to mind...

---

### Post by ugm6hr on 2007-12-21
> **buccaneere said:**
> Hi Jay...

Download [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/). This will allow windows to map your linux drive and partitions, and allow you to save your linux apps onto the linux drive.

There might be another way, but that's first to come to mind...

Doesn't he need to be networked with samba first for this to work?  He was saying he can't install samba at the moment.

---

### Post by buccaneere on 2007-12-24
> **ugm6hr said:**
> Doesn't he need to be networked with samba first for this to work?  He was saying he can't install samba at the moment.

Not if he has windows and linux on the same machine. 

He said he can link both XP-booted machines by ethernet.

Boot both into windows and link them.

With the internet-linked machine, download Ext2, and save it to the ethernet only machine. 

Start the Ext2 service manager on the ethernet-only machine, and the linux volumes will map in 'My Computer', on both machines.

Then, download samba, save to one of the mapped linux volumes on the ethernet-only machine, re-boot it into linux, extract and install samba.

I don't know for a fact that it would work. It would take only about 15 minutes to find out. He said in a couple of hours, he got 3 files copied the other way...

---

### Post by JayKav on 2008-01-05
> **ugm6hr said:**
> I would recommend this: [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

It is explained here: [http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

It is a lot easier than messing with any of the other options.


Great thanks!!! That worked so I could install Samba (still puzzled why it wasn't installed by default but anyway). Now I just have to get the graphics driver working...

---

