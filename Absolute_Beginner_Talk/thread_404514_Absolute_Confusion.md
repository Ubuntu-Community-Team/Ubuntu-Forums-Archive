---
title: "Absolute Confusion"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by tbuss on 2007-04-08
Okay, I don't know what else to do. I don't know if I just don't explain the problem very well or if I'm missing something.

I have been in #ubuntu, this forum, and others. I have subscribed to mailing list and have read until my eyes felt like they were going to bleed. I have failed to come up with a solution to this problem.

All I want to do is share folders on my home network using samba
I have 3 pc's all running edgy
The pc that I use has a [COLOR="Red"]external hdd attached via firewire[/COLOR]
I have [COLOR="Red"]mounted[/COLOR] this external drive with [COLOR="Red"]ntfs-3g[/COLOR]
I am able to read and write to this external drive (from pc that is attached)
I [COLOR="Red"]dual boot[/COLOR] so that is why I have chosen to use ntfs-3g
When logged into Ubuntu, I select the folder I want to share on the external hdd
When I log into another pc (Ubuntu) and go to *places -> connect to server -> windows share ->*
I type in the ip of the computer with the external hdd.
Then when I try to connect, [COLOR="Red"]nautilus shows the icon for the share, but I can't access it:[/COLOR]
[B]The folder contents could not be displayed.
"Home_Productivity" couldn't be found. Perhaps it has recently been deleted.[/B]

At that point I tried to share a folder located locally
That share works fine.
[B]
I then took a look at the smb.conf and I found both shares listed at the bottom:[/B]
```
[Home_Productivity]
path = /media/External/Home_Productivity
available = yes
browsable = yes
public = yes
writable = yes

[docs]
path = /home/tbuss/docs
comment = test share file
available = yes
browsable = yes
public = yes
writable = yes
```

**I then tried:**
```
smbclient -L //IP.OF.LINUX.BOX
```
to check the permissions on the external hdd, but I was prompted for a password and could never authenticate. I was told that samba does not handle permissions for the external hdd?

So I don't know where to go for help. Is this a[COLOR="Red"] Samba[/COLOR] issue, because I had success sharing a folder stored locally. Is this a problem with the external hdd, does it need to be [COLOR="Red"]formatted as something other than ntfs-3g?[/COLOR] If anyone has any advice, you don't have to tell me step by step, just something to get me going in the right direction: 

**I'll post the output of mount if it will help any:**
```
tbuss@tbuss-desktop:~$ mount
/dev/hdb5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/sda1 on /media/External type fuse (rw,nosuid,nodev,noatime,allow_other,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
tbuss@tbuss-desktop:~$
```

---

### Post by dstew on 2007-04-08
I have worked a bit with Samba. I had a hard problem to solve once. I was connecting to a NT filesystem at work over a VPN. I was able to mount the share, using smbmount, but I could not see any files in the folder. It eventually proved to be a problem with an unusual character (a trademark symbol) in one of the file names.

I used smbclient a lot to debug the problem. It showed me that my directory listing was messed up, and that was the clue I needed.

Anyway, when I used smbmount to mount the share, I had to use sudo, and put the username for the share, and my local userid and groupid into the smbmount command like this:

sudo smbmount //servername/sharename mountpoint -o username=*shareusername*,uid=*localusername*,gid=*localusername*

After this, it asks me first for my local user name to satisfy the sudo command. Then, it asks me for my share password. After this, I can look at the share using smbclient.

I don't know if this helps, but I saw nobody had answered your post so I felt a little sorry for you.

---

### Post by tbuss on 2007-04-08
Thanks man,

Are you familiar with the dopamine rush you get when you see that your thread has been answered? :)

I'm not sure what is going on with this drive, I can share files from any location except the external drive. I would format the drive and use something other than ntfs-3g but I dual boot into windows and need access to the files stored on the external. I'm still working on it slowly but surely.

---

### Post by freebird54 on 2007-04-08
Not sure this will help - but I have heard the CIFS is the new(er) way to access things from SAmba.  Are you using this, or smbfs?  Might make a difference.

Another thought that crosses my mind is that I use ext3 formatted partition for dual-boot access - using a Win prog Explorer2FS (or similar name) to get to and from it.  That way I get a better filesystem for my double-access stuff  :)

Hope it helps!

EDIT:  [http://linux-cifs.samba.org/](http://linux-cifs.samba.org/)

---

### Post by strabes on 2007-04-08
You can read & write ext3 in windows using the fs-driver. [http://fs-driver.org/](http://fs-driver.org/)

---

### Post by tbuss on 2007-04-08
Looks like ext3. I found some info on ext3:
> Before you can mount a partition as ext3 you have to create a journal on it. The easiest way to do it is to type:

    tune2fs -j /dev/hdaX

This can be done on an unmounted or on a mounted filesystem. If you create the journal on a mounted filesystem you will see a .journal file. Don't try to delete this and don't back this up or restore it from backup! If you run tune2fs -j on an unmounted partition an unvisible journal file will be created.
Now you can mount the filesystem as ext3 using:

    mount -t ext3 /dev/hdaX /mnt/somewhere

I'm not very familiar with the process, but this requires me to format the hard drive correct? The only reason I'm asking is that it says you can mount a partition as ext3 on a mounted filesytem.

---

