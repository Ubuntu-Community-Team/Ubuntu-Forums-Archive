---
title: "Can't copy files off windows hard drive!"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by TygerTung on 2007-08-22
G'day,

I'm trying to copy a whole swathe of files off my windows desktop onto my ubuntu desktop so I can format the windows hard drive.

The problem is it just says access denied, how can I get around this?

It also says access denied when I try to open them in windows too, windows seems to have gone all bung. It won't let them copy them onto this hard drive either it just says access denied.

Any help would be greatly appreciated,

Sam

---

### Post by swoll1980 on 2007-08-22
Install ntfs config from synaptics (easy as pie) This program allows you write access to your windows as well. Works great for me!!

---

### Post by logos34 on 2007-08-22
> **TygerTung said:**
> It also says access denied when I try to open them in windows too, windows seems to have gone all bung. It won't let them copy them onto this hard drive either it just says access denied.

bung is right...In which case I'm not sure ntfs-3g is gonna help you.

---

### Post by TygerTung on 2007-08-22
I think I already have nfts3g

---

### Post by logos34 on 2007-08-22
> **TygerTung said:**
> I think I already have nfts3g

in that case maybe the permissions got changed (that driver would be the only explanation as to how that could have happened). You may not have read access.   cd over to where your ntfs drive is mounting.

what does

**ls -l**

show?

---

### Post by hyper_ch on 2007-08-22
for reading access you don't need ntfs-3g... you just need to mount the windows drive properly and it'll work.

---

### Post by TygerTung on 2007-08-22
How can I change the permissions back to make it more permissable?

I'm not sure how to cd to the other drive, in DOS you just go cd.. till you get to c: or whatever then type in d: but I can't seem to get that to work.

---

### Post by logos34 on 2007-08-22
for example. if it's mounted at /media/windows, 

cd /media/windows

ls -l
(this will show permissions/ownership for all the folders)

post that.  it may or may not be a permissions/ownership issue, just a guess.  soemthing's really screwy when you no longer have access to windows files IN windows.

---

### Post by TygerTung on 2007-08-22
How to you go down a level? In DOS you go CD.. how do you do it in the terminal?

---

### Post by logos34 on 2007-08-22
> **cd .. **

is that what you wanted? (only diff is there's a space after d, i think)

---

### Post by TygerTung on 2007-08-22
AHA!!!! you need to put a space in-between cd and the .., who would have thought!!!!!! Am used to DOS which I used to use when I was like 7 you see...

---

### Post by logos34 on 2007-08-22
> **hyper_ch said:**
> for reading access you don't need ntfs-3g... you just need to mount the windows drive properly and it'll work.

but that doesn't explain why the OP can no longer read them in windows either...I was thiniking   IF it was a permissions change issue in which windows files can't be accessed any longer IN wi dows, then they would need to have been altered (i.e. written to) with ntfs-3g.  then again, maybe this happened on the windows side, hard to tell.  all i know is I need some sleep....

---

### Post by logos34 on 2007-08-22
> **TygerTung said:**
> AHA!!!! you need to put a space in-between cd and the .., who would have thought!!!!!! Am used to DOS which I used to use when I was like 7 you see...
 and i know next to nothing about DOS, maybe i'll decide to learn it one of these days (like some boring rainy day)

---

### Post by tyggna1 on 2007-08-22
I would install the NTFS configuration tool from add/remove programs--that way, you can change the permissions in a nice GUI interface (even though it'll only give you two options, one of them is "enable read and write support.")

As a general guideline--synaptic is meant to be more advanced than add/remove programs.  While you can do more with it--it takes more know-how to use.  After installing a package, try typing in:

```
man <nameofpackage>
```

in the terminal, and that should give you an idea of how to use a utility.  You may need to navigate to where that package was installed--someone else will know more about that then I do.

---

### Post by dptxp on 2007-08-22
Why not copy from Windows ?
How to:
[http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html](http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html)
Download site:
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by tyggna1 on 2007-08-22
As for DOS conversion:  I myself am a convert that used DOS back in the day.  Here's a few tips that I picked up along the way.

Terminal/Unix:  It's CaSe Sensitive -- so you have a lot more options in Unix, but you need to be a lot more exact than in dos.
the man command:  use this before typing in a command, it's similar to /? and will give you any documentation associated with a specific command.  Boy has this one saved my bacon on more than one occasion.

There is no "Run" command.  <sigh>  Unix deals with programs in a different way.  Sure, it can execute a program in a manner similar to windows, but this is done almost exclusively with .bin (binary) files.  Rather, Unix is more likely to compile source-code on the spot, and run that.  If you don't have a program designed to run a file--then you'll have a very difficult time running that file.   Take a .exe for example:

.exe is just part of the file name in unix.  With the proper tools, it's unnecessary to have a .exe tagged on at the end of the file.   If you have a program that can recognize a .exe file as an executable (like Wine), then you can only run that file within that program i.e.

```
wine <location of file> && filename.exe
```

This threw me through a loop--as I was used to almost everything being a self-executable in DOS.  It's just different, though.

The next command--which I still, sadly, know very little about, is the make command.  Make is designed to recompile source code right there on the spot, and run the program you want.  You'll probably run into some installation instructions that will include something to the effect of:

```
make <program or path name to source code> install
```

Which means: make this programmer's source code into a runnable file, called install, that will put this piece of software on my machine.


Also, in regards to Unix: get help first, and write down important commands on paper!  I'm pretty confident with the terminal now--and I'm getting to the point where I use it fairly regularly.  Unfortunately, when I was first starting out with it, I didn't know exactly what I was doing.  My OS would no longer boot into the Graphical interface after I changed a few things (xorg.conf), and I had made a backup-as instructed, but I couldn't remember how to copy that backup over into the original file.  As a result, I had to reinstall my OS.  This was technically unnecessary, but I needed my computer working again--and I didn't have internet access.

Lastly:  be ready to do quite a bit of reading.  Unix and DOS aren't very similar, and most the stuff you knew how to do in DOS won't apply.  A safe approach is to assume you know nothing.  This is a good way to start.  I didn't know that there's a different command for editing text in a command-line interface than in a GUI  (cli uses the command vim, and GUI typically uses gedit).  You'll have to sort out the differences between using sudo before a command and being able to just use the program.  Of course, we're here to help, as a community, but so much help is already available online.  I've probably spent a few hours reading up information on a single problem, but I learned a lot in the process.  Just be willing to dig and search, and you'll get an answer in due time.

---

### Post by biomedtech on 2007-08-26
so I figured out how to cd to the media disk that I want, and I see that 'root' is the owner. How do I enable permissions, so that I can move files from ubuntu media, to the xp media (both ntfs)?

---

### Post by logos34 on 2007-08-26
> **biomedtech said:**
> so I figured out how to cd to the media disk that I want, and I see that 'root' is the owner. How do I enable permissions, so that I can move files from ubuntu media, to the xp media (both ntfs)?

linux can't write to ntfs without a special driver...you need ntfs-3g

**sudo apt-get install ntfs-config**

(it will grab the main program ntfs-3g as a dependancy)

then call up the gui:

**sudo ntfs-config**

>enable write support 

It will automatically edit your /etc/fstab file so that your ntfs partitions mount at boot with r+w access

reboot

---

### Post by biomedtech on 2007-08-26
no go. 

ntfs config only gave me an option to enable write support for external devices. The selection for 'internal' support was shadowed out. 

Here's my setup. 

One hard drive initially for XP.   

Second hard drive added, split in half, for Windows volume and Ubuntu system. both volumes on the 2nd drive are ntfs. 

Dual boot is normal, with the option to select  either OS.  Ubuntu sees all of the Windows volumes. I can read from them, but not write too, because 'root' is owner.  Ubuntu labels these volumes as Disk, Disk-1, Disk-2. 

If ntfs-config won't offer access to internal drives, how do I enable permissions to 'root' so that I can drag and drop from my 'Home' folder to the 'Disk' volumes?  Thank you.

---

### Post by logos34 on 2007-08-26
I think I know what the problem here is. 

If you could, please post the following files/output:

**sudo fdisk -l** (lowercase L)

[B]cat /etc/fstab

ls /media[/B]

**mount**

---

### Post by biomedtech on 2007-08-26
Hope this helps.

administrator@PD:/media/disk-1$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20022   160826683+   7  HPFS/NTFS

Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551       17234   117949230    f  W95 Ext'd (LBA)
/dev/hda3   *       17235       30515   106679632+  83  Linux
/dev/hda5            2551       16666   113386738+   7  HPFS/NTFS
/dev/hda6           16667       17234     4562428+  82  Linux swap / Solaris
administrator@PD:/media/disk-1$ cat /etc/stab
cat: /etc/stab: No such file or directory
administrator@PD:/media/disk-1$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda3 :
UUID=53f35782-91fa-4d53-8f8e-79fabb4bf049 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda6 :
UUID=e2c9b1db-14df-4b5f-9a98-b7086ef947fe none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/diskone ntfs-3g defaults,locale=en_US.UTF-8 0 0
administrator@PD:/media/disk-1$ ls /media
cdrom  cdrom0  disk  disk-1  diskone  floppy  floppy0
administrator@PD:/media/disk-1$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda5 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sda1 on /media/disk-1 type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/hda1 on /media/diskone type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
administrator@PD:/media/disk-1$

---

### Post by logos34 on 2007-08-27
> [COLOR="Red"]/dev/hda5 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf
/dev/sda1 on /media/disk-1 type ntfs (rw,nosuid,nodev,umask=222,utf[/COLOR]
[COLOR="Blue"]/dev/hda1 on /media/diskone type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)[/COLOR]

> # /etc/fstab: static file system information.
#
# -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda3 :
UUID=53f35782-91fa-4d53-8f8e-79fabb4bf049 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda6 :
UUID=e2c9b1db-14df-4b5f-9a98-b7086ef947fe none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
[COLOR="Blue"]/dev/hda1 /media/diskone ntfs-3g defaults,locale=en_US.UTF-8 0 0[/COLOR]

Just as I thought--only one ntfs partition has a permanant mount/fstab entry, and consequently (according to mount) is the only one mounting with write support ('fuse' module)...ntfs-3g can only convert ntfs partitions listed in fstab (which is why write support for internal devices is grayed-out in config gui).  You can't use the system-generated mount points 'disk' and 'disk-1'.  You should be able to write to hda1, however.

You need to create mount points for hda5 and sda1 and add them to fstab.

[B]sudo umount /media/disk
sudo umount /media/disk-1[/B]

[B]cd /media
sudo mkdir sda1 hda5[/B]

So 'ls /media' should now show:
> cdrom cdrom0 diskone floppy floppy0 **hda5 sda1**

Edit fstab:

**gksudo gedit /etc/fstab**

Add these two lines:

> [B]/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
/dev/hda5 /media/hda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 0[/B]

(That is the standard entry for ntfs partition in Feisty.)  

Reboot.  They should automount properly in read-only mode at /media/sda1 and /media/hda5. 

Now try enabling write support again in ntfs-config.  Check to see that fstab entries were converted to ntfs-3g.  They should now look like this:

> /dev/hda1 /media/diskone ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/hda5 /media/hda5 ntfs-3g defaults,locale=en_US.UTF-8 0 0

Hopefully you will have r+w access to all three ntfs partitions.

---

### Post by biomedtech on 2007-08-27
Thank you for the assistance. I am a little bleary-eyed, so will give this a go tomorrow. Hope all are having a good night. Take care

---

### Post by biomedtech on 2007-08-30
logos34, you totally rock!!!!!  This auto-mounted the XP volumes, and allows me to r /w freely.  
Thank you Thank you Thank you. 

I have only observation.  The XP start up went into a comatose state immediately after configuring Unbuntu. I imagine I goofed somewhere in my pursuit of cross-platform copying, but after running a registry cleaner, XP is mostly back on its feet. 

I really can't thank you enough for your assistance in these adjustments.  It sort of took me back to when I ran Amiga and Mac hardware. Only the Mac had a TCP protocol, so I had to set a scsi-based dos drive that both OS recognized. The Mac could access Internet, and my scsi interface fed updates to my Amiga  from time to time. 
I've no wish to repeat those times.  Thanks again, and take care.

---

### Post by logos34 on 2007-08-30
Thanks for the comments.  My pleasure  (troubleshooting is hobby of mine).  Good to hear XP is mounting properly r+w.  Wonder why XP freaked on boot...maybe it finally realized it's days are numbered and linux is closing in!

Enjoy!

---

