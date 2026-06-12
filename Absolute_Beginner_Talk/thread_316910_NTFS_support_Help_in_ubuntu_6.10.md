---
title: "NTFS support Help in ubuntu 6.10"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Copperteeth on 2006-12-11
I am a new and hopeful Linux user! I just installed ubuntu last night and the first thing i wanted to do is listen to some music. However, all my music is on my other hard drive but its in ntfs format! So far i googled to find out how i can access my files and i came up with a page that looked very helpful. Anyway, i followed these instructions:

 Via the command line:

mkdir /mnt/windows
mount /dev/hda1 /mnt/windows -t ntfs -o umask=0002,nls=utf8

so i opened up terminal and i copy and pasted those commands, however it told me the following:

mkdir: cannot create directory `/mnt/windows': Permission denied

hmm thats not right? so basically how do i give myself permission to create that directory or whatever i need to do so it will do what its meant to do.

so far from what i've read about all the windows alternative programs (ie open office) Linux may become my os of choice, but for me to make the first step to becoming a Linux user, i gotta get all my files! lol
any help people?

---

### Post by taurus on 2006-12-11
```

sudo mkdir /mnt/windows
sudo mount /dev/hda1 /mnt/windows -t ntfs -o umask=0222,nls=utf8

```

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Copperteeth on 2006-12-11
ok i pasted those commands, i didnt get any errors so im assuming it worked. but now where are my harddrives saposed to show up? im viewing the computer:// location and all i see are my floppy, 2 dvd drives ,my filesystem and for some reason a floppy1 drive? Did somthing happen that wasnt saposed to?

---

### Post by taurus on 2006-12-11
```
ls -la /mnt/windows
```

---

### Post by Copperteeth on 2006-12-11
THANK YOU SO MUCH! now if i wanted it to mount on startup what should i do because i have no clue where to start

---

### Post by taurus on 2006-12-11
The link from my post shows you how to do it but you need to add this line to the end of /etc/fstab...

```

/dev/hda1  /mnt/windows  ntfs  nls=utf8,umask=0222  0  0

```
You can edit /etc/fstab with an editor like

```
gksudo gedit /etc/fstab
```

---

### Post by Copperteeth on 2006-12-11
well i tryed to follow that page but i found it most confusing tbh, i want to mount hdb1 but i cant seem to figure it out! help please!

---

### Post by taurus on 2006-12-11
Now you want to mount /dev/hdb1 besides /dev/hda1!  What filesystem is it and where do you want to mount it to?

---

### Post by Copperteeth on 2006-12-11
hdb1 is ntfs, i want to mount it to /mnt/storage

---

### Post by taurus on 2006-12-11
Add this line to the end of /etc/fstab then.

```

/dev/hdb1  /mnt/storage  ntfs  nls=utf8,umask=0222  0  0

```
Then, create a mount point and mount it.

```
sudo mkdir /mnt/storage
sudo mount -a
df -h
```

---

### Post by Copperteeth on 2006-12-11
bash: /dev/hdb1: Permission denied

---

### Post by taurus on 2006-12-11
> **Copperteeth said:**
> bash: /dev/hdb1: Permission denied
What did you run to get that error message?

---

### Post by Copperteeth on 2006-12-11
in terminal i typed

/dev/hdb1  /mnt/storage  ntfs  nls=utf8,umask=0222  0  0

and i got

bash: /dev/hdb1: Permission denied

---

### Post by taurus on 2006-12-11
> **Copperteeth said:**
> in terminal i typed

/dev/hdb1  /mnt/storage  ntfs  nls=utf8,umask=0222  0  0

and i got

bash: /dev/hdb1: Permission denied
No, no, no.  You need to edit /etc/fstab and add that line to the end of it, just like you did with /dev/hda1...

```
gksudo gedit /etc/fstab
```

---

### Post by Copperteeth on 2006-12-11
Thank you so much! it works, i made a launcher on the desktop to go to /mnt but one question, will those drives mount on startup automaticly and should i add

sudo mkdir /mnt/storage
sudo mount -a
df -h

to 

gksudo gedit /etc/fstab

or is that a one time thing?
right now

gksudo gedit /etc/fstab

looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=bd2d841c-6398-4969-8696-fe61b4494e24 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=bb3a1e8d-3c07-42f8-a130-0c0cf5d1b394 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1  /mnt/windows  ntfs  nls=utf8,umask=0222  0  0
/dev/hdb1  /mnt/storage  ntfs  nls=utf8,umask=0222  0  0

is all that right? or should i fix anything, if not thanks a lot!

---

### Post by taurus on 2006-12-11
Everything looks good in /etc/fstab.  And each time you boot your Ubuntu, those two partitions will be automatically mounted on /mnt/windows & /mnt/storage, respectively, waiting for you to access them.  

So, reboot and see them with this command!

```
df -h
```

---

