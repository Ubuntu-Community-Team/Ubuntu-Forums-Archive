---
title: "help !!! please"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by payneardo on 2007-05-18
hiall been reading the manuals but still cant get osx or windows to map to a drive

hope you can help

I have ubuntu installed and each time i reboot I have to reformat 2 of my hard drives and then I can setup a share and I can connect but I am unable to write to them :(

please as anybody got any step by step instructions where it will remount the hard drives on reboot and also allow me to read & write to the shares I create.  Mind you it probably wont reconsie the smb users Icreated and now I cant find that command.

I am new to linux ( I installed it on this box 2 days ag0) and are struggling to get these thigs sorted above

Many Thanks

Dave

---

### Post by RichGuk on 2007-05-18
I don't quite understand what you're asking..

Are you wanting to connect to Windows/OSX shares from your ubuntu box? But them to be avaiable at boot?

You'll want to setup Samba most likely, [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server) and mount the drive in your /etc/fstab file, its on ubuntu guide I think :)

---

### Post by payneardo on 2007-05-18
u have installed samba and tried everything in the guide :(

I have seen this on the guide but it doesnt work :(

Mounting Automatically 
Create mountpoint: 

sudo mkdir /mnt/files
Edit configuration: 

sudo vi /etc/fstab
Add something similar to below: 

192.168.1.1:/path/to/shared/files /mnt/files nfs rsize=8192,wsize=8192,timeo=14,intr
Test new configuration: 

sudo mount /mnt/files


I have 3 hard drives in the machine /dev/hdb & /dev/hdd are both empty /dev/hda has 140 gig of free space on it.

All I want to do is when it reboots is to have access to them & then map a drive from my windows & osx box to them and have read write access to them

I did get a drive mapped once but it would let me write to it, even though I tried to put the creat mask = 0777 in the smb.conf file


hope you can help again

Cheers

---

### Post by RichGuk on 2007-05-18
Ah I get you now,

other why to what I was thinking :).

What filetype are the drives? ext3? Can you access (read/write) to the drives locally on your ubuntu machine? If this is the case you'll first need to install samba (if not already). If you can't access the drives locally you'll need to mount them via your fstab...as I said for filetype are they NTFS, ext3?

```
sudo apt-get install samba
```

Then you'll need to edit your samba config

```
sudo gedit /etc/samba/smb.conf
```


I'd follow the guide where I linked over at Ubuntu Guide, but basically you'll want to add something like this for one of your shares

```

[Group]
  comment = Group Folder
  path = /media/hdb_content
  public = yes
  writable = no
  valid users = system_username1 system_username2
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

```

---

### Post by payneardo on 2007-05-18
cheers that looks good they are ext3 drives but everytime I reboot they disapear and I have to reformat to get them back but then again I must be doing something wrong, I guess I have to mount them so they keep coming up.

Do I create the share first or does that command create it, I am sorry but this is my first time with linux, last time I tried it I ditched and went back to windows but this time I am going to crack it :)

This bit I am confused with ??  If I have a hard disc called /dev/hdb, how do i use it in this context ??

Cheers

dave

Mounting Automatically 
Create mountpoint: 

sudo mkdir /mnt/files
Edit configuration: 

sudo vi /etc/fstab
Add something similar to below: 

192.168.1.1:/path/to/shared/files /mnt/files nfs rsize=8192,wsize=8192,timeo=14,intr
Test new configuration: 

sudo mount /mnt/files

---

### Post by payneardo on 2007-05-18
bump :)

please help :) :KS

---

### Post by RichGuk on 2007-05-18
Hello,

sorry I went to an exam, back now..

Well they should have been created/formated if that is the case then add something like this to your fstab (this is taken from mine, and changed to suite you :p):

```
/dev/hdb /mnt/files ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 0
```

:)

to test it works you can type

```
sudo mount -a
```

Then try going into /mnt/files and seeing if you can read/write to that drive :p

---

### Post by payneardo on 2007-05-18
excellent thanks v much wil try that when I get home later, was worried I might have to put vista basic back on :(

thanks for your help :):guitar:

---

### Post by RichGuk on 2007-05-18
No problems.....glad too :D

---

