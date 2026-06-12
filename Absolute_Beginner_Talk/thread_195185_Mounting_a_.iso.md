---
title: "Mounting a .iso"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by xxrealmsxx on 2006-06-12
I am trying to mount a .iso file that I have downloaded, is there a way to do that in Ubuntu without a 3rd party app? I believe there is but I can't seem to figure it out.

I tried: 

mount -o loop cdimage.iso /mnt/cdrom 
where /mnt/cdrom is whereever you want it mounted (where the cdrom
normally goes it a good choice)

as root but that did not work, I would prefer a method not needing root access.

Thanks in advance!

---

### Post by bluevoodoo1 on 2006-06-12
Perhaps this...
[http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning](http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning)

---

### Post by =Kevin= on 2006-06-12
Heya, try this, it worked with iso's for me:

sudo mkdir /media/iso
sudo modprobe loop
sudo mount /yourmap/youriso.iso /media/iso -t iso9660 -o loop


To unmount it you just put in the following line in the terminal:
sudo umount /media/iso

You do need the sudo command tho ;)

---

### Post by xxrealmsxx on 2006-06-12
[QUOTE==Kevin=]Heya, try this, it worked with iso's for me:

sudo mkdir /media/iso
sudo modprobe loop
sudo mount /yourmap/youriso.iso /media/iso -t iso9660 -o loop


To unmount it you just put in the following line in the terminal:
sudo umount /media/iso

You do need the sudo command tho ;)[/QUOTE]

Yeah I found the wiki and gave it a whirl, however this is what I got:

jamiewitter@jamiewitter-laptop:~$ sudo mount /home/jamiewitter/Downloads/Software/Windows XP Pro SP2 Corporate Edition/XPPROSP2.iso /media/iso/ -t iso9660 -o loop
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
jamiewitter@jamiewitter-laptop:~$ sudo unmount /media/iso
sudo: unmount: command not found
jamiewitter@jamiewitter-laptop:~$ sudo umount /media/iso
umount: /media/iso: not mounted
jamiewitter@jamiewitter-laptop:~$

I need to get a book so I can understand UNIX commands better, im sure my syntax is off in a newbish manner :-({|=

---

### Post by someusernoob on 2006-06-12
You cannot use spaces in a file- or foldername in the terminal.

/home/jamiewitter/Downloads/Software/Windows XP Pro SP2 Corporate Edition/XPPROSP2.iso

Try to rename the folder.

---

### Post by Ben Sprinkle on 2006-06-12
o easy do this

su
password*

mkdir '/media/iso'
mount -o loop '/home/*account*/iso.iso' '/media/iso'


and thats it :rolleyes:

---

### Post by bluevoodoo1 on 2006-06-12
[QUOTE=someusernoob]You cannot use spaces in a file- or foldername in the terminal.

/home/jamiewitter/Downloads/Software/Windows XP Pro SP2 Corporate Edition/XPPROSP2.iso

Try to rename the folder.[/QUOTE]

Actually... you should able to if you use \ before the space.

```
/home/jamiewitter/Downloads/Software/Windows\ XP\ Pro\ SP2\ Corporate\ Edition/XPPROSP2.iso
```

---

### Post by someusernoob on 2006-06-12
[QUOTE=bluevoodoo1]Actually... you should able to if you use \ before the space.

```
/home/jamiewitter/Downloads/Software/Windows\ XP\ Pro\ SP2\ Corporate\ Edition/XPPROSP2.iso
```[/QUOTE]
LoL, didnt knew that. Getting smarter every minute. :)

---

### Post by =Kevin= on 2006-06-12
> 
mkdir '/media/iso'
mount -o loop '/home/*account*/iso.iso' '/media/iso'


Isn't it supposed to be with " (double quotes) instead of '?

---

### Post by xxrealmsxx on 2006-06-12
The location of the .iso reads: "/home/jamiewitter/Downloads/Software/Windows_Xp"

the file name is: XPPROSP2.iso

and I did:

jamiewitter@jamiewitter-laptop:~$ su
Password:
root@jamiewitter-laptop:/home/jamiewitter# mount -o loop /home/jamiewitter/XPPROSP2.iso /media/iso
/home/jamiewitter/XPPROSP2.iso: No such file or directory

what am i missing?

---

### Post by nanotube on 2006-06-12
[QUOTE=xxrealmsxx]The location of the .iso reads: "/home/jamiewitter/Downloads/Software/Windows_Xp"

the file name is: XPPROSP2.iso

and I did:

jamiewitter@jamiewitter-laptop:~$ su
Password:
root@jamiewitter-laptop:/home/jamiewitter# mount -o loop /home/jamiewitter/XPPROSP2.iso /media/iso
/home/jamiewitter/XPPROSP2.iso: No such file or directory

what am i missing?[/QUOTE]
you are answering your own question here. you said the location of the file is /home/jamiewitter/Downloads/Software/Windows_Xp, but then you show that your command is attempting to mount /home/jamiewitter/XPPROSP2.iso

just put in the full path in there, and it should work. :)

---

### Post by xxrealmsxx on 2006-06-12
[QUOTE=nanotube]you are answering your own question here. you said the location of the file is /home/jamiewitter/Downloads/Software/Windows_Xp, but then you show that your command is attempting to mount /home/jamiewitter/XPPROSP2.iso

just put in the full path in there, and it should work. :)[/QUOTE]

Haha I misread a previous post that said:

mkdir '/media/iso'
mount -o loop '/home/*account*/iso.iso' '/media/iso'

would work and it didn't.

the logical way worked after i changed .ISO to .iso in the filename although that shouldnt matter i thought.

I feel like im learning to crawl.

---

