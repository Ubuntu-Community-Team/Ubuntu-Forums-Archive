---
title: "Missing Partition hda4 (&quot;/documents&quot;)"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Aurora@FleetBuzz on 2007-05-05
In order to install Edgy, I partitioned my HD along the lines of the instructions from this site:
[http://www.psychocats.net/ubuntu/installin](http://www.psychocats.net/ubuntu/installin)
First, I set it up  in four partions as follows:
hda1: XP (NFTS filesystem) 77GB
hda2: root (ext3 filesystem)5GB
hda3: swap  1 GB
hda4: documents (ext3 format)72GB

When I mounted the drives I used the following mount points as shown in the link:
hda1:  /windows
hda2: /
hda3: swap
hda4: /documents

After the install, I can't seem to access the hda4 drive.  From the terminal a check shows it's there:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2              5281348   2366696   2646368  48% /
varrun                  257696        80    257616   1% /var/run
varlock                 257696         0    257696   0% /var/lock
procbususb               10240       104     10136   2% /proc/bus/usb
udev                     10240       104     10136   2% /dev
devshm                  257696         0    257696   0% /dev/shm
lrm                     257696     17580    240116   7% /lib/modules/2.6.17-11-generic/volatile
/dev/hda4             71813692    184480  67981256   1% /documents
/dev/hda1             76870988  20264584  56606404  27% /windows

Also, when I check in Disk Usage Analyzer, it only shows that I'm using 14% of 21.8 GB!

Is there a way I can map it so that the software, like Openoffice & Gimp, know it's there?

I know I probably should have set it up as FAT 32, but I'd rather not do the install again!

---

### Post by [bigmac] on 2007-05-05
The link does not work...

is /dev/hda4 in /etc/fstab?

---

### Post by Aurora@FleetBuzz on 2007-05-05
Here's the link to the start page:
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
Click on "Install Desktop CD Ubuntu" on the left and it will take you to to the page.

I don't understand your question: " is /dev/hda4 in /etc/fstab?"
What is "/etc/fstab"?

---

### Post by Aurora@FleetBuzz on 2007-05-05
I finally found the etc/fstab file.  Here's a copy of the contents.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=5187c302-97c4-49a9-b6db-a897e08e9b4d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=677cc78c-5244-4b48-b3d4-89319b71b199 /documents      ext3    defaults        0       2
# /dev/hda1
UUID=EEDC0A88DC0A4B73 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=16c67b09-f347-4e18-b19f-12dbabe4eb9d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

There's an error showing under hda2.  What does this mean?  

Appreciate any advice.

---

### Post by [bigmac] on 2007-05-06
The "errors" thing in fstab file under hda2 is normal, don't be concerned about it, maybe someone can explain it..

But if you open terminal and write:

```
sudo mount /documents
```

What happens then?

Or if you write 
```
cd /documents
```

Does it say some errormessage?

---

### Post by Aurora@FleetBuzz on 2007-05-06
> **'[bigmac] said:**
> 
But if you open terminal and write:
```
sudo mount /documents
```
What happens then?

It shows the drive is already mounted!
> mount: /dev/disk/by-uuid/677cc78c-5244-4b48-b3d4-89319b71b199 already mounted or /documents busy
mount: according to mtab, /dev/hda4 is already mounted on /documents


> Or if you write 
```
cd /documents
```
Does it say some errormessage?
Not at all!  It says:
> donj@DonandNaome:/documents$ 

Is the drive then properly mounted and accessible?  If so, why can't I get it to show as a place to save files, etc?

BTW, you have been a great help so far!  This newbie is much obliged.

---

### Post by junjan on 2007-05-06
What about the permissions? Perhaps that partition can be seen only by root user, then you will not see it. 

Check this out:
```
ls -la /documents
```

Who is the owner? root? Then you should change the permissions.

---

### Post by Aurora@FleetBuzz on 2007-05-06
> **junjan said:**
> What about the permissions? Perhaps that partition can be seen only by root user, then you will not see it. 
Check this out:
```
ls -la /documents
```
Who is the owner? root? Then you should change the permissions.

I did as you suggested.  This is what I got:
> donj@DonandNaome:~$ ls -la /documents
total 24
drwxr-xr-x  3 root root  4096 2007-05-04 12:24 .
drwxr-xr-x 23 root root  4096 2007-05-04 18:20 ..
drwx------  2 root root 16384 2007-05-04 12:24 lost+found
donj@DonandNaome:~$ 

Is root the owner?  Do I need to change permissions?  If so, how do I do this?  If not, then could you please suggest what else might be the cause?

Thank you for your answer and assistance!

---

