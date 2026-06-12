---
title: "have write permission but still can't write"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by blent07 on 2006-09-29
I've had a partition hda3 (named bob) that i've used as storage for files. It's FAT and i've been using it for a while now. But all of the sudden I can't write to it? It's still mounted, though.
Under System -> Admin. -> Disks, it says it's accessible and in its Properties Permissions tab, it has all nine options checked, so anyone can read/write. My 'mount' command is as follows:

> trevor@Trevor-home:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hda2 on /media/windows type ntfs (rw,nls=utf8,umask=0222)
/dev/hda3 on /media/bob type vfat (rw,iocharset=utf8,umask=000)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

And the fstab is:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2       /media/windows ntfs  nls=utf8,umask=0222 0    0
/dev/hda3       /media/bob vfat  iocharset=utf8,umask=000  0    0
/dev/sda1       /mnt/ipod vfat user,noauto,umask=000 0 0
/dev/sda        /media/floppy auto defaults,umask=0,gid=46 0 1


The only thing I can think I've changed is when I added the last /dev/sda to be able to mount my floppy, cuz that was a pain to get working. So I removed this line and used the command: 'sudo mount -a' and nothing changed, so I put it back in fstab.


I have no idea what could have prompted this? Any ideas?

---

### Post by nthdegree on 2006-09-29
/dev/hda3 on /media/bob type vfat (rw,iocharset=utf8,umask=000)

My hunch is the umask,  try UID=1000,GID=1000,noauto,user as your options in the fstab

---

### Post by bodhi.zazen on 2006-09-29
Your unmask need an additional zero

/dev/hda3 /media/bob vfat iocharset=utf8,umask=0000 0 0

I advise you use:


/dev/hda3 /media/bob vfat auto,users,rw 0 0

---

### Post by blent07 on 2006-09-29
neither option worked if i changed it and used 'sudo mount -a'

unless i would have to reboot to make the changes take effect.

secondly, the fstab entry that i have has worked for a month or two and the umask with only three zeros is the entry in Ubuntu wiki.

??

---

### Post by bodhi.zazen on 2006-09-29
have to as the obvious, 

umount and then re-mount ?

---

### Post by blent07 on 2006-09-29
...
naturally. of course now it appears in Nautilus w/ that little pencil and the line through it saying i can't write, but i can't write to it fine after umounting and re-mounting.


thanks for keeping me awake.

---

### Post by blent07 on 2006-09-29
incredibly interesting: it turns out apollon does it. i have apollon configured to download to hda3 (bob) and it's been acting weird lately. 
when it opens, it pauses all the downloads AND makes me not allowed to write to hda3. 

anyone else find that weird?

---

### Post by thojoh on 2006-10-14
hi blent07 and others,


I have the same weird problem:

Usually, I can write and edit my sda5 (FAT32) partition with no problem whatsoever, but recently, I encountered the same problem as blent07:

I start up the computer and everything is normal and then all of a sudden, this icon with the pencil that is crossed to indicate 'read-only' is appearing in Nautilus and I cannot move or delete files anymore.
I found out that with me it is at least bittornardo that is causing this problem. When bittornado downloadstsomething to sda5, it sometimes causes this change in write-permission (curiously, the current download goes on fine, but any new download I try to initiate with bittornado is stopped because it says it cannot write to sda5) 

Permissions don't change, but still the system stops me from writing to that partition.To show that it is no problem of the permissions, here my fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat iocharset=utf8,rw,user,exec,umask=000 0 0
/dev/sda2       /media/sda2     ntfs nls=utf8,user,auto,umask=0222 0 0
/dev/sda5       /media/sda5     vfat iocharset=utf8,rw,user,exec,umask=000 0 0
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

And as I said, I use Ubuntu now for more than a year and I usually don't have any permission problems with this configuration.
So it must be something that Bittornado does (but maybe it is a general problem of a download action to a FAT 32 partition (as blent07 reports it about apollon). So that would maybe mean that it is a ubuntu or nautilus bug that could be fixed in the future. But I am no expert, so I don't know.

Does anyone else know about this problem?

If there is no solution to this at the moment, maybe there is a clever linux user here who can advice me how to make a one-click bash-file that unmounts and remounts my sda5 partition, because that seems to be what I can do to manually repair the problem when it occurs. 
At the moment I cannot figure out how to unmount sda5 properly, because the system soemtimes tells me that the device is busy (while I think I closed all applications working with that partition). Is there something I forget?
 How can I make this work?

thanks for any help 8) 

thomas

---

### Post by bodhi.zazen on 2006-10-14
> **thojoh said:**
> If there is no solution to this at the moment, maybe there is a clever linux user here who can advice me how to make a one-click bash-file that unmounts and remounts my sda5 partition, because that seems to be what I can do to manually repair the problem when it occurs. 
At the moment I cannot figure out how to unmount sda5 properly, because the system soemtimes tells me that the device is busy (while I think I closed all applications working with that partition). Is there something I forget?
 How can I make this work?

thanks for any help 8) 

thomas

Not sure 'bout the problem. :-({|=

Bash script is EASY ! :twisted:

> #! /bin/bash
umount /media/sda5
mount /media/sda5

[list=number][*]Save this in your home folder, perhaps under ~/bash_scripts, and make it executable:```

mkdir ~/bash_scripts
gedit ~/bash_scripts/remount
```
[indent]Now copy-n-paste.
Save and exit.[/indent]
```
chmod a+x ~/bash_scripts/remount
```
[*]Now add a menu item, desktop icon, or launcher.
> Name = Remount
Command = ~/bash_scripts/remount[/list]

8-)

---

### Post by blent07 on 2006-10-15
> At the moment I cannot figure out how to unmount sda5 properly, because the system soemtimes tells me that the device is busy (while I think I closed all applications working with that partition). Is there something I forget?

Sometimes a program has grabbed the partition that you wouldn't expect. I have to close not only Apollon, which causes the problem, but also Amarok, even though Amarok wasn't playing anything, especially not from that partition. Nevertheless, it looks at music on there, so it had a hold on it and I had to close it. Try closing any programs that might look at any files you store on your sda5, then umount and re-mounting.

---

### Post by thojoh on 2006-10-16
Thanks, bhodi.zazen for the bash walkthrough! 
Don't I need to give root permissions in the bash script? (because if I unmount with the terminal typing "umount" I have to use sudo) Or is a bash script automatically 'root'?

thanks for the info bent07; I realise that my problem is actually more complex: As I described, at some point while downloading things to sda5 with bittornado, the program causes sda5 to become "read-only" (but I still couldn't figure out at precisely which point - sometimes I can use bittornado without anyhting happening, sometimes it does happen). 
In any case, once it happens I would have to close all downloads in order to unmount/remount (stop activity on sda5), and then start up the downloads again, which might cause bittornado to do exactly the same thing again. (its a classical viscious circle!  :rolleyes:  :-k   )

Anyway, I hope my computer will just grow out of it over time (behave like a patient parent is maybe the best stance to take)   ;)

but if you have any new insights, keep me posted.
 
all the best,

thomas

---

### Post by bodhi.zazen on 2006-10-16
> **thojoh said:**
> Thanks, bhodi.zazen for the bash walkthrough! 
Don't I need to give root permissions in the bash script? (because if I unmount with the terminal typing "umount" I have to use sudo) Or is a bash script automatically 'root'?

Try:```
sudo umount /media/sda5
mount /media/sda5
```
The sudo command unmounts sda5, the second command mounts the partition as a user.

If that works, the script will work.

If it does not work we will need to edit fstab, although I looked over your fstab (again) and it looks fine....

One thing I forgot, you will need to add ~/bash_script to your path, or copy/move remount into a directory in your path, or create a link.

Let's try something new...

```
sudo ln -s /home/user_name/bash_scripts/remount /usr/bin/remount
sudo chmod a+x /usr/bin/remount
```

Now, you should be able to run the remount script from a terminal:```
remount
```

For you command in a desktop icon/menu/launcher you can use /usr/bin/remount

---

