---
title: "Unmount doubt."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by miguelangelo1986 on 2007-06-25
I have installed Xubuntu and until now it's - despite the fact that I can't connect to the Internet - been working just fine. I noticed that, even I'm not mounting any of my Windows XP hda, my "X" partition was mounted. Well, I tried to unmounted it: right clicked on the volume and then on "Unmount volume". The following messages appeared on the screen:

Cannot unmount the volume "X":
unmount: /media/hda1 mount disagrees with the fstab.

Then I clicked OK, and the following message appeared:

Unable to unmount "X":
Unknown error.

Can anyone tell me how do I unmount this volume without prejudicing the volume unmounted in my Windows XP partition?

Thanks a lot.

---

### Post by raul_ on 2007-06-25
Could you post the output of the file /etc/fstab ?

---

### Post by miguelangelo1986 on 2007-06-25
Sorry, you will have to explain what's that. I'm new with these things.

---

### Post by php_penguin on 2007-06-25
I have a similiar problem.

Basically, Fstab has to have an entry in it for each drive in order to mount a drive, but if there is an entry in Fstab, you can't unmount it.

Catch 22, sort it for GG?

**edit**
just rememberd about mtab, how would this change the situation?

---

### Post by miguelangelo1986 on 2007-06-25
And what the hell is a fstab, hehehe?

---

### Post by Zalbor on 2007-06-25
If an entry exists in fstab, the system mounts the partition and so you (as a normal user) can't unmount it.
The things you can unmount are things like CDs and USB drives, which shouldn't have an entry in fstab. That way they're mounted by "you" right when they're inserted.

As for what fstab is, it's the file /etc/fstab. It lists what the system should automatically mount when booting.

---

### Post by php_penguin on 2007-06-25
DP i know, 

Fstab ( /etc/fstab ) contains a list of the physical drives to mount, where to mount them, and some basic info about those drives (eg filesystem).

On load, the system mounts anything in Fstab that it can, meaning that you can use them.

However, the problem is that when you try to unmount a drive, the Fstab basically says "No, it's in my list".

There may be a solution with editing the Fstab and Mtab ( /etc/mtab ), but this isn't really the user friendly solution. There is probably a GUI out there to do it all for you.

---

### Post by miguelangelo1986 on 2007-06-25
But I am the only user - shouldn't I be the Administrator by default?

---

### Post by FleetAdmiral74 on 2007-06-25
Nope, in linux (usually) you are not put in as this administrator, but as a normal user account.  If you want to know why, its for security reasons. When you need to do admin tasks, you have to input your password. Like I said, this is a very good system and makes the spread of viruses and other malware quite difficult.

this explanation is super short, if someone else has a nice link just share it, people have discussed this to no end.

---

### Post by Zalbor on 2007-06-25
No, the administrator is a "super user" that can be used by anyone who has the authority. As the single user you do have this authority, but in order to use the administrator you need to temporarily gain the rights. (commands like sudo and gksudo).
Right-clicking and "unmount" tries to do it with your own rights, not the admin's (root). To unmount something as root, you should open a terminal and run a command like "sudo umount /media/disk1", depending on where what you want to unmount is mounted, or what device it is (like /dev/hda1).

---

### Post by miguelangelo1986 on 2007-06-25
OK, got it. Certainly I'll try it.
Thanks a lot.

---

### Post by miguelangelo1986 on 2007-06-25
Just one more doubt: if I unmount this volume, which belongs to my hda1 (Windows XP), will it disappear in the Windows XP?

---

### Post by php_penguin on 2007-06-25
heres a way to unmount a drive on a one off basis (will still be mounted on reboot):

go into /media and check which one of these is the disk you want to umount (hda4 for example), then open a terminal and type (changing hda4 to whatever is right)

```
sudo umount /media/hda4
```
and type in your admin password if prompted. that should sort it temporarily

**permanent way !! DANGEROUS !!**
dont blame me if this goes wrong, but its simple enough
find which drive you want ( /media/bla ), and open a terminal, now type
```
sudo gedit /etc/fstab
```
a text file will load and you now need to check the lines for the one which contains the hardrive you want to never mount again.

there will be a series of things which look like this:
```
# /dev/sda6
UUID=B8F47D80F47D4224 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

delete whichever line has the right bit (sda6 for whatver you want).

I know this isn't very user friendly, but its the way i do it.

---

### Post by php_penguin on 2007-06-25
no, unmounting in Linux won't stop your ability to boot into Windows or access the files in Windows.

---

### Post by miguelangelo1986 on 2007-06-25
sudo unmount /media/hda1
sudo gedit /etc/fstab

Which are the problems that can occur if I choose the second otpion?
How do I identify the right lines to delete and how to delete?

---

### Post by BobCFC on 2007-06-25
linux reads fstab when it boots to know which partitions to access.  So you could stop it loading.

Post you fstab here and tell us what you are trying to achieve.


BTW sudo is good because it stops you deleting system files by accident.

---

### Post by Shazaam on 2007-06-25
IMHO a safer way to change fstab is to comment out the disk entries instead of deleting them. Put a # in front of the entries. This way you can "screw up" and still be able to fix it with a livecd. No need to remember any uuid's.

Do this-- 
# /dev/sda6
#UUID=B8F47D80F47D4224 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

(use your own entry, this is just an example)

---

