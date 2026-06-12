---
title: "reading/writing ntfs drive"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by hrd12 on 2007-03-29
Hi everyone, Linux noob here.  I have Ubuntu on one drive, and Windows XP on the other drive.  I am trying to set up Ubuntu so I can access my ntfs windows drive.  I read in a previous post that the following command will make the directory, and mount the drive.  I was able to read the files but not copy anything to my desktop in Ubuntu:
[I]
sudo mkdir /media/windows; sudo mount /dev/hda1 /media/windows; sudo nautilus /media/windows || sudo konqueror /media/windows[/I]

So I found something else that suggested I change my /etc/fstab, so now it looks like this:

[I]$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=613074bf-f95a-4f84-82ad-e8042afd803b /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda1     /media/windows  ntfs   nls=utf8,umask=0222  0   0
# /dev/hdb5
UUID=32a52820-ae7e-465c-9fa7-9e12299e9f5a none            swap    sw            
  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
[/I]

I rebooted as the post suggested and the permissions changed as shown here:

[I]erich@erich-desktop:/media$ pwd
/media
erich@erich-desktop:/media$ ls -la 
total 64
drwxr-xr-x  6 root root  4096 2007-03-27 17:08 .
drwxr-xr-x 21 root root  4096 2007-02-11 23:34 ..
lrwxrwxrwx  1 root root     6 2007-02-08 11:04 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-02-08 11:04 cdrom0
drwxr-xr-x  2 root root  4096 2007-02-08 11:04 cdrom1
-rw-r-----  1 root root 39967 2007-03-27 17:08 everything.pls
lrwxrwxrwx  1 root root     7 2007-02-08 11:04 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2007-02-08 11:04 floppy0
drwxr-xr-x  2 root root  4096 2007-03-27 16:20 windows
[/I]

I still couldn't see the files when I used the file browser, so I thought the problem might have been the ownership:

[I]erich@erich-desktop:/media$ chown erich windows
chown: changing ownership of `windows': Operation not permitted
[/I]

I'm kinda out of ideas right now, so any suggestions would be much appreciated.  Thanks!

---

### Post by dannyboy79 on 2007-03-29
you should be able to copy any files from a ntfs partition to your Ubuntu Desktop no matter what whether or not if you add the ntfs partition in your fstab or not. the fstab is just so that it mounts automatically every time you boot up. so, to fix your fstab, you need to uncomment that line, so delete the "#" and you should be set. also, you have to use sudo when changing the ownership of folders, also, don't just change the user but also the group, that's what I do anyway, so you would type in
sudo chown erich:erich /media/windows
and that will make the owner as well as the group yours. now you don't have to restart just to see if your fstab works. just type in 
sudo mount -a
and that will parse your fstab amd mount everytthing in it, so then you should see your contents show up in /media/windows

good luck

---

### Post by ComplexNumber on 2007-03-29
install and run [this]("http://flomertens.free.fr/ntfs-config/") (near the bottom of the page, it has the debs for edgy and fiesty). thats what i did. just download it, then fire up the terminal and go to where you downloaded it. then type in the following on the terminal:
**sudo dpkg -i *.deb**

btw i assume that you have already installed the ntfs-3g package(s).

i didn't need to edit my fstab file at all.

---

### Post by bodhi.zazen on 2007-03-29
See this link : [http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

Basically ntfs does not work that way.

You will need to modify permissions, ownership at the time of mount.

Either use ntfs-config (a gui tool) or read up on fstab, mount, and ntfs-3g.

---

### Post by hrd12 on 2007-03-29
Super it works now! Thanks for the quick help guys, I really appreciate it.

---

### Post by x1a4 on 2007-03-29
Hi,

Be sure to do a search before posting.  This topic has already been covered to death.

---

### Post by cowlip on 2007-03-29
ntfs-config is a godsend :)  It seems like there's a question about this a few times a day, maybe there should be a sticky or something..

---

### Post by dannyboy79 on 2007-03-30
> **bodhi.zazen said:**
> See this link : [http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

Basically ntfs does not work that way.

You will need to modify permissions, ownership at the time of mount.

Either use ntfs-config (a gui tool) or read up on fstab, mount, and ntfs-3g.

You are incorrect, ntfs CAN have it's umask set within your fstab. According to man mount:

**Mount options for ntfs**
*iocharset*=name 
Character set to use when returning file names. Unlike VFAT, NTFS suppresses names that contain unconvertible characters. 
utf8 
Use UTF-8 for converting file names. 
uni_xlate=[0|1|2] 
For 0 (or `no' or `false'), do not use escape sequences for unknown Unicode characters. For 1 (or `yes' or `true') or 2, use vfat-style 4-byte escape sequences starting with ":". Here 2 give a little-endian encoding and 1 a byteswapped bigendian encoding. 
*posix*=[0|1] 
If enabled (posix=1), the file system distinguishes between upper and lower case. The 8.3 alias names are presented as hard links instead of being suppressed. 
*uid*=value, *gid*=value and *umask*=value
Set the file permission on the filesystem. By default, the files are owned by root and not readable by somebody else. The umask value is given in octal.

---

### Post by bodhi.zazen on 2007-03-30
> **dannyboy79 said:**
> You are incorrect, ntfs CAN have it's umask set within your fstab. According to man mount:

**Mount options for ntfs**
*iocharset*=name 
Character set to use when returning file names. Unlike VFAT, NTFS suppresses names that contain unconvertible characters. 
utf8 
Use UTF-8 for converting file names. 
uni_xlate=[0|1|2] 
For 0 (or `no' or `false'), do not use escape sequences for unknown Unicode characters. For 1 (or `yes' or `true') or 2, use vfat-style 4-byte escape sequences starting with ":". Here 2 give a little-endian encoding and 1 a byteswapped bigendian encoding. 
*posix*=[0|1] 
If enabled (posix=1), the file system distinguishes between upper and lower case. The 8.3 alias names are presented as hard links instead of being suppressed. 
*uid*=value, *gid*=value and *umask*=value
Set the file permission on the filesystem. By default, the files are owned by root and not readable by somebody else. The umask value is given in octal.

LOL

What I meant is ntfs will not give write access.

For write access you need ntfs-3g.

Sorry if there was some confusion.

---

