---
title: "External Hard-Drive Permissions"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by PricklySponge on 2006-10-16
When I try write to my external hard drive it tells me 

" Error while copying to......." " You do not have permissions to write to this folder"

How do I get the Permissions to write to it?

Thanks, 
PricklySponge

---

### Post by gustolove on 2006-10-18
Right Click Empty Space in Folder on Ext Hard Drive > Scripts > root-nautilus-here

see if you are able to write copy into the folder that opens up then.

if you are unable to then it may be that the external hard drive is formatted as NTFS or something that is difficult for Ubuntu to write to.

---

### Post by mcduck on 2006-10-18
> **gustolove said:**
> Right Click Empty Space in Folder on Ext Hard Drive > Scripts > root-nautilus-here

see if you are able to write copy into the folder that opens up then.

if you are unable to then it may be that the external hard drive is formatted as NTFS or something that is difficult for Ubuntu to write to.
That's not going to work unless PricklySponge has installed a nautilus script you used.. :)

As long as it's not formatted in NTFS (or FAT, but then you wouldn't have any permission problems) you can do this:

1. press ctrl-f2 and type 'gksudo nautilus'
2. enter your password
3. in the nautilus window that opened browse to your external drive and make a new directory
4. right-click on the new directory's icon, select 'Properties' and on the 'Permissions'-tab change the directory's owner & group to your user.
5. Close the nautilus window, it's running with root permissions and you don't want to have it open if it's not absolutely needed as you can easily  break your system with it..

Now you have a directory where you can read/write as your user..

---

### Post by dislocated on 2008-07-11
Reference: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/185729](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/185729)


This seems to be a known bug. I have the same problem, and here is my workaround:

I installed the file "Dolphin" file manipulation program, and it doesn't seem to have any problem moving external folders around. It must be a bug in Nautilus and not in Samba.

Hope this helps.

---

### Post by dislocated on 2008-07-12
After having played with the problem a little more, I've discovered that if I modify the /etc/fstab file and permanently mount the external drive, then Nautilus doesn't seem to have any problem in copying the folders any more.

My NAS is located at //192.168.1.100/ and I wanted to mount it at /media/backup so this is what I added to fstab:

```
//192.168.1.100/Volume_1 /media/backup cifs guest,uid=1000	0	0
```

It works like a charm now!

---

