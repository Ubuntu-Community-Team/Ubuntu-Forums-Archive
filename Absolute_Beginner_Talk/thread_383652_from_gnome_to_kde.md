---
title: "from gnome to kde"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by tomxyz on 2007-03-13
Hi,

To sketch the problem, a while ago I installed dapper witch has gnome installed by default. I have an external harddisk that I didn't want to format into ext3 or fat32 because of the data on it. 
No problem, installed the ntfs-3g 'thing', changed the permissions so I had complete control over the drive. and it worked without any hick-ups.
Then I installed the KDE graphic interface on my system, it coexists, I can choose the one I want  when I login. 
Now when using KDE interface, I can not write or execute on my external drive. not even when I do sudo chmod 770 /media/sda1. Read only device it says.
I tought that the graphical interface only changed the appearence? should I reïnstall this ntfs-3g driver when changing desktop?

regards Tom

---

### Post by Najand on 2007-03-13
Do you mount your external Hard Disk Manually or using "Automount" to do so. If you do it manually try to use "rw" option for mounting it or try to mount it manually if you are not mounting it manually by yourself.
BTW, It sounds to me you haven't disable the generic ntfs driver to prevent it from loading into the kernel.

---

### Post by tomxyz on 2007-03-13
In both desktops it shows up on my desktop automatically, I will try to mount it manually and get back to you.

thanks!

---

### Post by tomxyz on 2007-03-13
Another thing I noticed, when in Gnome my harddisk is called /dev/usbdisk and is mounted in /media/usbdisk.
In KDE it's called /dev/sda1 and is mounted in media/sda1. When in KDE I also see the folder USBDISK in the media folder but when I try to mount /dev/sda1 to /media/usbdisk instead of /media/sda1, it says the folder doesn't exist.

I looked in /dev and saw that root was the owner of sda1.
So I did sudo chown tom /dev/sda1 and then also sudo chgrp tom /dev/sda1.
This worked, now I am owner of sda1 and anyone who is in my group.
I tried again sudo chmod 770 /dev/sda1 > nogo > sudo chmod u+rw /dev/sda1 > nogo > sudo chmod u+rwx /dev/sda1 > nogo > sudo chmod 770 /media/sda1 > nogo ...
any idea? thanks Tom

---

### Post by Najand on 2007-03-13
Why are you trying to change the permissions of your drivers? "root" is the safest owner for devices/system files. Better not change them. Did you try mounting by "rw" option?

---

### Post by tomxyz on 2007-03-13
hi Najand,

Don't let the moderators of this site mislead you, they changed my 1 cup of ubuntu to 5 cups of ubuntu but as you can see I only have 18 beans behind my name :)
with the rw option, do you mean sudo mount rw /dev/sda1 /media/sda1? I tried that and it gives me the man page of mount so obviously I'm doing something wrong!

Tom

---

### Post by Najand on 2007-03-13
For options, use ```
sudo  mount -o <OPTIONS> <Mounting Device> <Mount Point>
```
The cups of ubuntu means almost nothing.... It is just something to have fun when using forums.

---

### Post by tomxyz on 2007-03-13
hi I read the man page of the mount command and got a little smarter yet again!
(like they say read the f* manual:) )

I typed the following into a terminal and this is what i got, 
tom@tom-laptop:~$ sudo mount -o rw /dev/sda1
mount: /dev/sda1 al aangekoppeld of /media/sda1 bezig
mount: volgens mtab, is /dev/sda1 al aangekoppeld op /media/sda1
tom@tom-laptop:~$

it says the device is already mounted or busy and in the second line it says 'according to mtab it is already mounted'.
it's not that I don't have access, but I dont have full rights when working in KDE, for example when I right click on a picture that is on the external drive I don't have the 'move to trash option'

regards tom

---

### Post by Najand on 2007-03-13
Thanks for the dutch translation.
Try to unmount  it before mounting it again.
```

sudo umount /dev/sda1

```

---

### Post by tomxyz on 2007-03-13
yeah, I figured if I can't read japanese you would probably don't read dutch. I've been in Tokyo once, for my work, awsome city, could not visit anything tough:( just a one night stop. 

Like you said, I unmounted it, then tried remounting it. I got 'can't find device'. Then I tried entering the full path and it got mounted but I couldn't access it anymore. I had to unmount it again and mount it in the graphic interface (right click) to get access again?

tom@tom-laptop:~$ sudo umount /dev/sda1
Password:
tom@tom-laptop:~$ sudo mount -o rw /dev/sda1
mount: kan /dev/sda1 niet vinden in /etc/fstab of /etc/mtab
tom@tom-laptop:~$ sudo mount -o rw /dev/sda1 /media/sda1
tom@tom-laptop:~$ sudo umount /dev/sda1
tom@tom-laptop:~$

the plot thickens! regards tom

---

### Post by Najand on 2007-03-13
Nice you liked Tokyo.
Well, try to specify the type of your device which is ntfs-3g
Like:
 ```

sudo mount -t ntfs-3g -o rw /dev/sda1 /media/sda1

```

---

### Post by tomxyz on 2007-03-13
this is what rolled out

tom@tom-laptop:~$ sudo mount -t ntfs-3g -o rw /dev/sda1 /media/sda1
fusermount: mountpoint is not empty
fusermount: if you are sure this is safe, use the 'nonempty' mount option
FUSE mount point creation error: No such file or directory
Unmounting /dev/sda1 ()
tom@tom-laptop:~$

When the drive was unmounted I looked in the folder /media/sda1 and there is a file called .created_by_pmount. (This file is not present in /media/usbdisk)

Well Najand I have to go to bed now (not because my mother says so :lolflag: , but because I have an important day at work tomorrow. I will get back on the forum tomorrow evening and check up on things. Thanks for your help so far !!!

Tom

---

