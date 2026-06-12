---
title: "Help with a floppy drive?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Nostromo on 2006-09-14
Could someone give a hand with a floppy drive issue? I really am an absolute beginner.

I managed to get Ubuntu 6.06 to recognise the floppy drive - if I recall I had to change a line in something called fstab? The problem is that when I try to mount it, I'm told that 

"Unable to mount the selected floppy drive. mount: special device /dev/fd0 does not exist
"

Someone said that the problem might have something to do with a disk formatted in Windows. I only need floppies to transport texts between this Ubuntu and an old laptop with Windows '95...

If you can help me, please describe the process thoroughly. I'm not familiar with the terminal. Thanks in advance!

---

### Post by bodhi.zazen on 2006-09-14
Put a floppy in the drive first.

Then mount.
```
sudo mount -t vfat /dev/fdo /mnt/floppy
```

---

### Post by Nostromo on 2006-09-14
Thanks for a quick answer. However, it didn't work, I probably have a broken disk. 

"mount: mount point /mnt/floppy does not exist"

If I get it to work, is there a way to make it permanent? Of course I can always go to terminal, but I just have difficulties remembering the commands.

---

### Post by steve.horsley on 2006-09-14
You have to make the mount point:
**sudo mkdir /mnt/floppy**
although personally, I would rather use /media/floppy because I think it would then show up on your desktop.

I would expect /dev/fd0 to exist. Try this command, which loads the floppy driver (just in case it isn't already loaded):
**sudo modprobe floppy**
and then try to mount the floppy again.

---

### Post by bodhi.zazen on 2006-09-14
sorry, do this first:

sudo mkdir /mnt/floppy
sudo chmod 777 /mnt/floppy

Then mount your floppy as above.

Post fstab (/etc/fstab) for advice on perminancy.

---

### Post by steve.horsley on 2006-09-14
> 
sudo mkdir /mnt/floppy
sudo chmod 777 /mnt/floppy


What is the chmod for? Root can mount it anyway, and I thought the read/write mode once it wasa mounted was controlled by the umask option in the mount command.

---

### Post by bodhi.zazen on 2006-09-14
I do not have a reason other then "it works". Without chmod I have had problems with rw access to partitions (as a user) once mounted (as root owns the mount point). I think this is due to the permissions of the mount point, thus the chmod. Perhaps 666 would be more secure.

If you would be so kind as to comment further, perhaps I have been going about this all wrong.

---

### Post by steve.horsley on 2006-09-15
Just trying to learn myself. I'll have to do some experiments when I get the time.

---

### Post by Najand on 2006-09-15
I think when you mount a partition or device or file to a mountpoint, the mount command changes the permisson of the mountpoint folder to what it is defined in the mount command.

---

### Post by bodhi.zazen on 2006-09-15
> **steve.horsley said:**
> Just trying to learn myself. I'll have to do some experiments when I get the time.

You peaked my curiosity......

As it turns out you can use either the option "user" or unmask in fstab and do not have to set anything else....

sudo mkdir /mnt/usb (I hate icons on my desktop......)
owner will be root:root


Example:```
/dev/sdb4       /mnt/test       vfat    user    0 0
```

Now a user can mount the usb drive with mount /mnt/usb.

> bodhi@Arch:~$ sudo mkdir /mnt/test
bodhi@Arch:~$ ls -l /mnt/ | grep test
drwxr-xr-x  2 root root  4096 2006-09-15 01:55 test
bodhi@Arch:~$ mount /mnt/test/
bodhi@Arch:~$ ls -l /mnt/ | grep test
drwxr-xr-x  3 bodhi users 16384 1969-12-31 17:00 test
bodhi@Arch:~$ ls /mnt/test/ | grep test_file
bodhi@Arch:~$ touch /mnt/test/test_file
bodhi@Arch:~$ ls /mnt/test/ | grep test_file
test_file
bodhi@Arch:~$ echo "Hi Steve" >> /mnt/test/test_file
bodhi@Arch:~$ cat /mnt/test/test_file
Hi Steve
bodhi@Arch:~$ rm /mnt/test/test_file
rm: remove regular file `/mnt/test/test_file'? y
bodhi@Arch:~$ umount /mnt/test/
bodhi@Arch:~$ ls -l /mnt/ | grep test
drwxr-xr-x  2 root root  4096 2006-09-15 01:55 test
bodhi@Arch:~$

No need for umask, although you could change the permissions with umask to prevent executables, which would be more secure.

ex```
/dev/sdb4       /mnt/test vfat user,umask=0033 0 0
```

Now yields:> bodhi@Arch:~$ ls -l /mnt/ | grep test
drwxr-xr-x  2 root root  4096 2006-09-15 01:55 test
bodhi@Arch:~$ mount /mnt/test/
bodhi@Arch:~$ ls -l /mnt/ | grep test
drwxr--r--  3 bodhi users 16384 1969-12-31 17:00 test
bodhi@Arch:~$ touch /mnt/test/test_file
bodhi@Arch:~$ echo "Hi Steve" >> /mnt/test/test_file
bodhi@Arch:~$ cat /mnt/test/test_file
Hi Steve
bodhi@Arch:~$ rm /mnt/test/test_file
rm: remove regular file `/mnt/test/test_file'? y
bodhi@Arch:~$ umount /mnt/test/
bodhi@Arch:~$ ls -l /mnt/ | grep test
drwxr-xr-x  2 root root  4096 2006-09-15 01:55 test
bodhi@Arch:~$

HTH  :roll: :roll: :roll:

---

### Post by Nostromo on 2006-09-15
Still no reaction. I did these:

antti@mordbuntu:~$ sudo modprobe floppy
Password:
antti@mordbuntu:~$ sudo mount -t vfat /dev/fdo /mnt/floppy
mount: mount point /mnt/floppy does not exist
antti@mordbuntu:~$ sudo mkdir /mnt/floppy
antti@mordbuntu:~$ sudo chmod 777 /mnt/floppy
antti@mordbuntu:~$ sudo mount -t vfat /dev/fdo /mnt/floppy
mount: special device /dev/fdo does not exist
antti@mordbuntu:~$

steve.horsley:
> You have to make the mount point:
sudo mkdir /mnt/floppy although personally, I would rather use /media/floppy because I think it would then show up on your desktop.

Do you mean /media/floppy would come instead mnt/floppy, after sudo mkdir?

---

### Post by Najand on 2006-09-15
It is "fd0" (f-d-Zero), not fdo (f-d-O),

---

### Post by Nostromo on 2006-09-15
Thanks, Najand. I should have known *that*, though probably I'll do such mistakes for the next ten years!

---

### Post by Najand on 2006-09-15
We all mistake... Anyway, with "fd0" 
could you mount the floppy disk or not?

---

### Post by Nostromo on 2006-09-15
Even with zero the terminal says the same as GNOME: mount: special device /dev/fd0 does not exist

Damn.

---

### Post by Najand on 2006-09-15
Ok, Can you copy and paste the output of the following command here?
```

[FONT=Franklin Gothic Medium] fdisk -l[/FONT] 

```

---

### Post by Nostromo on 2006-09-15
fdisk -l gave no reaction BUT I'm afraid I've bothered you for wrong reasons. It appears that the floppy drive may not be physically connected at all.

Anyway, great to get such quick response - I believe I'll need it in the future, too. Thanks!

---

### Post by Najand on 2006-09-15
Hmm, that is strange....  fdisk -l should show all your Hard Disks connected to your  computer as well as your Root Partition, Swap Partitions and so on... 
Is your Floppy Drive a USB one?

---

### Post by Nostromo on 2006-09-15
Ok, that sounds strange.

I have USB drive which I haven't even tried yet. At the moment my problem is/was the 3,5" diskette drive, that I'd need to trasnport files from an old laptop with Widows '95. So far I've only saved files on the internal hard disk of this Ubuntu-using computer (I'm not very familiar with the English terminology, so I hope I use correct words, e.g. hard disk).

I contacted the guy from whom I got the computer, and he didn't remember connecting the floppy drive (fd0), and I was told to check something in the terminal - apparently there were no traces of the drive.



Darn. After writing all that I tried sudo fdisk -l. Like I said, I'm an absolute beginner... But at least I figured that out myself :) 

Results:
antti@mordbuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081   83  Linux
/dev/hda2            4866        5005     1124550    5  Extended
/dev/hda5            4866        5005     1124518+  82  Linux swap / Solaris

---

### Post by steve.horsley on 2006-09-15
> **Nostromo said:**
> fdisk -l gave no reaction BUT I'm afraid I've bothered you for wrong reasons. It appears that the floppy drive may not be physically connected at all.

Chuckle. That would explain it. I think that the Linux kerenel creates the /dev/fd0 device during boot-up if it sees a floppy disk drive. So I was thinking that the absence of /dev/fd0 meant the driver wasn't being loaded.

---

### Post by bodhi.zazen on 2006-09-15
Steve: FYI: whith the fstab umask options I posted a user can mount, but not unmount the partition.

---

### Post by maccatracca on 2006-09-15
run:   MAKEDEV -v fd0

this should create the fd0 directory under /dev/

sudo mount -t vfat /dev/fdo /mnt/floppy

macca

---

### Post by Scunizi on 2006-09-15
I've got basically the same issue with a twist.  I've got the floppy mounted in /media/floppy using 

sudo mount -t vfat /dev/fdo /media/floppy 

and it appears on the desktop as expected.  I can open it and see files but can't delete them without using sudo.  My fstab line for the floppy reads..

/dev/fd0 /media/floppy auto defaults,umask=0777,gid=46 0 1

I've also tried ...


/dev/fd0 /media/floppy vfat rw,user,noauto

Now from the Wiki I tried  

/dev/fd0 /media/floppy	auto rw,users,noauto,fmask=111,dmask=000 0 0

The second one allowed me to mount the floppy manually.  The first did it automaticaly.  The third can be mounted manually and read but not written to.

When I go to System/Admin/Disks after mounting the floppy I am not able to get any information on it.  The icon is there but no data.  In all cases I've inserted a floppy into the drive.

I'd sure like to have write permission on this drive as I'm attempting to do some grub stuff for VMWare.

Any other ideas?

EDIT:  First and second notations above I reversed in the line for what they did which is why second is mentioned first and first second. Descriptors read correctly now.

---

### Post by Scunizi on 2006-09-15
Sorry for the double post but I thought this was important enough that I didn't want a second EDIT of my previous post to go unnoticed.  

After using the Wiki instructions and rebooting, the floppy did not appear on the desktop as expected so I had mounted it manually using the line stated in my previous post and couldn't get permission to write to the drive.  However after unmounting it and going to Places/Computer and double clicking on Floppy, it mounted with full read/write permissions.  VIOLA!  It now works.  Hopefully it will for you too!:biggrin:

---

### Post by xpod on 2006-09-15
> If I get it to work, is there a way to make it permanent? Of course I can always go to terminal, but I just have difficulties remembering the command

If your like moi...and have a brain like a seive then it`s a good idea to create a little "text file" and keep copies of ALL the commands you learn.
 also keep a little note of the problems you encounter and how you fixed them.

Im 37 and still need a note when the wife or kids send me to the shops:-\"

---

### Post by steve.horsley on 2006-09-15
> **Scunizi said:**
> I can open it and see files but can't delete them without using sudo.  My fstab line for the floppy reads..

/dev/fd0 /media/floppy auto defaults,umask=0777,gid=46 0 1



Any other ideas?


Yes - the umask is the inverse of the bits you want in the file mode, so to allow read/write/execute for everyone you need a umask of 0.

---

### Post by Scunizi on 2006-09-15
You must mean something like the attached.  VERY easy todo with the right program!  If your interested go to Synaptic and install VYM. There is a newer version (of course) that's not in the libraries.  You can download the RPM and "alien" it to a deb then install.  The newer one is much nicer.

---

### Post by Scunizi on 2006-09-15
It looked like I attached the file.  But nothing happened.  It exports to a html file. Am I able to attach a html file?

Edit:  Check out [http://www.insilmaril.de/vym/](http://www.insilmaril.de/vym/).  It's called mindmapping.

---

