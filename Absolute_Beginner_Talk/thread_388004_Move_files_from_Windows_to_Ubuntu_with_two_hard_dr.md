---
title: "Move files from Windows to Ubuntu with two hard drives"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by explorer716 on 2007-03-19
I have two internal hard drives on my computer.  Windows XP is on the first drive and Ubuntu is on second drive.  When I am running Ubuntu and click on Places>Computer, the Ubuntu drive as well as the CD & DVD drives are shown.  However, the Windows XP drive isn't listed.  Is this correct?

I am new to Unbuntu, but like what I see and want to move my files, mail, address books, documents, graphics, music, etc. from Windows to Unbuntu.  In Windows I used Firefox as my browster and Thunderbird as my mail client.  I plan to keep using them in Ubuntu.  

Please explain how to move my files from Windows XP to Ubuntu with my hardware configuration.  Also, please consider that I am very new to Ubuntu.

Thank you in advance for your time and knowledge.

---

### Post by crispy_420 on 2007-03-19
As far as sharing files I would go with a driver that allows WinXP to read/write for ext3. Sure you go the other way(linux driver for NTFS), but it is not as stable.

But the ultimate option would be an external drive.

---

### Post by explorer716 on 2007-03-19
Can you please explain you answer in more detail because I don't understand?  Sorry, that I am so new.

Thanks,

---

### Post by barney_1 on 2007-03-19
When I still had a windows partition I mounted it as a read-only directory in my Linux system.  I mounted it to /mnt/Cdrive but you can put it anywhere you like.  A step-by-step guide for this on Edgy can be found here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by ubuntu27 on 2007-03-19
> **explorer716 said:**
> I have two internal hard drives on my computer.  Windows XP is on the first drive and Ubuntu is on second drive.  When I am running Ubuntu and click on Places>Computer, the Ubuntu drive as well as the CD & DVD drives are shown.  However, the Windows XP drive isn't listed.  Is this correct?

I am new to Unbuntu, but like what I see and want to move my files, mail, address books, documents, graphics, music, etc. from Windows to Unbuntu.  In Windows I used Firefox as my browster and Thunderbird as my mail client.  I plan to keep using them in Ubuntu.  

Please explain how to move my files from Windows XP to Ubuntu with my hardware configuration.  Also, please consider that I am very new to Ubuntu.

Thank you in advance for your time and knowledge.

First mount NTFS (Win XP) following [this guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only"):

And then, re-start and go into Windows.

OPen Firefox, and then go to Files/Export

and export (save) all your favorites somewhere (My Documents?)

then do the same with Thunderbird, somewhere in the menus, there must be a export option.


After all that, re-start the computer and initialize Ubuntu.
OPen Firefox and Thunderbird, and choose IMPORT.


That's it :)

---

### Post by LanDan on 2007-03-19
mounting the NTFS from linux seems the most logical indeed,

but you can simply place the thunderbird and firefox files in your home partition and name the .Thunderbird and .Firefox (not sure about the capitals) so you do not have to import anything if that is possible at all

---

### Post by Najand on 2007-03-19
Look, there are few ways to mount NTFS (the filesystem for Windows NT, 2000, XP, so on) on Linux. By default, the driver which most of the users use can mount NTFS devices just in read-only mode. So you can see files and copy them from the Windows Partition but you won't be able to delete them or change them or copy date to your Windows Drive.
If you want to see your Windows Partition/Harddisk to computer or desktop you must add a directory to /media and then mount the device on it.
To make a directory to /media, open a terminal (Applications => Accesories => Terminal) and then run:
```

sudo mkdir /media/windows

```
You may change windows with whatever you like. It would be your mountpoint.
Then, try to  find which device is the one with windows on it. It can be done using
```

sudo fdisk -l

```
when you found it (for example /dev/hda1) there are two options:
1. To mount it manually, you can use:
```

sudo mount -t ntfs /dev/hda1 /media/windows

```
2. for automount, add something like: 
```

/dev/hda1       /media/windows  ntfs    defaults,nls=utf8,users 0 0

```
to your /etc/fstab. (for editing /etc/fstab use
```

sudo nano /etc/fstab

```
in Terminal.)
You will find it in your gnome computer or you can mount it manually using:
```

mount /media/windows

```
afterwards.

---

### Post by explorer716 on 2007-03-20
Thanks for the help.  I am new to Ubuntu  so I want to be sure before I start changing things. 

Reading Najand's post I would:

1) Open Applications>Accessories>Terminal
2)At the blinking cursor type: sudo mkdir /media/windows  and hit enter
3) If I  get a request for password, Is it the password I use when Ubuntu starts up?
    When I have typed the password before, the blinking cursor does not move from left to        right when you type a letter or number. Is this correct?  
4) I assume if a password is asked, I type it in and hit enter.
5The instructions state: You may change Windows with whatever you like and it would be your mountpoint - please explain
6)I assume the next step is to type: sudo fdisk -1 and hit enter
7) Please advise which option to choose: manual or automount
8)Depending on the choice made above I should the appropriate code and it enter
9) Type in: sudo nano /etc/fstab and hit enter
10) Please explain what is required at this step:  You will find it in your gnome computer or you can mount it manually using:


Thank you for taking the the time to help baby newbie

---

### Post by steve101101 on 2007-03-20
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

