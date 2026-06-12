---
title: "Partition mistake?"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by TimJBart on 2006-07-26
I was following the video instructions on linux.com on how to partition the harddrive correctly for linux (ext3 for software, swap partition, and ext3 for data).  I did this in Gnome Partition Editor.

However, when it came to installing Ubuntu, I wasn't sure what to do with the 3 partitions.  I tried to leave them to ubuntus choices, so it correctly saw the swap file.  It also mounted one of the partitions on /

However, with the data partition I think I did something wrong as I have a partition on my desktop called HDA2 and I am unable to edit it!  I cannot create folders or move anything in there.  Do I have to mount it on / as well  (don't really know what this means!)

The only folder in this unusable drive is a LOST+FOUND.  Very strange.

Any help will be greatly appreciated as I want to stick with linux! :mrgreen:

---

### Post by moma on 2006-07-26
Can you give some more information.
Reply and copy/paste output of these commands (start terminal window from Applications -> Accessories menu and type these commands)

$ sudo fdisk -l 

$ cat /etc/fstab 

$ mount

// moma
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

---

### Post by OpsVentus on 2006-07-26
Hello Tim,

Can you go to a terminal(Programs-tools-terminal)
And type:
#mount
And tell us what's in your fstab? In a terminal type:
#gedit /etc/fstab

This way we can have a look at how the drive is mounted.
And tell us how you think your disk should be mounted.
Like:
hda1 /
hda2 /home
hda3 swap?

Cheers,
Bart.

---

### Post by TimJBart on 2006-07-26
As you can see I'm dual booting but hda2 is the problem drive.  I also don't have a home drive.

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2340    18796018+   7  HPFS/NTFS
/dev/hda2            2341        2936     4787370   83  Linux
/dev/hda3            2937        3066     1044225   82  Linux swap / Solaris
/dev/hda4            3067        3738     5397840   83  Linux


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /media/hda2     ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


/dev/hda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hda2 on /media/hda2 type ext3 (rw)



Thanks for the quick replies!

---

### Post by adam.tropics on 2006-07-26
On the installer, if you leave it to defaults, even if you create an extra partition with the intention of it being /home, unles you specify that mount point, it will simply format it to ext3, and create a default mount point. In this case it is mounted in /media/hda2. You do obviously have a /home. however it is on the root partition, and so is a folder rather than a partition. This is fine, not ideal, but usable never the less.

---

### Post by TimJBart on 2006-07-26
> **adam.tropics said:**
> On the installer, if you leave it to defaults, even if you create an extra partition with the intention of it being /home, unles you specify that mount point, it will simply format it to ext3, and create a default mount point. In this case it is mounted in /media/hda2. You do obviously have a /home. however it is on the root partition, and so is a folder rather than a partition. This is fine, not ideal, but usable never the less.

If it is fine why can I not use the hda2 for anything.  It is unwritable.

Is there a way I can use Gparted to correct this?

---

### Post by adam.tropics on 2006-07-26
try in fstab,

/dev/hda2 /media/hda2 ext3 defaults,rw 0 2

---

### Post by TimJBart on 2006-07-26
> **adam.tropics said:**
> try in fstab,

/dev/hda2 /media/hda2 ext3 defaults,rw 0 2

I have literally just installed linux! how do I do what you have described?  I dont understand ](*,)

---

### Post by adam.tropics on 2006-07-26
apologies, from a terminal, type

```
sudo gedit /etc/fstab
```

then hit enter, give your password, and an editor will open. In the file you will see the above posted line, and you need to add th rw and the comma. Save, exit, and remount the drive. that should allow you to write to it.

edit: Terminal can be found in Applications>>Accessories>>Terminal

---

### Post by TimJBart on 2006-07-26
sorry for being such an idiot at this.  I ahve added the rw but how do I unmount and remount the drive?

On the dektop I right clicked the drive and clicked unmount, but it came up with the error:

*Unable to unmount volume: mount: only root can unmount /dev/hda2 from /media/hda2*

---

### Post by adam.tropics on 2006-07-26
No problem, back in the terminal

```
sudo umount /dev/hda2
```

then

```
sudo mount /dev/hda2
```

---

### Post by OpsVentus on 2006-07-26
And remounting goes like:
sudo umount /dev/hda2
sudo mount /dev/hda2

;)

Too late...

---

### Post by TimJBart on 2006-07-26
```
t@TimJBart:~$ sudo umount /dev/hda2
t@TimJBart:~$ t
bash: t: command not found


t@TimJBart:~$ sudo mount /dev/hda2
mount: /dev/hda2 already mounted or /media/hda2 busy
mount: according to mtab, /dev/hda2 is already mounted on /media/hda2
```

My ineptness is sucking my will to live

---

### Post by OpsVentus on 2006-07-26
Try the sudo umount /dev/hda2 again.

---

### Post by TimJBart on 2006-07-26
```
t@TimJBart:~$
t@TimJBart:~$ sudo umount /dev/hda2
t@TimJBart:~$ t
bash: t: command not found
t@TimJBart:~$ sudo umount /dev/hda2
umount: /dev/hda2: not mounted

t@TimJBart:~$ sudo mount /dev/hda2
t@TimJBart:~$ t
bash: t: command not found
t@TimJBart:~$ sudo mount /dev/hda2
mount: /dev/hda2 already mounted or /media/hda2 busy
mount: according to mtab, /dev/hda2 is already mounted on /media/hda2
```

it seems to work but always says command not found!  but despite you help, I cannot create a folder in hda2


Is it worth rebooting linux or does it not work like that?

I am tempted to reinstall ubuntu.

I have 3 partitions, one for data, sone for software, and a swap.  When I get to the partition part of ubuntu installation, should both the software and data drives be mounted  at   /

---

### Post by mcvos on 2006-07-26
It says "command not found" because you gave the command "t", which doesn't exist. The umounting and mounting seems to work fine. Test if it works now.

---

### Post by OpsVentus on 2006-07-26
Yes, first try if it works again.

If not:
If your willing to reinstall Linux I can advise you to do so and make sure you set the mountpoint '/home' for the second data disk.
This way you have all your data and settings on the data disk.

Cheers,
Bart.

---

### Post by TimJBart on 2006-07-26
I am stupid, i was assuming it would ask for my password!

Ok, yes when i unmount it disappears from the desktop,then mount and it appears again, but still whenever i try and copy anything into it by dragging and dropping, it says I dont have the permissions.

---

### Post by TimJBart on 2006-07-26
> **adam.tropics said:**
> 
If not:
If your willing to reinstall Linux I can advise you to do so and make sure you set the mountpoint '/home' for the second data disk.
This way you have all your data and settings on the data disk.

Cheers,
Bart.

so the first disk would be /
the scond is my SWAP
the third I set to /home

would this be correct? I might reformat the partitions and reinstall ubuntu and get it right!

---

### Post by OpsVentus on 2006-07-26
You haven't got anything setup anything yet so yes, you can format and install again.
You benefit from it later.

Cheers,
Bart.

---

### Post by moma on 2006-07-26
Hello,

**Long method:**

Your /etc/fstab seems to be OK.  
```
/dev/hda2 /media/hda2 ext3 defaults 0 2
```

/dev/hda2 is mounted to /media/hda2. Read/write (rw) is also a default option on ext2 and ext3 filesystems.
----

Start gnome-terminal program from Applications -> Accessories -> Terminal menu. Issue following commands on the commandline:

$ [COLOR="Green"]sudo umount /dev/hda2[/COLOR] 

Test wheather the partition actually HAS an ext3 filesystem.
$ [COLOR="Green"]sudo fsck.ext3 /dev/hda2[/COLOR]

It must report similar to this
```
e2fsck 1.38 (30-Jun-2005)
/1: clean, 217813/5124480 files, 1559393/5120718 blocks
```

Is it OK?

Remount all entries in /etc/fstab
$ [COLOR="Green"]sudo mount -a[/COLOR] 

Always type (sudo mount -a) if you change your /etc/fstab or just want to remount all entries.

Now your /dev/hda2 is mounted on /media/hda2.
--

Make a data directory on /media/hda2
$ [COLOR="Green"]sudo mkdir /media/hda2/data[/COLOR] 

[COLOR="SandyBrown"]Notice: 
You could start Nautilus filemanager with "root" admin permissions and do the same thing with it.
$ sudo nautilus 
[/COLOR]
$ Let you (your login name) own that directory
$ [COLOR="Green"]sudo chown $USER:$USER /media/hda2/data [/COLOR]

Check the result 
$ [COLOR="Green"]ls -ld /media/hda2/data[/COLOR]
drwxr-xr-x 3 XXXX XXXX 4096 2006-07-26 13:10 /media/hda2/test

Now you can write and edit files on /media/hda2/data directory!

Start Nautilus filemanager (from Places -> Home folder menu) and do your work.
=====================================================

**Short method:**
Mount all partitions
$ sudo mount -a 

Start Nautilus filemanager with "root" admin rights
$ sudo nautilus 

Browse to: File System -> /media/hda2
and press right-mouse-button on /media/hda2
and choose "Properties" from popup-menu. Select Permissions tab and change permissions on that folder.

---

### Post by TimJBart on 2006-07-26
sorry moma, dont really understand all that, but I had already reinstalled.

Now, I have 10 gig in my home folder and I can use it properly now.

However, since the reinstall I now have on my desktop hda1 (which was my windowsXP partition)

How do I remove this from the desktop and how do I put my HOME folder on my desktop?

Thanks again for all the replies...you're draggin me kicking and screaming into the world of linux

---

### Post by Aurdal on 2006-07-26
Can you post your fstab file again?
It's at /etc/fstab

---

### Post by moma on 2006-07-26
Hello,

Good you fixed your home folder. Is it /dev/hda2 ?
Anyway,

1) Remove or comment out /dev/hda1 line in /etc/fstab. It will make your windows disk ureachable.
$ sudo cp /etc/fstab{,.backup} 

$ sudo gedit /etc/fstab 

$ sudo umount /dev/hda1

Restart HAL (= Hardware Abstarction Layer)
$ sudo /etc/init.d/dbus restart

It will also refresh the device-icons on the desktop.
Press CNTR + ALT + BACKSPACE to restart the desktop (if necessary).
-----

HAL:
[http://freedesktop.org/wiki/Software/hal](http://freedesktop.org/wiki/Software/hal)

---

