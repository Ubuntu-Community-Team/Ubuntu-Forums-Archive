---
title: "Mounting a 2nd HDD"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by derouge on 2006-05-12
Okay .. heres my situation. 

I have two harddrives - both contain Ubuntu (Breezy Badger v5.10).  I need to be able to access the second harddrive's files. How is this done? The main HDD is set to master, while the second is cabled to slave. They both appear in BIOS.

---

### Post by aysiu on 2006-05-12
If it's an NTFS or FAT32 partition, follow these instructions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise--if it's Ext3--I can walk you through it.

---

### Post by derouge on 2006-05-12
It's Ext3

---

### Post by aysiu on 2006-05-12
You'll need some terminal commands--you can copy and paste these.

Find out where it lives: ```
sudo fdisk -l
``` My guess is it's (and for the sake of this example I'm assuming it's) /dev/hdb1

Ensure it's not already mounted: ```
sudo umount /dev/hdb1
```
Create a mount point for it: ```
sudo mkdir /second_drive
```
Back up the fstab: ```
sudo cp /etc/fstab /etc/fstab_backup
```
Edit the fstab: ```
sudo nano /etc/fstab
``` Add in this line at the end of the file: ```
/dev/hdb1 /second_drive ext3 defaults 0 0
``` Save the file: Control-X, Y, Enter ```
 Mount the drive: [code]sudo mount -a
``` Change ownership to you: ```
sudo chown -R derouge:derouge /second_drive
``` Set permissions: ```
sudo chmod -R 755 /second_drive
```

---

### Post by derouge on 2006-05-12
It worked great! Thanks a lot. :)

---

### Post by bbarrons on 2006-05-12
I had been searching for sometime for the answer to my problem I had a partition I could not access. Thanks also for the quick rundown . worked for me and got me access to another 30 gigs.... my son will be very happy.
thanks again
Bill

---

### Post by PaulCenji on 2006-05-13
I've been working on a similar problem. I have dapper on the 2nd HDD and XP on the     "master" (wife is not an advanced computer user, she's willing to try to learn Ubuntu...trying to rationalize keeping windows.) 
Anyways, Ubuntu is on a 10 GB HD and I have a ton of stuff I want to be able to access from my "master" 160 GB drive. I've followed these instructions plus had my brother try to help and he's been doing Ubuntu for a while. 
The only problem I'm having is permissions for my XP NTFS HD. THe only way to access the information on my 160 GB HD from Ubuntu is to go through sudo. Not that that is a problem but if I could access it from my user would be nice. I read in some posts that an NTFS disk will not remember linux permissions.
Not trying to thread jack, Newbie trying to get by and noticing the similarity with my own question.

---

### Post by aysiu on 2006-05-13
You won't be able to write to NTFS, but you can mount it read-only:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

The alternative is to make your Ubuntu partition bigger and then use [http://www.fs-driver.org/](http://www.fs-driver.org/) to read/write Ubuntu from Windows.

---

### Post by PaulCenji on 2006-05-14
Thank you ayisu. Finally figured out my problem. When I was gediting fstab the screen was still small so was showing the pass  and dump on a second line so I, the idiot I am, used a carrage return instead of just the necessary spaces. I was wondering why i was getting the error mount: mount point 0 does not exist.

---

### Post by kart3r on 2006-05-17
i have the same problem that derouge had's but when i do "sudo mount -a" it shows me this error:

mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I type "dmesg" and it shows me this:

[ 4561.254486] EXT3-fs: unable to read superblock
[ 4575.381180] VFS: Can't find ext3 filesystem on dev hdd1.

this second disk has ubuntu 6.06 installed but it doesn't work so i've installed kubuntu 6.06 on another disk but now i need to retrieve some information stored in the second this ( the one with ubuntu) help me =X

---

### Post by catlett on 2006-05-17
[QUOTE=aysiu]You'll need some terminal commands--you can copy and paste these.

Find out where it lives: ```
sudo fdisk -l
``` My guess is it's (and for the sake of this example I'm assuming it's) /dev/hdb1

Ensure it's not already mounted: ```
sudo umount /dev/hdb1
```
Create a mount point for it: ```
sudo mkdir /second_drive
```
Back up the fstab: ```
sudo cp /etc/fstab /etc/fstab_backup
```
Edit the fstab: ```
sudo nano /etc/fstab
``` Add in this line at the end of the file: ```
/dev/hdb1 /second_drive ext3 defaults 0 0
``` Save the file: Control-X, Y, Enter ```
 Mount the drive: [code]sudo mount -a
``` Change ownership to you: ```
sudo chown -R derouge:derouge /second_drive
``` Set permissions: ```
sudo chmod -R 755 /second_drive
```[/QUOTE]
This and your psycho cats how to really should be stickied someowhere in the Ubuntu beginner's forum. This issue seems to constantly come up and it seeems your directions always work, even for new people who might not know exactly what they are doing but you directions are good eneough that they are successful. So instead of you constantly posting this advice it would be nice if they made it permanent somewhere.

---

### Post by mister_p_1998 on 2006-05-17
Ive managed to mount a second drive in dapper, but it doesnt appear in places/ Computer...
just the floppy and filesystem, the only way I can access the second drive is by putting a shortcut to it on the desktop, is there an  easier way? something like "My computer" in windows?

---

### Post by aysiu on 2006-05-17
[QUOTE=mister_p_1998]Ive managed to mount a second drive in dapper, but it doesnt appear in places/ Computer...[/QUOTE] Bookmark it in Nautilus, and it'll appear there.

[quote=catlett]This and your psycho cats how to really should be stickied someowhere in the Ubuntu beginner's forum.[/quote] Thanks, but I think there are enough stickies as is.

---

### Post by casperfelix on 2006-06-10
Thanks. Worked for me too.

---

### Post by meazz1 on 2008-02-19
> **aysiu said:**
> Bookmark it in Nautilus, and it'll appear there.

 Thanks, but I think there are enough stickies as is.

I followed this direction and everything works except for this.
I bookmarked it in Nautilus and when I rebooted, it did not show in Computer any more.
Any help is appreciated.

---

