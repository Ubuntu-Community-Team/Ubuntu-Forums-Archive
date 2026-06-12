---
title: "Feisty &amp; Samba share on lan"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Gus_T_Reer on 2007-05-10
Hello,
I'm new to Ubuntu and I was wondering if someone could help me with sharing a Windows folder on feisty.
I am dual booting with XP and have installed Ubuntu on a second ide drive. The Windows drive has 2 partitions: an NTFS partition for system files and a FAT32 partition for files to share between Ubuntu and Windows. The NTFS partition is mounted as /windows/system and the FAT partition is mounted as /windows/share. As my user I can access the files and folders on both partitions no problem both through file manager and using applications. The /windows/share partition and the folders within it have an owner of root and group of plugdev. Both the owner and group have create and delete permissions, others do not have any permission.
What I want to do is share certain folders (read access only) within the /windows/share partition with other (Windows) users on my lan using samba without the need for them to log on (guest ok?).
Ok, here's the peculiar part: Using Nautilus, I can right click on /windows/share which shows up as a folder and share the folder (partition) without a problem. However, if I right click to share a folder within the partition it asks me for the su password and then comes up with the message "The folder contents could not be displayed. error accessing 'file:///windows/share/folder_name': Access denied". I don't understand this as the permissions appear to be the same for /windows/share and the folders and files within the partition yet it will allow me to share one but not the other.
I tried setting myself up in the samba password list (smbpasswd -a user, smbpasswd -e user) but that didn't have any effect so I tried (in Terminal) sudo shares-admin --add-share=/windows/share/folder_name but that came up with the same access error as before.

fstab is mounting the partitions with the following lines:

# /dev/sda2
UUID=xxxx-xxxx  /windows/share  vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=xxxxxxxxxxxxxxxx /windows/system ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

I have looked at this: [https://wiki.ubuntu.com/ComprehensiveSambaGuide?highlight=%28samba%29](https://wiki.ubuntu.com/ComprehensiveSambaGuide?highlight=%28samba%29) but this is about accessing a windows share from Ubuntu and this: [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba) which unfortunately didn't work for me.

If anybody could give me guidance on how to share a folder with guest access on my home lan, I'd appreciate it very much.


PS. As an aside: when I got the permissions error message I also got another interactive box up which to all intent and purpose looked like the system was still allowing me to share the folder I wanted. If I went ahead and shared the folder then the system actually shared the higher level, ie. the whole partition. This to me seems like a rather dangerous bug.

---

### Post by [S|G] on 2007-05-10
Can you read the files as user "nobody"? You could try to change the umask option on your fstab to 003, so that all users would have read permission (the files should become 774)

---

### Post by Nythain on 2007-05-10
if you dont want them to have to login at all, and just be able to access it without complication, you are going to want to change security to share instead of user... i had to start over from scratch with my /etc/samba/smb.conf to get it to work right in feisty (kubuntu)
my current smb.conf with shares a folder /data with all my lan mates and gives them read write create delete access looks about like this:
```

[global]
workgroup = WORKGROUP
security = share

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
security = share
restrict anonymous = no
domain master = no
preferred master = no

[stuff]
case sensitive = no
guest ok = yes
path = /data/
read only = no

```
you could use that as a base and edit it to meet your needs

---

### Post by Gus_T_Reer on 2007-05-11
Hi Guys, thanks very much for the replies.

In the end I amended fstab to assign the partition with a umask of 000, I'm gonna have to play around with this to see what are the minimum permissions I can get away with but the fact seems to remain that 'others' need to have at least read permission as you say SIG.

As regards samba, I managed to get swat working using a combination of this thread: [http://ubuntuforums.org/showthread.php?t=58434&highlight=swat](http://ubuntuforums.org/showthread.php?t=58434&highlight=swat) and this page: [http://www.go2linux.org/node/98](http://www.go2linux.org/node/98). The last one may be enough but the thread gave me an insight to the problems people have been having getting swat working. Oh, and this gives a basic description of fstab: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Anyway in the end I ended up with the following smb.conf:

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2007/05/11 10:31:20

[global]
	workgroup = xxxxxxxxxx
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[shared_folder]
	comment = sex & drugs & rock'n'roll
	path = /windows/share/Scores/
	guest ok = Yes
	hosts allow = xxxxxxxx, xxxxxxxx, xxxxxxx

[transfer docs]
	comment = docs to be transferred
	path = /windows/share/Transfers/
	guest ok = Yes
	hosts allow = xxxxxxx, xxxxxxx, xxxxxxxxx

The printer stuff I don't need and I'll have to do some security work but otherwise everything's working.
Although I'm new to Ubuntu I have used other distros and Ubuntu is the easiest to get things up and running, except for samba but maybe that's because I'm used to kde. However, having said that, I think this is one area where Ubuntu/Gnome really need to get things simplified if it's to rival Windows. Otherwise, great distro.

Whatever, Thanks a lot guys. :guitar:

---

### Post by kag on 2007-05-25
I would like to add that I've been having the same problem with two FAT32 partitions.

They were both mounted with "umask=007". Changing to "umask=003" did not help, but "umask=000" worked although I consider this more like a temporary patch than a real solution.

I had also added the samba user to the plugdev group, so it should already have been working with the default "umask=007"...

I really don't understand. Could someone try to explain more precisely why it is behaving like this?

---

### Post by [S|G] on 2007-05-28
When a user connects to a samba share that allows for guest access, it access the files as the user 'nobody'. Therefore you need to either set user nobody as the owner of the files (bad for security) or allow read access to 'others'. 

Umask 003 sets file permissions to 774 (rwxrwxr--). When you mount FAT partitions you need to set the umask because FAT doesn't have a permission control system, and every file will use the umask permissions.

---

### Post by craigsn on 2007-07-05
I'm trying to get samba working with Virtual box Windows Vista guest to share an external drive connected to my feisty amd64 machine. 

Shared folders from virtual box doesn't work, I get a BSOD in Vista, somehow caused by VB. So another person suggested samba.

I also have another windows computer on the network, that used to work with my feisty install, but now after installing samba it doesn't. 

What info do you need to help me?

Thanks
Craig

---

