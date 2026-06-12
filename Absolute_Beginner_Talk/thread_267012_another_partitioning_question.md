---
title: "another partitioning question"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-09-28
when i installed ubuntu i made a good sized cock up.
i partitioned my 80gb hard-drive in to parts leaving 2 gb aside for swap.

im not sure if youl understand what im saying next.
the first partition had a label of "/" if you know what i mean.

i knew this was going to come out as the root drive in the file system in "places/computer"

i labeled my second partition as "/2" thinking this would give me a seperate file system in "places/computer"

instead i now have a file in root "/" called /2

can i reverse this anyway? remove the partition and merge it with the first?

idealy i would like a second filesystem in "places/computer" to keep say music etc in away from the system files.

do i do this by giving the second partition the ext3 format coz i gave it ext2 last time.

also someone told me i cant write to the file system anyway.if this is so then where do i keep my downloads?
surly i cant be expected to keep them on my desktop.whenever i try to put anything on the filesytem it blanks out the paste or if i try to move them from an aplication it pop ups with a notice saying i dont have permission to do that.

i really am getting fed up with this permission lark and i am so close to reverting to the single root account.
surely i cant go too far wrong if i just learn which folders to stay away from. i only want to put a few music files etc in there somwhere.

sorry if this is a bad explanation.

p.s me and my friend ------>](*,) <------- have a suicide pact!
anyone care for a cup of kamakazi?

---

### Post by davmac on 2006-09-28
Most of the times when I've installed Ubuntu, I've just allowed the installer to make the partitioning choices for me. You then end up with a /home/<myuserid> directory that you can use to your heart's content.

I have also tried manually setting up the partitions and on one of my servers have two partitions (plus swap of course) for / and /home. With this 2nd approach the few advantanges don't outweigh the disadvantages for me.

With your current situation you should be able to rescue the situation without a reinstall. You should find that you've already got a /home/loginid directory that you can use. You can install gparted using synaptic and use it to delete the /2 partition and then extend / into the space left behind (assuming that they're on contiguous disk areas.

I'm conscious that I've glossed over these instructions fairly quickly. If you want to take this approach and need more detail about how to do it, just shout up.

Mind you, if I was in your shoes and I hadn't done much configuration of the new system I'd probably nuke it and start again.

Hope this helps,

Dave Mac

---

### Post by GlennB on 2006-09-28
Hi,

> **uk_sphinx said:**
> when i installed ubuntu i made a good sized cock up.

You're not alone! I suspect most people have made mistakes while partitioning their drives. Don't panic!

> 
i partitioned my 80gb hard-drive in to parts leaving 2 gb aside for swap.


Ok so far. 2 gigs is probably a bit large for a swap partition, but it won't hurt. 

> 
im not sure if youl understand what im saying next.
the first partition had a label of "/" if you know what i mean.

The partition you are referring to is the 'root' partition, labelled as "/". This is essentially the top of your directory tree.

> 
i labeled my second partition as "/2" thinking this would give me a seperate file system in "places/computer"

In one sense, you're right. It would give you a separate file system, but not in any place that you would normally expect to find it. :) 

The only thing you did wrong, AFAICT, is to give your second partition a weird mount point. No big deal.

You need to remember that in Linux, everything is a file, and that the directory hierarchy is all relative to the root ( / ) directory. You can mount an entire partition so that it just appears as a 'normal' directory. You just called your directory '2' if I understand properly.

Let's do this by example.

First, let's find out what Ubuntu (and you) have done with the drive up to now. Go to a terminal window and enter this command to get a list of the drive partitions:

```
sudo fdisk -l
```

With luck, you should see something like this:

```
glenn@mypc:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2550    20482843+   7  HPFS/NTFS
/dev/hda2   *        2551        3825    10241437+  83  Linux
/dev/hda3            9435        9729     2369587+   5  Extended
/dev/hda4            3826        9434    45054292+  83  Linux
/dev/hda5            9435        9729     2369556   82  Linux swap / Solaris
```

Your partitions will be different to these. From what you have said, I'm guessing that you will see three entries (plus, maybe an 'extended' partition entry). Make a note of the 'device' column entries. If you have two entries here that are labelled 'Linux' under the 'System' heading, then you have indeed created two file systems.

Now back at the terminal prompt, let's find out where in the filesystem each of these devices is mounted, by using the mount command. Enter:

```
glenn@glenn-laptop:~$ mount
```

and hit return. You should see a list of devices and (to their right) the place in the filesystem where they appear, as below:

```
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
/dev/hda4 on /home type ext3 (rw,nosuid,nodev)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
```

There is a lot of stuff here you needn't worry about right now. Look in the left column for the devices that you saw in the output from the fdisk -l command, and note where they are mounted. On the system above, the root partition is on /dev/hda2, and /dev/hda4 is where the /home directory is mounted.

Now you know which drive partitions appear as particular directories. You may find that you have an entry that reads something like:

```
/dev/hda2 on /2
```

You probably don't want this. I'll be bold and suggest that you probably want something along the lines of

```
/dev/hda2 on /home/music
```

instead. The reason is that /2 is not part of the standard filesystem layout in Linux, and so it appears you have created a directory called '2' that has its own partition. You could use this, but there are better ways!

> 
can i reverse this anyway? remove the partition and merge it with the first?

You have choices to make (hey, this is Linux!). For example, you could:

[LIST]
[*]Delete the partition mounted at '2' and then resize the '/' partition to fill the disk
[*]Remount the partition at another place in the filesystem (maybe /home?)
[/LIST]

> idealy i would like a second filesystem in "places/computer" to keep say music etc in away from the system files.

ok, this makes sense. So maybe a good plan would be to create a directory under /home called /home/music, and then use it as the mount point for your second partition. This should be simple to do:

[LIST]
[*]Check there is nothing you need to keep on /2 !!
[*]Unmount the second partition (if it is currently mounted)
[*]Create a new mount point for your 'music drive'
[*]Make that mount point belong to you.
[*]Remount that partition on the new mount point.
[/LIST]

Example:

```
sudo umount /2
sudo mkdir /home/music
sudo chown yourusername /home/music
sudo mount /dev/hda2 /home/music
```

(That's a bit oversimplified, but it gives the idea - post back with your mount points and fdisk output if you need specifics). 

> 
do i do this by giving the second partition the ext3 format coz i gave it ext2 last time.

Either will work. If you want to stay 'standard' then go with ext3.

> 
also someone told me i cant write to the file system anyway.if this is so then where do i keep my downloads?

You're the sysadmin. It's up to you if you mount a partition read only or read/write. You can certainly mount an ext2 or ext3 partition read/write.

> surly i cant be expected to keep them on my desktop.whenever i try to put anything on the filesytem it blanks out the paste or if i try to move them from an aplication it pop ups with a notice saying i dont have permission to do that.

Remember that your Desktop IS IN the filesystem, and it lives in
/home/username/Desktop. It just so happens that you have write access to this directory, as it belongs to you.

> i really am getting fed up with this permission lark and i am so close to reverting to the single root account.
surely i cant go too far wrong if i just learn which folders to stay away from. i only want to put a few music files etc in there somwhere.

Please don't! It will be easier and better in the long run if you just mount your extra partition so that you have read/write access to it, somewhere under /home, and then store your files there. Using an account with root access for day to day use is asking for trouble.

Sorry this got so long, but I hope it helps.

Regards,

Glenn.

---

