---
title: "File permissions"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by davebrads1972 on 2006-10-30
Help !

I installed Dapper Drake on a dual boot system with XP Pro. I created a main linux partition, a swap partition and a "Data" partion. Everything installed OK but I cant use the data partion as i dont have ther correct permissions ? It says its owned by root, so how do i give myself full read+write access to the partion since its where i want to store all my files. I've read loads of threads about chmod etc and tried to change the permissons but dont know what Im doin ! Im completly new to this havin been with Windows for 10 years all this command line terminal stuff is hard work.

I just need a simple "how to" get access to a partion. Can anybody help please ?](*,)

---

### Post by caravel on 2006-10-30
I'm not sure about this, but I think maybe you should have mounted it under the /home folder.  That way all of your user related files would be stored on a separate partition.  Wait for someone that knows more about this than I do, to respond though.

---

### Post by podunk on 2006-10-30
This is how I set up a separate /home partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I don't know if you will have to start over? I *think* you can skip down to the part where you start mounting.

---

### Post by Kateikyoushi on 2006-10-30
You have full read write access to your home folder, isn't that enough ?
You could write anywhere you like but I would rather recommend try to do things the linux way and not as it were windows.

---

### Post by bsussman on 2006-10-30
Do not do any of the below commands until you are comfortable and understand what they do.  Otherwise you might be posting questions like 'pleez - I changed the owner of my system to achilles and now I can't boot'. Fo instance, type:

```
bos@Dillon:~$ man chown
```to read the traditional doc.


In a terminal window do the following.

Where is your data partition mounted?  You chose this when you installed ubuntu. Type;

```
bos@Dillon:~$ df
```to find out.  It will print something like:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             29293564   8529016  20764548  30% /
varrun                 1556652       224   1556428   1% /var/run
varlock                1556652         4   1556648   1% /var/lock
udev                   1556652       128   1556524   1% /dev
devshm                 1556652         0   1556652   0% /dev/shm
/dev/hda3             45815940  16026100  29789840  35% /home
/dev/hdb1             38298572    681768  35671336   2% /mnt/hdb1
/dev/hdb2             38622968   2293156  34367876   7% /mnt/hdb2
bos@Dillon:~$
```So the last column is the mountpoint where the partition is mounted.

Type:

```
bos@Dillon:~$ ls -la /your/mountpoint
```and you will get something like thie:

```
total 124
drwxr-xr-x  21 root root  4096 2006-10-28 15:47 .
drwxr-xr-x   9 root root   216 2006-10-28 14:10 ..
drwxr-xr-x   2 root root  4096 2006-10-28 14:59 bin
drwxr-xr-x   3 root root  4096 2006-10-28 14:57 boot
lrwxrwxrwx   1 root root    11 2006-10-28 14:48 cdrom -> media/cdrom
```probably your list will be very short, like just a lostandfound and . and .. You are doing this to confirm that you have the right partition and contents, so that you do not change what you do not want to change.

If you want xerxes to own the "data" area, type:

```
bos@Dillon:~$ sudo chown xerxes /your/mountpoint
```

---

### Post by CatKiller on 2006-10-30
Although permissions on the files matter for access, permissions on the mount point do not. I believe that the problem lies with the OP's /etc/fstab.

---

### Post by marx2k on 2006-10-30
When I 'sudo mkdir /media/hdb3' (for example), root owns it.

In order to access it (write to it) I have to 
'sudo chown myusername:myusername /media/hdb3'

However, the other directories in that folder are mounted drives and look like...

lrwxrwxrwx  1 root   root        6 2006-10-28 18:30 cdrom -> cdrom0
dr-xr-xr-x 14 root   root     4096 2006-10-25 09:35 cdrom0
drwxr-xr-x  2 root   root     4096 2006-10-30 15:56 data
lrwxrwxrwx  1 root   root        7 2006-10-28 18:30 floppy -> floppy0
drwxr-xr-x  2 root   root     4096 2006-10-28 18:30 floppy0
dr-xr-x---  1 root   plugdev 12288 2006-10-30 00:09 hda1
dr-xr-x---  1 root   plugdev 24576 2006-10-28 22:03 hdb1
drwxr-xr-x  2 root   root     4096 2006-10-30 20:54 hdb3
drwxr-xr-x  2 root   root     4096 2006-10-30 15:47 hdb4
dr-xr-x---  1 root   plugdev 12288 2006-10-30 00:09 hdd1
dr-xr-x---  1 root   plugdev 28672 2006-10-28 21:35 hde1
dr-xr-x---  1 root   plugdev  8192 2006-10-28 21:34 hde2
drwxr-xr-x  4 marx2k marx2k   4096 2006-10-30 21:04 hde3
dr-xr-x---  1 root   plugdev 16384 2006-10-30 11:58 hdf1

Even though this works (I am marx2k, so you can see hde3 is mine).. shouldnt the permissions and ownership look like the other drives? WHen I chown to root:plugdev or root:root, I cannot access the drive in Gnome.

Any ideas?

---

### Post by bsussman on 2006-10-31
does

```
you@yoursys:~$ df
```show it mounted?

If not, all you've done is create a potential mountpoint, which is a plain old directory until something is mounted there,  It gets changed, written to, read from just like any other directory.  This would explain the behavior you are reporting.

You should not be writing any files into a directory that is meant to be a mountpoint, since they will be inaccessable while something is mounted there.  That is, unless that is the behavior you want.

The rest of this post is unnecessary and not probably worth reading if you have already gotten the filesystem mounted...

The permissions of the directory change to the permissions of the top of the filesystem when a mount is done (I use /mnt for casual mountpoints):

```
bos@Dillon:/mnt$ ls -ld hdb1
drwxr-xr-x 21 root root 4096 2006-10-28 15:47 hdb1
bos@Dillon:/mnt$ sudo umount hdb1
bos@Dillon:/mnt$ ls -ld hdb1
drwxrwxr-x 2 root root 48 2006-10-28 14:10 hdb1
bos@Dillon:/mnt$ sudo mount hdb1
bos@Dillon:/mnt$ ls -ld hdb1
drwxr-xr-x 21 root root 4096 2006-10-28 15:47 hdb1
bos@Dillon:/mnt$
```So yes, the perms probably should be the same as the others if the state of the mount is the same.

Generally, mountpoints like /media, /mnt are used for casual, temporary, recovery mounts, not things that you expect to be there all the time or have a use much of the time.  These should be worked into the notmal hierarchy ( [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/) documents both of these points). Is '/mymusic/tunes' not a great deal easier to deal with than '/media/hdx2'?

After all this is resolved to your understanding, you are ready to mount your actual filesystem.  If it is to be a regularly mounted filesystem, you may as well make the proper entry in fstab.  It probably will look a lot like this(from my system):

```
/dev/hdb2       /mnt/hdb2       ext3            defaults        0       0
```Although yours will, of course, reference your filesystem, not hdb2.

There are many parameters that can be set, including ones that prevent automatic mounting, allow users to mount and unmount at will without root, etc.  NONE ARE NEEDED for a filesystem that you would like to always have mounted.

---

### Post by Iowan on 2006-10-31
Could you post the output from ```
fstab
```

---

